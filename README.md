# 随机生成验证码

1. 01.html --> [demo1](https://mankeung.github.io/create-code/src/01.html)
1. 02.html --> [demo2](https://mankeung.github.io/create-code/src/02.html)
1. 03.html --> [demo3](https://mankeung.github.io/create-code/src/03.html)

+ demo-code
```
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <title>Document</title>
</head>

<body>
  <canvas id="myCanvas" width="80px" height="27px" style="float: right; border:1px solid #d3d3d3;"></canvas>
</body>

</html>
<script>
var code = '';

function createCode() {
  code = "";
  var codeLength = 4; //验证码的长度，可变
  var canvas = document.getElementById('myCanvas'); //获取画布
  var selectChar = new Array(0, 1, 2, 3, 4, 5, 6, 7, 8, 9,
    'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z',
    'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z'
  ); //所有候选组成验证码的字符

  for (var i = 0; i < codeLength; i++) {
    var charIndex = Math.floor(Math.random() * 62);
    code += selectChar[charIndex]+' ';
  }
  if (canvas) {
    var ctx = canvas.getContext('2d');
    ctx.fillStyle = '#FFFFFF';
    ctx.fillRect(0, 0, 70, 27);
    ctx.font = "20px arial";
    // 创建渐变
    var gradient = ctx.createLinearGradient(0, 0, canvas.width, 0);
    gradient.addColorStop("0", "magenta");
    gradient.addColorStop("0.5", "blue");
    gradient.addColorStop("1.0", "red");
    // 用渐变填色
    ctx.strokeStyle = gradient;
    ctx.strokeText(code, 5, 20); //画布上添加验证码
  }
}

createCode();
console.log(code);

</script>

```
