<!DOCTYPE html>  
<html lang="ko">  
<head>  
<meta charset="UTF-8">  
<title>조 추첨</title>  
<style>  
body{  
    font-family: sans-serif;  
    text-align:center;  
    margin-top:50px;  
}  
textarea{  
    width:300px;  
    height:200px;  
}  
button{  
    margin-top:20px;  
    padding:10px 20px;  
    font-size:16px;  
}  
#result{  
    margin-top:30px;  
    font-size:18px;  
}  
</style>  
</head>  
  
<body>  
  
<h1>조 추첨기 🎲</h1>  
  
<p>이름을 한 줄씩 입력하세요</p>  
  
<textarea id="names"></textarea><br>  
  
<p>조 인원</p>  
<input type="number" id="size" value="4">  
  
<br>  
<button onclick="draw()">조 추첨!</button>  
  
<div id="result"></div>  
  
<script>  
function draw(){  
  
let names = document.getElementById("names").value  
.split("\n")  
.filter(n => n.trim() !== "");  
  
let size = Number(document.getElementById("size").value);  
  
// shuffle  
for(let i = names.length - 1; i > 0; i--){  
let j = Math.floor(Math.random() * (i + 1));  
[names[i], names[j]] = [names[j], names[i]];  
}  
  
let result = "";  
let groupNum = 1;  
  
for(let i = 0; i < names.length; i += size){  
let group = names.slice(i, i + size);  
result += "<b>" + groupNum + "조</b>: " + group.join(", ") + "<br><br>";  
groupNum++;  
}  
  
document.getElementById("result").innerHTML = result;  
  
}  
</script>  
  
</body>  
</html>  
