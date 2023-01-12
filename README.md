# ninja-run-macromedia-flash-
A simple game built with the help of macromedia flash only !.

I will also give the relevant codes used in the game for the character to move and all the objects , buttons , starting and ending.

the codes are not exactly used the way it is written over here there are some changes to it such as the name of object to move is the ball
but in the game I have made a character and the instance name is changed to ( char ).
Like this there are several other changes to the code but If a person has a basic knowledge of the macromedia flash he can
easily refer to the codes here and modifiy the same to his/her purpose.

1. char actions: registration number ( 8 )

	onClipEvent (load) {
	var ground:MovieClip = _root.ground;
	var grav:Number = 0;
	var gravity:Number = 2;
	var speed:Number = 7;
	var maxJump:Number = -12;
	var touchingGround:Boolean = false;
	}
	onClipEvent (enterFrame) {
	_y += grav;
	grav += gravity;
	while (ground.hitTest(_x, _y, true)) {
	_y -= gravity;
	grav = 0;
	}
	if (ground.hitTest(_x, _y+5, true)) {
	touchingGround = true;
	} else {
	touchingGround = false;
	}
	if (Key.isDown(Key.RIGHT)) {
	_x += speed;	
	}
	if (Key.isDown(Key.LEFT)) {
	_x -= speed;
	}
	if (Key.isDown(Key.UP) && touchingGround) {
	grav = maxJump;
	}
	if (ground.hitTest(_x+(_width/2), _y-(_height/2), true)) {
	_x -= speed;
	}
	if (ground.hitTest(_x-(_width/2), _y-(_height/2), true)) {
	_x += speed;
	}
	if (ground.hitTest(_x, _y-(height), true)) {
	grav = 3;
	}
	}

2. Ground Registration number ( 5 )


3. restartBox actions: Registration number ( 2 )

	onClipEvent(enterFrame){
	this._visible = false;
	if(_root.char.hitTest(this)){
	_root.char._x =;
	_root.char._y =;
	}
	}


4. vcam actions:

	onClipEvent (enterFrame) {
	_y += (_root.char._y-_y)/5;
	_x += (_root.char._x-_x)/5;
	}

5. The ball does not directly goes from one scene to another because gotoAndStop does not work 
   directly and only works on button for that we still apply the same code " GoToAndStop " 
   but with a parameter and we apply the " frame name " also and the code for that is:
   
   _root.goToAndStop("Frame Name");


6.
rotation obstacle

onClipEvent(enterFrame) {
 this._rotation += 2;
 if(_root.char.hitTest(this)) {
  _root.vcam.hp.nextFrame();
 }
}

7.
score

onClipEvent (enterFrame) {
if (_root.char.hitTest(this)) {
_root.score += 10;
unloadMovie(this);
}
}


Thank you !
