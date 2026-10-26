<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-title" content="MY WORKOUT">
<meta name="theme-color" content="#0d0f14">

<title>MY WORKOUT</title>

<style>
:root{
  --bg:#0d0f14;
  --card:#171a21;
  --card2:#10131a;
  --line:#2a2f39;
  --text:#ffffff;
  --muted:#9099a8;
  --blue:#3a86ff;
  --green:#66d28d;
  --gold:#f2cd58;
}

*{
  box-sizing:border-box;
}

body{
  margin:0;
  background:var(--bg);
  color:var(--text);
  font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
}

.container{
  max-width:760px;
  margin:auto;
  padding:20px 14px 110px;
}

h1{
  margin:4px 0;
  font-size:34px;
}

.subtitle{
  color:#999;
  margin:7px 0 20px;
}

.top-actions{
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-bottom:18px;
}

.small-btn{
  border:1px solid var(--line);
  background:#171a21;
  color:#dde3ef;
  padding:10px 13px;
  border-radius:11px;
  font-weight:800;
}

.day-tabs{
  display:flex;
  gap:9px;
  overflow-x:auto;
  margin-bottom:18px;
  padding-bottom:5px;
  scrollbar-width:none;
}

.day-tabs::-webkit-scrollbar{
  display:none;
}

.day-btn{
  flex:0 0 auto;
  border:none;
  background:#1b1e26;
  color:#aaa;
  padding:12px 16px;
  border-radius:13px;
  font-weight:900;
}

.day-btn.active{
  background:var(--blue);
  color:white;
}

.today-card{
  background:linear-gradient(135deg,#17233b,#11151f);
  border:1px solid #28508a;
  border-radius:20px;
  padding:19px;
  margin-bottom:18px;
}

.today-small{
  color:#99a7bf;
  font-size:13px;
}

.today-title{
  font-size:30px;
  font-weight:950;
  margin:6px 0;
}

.today-sub{
  font-size:17px;
}

.today-note{
  color:#9ca8bb;
  line-height:1.5;
  font-size:14px;
  margin-top:7px;
}

.exercise{
  background:var(--card);
  border:1px solid var(--line);
  border-radius:18px;
  padding:15px;
  margin-bottom:14px;
}

.exercise.main{
  border-color:#3478cc;
}

.exercise.pre{
  border-color:#746119;
}

.exercise-head{
  display:flex;
  justify-content:space-between;
  gap:10px;
  align-items:flex-start;
}

.exercise-name{
  font-size:19px;
  font-weight:950;
}

.exercise-meta{
  color:var(--muted);
  font-size:13px;
  margin-top:5px;
}

.tag{
  display:inline-block;
  border-radius:999px;
  padding:4px 8px;
  margin-left:6px;
  font-size:10px;
  font-weight:950;
}

.tag.main{
  background:#163b69;
  color:#8bbcff;
}

.tag.pre{
  background:#4b3d09;
  color:#f2cf55;
}

.head-buttons{
  display:flex;
  gap:6px;
  flex-wrap:wrap;
  justify-content:flex-end;
}

.mini-btn{
  border:1px solid #394154;
  background:#10131a;
  color:#8fb7ff;
  border-radius:9px;
  padding:7px 9px;
  font-size:12px;
  font-weight:800;
}

.edit-btn{
  color:#f2cf55;
  border-color:#5a5130;
}

.previous{
  background:var(--card2);
  border-radius:11px;
  padding:10px;
  margin:11px 0;
  color:#abb4c4;
  font-size:13px;
  line-height:1.55;
}

.previous strong{
  color:#70a7ff;
}

.copy-btn{
  width:100%;
  background:#12151b;
  color:#cbd2df;
  border:1px solid #343a47;
  border-radius:9px;
  padding:9px;
  font-weight:800;
  margin-bottom:10px;
}

.headers,
.set-row{
  display:grid;
  grid-template-columns:34px 1fr 1fr 1fr;
  gap:6px;
  align-items:center;
}

.headers{
  font-size:11px;
  color:#777;
  text-align:center;
  margin-bottom:5px;
}

.set-row{
  margin-bottom:8px;
}

.set-number{
  color:#888;
  font-size:13px;
}

input{
  width:100%;
  min-width:0;
  background:#0d0f14;
  color:white;
  border:1px solid #333845;
  border-radius:9px;
  padding:10px 5px;
  text-align:center;
  font-size:16px;
}

.main-btn{
  width:100%;
  border:none;
  border-radius:14px;
  padding:16px;
  margin-top:10px;
  font-size:17px;
  font-weight:950;
}

.save-btn{
  background:#282d36;
  color:white;
}

.complete-btn{
  background:var(--blue);
  color:white;
}

.status{
  text-align:center;
  color:var(--green);
  min-height:22px;
  margin:13px 0;
  font-size:14px;
}

.bottom-info{
  text-align:center;
  color:#666;
  font-size:12px;
  line-height:1.6;
  margin-top:26px;
}

.modal{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.76);
  z-index:1000;
  padding:18px;
  overflow:auto;
}

