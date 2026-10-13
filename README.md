# AI-Based-Virtual-Brain-Connectivity

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>AI Virtual Brain Connectivity</title>

<style>
* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Arial, sans-serif;
    background: #080d1b;
    color: #f1f5f9;
}

header {
    padding: 22px;
    text-align: center;
    background: #111a30;
    border-bottom: 1px solid #263650;
}

header h1 {
    color: #67e8f9;
    font-size: 25px;
}

header p {
    margin-top: 8px;
    color: #a5b4cc;
}

nav {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 10px;
    padding: 18px;
}

nav button, .action {
    border: 0;
    padding: 12px 18px;
    border-radius: 8px;
    background: #24334e;
    color: white;
    cursor: pointer;
}

nav button.active, .action {
    background: #0891b2;
}

nav button:hover, .action:hover {
    opacity: 0.85;
}

main {
    max-width: 1050px;
    margin: auto;
    padding: 18px;
}

.page {
    display: none;
}

.page.active {
    display: block;
}

h2 {
    margin-bottom: 15px;
    color: #67e8f9;
}

p {
    line-height: 1.6;
}

.grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(230px, 1fr));
    gap: 18px;
    margin: 20px 0;
}

.card {
    padding: 22px;
    background: #111a30;
    border: 1px solid #263650;
    border-radius: 14px;
}

.card h3 {
    margin-bottom: 12px;
    color: #a5b4fc;
}

.value {
    margin: 12px 0;
    font-size: 25px;
    font-weight: bold;
    color: #67e8f9;
}

canvas {
    display: block;
    width: 100%;
    height: 220px;
    background: #070c18;
    border-radius: 10px;
    margin-top: 15px;
}

input, textarea {
    width: 100%;
    padding: 12px;
    margin: 10px 0;
    color: white;
    background: #080d1b;
    border: 1px solid #3b4b68;
    border-radius: 8px;
}

textarea {
    min-height: 90px;
    resize: vertical;
}

.emotions {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
    margin: 18px 0;
}

.emotion {
    flex: 1;
    min-width: 100px;
    padding: 17px 10px;
    border-radius: 10px;
    border: 2px solid #334155;
    background: #172238;
    color: white;
    cursor: pointer;
    font-size: 16px;
}

.emotion.selected {
    border-color: #67e8f9;
    background: #164e63;
}

#emotionIcon {
    font-size: 45px;
    margin: 12px 0;
}

.status {
    color: #94a3b8;
    font-size: 13px;
    margin-top: 10px;
}

table {
    width: 100%;
    border-collapse: collapse;
    margin-top: 15px;
}

th, td {
    padding: 12px 8px;
    text-align: left;
    border-bottom: 1px solid #334155;
    overflow-wrap: anywhere;
}

footer {
    text-align: center;
    color: #94a3b8;
    padding: 25px;
}

#message {
    margin-top: 12px;
    color: #67e8f9;
}

@media (max-width: 500px) {
    header h1 {
        font-size: 20px;
    }

    main {
        padding: 12px;
    }
}
</style>
</head>

<body>

<header>
    <h1>🧠 AI-Based Virtual Brain Connectivity</h1>
    <p>Brain Wave Visualization & Emotional Expression</p>
</header>

<nav>
    <button class="active" data-page="waves">1. Brain Waves</button>
    <button data-page="emotion">2. Emotion Detection</button>
    <button data-page="results">3. Results</button>
</nav>

<main>

<!-- PAGE 1: BRAIN WAVES -->
<section id="waves" class="page active">
    <h2>Brain Wave Monitoring</h2>
    <p>
        Explore a simulated EEG waveform and a visual representation
        of connected brain regions.
    </p>

    <div class="grid">
        <div class="card">
            <h3>EEG Waveform</h3>
            <p class="status">Simulated signal — not actual sensor data</p>
            <canvas id="waveCanvas"></canvas>
        </div>

        <div class="card">
            <h3>Brain Connectivity</h3>
            <canvas id="brainCanvas"></canvas>
            <p class="status">Illustrative network — not measured connectivity</p>
        </div>
    </div>

    <div class="card">
        <h3>Monitoring Status</h3>
        <div class="value" id="monitorStatus">Demo Running</div>
        <p>
            The animated signal demonstrates how brain-wave data
            could be displayed when connected to an EEG device.
        </p>
    </div>
</section>

