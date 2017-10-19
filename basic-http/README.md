# basic-http


# basic-http是可以进行事件派发的httpclient库，可以发文件



### 依赖basic-help，basic-event


### 快速开始：


    npm install basic-http


### 如何使用：

```html

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
        <script src="../basic-help/dist/basic-help.js" type="text/javascript"></script>
        <script src="../basic-event/dist/basic-event.js" type="text/javascript"></script>
        <script src="../basic-http/dist/basic-http.js" type="text/javascript"></script>
        <script type="text/javascript">
            function success(event) {
                alert("发送post请求返回" + event.mData);
            }
            function error(event) {
                alert("发送post请求返回错误");
            }
            function successFile(event) {
                alert("发送文件请求" + event.mData);
            }
            function errorFile(event) {
                alert("发送文件请求返回错误");
            }
            window.onload = function () {
                var data = {
                    'hOpCode': '1',
                    'userName': 'hello',
                    'userPassword': '123456'
                };
                var header = [];
                header["token"] = "sadwadawdwad";
                var httpClient = new basic.HttpClient();
                httpClient.send(data, "http://localhost:8080/grain-httpserver-test/s", header);
                httpClient.addEventListener(basic.httpEventType.SUCCESS, success, this);
                httpClient.addEventListener(basic.httpEventType.ERROR, error, this);


                document.getElementById("sendDemoTest").addEventListener("click", sendFileTest);
            };
            function sendFileTest() {
                var obj = document.getElementById("userImg");
                var data = {
                    'hOpCode': '1',
                    'userName': 'hello',
                    'userPassword': '123456'
                };
                var header = [];
                header["token"] = "sadwadawdwad";
                var httpClient = new basic.HttpClient();
                httpClient.sendFile(obj.files, data, "http://localhost:8080/grain-httpserver-test/s", header);
                httpClient.addEventListener(basic.httpEventType.SUCCESS, successFile, this);
                httpClient.addEventListener(basic.httpEventType.ERROR, errorFile, this);
            }
        </script>
    </head>
    <body>
    <div>
        <input type="file" id="userImg" name="uploadFiles"/>
        <input type="button" value="发送请求" id="sendDemoTest"/>
    </div>
    </body>
    </html>

```




	