.modal.show{
  display:block;
}

.modal-card{
  max-width:680px;
  margin:25px auto;
  background:#14171d;
  border:1px solid #2d323d;
  border-radius:18px;
  padding:16px;
}

.modal-head{
  display:flex;
  justify-content:space-between;
  align-items:center;
}

.modal-title{
  font-weight:950;
  font-size:20px;
}

.close-btn{
  border:none;
  background:#282d36;
  color:white;
  border-radius:9px;
  padding:9px 11px;
  font-weight:800;
}

.history-row{
  background:#0f1116;
  border:1px solid #272c35;
  border-radius:11px;
  padding:11px;
  margin:9px 0;
}

.history-date{
  color:#8f98a8;
  font-size:12px;
  margin-bottom:5px;
}

.history-sets{
  font-size:13px;
  line-height:1.55;
}

.edit-grid{
  display:grid;
  gap:12px;
  margin-top:16px;
}

.edit-label{
  font-size:12px;
  color:#929bab;
  font-weight:800;
  margin-bottom:5px;
}

.edit-input{
  text-align:left;
  padding:12px;
}

.edit-actions{
  display:flex;
  gap:8px;
  margin-top:14px;
}

.edit-actions button{
  flex:1;
  border:none;
  border-radius:10px;
  padding:12px;
  font-weight:900;
}

.reset-btn{
  background:#2b3039;
  color:#ddd;
}

.save-edit-btn{
  background:var(--blue);
  color:white;
}

@media(max-width:430px){
  .container{
    padding-left:11px;
    padding-right:11px;
  }

  .headers,
  .set-row{
    grid-template-columns:30px 1fr 1fr 1fr;
    gap:5px;
  }

  .exercise{
    padding:13px;
  }

  .today-title{
    font-size:28px;
  }
}
</style>
</head>

<body>

<div class="container">

  <h1>MY WORKOUT</h1>

  <div class="subtitle">
    Rolling 5 Split · BACK → CHEST → LEGS → SHOULDERS → ARMS
  </div>

  <div class="top-actions">
    <button class="small-btn" onclick="openAllHistory()">전체 기록</button>

    <button class="small-btn" onclick="exportData()">백업</button>

    <label class="small-btn">
      복원
      <input
        id="restoreFile"
        type="file"
        accept=".json,application/json"
        hidden
        onchange="restoreData(event)"
      >
    </label>
  </div>

  <div class="day-tabs" id="tabs"></div>

  <div class="today-card">

    <div class="today-small">
      CURRENT WORKOUT
    </div>

    <div
      class="today-title"
      id="dayTitle">
    </div>

    <div
      class="today-sub"
      id="daySub">
    </div>

    <div
      class="today-note"
      id="dayNote">
    </div>

  </div>

  <div id="exerciseList"></div>

  <button
    class="main-btn save-btn"
    onclick="saveDraft()">
    현재 기록 임시저장
  </button>

  <button
    class="main-btn complete-btn"
    onclick="completeWorkout()">
    운동 완료 → 다음 DAY
  </button>

  <div
    class="status"
    id="status">
  </div>

  <div class="bottom-info">
    각 운동의 <b>편집</b> 버튼에서<br>
    운동 이름과 세트 수를 직접 변경할 수 있습니다.
  </div>

</div>


<!-- 기록 모달 -->

<div
  class="modal"
  id="historyModal"
  onclick="historyBackground(event)">

  <div class="modal-card">

    <div class="modal-head">

      <div
        class="modal-title"
        id="historyTitle">
        기록
      </div>

      <button
        class="close-btn"
        onclick="closeHistory()">
        닫기
      </button>

    </div>

    <div id="historyContent"></div>

  </div>

</div>


<!-- 운동 편집 모달 -->

