<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的心意 - 向你表白</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ff9a9e 0%, #fad0c4 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }
        
        .container {
            background-color: rgba(255, 255, 255, 0.9);
            width: 90%;
            max-width: 600px;
            border-radius: 20px;
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1);
            padding: 40px;
            text-align: center;
            position: relative;
            z-index: 10;
            animation: fadeIn 1.5s ease;
        }
        
        h1 {
            color: #ff6b6b;
            margin-bottom: 20px;
            font-size: 2.5rem;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.1);
        }
        
        .heart-icon {
            font-size: 4rem;
            color: #ff6b6b;
            margin: 20px 0;
            animation: heartbeat 1.5s infinite;
        }
        
        .message {
            background-color: #fff5f7;
            padding: 20px;
            border-radius: 15px;
            margin: 20px 0;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            opacity: 0;
            transform: translateY(20px);
            transition: all 0.8s ease;
        }
        
        .message.show {
            opacity: 1;
            transform: translateY(0);
        }
        
        p {
            color: #555;
            line-height: 1.8;
            margin-bottom: 15px;
            font-size: 1.1rem;
        }
        
        .special-name {
            color: #ff6b6b;
            font-weight: bold;
            font-size: 1.2rem;
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 30px;
        }
        
        button {
            padding: 12px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        #yesBtn {
            background-color: #ff6b6b;
            color: white;
        }
        
        #noBtn {
            background-color: #e0e0e0;
            color: #555;
        }
        
        button:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
        }
        
        #yesBtn:hover {
            background-color: #ff5252;
        }
        
        #noBtn:hover {
            background-color: #d5d5d5;
        }
        
        .hearts-container {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: 1;
        }
        
        .heart {
            position: absolute;
            width: 20px;
            height: 20px;
            background-color: #ff6b6b;
            transform: rotate(45deg);
            opacity: 0;
        }
        
        .heart:before, .heart:after {
            content: '';
            width: 20px;
            height: 20px;
            background-color: #ff6b6b;
            border-radius: 50%;
            position: absolute;
        }
        
        .heart:before {
            top: -10px;
            left: 0;
        }
        
        .heart:after {
            top: 0;
            left: -10px;
        }
        
        .final-message {
            display: none;
            margin-top: 30px;
            padding: 20px;
            background-color: #ffebee;
            border-radius: 15px;
            animation: pulse 2s infinite;
        }
        
        .music-control {
            position: absolute;
            top: 20px;
            right: 20px;
            background-color: rgba(255, 255, 255, 0.8);
            width: 40px;
            height: 40px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
            z-index: 100;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        @keyframes heartbeat {
            0% { transform: scale(1); }
            50% { transform: scale(1.1); }
            100% { transform: scale(1); }
        }
        
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.02); }
            100% { transform: scale(1); }
        }
        
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-1000px) rotate(720deg); opacity: 0; }
        }
        
        @media (max-width: 600px) {
            .container {
                padding: 25px;
            }
            
            h1 {
                font-size: 2rem;
            }
            
            .buttons {
                flex-direction: column;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="hearts-container" id="heartsContainer"></div>
    
    <div class="music-control" id="musicControl">
        <span>??</span>
    </div>
    
    <div class="container">
        <h1>我喜欢你</h1>
        <div class="heart-icon">??</div>
        
        <div class="message" id="message1">
            <p>从第一次见到你，我的世界就变得不一样了。</p>
        </div>
        
        <div class="message" id="message2">
            <p>你的笑容像阳光一样温暖，照亮了我生活的每一个角落。</p>
        </div>
        
        <div class="message" id="message3">
            <p>和你在一起的每一刻，都让我感到无比幸福和安心。</p>
        </div>
        
        <div class="message" id="message4">
            <p>所以，我想问你：</p>
            <p>你愿意和我在一起吗，<span class="special-name" id="namePlaceholder">亲爱的</span>？</p>
        </div>
        
        <div class="buttons">
            <button id="yesBtn">我愿意 ??</button>
            <button id="noBtn">我再想想</button>
        </div>
        
        <div class="final-message" id="finalMessage">
            <h2>太棒了！??</h2>
            <p>从今天起，你就是我的全世界！</p>
            <p>我会用我全部的爱来珍惜你，保护你。</p>
            <div class="heart-icon">??</div>
        </div>
    </div>
    
    <audio id="bgMusic" loop>
        <source src="https://assets.mixkit.co/music/preview/mixkit-serene-view-443.mp3" type="audio/mpeg">
    </audio>

    <script>
        // 获取DOM元素
        const messages = document.querySelectorAll('.message');
        const yesBtn = document.getElementById('yesBtn');
        const noBtn = document.getElementById('noBtn');
        const finalMessage = document.getElementById('finalMessage');
        const heartsContainer = document.getElementById('heartsContainer');
        const musicControl = document.getElementById('musicControl');
        const bgMusic = document.getElementById('bgMusic');
        const namePlaceholder = document.getElementById('namePlaceholder');
        
        // 询问对方的名字
        let lovedName = prompt("请输入你心爱之人的名字:", "亲爱的");
        if (lovedName && lovedName.trim() !== "") {
            namePlaceholder.textContent = lovedName;
        }
        
        // 逐步显示消息
        let messageIndex = 0;
        const showMessages = () => {
            if (messageIndex < messages.length) {
                messages[messageIndex].classList.add('show');
                messageIndex++;
                setTimeout(showMessages, 1500);
            }
        };
        
        // 页面加载后开始显示消息
        window.addEventListener('load', () => {
            setTimeout(showMessages, 1000);
        });
        
        // 创建漂浮的心形
        const createHearts = () => {
            for (let i = 0; i < 30; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.classList.add('heart');
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.animation = `float ${6 + Math.random() * 6}s linear forwards`;
                    heart.style.opacity = Math.random() * 0.7 + 0.3;
                    heart.style.width = heart.style.height = (10 + Math.random() * 20) + 'px';
                    heartsContainer.appendChild(heart);
                    
                    // 动画结束后移除心形
                    setTimeout(() => {
                        heart.remove();
                    }, 12000);
                }, i * 300);
            }
        };
        
        // 定期创建心形
        setInterval(createHearts, 5000);
        
        // "我愿意"按钮点击事件
        yesBtn.addEventListener('click', () => {
            // 隐藏按钮和消息
            document.querySelector('.buttons').style.display = 'none';
            messages.forEach(msg => msg.style.display = 'none');
            
            // 显示最终消息
            finalMessage.style.display = 'block';
            
            // 创建更多心形
            for (let i = 0; i < 50; i++) {
                setTimeout(() => {
                    const heart = document.createElement('div');
                    heart.classList.add('heart');
                    heart.style.left = Math.random() * 100 + 'vw';
                    heart.style.animation = `float ${3 + Math.random() * 4}s linear forwards`;
                    heart.style.opacity = Math.random() * 0.7 + 0.3;
                    heart.style.width = heart.style.height = (15 + Math.random() * 25) + 'px';
                    heartsContainer.appendChild(heart);
                    
                    setTimeout(() => {
                        heart.remove();
                    }, 8000);
                }, i * 100);
            }
            
            // 播放庆祝音效
            try {
                const audio = new Audio('https://assets.mixkit.co/sfx/preview/mixkit-happy-crowd-celebration-454.mp3');
                audio.play();
            } catch(e) {
                console.log("音效播放失败:", e);
            }
        });
        
        // "我再想想"按钮点击事件
        noBtn.addEventListener('click', () => {
            // 移动按钮位置
            const randomX = Math.random() * 200 - 100;
            const randomY = Math.random() * 200 - 100;
            noBtn.style.transform = `translate(${randomX}px, ${randomY}px)`;
            
            // 改变按钮文本
            const texts = ["确定吗?", "再考虑一下?", "真的不要吗?", "给我个机会!", "求求你了!"];
            noBtn.textContent = texts[Math.floor(Math.random() * texts.length)];
            
            // 让"我愿意"按钮变大一点
            yesBtn.style.transform = 'scale(1.1)';
            setTimeout(() => {
                yesBtn.style.transform = 'scale(1)';
            }, 300);
        });
        
        // 音乐控制
        let musicPlaying = false;
        musicControl.addEventListener('click', () => {
            if (musicPlaying) {
                bgMusic.pause();
                musicControl.innerHTML = '??';
            } else {
                bgMusic.play().catch(e => {
                    console.log("自动播放被阻止，需要用户交互:", e);
                    alert("请点击页面任意位置以播放背景音乐");
                });
                musicControl.innerHTML = '??';
            }
            musicPlaying = !musicPlaying;
        });
        
        // 用户首次交互时尝试播放音乐
        document.addEventListener('click', () => {
            if (!musicPlaying) {
                bgMusic.play().then(() => {
                    musicPlaying = true;
                    musicControl.innerHTML = '??';
                }).catch(e => {
                    console.log("音乐播放失败:", e);
                });
            }
        }, { once: true });
    </script>
</body>
</html>
