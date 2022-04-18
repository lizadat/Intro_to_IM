# Exercises
* Exercise a: make the ellipse move horisontally, which is controlled by one sensor. I chose it to be ultrasound sensor. It measures the distance and maps into the values of the width of my canva and then draws a new ellipse on the mapped x position. I made the ellipses be drawn every time on a new background with transparency, which allows to see the previous ellipses. My range is 20 cm for the sensor, so if my hand is in its furthest - the ellipse is drawn on the right edge; in the closest - the left edge. I did not have problems with doing this exercises, however the ultrasound sensor sometimes is not precise enough, it can give very different values when the object is in front of it and not moving.
* Exercise b: I had to make something on p5.js that controls the LED brightness. First, I tried using mouseX, but it did not work out. I thought that the problem was that I move fast or something, but even when I started using the square that moves up and down changing y value, which I mapped for the red LED range, it still did not work out. After meeting with professor, we figured out that the problem was with analogWrite, but I am still not sure exactly what the problem was. As a result, it worked with my rectangle moving up and down, so I left it that way.
* The code:
* Arduino:
#define echoPin 2 
#define trigPin 3
const int LED = 9;
long duration;
int distance;

void setup() {
  pinMode(trigPin, OUTPUT); 
  pinMode(LED, OUTPUT);
  pinMode(echoPin, INPUT); 
  Serial.begin(9600); 

}

void loop() {
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2; 
//  Serial.print("Distance: ");
  Serial.println(distance);
//  Serial.println(" cm");
  int intByte = Serial.read();
  if (Serial.available() > 0) {
  // read information from p5
    int intByte = Serial.read();
    Serial.println(intByte);
    analogWrite(LED, intByte);
  }
}

* p5.js

let values = 0;
let serial;
let latestData = 0;
let bright = 0;

function setup() {
 createCanvas(windowWidth, windowHeight);
  rectMode(CENTER);
 serial = new p5.SerialPort();

 serial.list();
 serial.open('/dev/tty.usbmodem11401');

 serial.on('connected', serverConnected);

 serial.on('list', gotList);

 serial.on('data', gotData);

 serial.on('error', gotError);

 serial.on('open', gotOpen);

 serial.on('close', gotClose);
}

function serverConnected() {
 print("Connected to Server");
}

function gotList(thelist) {
 print("List of Serial Ports:");

 for (let i = 0; i < thelist.length; i++) {
  print(i + " " + thelist[i]);
 }
}

function gotOpen() {
 print("Serial Port is Open");
}

function gotClose(){
 print("Serial Port is Closed");
 latestData = "Serial Port is Closed";
}

function gotError(theerror) {
 print(theerror);
}

function gotData() {
 let currentString = serial.readLine();
  trim(currentString);
  if (currentString.length > 0) {
    if(currentString !== "hello"){
      values = currentString;
    }
  }else {
    return;
  }
}


function draw() {
  background(255, 255, 255, 10);
  let move = map(values, 0, 20, 0, width);
  fill(random(0, 255), random(0, 255), random(0, 255))
  ellipse(move, height/2, 30);
  let mapBright = floor(map(bright, -10, 450, 0, 250))
  serial.write(mapBright);
  fill(0);  
  rect(width/2, bright, 70, 80)
  print(mapBright);
}


function keyPressed() {
  if (keyCode === UP_ARROW) {
    if(bright >= 40){
      bright-=50;
    } else {
      bright = 40;
    }
  } else if (keyCode === DOWN_ARROW) {
    if(bright <= 400){
      bright+=50;
    } else {
      bright = 400;
    }
  }
}

