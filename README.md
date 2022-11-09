# CC_midterm_JuneLiu
//June Liu Midterm Project
var hr, m, sec;
var r; // radius
var size_max = 110;
var size_min = 50;
var butterfly = [];
var c0,c1,c2,c3,c4,c5,c6,c7;
// var c = ['#daffe0','#ffff4b','#ffa626','#d73536','#37c03a','#5b34c5','#941214','#3fe2e7'] //background
var c;

function setup() {
	createCanvas(600, 600);
	angleMode(DEGREES); // changes current mode to degrees
	rectMode(CENTER);
	
	c0 = color('rgb(218,255,224)');
	c1 = color('rgb(255,255,75)');
	c2 = color('rgb(255,166,38)');
	c3 = color('rgb(215,53,54)');
	c4 = color('rgb(55,192,58)');
	c5 = color('rgb(91,52,197)');
	c6 = color('rgb(148,18,20)');
	c7 = color('rgb(63,226,231)');
	c = [c0,c1,c2,c3,c4,c5,c6,c7];
	
	butterfly[0] = new Butterfly(0, -220, size_min,0);
	butterfly[1] = new Butterfly(220, 0, size_min,1);
	butterfly[2] = new Butterfly(0, 230, size_min,2);
	butterfly[3] = new Butterfly(-220, 0, size_min,3);

	sec = 0;
	frameRate(0.5);
}

function draw() {
	hr = hour();
	m = minute();
	r = height/2;	
	
	//background
	if(sec==0){
		background('rgb(62,120,144)');
		noStroke();
		fill('rgb(235,245,250)');
		rect(300,550,600,100);
		for(var i =0; i<20 ;i++){
			circle(random()*width,random()*height,random()*30);
		}
	}else if(sec==15){
		background('rgb(127,200,220)');
		noStroke();
		fill('rgb(34,165,40)');
		rect(300,550,600,100);
		//tree
		var tree_x=160;
		var tree_y=470;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(34,165,40)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
		
		var tree_x=450;
		var tree_y=460;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(34,165,40)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
		
		var tree_x=220;
		var tree_y=480;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(34,165,40)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
		
	}else if(sec==30){
		background('rgb(160,210,240)');
		noStroke();
		fill('rgb(30,110,150)');
		rect(300,550,600,100);
		fill('rgb(250,150,70)');
		circle(500,100,70);
	}else if(sec==45){
		background('rgb(255,240,190)');
		noStroke();
		fill('rgb(255,166,70)');
		rect(300,550,600,100);
		//tree
		var tree_x=160;
		var tree_y=470;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(255,166,70)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
		
		var tree_x=450;
		var tree_y=460;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(255,166,70)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
		
		var tree_x=220;
		var tree_y=480;
		fill('rgb(140,100,35)');
		rect(tree_x,tree_y,30,100);
		fill('rgb(255,166,70)');
		triangle(tree_x, tree_y-60, tree_x-50, tree_y-10, tree_x+50, tree_y-10);
		triangle(tree_x, tree_y-100, tree_x-50, tree_y-50, tree_x+50, tree_y-50);
		triangle(tree_x, tree_y-140, tree_x-50, tree_y-90, tree_x+50, tree_y-90);
	}
	
	//clock
	translate(300,300);
	rotate(-90); // makes clock upright	
	
	strokeWeight(20); // strokeWeight - sets width of stroke
	stroke(c[3]);
	// fill(c[0]);
	noFill();
	var secAngle = map(sec, 0, 60, 0, 360); // map(value, start1, stop1, start2, stop2)
	arc(0, 0, r, r, 0, secAngle);
	
	stroke(c[4]);
	noFill();
	var minAngle = map(m, 0, 60, 0, 360);
	arc(0, 0, r-50, r-50, 0, minAngle);	
	
	push();
	rotate(secAngle);
	stroke(c[6]);
	strokeWeight(4);
	line(0, 0, 100, 0);
	pop();
	
	push();
	rotate(90);
	for (i = 0; i < 4; i++) {
		butterfly[i].paint();
	}
	pop();
	
	sec += 15;
	if(sec>45){
		sec =0;
	}

}

