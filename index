<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LVT Competition Selection</title>

<style>
*{
  box-sizing:border-box;
}

body{
  margin:0;
  font-family:Arial,sans-serif;
  background:linear-gradient(135deg,#06101d,#10283e);
  color:white;
  min-height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  padding:20px;
}

.card{
  width:100%;
  max-width:500px;
  background:#0b1929;
  border:1px solid #c9a43b;
  border-radius:24px;
  padding:25px;
  box-shadow:0 15px 45px rgba(0,0,0,.5);
}

.logo{
  text-align:center;
  color:#d8b44a;
  font-weight:bold;
  letter-spacing:4px;
  font-size:13px;
}

h1{
  text-align:center;
  margin:10px 0;
}

.subtitle{
  text-align:center;
  color:#aab5c2;
  margin-bottom:25px;
}

label{
  display:block;
  color:#d8b44a;
  font-weight:bold;
  margin:15px 0 8px;
}

select{
  width:100%;
  padding:15px;
  border-radius:12px;
  border:1px solid #36506b;
  background:#081522;
  color:white;
  font-size:16px;
}

.numbers{
  display:grid;
  grid-template-columns:repeat(4,1fr);
  gap:10px;
  margin-top:12px;
}

.number{
  padding:16px 5px;
  border-radius:12px;
  border:1px solid #36506b;
  background:#10263b;
  color:white;
  font-size:18px;
  font-weight:bold;
  cursor:pointer;
}

.number:hover{
  border-color:#d8b44a;
}

.number.selected{
  background:#d8b44a;
  color:#07111f;
}

.number.used{
  opacity:.25;
  cursor:not-allowed;
}

#confirm{
  width:100%;
  margin-top:20px;
  padding:16px;
  border:0;
  border-radius:12px;
  background:#d8b44a;
  color:#07111f;
  font-size:16px;
  font-weight:bold;
  cursor:pointer;
}

#confirm:disabled{
  opacity:.4;
  cursor:not-allowed;
}

.result{
  display:none;
  margin-top:20px;
  padding:22px;
  text-align:center;
  background:#10263b;
  border:1px solid #d8b44a;
  border-radius:15px;
}

.result small{
  color:#aab5c2;
}

.result strong{
  display:block;
  margin-top:8px;
  color:#d8b44a;
  font-size:24px;
}

.status{
  text-align:center;
  margin-top:16px;
  color:#9eacbb;
  font-size:13px;
}

.note{
  text-align:center;
  margin-top:15px;
  color:#718094;
  font-size:12px;
}
</style>
</head>

<body>

<div class="card">

  <div class="logo">LVT COMPETITION</div>

  <h1>Private Selection</h1>

  <div class="subtitle">
    Choose your name and select one available number.
  </div>

  <label>Your Name</label>

  <select id="woman">
    <option value="">Select your name</option>
    <option>Mar’atussaliha</option>
    <option>Auntyn Yara</option>
    <option>Zahraty</option>
    <option>Cutieteemah Lyrics</option>
    <option>Autah Lyrics</option>
    <option>Teemarluvly</option>
    <option>Merhmerh Lyrics</option>
    <option>Queenjurry</option>
  </select>

  <label>Select Number</label>

  <div class="numbers" id="numbers"></div>

  <button id="confirm" disabled>
    CONFIRM SELECTION
  </button>

  <div class="result" id="result">
    <small>Your selected partner is:</small>
    <strong id="partner"></strong>
  </div>

  <div class="status" id="status">
    8 numbers available
  </div>

  <div class="note">
    Each participant can select only once.
  </div>

</div>

<script>

const men = [
  "Bakori Lyrics",
  "Bash Lyrics",
  "Yusufa Lyrics",
  "Jagora Lyrics",
  "Alkhaddab Lyrics",
  "King Haidar Lyrics",
  "Abbas Lyrics",
  "IBB Lyrics"
];

const women = [
  "Mar’atussaliha",
  "Auntyn Yara",
  "Zahraty",
  "Cutieteemah Lyrics",
  "Autah Lyrics",
  "Teemarluvly",
  "Merhmerh Lyrics",
  "Queenjurry"
];

let selectedNumber = null;

let usedNumbers =
  JSON.parse(localStorage.getItem("lvt_used_numbers") || "[]");

let completedWomen =
  JSON.parse(localStorage.getItem("lvt_completed_women") || "[]");

const womanSelect = document.getElementById("woman");
const numbersBox = document.getElementById("numbers");
const confirmButton = document.getElementById("confirm");
const resultBox = document.getElementById("result");
const partnerText = document.getElementById("partner");
const statusText = document.getElementById("status");


function renderNumbers(){

  numbersBox.innerHTML = "";

  for(let i = 1; i <= 8; i++){

    const button = document.createElement("button");

    button.className = "number";

    button.textContent = i;

    if(usedNumbers.includes(i)){
      button.classList.add("used");
      button.disabled = true;
    }

    if(selectedNumber === i){
      button.classList.add("selected");
    }

    if(
      !womanSelect.value ||
      completedWomen.includes(womanSelect.value)
    ){
      button.disabled = true;
    }

    button.onclick = function(){

      if(usedNumbers.includes(i)) return;

      selectedNumber = i;

      renderNumbers();

      confirmButton.disabled = false;
    };

    numbersBox.appendChild(button);
  }

  const remaining = 8 - usedNumbers.length;

  statusText.textContent =
    remaining + (remaining === 1
      ? " number available"
      : " numbers available");

}


womanSelect.addEventListener("change", function(){

  selectedNumber = null;

  resultBox.style.display = "none";

  if(completedWomen.includes(womanSelect.value)){

    alert("This participant has already made a selection.");

  }

  confirmButton.disabled = true;

  renderNumbers();

});


confirmButton.addEventListener("click", function(){

  const woman = womanSelect.value;

  if(!woman){
    alert("Please select your name.");
    return;
  }

  if(!selectedNumber){
    alert("Please select a number.");
    return;
  }

  if(completedWomen.includes(woman)){
    alert("You have already selected.");
    return;
  }

  if(usedNumbers.includes(selectedNumber)){
    alert("This number is no longer available.");
    renderNumbers();
    return;
  }

  const male = men[selectedNumber - 1];

  usedNumbers.push(selectedNumber);

  completedWomen.push(woman);

  localStorage.setItem(
    "lvt_used_numbers",
    JSON.stringify(usedNumbers)
  );

  localStorage.setItem(
    "lvt_completed_women",
    JSON.stringify(completedWomen)
  );

  partnerText.textContent = male;

  resultBox.style.display = "block";

  selectedNumber = null;

  confirmButton.disabled = true;

  renderNumbers();

});


renderNumbers();

</script>

</body>
</html>
