# How to write a good code and refactor bad ones
- https://betterprogramming.pub/the-art-of-refactoring-5-tips-to-write-better-code-3bc1f6f7689
1. Do not use switch statements, use objects.
```
const pokemon = {
    Water: 'Squirtle',
    Fire: 'Charmander',
    Plant: 'Bulbasur',
    Electric: 'Pikachu'
  };

const pokemon = new Map([
    ['Water', 'Squirtle'],
    ['Fire', 'Charmander'],
    ['Plant', 'Bulbasur'],
    ['Electric', 'Pikachu']
  ]);

```

2. Make Your Conditionals Descriptive
- put your conditionals into a function

``` 

function isGameLost() {
  return (
    remaining === 0 ||
    (remaining === 1 && remainingPlayers === 1) ||
    remainingPlayers === 0
  );
}

// Our function is now much easier to understand:
function checkGameStatus() {
  if (isGameLost()) {
    quitGame();
  }
}

```

3. Use Guard Clauses to Avoid Nested If Statements
- DO NOT USE NESTED STATEMENTS
- what is a Guard Clause?
- “In computer programming, a guard is a boolean expression that must evaluate to true if the program execution is to continue in the branch in question.” — Wikipedia
```
function publishTweet(tweet) {

  if (!isLoggedIn()) {
    throw new Error('You need to log in before tweeting');
  }
  if (!tweet) {
    throw new Error("Your tweet is empty, can't publish it");
  }
  if (!isTweetDoubleChecked()) {
    throw new Error('Dont publish without double checking your tweet');
  }

  tweetIt(tweet);
}

```