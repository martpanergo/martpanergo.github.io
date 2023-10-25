<!DOCTYPE html>
<html lang="en-us">
  <head>
<style>

html {
        font-family: sans-serif;
      }

      body {
        background-Color: #00EEFF;
        width: 50%;
        max-width: 800px;
        min-width: 480px;
        margin: 0 auto;
      }
      
      .form input[type="number"] {
        width: 130px;
      }

      .lastResult {
        color: white;
        padding: 3px;
      }
      
     #number {
         background-Color:#00B2BF;
         border-radius:4px;
         border: 1px  solid gray;
     } 
      #answer {
          background-Color:#00EEFF;
          border-radius:4px;
          border:1px solid gray
      }
      
      button {
           background-color:#FA1618;
           border-radius:4px;
           border: 1px solid gray;
           width:90px;
           height:30px;
           margin-left: 132px;
      }
      
      hr {
          border:0.1px solid black;
          width:345px;
          margin-left:1px;
      }


</style>



    <meta charset="utf-8">

    <title>Number guessing game</title>

    
  </head>

  <body>
    <h1>Number Guessing Game</h1>

    <p>Try to guess the number between 1 to 100.</p>
    <p>You only have  5 trials </p>
    <hr>
   
    <div class="form">
      <label for="guessField">Enter your guess: </label>
      <input id="number" type="number" min="1" max="100" required id="guessField" class="guessField">
      <input id="answer" type="submit" value="Submit" class="guessSubmit">
    </div>
    

    <div class="resultParas">
      <p class="guesses"></p>
      <p class="lastResult"></p>
      <p class="lowOrHi"></p>
    </div>

<script>

let randomNumber = Math.floor(Math.random() * 100) + 1;
      const guesses = document.querySelector('.guesses');
      const lastResult = document.querySelector('.lastResult');
      const lowOrHi = document.querySelector('.lowOrHi');
      const guessSubmit = document.querySelector('.guessSubmit');
      const guessField = document.querySelector('.guessField');
      let guessCount = 1;
      let resetButton;

      function checkGuess() {
        const userGuess = Number(guessField.value);
        if (guessCount === 1) {
          guesses.textContent = 'Previous guesses: ';
        }

        guesses.textContent += userGuess + ' ';

        if (userGuess === randomNumber) {
          lastResult.textContent = 'Congratulations! You got it right!';
          lastResult.style.backgroundColor = 'green';
          lowOrHi.textContent = '';
          setGameOver();
        } else if (guessCount === 5) {
          lastResult.textContent = '!!!GAME OVER!!!';
          lowOrHi.textContent = '';
          setGameOver();
        } else {
          lastResult.textContent = 'Wrong!';
          lastResult.style.backgroundColor = 'red';          
          if(userGuess < randomNumber) {
            lowOrHi.textContent = 'Higher!' ;
          } else if(userGuess > randomNumber) {
            lowOrHi.textContent = 'Lower!';
          }
        }

        guessCount++;
        guessField.value = '';
        guessField.focus();
      }

      guessSubmit.addEventListener('click', checkGuess);

      function setGameOver() {
        guessField.disabled = true;
        guessSubmit.disabled = true;
        resetButton = document.createElement('button');
        resetButton.textContent = 'Start new game';
        document.body.appendChild(resetButton);
        resetButton.addEventListener('click', resetGame);
      }

      function resetGame() {
        guessCount = 1;
        const resetParas = document.querySelectorAll('.resultParas p');
        for (const resetPara of resetParas) {
          resetPara.textContent = '';
        }

        resetButton.parentNode.removeChild(resetButton);
        guessField.disabled = false;
        guessSubmit.disabled = false;
        guessField.value = '';
        guessField.focus();
        lastResult.style.backgroundColor = '#00EEFF';
        randomNumber = Math.floor(Math.random() * 100) + 1;
      }

</script>



    
  </body>
</html>
