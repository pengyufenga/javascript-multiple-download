JavaScript多文件下载
============================

### 代码的封装以及相关 DEMO

DEMO1：[javascript-multiple-download](http://rawgithub.com/barretlee/javascript-multiple-download/master/test/test.html) (HTTPS，第三个有bug)

DEMO2：[javascript-multiple-download](http://qianduannotes.duapp.com/demo/javascript-multiple-download/test/test.html) (HTTP，测试正常)
      
Bug 说明，经过一番细节处理之后，基本兼容各个浏览器，我把代码放在 https://raw.github.com 上托管，可能因为是 https 传输，第三个测试中报错了，报错的具体内容是：HTTPS 安全受到 http://rawgithub.com/barretlee/javascript-multiple-download/master/file/test.jpg 的威胁，而 test.txt 文件没有报错。放到 http 协议下测试运行结果是可观的。（这点我没有去深究，肯定是有深层安全方面原因的，难道就因为他是 jpg图片格式？）后面的 demo 我放在 BAE 上，没有问题，不过没测试 safari 和 opera。

### 接口的调用

提供了三个接口，支持单文件下载，多文件下载，多文件下载自定义命名。

1）单文件下载

	Downer("./file/test.txt");

2）多文件下载
	
	Downer(["./file/test.txt","./file/test.txt"]);

3）多文件下载自定义命名
	
	Downer({
		"1.txt":"./file/test.txt",
		"2.jpg":"./file/test.jpg"
	});	

文件的 URL 如 `./file/test.jpg` 都可以改成 base64 或者其他格式,如：

	Downer({
	    "data64.jpg" : "data:image/jpg;base64,/9j/4AAQSkZJRgABAQEAYABgAAD/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsKCwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wAARCAAYADsDASIAAhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQAAAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWmp6ipqrKztLW2t7i5usLDxMXGx8jJytLT1NXW19jZ2uHi4+Tl5ufo6erx8vP09fb3+Pn6/8QAHwEAAwEBAQEBAQEBAQAAAAAAAAECAwQFBgcICQoL/8QAtREAAgECBAQDBAcFBAQAAQJ3AAECAxEEBSExBhJBUQdhcRMiMoEIFEKRobHBCSMzUvAVYnLRChYkNOEl8RcYGRomJygpKjU2Nzg5OkNERUZHSElKU1RVVldYWVpjZGVmZ2hpanN0dXZ3eHl6goOEhYaHiImKkpOUlZaXmJmaoqOkpaanqKmqsrO0tba3uLm6wsPExcbHyMnK0tPU1dbX2Nna4uPk5ebn6Onq8vP09fb3+Pn6/9oADAMBAAIRAxEAPwD9NgKKK8w8beO/EMVzGdJ08W2jW2t2WnXGpLdx+e7PPEkii3eJgYj5mwsJFkzkquAC3VFc0lFf10/UOlz1CivO9H+LEmreP7jw8mlBrLfPDa6nC1y0cksX30Z2t1hGCHBEcsjAqQVHOJPCfjnxFc+HNU1rxPpmh6Vp9mt232i01WWXmGV0IdXt0CrhD8+45xnaM4A00uZ9rgtZcq3vb5noFLXCfDz4j3vjbT9XM+hSabqdhtItWFxGswZCybTc28DjJDAkx7fRjzi/qmv6zH8LdR1m6sP+Ef12PSprprPzkufssyxMwXeBtfBA5xg0OLi2n/Vwh+8aUep1gFLXGeKhqmj+FtGmt9fvvtVvfWMc9w0VsWvUkuI43WUeVtAIcnMYQggYI6Hs6lqwk7pPuNrkPEHwn8N+KNRkvdQh1BpZJY7ho7fVru3haWPbslMUcqpvXYhD7d2VU54FFFNNxd1uPyJIfhb4dt/EkOuxwXy6hBNJPD/xNLryImkz5myHzPLUNkllC4J5IyAaWP4W+GY7+/uzp7yy3sc8UiTXc0kUazHdMIo2cpDvPLeWFyeTRRRd9wH6B8NNB8NyapJZx38kmpxrFePe6pdXbTKAQMmaRjkAkZHOMDOAKmbwLp9n8Pp/CGkr/Zmm/wBnyadbjLS+QjIUB+ZstjPdsn1oopOTfUa91prdf1+hFrfhnWNb0HSLCTVrGOaC6tbi+mXT323CwyrJtiXzv3RZkXljJgZ4PWuooopNtkpWVkf/2Q=="
	});
