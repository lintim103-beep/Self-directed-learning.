<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <title>Abyss Laboratory - Title Screen</title>
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            background: radial-gradient(circle at center, #2b0404 0%, #080101 70%, #000000 100%);
            color: #ffffff;
            font-family: 'Courier New', Courier, monospace;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            user-select: none;
        }

        #game-container {
            position: relative;
            width: 800px;
            height: 600px;
            background-color: #050202;
            border: 3px solid #300a0a;
            box-shadow: 0 0 50px rgba(139, 0, 0, 0.4);
            overflow: hidden;
        }

        #menu-screen {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: radial-gradient(circle at center, #2b0404 0%, #080101 70%, #000000 100%);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            padding: 50px 20px;
            z-index: 10;
        }

        @keyframes alertPulse {
            0%, 100% {
                text-shadow: 0 0 10px #ff0000, 0 0 20px #8b0000;
                opacity: 0.85;
            }
            50% {
                text-shadow: 0 0 25px #ff0000, 0 0 50px #ff0000, 0 0 70px #8b0000;
                opacity: 1;
            }
        }

        @keyframes warningFlicker {
            0%, 100% { opacity: 0.3; }
            50% { opacity: 0.9; }
        }

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
        }

        .menu-btn:hover {
            color: #ffffff;
            background-color: #8b0000;
            border-color: #ff0000;
            box-shadow: 0 0 20px rgba(255, 0, 0, 0.8);
            transform: scale(1.03);
        }

        .footer-info {
            font-size: 11px;
            color: #442222;
            letter-spacing: 2px;
            text-align: center;
        }

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

        #game-canvas {
            width: 100%;
            height: 300px;
            background-color: #050b05;
            border: 2px solid #00ff00;
            margin-bottom: 20px;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.2);
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
    <body>

<div id="game-container">
    <!-- 封面選單 -->
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

    <!-- 遊戲故事與畫布區域 -->
    <div id="story-screen" style="display: none;" onclick="nextSentence()">
        <canvas id="game-canvas" width="600" height="300"></canvas>
        <p id="story-text"></p>
        <div id="choices-box" style="display: none;">
            <button class="choice-btn" onclick="chooseOption1()">1. 搜尋附近的實驗桌</button>
            <button class="choice-btn" onclick="chooseOption2()">2. 試著推開生鏽的鐵門</button>
        </div>
    </div>
</div>

</body>
</html>
</head>

