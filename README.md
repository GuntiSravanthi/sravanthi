# sravanthi
HTML CODE
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Stopwatch</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>

  <div class="container">
    <h1>Stopwatch</h1>
    <div id="stopwatch">
      <span id="hours">00</span>:
      <span id="minutes">00</span>:
      <span id="seconds">00</span>:
      <span id="milliseconds">00</span>
    </div>
    <div class="controls">
      <button id="startBtn">Start</button>
      <button id="stopBtn">Stop</button>
      <button id="resetBtn">Reset</button>
    </div>
  </div>

  <script src="script.js"></script>
</body>
</html>
CSS CODE
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #f4f4f4;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.container {
  text-align: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

h1 {
  font-size: 2rem;
  margin-bottom: 20px;
}

#stopwatch {
  font-size: 3rem;
  margin-bottom: 20px;
}

.controls {
  display: flex;
  justify-content: center;
  gap: 20px;
}
button {
  padding: 10px 20px;
  font-size: 1rem;
  border: none;
  background-color: #ff6b6b;
  color: white;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #ff4c4c;
}
JAVASCRIPT CODE
let hours = 0;
let minutes = 0;
let seconds = 0;
let milliseconds = 0;
let interval;

// Start Button
document.getElementById('startBtn').addEventListener('click', function() {
  if (!interval) {
    interval = setInterval(startTimer, 10); // 10 ms for milliseconds
  }
});

// Stop Button
document.getElementById('stopBtn').addEventListener('click', function() {
  clearInterval(interval);
  interval = null;
});

// Reset Button
document.getElementById('resetBtn').addEventListener('click', function() {
  clearInterval(interval);
  interval = null;
  hours = 0;
  minutes = 0;
  seconds = 0;
  milliseconds = 0;
  document.getElementById('hours').textContent = "00";
  document.getElementById('minutes').textContent = "00";
  document.getElementById('seconds').textContent = "00";
  document.getElementById('milliseconds').textContent = "00";
});

// Timer Logic
function startTimer() {
  milliseconds += 10;
  
  if (milliseconds === 1000) {
    milliseconds = 0;
    seconds++;
  }

  if (seconds === 60) {
    seconds = 0;
    minutes++;
  }

  if (minutes === 60) {
    minutes = 0;
    hours++;
  }

  document.getElementById('milliseconds').textContent = formatTime(milliseconds / 10);
  document.getElementById('seconds').textContent = formatTime(seconds);
  document.getElementById('minutes').textContent = formatTime(minutes);
  document.getElementById('hours').textContent = formatTime(hours);
}

// Format time to always show two digits
function formatTime(time) {
  return time < 10 ? `0${time}` : time;
}
