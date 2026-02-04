---
title: Strands
toc: false
---

<style>
@import url('https://fonts.googleapis.com/css2?family=Karla:wght@400;700&family=Chomsky&display=swap');

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), auto;
}

:root {
    --nyt-blue: #5a594e;
    --nyt-yellow: #FFD43B;
    --nyt-light-blue: #85c7f2;
    --bg-white: #ffffff;
    --bg-pink: #ffcbd1;
    --text-dark: #121212;
    --border-gray: #dfdfdf;
    --hint-bg: #efefe6;
    --found-red: #803c40;
    --spangram-pink: #b56f76;
}

body {
    font-family: 'Karla', -apple-system, sans-serif;
    background: var(--bg-pink);
    color: var(--text-dark);
}

.nyt-header {
    width: 100%;
    background: white;
    border-bottom: 1px solid var(--border-gray);
    padding: 12px 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: -1rem -1rem 0 -1rem;
}

.nyt-logo {
    font-family: 'Chomsky', serif;
    font-size: 28px;
    font-weight: 700;
    letter-spacing: -0.5px;
}

.menu-icon {
    font-size: 24px;
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), pointer;
    color: var(--text-dark);
}

.game-container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
}

.title-section {
    text-align: center;
    margin: 20px 0 30px 0;
}

.game-title {
    font-size: 42px;
    font-weight: 700;
    letter-spacing: -1px;
    margin-bottom: 8px;
    color: var(--text-dark);
}

.game-date {
    font-size: 14px;
    color: #666;
    text-transform: uppercase;
    letter-spacing: 0.5px;
}

.theme-container {
    background: transparent;
    border: 4px dashed #803c40;
    border-radius: 8px;
    padding: 16px 20px;
    margin-bottom: 20px;
    text-align: center;
}

.theme-label {
    font-size: 12px;
    color: #803c40;
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 6px;
}

.theme-text {
    font-size: 24px;
    font-weight: 700;
}

.grid {
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    gap: 4px;
    margin-bottom: 20px;
    background: white;
    padding: 12px;
    border-radius: 8px;
    border: 1px solid var(--border-gray);
}

.letter {
    aspect-ratio: 1;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 20px;
    font-weight: 700;
    background: white;
    border: 2px solid var(--border-gray);
    border-radius: 4px;
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), pointer;
    transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    user-select: none;
    color: var(--text-dark);
    position: relative;
}

.letter:hover:not(.found):not(.spangram-found) {
    border-color: var(--nyt-blue);
    transform: scale(1.08);
    box-shadow: 0 2px 8px rgba(90, 89, 78, 0.15);
    z-index: 10;
}

.letter.selecting {
    background: var(--hint-bg);
    border-color: var(--nyt-blue);
    border-width: 3px;
    transform: scale(1.05);
    box-shadow: 0 2px 12px rgba(90, 89, 78, 0.2);
    z-index: 5;
}

