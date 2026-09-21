<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>ZPHS RAVUTLA – Homework</title>
<style>
*{box-sizing:border-box}body{margin:0;font-family:Arial,sans-serif;background:#f3f6fb;color:#172033}
header{background:#123b6d;color:white;padding:18px;text-align:center}
header h1{margin:0;font-size:24px}header p{margin:5px 0 0}
.container{max-width:1000px;margin:18px auto;padding:0 12px}
.card{background:white;border-radius:14px;padding:18px;margin-bottom:16px;box-shadow:0 3px 14px #00000012}
h2{margin-top:0;font-size:20px}.grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px}
label{font-weight:bold;font-size:14px;display:block;margin-bottom:5px}
input,select,textarea,button{width:100%;font:inherit}
input,select,textarea{padding:11px;border:1px solid #ccd5e0;border-radius:8px}
textarea{min-height:100px;resize:vertical}
button{padding:12px;border:0;border-radius:9px;background:#1769aa;color:white;font-weight:bold;cursor:pointer}
button.secondary{background:#e9eef5;color:#172033}.success{color:#087a42;font-weight:bold}.error{color:#b42318;font-weight:bold}
.homework-item{border-left:4px solid #1769aa;padding:10px 12px;margin:9px 0;background:#f7faff;border-radius:6px}
.homework-item b{display:inline-block;min-width:85px}
.toolbar{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.whatsapp{background:#168c45}.small{font-size:13px;color:#64748b}
.hidden{display:none}
@media(max-width:600px){.toolbar{grid-template-columns:1fr}}
</style>
</head>
<body>
<header>
<h1>ZPHS RAVUTLA</h1>
<p>Daily Homework Management System</p>
</header>

<div class="container">
<div class="card">
<h2>👩‍🏫 Teacher Homework Entry</h2>
<div class="grid">
<div><label>Teacher</label><select id="teacher"></select></div>
<div><label>Class</label><select id="class"></select></div>
<div><label>Subject</label><select id="subject"></select></div>
<div><label>Date</label><input id="date" type="date"></div>
</div>
<div style="margin-top:12px"><label>Homework / Task</label>
<textarea id="homework" placeholder="Enter today's homework..."></textarea></div>
<button id="submitBtn" style="margin-top:12px" onclick="submitHomework()">SUBMIT HOMEWORK</button>
<p id="status"></p>
</div>

<div class="card">
<h2>📋 Class-wise WhatsApp Homework</h2>
<div class="toolbar">
<div><label>Select Class</label><select id="viewClass" onchange="loadHomework()"></select></div>
<div><label>Date</label><input id="viewDate" type="date" onchange="loadHomework()"></div>
</div>
<div style="margin-top:12px">
<button class="whatsapp" onclick="copyWhatsApp()">📲 COPY WHATSAPP MESSAGE</button>
</div>
<div id="preview" style="margin-top:15px"></div>
</div>
</div>

<script>
const CONFIG = {
  WEB_APP_URL: "https://script.google.com/macros/s/AKfycbwo0N0BPH8T6a1gn2mmF4f3r31ef5vaVFLUilw9TGujFs7d8zOnPx6JshjP6aUELuim/exec",
  SCHOOL: "ZPHS RAVUTLA",
  TEACHERS: ["Headmaster CH SRINIVAS","M. Balaiah","B. Devising","V. Umashekar","P. Poshetty","A. Srinivas","K. Ravi","T Sudheer","S. Sushma"],
  SUBJECTS: ["Telugu","Hindi","English","Mathematics","Physical Science","Biological Science","Social Studies","Other"],
  CLASSES: ["6","7","8","9","10"]
};

const $=id=>document.getElementById(id);
function fill(id, arr){
  $(id).innerHTML=arr.map(x=>`<option value="${x}">${x}</option>`).join("");
}
function today(){
  const d=new Date(), m=String(d.getMonth()+1).padStart(2,"0"), day=String(d.getDate()).padStart(2,"0");
  return `${d.getFullYear()}-${m}-${day}`;
}
fill("teacher",CONFIG.TEACHERS); fill("subject",CONFIG.SUBJECTS); fill("class",CONFIG.CLASSES); fill("viewClass",CONFIG.CLASSES);
$("date").value=today(); $("viewDate").value=today();

async function api(params){
  const url=CONFIG.WEB_APP_URL;
  if(!url || url.includes("PASTE_YOUR")) throw new Error("Please paste the deployed Apps Script Web App URL into index.html.");
  const q=new URLSearchParams(params);
  const r=await fetch(url+"?"+q.toString());
  return await r.json();
}

async function submitHomework(){
  const status=$("status"), btn=$("submitBtn");
  const homework=$("homework").value.trim();
  if(!homework){status.className="error";status.textContent="Please enter homework.";return}
  btn.disabled=true; status.className=""; status.textContent="Saving...";
  try{
    const data=await api({action:"add",teacher:$("teacher").value,className:$("class").value,subject:$("subject").value,date:$("date").value,homework});
    if(!data.ok) throw new Error(data.error||"Could not save.");
    status.className="success";status.textContent="Homework saved successfully.";
    $("homework").value="";
    $("viewClass").value=$("class").value;$("viewDate").value=$("date").value;loadHomework();
  }catch(e){status.className="error";status.textContent=e.message}
  btn.disabled=false;
}

let currentItems=[];
async function loadHomework(){
  $("preview").innerHTML="<p class='small'>Loading...</p>";
  try{
    const data=await api({action:"get",className:$("viewClass").value,date:$("viewDate").value});
    if(!data.ok) throw new Error(data.error||"Could not load.");
    currentItems=data.items||[];
    render(currentItems);
  }catch(e){$("preview").innerHTML=`<p class="error">${e.message}</p>`}
}
function render(items){
  if(!items.length){$("preview").innerHTML="<p class='small'>No homework entered for this class and date.</p>";return}
  let html=`<div><strong>📚 ${CONFIG.SCHOOL} – CLASS ${$("viewClass").value}</strong><br><span class="small">${formatDate($("viewDate").value)}</span></div>`;
  items.forEach(x=>html+=`<div class="homework-item"><b>${escapeHtml(x.subject)}</b> ${escapeHtml(x.homework)}<div class="small">Teacher: ${escapeHtml(x.teacher)}</div></div>`);
  $("preview").innerHTML=html;
}
function formatDate(s){if(!s)return"";const [y,m,d]=s.split("-");return `${d}-${m}-${y}`}
function escapeHtml(s){return String(s).replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#039;"}[c]))}
function whatsappText(){
  const c=$("viewClass").value,d=$("viewDate").value;
  let t=`📚 *${CONFIG.SCHOOL}*\n*CLASS ${c} – TODAY'S HOMEWORK*\n📅 ${formatDate(d)}\n\n`;
  currentItems.forEach(x=>t+=`🔹 *${x.subject}:* ${x.homework}\n`);
  t+=`\n— Class Teacher`;
  return t;
}
async function copyWhatsApp(){
  if(!currentItems.length){alert("No homework available for this class/date.");return}
  const t=whatsappText();
  try{await navigator.clipboard.writeText(t);alert("WhatsApp message copied. Open the class WhatsApp group and paste it.");}
  catch(e){prompt("Copy this message:",t)}
}
loadHomework();
</script>
</body>
</html>
