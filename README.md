
<!DOCTYPE html>
<html>
<head>
    <title>Romantic Surprise 💖</title>

    <style>
        body { margin: 0; font-family: Arial; text-align: center; }

        /* LOGIN */
        #loginPage {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: #f2f2f2;
        }

        .box { background: white; padding: 25px; border-radius: 10px; }

        input { padding: 10px; margin: 10px; width: 200px; }

        button {
            padding: 12px 25px;
            margin: 10px;
            font-size: 18px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
        }

        /* MAIN PAGE */
        #mainPage {
            display: none;
            height: 100vh;
            background: url('https://images.unsplash.com/photo-1501785888041-af3ef285b470?auto=format&fit=crop&w=1600&q=80') no-repeat center center/cover;
            color: white;
            position: relative;
            overflow: hidden;
        }

        #mainPage::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
        }

        .content {
            position: relative;
            z-index: 2;
            top: 50%;
            transform: translateY(-50%);
        }

        h1 { font-size: 50px; }
        p { font-size: 28px; }

        /* Moon */
        .moon {
            position: absolute;
            top: 50px;
            right: 80px;
            width: 120px;
            height: 120px;
            background: white;
            border-radius: 50%;
            box-shadow: 0 0 50px white;
        }

        /* Stars */
        .star {
            position: absolute;
            width: 3px;
            height: 3px;
            background: white;
            border-radius: 50%;
            animation: blink 2s infinite alternate;
        }

        @keyframes blink {
            from { opacity: 0.3; }
            to { opacity: 1; }
        }

        /* Falling */
        .fall {
            position: absolute;
            top: -50px;
            animation: fall linear infinite;
        }

        @keyframes fall {
            100% { transform: translateY(100vh); }
        }

        /* Background text */
        #bgText {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            font-size: 80px;
            color: rgba(255,255,255,0.08);
        }

        #shayariBox {
            font-size: 30px;
            text-shadow: 0 0 10px pink;
        }
    </style>
</head>

<body>

<!-- LOGIN -->
<div id="loginPage">
    <div class="box">
        <h2>Birthday Login 🎂</h2>

        <form onsubmit="start(event)">
            <input type="text" id="name" placeholder="Enter Name" required><br>
            <input type="date" required><br>
            <button type="submit">Submit</button>
        </form>
    </div>
</div>

<!-- MAIN -->
<div id="mainPage">

    <div class="moon"></div>
    <div id="bgText">💖 I Like You Cutie 💖</div>

    <div class="content">

        <h1 id="message"></h1>

        <!-- STEP BUTTONS -->
        <button onclick="showMessage()" id="btn1" style="background:#ff69b4;">Click Me 💖</button>
        <p id="specialText"></p>

        <button onclick="showFinal()" id="btn2" style="display:none; background:#6a5acd;">Next 💜</button>
        <p id="finalText"></p>

        <button onclick="showBirthday()" id="btn3" style="display:none; background:#ff4500;">Surprise 🎁</button>
        <p id="birthdayText"></p>

        <button onclick="showEmoji()" id="btn4" style="display:none; background:#20b2aa;">More 💕</button>
        <p id="emojiText"></p>

        <button onclick="showShayari()" id="btn5" style="display:none; background:#ff1493;">Romantic 💝</button>
        <div id="shayariBox"></div>

    </div>

</div>

<script>
function start(event) {
    event.preventDefault();

    let name = document.getElementById("name").value;

    document.getElementById("loginPage").style.display = "none";
    document.getElementById("mainPage").style.display = "block";

    document.getElementById("message").innerHTML =
    "💖🌸💐 Hi Cutie " + name + " 💐🌸💖";

    createStars();
    setInterval(createFalling, 300);
}

// STEP FUNCTIONS
function showMessage() {
    document.getElementById("specialText").innerHTML =
    "🎉❤️🌸 Today’s special day for you 💐💖";

    document.getElementById("btn2").style.display = "inline-block";
}

function showFinal() {
    document.getElementById("finalText").innerHTML =
    "💖🌸 This is for my cutie 💐❤️";

    document.getElementById("btn3").style.display = "inline-block";
}

function showBirthday() {
    document.getElementById("birthdayText").innerHTML =
    "🎂💖🌸 Happy Birthday Cutie 💐❤️";

    document.getElementById("btn4").style.display = "inline-block";
}

function showEmoji() {
    document.getElementById("emojiText").innerHTML =
    "💐❤️🌸🌺🎂💖🌹";

    document.getElementById("btn5").style.display = "inline-block";
}

function showShayari() {
    document.getElementById("shayariBox").innerHTML =
    "💖🌹<br>Tumhari muskaan meri jaan hai,<br>Tumse hi meri pehchaan hai,<br>Har pal bas tum hi yaad aate ho,<br>Mere liye tum hi meri duniya ho 💐❤️";
}

// FALLING
function createFalling() {
    const items = ["❤️","🌸","💐","🌺","🌹"];
    const el = document.createElement("div");
    el.className = "fall";
    el.innerHTML = items[Math.floor(Math.random() * items.length)];

    el.style.left = Math.random() * window.innerWidth + "px";
    el.style.fontSize = (40 + Math.random() * 50) + "px";
    el.style.animationDuration = (3 + Math.random() * 5) + "s";

    document.body.appendChild(el);
    setTimeout(() => el.remove(), 8000);
}

// STARS
function createStars() {
    for (let i = 0; i < 100; i++) {
        let star = document.createElement("div");
        star.className = "star";
        star.style.top = Math.random() * window.innerHeight + "px";
        star.style.left = Math.random() * window.innerWidth + "px";
        document.body.appendChild(star);
    }
}
</script>

</body>
</html>
