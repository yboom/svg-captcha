#Anti-OCR

This modified fork of svg-captcha can be used to generate image to decrease the probabilty of computer algorithm to recognize and understand the text.

Chinese [中文](README_CN.md) is supported.

## install
```
git clone https://github.com/yboom/svg-captcha
npm install --save opentype.js tiny-inflate
```

## usage

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
Execute it in command line:
```Javascript
node app.js > app.html
```

Open app.html to see the result.

## License
[MIT](LICENSE.md)
