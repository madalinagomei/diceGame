Dice Game
Welcome to the Dice Game! This project is a simple dice game for two players, developed using HTML, CSS, and JavaScript. The game is designed to work seamlessly on desktop, tablet, and mobile devices.

Game Rules
The Dice Game is a turn-based game for two players. The objective is to be the first player to reach 100 points. Here are the detailed rules:

Starting the Game:

Each player starts with a score of 0.
Taking a Turn:

On a player's turn, they can roll a dice as many times as they wish.
Each roll adds the rolled number to the player's current score for that turn.
Rolling a '1':

If the player rolls a '1', their current score for that turn is lost, and it becomes the other player's turn.
Holding:

A player can choose to "hold" (save their current score).
When a player holds, their current score for that turn is added to their total score, and it becomes the other player's turn.
Winning the Game:

The first player to reach or exceed 100 points in their total score wins the game.
How to Play
Start a New Game:

Click the "🔄 New game" button to reset all scores and start a fresh game.
Roll the Dice:

Click the "🎲 Roll dice" button to roll the dice.
The result will be displayed on the dice image, and the current score for that turn will be updated.
Hold Your Score:

Click the "📥 Hold" button to add your current score for that turn to your total score.
The turn then passes to the other player.
Technologies Used
HTML: For the game structure.
CSS: For styling the game, including responsive design for mobile and tablet views.
JavaScript: For the game logic, including dice rolling, score tracking, and game state management.
Features
Responsive Design: The game layout adjusts seamlessly for desktop, tablet, and mobile devices.
Interactive UI: Real-time updates to the scores and dice rolls.
Simple and Intuitive Gameplay: Easy to understand and play, with clear rules and controls.
Installation and Setup
To run this game locally on your machine, follow these steps:

Clone the Repository:

bash
Copy code
git clone https://github.com/yourusername/dice-game.git
Navigate to the Project Directory:

bash
Copy code
cd dice-game
Open index.html in your browser:

You can open the index.html file directly in your preferred web browser.
Contribution
If you want to contribute to this project, feel free to fork the repository and submit a pull request. Your contributions are always welcome!

Contact
For any questions or suggestions, please feel free to contact me at madalinagome@gmail.com .

Example Code Snippets
HTML:

html
Copy code

<main class="main">
  <section class="player player--0 player--active">
    <h2 class="name" id="name--0">Player 1</h2>
    <p class="score" id="score--0">0</p>
    <div class="current">
      <p class="current-label">Current</p>
      <p class="current-score" id="current--0">0</p>
    </div>
  </section>
  <section class="player player--1">
    <h2 class="name" id="name--1">Player 2</h2>
    <p class="score" id="score--1">0</p>
    <div class="current">
      <p class="current-label">Current</p>
      <p class="current-score" id="current--1">0</p>
    </div>
  </section>
  <img src="dice-5.png" alt="Playing dice" class="dice" />
  <div class="btn-container">
    <button class="btn btn--new">🔄 New game</button>
    <button class="btn btn--roll">🎲 Roll dice</button>
    <button class="btn btn--hold">📥 Hold</button>
  </div>
</main>
CSS:

css
Copy code
@media (max-width: 480px) {
.main {
width: 90vw;
height: 90vh;
}
.name {
font-size: 1.5rem; /_ Smaller text for mobile _/
}
.btn-container {
display: flex;
justify-content: center;
align-items: center;
}
.btn--new, .btn--roll, .btn--hold {
position: static; /_ Remove absolute positioning for mobile _/
transform: none; /_ Remove transform _/
margin: 1rem; /_ Add margin for spacing _/
}
}
JavaScript:

javascript
Copy code
const switchPlayer = function () {
document.getElementById(`current--${activePlayer}`).textContent = 0;
currentScore = 0;
activePlayer = activePlayer === 0 ? 1 : 0;
player0El.classList.toggle('player--active');
player1El.classList.toggle('player--active');
};

btnRoll.addEventListener('click', function () {
if (playing) {
const dice = Math.trunc(Math.random() \* 6) + 1;
diceEl.classList.remove('hidden');
diceEl.src = `dice-${dice}.png`;
if (dice !== 1) {
currentScore += dice;
document.getElementById(`current--${activePlayer}`).textContent = currentScore;
} else {
switchPlayer();
}
}
});

btnHold.addEventListener('click', function () {
if (playing) {
scores[activePlayer] += currentScore;
document.getElementById(`score--${activePlayer}`).textContent = scores[activePlayer];
if (scores[activePlayer] >= 100) {
playing = false;
diceEl.classList.add('hidden');
document.querySelector(`.player--${activePlayer}`).classList.add('player--winner');
document.querySelector(`.player--${activePlayer}`).classList.remove('player--active');
} else {
switchPlayer();
}
}
});