<!-- PAGE 2: EMOTION -->
<section id="emotion" class="page">
    <h2>Emotion Expression</h2>
    <p>
        Select the emotion you want to demonstrate. In this prototype,
        the emotion is user-selected, not inferred from brain activity.
    </p>

    <div class="card">
        <h3>How are you feeling?</h3>

        <div class="emotions">
            <button class="emotion" data-emotion="Happy">
                😊 Happy
            </button>
            <button class="emotion" data-emotion="Sad">
                😢 Sad
            </button>
            <button class="emotion" data-emotion="Calm">
                😌 Calm
            </button>
        </div>

        <label for="person">Person / Session ID</label>
        <input id="person" type="text"
               placeholder="Example: Person 01" maxlength="50">

        <label for="notes">Share your feelings</label>
        <textarea id="notes"
                  placeholder="Write how you feel (optional)"
                  maxlength="500"></textarea>

        <button class="action" id="saveEmotion">
            Save Emotion Result
        </button>

        <p id="message" role="status"></p>
    </div>

    <div class="grid">
        <div class="card">
            <h3>Selected Emotion</h3>
            <div id="emotionIcon">💭</div>
            <div class="value" id="emotionValue">Not selected</div>
            <p id="emotionDescription">
                Select an emotion above to display the result.
            </p>
        </div>

        <div class="card">
            <h3>Purpose</h3>
            <p>
                This screen demonstrates one possible interface for
                expressing emotions when verbal communication is difficult.
            </p>
            <p class="status">
                Emotion labels are demonstrations, not medical findings.
            </p>
        </div>
    </div>
</section>

<!-- PAGE 3: RESULTS -->
<section id="results" class="page">
    <h2>Results & Connectivity</h2>

    <div class="grid">
        <div class="card">
            <h3>Current Emotion</h3>
            <div class="value" id="resultEmotion">No result</div>
            <p id="resultPerson">Person: —</p>
        </div>

        <div class="card">
            <h3>Total Saved Sessions</h3>
            <div class="value" id="totalSessions">0</div>
            <p>Results saved during this browser session.</p>
        </div>
    </div>

    <div class="card">
        <h3>Emotion Session History</h3>

        <div style="overflow-x:auto">
            <table>
                <thead>
                    <tr>
                        <th>Person</th>
                        <th>Emotion</th>
                        <th>Feeling Notes</th>
                        <th>Time</th>
                    </tr>
                </thead>
                <tbody id="history">
                    <tr>
                        <td colspan="4">No results saved yet.</td>
                    </tr>
                </tbody>
            </table>
        </div>

        <button class="action" id="clearHistory"
                style="margin-top:18px">
            Clear Session History
        </button>

        <p id="historyMessage" class="status"></p>
    </div>
</section>

</main>

<footer>
    AI-Based Virtual Brain Connectivity | Frontend Demonstration
</footer>

<script>
// ---------------- NAVIGATION ----------------
document.querySelectorAll("nav button").forEach(button => {
    button.addEventListener("click", () => {
        document.querySelectorAll("nav button").forEach(b =>
            b.classList.remove("active")
        );

        document.querySelectorAll(".page").forEach(page =>
            page.classList.remove("active")
        );

        button.classList.add("active");
        document.getElementById(button.dataset.page)
            .classList.add("active");
    });
});

// ---------------- EEG WAVE ANIMATION ----------------
const waveCanvas = document.getElementById("waveCanvas");
const waveCtx = waveCanvas.getContext("2d");
let waveOffset = 0;

function resizeCanvas(canvas) {
    const rect = canvas.getBoundingClientRect();
    const dpr = window.devicePixelRatio || 1;

    canvas.width = Math.max(1, Math.round(rect.width * dpr));
    canvas.height = Math.max(1, Math.round(rect.height * dpr));

    const ctx = canvas.getContext("2d");
    ctx.setTransform(dpr, 0, 0, dpr, 0, 0);

    return { width: rect.width, height: rect.height };
}

function drawWave() {
    const { width, height } = resizeCanvas(waveCanvas);

    waveCtx.clearRect(0, 0, width, height);

    waveCtx.strokeStyle = "#1e3650";
    waveCtx.lineWidth = 1;

    for (let y = 20; y < height; y += 25) {
        waveCtx.beginPath();
        waveCtx.moveTo(0, y);
        waveCtx.lineTo(width, y);
        waveCtx.stroke();
    }

    waveCtx.beginPath();
    waveCtx.strokeStyle = "#67e8f9";
    waveCtx.lineWidth = 2;

    for (let x = 0; x < width; x++) {
        const y = height / 2
            + Math.sin((x + waveOffset) * 0.035) * 25
            + Math.sin((x + waveOffset) * 0.09) * 8
            + Math.sin((x + waveOffset) * 0.17) * 4;

        if (x === 0) waveCtx.moveTo(x, y);
        else waveCtx.lineTo(x, y);
    }

    waveCtx.stroke();
    waveOffset += 2;

    requestAnimationFrame(drawWave);
}

