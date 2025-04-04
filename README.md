<html>
<html lang="uk">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Вгадай число</title>
  <style>
    .correct {
      color: green;
    }
    .incorrect {
      color: red;
    }
  </style>
  <script>
    let secretNumber;

    function setNumber() {
      secretNumber = parseInt(document.getElementById('userNumber').value);
      alert('Число записано! Тепер інша людина повинна вгадати його.');
      document.getElementById('guessDiv').style.display = 'block'; // Показуємо форму для вгадування
      document.getElementById('setDiv').style.display = 'none'; // Ховаємо форму для запису числа
      document.getElementById('result').textContent = ''; // Очищаємо попередні результати
      document.getElementById('result').className = ''; // Скидаємо стилі
    }

    function guessNumber() {
      let guess = parseInt(document.getElementById('guess').value);
      let resultDiv = document.getElementById('result');

      if (guess === secretNumber) {
        resultDiv.textContent = 'Правильно! Число вгадано.';
        resultDiv.className = 'correct';
      } else {
        resultDiv.textContent = 'Неправильно! Спробуйте ще раз.';
        resultDiv.className = 'incorrect';
      }

      // Зробимо кнопки недоступними після першої спроби
      document.getElementById('guess').disabled = true;
      document.querySelector('button').disabled = true;

      // Показуємо кнопку для початку нової гри
      document.getElementById('resetButton').style.display = 'block';
    }

    function resetGame() {
      // Ховаємо кнопку "Спробувати знову"
      document.getElementById('resetButton').style.display = 'none';
      
      // Очищаємо введення та результат
      document.getElementById('userNumber').value = '';
      document.getElementById('guess').value = '';
      document.getElementById('result').textContent = '';
      document.getElementById('result').className = '';

      // Відкриваємо поля для нової спроби
      document.getElementById('guess').disabled = false;
      document.querySelector('button').disabled = false;

      // Показуємо форму для запису числа
      document.getElementById('setDiv').style.display = 'block';
      document.getElementById('guessDiv').style.display = 'none';
    }
  </script>
</head>
<body>
  <div id="setDiv">
    <h1>Виберіть число від 1 до 5</h1>
    <select id="userNumber" required>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button onclick="setNumber()">Записати число</button>
  </div>

  <div id="guessDiv" style="display: none;">
    <h1>Спробуйте вгадати число!</h1>
    <select id="guess" required>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button onclick="guessNumber()">Вгадати</button>
    <p id="result"></p>
  </div>

  <!-- Кнопка для початку нової гри -->
  <button id="resetButton" onclick="resetGame()" style="display: none;">Спробувати знову</button>
</body>
</html>
