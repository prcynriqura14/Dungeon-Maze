<!doctype>
<html>
  <head>
    <title>Video Juego Nivel 02 </title>
    <link href="../Estilos/juego.css" type="text/css" rel="stylesheet" media="screen" />
    <style>
    input:valid {background:#FFF;}
    input:invalid {background:#FFF;}
    </style>
    <script type="text/javascript">
    var boxx = 2;
    var boxy = 0;
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
	img.src= "UltimateGoblin.gif";
	
	var img3 = new Image();
	img3.src= "Orco.gif";
	
		var img4 = new Image();
	img4.src=  "llave-01.gif";
	
	var img2 = new Image();
	img2.src= "guerrero1.gif";
	
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
	
	xllave = 935;
	yllave = 150;
	
	function llaves(){
ctx.drawImage(img4,xllave,yllave,50,50);/**/
		}
	
         	x= 40; //Left
			y= 320; //Top
			function Mover(direccion)
			{
				switch (direccion.keyCode)
				{
					//Arriba
					case 38:
						y-= 10;
						img2.style.top= String(y) + "px";
					break;
					//Izquierda
					case 39:
						x+= 10;
						img2.style.left= String(x) + "px";
					break;
					
					case 40:
						y+= 10;
						img2.style.top= String(y) + "px";
					break;
					
					case 37:
						x-= 10;
						img2.style.left= String(x) + "px";
					break;								
				}
								
			}
	
    function init(direccion){
      var h;
      ctx = document.getElementById('canvas').getContext('2d');
	  grad = ctx.createLinearGradient(boxx,boxy,boxx+boxwidth, boxy+boxheight);
      for (h=0; h < hue.length ;h++){
        color = 'rgb('+hue[h][0]+','+hue[h][1]+','+hue[h][2]+')';
        grad.addColorStop(h*1/6,color);      
      }
      ctx.fillStyle = grad;
      ctx.lineWidth = ballrad;
	  
	  //Mover(direccion);
      
      moveball();
	  
	  
	        setInterval(moveball,65);
      }
    
	
	var i = 0;
	var m = false;
    function moveball(direccion){
      ctx.clearRect(boxx,boxy,boxwidth,boxheight);
      moveandcheck();
      ctx.drawImage(img,ballx-ballrad,bally-ballrad,2*ballrad,2*ballrad);/**/
	  ctx.drawImage(img3,ballx-ballrad+20,bally-ballrad-100,2*ballrad,2*ballrad);/**/
      ctx.fillRect(boxx,boxy,ballrad,boxheight);
      ctx.fillRect(boxx+boxwidth-ballrad, boxy, ballrad, boxheight);
      ctx.fillRect(boxx,boxy,boxwidth,ballrad);
      ctx.fillRect(boxx,boxy+boxheight-ballrad,boxwidth,ballrad);
	  	  ctx.drawImage(img2,x,y,62,62); 
		  
		  llaves();
		  
		  
		  document.getElementById("posicion").innerHTML = img2.style.left;
		  document.getElementById("contador").innerHTML = i;
		  if (m == true){
			  document.getElementById("winner").style.visibility = "visible";
		  document.getElementById("winner").innerHTML = "SIGUIENTE NIVEL ";
		  }
		  
		  if (img2.style.left == "870px" && i == 0 ){
			  i++
			  m = true
			  }
			  if ( i >= 1 ){  
			  i++
			  }			  
			  if (m == true && i == 10 ){	
			  	  
					  
var pagina=" VideoJuego 1.3.html "
location.href=pagina 
}       



document.getElementById("puntos").innerHTML = 'img2: ' + img2.style.top + '|| img: ' + ctx.img;

if(img2.style.top > img.style.left && img2.style.top > img.style.top && img2.style.top < img.style.right && img2.style.top < img.style.bottom){
	
				  	  
					  
var pagina=" VideoJuego 1.2.html "
location.href=pagina 
	}



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
    
<script type="text/javascript">
			
		</script>
        
    </head>
    <body onLoad="init(event);" onkeyup="Mover(event);">
    <bgsound src="#" loop="-1">
    
    <div id="puntos"></div>
     
    <div id="posicion">
    </div>
    
        <div id="contador">
    </div>
    <div id = "winner"></div>
    <div id="container">
    <canvas id="canvas" width="1000" height="540">
      Your browser doesn't support canvas element, so meditate about that
    </canvas>
    
    <br/>
    </div>
    </body>
    </html>
    