<div
  class="modal"
  id="editModal"
  onclick="editBackground(event)">

  <div class="modal-card">

    <div class="modal-head">

      <div class="modal-title">
        운동 편집
      </div>

      <button
        class="close-btn"
        onclick="closeEdit()">
        닫기
      </button>

    </div>


    <div class="edit-grid">

      <div>

        <div class="edit-label">
          운동 이름
        </div>

        <input
          id="editName"
          class="edit-input"
          type="text">

      </div>


      <div>

        <div class="edit-label">
          세트 수 (1~20)
        </div>

        <input
          id="editSets"
          class="edit-input"
          type="number"
          min="1"
          max="20">

      </div>

    </div>


    <div class="edit-actions">

      <button
        class="reset-btn"
        onclick="resetExercise()">
        기본값 복원
      </button>

      <button
        class="save-edit-btn"
        onclick="saveExerciseEdit()">
        저장
      </button>

    </div>

  </div>

</div>


<script>

const routine = [

  {

    name:"BACK",

    sub:"등",

    note:"암풀다운 선행 · 광배 + 상부등 + 등 중앙 두께",

    exercises:[

      ["암풀다운",2,"12~20","PRE"],

      ["어시스트 풀업",5,"6~10","MAIN"],

      ["Hammer Front High Row",5,"8~12","MAIN"],

      ["Life Fitness Strength Row (윗손잡이)",4,"8~12",""],

      ["Nautilus Row",4,"8~12",""],

      ["Hammer Iso-Lateral Row",3,"8~12",""],

      ["한팔 케이블 광배로우",3,"10~15",""],

      ["Nautilus Lat Pulldown",3,"8~12",""]

    ]

  },


  {

    name:"CHEST",

    sub:"가슴",

    note:"펙덱 선행 · 윗가슴 + 중앙 두께 우선",

    exercises:[

      ["Nautilus Pec Deck Fly",3,"12~20","PRE"],

      ["Hammer Incline Press",5,"6~10","MAIN"],

      ["Nautilus Chest Press",5,"8~12","MAIN"],

      ["플레이트로드 Chest Press",4,"8~12",""],

      ["Hammer Dip Machine",4,"8~12",""],

      ["케이블 플라이",3,"10~15",""],

      ["케이블 풀오버",3,"10~15",""]

    ]

  },


  {

    name:"LEGS",

    sub:"하체",

    note:"Hack Squat + Leg Press 메인 · 대퇴사두 우선",

    exercises:[

      ["이너타이",2,"12~20","PRE"],

      ["아웃타이",2,"12~20","PRE"],

      ["Hack Squat",5,"6~10","MAIN"],

      ["Leg Press",5,"10~15","MAIN"],

      ["Leg Extension",4,"10~15",""],

      ["Leg Curl",4,"8~15",""],

      ["Hip Thrust",4,"8~12",""],

      ["Calf Raise",4,"8~15",""],

      ["Back Extension",3,"10~15",""]

    ]

  },


  {

    name:"SHOULDERS",

    sub:"어깨",

    note:"오버헤드 슈러그 예열 → 프레스 → 측면 → 후면 → 사레레 머신",

    exercises:[

      ["Overhead Shrug",2,"12~20","PRE"],

      ["Nautilus Shoulder Press",4,"6~10",""],

      ["덤벨 Side Lateral Raise",5,"10~20","MAIN"],

      ["덤벨 Bent-over Lateral Raise",4,"12~20",""],

      ["External Rotation + 바깥쪽 Row (후면)",3,"12~20",""],

      ["Cable Cross Rear Delt Pull",3,"12~20",""],

      ["Nautilus Deltoid Raise",5,"10~20","MAIN"]

    ]

  },


  {

    name:"ARMS",

    sub:"팔",

    note:"이두 + 삼두",

    exercises:[

      ["Nautilus Biceps Curl (한팔)",5,"8~12","MAIN"],

      ["Bayesian Curl",4,"10~15",""],

      ["Rope Hammer Curl",4,"10~15",""],

      ["Cable Pushdown",5,"8~12","MAIN"],

      ["OH Cable Triceps Extension",4,"10~15",""],

      ["Cross-body Triceps Extension",4,"10~15",""],

      ["Lying Triceps Extension",3,"8~12",""]

    ]

  }

];


const HISTORY_KEY = "workoutHistory5";

const CURRENT_DAY_KEY = "currentDay5";

const CONFIG_KEY = "routineConfig5";

