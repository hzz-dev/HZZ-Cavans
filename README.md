# HZZ-Cavans
一 .canvars 基础用法 
    //绘制矩形
 
    <body>
		<!-- canvas三要素 设置画布 id,width,height -->
		<canvas id="canvars1" width="600" height="600">			
		</canvas>		
		
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			console.log(ctx)
			
			//3. 绘制路径
			ctx.rect(50,50,300,300)
			//4. 设置填充 样式
			ctx.fillStyle = 'aquamarine'
			ctx.fill()
			
			//5.描边 渲染路径
			ctx.lineWidth = '20'
			ctx.strokeStyle = 'coral'
			ctx.stroke()							
		</script>		
	</body>

二 .绘制圆形和文本  
1/绘制线条 
   
    <body>
		<!-- canvas三要素 设置画布 id,width,height -->
		<canvas id="canvars1" width="600" height="600">			
		</canvas>	
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			console.log(ctx)
			
			//3. 设置绘制起始点
			ctx.beginPath() //设置开始绘制路径
			ctx.moveTo(50,50)
			//设置经过某个位置
			ctx.lineTo(50,300)
			ctx.lineTo(300,100)
			ctx.lineTo(300,250)
			ctx.closePath() //设置结束绘制
			
			//4. 绘制路径
			ctx.lineCap = 'round' //起始点样式
			// ctx.lineJoin = 'round' //中间拐角样式
			// ctx.miterLimit = 2 //裁剪角 1,2,3三个等级 
			ctx.lineWidth=10
			ctx.strokeStyle = 'crimson'
			ctx.stroke()
			
			ctx.fillStyle = 'aquamarine'
			ctx.fill()			
		</script>
	</body>

2/绘制圆形 

    <body>
		<!-- canvas三要素 设置画布 id,width,height -->
		<canvas id="canvars1" width="600" height="600">			
		</canvas>
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			// console.log(ctx)
			// 默认为falses顺时针
			ctx.arc(300,300,100,0,2*Math.PI,true)
			ctx.strokeStyle ='aquamarine'
			ctx.stroke()			
			ctx.fillStyle = 'burlywood'
			ctx.fill()
		</script>
	</body>

3/绘制文本 
    
     <body>
		<canvas id="canvars1" width="600" height="600">
		</canvas>
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			// console.log(ctx)
			ctx.font = "50px 微软雅黑"
			
			// 阴影
			ctx.shadowColor = 'rgba(0,0,0,1)'
			ctx.shadowBlur = '10'
			ctx.shadowOffsetX =10
			ctx.shadowOffsetY =10
			
			var x = 600;
			setInterval(function() {
				// 清空画布
				ctx.clearRect(0,0,600,600)
				x-=3;
				if(x<-100) {
					x = 600;
				}
				ctx.fillText('helloworld',x,100)
				ctx.strokeText('哈哈哈哈',x,200)
			},16)
		</script>
	</body>

三  .绘制图像
 	1/图片处理 +文字 打码 

    <body>
		<canvas id="canvars1" width="600" height="600">
		</canvas>
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			console.log(ctx)

			// 绘制图像
			// ctx.drawImage(图片对象,x位置,y位置)
			//ctx.drawImage(图片对象,x位置,y位置,宽度,高度)
			//ctx.drawImage(图片对象,图像裁剪的位置x,图像裁剪的位置y,裁剪的宽度,裁剪的高度,x位置,y位置,宽度,高度)
			var img = new Image()
			img.src = './cat.jpg'
			
			// var img2 = new Image()
			// img2.src = './dog.jpg'
			// 图片载入数据后再绘制内容
			img.onload = function(){
				// ctx.drawImage(img,50,50,300,200)
				ctx.drawImage(img,50,50,300,200)
				ctx.font = '12px 微软雅黑'
				ctx.fillStyle = 'aqua'
				ctx.fillText('打码',310,235)
			}
			// img2.onload = function(){
			// 	ctx.drawImage(img2,100,100)
			// }
		</script>
	</body>

2/绘制视频 

    <body>
		<canvas id="canvars1" width="800" height="600"></canvas>
		<video width="800" height="" src="./news.mp4" controls="controls">	
		</video>
		<script type="text/javascript">
			var video = document.querySelector('video')
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')
				
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			var interId;
			video.onplay = function(){
				interId = setInterval(function(){
					// ctx.clearRect(0,0,800.600)
					ctx.fillRect(0,0,800,600)
					ctx.drawImage(video,0,70,800,440)
					ctx.fill()
					ctx.font = '20px 微软雅黑'
					ctx.strokeStyle = 'chartreuse'
					ctx.strokeText('..1打码',50,50)
				},16)
			}
			video.onpause = function(){
				clearInterval(interId)
			}
		</script>
	</body>

