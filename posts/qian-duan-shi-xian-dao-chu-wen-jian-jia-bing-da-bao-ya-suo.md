---
title: '前端实现导出文件夹并打包压缩'
date: 2020-10-15 13:34:02
tags: []
published: true
hideInList: false
feature: 
isTop: false
---
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>Document</title>
  </head>
  <body>
    <p>Works on firefox, chrome , opera &gt;= 15 and IE &gt;= 10 (but NOT in compatibility view).</p>
    <button id="zip" class="btn btn-primary">click to zip</button>
    <button id="unzip" class="btn btn-primary">click to unzip</button>
    <div id="result_block" class="hidden">
      <h3>Content :</h3>
      <div id="result"></div>
      <div id="fileContent"></div>
    </div>
  </body>
  <script src="./node_modules/jquery/dist/jquery.min.js"></script>
  <script src="./node_modules/jszip/dist/jszip.js" ></script>
  <script src="./node_modules/file-saver/dist/FileSaver.js" ></script>
  
  <!-- 导入这个插件，可以不用使用下面的 download 函数 -->
  <script type="text/javascript">

    // 创建一个zip 对象，将文件名和内容读到文件中
    var zip = new JSZip();
    zip.file("readme.md", "#### hello\nMichael 测试文件"); // 直接把一个文件放在根目录下面
    zip.folder("media").file("image1.jpg", "#### hello\nMichael 测试文件").file("image2.png", "#### hello\nMichael 测试文件"); // 在根目录下放一个文件夹 media，内部包含两个模拟图片文件
    zip.folder("template").file("index.html", "<html><h3>Hello</h3></html>"); // 在根目录下放一个文件夹 template 内部是一个HTML文件。
    window.result = '';

    // 将文本压缩zip 并下载
    $("#zip").on("click", function () {
        // type: "string"
        zip.generateAsync({type:"blob"}).then(function (blob) {
        // 1) generate the zip file
            // console.log(blob);
            window.result = blob; // 绑定到全局组件上，使用另一个按钮下载
            // // 2) trigger the download
            saveAs(blob, "hello.zip");
            
        }, function (err) {
            $("#blob").text(err);
        });
    });


    // 将 zip 文件解压缩成内容读取。
    $("#unzip").on("click", function () {
      JSZip.loadAsync(window.result)
      // 1) read the Blob
        .then(function(zip) {
            console.log(zip);
            zip.forEach(function (relativePath, zipEntry) {
            // 2) print entries
                $("#fileContent").append($("<li>", {
                    text : zipEntry.name
                }));
            });
        }, function (e) {
            $('#result').append($("<div>", {
                "class" : "alert alert-danger",
                text : "Error reading " + window.result.name + ": " + e.message
            }));
        });
    });

    // 模拟点击，下载文件
    // fake_click(save_link);
    function fake_click(obj) {
      var ev = document.createEvent("MouseEvents");
      ev.initMouseEvent("click", true, false, window, 0, 0, 0, 0, 0, false, false, false, false, 0, null);
      obj.dispatchEvent(ev);
    }

    // 下载文件
    // download("save.txt","hello world");
    function download(name, data) {
      var urlObject = window.URL || window.webkitURL || window;
      var downloadData = new Blob([data]);
      var save_link = document.createElementNS("http://www.w3.org/1999/xhtml", "a")
      save_link.href = urlObject.createObjectURL(downloadData);
      save_link.download = name;
      fake_click(save_link);
    }
  </script>
</html>

```