class Butterfly{
	constructor(startPosX, startPosY, size,kind) { 
		this.X = startPosX;
		this.Y = startPosY; 
		this.size = size;
		this.kind = kind;
	}
	
	paint(){
		var quadx = this.X;
		var quady = this.Y;
		var quadsize = this.size;
		
		if(this.kind == 0){
			if(sec==0){
				this.size = size_max;
			}else{
				this.size = size_min;
			}
			
			stroke(c[1]);
			strokeWeight(1);
			fill(c[2]);
			ellipse(this.X,this.Y,this.size/2,this.size);
			fill(c[3]);
			circle(this.X-this.size/8,this.Y+this.size/8,this.size/6);
			circle(this.X+this.size/8,this.Y-this.size/8,this.size/6);
			
		}
		else if(this.kind == 1){
			if(sec==15){
				this.size = size_max;
			}else{
				this.size = size_min;
			}
			
			stroke(c[1]);
			strokeWeight(1);
			fill(c[4]);
			ellipse(this.X-this.size,this.Y,this.size/3,this.size/2);
			fill(c[3]);
			circle(this.X-this.size,this.Y+this.size/16,this.size/12);
			circle(this.X-this.size,this.Y-this.size/16,this.size/12);
			fill(c[4]);
			ellipse(this.X-this.size/4*3,this.Y-this.size/6,this.size/3,this.size/2);
			fill(c[3]);
			circle(this.X-this.size/4*3-this.size/16,this.Y-this.size/6+this.size/16,this.size/12);
			circle(this.X-this.size/4*3+this.size/16,this.Y-this.size/6-this.size/16,this.size/12);
			fill(c[4]);
			ellipse(this.X-this.size/2,this.Y-this.size/3,this.size/3,this.size/2);
			fill(c[3]);
			circle(this.X-this.size/2-this.size/16,this.Y-this.size/3+this.size/16,this.size/12);
			circle(this.X-this.size/2+this.size/16,this.Y-this.size/3-this.size/16,this.size/12);
			fill(c[4]);
			ellipse(this.X-this.size/4,this.Y-this.size/6,this.size/3,this.size/2);
			fill(c[3]);
			circle(this.X-this.size/4-this.size/16,this.Y-this.size/6+this.size/16,this.size/12);
			circle(this.X-this.size/4+this.size/16,this.Y-this.size/6-this.size/16,this.size/12);
			fill(c[4]);
			ellipse(this.X,this.Y,this.size/3,this.size/2);
			fill(c[3]);
			circle(this.X-this.size/16,this.Y+this.size/16,this.size/12);
			circle(this.X+this.size/16,this.Y-this.size/16,this.size/12);
			stroke(c[5]);
			strokeWeight(2);
			quadx = this.X+this.size/4-this.size/16;
			quady = this.Y+this.size/16-this.size/2.5;
			line(quadx,quady,quadx,quady+this.size/4);
			stroke(c[1]);
			strokeWeight(1);
			fill(c[3]);
			circle(quadx,quady,this.size/10);
			stroke(c[5]);
			strokeWeight(2);
			quadx = this.X+this.size/4+this.size/10;
			quady = this.Y+this.size/16-this.size/3;
			line(quadx,quady,quadx,quady+this.size/4);
			stroke(c[1]);
			strokeWeight(1);
			fill(c[3]);
			circle(quadx,quady,this.size/10);
			fill(c[3]);
			ellipse(this.X+this.size/4,this.Y+this.size/16,this.size/3,this.size/2);
			fill(c[4]);
			quadx = this.X+this.size/4-this.size/16;
			quady = this.Y+this.size/16;
			quadsize = this.size/16;
			quad(quadx-quadsize,quady,quadx,quady-quadsize,quadx+quadsize,quady,quadx,quady+quadsize);
			quadx = this.X+this.size/4+this.size/6;
			quady = this.Y+this.size/16;
			quadsize = this.size/10;
			quad(quadx-quadsize,quady,quadx,quady-quadsize,quadx+quadsize,quady,quadx,quady+quadsize);
			fill(c[5]);
			quadx = this.X+this.size/4+this.size/16;
			quady = this.Y+this.size/16+this.size/8;
			quadsize = this.size/16;
			triangle(quadx,quady-quadsize,quadx-quadsize,quady,quadx+quadsize,quady);

			

			
		}
		else if(this.kind == 2){
			if(sec==30){
				this.size = size_max;
			}else{
				this.size = size_min;
			}
			
			quadx = this.X;
			quady = this.Y;
			quadsize = this.size/5;
			
			stroke(c[5]);
			strokeWeight(quadsize/4);
			line(quadx+quadsize/2.5,quady-quadsize*2.2,quadx+quadsize/2.5,quady-quadsize*3.5);
			line(quadx+quadsize/2.5-quadsize/2,quady-quadsize*3.5,quadx+quadsize/2.5+quadsize/2,quady-quadsize*3.5);
			fill(c[6]);
			stroke(c[6]);
			strokeWeight(quadsize/16);
			quad(quadx,quady-quadsize*1.5,quadx-quadsize/2,quady,quadx,quady+quadsize*1.5,quadx+quadsize*2,quady-quadsize*0.8);
			triangle(quadx,quady+quadsize*1.5,quadx+quadsize*2,quady-quadsize*0.8,quadx+quadsize,quady+quadsize*2.5);
			fill(c[2]);
			stroke(c[2]);
			triangle(quadx,quady-quadsize*1.5,quadx+quadsize*2,quady-quadsize*0.8,quadx+quadsize/2.5,quady-quadsize*2.2);
			fill(c[3]);
			stroke(c[1]);
			circle(quadx,quady,quadsize/2);
			circle(quadx+quadsize*1.2,quady-quadsize*0.5,quadsize/2);
			circle(quadx+quadsize*0.8,quady+quadsize*0.6,quadsize/2);
			
			
			
		}
		else if(this.kind == 3){
			if(sec==45){
				this.size = size_max;
			}else{
				this.size = size_min;
			}
			
			quadx = this.X;
			quady = this.Y;
			quadsize = this.size;
			
			fill(c[7]);
			stroke(c[2]);
			strokeWeight(quadsize/40);
			triangle(quadx,quady,quadx+quadsize,quady-quadsize,quadx+quadsize*0.3,quady-quadsize*0.7);
			fill(c[4]);
			triangle(quadx,quady,quadx+quadsize,quady-quadsize,quadx+quadsize*0.8,quady-quadsize*0.2);
			
			fill(c[7]);
			stroke(c[2]);
			strokeWeight(quadsize/80);
			triangle(quadx,quady,quadx+quadsize*1.3,quady-quadsize*0.5,quadx+quadsize*1.5*0.3,quady-quadsize*0.6*0.7);
			fill(c[4]);
			triangle(quadx,quady,quadx+quadsize*1.3,quady-quadsize*0.5,quadx+quadsize*0.8,quady+quadsize*0.1);
			
			fill(c[5]);
			stroke(c[2]);
			push();
			translate(quadx,quady);
			rotate(45);
			rect(0,0,quadsize*0.8,quadsize/8,quadsize/16);
			fill(c[2]);
			rect(0,0,quadsize*0.1,quadsize/8);
			rect(quadsize*0.15,0,quadsize*0.05,quadsize/16);
			rect(-quadsize*0.15,0,quadsize*0.05,quadsize/16);
			fill(c[5]);
			stroke(c[2]);
			circle(-quadsize*0.4,0,quadsize*0.3);
			fill(c[4]);
			rect(-quadsize*0.4,0-quadsize*0.1,quadsize*0.15,quadsize*0.15);
			rect(-quadsize*0.4-quadsize*0.1,0+quadsize*0.1,quadsize*0.1,quadsize*0.1);
			pop();
			
			
		}
		
	}

}