.letter.found {
    background: var(--found-red);
    color: white;
    border-color: var(--found-red);
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), default;
    font-weight: 700;
    animation: popIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.letter.spangram-found {
    background: var(--spangram-pink);
    color: white;
    border-color: var(--spangram-pink);
    animation: popIn 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

@keyframes popIn {
    0% { 
        transform: scale(0.8);
        opacity: 0.5;
    }
    50% { 
        transform: scale(1.15);
    }
    100% { 
        transform: scale(1);
        opacity: 1;
    }
}

.current-selection {
    min-height: 50px;
    text-align: center;
    margin-bottom: 15px;
    padding: 0 20px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.current-word {
    font-size: 28px;
    font-weight: 700;
    letter-spacing: 3px;
    color: var(--nyt-blue);
    transition: all 0.2s ease;
}

.current-word.shake {
    animation: shake 0.4s ease;
}

@keyframes shake {
    0%, 100% { transform: translateX(0); }
    25% { transform: translateX(-8px); }
    75% { transform: translateX(8px); }
}

.hint-section {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

.hint-button {
    background: #cc3333;
    border: 2px solid var(--bg-pink);
    border-radius: 20px;
    padding: 10px 24px;
    font-size: 14px;
    font-weight: 700;
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), pointer;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
}

.hint-button:hover:not(:disabled) {
    border-color: var(--found-red);
    background: var(--found-red);
    transform: translateY(-2px);
    box-shadow: 0 4px 12px rgba(90, 89, 78, 0.15);
}

.hint-button:active:not(:disabled) {
    transform: translateY(0);
}

.hint-button:disabled {
    opacity: 0.9;
    cursor: url('https://www.pngall.com/wp-content/uploads/11/Cupid-Background-PNG.png'), not-allowed;
}

.hint-progress {
    width: 40px;
    height: 6px;
    background: #efefe6;
    border-radius: 3px;
    overflow: hidden;
    -webkit-overflow-scrolling: touch;
}

.hint-fill {
    height: 100%;
    background: var(--found-red);
    width: 0%;
    transition: width 0.4s cubic-bezier(0.4, 0, 0.2, 1);
}

.found-counter {
    text-align: center;
    margin-bottom: 30px;
    font-size: 14px;
    color: #cc3333;
    transition: all 0.3s ease;
}

.counter-number {
    font-weight: 700;
    color: var(--text-light);
    transition: all 0.3s ease;
}

.counter-number.pulse {
    animation: pulse 0.5s ease;
}

@keyframes pulse {
    0%, 100% { transform: scale(1); }
    50% { transform: scale(1.2); color: var(--found-red); }
}

.victory-modal {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%vw;
    height: 100%vh;
    background: rgba(0, 0, 0, 0.6);
    backdrop-filter: blur(4px);
    z-index: 1000;
    align-items: center;
    justify-content: center;
    animation: fadeIn 0.4s ease;
    padding: 0;
    overflow: hidden;
}

.victory-modal.active {
    display: flex;
}

.victory-content {
    background: white;
    border-radius: 16px;
    padding: 50px;
    max-width: 800px;
    width: 90%;
    max-height: 85vh;
    overflow-y: auto;
    text-align: center;
    animation: slideUp 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.3);
    margin: auto;
}

@keyframes slideUp {
    from {
        transform: translateY(100px) scale(0.8);
        opacity: 0;
    }
    to {
        transform: translateY(0) scale(1);
        opacity: 1;
    }
}

@keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
}

.victory-title {
    font-size: 23px;
    font-weight: 550;
    margin-bottom: 20px;
    color: var(--text-dark);
}

.victory-heart {
    font-size: 65px;
    margin: 10px 0;
    animation: heartBeat 1.5s ease-in-out infinite;
}

@keyframes heartBeat {
    0%, 100% { transform: scale(1); }
    10%, 30% { transform: scale(1.15); }
    20%, 40% { transform: scale(1); }
}

.victory-message {
    font-size: 26px;
    line-height: 1.6;
    color: var(--text-dark);
    margin-bottom: 30px;
    font-style: italic;
}

.email-prompt {
    margin-top: 30px;
    padding-top: 30px;
    border-top: 2px solid #ffcbd1;
    animation: fadeInUp 1s ease 1s backwards;
}

.email-button {
    background: linear-gradient(90deg, 
        #ff0000 0%, 
        #ff7f00 16.66%, 
        #ffff00 33.33%, 
        #00ff00 50%, 
        #0000ff 66.66%, 
        #4b0082 83.33%, 
        #9400d3 100%);
    background-size: 200% 100%;
    color: white;
    border: none;
    border-radius: 50px;
    padding: 18px 40px;
    font-size: 20px;
    font-weight: 700;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
    font-family: 'Karla', sans-serif;
    animation: rainbow-shift 3s ease infinite;
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.3);
}

@keyframes rainbow-shift {
    0%, 100% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
}

.email-button:hover {
    transform: translateY(-3px) scale(1.05);
    box-shadow: 0 6px 25px rgba(0, 0, 0, 0.4);
    animation: rainbow-shift 1s ease infinite;
}

.email-button:active {
    transform: translateY(-1px) scale(1.03);
}

.valentine-question {
    font-size: 32px;
    font-weight: 700;
    color: #b56f76;
    margin-top: 20px;
    animation: fadeInUp 0.8s ease 0.5s backwards;
}

