# Steps on the project:
The project consists of 2 part: Arduino and p5.js. We decided to move together with these 2 parts but by steps. 
* Firstly, we connected motors to Arduino and made sure it worked. However, not everything worked out. The B part of the motor driver did not work. It turned out that the problem was with the brideboard. For some reason ot was not warking, so moving the wires and the motor driver to another part of the board helped.
* Secondly, the main idea of our project is to pass the information from p5.js to Arduino in order to control the car's move. As it will be controlled by the arrows, we decided to use the cases: if up, down, right or left arrow is pressed. If the up_arrow is pressed the car is supposed to move constantly, the down_arrow - reverse, back, the right_arrow - turn right, the left - left. In our plans the the side arrows are pressed only one side of the wheels move abd that is why the car is able to turn. However, it is not for sure yet, we will see how it works when we connect the car completely to Arduino and make aal the wheel move forwards and backwards.
* While using cases we cannot impact the car's speed, but maybe in the end we will change the cases to the list that will be passed to arduino in order to control it. 
* We connected 4 motors and it worked, so we continued with cutting a part of the wood, about 20 cm to 15 cm and marked where to put the motors.

![1](https://github.com/lizadat/Intro_to_IM/blob/5a4e1fe8633b72a99139593ed5e3933d52342d9a/Final_Project/1.jpeg)

* After that we glued the rest of the motors with the hot glue and put the wheels on it. It was a technical part, physical. We made sure it was all connected and we also placed the arduino and the brideboards on the car. It is all temporary, as we plan to solder and make it permanent.

![2](https://github.com/lizadat/Intro_to_IM/blob/9b3248dc2e1ed7584087e82ecc2ff30a957f56d3/Final_Project/2.jpeg)

* For now with our code only 1 wheel was working, but we were able to control it from p5.js. Also there was used the function keyPressed(), but it was one time thing: is pressed - it runs once and stops in a few seconds. The function should probably be changed to keyIsPressed().
* Also we need to make sure that all 4 wheels are controlled.
* Unfortunately, when we try to run the code, the information is passed from p5.js tp Arduino, but only 1 wheel is working. We checked the code and all the pins, but it looks like there is a problem with Motor Driver. When I tried to check it with voltage meter, I discovered that only A part of the second Motor Driver is working. 
![problem1](https://github.com/lizadat/Intro_to_IM/blob/0972802884745a68c95f42769300e80b88bc03ef/Final_Project/problem1.jpeg)

# Progress
* All previous problems were solved. Only 1 wheel was working because passing the speed in range 0-255 was not working. The lowest value I found that was running - 128. Unfortunately, we will not be able to control the speed, it will be stable.
* So now all 4 wheels are working. I made it go forward if the up_arrow is pressed, reverse is down_arrow, right - right, left - left. The information is sent from p5 in numbers 0, 1, 2, 3 and 4 and in Arduino it is divided into cases. For each case there is a specific code for the motors.
* I tried to connect ultrasonic sensor. However, here is the issue: there are not enough pins. Every motors requires 3 pins = 12 pins for all. And we need 2 more pins for the sensor. Only 0 and 1 are left but the sensor does not seemd to work with it. Here is the progress that we have so far with hardware.
 
[Video](https://youtu.be/RvP7uVFEp7E)

* I also created a communication between Arduino and p5.js, but it is useless for now, untill we figure out what to do with needed pins.
