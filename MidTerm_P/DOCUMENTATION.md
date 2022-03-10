# Midterm Project - Tetris
* For my midterm project for Introduction to Interactive Media class I created a tetris game.
![Example of the game](https://github.com/lizadat/Intro_to_IM/blob/76c84db182443ca42269a9df03cea921b0f075b9/MidTerm_P/GameExample.png)
* I was inspired by my childhood memories, when I played it on the separate device when there were no phones yet.
* It is a very interesting games which develops your attention skills and motility.
* The tetris game is where the 7 different shapes move down, you can rotate them and store on the bottom. The end is when there is no space left and the bottom reaches the top.
![How the shapes in tetris look like](https://github.com/lizadat/Intro_to_IM/blob/bc499a9d7ff83fc0d797d8ec9207f582b1b87826/MidTerm_P/TetrisShapes.png)
# My game
* I started making my game with following the series of 7 videos on how to create tetris. The code was clear to me but sometimes I faced problems with understanding the syntax. Because of that I had a few errors while coding, but it helped me to discover javascript more and to learn new functions.
[The first part of the series is here](https://www.youtube.com/watch?v=Wcb0_Q9r6i4)
* It took me around 5 days to complete it, but as a result it all worked.
* Another challenge came when I tried to implement my ideas. The first was that I wanted to have a piece of the image to be shown through the piece and the point of the game to be "recreating the image"
* An image is randomly chosen out of 4 and shown in the beginning of the game. Then the image is converted into the list for displaying it in the piece.
![My images](https://github.com/lizadat/Intro_to_IM/blob/264515f82aaa1037995f522a5113c61f0069a8b8/MidTerm_P/images.png)
* The game starts with this screen
![Start Screen](https://github.com/lizadat/Intro_to_IM/blob/264515f82aaa1037995f522a5113c61f0069a8b8/MidTerm_P/startScreen.png)
* Also to have the end of the game I had to reset the game when the last piece reaches the top. I struggled a lot with that, as in my example it was cleared up and started again, but I wanted it to quit. So after long time I came up with the algorithm and gpt help from the Unix Lad in implementing.
* The game has a sound: when the piece is moved left, right, down and when it rotates.
![Progress of the game](https://github.com/lizadat/Intro_to_IM/blob/264515f82aaa1037995f522a5113c61f0069a8b8/MidTerm_P/progress1.png)
* To stop playing before reaching the top you can press Space 
![Enter was pressed](https://github.com/lizadat/Intro_to_IM/blob/264515f82aaa1037995f522a5113c61f0069a8b8/MidTerm_P/progress2_enter.png) and if you want to continue with the progress - press space again. If you want to start over - press Enter to go back to the Beginning. If you reach the top the game will automatically stop.
* There is winning and losing in the game. The key is to recreate at least 62% of the image, which is equall to 250 boxes out of 400.
![The end](https://github.com/lizadat/Intro_to_IM/blob/264515f82aaa1037995f522a5113c61f0069a8b8/MidTerm_P/progress3_AutoEnd.png)

