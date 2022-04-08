<script>
	
	let start ={x:0,y:0};
	let end={x:0,y:0};
	let flag = false;
	let penColor='#000';
	

	function handleMouseDown(event){
		flag=true;
		start.x=event.clientX;
		start.y=event.clientY;
	}

	function hanldeMouseUp(event){
		flag=false;
	}

	function handleMouseMove(event){
		if(flag){
			end.x=event.clientX;
			end.y=event.clientY;
			
			var canvas = document.getElementById('myCanvas');
			var ctx = canvas.getContext('2d');
			var rect = canvas.getBoundingClientRect();
			var offsetX = rect.left;
			var offsetY = rect.top;

			ctx.beginPath();
			ctx.fillStyle = "#059862";
			ctx.moveTo(start.x-offsetX, start.y-offsetY);
			ctx.lineTo(end.x-offsetX, end.y-offsetY);
			
			ctx.stroke(); 	
			start.x=end.x;
			start.y=end.y;
		}
	}
</script>

<main>
	<h2>Scratch Pad - Draw Freehand</h2>
	<canvas id="myCanvas" width="800" height="600" style="width: 800px; height: 600px; border:1px solid #c3c3c3;" on:mousedown={handleMouseDown} on:mouseup={hanldeMouseUp} on:mousemove={handleMouseMove}>

	</canvas>
	
	
	
</main>

<style>
	.pallete{
		margin:0 auto;
		display: flex;
		-ms-flex-align: center;
	}
	.color-component{
		width:50px;
		height:50px;
		background-color: aqua;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>