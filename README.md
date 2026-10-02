<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>Abyss Laboratory - Title Screen</title>
    <style>
       #story-screen {
         position: absolute;
          top: 0;
          left: 0;
        width: 100%;
         height: 100%;
         padding: 40px;
       color: #FFFFFF;
           font-size: 20px;
          line-height: 1.8;
        } 
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: radial-gradient(circle at center, #2b0404 0%, #080101 70%, #000000 100%);
            color: #ffffff;
            font-family: 'Courier New', Courier, monospace; /* 改用帶有復古電腦/文件感 Monospace 字體 */
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            user-select: none;
        }

        /* 遊戲畫布框 */
        #game-container {
            position: relative;
            width: 800px;
            height: 600px;
            background-color: #050202;
            border: 3px solid #300a0a;
            box-shadow: 0 0 50px rgba(139, 0, 0, 0.4);
            overflow: hidden;
        }

        /* STATE_MENU: 暗黑血腥封面 */
        #menu-screen {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            /* 極深濃血色放射漸層 */
            background: radial-gradient(circle at center, #2b0404 0%, #080101 70%, #000000 100%);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            padding: 50px 20px;
            z-index: 10;
        }

        /* 警報閃爍動畫 */
        @keyframes alertPulse {
            0% {
                text-shadow: 0 0 10px #ff0000, 0 0 20px #8b0000;
                opacity: 0.85;
            }
            50% {
                text-shadow: 0 0 25px #ff0000, 0 0 50px #ff0000, 0 0 70px #8b0000;
                opacity: 1;
            }
            100% {
                text-shadow: 0 0 10px #ff0000, 0 0 20px #8b0000;
                opacity: 0.85;
            }
        }

        /* 警告警語呼吸燈 */
        @keyframes warningFlicker {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 0.9; }
        }

        /* 標題區塊 */
        .title-group {
            text-align: center;
            margin-top: 10px;
        }

        .warning-tag {
            color: #ff3333;
            font-size: 13px;
            letter-spacing: 5px;
            margin-bottom: 15px;
            animation: warningFlicker 2s infinite;
            font-weight: bold;
        }

        .main-title {
            font-size: 54px;
            font-weight: 900;
            letter-spacing: 6px;
            color: #ff1a1a;
            animation: alertPulse 3s infinite ease-in-out;
            margin-bottom: 5px;
            text-transform: uppercase;
        }

        .subtitle {
            font-size: 18px;
            letter-spacing: 8px;
            color: #a3a3a3;
            text-transform: uppercase;
            border-top: 1px solid #5a1111;
            border-bottom: 1px solid #5a1111;
            padding: 6px 0;
            margin-top: 10px;
        }

        /* 按鈕區塊 */
        .menu-buttons {
            display: flex;
            flex-direction: column;
            gap: 18px;
            width: 240px;
        }

        .menu-btn {
            padding: 12px 20px;
            font-size: 16px;
            font-weight: bold;
            font-family: inherit;
            color: #888888;
            background-color: rgba(10, 2, 2, 0.85);
            border: 1px solid #4a0e0e;
            cursor: pointer;
            transition: all 0.2s ease;
            letter-spacing: 3px;
            text-align: center;
            position: relative;
        }

        /* 滑鼠移上去時的效果：像血光閃爍 */
        .menu-btn:hover {
            color: #ffffff;
            background-color: #8b0000;
            border-color: #ff0000;
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.8);
            transform: scale(1.03);
        }

        .menu-btn:active {
            transform: scale(0.98);
        }

        /* 底部警語 */
        .footer-info {
            font-size: 11px;
            color: #442222;
            letter-spacing: 2px;
            text-align: center;
        }
         /*音樂按鈕 */
       #sound-btn {
    background-color: rgba(10, 2, 2, 0.85);
}