三  .canvas绘制时间 

    <body>
		<!-- canvas三要素 设置画布 id,width,height -->
		<canvas id="canvars1" width="800" height="600"></canvas>
			
		<script type="text/javascript">
			var canvars1 = document.querySelector('#canvars1')	
			var ctx = canvars1.getContext('2d')
	
			function renderClock(){
				ctx.clearRect(0,0,800,600)
				// 保留原始状态
				ctx.save()
				// 将坐标移动到画布的中央
				ctx.translate(400,300)
				ctx.rotate(-2*Math.PI/4)
				ctx.save()
				
				// 绘制表盘
				ctx.beginPath()
				ctx.arc(0,0,200,0,2*Math.PI)
				ctx.strokeStyle='darkgrey'
				ctx.lineWidth = 10
				ctx.stroke()
				ctx.closePath()
						
				// 绘制分钟刻度
				for(var j =0; j<60; j++) {
					ctx.rotate(Math.PI/30)
					ctx.beginPath()
					ctx.moveTo(180,0)
					ctx.lineTo(190,0)
					ctx.lineWidth = 2
					ctx.strokeStyle = 'orangered'
					ctx.stroke()
					ctx.closePath()
				}
				ctx.restore()
				ctx.save()	
						
				// 绘制时针刻度
				for(var i =0; i<12; i++) {
					ctx.rotate(Math.PI/6)
					ctx.beginPath()
					ctx.moveTo(180,0)
					ctx.lineTo(200,0)
					ctx.strokeStyle = 'darkgrey'
					ctx.lineWidth = 10
					ctx.stroke()
					ctx.closePath()
				}
				// 恢复 上一个save的位置
				ctx.restore()
				// 保留当前位置
				ctx.save()	
				
				var time = new Date()
				var hour = time.getHours()
				var min = time.getMinutes()
				var sec = time.getSeconds()
				hour = hour>12?hour-12:hour,
				console.log(hour+":"+min+":"+sec)
				
				// 绘制秒针
				ctx.beginPath()
				// 根据秒针的时间进行旋转
				ctx.rotate(2*Math.PI/60*sec)
				ctx.moveTo(-30,0)
				ctx.lineTo(170,0)
				ctx.lineWidth = 2
				ctx.strokeStyle = 'orangered'
				ctx.stroke()
				ctx.closePath()
				ctx.restore()
				ctx.save()	
				
				// 绘制分针
				ctx.beginPath()
				// 根据分针的时间进行旋转
				ctx.rotate(2*Math.PI/60*min+2*Math.PI/3600*sec)
				ctx.moveTo(-20,0)
				ctx.lineTo(150,0)
				ctx.lineWidth = 4
				ctx.strokeStyle = 'greenyellow'
				ctx.stroke()
				ctx.closePath()
				ctx.restore()
				ctx.save()	
				
				// 绘制时针
				ctx.beginPath()
				// 根据时针的时间进行旋转
				ctx.rotate(2*Math.PI/12*hour+2*Math.PI/60/12*min+2*Math.PI/12/60/60*sec)
				ctx.moveTo(-10,0)
				ctx.lineTo(100,0)
				ctx.lineWidth = 6
				ctx.strokeStyle = 'lightcoral'
				ctx.stroke()
				ctx.closePath()
				
				
				ctx.beginPath()
				ctx.arc(0,0,10,0,2*Math.PI)
				ctx.fillStyle='aqua'
				ctx.fill()
				ctx.closePath()
				ctx.restore()
				ctx.restore()	
			}
			
			setInterval(function() {
				renderClock()
			},1000)
			
		</script>	
	</body>

