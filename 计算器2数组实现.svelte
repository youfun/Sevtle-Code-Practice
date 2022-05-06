<script src="//qidian.gtimg.com/lulu/theme/peak/js/common/all.js">
  import browser from "webextension-polyfill";
    let numdispay = 0;
		$:numdispay=strtmp[strtmp.length-1].slice(1,)
    let numstr = [];
		$: numstr=strtmp.join("");
	let strtmp =[" "];
	let result=0

	// 数字类按钮点击函数
    function num1() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num1').innerText;
         strtmp = strtmp}
    function num2() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num2').innerText;
        strtmp = strtmp}
    function num3() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num3').innerText;
         strtmp = strtmp}
    function num4() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num4').innerText;
        strtmp = strtmp}
    function num5() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num5').innerText;
         strtmp = strtmp}
    function num6() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num6').innerText;
         strtmp = strtmp}
    function num7() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num7').innerText;
         strtmp = strtmp}
    function num8() {
       strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num8').innerText;
        strtmp = strtmp}
    function num9() {
        strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + document.getElementById('num9').innerText;
         strtmp = strtmp}
   
	
    function num0() {
			if (strtmp[strtmp.length - 1][1]==="0"){
        alert("不能连续输入两个零")
			}
			else{strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + 
				document.getElementById('zero').innerText;
    		strtmp = strtmp;}
        }
    

	    function decimal() {
			if (strtmp[strtmp.length - 1].indexOf(".") != -1){
        alert("一个数字中不能输入两个小数点")
			}
			else{strtmp[strtmp.length - 1] = strtmp[strtmp.length - 1] + 				
				document.getElementById('decimal').innerText;
    		strtmp = strtmp;}
        }

												
	// 重置按钮点击函数
    function AC() {numstr = []; numdispay = 0;strtmp =[" "]; result=0}
	
   // 四则运算按钮点击函数
    function add() {
			strtmp=[...strtmp,document.getElementById('add').innerText]
		}
	
    function subtract(){
			strtmp=[...strtmp,document.getElementById('subtract').innerText];
    }
	
    function multiply(){
			strtmp=[...strtmp,document.getElementById('multiply').innerText];
    }
	
	    function divide(){
			strtmp=[...strtmp,document.getElementById('divide').innerText];
    }
	
   // 等于按钮点击函数
   function equal() { 
	let result = Number(strtmp[0])
    let way = ""
    for (var i = 1; i < strtmp.length; i++) {
        let num = Number(strtmp[i].slice(1, ))
        if (num.length > 1) {
            break;
        } else if (strtmp[i - 1] === "x"||strtmp[i - 1] === "/"||strtmp[i - 1] === "-") {
            num = 0 - num;
            way = strtmp[i - 1];
        } else if (strtmp[i].length > 1) {
            way = strtmp[i][0]
        }
        switch (way) {
            case "+":
                result = result + num;
                break;
            case "-":
                result = result - num;
                break;
            case "x":
                result = result * num;
                break;
            case "/":
                result = result / num;
                break;
        }
    }
    return numdispay=result
}
    
</script>
<link rel="stylesheet" href="//qidian.gtimg.com/lulu/theme/peak/css/common/ui.css">


<body>
    <p style="font-size:large;">计算器</p>
    <div style="min-height:30px;">
            <p  style="color:orange;font-size:18px;margin-right:20px">{numstr}</p>
	</div>
	<div style="min-height:30px;"> 		
			<p  style="color:black;font-size:24px;margin-right:20px" >{numdispay}</p>

    </div>
	<div>
    <button on:click={AC} class="ui-button" style="width:140px;">AC</button>
    <button on:click={divide} class="ui-button" id="divide" >/</button>
    <button on:click={multiply} class="ui-button" id="multiply">x</button>
<br>
    <button on:click={num1} class="ui-button" id="num1">1</button>
    <button on:click={num2} class="ui-button" id="num2" >2</button>
    <button on:click={num3} class="ui-button" id="num3">3</button>
	
    <button on:click={subtract} class="ui-button" id="subtract"> -</button>
    <br>

    <button on:click={num4} class="ui-button" id="num4">4</button>
    <button on:click={num5} class="ui-button" id="num5">5</button>
    <button on:click={num6} class="ui-button" id="num6">6</button>
	
    <button on:click={add} class="ui-button" id="add"> +</button>
    <br>

    <button on:click={num7} class="ui-button" id="num7">7</button>
    <button on:click={num8} class="ui-button" id="num8">8</button>
    <button on:click={num9} class="ui-button" id="num9">9</button>
	
    <button on:click={equal} class="ui-button" style="height:143px; position: absolute; margin-left:0.25rem">=</button>
    <br>
    <button on:click={num0}  class="ui-button" style="width:140px;" id="zero">0</button>
    <button on:click={decimal} class="ui-button"id="decimal" style="font-size:large;"  >.</button>
    </div>
  <!-- 
    <p>the strtmp is 等于{strtmp} </p>
    <p>the numstr is 等于{numstr} </p>
   -->

</body>

<style>
    body {
        width: 300px;
        font-family: helvetica, arial, sans-serif;
        font-size: 13px;
        height: 500px;
    }
   
    button{
    width:68px;
    height:68px;
    font-size: larger;
    }

    div {
        width: 300px
    }
</style>