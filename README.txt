<!doctype>
<html>
  <head>
    <title>Video Juego </title>
    <link href="../Estilos/juego.css" type="text/css" rel="stylesheet" media="screen" />
    <style>
    input:valid {background:#FFF;}
    input:invalid {background:#FFF;}
    </style>
    <script type="text/javascript">
    var boxx = 10;
    var boxy = 10;
    var boxwidth = 1000;
    var boxheight =530;
    var ballrad = 20;
    var boxboundx =  boxwidth + boxx - ballrad;
    var boxboundy = boxheight + boxy - ballrad;
    var inboxboundx = boxx + ballrad;
    var inboxboundy = boxy + ballrad;
    var ballx = 50;/*1*/
    var bally = 60;
    var ctx;
    var ballvx = 9;
    var ballvy = 8;
    var img = new Image();
	img.src= "Valkiria.gif";
	var grad;
    var color;
    var hue = [/*variación de Colores*/
      [10, 0, 0],
      [0, 0, 0],
      [0, 2, 0],
      [1, 0, 0],
      [0, 0, 0],
      [0, 0, 9]
    ];    
	
    function init(){
      var h;
      ctx = document.getElementById('canvas').getContext('2d');
      grad = ctx.createLinearGradient(boxx,boxy,boxx+boxwidth, boxy+boxheight);
      for (h=0; h < hue.length ;h++){
        color = 'rgb('+hue[h][0]+','+hue[h][1]+','+hue[h][2]+')';
        grad.addColorStop(h*1/6,color);      
      }
      ctx.fillStyle = grad;
      ctx.lineWidth = ballrad;
      
      moveball();
      setInterval(moveball,100);
      }
    
    function moveball(){
      ctx.clearRect(boxx,boxy,boxwidth,boxheight);
      moveandcheck();
      ctx.drawImage(img,ballx-ballrad,bally-ballrad,2*ballrad,2*ballrad);/**/
      ctx.fillRect(boxx,boxy,ballrad,boxheight);
      ctx.fillRect(boxx+boxwidth-ballrad, boxy, ballrad, boxheight);
      ctx.fillRect(boxx,boxy,boxwidth,ballrad);
      ctx.fillRect(boxx,boxy+boxheight-ballrad,boxwidth,ballrad);          
    }
    
    function moveandcheck(){
      
      var nballx = ballx + ballvx;
      var nbally = bally + ballvy;
      
      if (nballx > boxboundx){
        nballx = boxboundx;
        ballvx = -ballvx;
        
      }
      
      if (nballx < inboxboundx) {
        nballx = inboxboundx;
        ballvx = -ballvx;
      }
      
      if (nbally > boxboundy){
        nbally = boxboundy;
        ballvy = -ballvy;
      }
      if (nbally < inboxboundy){
        nbally = inboxboundy;
        ballvy = -ballvy;
      }
      ballx = nballx;
      bally = nbally;
    }
    function change() {
      ballvx = Number(f.hv.value);
      ballvy = Number(f.vv.value);
      return false;
    }
    </script>
    
    <script  type="text/javascript">
	 var boxx = 10;
    var boxy = 10;
    var boxwidth = 1000;
    var boxheight =530;
    var ballrad = 20;
    var boxboundx =  boxwidth + boxx - ballrad;
    var boxboundy = boxheight + boxy - ballrad;
    var inboxboundx = boxx + ballrad;
    var inboxboundy = boxy + ballrad;
    var ballx = 50;/*1*/
    var bally = 60;
    var ctx;
    var ballvx = 9;
    var ballvy = 8;
    var img = new Image();
	img.src= "Valkiria.gif";
	function init(){
      var h;
      ctx = document.getElementById('canvas').getContext('2d');
      grad = ctx.createLinearGradient(boxx,boxy,boxx+boxwidth, boxy+boxheight);
      for (h=0; h < hue.length ;h++){
        color = 'rgb('+hue[h][0]+','+hue[h][1]+','+hue[h][2]+')';
        grad.addColorStop(h*1/6,color);      
      }
      ctx.fillStyle = grad;
      ctx.lineWidth = ballrad;
      
      moveball();
      setInterval(moveball,100);
      }
    
    function moveball(){
      ctx.clearRect(boxx,boxy,boxwidth,boxheight);
      moveandcheck();
      ctx.drawImage(img,ballx-ballrad,bally-ballrad,2*ballrad,2*ballrad);/**/
      ctx.fillRect(boxx,boxy,ballrad,boxheight);
      ctx.fillRect(boxx+boxwidth-ballrad, boxy, ballrad, boxheight);
      ctx.fillRect(boxx,boxy,boxwidth,ballrad);
      ctx.fillRect(boxx,boxy+boxheight-ballrad,boxwidth,ballrad);          
    }
    
    function moveandcheck(){
      
      var nballx = ballx + ballvx;
      var nbally = bally + ballvy;
      
      if (nballx > boxboundx){
        nballx = boxboundx;
        ballvx = -ballvx;
        
      }
      
      if (nballx < inboxboundx) {
        nballx = inboxboundx;
        ballvx = -ballvx;
      }
      
      if (nbally > boxboundy){
        nbally = boxboundy;
        ballvy = -ballvy;
      }
      if (nbally < inboxboundy){
        nbally = inboxboundy;
        ballvy = -ballvy;
      }
      ballx = nballx;
      bally = nbally;
    }
    function change() {
      ballvx = Number(f.hv.value);
      ballvy = Number(f.vv.value);
      return false;
    }
	</script>
    </head>
    <body onLoad="init();">
    <div id="container">
    <canvas id="canvas" width="1024" height="768">
      Your browser doesn't support canvas element, so meditate about that
    </canvas>
    <br/>
    </div>
    </body>
    </html>
    