四  .刮刮卡 
1/新图的 叠加模式 
        
       <body>
		<!-- canvas三要素 设置画布 id,width,height -->
		<canvas id="canvars1" width="600" height="600">	
		</canvas>
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			// 第一个红色为目标图像
			ctx.fillStyle = 'aquamarine'
			ctx.fillRect(100,100,200,200)
			
			// 默认值为source-over,源图像叠加在目标图像上
			//ctx.globalCompositeOperation='source-over'
			// source-atop 源图像在目标图像外的不显示
			// ctx.globalCompositeOperation ='source-atop'
			// source-in 显示两个叠加的内容
			// ctx.globalCompositeOperation ='source-in'
			// source-out 源图像在目标图像外的显示
			// ctx.globalCompositeOperation ='source-out'
			// description-over 在目标图像上显示源图像
			// ctx.globalCompositeOperation ='destination-over'
			// destination-atop 目标图像在源图像外的不显示
			// ctx.globalCompositeOperation ='destination-atop'
			// destination-in 目标图像在源图像外的显示
			// ctx.globalCompositeOperation ='destination-in'
			// destination-out 目标图像在源图像外的显示
			// ctx.globalCompositeOperation ='destination-out'
			// lighter = xor 显示两个图像除了重叠的部分
			// ctx.globalCompositeOperation ='lighter'
			// copy 只显示源图像
			// ctx.globalCompositeOperation ='copy'						
			// 第二个为源图像
			ctx.fillStyle = 'crimson'
			ctx.fillRect(200,200,200,200)
		</script>

2/刮刮卡 

    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <title></title>
            <style type="text/css">
                #ggk {
                    width: 400px;
                    height: 100px;
                    position: relative;
                }
                .jp {
                    width: 400px;
                    height: 100px;
                    position: absolute;
                    top: 0;
                    left: 0;
                    text-align: center;
                    line-height: 100px;
                    color: crimson;
                    font-size: 30px;
                }
			
			#canvars1{
				width: 400px;
				height: 100px;
				position: absolute;
				top: 0;
				left: 0;
			}
			
			
		</style>
	</head>
	<body>
		<div id="ggk">
			<div class="jp">谢谢惠顾</div>
			<!-- canvas三要素 设置画布 id,width,height -->
			<canvas id="canvars1" width="400" height="100">	
			</canvas>
		</div>
		
		<script type="text/javascript">
			//1. 获取画布对象
			var canvars1 = document.querySelector('#canvars1')	
			var ggkDom = document.querySelector('#ggk')	 
			var jpkDom = document.querySelector('.jp')	 
			//2. 找到上下文对象(画笔)
			var ctx = canvars1.getContext('2d')  //webgl:3D引擎
			
			ctx.fillStyle = 'darkgrey'
			ctx.fillRect(0,0,400,100)
			
			ctx.fillStyle = '#fff'
			ctx.font = '30px 微软雅黑'
			ctx.fillText('刮刮卡',160,60)
			
			var isDraw = false
			// 默认isDraw=true,即为允许绘制
			canvars1.onmousedown = function(){
				isDraw = true
			}
			
			// 移动的时候绘制圆形,将源图像内的目标内容清除掉
			canvars1.onmousemove = function(e){
				if(isDraw) {
					var x = e.pageX - ggkDom.offsetLeft
					var y = e.pageY - ggkDom.offsetTop
					ctx.globalCompositeOperation='destination-out'
					ctx.arc(x,y,20,0,2*Math.PI)
					ctx.fill()
				}
			}
			
			canvars1.onmouseup= function(){
				isDraw = false
			}
			
			var jpArr = [{content:'一等奖:IphoneXs',p:0.1},{content:'二等奖:Ipadpro',p:0.2},{content:'三等奖:Iwatch',p:0.3}]
			var randomNum = Math.random()
			console.log(randomNum)
			
			if(randomNum<jpArr[0].p) {
				jpkDom.innerHTML = jpArr[0].content
			}
			else if(randomNum<jpArr[1].p+jpArr[0].p) {
				jpkDom.innerHTML = jpArr[1].content
			}
			else if(randomNum<jpArr[2].p+jpArr[1].p+jpArr[0].p) {
				jpkDom.innerHTML = jpArr[2].content
			}
			
		</script>
	</body>
    </html>


