# tools
<!--easy to create html sources-->
<!doctype html>
<html>
<head>
<title>タグ</title>
<style>
body,html{
  width:100%;
  height: 100%;
  font-size:100%;
  -webkit-text-size-adjust:100%;
}
textarea{
width: 100%;
height: 40vh;
}
#changeT{
width:80%;
display: block;
margin: 0 auto 30px;
}
input[value="出力"]{
color:red;
font-weight: 600;
}
#changeT input{
  margin-bottom:1em;

}
</style>
</head>
<body>
<form id="changeT">
<textarea id="textB"></textarea>
<p>
<input type="text" name="textH" id="textH" placeholder="先頭" value="<table>">
<input type="text" name="textF" id="textF" placeholder="行頭" value="<tr><td>">
<input type="text" name="textL" id="textL" placeholder="行末" value="</td><td></td></tr>">
<input type="text" name="textT" id="textT" placeholder="末尾" value="</table>">
<select name="hName" id="hName" onchange="headN(this.value)">
<option>-</option>
<option value="h2">h2</option>
<option value="h3">h3</option>
<option value="h4">h4</option>
<option value="h5">h5</option>
<option value="h6">h6</option>
<option value="p">p</option>
<option value="span">span</option>
<option value="strong">strong</option>
<option value="figure">figure</option>
</select>
</p>
<p>
<input type="button" value="リセット" onclick="resetA()">
<input type="button" value="table先頭列セット" onclick="setT()">
<input type="button" value="ul" onclick="setUl()">
<input type="button" value="dl" onclick="setDl()">
<input type="button" value="article section" onclick="setArt()">
<input type="button" value="div divセット" onclick="setDiv()">
<input type="button" value="囲い数字表示" onclick="setNum()">
<input type="button" value="ギリシャ文字表示" onclick="setGreek()">
<input type="button" value="選択" onclick="getA()">
<input type="button" value="出力" onclick="outS()">
</p>
<textarea id="textA"></textarea>
</form>
<script>
function outS(){
var sourceT = document.getElementById('textB').value;
var head = document.getElementById('textH').value;
var first = document.getElementById('textF').value;
var last = document.getElementById('textL').value;
var tail = document.getElementById('textT').value;
sourceT = repl(sourceT);
head = repl(head);
first = repl(first);
last = repl(last);
tail = repl(tail);
sourceT = sourceT.replace(/\n/g, last+"\n"+first);
if(head != ""){
document.getElementById("textA").innerHTML += head+"\n"+first+sourceT+last+"\n"+tail+"\n";
}else{
document.getElementById("textA").innerHTML += first+sourceT+last+tail+"\n";
}getA();
}
function repl(x){
x = x.replace(/&/g,'&amp;');
x = x.replace(/</g,'&lt;');
x = x.replace(/>/g,'&gt;');
x = x.replace(/"/g,'&quot;');
x = x.replace(/'/g,"&#39;");
return x;
}
function headN(n){
document.getElementById('textH').value="";
//var headV = document.getElementsByName('hName')[0].value;
document.getElementById('textF').value=`<${n}>`;
document.getElementById('textL').value=`</${n}>`;
document.getElementById('textT').value="";
}
function setNum(){
  document.getElementById('textA').textContent = `&amp;#9312;<!--1-->
&amp;#9313;<!--2-->
&amp;#9314;<!--3-->
&amp;#9315;<!--4-->
&amp;#9316;<!--5-->
&amp;#9317;<!--6-->
&amp;#9318;<!--7-->
&amp;#9319;<!--8-->
&amp;#9320;<!--9-->
&amp;#9321;<!--10-->`;
}
function setGreek(){
  document.getElementById("textA").textContent = `&#8544;<!--Ⅰ-->
&#8545;<!--Ⅱ-->
&#8546;<!--Ⅲ-->
&#8547;<!--Ⅳ-->
&#8548;<!--Ⅴ-->
&#8549;<!--Ⅵ-->
&#8550;<!--Ⅶ-->
&#8551;<!--Ⅷ-->
&#8552;<!--Ⅸ-->
&#8553;<!--Ⅹ-->
`;
}
function resetA(){
document.getElementById('textB').value="";
document.getElementById('textH').value="";
document.getElementById('textF').value="";
document.getElementById('textL').value="";
document.getElementById('textT').value="";
document.getElementById('textA').value="";
window.location.reload();
}
function setArt(){
document.getElementById('textH').value='<article><section>';
document.getElementById('textF').value="<div>";
document.getElementById('textL').value="</div>";
document.getElementById('textT').value="</section></article>";
}

function setT(){
document.getElementById('textH').value="<table>";
document.getElementById('textF').value="<tr><th>";
document.getElementById('textL').value="</th><td></td></tr>";
document.getElementById('textT').value="</table>";
}
function setUl(){
document.getElementById('textH').value="<ul>";
document.getElementById('textF').value="<li>";
document.getElementById('textL').value="</li>";
document.getElementById('textT').value="</ul>";
}
function setDl(){
document.getElementById('textH').value="<dl>";
document.getElementById('textF').value="<dt>";
document.getElementById('textL').value="</dt><dd></dd>";
document.getElementById('textT').value="</dl>";
}
function setSpan(){
document.getElementById('textH').value="";
document.getElementById('textF').value="<span>";
document.getElementById('textL').value="</span>";
document.getElementById('textT').value="";
}
function setDiv(){
document.getElementById('textH').value="<div>";
document.getElementById('textF').value="<div>";
document.getElementById('textL').value="</div>";
document.getElementById('textT').value="</div>";
}
function getA(){
document.getElementById('textA').select();
document.execCommand('copy');
}
</script>
</body>
</html>