@keyframes fadeInUp {
    from {
        opacity: 0;
        transform: translateY(20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

@media (max-width: 600px) {
    .game-title {
        font-size: 32px;
    }
    
    .letter {
        font-size: 16px;
    }
    
    .grid {
        gap: 3px;
        padding: 8px;
    }
    
    .current-word {
        font-size: 22px;
    }
    
    .victory-modal {
        padding: 0;
    }
    
    .victory-content {
        padding: 15px;
        max-height: 75vh;
        width: 95%;
        border-radius: 12px;
    }
    
    .victory-title {
        font-size: 16px;
        margin-bottom: 6px;
        line-height: 1.2;
    }
    
    .victory-heart {
        font-size: 35px;
        margin: 6px 0;
    }
    
    .victory-message {
        font-size: 14px;
        margin-bottom: 8px;
        line-height: 1.3;
    }
    
    .valentine-question {
        font-size: 16px;
        margin-top: 6px;
        line-height: 1.2;
    }
    
    .email-prompt {
        margin-top: 8px;
        padding-top: 8px;
    }
    
    .email-button {
        padding: 10px 20px;
        font-size: 14px;
    }
}

</style>

<div class="nyt-header">
    <div class="nyt-logo">The M&M Times</div>
    <div class="menu-icon">☰</div>
</div>

<div class="game-container">
    <div class="title-section">
        <h1 class="game-title">Valentine's Strands</h1>
        <div class="game-date" id="gameDate"></div>
    </div>
    <div class="theme-container">
        <div class="theme-label">Today's Theme</div>
        <div class="theme-text">🧑🏻‍❤️‍💋‍🧑🏾</div>
    </div>
    <div class="current-selection">
        <div class="current-word" id="currentWord"></div>
    </div>
    <div class="grid" id="grid"></div>
    <div class="hint-section">
        <button class="hint-button" id="hintBtn" disabled>
            <span>💡</span>
            <span>Hint</span>
            <div class="hint-progress">
                <div class="hint-fill" id="hintFill"></div>
            </div>
        </button>
    </div>
    <div class="found-counter">
        <span class="counter-number" id="foundCount">0</span> of <span class="counter-number">8</span> theme words found
    </div>
</div>

<div class="victory-modal" id="victoryModal">
    <div class="victory-content">
        <div class="victory-title">Woo-Hoo!! Puzzle Complete!!! Let's Fucking Goooooo 💪💪💪 AYE AYE AYE 🗣️ </div>
        <div class="victory-heart">bada bing bada boom 🎯</div>
        <div class="victory-message">
            MARINA!!!!!,<br>
            You solved the puzzle!!
        </div>
        <div class="valentine-question">
            💌 Will you be my Valentine? 💌
        </div>
        <div class="email-prompt">
            <button class="email-button" id="emailButton">
                Click here to say YES 👅
            </button>
        </div>
    </div>
</div>

```js
// Wait for DOM to be ready
setTimeout(() => {
    // Set current date
    const gameDateEl = document.getElementById('gameDate');
    if (gameDateEl) {
        const today = new Date();
        const options = { year: 'numeric', month: 'long', day: 'numeric' };
        gameDateEl.textContent = today.toLocaleDateString('en-US', options);
    }

    // Game Configuration - "Dear my Marina, will you be my Valentine?"
    const gameWords = ['DEAR', 'MY', 'MARINA', 'WILL', 'YOU', 'BE', 'MY', 'VALENTINE'];
    const GRID_ROWS = 6;
    const GRID_COLS = 8;
    const GRID_SIZE = GRID_ROWS * GRID_COLS;

    // Common English words dictionary for validation (extended list)
    const englishWords = new Set([
        'THE', 'AND', 'FOR', 'ARE', 'BUT', 'NOT', 'YOU', 'ALL', 'CAN', 'HER', 'WAS', 'ONE', 
        'OUR', 'OUT', 'DAY', 'HAD', 'HAS', 'HIS', 'HOW', 'MAN', 'NEW', 'NOW', 'OLD', 'SEE',
        'TWO', 'WAY', 'WHO', 'BOY', 'ITS', 'LET', 'PUT', 'SAY', 'SHE', 'TOO', 'USE', 'MAKE',
        'LIKE', 'TIME', 'VERY', 'WHEN', 'THEM', 'BEEN', 'CALL', 'FIND', 'LONG', 'MANY', 'MORE',
        'PART', 'THAN', 'THEN', 'WELL', 'WORK', 'YEAR', 'BACK', 'CAME', 'COME', 'GOOD', 'HAND',
        'HIGH', 'JUST', 'KEEP', 'LAST', 'LEFT', 'LIFE', 'LIVE', 'MADE', 'MUST', 'NAME', 'OVER',
        'SAME', 'SEEM', 'SUCH', 'TAKE', 'TELL', 'THAT', 'THIS', 'WANT', 'WENT', 'WERE', 'WHAT',
        'WITH', 'WORD', 'ALSO', 'AWAY', 'EVEN', 'EYES', 'FEEL', 'FOUR', 'FROM', 'GAVE', 'GIVE',
        'HAVE', 'HERE', 'HOME', 'INTO', 'KIND', 'KNOW', 'LATE', 'LINE', 'LOOK', 'MEAN', 'MOVE',
        'MUCH', 'NEED', 'ONCE', 'ONLY', 'OPEN', 'PLAY', 'READ', 'REST', 'SAID', 'SHOW', 'SIDE',
        'SOON', 'SURE', 'TALK', 'THEY', 'TOLD', 'TOOK', 'TURN', 'USED', 'WALK', 'WILL', 'WISH',
        'BEST', 'BOTH', 'CITY', 'DOWN', 'EACH', 'FALL', 'FIVE', 'GIRL', 'GONE', 'GROW', 'HALF',
        'HELP', 'HOLD', 'HOUR', 'KNEW', 'LAND', 'LESS', 'LOVE', 'MINE', 'NEAR', 'NEXT', 'ROOM',
        'SOME', 'STOP', 'THAN', 'THEM', 'THEY', 'TREE', 'UPON', 'WAIT', 'WARM', 'WEEK', 'WEST',
        'WIND', 'WIRE', 'DONE', 'DOOR', 'DRAW', 'FACE', 'FACT', 'FARM', 'FAST', 'FELT', 'FIRE',
        'FISH', 'FOOT', 'FORM', 'FULL', 'GAME', 'GETS', 'GOES', 'GOLD', 'HARD', 'HEAD', 'HEAR',
        'HEAT', 'HOPE', 'IDEA', 'IRON', 'LAKE', 'LIST', 'LOST', 'MAIN', 'MARK', 'MIND', 'MISS',
        'MOON', 'NOTE', 'PAGE', 'PASS', 'PAST', 'PLAN', 'POOR', 'PULL', 'RAIN', 'REAL', 'RIDE',
        'RING', 'ROAD', 'ROCK', 'ROSE', 'SAFE', 'SAIL', 'SALT', 'SAVE', 'SENT', 'SHIP', 'SHOP',
        'SING', 'SIZE', 'SLOW', 'SNOW', 'SOFT', 'SOIL', 'SONG', 'SORT', 'STAR', 'STAY', 'STEP',
        'TALL', 'TEST', 'THIN', 'TOWN', 'TRUE', 'UNIT', 'VIEW', 'VOTE', 'WAVE', 'WEAR', 'WIFE',
        'WILD', 'WOOD', 'ABLE', 'ARMY', 'BABY', 'BALL', 'BANK', 'BASE', 'BEAR', 'BEAT', 'BELL',
        'BILL', 'BIRD', 'BLUE', 'BOAT', 'BODY', 'BOOK', 'BORN', 'BURN', 'BUSY', 'CALM', 'CAMP',
        'CARD', 'CARE', 'CASE', 'CAST', 'CENT', 'CLUB', 'COAT', 'COLD', 'COOK', 'COOL', 'CORN',
        'COST', 'CREW', 'DARK', 'DATA', 'DEAD', 'DEAL', 'DEEP', 'DESK', 'DIET', 'DRUG', 'DUTY',
        'EARN', 'EAST', 'EDGE', 'ELSE', 'FAIL', 'FAIR', 'FEAR', 'FEED', 'FILL', 'FILM', 'FINE',
        'FLAT', 'FLEW', 'FLOW', 'FOLK', 'FOOD', 'FORD', 'GAIN', 'GATE', 'GLAD', 'GOAL', 'GOES',
        'GRAY', 'GREW', 'GROW', 'GULF', 'HAIR', 'HANG', 'HARM', 'HATE', 'HELD', 'HERO', 'HIDE',
        'HILL', 'HOLE', 'HOLY', 'HUGE', 'HUNT', 'HURT', 'INCH', 'JANE', 'JOIN', 'JUMP', 'JURY',
        'KING', 'LACK', 'LADY', 'LAID', 'LEAN', 'LIFT', 'LINK', 'LOAD', 'LOAN', 'LOCK', 'LORD',
        'LOSS', 'LUCK', 'MAIL', 'MASS', 'MATE', 'MEAL', 'MEAT', 'MEET', 'MILE', 'MILK', 'MILL',
        'MOOD', 'MOST', 'NECK', 'NINE', 'NONE', 'NOSE', 'ONTO', 'ORAL', 'PACE', 'PACK', 'PAID',
        'PAIN', 'PAIR', 'PALM', 'PARK', 'PATH', 'PEAK', 'PICK', 'PILE', 'PINK', 'PIPE', 'POEM',
        'POET', 'POLE', 'POLL', 'POND', 'POOL', 'PORT', 'POST', 'PURE', 'PUSH', 'RACE', 'RAIL',
        'RANK', 'RARE', 'RATE', 'RENT', 'RICE', 'RICH', 'RISE', 'RISK', 'ROLE', 'ROOF', 'RULE',
        'RUSH', 'SAKE', 'SAND', 'SEAT', 'SEED', 'SEEK', 'SELF', 'SELL', 'SHED', 'SICK', 'SIGN',
        'SITE', 'SKIN', 'SLIP', 'SOLD', 'SOLE', 'SOUL', 'SPOT', 'STEM', 'SUIT', 'TAPE', 'TASK',
        'TEAM', 'TEAR', 'TEND', 'TERM', 'TEXT', 'TIDE', 'TINY', 'TONE', 'TOOL', 'TOUR', 'TRIP',
        'TWIN', 'TYPE', 'VARY', 'VAST', 'VERB', 'VICE', 'WALL', 'WASH', 'WAVE', 'WEAK', 'WHOM',
        'WIDE', 'WING', 'WISE', 'YARD', 'ZONE', 'WINE', 'RAIL', 'VAIN', 'LAIR', 'LEAN', 'YARN',
        'BEAN', 'EARN', 'WEAN', 'VARY', 'VALE', 'VEIL', 'LIAR', 'NEAR', 'YEAR'
    ]);

    // Create a strategic grid layout that allows words to be found
    function createStrategicGrid() {
        const grid = Array(GRID_SIZE).fill('');
        const placements = [];
        
        // Define word placements (row, col, direction: 'H'orizontal, 'V'ertical, 'D'iagonal)
        const wordPlacements = [
            { word: 'DEAR', row: 0, col: 0, dir: 'H' },
            { word: 'MY', row: 0, col: 5, dir: 'H' },
            { word: 'MARINA', row: 1, col: 0, dir: 'H' },
            { word: 'WILL', row: 2, col: 0, dir: 'H' },
            { word: 'YOU', row: 2, col: 5, dir: 'H' },
            { word: 'BE', row: 3, col: 0, dir: 'H' },
            { word: 'MY', row: 3, col: 3, dir: 'H' }, // Second "MY"
            { word: 'VALENTINE', row: 4, col: 0, dir: 'H' } // Spangram
        ];
        
        // Place each word in the grid
        wordPlacements.forEach(placement => {
            const { word, row, col, dir } = placement;
            const positions = [];
            
            for (let i = 0; i < word.length; i++) {
                let r = row;
                let c = col;
                
                if (dir === 'H') c += i;
                else if (dir === 'V') r += i;
                else if (dir === 'D') { r += i; c += i; }
                
                const index = r * GRID_COLS + c;
                grid[index] = word[i];
                positions.push(index);
            }
            
            placements.push({ word, positions });
        });
        
        // Fill empty spaces with random letters
        const fillerLetters = 'AEILNORSTUVWY';
        for (let i = 0; i < grid.length; i++) {
            if (grid[i] === '') {
                grid[i] = fillerLetters[Math.floor(Math.random() * fillerLetters.length)];
            }
        }
        
        return { grid, placements };
    }

    const { grid: gridLetters, placements: wordPlacements } = createStrategicGrid();

    // Game state
    const state = {
        currentSelection: [],
        foundWords: new Set(),
        foundWordInstances: [],
        letterElements: [],
        incorrectWordCount: 0,
        hintsAvailable: 0,
        isSelecting: false,
        usedHintWords: new Set()
    };

    // Check if selected indices match any word placement
    function findMatchingWord() {
        const sortedSelection = [...state.currentSelection].sort((a, b) => a - b);
        
        for (const placement of wordPlacements) {
            const sortedPositions = [...placement.positions].sort((a, b) => a - b);
            
            if (sortedSelection.length === sortedPositions.length &&
                sortedSelection.every((val, idx) => val === sortedPositions[idx])) {
                return placement.word;
            }
        }
        return null;
    }

    // Render grid
    function renderGrid() {
        const grid = document.getElementById('grid');
        if (!grid) return;
        
        grid.innerHTML = '';
        state.letterElements = [];

        gridLetters.forEach((letter, index) => {
            const letterDiv = document.createElement('div');
            letterDiv.className = 'letter';
            letterDiv.textContent = letter;
            letterDiv.dataset.index = index;

            letterDiv.addEventListener('mousedown', (e) => {
                e.preventDefault();
                startSelection(index);
            });
            
            letterDiv.addEventListener('mouseenter', () => {
                if (state.isSelecting) addToSelection(index);
            });

            letterDiv.addEventListener('touchstart', (e) => {
                e.preventDefault();
                startSelection(index);
            }, { passive: false });

            letterDiv.addEventListener('touchmove', (e) => {
                e.preventDefault();
                const touch = e.touches[0];
                const element = document.elementFromPoint(touch.clientX, touch.clientY);
                if (element && element.classList.contains('letter')) {
                    addToSelection(parseInt(element.dataset.index));
                }
            }, { passive: false });

            grid.appendChild(letterDiv);
            state.letterElements.push(letterDiv);
        });

        document.addEventListener('mouseup', endSelection);
        document.addEventListener('touchend', endSelection);
    }

    function startSelection(index) {
        if (state.letterElements[index].classList.contains('found') || 
            state.letterElements[index].classList.contains('spangram-found')) return;
        
        state.isSelecting = true;
        state.currentSelection = [index];
        updateSelectionDisplay();
    }

    function addToSelection(index) {
        if (state.letterElements[index].classList.contains('found') || 
            state.letterElements[index].classList.contains('spangram-found')) return;
        if (state.currentSelection.includes(index)) return;
        
        state.currentSelection.push(index);
        updateSelectionDisplay();
    }

    function endSelection() {
        if (!state.isSelecting) return;
        
        state.isSelecting = false;
        if (state.currentSelection.length > 0) checkWord();
    }

    function updateSelectionDisplay() {
        state.letterElements.forEach(el => el.classList.remove('selecting'));
        
        state.currentSelection.forEach(index => {
            state.letterElements[index].classList.add('selecting');
        });
        
        const word = state.currentSelection.map(i => gridLetters[i]).join('');
        const currentWordEl = document.getElementById('currentWord');
        if (currentWordEl) currentWordEl.textContent = word;
    }

    function checkWord() {
        const word = state.currentSelection.map(i => gridLetters[i]).join('');
        const matchedWord = findMatchingWord();
        
        // Check if this exact selection was already found
        const selectionKey = [...state.currentSelection].sort((a, b) => a - b).join(',');
        const alreadyFound = state.foundWordInstances.some(instance => 
            [...instance.indices].sort((a, b) => a - b).join(',') === selectionKey
        );
        
        if (matchedWord && !alreadyFound) {
            // CORRECT WORD!
            state.foundWords.add(matchedWord);
            state.foundWordInstances.push({
                word: matchedWord,
                indices: [...state.currentSelection]
            });
            
            state.currentSelection.forEach(index => {
                state.letterElements[index].classList.remove('selecting');
                if (matchedWord === 'VALENTINE') {
                    state.letterElements[index].classList.add('spangram-found');
                } else {
                    state.letterElements[index].classList.add('found');
                }
            });
            
            updateDisplay();
            
            // Check if won (all 8 word instances found)
            if (state.foundWordInstances.length === gameWords.length) {
                setTimeout(showVictory, 600);
            }
        } else if (word.length >= 4 && englishWords.has(word) && !gameWords.includes(word)) {
            // Valid English word that's NOT a target word - grant hint
            if (!state.usedHintWords.has(word)) {
                state.usedHintWords.add(word);
                state.incorrectWordCount++;
                
                if (state.incorrectWordCount >= 3) {
                    state.hintsAvailable++;
                    state.incorrectWordCount = 0;
                    const hintBtn = document.getElementById('hintBtn');
                    if (hintBtn) hintBtn.disabled = false;
                }
                updateHintProgress();
            }
            
            // Shake animation for non-target word
            const currentWordEl = document.getElementById('currentWord');
            if (currentWordEl) {
                currentWordEl.classList.add('shake');
                setTimeout(() => currentWordEl.classList.remove('shake'), 400);
            }
        } else if (word.length >= 4) {
            // Invalid word - just shake
            const currentWordEl = document.getElementById('currentWord');
            if (currentWordEl) {
                currentWordEl.classList.add('shake');
                setTimeout(() => currentWordEl.classList.remove('shake'), 400);
            }
        }
        
        setTimeout(clearSelection, 300);
    }

    function clearSelection() {
        state.currentSelection.forEach(index => {
            if (!state.letterElements[index].classList.contains('found') &&
                !state.letterElements[index].classList.contains('spangram-found')) {
                state.letterElements[index].classList.remove('selecting');
            }
        });
        state.currentSelection = [];
        const currentWordEl = document.getElementById('currentWord');
        if (currentWordEl) currentWordEl.textContent = '';
    }

    function updateHintProgress() {
        const progress = (state.incorrectWordCount / 3) * 100;
        const hintFill = document.getElementById('hintFill');
        if (hintFill) hintFill.style.width = progress + '%';
    }

    const hintBtn = document.getElementById('hintBtn');
    if (hintBtn) {
        hintBtn.addEventListener('click', () => {
            if (state.hintsAvailable > 0) {
                // Find unfound words
                const unfoundWords = wordPlacements.filter(placement => {
                    const selectionKey = [...placement.positions].sort((a, b) => a - b).join(',');
                    return !state.foundWordInstances.some(instance =>
                        [...instance.indices].sort((a, b) => a - b).join(',') === selectionKey
                    );
                });
                
                if (unfoundWords.length > 0) {
                    const randomUnfound = unfoundWords[Math.floor(Math.random() * unfoundWords.length)];
                    alert(`Hint: Look for the word "${randomUnfound.word}"`);
                    state.hintsAvailable--;
                    if (state.hintsAvailable === 0) {
                        hintBtn.disabled = true;
                    }
                }
            }
        });
    }

    function updateDisplay() {
        const foundCountEl = document.getElementById('foundCount');
        if (foundCountEl) {
            foundCountEl.textContent = state.foundWordInstances.length;
            foundCountEl.classList.add('pulse');
            setTimeout(() => foundCountEl.classList.remove('pulse'), 500);
        }
    }

    function showVictory() {
        const victoryModal = document.getElementById('victoryModal');
        if (victoryModal) {
            victoryModal.classList.add('active');
            document.body.style.overflow = 'hidden'; // Prevent background scrolling
    }
}

    // Initialize
    renderGrid();
    updateDisplay();
}, 100);

// Email button functionality
const emailButton = document.getElementById('emailButton');
if (emailButton) {
    emailButton.addEventListener('click', () => {
        const recipient = 'madisoncwatkins@gmail.com';
        const subject = encodeURIComponent('YES!');
        const body = encodeURIComponent("YES, Now let's kiss 💋");
        
        window.location.href = `mailto:${recipient}?subject=${subject}&body=${body}`;
    });
}

```