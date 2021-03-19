# Alexandre de Pape - Portofolio

Welcome to my portofolio.

There's nothing better than learning by doing, and the projects I've done have made me much more comfortable writing code.

## Project 1 : Connect 4 Monte Carlo Search Tree

This project consisted in learning how the _Monte Carlo Search Tree_ (MCTS) algorithm worked and implement in for the game Connect4.

I created a frontend with the Javascript library **pixi.js** that communicates with a backend written in Golang that I learned for the occasion.

Both parts were deployed the platform **Heroku**

The game is playable at:

[connect4](https://connect4-vs-ai.herokuapp.com/)

![connect4](connect4.png)

## Source code
- Frontend: https://github.com/Maulorian/connect4_frontend
- Backend: https://github.com/Maulorian/connect4_backend

## Project 2 : Tetris Clone

I love games, and I have a big interest in thinking about how the first video games were made, because their gameplay was so simple and so awesome at the same time. With Tetris, I was intrigued by how the game mechanics worked, the collision, the rotation of pieces, and I decided to code my own.

First written in Java, I rewrote the code in Javascript and HTML Canvas to be able to deploy it on the web.

The game is playable at:

[tetris](https://pretty-tetris.herokuapp.com/html/solo.html)

![tetris](tetris.png)

## Source code
- https://github.com/Maulorian/Tetris

## Project 3 : League of Legends Highlights Creator and Uploader

I love playing League of Legends, so why not combining two things I like and learn some neat things along the way?

Some Youtube channels upload gameplay of high ELO players, but they are sometimes 50 long and that takes time to watch. So I decided that I should improve the concept by creating and uploading highlights of the best action that happend in the game, instead of the full games.

For this project I had to learn how to open programs programaticaly, how to send input to programs, and come up with an algorithm that creates a ~5min highlight video of a ~40min one.

The steps of the process are the following:

1. **Retrieves** not yet recorded Challenger Games from database (MongoDB) filled by a microservice running 24/7: https://github.com/Maulorian/RecordingsEnabler/tree/master.
2. **Processes** those games with the Riot Games API and chooses the **most relevant** player to watch by looking at kills, damages done, etc.
3. **Opens** *League of Legends* and OBS Studio (https://obsproject.com/) and sends inputs to **selects** the player, **hides** the fog of war and **records** the game.
4. **Creates** a *5-10 minutes* **highlights video** from a *30-40 minutes game* based off of the a timeline of **events** and their timestamps such as kills, deaths, epic monster kills, etc.
5. **Creates** a thumbnail image for the video based on metadata such as items, kills, runes, that will be uploaded with the video.
6. **Uploads** the video on the **Challenger Highlights** *Youtube* Channel: https://www.youtube.com/channel/UCz2zp337iZ9xkpLDACxpRHA

This project took me 2 month because of the amount of challenges that I faced
