# aiax
js和jq跨域获取数据
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>手风琴导航测试</title>
	<script src="js/jquery-3.3.1.min.js"></script>
<style>
*{
	padding: 0;
	margin: 0;
}
.nav{
	width: 200px;
	list-style: none;
	border: 2px solid #ff6700;
	margin: 100px auto;
}
.box{
	width: 200px;
	height: 50px;
	background: green;
	color: #fff;
	text-align: center;
	line-height: 50px;
	cursor: pointer;
	border-bottom: 2px solid #fff;
}
.sum{
	width: 150px;
	height: 150px;
	margin-left: 25px;
	background: red;
	display: none;
}
</style>
</head>
<body>
	<ul class="nav">
		<li class="box">标题111</li><!--  li的下标0 -->
		<li class="sum">内容111</li> <!-- sum的下标0 -->
		<li class="box">标题222</li> <!-- li的下标2 -->
		<li class="sum">内容222</li> <!-- sum的下标1 -->
		<li class="box">标题333</li> <!-- li的下标4 -->
		<li class="sum">内容333</li> <!-- sum的下标2 -->
		<li class="box">标题444</li> <!-- li的下标6 -->
		<li class="sum">内容444</li> <!-- sum的下标3 -->
		<li class="box">标题555</li> <!-- li的下标8 -->
		<li class="sum">内容555</li> <!-- sum的下标4  后面依次由li的下标除以2等于sum的下标 -->
		<li class="box">标题444</li> 
		<li class="sum">内容444</li> 
		<li class="box">标题555</li> 
		<li class="sum">内容555</li>
		<li class="box">标题444</li> 
		<li class="sum">内容444</li> 
		<li class="box">标题555</li> 
		<li class="sum">内容555</li> 
	</ul>

<script>
	// js写法
	// var box = document.getElementsByClassName("box");
	// var sum = document.getElementsByClassName("sum");
	// for(var i=0;i<box.length;i++){
	// 	box[i].index = i;
	// 	box[i].onclick = function(){
	// 		var index = this.index;
	// 		for(var k=0;k<sum.length;k++){
	// 			sum[k].style.display = "none";
	// 		}
	// 		sum[index].style.display = 'block'; 
	// 	}
	// }


	// jq方法
	$(".box").click(function(){
		// $(this).css("background",'blue').siblings().css("background","green");
		var index = $(this).index();
		if(index == 2){ // 为了让li下标2对接sum下标1的判断
			index -= 1;
		}else{
		// 注意：因为上面用的是li的布局 所以要根据下标来对应计算
		// 使被点击的li的下标对应sum的下标
			index /= 2;
		}
		console.log(index)
		var sum = $(".sum");
		// 先吧所有的sum隐藏 只显示当前index下标的sum
		$(".sum").siblings('.sum').stop(true).slideUp().eq(index).slideDown();
	})



</script>


</body>
</html>