四  .canvas实现画板


    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="utf-8">
            <title></title>
		
		<style type="text/css">
			*{
				padding: 0;
				margin: 0;
				box-sizing: border-box;
			}
			body{
				width: 100vw;
				height: 100vh;
				display: flex;
				flex-direction: column;
				justify-content: flex-start;
			}
			
			.caidan {
				height: 100px;
				width: 100vw;
				display: flex;
				border-bottom: 3px solid #ccc;
				justify-content: space-around;
				align-items: center;
			}
			
			#canvars1{
				flex: 1;
				width: 100vw;
			}
			
			.btn {
				width: 120px;
				height: 40px;
				border: 1px solid #ccc;
				border-radius: 20px;
				text-align: center;
				line-height: 40px;
				color: #999;
			}
			
			.btn,.btn2{
				width: 120px;
				height: 40px;
				border: 1px solid #ccc;
				border-radius: 20px;
				text-align: center;
				line-height: 40px;
				color: #999;
			}
			
			.btn.active {
				box-shadow: 0 0 20px deepskyblue;
				border: 1px solid deepskyblue;
			}
			
		</style>
		
	</head>
	<body>
		<!-- 将画面功能:能够拖动鼠标在页面内绘图,能够设置画笔的粗细,设置画笔的颜色
			能够在任意位置绘制圆形,随意定制大小
			能够在任意位置绘制矩形,随意定制大小
		 -->
		 <div class="caidan">
			<div class="btn">橡皮擦</div>
		 	<div class="btn" id="huabi">圆笔</div>
		 	<div class="btn" id="rect">矩形</div>	
		 	<div class="btn">圆形</div>
			<div class="btn">线段粗细</div>
			<div class="btn">画笔颜色</div>
			<div class="btn2"><input type="color" name="color" id="color" value="#000000"></input></div>
			<div class="btn2 download">
				<a href="" download="download">下载图片</a>
			</div>
		 </div>
		 
		 <canvas id="canvars1"></canvas>
		 <script type="text/javascript">
			var allBtn = document.querySelectorAll('.btn')
		 	var canvars1 = document.querySelector('#canvars1')
			var ctx = canvars1.getContext('2d')
			// 设置canvas的宽度和高度
			canvars1.setAttribute('width',canvars1.offsetWidth)
			canvars1.setAttribute('height',canvars1.offsetHeight)
			var huaban = {
				type:'none',
				isDrow:false,
				beginX:0,
				beginY:0,
				imageDate:null,
				// 画笔
				huabiFn:function(e){
					var x = e.pageX-canvars1.offsetLeft
					var y = e.pageY-canvars1.offsetTop
					ctx.beginPath()
					ctx.arc(x,y,3,0,2*Math.PI)
					ctx.fill()
					ctx.closePath()
				},
				// 画矩形
				rectFn:function(e){
					var x = e.pageX-canvars1.offsetLeft
					var y = e.pageY-canvars1.offsetTop
					ctx.clearRect(0,0,canvars1.offsetWidth,canvars1.offsetHeight)
					if(huaban.imageDate != null)  {
					ctx.putImageData(huaban.imageDate,0,0,0,0,canvars1.offsetWidth,canvars1.offsetHeight)
					}
					ctx.beginPath()
					ctx.rect(huaban.beginX,huaban.beginY,x-huaban.beginX,y-huaban.beginY)
					ctx.stroke()
					ctx.closePath()
				}
			}
		 
			var huabiBtn = document.querySelector('#huabi')
			huabiBtn.onclick = function(){
				allBtn.forEach(function(item,i) {
					item.classList.remove('active')
				})
				huabiBtn.classList.add('active')
				huaban.type='huabi'
			}
			
			var rectBtn = document.querySelector('#rect')
			rectBtn.onclick = function(){			
				allBtn.forEach(function(item,i) {
					item.classList.remove('active')
				})
				rectBtn.classList.add('active')
				huaban.type='rect'
			}
			
			// 找到下载按钮
			var downloadBtn = document.querySelector('.download')
			downloadBtn.onclick = function(){
				var url = canvars1.toDataURL()
				console.log(url)
				var aDom = document.querySelector('.download a')
				aDom.setAttribute('href',url)
				// 点击自动下载
				// aDom.click()
			}
			
			// 监听鼠标按下事件
			canvars1.onmousedown = function(e){
				huaban.isDrow = true
				if(huaban.type == "rect") {
					var x = e.pageX-canvars1.offsetLeft
					var y = e.pageY-canvars1.offsetTop
					huaban.beginX = x
					huaban.beginY = y
				}
			}
			// 监听鼠标抬起事件
			canvars1.onmouseup = function(){
				// 把画板上所有数据保留
				huaban.imageDate = ctx.getImageData(0,0,canvars1.offsetWidth,canvars1.offsetHeight)
				huaban.isDrow = false
			}
			
			canvars1.onmousemove = function(e){
				if(huaban.isDrow) {
					var strFn = huaban.type+'Fn'
					// console.log(strFn)
					huaban[strFn](e)
				}
			}
			
		 
		 </script>
	</body>
</html>