* [The video of how it all works](https://youtu.be/FjgZsPld7Jw)

* Excercise c: Using the wind example I had to make the LED light up if the ball touches the "ground" and add something to control the side of the wind. First, I opened the code and found the places where I would have to make changes. I started with the blue LED, and it worked perfectly from the first try. However, with the wind I faced some problems. First, the p5.serialcontrol was not passing the values, even though the serial monitor was showing. The mistake was that I used Serial.print instead of Serial.println. Then everything worked. Second problem I faced was that technically the wind was controlled by digital sensor (right arrow and left arrow) in the code, but I had to use the analog sensor. Initially, I thought that with potentiometer I will be able to control it this way: if the new value is bigger then the old one - move right, the opposite - move left. Here I did not know that the wind works only when there is 2 options, but also I did not know how to make p5 remember my previous value of potentiometer. So I just ended up making a "digital sensor" from the potentiometer. If the values from it are bigger than 512, it moves right, < 512 - left. 


* The code:

* Arduino

const int LED_PIN = 7;
int POT_PIN = A0;
void setup() {
  // put your setup code here, to run once:
  pinMode(LED_PIN, OUTPUT);
  Serial.begin(9600);
}

void loop() {
  // put your main code here, to run repeatedly:
  int potReading = analogRead(POT_PIN);
  Serial.println(potReading);
  if (Serial.available() > 0) {
  int val = Serial.read();
  // read information from p5
    switch(val) {
      case 1:
        digitalWrite(LED_PIN, HIGH);
        break;
      case 0:
        digitalWrite(LED_PIN, LOW);
        break;
    }
  }
}

* p5.js

let serial;
let latestData = 0;
let velocity;
let gravity;
let position;
let acceleration;
let wind;
let drag = 0.99;
let mass = 50;
let hDampening;
let values = [];

function setup() {
  serial = new p5.SerialPort();

  serial.list();
  serial.open("/dev/tty.usbmodem11401");

  serial.on("connected", serverConnected);

  serial.on("list", gotList);

  serial.on("data", gotData);

  serial.on("error", gotError);

  serial.on("open", gotOpen);

  serial.on("close", gotClose);
  createCanvas(640, 360);
  noFill();
  position = createVector(width / 2, 0);
  velocity = createVector(0, 0);
  acceleration = createVector(0, 0);
  gravity = createVector(0, 0.5 * mass);
  wind = createVector(0, 0);
  hDampening = map(mass, 15, 80, 0.98, 0.96);
}

function serverConnected() {
  print("Connected to Server");
}

function gotList(thelist) {
  print("List of Serial Ports:");

  for (let i = 0; i < thelist.length; i++) {
    print(i + " " + thelist[i]);
  }
}

function gotOpen() {
  print("Serial Port is Open");
}

function gotClose() {
  print("Serial Port is Closed");
  latestData = "Serial Port is Closed";
}

function gotError(theerror) {
  print(theerror);
}

function gotData() {
  let currentString = serial.readLine();
  trim(currentString);
  if (currentString>0){
    values = currentString;
    print(values);
    latestData = currentString;
  } else {
    return;
  } 
}

function draw() {
  background(255);
  windPotentiometer();
  if (!windPotentiometer) {
    wind.x = 0;
    velocity.x *= hDampening;
  }
  applyForce(wind);
  applyForce(gravity);
  velocity.add(acceleration);
  velocity.mult(drag);
  position.add(velocity);
  acceleration.mult(0);
  ellipse(position.x, position.y, mass, mass);
  if (position.y > height - mass / 2) {
    // LED on
    serial.write(1);
    velocity.y *= -0.9; // A little dampening when hitting the bottom
    position.y = height - mass / 2;
  } else {
    serial.write(0);
  }
}

function applyForce(force) {
  // Newton's 2nd law: F = M * A
  // or A = F / M
  let f = p5.Vector.div(force, mass);
  acceleration.add(f);
}

function windPotentiometer() {
  // potentiometer controlled part:
  if (values<512) {
    wind.x = -1;
  }
  if (values>=512) {
    wind.x = 1;
  }
}

* [The video of how it all works](https://youtu.be/KkcJX6ad9-A)

* The circuit for the excercises:
![The circuit for the excercises](https://github.com/lizadat/Intro_to_IM/blob/82434d6945a0ebb4acf2b460eba3008a94bbb17a/Week12/Arduino-p5.js_exercises.jpeg)
