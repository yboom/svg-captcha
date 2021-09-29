# Anti-OCR

这是一个修改版的 svg-captcha 用于生成计算机算法难以识别和理解的文字，以减少通信等过程中的信息泄漏。支持中文。

## 安装
```
git clone https://github.com/yboom/svg-captcha
npm install --save opentype.js tiny-inflate
```

## 用法

app.js

```Javascript
var svgCaptcha = require('./svg-captcha');

var text = "Text to protect";

svgCaptcha.loadFont("hand.ttf")
const lineSize = 20;
const fontSize = 32;
console.log("<html><body>");
for (let i=0;i<text.length;i+=lineSize){
	let line = text.substring(i,Math.min(i+lineSize,text.length));
	let captcha = svgCaptcha(line, {noise:fontSize/8, fontSize:fontSize, height:fontSize, width:line.length*fontSize});
	console.log(captcha);
	console.log("</br>");
}
console.log("</body></html>");
```
执行之：
```Javascript
node app.js > app.html
```

用浏览器打开生成的 app.html 文件可以看到结果。

## 协议
[MIT](LICENSE.md)
