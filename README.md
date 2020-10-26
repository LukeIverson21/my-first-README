# My First README

Repo explaining README.md

## Steps to install on local computer

1. Go to [repo](https://github.com/SEI-ATL/tic-tac-toe)
2. `Fork` and `Clone` repo.
3. git clone on local machine via `Terminal`
4. `code .` into tic-tac-toe repo.


THIS IS THE `JAVASCRIPT` DATA OF MY TIC-TAC-TOE GAME
```javascript
// grab elements!


const statusDiv = document.querySelector('.status');
const clearDiv = document.querySelector('.clear');
const boxDivs = document.querySelectorAll('.box');

// game constants
const xSymbol = 'x';
const oSymbol = 'o';

// Game variables/Logic
let gameStarted = true;
let xIsNext = true;
let winner = null;


// FUNCTIONS
const letterToSymbol = (letter) => letter === 'x' ? xSymbol : oSymbol;

const handleWin = (letter) => {
  gameStarted = false;
  if (letter === 'x') {
    statusDiv.textContent = `${letterToSymbol(letter)} has won!`;
  } else {
    statusDiv.textContent = `${letterToSymbol(letter)} has won!`;
  }
};

const checkGameData = () => {
  const topLeft = boxDivs[0].classList[2];
  const topMiddle = boxDivs[1].classList[2];
  const topRight = boxDivs[2].classList[2];
  const middleLeft = boxDivs[3].classList[2];
  const middleMiddle = boxDivs[4].classList[2];
  const middleRight = boxDivs[5].classList[2];
  const bottomLeft = boxDivs[6].classList[2];
  const bottomMiddle = boxDivs[7].classList[2];
  const bottomRight = boxDivs[8].classList[2];

// CHECK WINNER
  if (topLeft && topLeft === topMiddle && topLeft === topRight) {
    handleWin(topLeft);
    boxDivs[0].classList.add('won');
    boxDivs[1].classList.add('won');
    boxDivs[2].classList.add('won');
  } else if (middleLeft && middleLeft === middleMiddle && middleLeft === middleRight) {
    handleWin(middleLeft);
    boxDivs[3].classList.add('won');
    boxDivs[4].classList.add('won');
    boxDivs[5].classList.add('won');
  } else if (bottomLeft && bottomLeft === bottomMiddle && bottomLeft === bottomRight) {
    handleWin(bottomLeft);
    boxDivs[6].classList.add('won');
    boxDivs[7].classList.add('won');
    boxDivs[8].classList.add('won');
  } else if (topLeft && topLeft === middleLeft && topLeft === bottomLeft) {
    handleWin(topLeft);
    boxDivs[0].classList.add('won');
    boxDivs[3].classList.add('won');
    boxDivs[6].classList.add('won');
  } else if (topMiddle && topMiddle === middleMiddle && topMiddle === bottomMiddle) {
    handleWin(topMiddle);
    boxDivs[1].classList.add('won');
    boxDivs[4].classList.add('won');
    boxDivs[7].classList.add('won');
  } else if (topRight && topRight === middleRight && topRight === bottomRight) {
    handleWin(topRight);
    boxDivs[2].classList.add('won');
    boxDivs[5].classList.add('won');
    boxDivs[8].classList.add('won');
  } else if (topLeft && topLeft === middleMiddle && topLeft === bottomRight) {
    handleWin(topLeft);
    boxDivs[0].classList.add('won');
    boxDivs[4].classList.add('won');
    boxDivs[8].classList.add('won');
  } else if (topRight && topRight === middleMiddle && topRight === bottomLeft) {
    handleWin(topRight);
    boxDivs[2].classList.add('won');
    boxDivs[4].classList.add('won');
    boxDivs[6].classList.add('won');
  } else if (topLeft && topMiddle && topRight && middleLeft && middleMiddle && middleRight && bottomLeft && bottomMiddle && bottomRight) {
    gameStarted = false;
    statusDiv.textContent = 'Game is tied!';
  } else {
    xIsNext = !xIsNext;
    if (xIsNext) {
      statusDiv.textContent = `${xSymbol} is next`;
    } else {
      statusDiv.textContent = `${oSymbol} is next`;
    }
  }
};
// EVENT HANDLERS
const handleClear = () => {
  xIsNext = true;
  statusDiv.textContent = `${xSymbol} is next`;
  for (const boxDiv of boxDivs) {
    boxDiv.classList.remove('x');
    boxDiv.classList.remove('o');
    boxDiv.classList.remove('won');
  }
  gameStarted = true;
};

const handleBoxClick = (e) => {
  const classList = e.target.classList;

  if (!gameStarted || classList[1] === 'x' || classList[1] === 'o') {
    return;
  }

  if (xIsNext) {
    classList.add('x');
    checkGameData();
  } else {
    classList.add('o');
    checkGameData();
  }
};


//EVENT LISTENERS

clearDiv.addEventListener('click', handleClear);

for (const boxDiv of boxDivs) {
  boxDiv.addEventListener('click', handleBoxClick)
}
```
ALL OF THE DATA ABOVE IS HOW I WANT MY GAME TO BEHAVE AND FUNCTION SORT OF LIKE THE BRAIN OF MY APPLICATION.








THIS IS MY `CSS STYLE SHEET`.
```css
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.container {
  background: red;
  margin: 50px;
  padding: 50px;
}

body {
  display: flex;
  font-family: sans-serif;
  justify-content: center;
  color: green;
}

.title {
  text-align: center;
}

.status-action {
  display: flex;
  margin-top: 25px;
  font-size: 25px;
  justify-content: space-around;
}

.clear {
  cursor: pointer;
}

.clear:hover {
  color: blue;
}

.game-grid {
  background: black;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
  grid-gap: 15px;
  margin-top: 50px;
}

.box {
  height: 200px;
  width: 200px;
  background: red;
  cursor: pointer;
}

.x::before {
  content: 'x';
  font-size: 175px;
}

.o::before {
  content: 'o';
  font-size: 175px;
}

```
ALL OF MY ELEMENTS FROM MY `HTML` LISTED IN MY `CSS` HAVE BEEN STYLED INDIVIDUALLY TO FOR MY TIC-TAC-TOE GAME.







THIS IS MY `INDEX.HTML` PAGE.
```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <link rel="stylesheet" href="/css/style.css">
  <title>Tic-Tac-Toe</title>
</head>
<body>
  <div class="container">
    <h1 class="title">Tic-Tac-Toe</h1>
    <div class="status-action">
      <div class="status">x is next</div>
      <div class="clear">clear</div>
    </div>
    <div class="game-grid">
      <div class="box top-left"></div>
      <div class="box top-middle"></div>
      <div class="box top-right"></div>
      <div class="box middle-left"></div>
      <div class="box middle middle"></div>
      <div class="box middle-right"></div>
      <div class="box bottom-left"></div>
      <div class="box bottom-middle"></div>
      <div class="box bottom-right"></div>
    </div>
  </div>
  <script src="/js/app.js"></script>
</body>
</html>
```
THIS IS THE SKELETON OF MY WEBPAGE WHERE I IDENTIFY ALL OF MY ELEMENTS BY NAME AND CLASS.






| functions | Description |
| ----------- | ----------- |
| `handleWin()` | Handle the win of either player |
| `checkGameData()` | Check the data after each turn |
| `letterToSymbol()` | inserting a `new` symbol in place of the `original letter` |
| `handleCLear` | handling the ability to clear all content and start game over |
| `handleBoxClick` | handling the ability to print `x` and `o` in select boxes |