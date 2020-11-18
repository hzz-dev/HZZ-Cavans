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



































































































































