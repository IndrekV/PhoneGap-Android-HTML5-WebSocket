Android HTML5 WebSocket 
=======================

A Java library that makes a WebSocket object available for projects that uses a WebView (like PhoneGap project)

Usage
=====

* copy the java-src contents into the src folder of your project.
* add `import com.freakdev.phonegap.*;` to the imports of your main java file
* also add these two lines inside the onCreate function, after the loadUrl

```java
   WebSocketFactory wsFactory = new WebSocketFactory(appView);
   appView.addJavascriptInterface(wsFactory, "WebSocketFactory");
```

* copy websocket.js to your assets/www folder
* edit your index.html to include the websocket.js
* in your javascript, create a new WebSocket, and overload its methods 'onopen','onmessage','onerror','onclose';

```javascript
var ws = new WebSocket("ws://192.168.13.37:1337/");

ws.onopen = function()
{
	ws.send("Message to send");
	alert("Message is sent...");
};
ws.onerror = function (e) 
{ 
	alert("Error...");
};
ws.onmessage = function (evt) 
{ 
	var received_msg = evt.data;
	alert("Message is received...");
};
ws.onclose = function()
{ 
	alert("Connection is closed..."); 
};
```
