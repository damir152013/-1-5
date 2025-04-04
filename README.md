<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Угадай число</title>
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
      alert('Число записано! Теперь другой человек должен угадать его.');
      document.getElementById('guessDiv').style.display = 'block'; // Показываем форму для угадывания
      document.getElementById('setDiv').style.display = 'none'; // Скрываем форму для записи числа
      document.getElementById('result').textContent = ''; // Очищаем предыдущие результаты
      document.getElementById('result').className = ''; // Сбрасываем стили
    }

    function guessNumber() {
      let guess = parseInt(document.getElementById('guess').value);
      let resultDiv = document.getElementById('result');

      if (guess === secretNumber) {
        resultDiv.textContent = 'Правильно! Число угадано.';
        resultDiv.className = 'correct';
      } else {
        resultDiv.textContent = 'Неправильно! Попробуйте снова.';
        resultDiv.className = 'incorrect';
      }

      // Делаем кнопки недоступными после первой попытки
      document.getElementById('guess').disabled = true;
      document.querySelector('button').disabled = true;

      // Показываем кнопку для начала новой игры
      document.getElementById('resetButton').style.display = 'block';
    }

    function resetGame() {
      // Скрываем кнопку "Снова"
      document.getElementById('resetButton').style.display = 'none';
      
      // Очищаем ввод и результат
      document.getElementById('userNumber').value = '';
      document.getElementById('guess').value = '';
      document.getElementById('result').textContent = '';
      document.getElementById('result').className = '';

      // Разблокируем поля ввода и кнопку для новой попытки
      document.getElementById('guess').disabled = false;
      document.querySelector('button').disabled = false;

      // Показываем форму для записи числа
      document.getElementById('setDiv').style.display = 'block';
      document.getElementById('guessDiv').style.display = 'none';
    }
  </script>
</head>
<body>
  <div id="setDiv">
    <h1>Выберите число от 1 до 5</h1>
    <select id="userNumber" required>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button onclick="setNumber()">Записать число</button>
  </div>

  <div id="guessDiv" style="display: none;">
    <h1>Попробуйте угадать число!</h1>
    <select id="guess" required>
      <option value="1">1</option>
      <option value="2">2</option>
      <option value="3">3</option>
      <option value="4">4</option>
      <option value="5">5</option>
    </select>
    <button onclick="guessNumber()">Угадать</button>
    <p id="result"></p>
  </div>

  <!-- Кнопка для начала новой игры -->
  <button id="resetButton" onclick="resetGame()" style="display: none;">Снова</button>
</body>
</html>
