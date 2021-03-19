# Alexandre de Pape - Portofolio

Welcome to my portofolio.

There's nothing better than learning by doing, and the projects I've done have made me much more comfortable writing code.

## Project 1 : Connect 4 Monte Carlo Search Tree

This project consisted in learning how the _Monte Carlo Search Tree_ (MCTS) algorithm worked and implement in for the game Connect4.

I created a frontend with the Javascript library **pixi.js** that communicates with a backend written in Golang that I learned for the occasion.

Both parts were deployed the platform **Heroku**

The game is playable at:

[https://connect4-vs-ai.herokuapp.com/](https://connect4-vs-ai.herokuapp.com/)

![connect4](connect4.png)

## Source code
- Frontend: https://github.com/Maulorian/connect4_frontend
- Backend: https://github.com/Maulorian/connect4_backend

## Project 2 : Tetris Clone

I love games, and I have a big interest in thinking about how the first video games were made, because their gameplay was so simple and so awesome at the same time. With Tetris, I was intrigued by how the game mechanics worked, the collision, the rotation of pieces, and I decided to code my own.

First written in Java, I rewrote the code in Javascript and HTML Canvas to be able to deploy it on the web.

The game is playable at:

[https://pretty-tetris.herokuapp.com/html/solo.html](https://pretty-tetris.herokuapp.com/html/solo.html)

![tetris](tetris.png)

## Source code
- https://github.com/Maulorian/Tetris

## Project 3 : League of Legends Highlights Creator and Uploader

I love playing League of Legends, so why not combine two things I love and learn interesting things at the same time?

Some Youtube channels put online games of high ELO players, but they are sometimes 50 minutes long and it takes a long time to watch. So I decided to improve the concept by creating and uploading the best moments of the game, instead of the complete games.

For this project, I had to learn how to open programs, send input key to different programs and create an algorithm that creates a ~5 minute video from a ~40 minute video with [moviepy](https://zulko.github.io/moviepy/).

The steps of the process are the following:

1. **Find** Challenger games not yet registered in the database (MongoDB) powered by a microservice running 24 hours a day, 7 days a week: https://github.com/Maulorian/RecordingsEnabler/tree/master.
2. **Processes** these games with the Riot Games API and chooses the **most relevant** player to watch by looking at kills, damage done, etc.
3. **Operates** *League of Legends* and OBS Studio (https://obsproject.com/) and sends inputs to **select** the player, **hide** the fog of war and **record** the game.
4. **Create** a 5-10 minute video from a 30-40 minute game, based on the timeline of events and their timestamps, such as kills, deaths, epic monsters, etc.
5. **Create** a thumbnail for the video based on metadata such as objects, deaths, runes, which will be uploaded with the video.
6. **Upload** the video to the **Challenger Highlights** *Youtube* channel: https://www.youtube.com/channel/UCz2zp337iZ9xkpLDACxpRHA


During this project I faced two huge challenges.

- The first challenge I faced was reverse engineering and understanding Riot Games' viewer system. It works like this: once a game is running, people can watch it live. Once the game is over, it is no longer possible to watch it. Websites like OPGG and Porofessor actually save the packets used to recreate the replay of a game. And once you have those packets, you can open the Spectator client at any time.
This was especially useful for me, because my system was based on watching the best possible games, and watching a game takes 30-40 minutes of real time, so a limited number of games can be watched per day.
Therefore, I had to find a clever solution to optimize this valuable time. To that end, I created a microservice that scans the challenger's ranking (high elo) to see if a player is currently at the start of a game, and if yes, sends a request to the third-party website to start recording packets in its database. I would then put the match ID into a mongoDB database to save the fact that I have the ability to watch that match later.
The main program on my desktop computer would then scan the database and retrieve information about completed matches, then choose the best match to watch.

- The second challenge I faced was actually uploading the video, because Youtube's API requires you to verify your "application" in order to put your video in public, otherwise it remains locked in private. Also, Youtube has a video upload limit that only allows you to upload about a dozen videos per day.
To solve this problem, I used Selenium to automate the upload through the browser itself. This solution allowed me to download 50 videos per day.

Overall, I spent a lot of time on this project and faced many challenges, but now I feel like I can, and will, automate anything =D

![](league.png)

## Source code
- https://github.com/Maulorian/LeagueUploader

## Project 4 : Creating a multiplayer Flappy Bird in the Browser

I am a competitive gamer, and in a competitive game, players are synchronized across machines to a game state that occurs on a centralized server.

Since I like a challenge, I had to learn how such a system works. As it turns out, Game Networking is one of the hardest engineering problems out there, which is even more fascinating.