const DRAFT_PREFIX = "draft5_";


let currentDay =
  Number(localStorage.getItem(CURRENT_DAY_KEY) || 0);


if(
  !Number.isInteger(currentDay) ||
  currentDay < 0 ||
  currentDay >= routine.length
){
  currentDay = 0;
}


let editing = null;



function getHistory(){

  try{

    const data =
      JSON.parse(
        localStorage.getItem(HISTORY_KEY) || "[]"
      );

    return Array.isArray(data)
      ? data
      : [];

  }
  catch{

    return [];

  }

}



function setHistory(data){

  localStorage.setItem(
    HISTORY_KEY,
    JSON.stringify(data)
  );

}



function getConfig(){

  try{

    return (
      JSON.parse(
        localStorage.getItem(CONFIG_KEY) || "{}"
      )
      || {}
    );

  }
  catch{

    return {};

  }

}



function setConfig(data){

  localStorage.setItem(
    CONFIG_KEY,
    JSON.stringify(data)
  );

}



function exerciseId(dayIndex,exerciseIndex){

  return "d" + dayIndex + "e" + exerciseIndex;

}



function getExercise(dayIndex,exerciseIndex){

  const base =
    routine[dayIndex].exercises[exerciseIndex];

  const config =
    getConfig()[exerciseId(dayIndex,exerciseIndex)]
    || {};

  const customSets =
    parseInt(config.sets);

  const sets =
    customSets >= 1 &&
    customSets <= 20
      ? customSets
      : base[1];

  const name =
    config.name
      ? config.name.trim()
      : base[0];

  const aliases =
    [
      base[0],
      ...(config.aliases || []),
      config.name
    ]
    .filter(Boolean);

  return {

    id:exerciseId(dayIndex,exerciseIndex),

    name,

    sets,

    reps:base[2],

    tag:base[3],

    baseName:base[0],

    baseSets:base[1],

    aliases:[
      ...new Set(aliases)
    ]

  };

}



function draftKey(){

  return (
    DRAFT_PREFIX +
    routine[currentDay].name
  );

}



function getDraft(){

  try{

    return JSON.parse(
      localStorage.getItem(draftKey())
      || "null"
    );

  }
  catch{

    return null;

  }

}



