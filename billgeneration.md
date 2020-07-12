<!DOCTYPE html>
<html>
<head>
<title>Bill Generation</title>
<script>
	var amount = new Number();
	
	function init(){
		
		var name = document.getElementById("name").value;
   	var billID = document.getElementById("billID").value;
    var data = "<table border='1' > <tr> <th colspan='2'>NAME:"+name+"</th><th colspan='2'>BILL ID:"+billID+"</th></tr><tr><th >PRODUCT NAME</th><th >PRICE</th><th >QUANTITY</th><th >TOTAL</th></tr>                                                                  ";
    document.getElementById("bill").innerHTML = data;
   		
   	document.getElementById("content").innerHTML = "<lable>PRODUCT NAME:</lable><select name='product' id='product' required><option></option><option>A1</option><option>A2</option><option>A3</option><option>A4</option><option>A5</option></select><lable>PRICE:</lable><input type='number' name='price' id='price' required><lable>QUANTITY:</lable><input type='number' name='quantity' id='quantity' onchange='sum();' required><lable>TOTAL:</lable><input type='number' name='total' id='total'  readonly> <input type='button' value='   ADD   ' id='add' onclick='print1()' > <input type='button' value='   PRINT   ' id='print' onclick='getprint()' >";
	}
function print1(){
	
	
    var product = document.getElementById("product").value;
    var price = document.getElementById("price").value;
    var quantity = document.getElementById("quantity").value;
    var total = document.getElementById("total").value;
    amount = Number(amount) +  Number(total);
  
 	  var data = document.getElementById("bill").innerHTML;
 	  
  	 data =  data.slice(0,data.length-59) ;
 
    document.getElementById("bill").innerHTML = data+ "<tr ><td >"+product+"</td><td >"+price+"</td><td >"+quantity+"</td><td >"+total+"</td></tr><tr><th colspan='4'>TOTAL AMOUNT:"+amount+"</th></tr></table>";
  
}
function sum(){
 	var price = document.getElementById("price").value;
    var quantity = document.getElementById("quantity").value;
  
    document.getElementById("total").value = price*quantity;

}
function getprint(){
	var original = document.body.innerHTML;
	document.body.innerHTML = document.getElementById("bill").innerHTML;

	window.print();

	document.body.innerHTML =  document.getElementById("o").innerHTML;
}
</script>
<style type="text/css">
	
</style>
</head>
<body >
	<div id="o">
<h1>XYZ STORE</h1>
<lable>NAME:</lable>
<input type="text" name="name" id="name" required>
<lable>BILL ID:</lable>
<input type="text" name="billID" id="billID" required>
<input type="button" value="NEXT" id="next" onclick="init();" >
</div>
<br><br>
<div id="content"></div>
<br><br>
<div id="bill"></div>


</body>
</html>
