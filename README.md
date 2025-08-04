# React Tenzies Game

A simple and fun Tenzies dice game built with React.

## Overview

Tenzies is a dice game where the goal is to roll until all dice show the same number. You can click on individual dice to "hold" their value between rolls. Once all dice are held and show the same number, you win!

This project demonstrates React hooks (`useState`, `useEffect`, `useRef`), component-driven design, and basic game logic.

## Features

- Roll 10 dice with a click
- Hold individual dice to keep their values
- Win detection when all dice are held and have the same value
- Confetti animation on winning
- Focus management for accessibility (button focuses on win)
- Simple and clean UI

## How to Play

1. Click **Roll** to roll the dice.
2. Click any die to hold it at its current value.
3. Keep rolling and holding until all dice show the same number.
4. When you win, click **New Game** to start over.

## Technologies Used

- React (functional components and hooks)
- nanoid for unique IDs
- react-confetti for win animation

## Running Locally

1. Clone the repository
2. Run `npm install` to install dependencies
3. Run `npm start` to start the development server

## Code Snippet

Here’s a glimpse of the core game logic:

```js
const gameWon = dice.every(die => die.isHeld) &&
    dice.every(die => die.value === dice[0].value);

function rollDice() {
    if (!gameWon) {
        setDice(oldDice => oldDice.map(die =>
            die.isHeld ? die : { ...die, value: Math.ceil(Math.random() * 6) }
        ));
    } else {
        setDice(generateAllNewDice());
    }
}