#game-canvas {
    width: 100%;
    height: 300px;
    background-color: #050b05;
    border: 2px solid #00ff00;
    margin-bottom: 20px;
    box-shadow: 0 0 15px rgba(0, 255, 0, 0.2);
}
.scene-tag {
    color: #00ff00;
    font-family: monospace;
    font-size: 1.2rem;
    letter-spacing: 2px;
    animation: blink 1.5s infinite; /* 文字閃爍 */
}
@keyframes blink {
    0% { opacity: 1; }
    50% { opacity: 0.3; }
    100% { opacity: 1; }
}

.choice-btn {
    display: block;
    width: 100%;
    margin: 10px 0;
    padding: 12px 20px;
    background-color: rgba(0, 20, 0, 0.8);
    color: #00ff00;
    border: 1px solid #00ff00;
    font-family: monospace;
    font-size: 1rem;
    cursor: pointer;
    text-align: left;
    transition: all 0.2s ease-in-out;
}

.choice-btn:hover {
    background-color: #00ff00;
    color: #000000;
    box-shadow: 0 0 10px #00ff00;
}
    </style>
</head>
<body>

<div id="game-container">
<!-- STATE_MENU: 恐怖恐怖風格封面 -->
    <div id="menu-screen">
        <div class="title-group">
            <div class="warning-tag">▲ WARNING: BIOHAZARD CONTAINMENT BREACH ▲</div>
            <h1 class="main-title">ABYSS LABORATORY</h1>
  </div>
        

        <div class="menu-buttons">
            <button id="sound-btn" class="menu-btn" onclick="toggleSound()">🔊 音效: 開</button>
            <button class="menu-btn" onclick="onStartClick()">進入遊戲</button>
            <button class="menu-btn" onclick="onLoadClick()">載入紀錄</button>
            <button class="menu-btn" onclick="onControlsClick()">操作指南</button>
        </div>

        <div class="footer-info">
            SYSTEM STATUS: CRITICAL | B3 SECTOR LOCKED<br>
            18-Week Project
        </div>
    </div>

<div id="story-screen" style="display: none;" onclick="nextSentence()">


   <!-- 1. 最上方：將 scene-box 替換為遊戲畫布 canvas -->
    <canvas id="game-canvas" width="600" height="300"></canvas>
    

    <!-- 2. 中間：對話框區域 -->
    <p id="story-text"></p>

    <!-- 3. 最下方：抉擇選項區域 -->
    <div id="choices-box" style="display: none;">
        <button class="choice-btn" onclick="chooseOption1()">1. 搜尋附近的實驗桌</button>
        <button class="choice-btn" onclick="chooseOption2()">2. 試著推開生鏽的鐵門</button>
    </div>

</div>

<script>

function onStartClick() {
    document.getElementById("menu-screen").style.display = "none";
    document.getElementById("story-screen").style.display = "block";
    textIndex = 0; // 歸零
    typeWriter();
}
    function onLoadClick() {
       
        alert("【打卡鐘紀錄】尚無存檔資料。");
    }

    function onControlsClick() {
        alert("【生存指南】\nWASD - 移動\n滑鼠 - 手電筒與瞄準\n左鍵 - 射擊/互動");
    }
