# Analog and Digital Switch
* I created the circuit, with 2 LEDs, one analog and one digital switch.
* Firts of all, I want to say that I am very confused while working with hardware and software. Since it is the first time I use Arduino, I am not acquainted with many things and have mix in my head. However, I feel like the more I work with it the more I explore. 
* Doing this assignment seemed very difficult at first. After the clarification I understood that I need 2 LEDs and they have to be controlled in 2 different ways. So one was a button and another one - the sensor.
* I first tried the tempreture sensor, but the values it was giving were very confusion. Because of the small range (it was like 2 scale factors) was too smal for the LED, so I could not control it's brightness.
* While working in the IM lab I found another sensor - force sensor and connected it to my circuit.
![Here is how my circuit looks like](https://github.com/lizadat/Intro_to_IM/blob/bdc160e2d64ec8879a2dd916f812a29b07c8a422/Week9/photo_2022-04-05%2009.05.28.jpeg)
![Here is the screenshot of the code](https://github.com/lizadat/Intro_to_IM/blob/e2663770a07e1134d5b95f68ad52b29ffd324b04/Week9/Screen%20Shot%202022-04-05%20at%209.26.01%20AM.png)
* Everything worked the way I wanted, but the problem is that while using the force sensor, you need to press it super hard to use its full ramge (1023), but with all my strength I could get only to the middle. After a few manipulations (dividing the value by 2) with the force sensor value I created a map, that transfered the values of ssensor to the values 0-255 for the light. Unfortunately, it does not work that precisely with the LED, you cannot see huge changes in the brighness, but it is seen a little bit.
![This is the working circuit](https://github.com/lizadat/Intro_to_IM/blob/bdc160e2d64ec8879a2dd916f812a29b07c8a422/Week9/photo_2022-04-05%2009.05.30.jpeg)
* For the digital switch, to make it more creative, I made the LED be on and off with a particular timings when the button is pressed. It goes on for half of the second, then 1/10 of the second off and repeats. 
* Later on I also found another force sensor, which is much smaller. Even though I do not know the difference (either it does not have a difference at all or the difference is in the range) I decided to use this one because of its convenience. The changes in my LED were not noticed.
![The circuit with another force sensor](https://github.com/lizadat/Intro_to_IM/blob/bdc160e2d64ec8879a2dd916f812a29b07c8a422/Week9/photo_2022-04-05%2009.05.38.jpeg) 
