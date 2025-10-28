<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grace's Magical ABC Game</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

```
    body {
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
        background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        padding: 20px;
    }

    .game-container {
        background: white;
        border-radius: 30px;
        padding: 40px;
        max-width: 600px;
        width: 100%;
        box-shadow: 0 20px 40px rgba(0,0,0,0.1);
        border: 4px solid #a855f7;
    }

    .header {
        text-align: center;
        margin-bottom: 30px;
    }

    .unicorn-icon {
        font-size: 50px;
        margin-bottom: 10px;
    }

    .title {
        font-size: 32px;
        font-weight: bold;
        background: linear-gradient(45deg, #ec4899, #8b5cf6);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 10px;
    }

    .subtitle {
        color: #8b5cf6;
        font-size: 18px;
    }

    .progress-section {
        margin-bottom: 30px;
    }

    .progress-text {
        display: flex;
        justify-content: space-between;
        color: #8b5cf6;
        font-size: 14px;
        margin-bottom: 10px;
    }

    .progress-bar {
        background: #e9d5ff;
        height: 16px;
        border-radius: 10px;
        border: 2px solid #c084fc;
        overflow: hidden;
    }

    .progress-fill {
        background: linear-gradient(45deg, #f472b6, #8b5cf6);
        height: 100%;
        transition: width 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: flex-end;
        padding-right: 8px;
        color: white;
        font-size: 12px;
    }

    .letter-card {
        background: linear-gradient(135deg, #f472b6, #8b5cf6);
        border-radius: 20px;
        padding: 40px;
        margin-bottom: 30px;
        position: relative;
        border: 4px solid white;
        text-align: center;
    }

    .letter-icons {
        position: absolute;
        font-size: 30px;
    }

    .top-left { top: 10px; left: 10px; }
    .top-right { top: 10px; right: 10px; }
    .bottom-center { bottom: 10px; left: 50%; transform: translateX(-50%); }

    .letter-prompt {
        color: white;
        font-size: 20px;
        font-weight: bold;
        margin-bottom: 20px;
    }

    .current-letter {
        font-size: 120px;
        font-weight: bold;
        color: white;
        text-shadow: 0 4px 8px rgba(0,0,0,0.3);
    }

    .button-section {
        text-align: center;
        margin-bottom: 30px;
    }

    .instruction {
        color: #8b5cf6;
        font-weight: bold;
        margin-bottom: 20px;
    }

    .button-container {
        display: flex;
        gap: 20px;
    }

    .btn {
        flex: 1;
        padding: 20px;
        border: none;
        border-radius: 15px;
        font-size: 18px;
        font-weight: bold;
        cursor: pointer;
        transition: all 0.3s ease;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
    }

    .btn-correct {
        background: linear-gradient(45deg, #10b981, #059669);
        color: white;
    }

    .btn-wrong {
        background: linear-gradient(45deg, #f97316, #ec4899);
        color: white;
    }

    .btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    }

    .btn:disabled {
        opacity: 0.6;
        cursor: not-allowed;
        transform: none;
    }

    .feedback {
        text-align: center;
        padding: 20px;
        border-radius: 15px;
        margin: 20px 0;
        font-weight: bold;
        border: 2px solid;
    }

    .feedback-correct {
        background: linear-gradient(45deg, #dcfce7, #bbf7d0);
        color: #166534;
        border-color: #86efac;
    }

    .feedback-wrong {
        background: linear-gradient(45deg, #fed7aa, #fecaca);
        color: #c2410c;
        border-color: #fdba74;
    }

    .stats {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        gap: 15px;
        margin-bottom: 30px;
    }

    .stat-card {
        padding: 20px;
        border-radius: 15px;
        text-align: center;
        border: 2px solid;
    }

    .stat-correct {
        background: linear-gradient(45deg, #dcfce7, #bbf7d0);
        border-color: #86efac;
    }

    .stat-wrong {
        background: linear-gradient(45deg, #fed7aa, #fecaca);
        border-color: #fdba74;
    }

    .stat-remaining {
        background: linear-gradient(45deg, #e9d5ff, #ddd6fe);
        border-color: #c084fc;
    }

    .stat-icon {
        font-size: 24px;
        margin-bottom: 5px;
    }

    .stat-label {
        font-size: 12px;
        color: #8b5cf6;
        margin-bottom: 5px;
    }

    .stat-number {
        font-size: 20px;
        font-weight: bold;
    }

    .letters-section {
        margin-bottom: 30px;
    }

    .letters-group {
        margin-bottom: 20px;
        text-align: center;
    }

    .letters-title {
        font-size: 14px;
        font-weight: bold;
        margin-bottom: 10px;
    }

    .correct-title { color: #059669; }
    .wrong-title { color: #c2410c; }

    .letters-container {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
        justify-content: center;
    }

    .letter-badge {
        padding: 8px 12px;
        border-radius: 20px;
        font-size: 14px;
        font-weight: bold;
        border: 2px solid;
    }

    .letter-correct {
        background: linear-gradient(45deg, #86efac, #34d399);
        color: #166534;
        border-color: #059669;
    }

    .letter-wrong {
        background: linear-gradient(45deg, #fdba74, #fbbf24);
        color: #c2410c;
        border-color: #f97316;
    }

    .reset-btn {
        display: block;
        margin: 0 auto;
        padding: 10px 20px;
        background: none;
        border: none;
        color: #8b5cf6;
        cursor: pointer;
        font-size: 14px;
        font-weight: bold;
    }

    .reset-btn:hover {
        color: #7c3aed;
    }

    .completion-screen {
        text-align: center;
    }

    .completion-icon {
        font-size: 80px;
        margin-bottom: 20px;
    }

    .completion-title {
        font-size: 36px;
        font-weight: bold;
        background: linear-gradient(45deg, #ec4899, #8b5cf6);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        margin-bottom: 20px;
    }

    .completion-subtitle {
        font-size: 20px;
        color: #8b5cf6;
        margin-bottom: 30px;
    }

    .final-stats {
        background: linear-gradient(45deg, #fce7f3, #e9d5ff);
        border: 2px solid #c084fc;
        border-radius: 15px;
        padding: 20px;
        margin-bottom: 30px;
    }

    .final-stats-title {
        font-size: 18px;
        font-weight: bold;
        color: #7c3aed;
        margin-bottom: 15px;
    }

    .final-stat {
        color: #8b5cf6;
        margin-bottom: 5px;
    }

    .play-again-btn {
        background: linear-gradient(45deg, #f472b6, #8b5cf6);
        color: white;
        padding: 15px 30px;
        border: none;
        border-radius: 15px;
        font-size: 18px;
        font-weight: bold;
        cursor: pointer;
        display: flex;
        align-items: center;
        gap: 10px;
        margin: 0 auto;
    }

    .play-again-btn:hover {
        transform: translateY(-2px);
        box-shadow: 0 10px 20px rgba(0,0,0,0.2);
    }

    .loading {
        text-align: center;
        padding: 40px;
        color: #8b5cf6;
        font-weight: bold;
        animation: pulse 2s infinite;
    }

    @keyframes pulse {
        0%, 100% { opacity: 1; }
        50% { opacity: 0.5; }
    }

    @media (max-width: 600px) {
        .game-container {
            padding: 20px;
        }

        .title {
            font-size: 24px;
        }

        .current-letter {
            font-size: 80px;
        }

        .button-container {
            flex-direction: column;
        }

        .stats {
            grid-template-columns: 1fr;
            gap: 10px;
        }
    }
</style>
```