function escapeHTML(value){

  return String(value ?? "")

    .replace(/&/g,"&amp;")

    .replace(/</g,"&lt;")

    .replace(/"/g,"&quot;");

}



function formatSet(set,index){

  const weight =
    set.weight === ""
      ? "-"
      : set.weight;

  const reps =
    set.reps === ""
      ? "-"
      : set.reps;

  const rir =
    set.rir === ""
      ? "-"
      : set.rir;

  return (
    `${index+1}세트 ` +
    `${weight}kg × ` +
    `${reps}회 · ` +
    `RIR ${rir}`
  );

}



function getExerciseHistory(dayIndex,exerciseIndex){

  const exercise =
    getExercise(dayIndex,exerciseIndex);

  return getHistory()

    .filter(
      session =>
        session.day ===
        routine[dayIndex].name
    )

    .map(session=>{

      const found =
        (session.exercises || [])
        .find(exerciseRecord =>

          exerciseRecord.id === exercise.id

          ||

          exercise.aliases.includes(
            exerciseRecord.name
          )

        );

      if(!found){
        return null;
      }

      return {

        date:session.date,

        sets:found.sets || []

      };

    })

    .filter(Boolean);

}



function getLastExercise(dayIndex,exerciseIndex){

  const records =
    getExerciseHistory(
      dayIndex,
      exerciseIndex
    );

  if(!records.length){
    return null;
  }

  return records[
    records.length - 1
  ];

}



function renderTabs(){

  const tabs =
    document.getElementById("tabs");

  tabs.innerHTML = "";


  routine.forEach((day,index)=>{

    const button =
      document.createElement("button");

    button.className =
      "day-btn" +
      (
        index === currentDay
        ? " active"
        : ""
      );

    button.innerText =
      day.name;

    button.onclick = ()=>{

      currentDay = index;

      localStorage.setItem(
        CURRENT_DAY_KEY,
        currentDay
      );

      render();

      window.scrollTo({
        top:0,
        behavior:"smooth"
      });

    };

    tabs.appendChild(button);

  });

}



function tagHTML(tag){

  if(tag === "MAIN"){

    return `
      <span class="tag main">
        MAIN
      </span>
    `;

  }


  if(tag === "PRE"){

    return `
      <span class="tag pre">
        선행
      </span>
    `;

  }


  return "";

}



function render(){

  renderTabs();


  const day =
    routine[currentDay];


  document.getElementById(
    "dayTitle"
  ).innerText =
    day.name;


  document.getElementById(
    "daySub"
  ).innerText =
    day.sub;


  document.getElementById(
    "dayNote"
  ).innerText =
    day.note;


  const list =
    document.getElementById(
      "exerciseList"
    );


  list.innerHTML = "";


  const draft =
    getDraft();


  day.exercises.forEach(
    (baseExercise,exerciseIndex)=>{


      const exercise =
        getExercise(
          currentDay,
          exerciseIndex
        );


      const previous =
        getLastExercise(
          currentDay,
          exerciseIndex
        );


      const card =
        document.createElement("div");


      card.className =
        "exercise " +
        (
          exercise.tag === "MAIN"
          ? "main"
          :
          exercise.tag === "PRE"
          ? "pre"
          :
          ""
        );


      let previousHTML =
        `
          <div class="previous">
            지난 기록 없음
          </div>
        `;


      if(previous){

        previousHTML =
          `
            <div class="previous">

              <strong>
                지난 기록 ·
                ${previous.date}
              </strong>

              <br>

              ${
                previous.sets
                .map(formatSet)
                .join("<br>")
              }

            </div>
          `;

      }


      let rows = "";


      for(
        let setIndex=0;
        setIndex<exercise.sets;
        setIndex++
      ){

        const saved =
          draft?.exercises?.[
            exerciseIndex
          ]?.sets?.[
            setIndex
          ]
          || {};


        rows += `

          <div class="set-row">

            <div class="set-number">
              ${setIndex+1}
            </div>

            <input
              id="weight-${exerciseIndex}-${setIndex}"
              type="number"
              step="0.5"
              inputmode="decimal"
              placeholder="kg"
              value="${escapeHTML(saved.weight)}"
            >

            <input
              id="reps-${exerciseIndex}-${setIndex}"
              type="number"
              inputmode="numeric"
              placeholder="회"
              value="${escapeHTML(saved.reps)}"
            >

            <input
              id="rir-${exerciseIndex}-${setIndex}"
              type="number"
              inputmode="numeric"
              placeholder="RIR"
              value="${escapeHTML(saved.rir)}"
            >

          </div>

        `;

      }


      card.innerHTML = `

        <div class="exercise-head">

          <div>

            <div class="exercise-name">

              ${exercise.name}

              ${tagHTML(exercise.tag)}

            </div>

            <div class="exercise-meta">

              ${exercise.sets}세트
              ·
              ${exercise.reps}회

            </div>

          </div>


          <div class="head-buttons">

            <button
              class="mini-btn edit-btn"
              onclick="openEdit(
                ${currentDay},
                ${exerciseIndex}
              )">

              편집

            </button>


            <button
              class="mini-btn"
              onclick="openExerciseHistory(
                ${currentDay},
                ${exerciseIndex}
              )">

              기록 보기

            </button>

          </div>

        </div>


        ${previousHTML}


        ${
          previous

          ?

          `
            <button
              class="copy-btn"
              onclick="copyLast(
                ${exerciseIndex}
              )">

              지난 기록 불러오기

            </button>
          `

          :

          ""
        }


        <div class="headers">

          <div></div>

          <div>KG</div>

          <div>REPS</div>

          <div>RIR</div>

        </div>


        ${rows}

      `;


      list.appendChild(card);

    }

  );

}



function collectWorkout(){

  const day =
    routine[currentDay];


  const exercises = [];


  day.exercises.forEach(
    (baseExercise,exerciseIndex)=>{


      const exercise =
        getExercise(
          currentDay,
          exerciseIndex
        );


      const sets = [];


      for(
        let setIndex=0;
        setIndex<exercise.sets;
        setIndex++
      ){

        sets.push({

          weight:
            document.getElementById(
              `weight-${exerciseIndex}-${setIndex}`
            ).value,

          reps:
            document.getElementById(
              `reps-${exerciseIndex}-${setIndex}`
            ).value,

          rir:
            document.getElementById(
              `rir-${exerciseIndex}-${setIndex}`
            ).value

        });

      }


      exercises.push({

        id:exercise.id,

        name:exercise.name,

        sets

      });

    }

  );


  return {

    day:day.name,

    exercises

  };

}