let audioCtx = null;
let isPlaying = false;
let timer = null;
let storyLines = [
    "【系統紀錄】你睜開眼睛，四周是一片死寂的廢棄實驗室...",
    "【警報系統】警告：三號隔離區生化防護已失效！",
    "【未知聲音】『你...終於醒了嗎...？』"
];
let currentLineIndex = 0;
let textIndex = 0;

};// 繪製遊戲畫面與特戰員（含戰術背心與頭盔外貌）
function drawGame() {
    let canvas = document.getElementById("game-canvas");
    let ctx = canvas.getContext("2d");

    // 1. 清空畫布（夜視深綠底色）
    ctx.fillStyle = "#050b05";
    ctx.fillRect(0, 0, canvas.width, canvas.height);

    // 2. 手電筒微塵光束 (向右照射)
    let gradient = ctx.createRadialGradient(player.x, player.y, 10, player.x + 80, player.y, 90);
    gradient.addColorStop(0, "rgba(255, 255, 180, 0.4)");
    gradient.addColorStop(1, "rgba(255, 255, 180, 0.0)");
    ctx.fillStyle = gradient;
    ctx.beginPath();
    ctx.arc(player.x + 80, player.y, 70, -Math.PI / 5, Math.PI / 5);
    ctx.lineTo(player.x, player.y);
    ctx.fill();

    // 3. 特戰員身體 (戰術背心與雙腿)
    ctx.fillStyle = "#1a1f1a"; // 深灰綠戰術服
    ctx.fillRect(player.x - 8, player.y - 6, 16, 18); // 軀幹
    ctx.fillStyle = "#111111"; // 黑色戰術長褲
    ctx.fillRect(player.x - 7, player.y + 12, 5, 8); // 左腿
    ctx.fillRect(player.x + 2, player.y + 12, 5, 8); // 右腿

    // 4. 頭盔與頭部
    ctx.fillStyle = "#2d4a2d"; // 軍綠色戰術頭盔
    ctx.beginPath();
    ctx.arc(player.x, player.y - 4, 9, 0, Math.PI * 2);
    ctx.fill();

    // 5. 戰術夜視鏡 (強烈螢光綠發光)
    ctx.fillStyle = "#00ff66";
    ctx.shadowColor = "#00ff66";
    ctx.shadowBlur = 8;
    ctx.fillRect(player.x + 2, player.y - 7, 6, 4);
    ctx.shadowBlur = 0; // 還原發光效果

    // 6. 手槍與手電筒
    ctx.fillStyle = "#222222";
    ctx.fillRect(player.x + 6, player.y + 2, 10, 4);
}
function onStartClick() {
    // 隱藏選單、顯示故事畫面
    document.getElementById("menu-screen").style.display = "none";
    document.getElementById("story-screen").style.display = "block";
    
    // 新增這行：呼叫繪製函數，畫出特戰員！
    drawGame();

    // 開始打字機效果
    typeWriter();
}


function toggleSound() {
    if (!audioCtx) {
        audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    }
    
    isPlaying = !isPlaying; // 切換開關狀態
    const soundBtn = document.getElementById("sound-btn");
    
    if (isPlaying) {
        // 開啟：每 0.5 秒嗶一次
        timer = setInterval(playBeep, 500);
        soundBtn.innerText = "🔊 音效: 開";
    } else {
        // 關閉：清除定時器
        clearInterval(timer);
        soundBtn.innerText = "🔇 音效: 關";
    }
}

function playBeep() {
    let osc = audioCtx.createOscillator();
    let gain = audioCtx.createGain();
    
    osc.type = "sawtooth";
    osc.frequency.value = 880;
    
    osc.connect(gain);
    gain.connect(audioCtx.destination);
    
    osc.start();
    osc.stop(audioCtx.currentTime + 0.15);
}

  // 開頭劇情
function typeWriter() {
    let fullText = storyLines[currentLineIndex];
    if (textIndex < fullText.length) {
        document.getElementById("story-text").innerText = fullText.slice(0, textIndex + 1);
        textIndex++;
        setTimeout(typeWriter, 100);
    }
}


function nextSentence() {
    if (currentLineIndex < storyLines.length - 1) {
        currentLineIndex++;
        textIndex = 0;
        document.getElementById("story-text").innerText = "";
        typeWriter();
    } else {
        // 當劇情已經到最後一句時，顯示抉擇選項！
        document.getElementById("choices-box").style.display = "block";
    }
}

// 移動
window.addEventListener("keydown", function(event) {
    // 判斷按下的按鍵並改變特戰員座標
    if (event.key === "w" || event.key === "W" || event.key === "ArrowUp") {
        player.y -= 5; // 向上走
    } else if (event.key === "s" || event.key === "S" || event.key === "ArrowDown") {
        player.y += 5; // 向下走
    } else if (event.key === "a" || event.key === "A" || event.key === "ArrowLeft") {
        player.x -= 5; // 向左走
    } else if (event.key === "d" || event.key === "D" || event.key === "ArrowRight") {
        player.x += 5; // 向右走
    }

    drawGame();
});


</script>

</body>
</html>