// ---------------- BRAIN NETWORK VISUALIZATION ----------------
const brainCanvas = document.getElementById("brainCanvas");
const brainCtx = brainCanvas.getContext("2d");

function drawBrain() {
    const { width, height } = resizeCanvas(brainCanvas);

    brainCtx.clearRect(0, 0, width, height);

    const nodes = [
        [0.50, 0.15], [0.28, 0.30], [0.72, 0.30],
        [0.18, 0.52], [0.50, 0.48], [0.82, 0.52],
        [0.33, 0.72], [0.67, 0.72], [0.50, 0.88]
    ];

    const links = [
        [0,1],[0,2],[1,2],[1,3],[1,4],[2,4],
        [2,5],[3,4],[4,5],[3,6],[4,6],[4,7],
        [5,7],[6,7],[6,8],[7,8]
    ];

    brainCtx.strokeStyle = "#365b8b";
    brainCtx.lineWidth = 1.5;

    links.forEach(([a, b]) => {
        brainCtx.beginPath();
        brainCtx.moveTo(nodes[a][0] * width, nodes[a][1] * height);
        brainCtx.lineTo(nodes[b][0] * width, nodes[b][1] * height);
        brainCtx.stroke();
    });

    nodes.forEach(([x, y], i) => {
        brainCtx.beginPath();
        brainCtx.arc(x * width, y * height, 6, 0, Math.PI * 2);
        brainCtx.fillStyle = i % 2 ? "#67e8f9" : "#a78bfa";
        brainCtx.fill();
    });
}

// ---------------- EMOTION SELECTION ----------------
let selectedEmotion = "";

const emotionInfo = {
    Happy: {
        icon: "😊",
        description: "Happy emotion selected for demonstration."
    },
    Sad: {
        icon: "😢",
        description: "Sad emotion selected for demonstration."
    },
    Calm: {
        icon: "😌",
        description: "Calm emotion selected for demonstration."
    }
};

document.querySelectorAll(".emotion").forEach(button => {
    button.addEventListener("click", () => {
        selectedEmotion = button.dataset.emotion;

        document.querySelectorAll(".emotion").forEach(b =>
            b.classList.remove("selected")
        );

        button.classList.add("selected");

        document.getElementById("emotionIcon").textContent =
            emotionInfo[selectedEmotion].icon;

        document.getElementById("emotionValue").textContent =
            selectedEmotion;

        document.getElementById("emotionDescription").textContent =
            emotionInfo[selectedEmotion].description;

        document.getElementById("message").textContent = "";
    });
});

// ---------------- SAVE RESULTS ----------------
const sessions = [];

document.getElementById("saveEmotion").addEventListener("click", () => {
    if (!selectedEmotion) {
        document.getElementById("message").textContent =
            "Please select Happy, Sad, or Calm first.";
        return;
    }

    const personInput = document.getElementById("person").value.trim();
    const notes = document.getElementById("notes").value.trim();

    const session = {
        person: personInput || "Anonymous",
        emotion: selectedEmotion,
        notes: notes || "No notes",
        time: new Date().toLocaleTimeString()
    };

    sessions.push(session);

    document.getElementById("message").textContent =
        "Emotion result saved successfully.";

    document.getElementById("resultEmotion").textContent =
        session.emotion;

    document.getElementById("resultPerson").textContent =
        "Person: " + session.person;

    updateHistory();
});

function updateHistory() {
    const history = document.getElementById("history");
    history.replaceChildren();

    document.getElementById("totalSessions").textContent =
        sessions.length;

    if (sessions.length === 0) {
        const row = history.insertRow();
        const cell = row.insertCell();
        cell.colSpan = 4;
        cell.textContent = "No results saved yet.";

        document.getElementById("resultEmotion").textContent =
            "No result";

        document.getElementById("resultPerson").textContent =
            "Person: —";

        return;
    }

    sessions.slice().reverse().forEach(session => {
        const row = history.insertRow();

        [
            session.person,
            session.emotion,
            session.notes,
            session.time
        ].forEach(value => {
            const cell = row.insertCell();
            cell.textContent = value;
        });
    });
}

// ---------------- CLEAR HISTORY ----------------
document.getElementById("clearHistory").addEventListener("click", () => {
    sessions.length = 0;
    updateHistory();

    document.getElementById("historyMessage").textContent =
        "Session history cleared.";
});

// Start visualizations
drawWave();
drawBrain();

window.addEventListener("resize", drawBrain);
</script>

</body>
</html>