function saveDraft(){

  const data =
    collectWorkout();


  data.savedAt =
    new Date().toLocaleString("ko-KR");


  localStorage.setItem(
    draftKey(),
    JSON.stringify(data)
  );


  document.getElementById(
    "status"
  ).innerText =
    "✓ 임시저장 완료";

}



function copyLast(exerciseIndex){

  const previous =
    getLastExercise(
      currentDay,
      exerciseIndex
    );


  if(!previous){
    return;
  }


  previous.sets.forEach(
    (set,index)=>{


      const weight =
        document.getElementById(
          `weight-${exerciseIndex}-${index}`
        );


      const reps =
        document.getElementById(
          `reps-${exerciseIndex}-${index}`
        );


      const rir =
        document.getElementById(
          `rir-${exerciseIndex}-${index}`
        );


      if(weight){
        weight.value =
          set.weight || "";
      }


      if(reps){
        reps.value =
          set.reps || "";
      }


      if(rir){
        rir.value =
          set.rir ?? "";
      }

    }

  );


  saveDraft();

}



function completeWorkout(){

  const workout =
    collectWorkout();


  const hasData =
    workout.exercises.some(
      exercise =>
        exercise.sets.some(
          set =>
            set.weight ||
            set.reps ||
            set.rir !== ""
        )
    );


  if(
    !hasData
    &&
    !confirm(
      "입력된 기록이 없습니다. 그래도 완료할까요?"
    )
  ){
    return;
  }


  const now =
    Date.now();


  workout.ts =
    now;


  workout.id =
    workout.day +
    "-" +
    now;


  workout.date =
    new Date(now)
    .toLocaleString("ko-KR");


  const history =
    getHistory();


  history.push(
    workout
  );


  setHistory(
    history
  );


  localStorage.removeItem(
    draftKey()
  );


  currentDay =
    (
      currentDay + 1
    )
    %
    routine.length;


  localStorage.setItem(
    CURRENT_DAY_KEY,
    currentDay
  );


  document.getElementById(
    "status"
  ).innerText =
    "✓ 운동 완료 · 다음 DAY";


  render();


  window.scrollTo({
    top:0,
    behavior:"smooth"
  });

}



function openEdit(
  dayIndex,
  exerciseIndex
){

  try{
    saveDraft();
  }
  catch{}


  editing = {
    dayIndex,
    exerciseIndex
  };


  const exercise =
    getExercise(
      dayIndex,
      exerciseIndex
    );


  document.getElementById(
    "editName"
  ).value =
    exercise.name;


  document.getElementById(
    "editSets"
  ).value =
    exercise.sets;


  document.getElementById(
    "editModal"
  ).classList.add(
    "show"
  );

}



function closeEdit(){

  document.getElementById(
    "editModal"
  ).classList.remove(
    "show"
  );


  editing = null;

}



function editBackground(event){

  if(
    event.target.id ===
    "editModal"
  ){

    closeEdit();

  }

}



function saveExerciseEdit(){

  if(!editing){
    return;
  }


  const {
    dayIndex,
    exerciseIndex
  } = editing;


  const exercise =
    getExercise(
      dayIndex,
      exerciseIndex
    );


  const newName =
    document.getElementById(
      "editName"
    ).value.trim();


  const newSets =
    parseInt(
      document.getElementById(
        "editSets"
      ).value
    );


  if(!newName){

    alert(
      "운동 이름을 입력하세요."
    );

    return;

  }


  if(
    newSets < 1
    ||
    newSets > 20
  ){

    alert(
      "세트 수는 1~20 사이로 입력하세요."
    );

    return;

  }


  const config =
    getConfig();


  const oldConfig =
    config[exercise.id]
    || {};


  const aliases = [

    ...(
      oldConfig.aliases
      || []
    ),

    exercise.name,

    exercise.baseName

  ];


  config[exercise.id] = {

    name:newName,

    sets:newSets,

    aliases:[
      ...new Set(aliases)
    ]

  };


  setConfig(
    config
  );


  closeEdit();


  render();


  document.getElementById(
    "status"
  ).innerText =
    `✓ ${newName} · ${newSets}세트`;

}



function resetExercise(){

  if(!editing){
    return;
  }


  const id =
    exerciseId(
      editing.dayIndex,
      editing.exerciseIndex
    );


  const config =
    getConfig();


  delete config[id];


  setConfig(
    config
  );


  closeEdit();


  render();


  document.getElementById(
    "status"
  ).innerText =
    "✓ 기본값으로 복원";

}