</head>
<body>
    <div class="game-container">
        <div id="game-content">
            <!-- Game content will be inserted here by JavaScript -->
        </div>
    </div>

```
<script>
    // Game state
    let gameState = {
        allLetters: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split(''),
        remainingLetters: [],
        correctLetters: [],
        wrongLetters: [],
        currentLetter: '',
        feedback: '',
        gameComplete: false,
        waitingForAnswer: false
    };

    // Letter icons mapping
    const letterIcons = {
        'A': { top: '✈️', bottom: '🍎' },
        'B': { top: '🎈', bottom: '🐻' },
        'C': { top: '🍪', bottom: '🐱' },
        'D': { top: '🦆', bottom: '🐕' },
        'E': { top: '🐘', bottom: '🥚' },
        'F': { top: '🌸', bottom: '🐸' },
        'G': { top: '🦒', bottom: '🍇' },
        'H': { top: '❤️', bottom: '🏠' },
        'I': { top: '🐛', bottom: '🍦' },
        'J': { top: '🕺', bottom: '🃏' },
        'K': { top: '🪁', bottom: '🔑' },
        'L': { top: '🍃', bottom: '🦁' },
        'M': { top: '🌙', bottom: '🐒' },
        'N': { top: '🪺', bottom: '🥜' },
        'O': { top: '🍊', bottom: '🐙' },
        'P': { top: '🍕', bottom: '🐧' },
        'Q': { top: '❓', bottom: '👸' },
        'R': { top: '🌈', bottom: '🚀' },
        'S': { top: '⭐', bottom: '🐍' },
        'T': { top: '🌳', bottom: '🐅' },
        'U': { top: '🦄', bottom: '☂️' },
        'V': { top: '💜', bottom: '🌋' },
        'W': { top: '🌊', bottom: '🐋' },
        'X': { top: '❌', bottom: '📦' },
        'Y': { top: '💛', bottom: '🧶' },
        'Z': { top: '⚡', bottom: '🦓' }
    };

    // Initialize game
    function initGame() {
        gameState.remainingLetters = [...gameState.allLetters];
        gameState.correctLetters = [];
        gameState.wrongLetters = [];
        gameState.currentLetter = '';
        gameState.feedback = '';
        gameState.gameComplete = false;
        gameState.waitingForAnswer = false;
        pickRandomLetter();
    }

    // Pick random letter
    function pickRandomLetter() {
        if (gameState.remainingLetters.length === 0) {
            gameState.gameComplete = true;
            render();
            return;
        }

        const randomIndex = Math.floor(Math.random() * gameState.remainingLetters.length);
        gameState.currentLetter = gameState.remainingLetters[randomIndex];
        gameState.feedback = '';
        gameState.waitingForAnswer = true;
        render();
    }

    // Handle correct answer
    function handleCorrect() {
        if (!gameState.waitingForAnswer) return;

        gameState.waitingForAnswer = false;
        gameState.feedback = 'Magical! She got it right! 🦄✨';
        gameState.correctLetters.push(gameState.currentLetter);
        gameState.remainingLetters = gameState.remainingLetters.filter(letter => letter !== gameState.currentLetter);
        
        render();

        setTimeout(() => {
            pickRandomLetter();
        }, 2000);
    }

    // Handle incorrect answer
    function handleIncorrect() {
        if (!gameState.waitingForAnswer) return;

        gameState.waitingForAnswer = false;
        gameState.feedback = `Not quite! The answer is "${gameState.currentLetter}". The unicorns believe in her! 🦄💜`;
        gameState.wrongLetters.push(gameState.currentLetter);
        gameState.remainingLetters = gameState.remainingLetters.filter(letter => letter !== gameState.currentLetter);
        
        render();

        setTimeout(() => {
            pickRandomLetter();
        }, 3000);
    }

    // Calculate accuracy
    function getAccuracy() {
        const total = gameState.correctLetters.length + gameState.wrongLetters.length;
        if (total === 0) return 0;
        return Math.round((gameState.correctLetters.length / total) * 100);
    }

    // Get progress percentage
    function getProgress() {
        const total = gameState.correctLetters.length + gameState.wrongLetters.length;
        return Math.round((total / 26) * 100);
    }

    // Render game
    function render() {
        const gameContent = document.getElementById('game-content');

        if (gameState.gameComplete) {
            gameContent.innerHTML = `
                <div class="completion-screen">
                    <div class="completion-icon">🦄</div>
                    <div class="completion-icon">⭐</div>
                    <h1 class="completion-title">🌟 Unicorn Magic Complete! 🌟</h1>
                    <p class="completion-subtitle">Grace has gone through all her magical letters!</p>
                    
                    <div class="final-stats">
                        <div class="final-stats-title">✨ Final Sparkle Stats ✨</div>
                        <div class="final-stat">Correct answers: ${gameState.correctLetters.length}</div>
                        <div class="final-stat">Wrong answers: ${gameState.wrongLetters.length}</div>
                        <div class="final-stat">Accuracy: ${getAccuracy()}%</div>
                    </div>
                    
                    <button class="play-again-btn" onclick="initGame()">
                        🔄 Play Again 🦄
                    </button>
                </div>
            `;
            return;
        }

        const icons = letterIcons[gameState.currentLetter] || { top: '✨', bottom: '🌈' };

        gameContent.innerHTML = `
            <div class="header">
                <div class="unicorn-icon">🦄</div>
                <h1 class="title">🌟 Grace's Magical ABC Game 🌟</h1>
                <p class="subtitle">Learning letters with unicorn friends!</p>
            </div>

            <div class="progress-section">
                <div class="progress-text">
                    <span>🦄 Progress: ${gameState.correctLetters.length + gameState.wrongLetters.length}/26 letters</span>
                    <span>✨ Accuracy: ${getAccuracy()}%</span>
                </div>
                <div class="progress-bar">
                    <div class="progress-fill" style="width: ${getProgress()}%">
                        ${getProgress() > 0 ? '🦄' : ''}
                    </div>
                </div>
            </div>

            <div class="letter-card">
                <div class="letter-icons top-left">${icons.top}</div>
                <div class="letter-icons top-right">✨</div>
                <div class="letter-prompt">What letter is this?</div>
                <div class="current-letter">${gameState.currentLetter}</div>
                <div class="letter-icons bottom-center">${icons.bottom}</div>
            </div>

            ${gameState.waitingForAnswer ? `
                <div class="button-section">
                    <div class="instruction">Listen to her answer, then click:</div>
                    <div class="button-container">
                        <button class="btn btn-correct" onclick="handleCorrect()">
                            ✅ Correct! 🦄
                        </button>
                        <button class="btn btn-wrong" onclick="handleIncorrect()">
                            ❌ Try Again 💜
                        </button>
                    </div>
                </div>
            ` : `
                <div class="loading">
                    Getting next magical letter... ✨
                </div>
            `}

            ${gameState.feedback ? `
                <div class="feedback ${gameState.feedback.includes('Magical') ? 'feedback-correct' : 'feedback-wrong'}">
                    ${gameState.feedback}
                </div>
            ` : ''}

            <div class="stats">
                <div class="stat-card stat-correct">
                    <div class="stat-icon">✅</div>
                    <div class="stat-label">Correct</div>
                    <div class="stat-number">${gameState.correctLetters.length}</div>
                </div>
                <div class="stat-card stat-wrong">
                    <div class="stat-icon">❌</div>
                    <div class="stat-label">Wrong</div>
                    <div class="stat-number">${gameState.wrongLetters.length}</div>
                </div>
                <div class="stat-card stat-remaining">
                    <div class="stat-icon">🦄</div>
                    <div class="stat-label">Remaining</div>
                    <div class="stat-number">${gameState.remainingLetters.length}</div>
                </div>
            </div>

            <div class="letters-section">
                ${gameState.correctLetters.length > 0 ? `
                    <div class="letters-group">
                        <div class="letters-title correct-title">✨ Correct Answers ✨</div>
                        <div class="letters-container">
                            ${gameState.correctLetters.sort().map(letter => 
                                `<span class="letter-badge letter-correct">${letter} ✅</span>`
                            ).join('')}
                        </div>
                    </div>
                ` : ''}

                ${gameState.wrongLetters.length > 0 ? `
                    <div class="letters-group">
                        <div class="letters-title wrong-title">💜 Letters to Practice More 💜</div>
                        <div class="letters-container">
                            ${gameState.wrongLetters.sort().map(letter => 
                                `<span class="letter-badge letter-wrong">${letter} 🦄</span>`
                            ).join('')}
                        </div>
                    </div>
                ` : ''}
            </div>

            <button class="reset-btn" onclick="initGame()">
                🔄 Start New Unicorn Adventure 🦄
            </button>
        `;
    }

    // Start the game when page loads
    document.addEventListener('DOMContentLoaded', function() {
        initGame();
    });
</script>
```

</body>
</html>
