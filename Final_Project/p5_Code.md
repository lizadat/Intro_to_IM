### A little background:
Since the idea of our game initially involved a "car moving" aspect for that, we explored different options of making this game as engaging and fun as
possible for the user. We were thinking of only making a "traveling" or "sightseeing" kind of game where the background scenery changes according to the
time change/speed or anything like that. There, we stopped on the sightseeing idea thinking it would be very interesting.

### Hence, our idea in three parts:
- Driving and controlling a car
A user will be able to control the car both in real life and in the game just by using the arrows (up, left, right, down) which adds up to the overall
experience of having a 100% user-engaging game.
- Thinking of countries:
We realized that it's going to be very interesting to add different cities and countries, while also adding the pictures of countries' most remarkable
places. Thus, we decided to choose 3 countries - travel destinations where the user can go - France, Italy and Japan.
- Adding some spice:
Adding a sightseeing experience to make the game feel more enjoyable.

### After starting the code, I had a small question to myself: what if I add some obstacles to the game so that the experience becomes more interesting? It must be really boring to just drive a car without anything exciting to that.
This is what the game looked like prior adding all the obstacles:
<img width="589" alt="Screen Shot 2022-05-13 at 20 59 03" src="https://user-images.githubusercontent.com/90758768/168332460-3ce4f453-6113-4b36-a8c6-b7042ac86d75.png">
It's definitely not the most appealing game, which made me think of the ways to make it more fun and exciting for the users to play it.
### first thing I thought of: making people (specifically, elder people) cross the road so that the car would need to avoid them.
### second thing: adding benches on the road so the user should drive the way to not crash into those benches randomly placed on the road.
To do that, I created two different classes: a separate class for people and another class for benches:
<img width="511" alt="Screen Shot 2022-05-13 at 21 02 17" src="https://user-images.githubusercontent.com/90758768/168332931-42001fe1-9df3-473a-80fb-d5732615246d.png">
<img width="529" alt="Screen Shot 2022-05-13 at 21 02 58" src="https://user-images.githubusercontent.com/90758768/168333017-2bbc3cf1-b7ba-4d0e-9362-05e1d92bd0a3.png">

### as a result, this is how the game started looking like:
<img width="1440" alt="Screen Shot 2022-05-09 at 12 33 03" src="https://user-images.githubusercontent.com/90758768/168333409-0fc3877f-babc-41d1-a29c-0220328d0ad1.png">

However, after running the code and trying to play it myself, I realized that the decision to put obstacles in those particular ways were lacking some logic to it. For example, why would grandpas walk down the road full of cars? Or why would someone place benches and trees in the middle of the road?
I know that even though game developers can be as creative in their games as possible, I still find it important to keep some logic in mind. That's why I decided to develop my idea of the obstacles and put it in a different level:
First of all, I decided to make 2 horizontal crosswalks on the roadso the grandpas will have to cross them. Here, I had some difficulties: I didn't know how to divide one class into two different constrains. For example, having half of the elder people cross just one crosswalk (constrained by particular heights) and another half of them cross another crosswalk (constrained by other values of height). 
After that, I just decided to do this: in the setup function, I just divided the class into two and assigned to different constrained and randomized heights to the same class.

<img width="500" alt="Screen Shot 2022-05-13 at 21 14 31" src="https://user-images.githubusercontent.com/90758768/168334629-4ded33c7-47a0-47c8-97a9-5059a629fc1e.png">

Instead of benches on the road, I decided to add stop signs and a traffic light which, truly, looks more logical to actually be on the road.

<img width="180" alt="Screen Shot 2022-05-13 at 21 16 25" src="https://user-images.githubusercontent.com/90758768/168334922-8ef9ebf5-7dac-474e-adf2-928a17715707.png">

## Problems faced:
### Obstacles:
When the car touches any of the obstacles, it disappears not just from one country’s screen, but from all countries, because it’s one class. For example:
<img width="507" alt="Screen Shot 2022-05-13 at 21 51 09" src="https://user-images.githubusercontent.com/90758768/168339963-bac5b02f-efe3-4a5a-ba9d-46e2fd4c3225.png">
Here, the one obstacle will go away from all other screens if you hit it in one gamescreen.

### Win/lose screen:
When you complete the journey or lose by getting too many fines, there should be a win/lost screen. But when I put it, all the elements like obstacles stay on screen. 

![WhatsApp Image 2022-05-09 at 3 56 42 PM](https://user-images.githubusercontent.com/90758768/168340598-1978f2cd-9c81-4b86-bdd7-ca6a6770561e.jpeg)

### Design
It was a bit challenging for me to make the design prettier. I’ve never been a fan of car-related games, so I didn’t know what to add.

Here's how the design turned out:
# Italy Screen
<img width="793" alt="Screen Shot 2022-05-09 at 15 54 29" src="https://user-images.githubusercontent.com/90758768/168336327-9ee02ddd-fa5e-41c6-9407-7bf93c043aac.png">

# France Screen
<img width="798" alt="Screen Shot 2022-05-09 at 15 54 48" src="https://user-images.githubusercontent.com/90758768/168336365-54401390-be78-4dbc-ae5e-d69ba61bb34b.png">

# Japan Screen
<img width="797" alt="Screen Shot 2022-05-09 at 15 54 59" src="https://user-images.githubusercontent.com/90758768/168336392-b8e26010-993c-47b7-b4cc-98a5227447c4.png">

## How I solved the problems: Obstacles:
Regarding the obstacles, I decided to leave it as it is. However, when the user goes through all the countries and restarts the game, I just increased the number of obstacles, so that the level gets higher. This way I used the "it's a feature, not a bug" mentality and it actually turned out great! When other people were playing, they particualrly enjoyed that the level was increasing every time they restarted the game. Here's a picture of my friend playing our game:

![IMG_2084](https://user-images.githubusercontent.com/90758768/168342010-9963ea94-55d4-4365-9087-3c995d7cb2c8.jpg)

## Win/lose screen:
I decided to make separate gamescreens for the "lose" and "win" screens. Here's the code for the gameScreen = 4(win screen):
<img width="581" alt="Screen Shot 2022-05-13 at 22 11 42" src="https://user-images.githubusercontent.com/90758768/168342808-7ad05c3a-b27d-49a9-972b-0a9467a2f1b9.png">

Here's the code for the gameScreen = 5 (lose screen):
<img width="588" alt="Screen Shot 2022-05-13 at 22 12 29" src="https://user-images.githubusercontent.com/90758768/168342908-1211e6c6-b75a-41d9-aac7-b551f24e1b7a.png">

At the end, I could successfully solve all the issues and connect the arduino part to the p5 game.