function openExerciseHistory(
  dayIndex,
  exerciseIndex
){

  const exercise =
    getExercise(
      dayIndex,
      exerciseIndex
    );


  const records =
    getExerciseHistory(
      dayIndex,
      exerciseIndex
    )
    .slice()
    .reverse();


  document.getElementById(
    "historyTitle"
  ).innerText =
    exercise.name;


  const content =
    document.getElementById(
      "historyContent"
    );


  if(!records.length){

    content.innerHTML =
      `
        <div class="history-row">
          기록 없음
        </div>
      `;

  }
  else{

    content.innerHTML =
      records.map(record=>`

        <div class="history-row">

          <div class="history-date">
            ${record.date}
          </div>

          <div class="history-sets">

            ${
              record.sets
              .map(formatSet)
              .join("<br>")
            }

          </div>

        </div>

      `).join("");

  }


  document.getElementById(
    "historyModal"
  ).classList.add(
    "show"
  );

}



function openAllHistory(){

  const history =
    getHistory()
    .slice()
    .reverse();


  document.getElementById(
    "historyTitle"
  ).innerText =
    "전체 운동 기록";


  const content =
    document.getElementById(
      "historyContent"
    );


  if(!history.length){

    content.innerHTML =
      `
        <div class="history-row">
          기록 없음
        </div>
      `;

  }
  else{

    content.innerHTML =
      history.map(session=>`

        <div class="history-row">

          <div class="history-date">
            ${session.date}
          </div>

          <div style="
            font-weight:900;
            margin-bottom:8px;
          ">

            ${session.day}

          </div>

          <div class="history-sets">

            ${
              (session.exercises || [])
              .map(exercise=>{

                const entered =
                  (exercise.sets || [])
                  .filter(
                    set =>
                      set.weight ||
                      set.reps ||
                      set.rir !== ""
                  );


                if(!entered.length){
                  return "";
                }


                return `

                  <b>
                    ${exercise.name}
                  </b>

                  <br>

                  ${
                    entered
                    .map(formatSet)
                    .join("<br>")
                  }

                `;

              })

              .filter(Boolean)

              .join("<br><br>")
            }

          </div>

        </div>

      `).join("");

  }


  document.getElementById(
    "historyModal"
  ).classList.add(
    "show"
  );

}



function closeHistory(){

  document.getElementById(
    "historyModal"
  ).classList.remove(
    "show"
  );

}



function historyBackground(event){

  if(
    event.target.id ===
    "historyModal"
  ){

    closeHistory();

  }

}



function exportData(){

  const data = {

    currentDay5:
      currentDay,

    workoutHistory5:
      getHistory(),

    routineConfig5:
      getConfig(),

    exportedAt:
      new Date()
      .toISOString()

  };


  const blob =
    new Blob(
      [
        JSON.stringify(
          data,
          null,
          2
        )
      ],
      {
        type:"application/json"
      }
    );


  const url =
    URL.createObjectURL(
      blob
    );


  const a =
    document.createElement(
      "a"
    );


  a.href =
    url;


  a.download =
    "workout-backup.json";


  a.click();


  setTimeout(
    ()=>URL.revokeObjectURL(url),
    1000
  );

}



function restoreData(event){

  const file =
    event.target.files?.[0];


  if(!file){
    return;
  }


  const reader =
    new FileReader();


  reader.onload = ()=>{

    try{

      const data =
        JSON.parse(
          reader.result
        );


      if(
        Array.isArray(
          data.workoutHistory5
        )
      ){

        setHistory(
          data.workoutHistory5
        );

      }


      if(
        data.routineConfig5
      ){

        setConfig(
          data.routineConfig5
        );

      }


      if(
        Number.isInteger(
          data.currentDay5
        )
      ){

        currentDay =
          Math.max(
            0,
            Math.min(
              routine.length - 1,
              data.currentDay5
            )
          );


        localStorage.setItem(
          CURRENT_DAY_KEY,
          currentDay
        );

      }


      render();


      document.getElementById(
        "status"
      ).innerText =
        "✓ 복원 완료";

    }
    catch{

      alert(
        "백업 파일을 읽을 수 없습니다."
      );

    }


    event.target.value = "";

  };


  reader.readAsText(
    file
  );

}



render();

</script>

</body>
</html>
