var minutes = 0;
var seconds = 0;
var centiseconds = 0;
var timerCount;

function start() {
    let btn = document.getElementById('btn-start');
    if (btn.innerText === "Start") {
        btn.innerText = "Stop";
        btn.classList.remove('start');
        btn.classList.add('stop');
        startCount();
    } else {
        btn.innerText = "Start";
        btn.classList.remove('stop');
        btn.classList.add('start');
        stopCount();
    }
}

function startCount() {
    count();
    timerCount = setInterval(count, 10);
}

function count() {
  centiseconds++;
  if (centiseconds === 100) {
    centiseconds = 0;
    seconds++;
    if (seconds === 60) {
      seconds = 0;
      minutes++;
      if (minutes === 60) {
        minutes = 0;
      }
      updateMinutes();  
    }
    updateSeconds();
  }
  updateCentiseconds();
}

function updateCentiseconds() {
  document.getElementById('centiseconds').innerHTML = getTimeStr(centiseconds);
}
function updateSeconds() {
  document.getElementById('seconds').innerHTML = getTimeStr(seconds);
}
function updateMinutes() {
  document.getElementById('minutes').innerHTML = getTimeStr(minutes);
}
function getTimeStr(t) {
  return t < 10 ? `0${t}` : `${t}`;
}

function stopCount() {
    if (timerCount) {
        clearInterval (timerCount);
    }
}

function reset() {
    minutes = 0;
    seconds = 0;
    centiseconds = 0;
    
    updateCentiseconds();
    updateSeconds();
    updateMinutes();
} 