const themes = {
    mansion: {
        name: { ru: "Старый особняк", eng: "Old Mansion" },
        words: [
            { eng: "CANDLESTICK", ru: "ПОДСВЕЧНИК" }, { eng: "TYPEWRITER", ru: "МАШИНКА" },
            { eng: "CHESSBOARD", ru: "ШАХМАТЫ" }, { eng: "MAGNIFIER", ru: "ЛУПА" },
            { eng: "SPECTACLES", ru: "ОЧКИ" }, { eng: "INKWELL", ru: "ЧЕРНИЛЬНИЦА" },
            { eng: "BOOKCASE", ru: "ШКАФ" }, { eng: "ENVELOPE", ru: "КОНВЕРТ" },
            { eng: "MANUSCRIPT", ru: "РУКОПИСЬ" }, { eng: "QUILL", ru: "ПЕРО" },
            { eng: "CHANDELIER", ru: "ЛЮСТРА" }, { eng: "TAPESTRY", ru: "ГОБЕЛЕН" },
            { eng: "ARMCHAIR", ru: "КРЕСЛО" }, { eng: "FIREPLACE", ru: "КАМИН" },
            { eng: "PORTRAIT", ru: "ПОРТРЕТ" }, { eng: "DECANTER", ru: "ГРАФИН" },
            { eng: "TELESCOPE", ru: "ТЕЛЕСКОП" }, { eng: "GRAMOPHONE", ru: "ГРАММОФОН" }
        ]
    },
    train: {
        name: { ru: "Восточный экспресс", eng: "Orient Express" },
        words: [
            { eng: "TICKET", ru: "БИЛЕТ" }, { eng: "SUITCASE", ru: "ЧЕМОДАН" },
            { eng: "COMPARTMENT", ru: "КУПЕ" }, { eng: "CONDUCTOR", ru: "ПРОВОДНИК" },
            { eng: "TELEGRAM", ru: "ТЕЛЕГРАММА" }, { eng: "LOCOMOTIVE", ru: "ПАРОВОЗ" },
            { eng: "WHISTLE", ru: "СВИСТОК" }, { eng: "LANTERN", ru: "ФОНАРЬ" },
            { eng: "POCKETWATCH", ru: "ЧАСЫ" }, { eng: "NEWSPAPER", ru: "ГАЗЕТА" },
            { eng: "UMBRELLA", ru: "ЗОНТ" }, { eng: "RAINCOAT", ru: "ПЛАЩ" },
            { eng: "PASSPORT", ru: "ПАСПОРТ" }, { eng: "BERTH", ru: "ПОЛКА" },
            { eng: "VALISE", ru: "САКВОЯЖ" }, { eng: "STATION", ru: "ВОКЗАЛ" }
        ]
    },
    theatre: {
        name: { ru: "Королевский театр", eng: "Royal Theatre" },
        words: [
            { eng: "BINOCULARS", ru: "БИНОКЛЬ" }, { eng: "CURTAIN", ru: "ЗАНАВЕС" },
            { eng: "BACKSTAGE", ru: "ЗАКУЛИСЬЕ" }, { eng: "COSTUME", ru: "КОСТЮМ" },
            { eng: "PROGRAMME", ru: "ПРОГРАММА" }, { eng: "BOUQUET", ru: "БУКЕТ" },
            { eng: "ORCHESTRA", ru: "ОРКЕСТР" }, { eng: "MONOCLE", ru: "МОНОКЛЬ" },
            { eng: "LIPSTICK", ru: "ПОМАДА" }, { eng: "MASK", ru: "МАСКА" },
            { eng: "VIOLIN", ru: "СКРИПКА" }, { eng: "DAGGER", ru: "КИНЖАЛ" },
            { eng: "SPOTLIGHT", ru: "ПРОЖЕКТОР" }, { eng: "SCENERY", ru: "ДЕКОРАЦИИ" },
            { eng: "PROMPTER", ru: "СУФЛЕР" }, { eng: "BALCONY", ru: "БАЛКОН" }
        ]
    }
};

const crimeElements = {
    killers: [
        { eng: "BUTLER", ru: "ДВОРЕЦКИЙ" }, { eng: "DOCTOR", ru: "ДОКТОР" },
        { eng: "GARDENER", ru: "САДОВНИК" }, { eng: "MAID", ru: "ГОРНИЧНАЯ" },
        { eng: "COLONEL", ru: "ПОЛКОВНИК" }, { eng: "LAWYER", ru: "АДВОКАТ" },
        { eng: "ARTIST", ru: "ХУДОЖНИК" }, { eng: "COOK", ru: "ПОВАР" },
        { eng: "POET", ru: "ПОЭТ" }, { eng: "CAPTAIN", ru: "КАПИТАН" }
    ],
    victims: [
        { eng: "JASON", ru: "ДЖЕЙСОН" }, { eng: "ARTHUR", ru: "АРТУР" },
        { eng: "MARIA", ru: "МАРИЯ" }, { eng: "ELIZA", ru: "ЭЛИЗА" },
        { eng: "HENRY", ru: "ГЕНРИ" }, { eng: "VICTOR", ru: "ВИКТОР" },
        { eng: "CLARA", ru: "КЛАРА" }, { eng: "CEDRIC", ru: "СЕДРИК" }
    ],
    weapons: [
        { eng: "KNIFE", ru: "НОЖ" }, { eng: "POISON", ru: "ЯД" },
        { eng: "HAMMER", ru: "МОЛОТОК" }, { eng: "DAGGER", ru: "КИНЖАЛ" },
        { eng: "PISTOL", ru: "ПИСТОЛЕТ" }, { eng: "ROPE", ru: "ВЕРЕВКА" },
        { eng: "STATUETTE", ru: "СТАТУЭТКА" }, { eng: "RAZOR", ru: "БРИТВА" },
        { eng: "SCISSORS", ru: "НОЖНИЦЫ" }, { eng: "CANDLESTICK", ru: "ПОДСВЕЧНИК" }
    ],
    locations: [
        { eng: "ARCHIVE", ru: "АРХИВ" }, { eng: "GARDEN", ru: "САД" },
        { eng: "KITCHEN", ru: "КУХНЯ" }, { eng: "LIBRARY", ru: "БИБЛИОТЕКА" },
        { eng: "BALCONY", ru: "БАЛКОН" }, { eng: "CELLAR", ru: "ПОГРЕБ" },
        { eng: "PARLOR", ru: "ГОСТИНАЯ" }, { eng: "ATTIC", ru: "ЧЕРДАК" },
        { eng: "STUDY", ru: "КАБИНЕТ" }, { eng: "TERRACE", ru: "ТЕРРАСА" }
    ]
};

const gridSize = 15;
let currentLang = 'ru', grid = [], answerCells = new Set(), wordPositions = {};
let currentVocabulary = [], currentAnswers = {}, foundCount = 0, isFinalPhase = false;
let isSelecting = false, startCell = null, selection = [];
const directions = [[0, 1], [0, -1], [1, 0], [-1, 0], [1, 1], [1, -1], [-1, 1], [-1, -1]];

function updateInterface() {
    const ui = {
        ru: { btnLang: "Язык поиска: RU", listTitle: "Список поиска:", btnReset: "Начать заново", protocol: "ПРОТОКОЛ РАССЛЕДОВАНИЯ", desc: "Используйте оставшиеся буквы, чтобы заполнить отчет:", k: "Убийца (Killer):", v: "Жертва (Victim):", w: "Орудие (Weapon):", l: "Место (Location):", check: "Проверить версию" },
        eng: { btnLang: "Search Language: ENG", listTitle: "Search List:", btnReset: "Reset Game", protocol: "INVESTIGATION PROTOCOL", desc: "Find the killer using letters:", k: "Killer:", v: "Victim:", w: "Weapon:", l: "Location:", check: "Verify Version" }
    }[currentLang];
    document.getElementById('btn-lang').textContent = ui.btnLang;
    document.getElementById('list-title').textContent = ui.listTitle;
    document.getElementById('btn-reset').textContent = ui.btnReset;
    document.getElementById('protocol-title').textContent = ui.protocol;
    document.getElementById('protocol-desc').textContent = ui.desc;
    document.getElementById('label-killer').textContent = ui.k;
    document.getElementById('label-victim').textContent = ui.v;
    document.getElementById('label-weapon').textContent = ui.w;
    document.getElementById('label-location').textContent = ui.l;
    document.getElementById('btn-verify').textContent = ui.check;
}

function toggleLanguage() { currentLang = currentLang === 'ru' ? 'eng' : 'ru'; updateInterface(); resetGame(); }

function generateNewCrime() {
    const pick = (arr) => arr[Math.floor(Math.random() * arr.length)];
    currentAnswers = {
        killer: pick(crimeElements.killers)[currentLang],
        victim: pick(crimeElements.victims)[currentLang],
        weapon: pick(crimeElements.weapons)[currentLang],
        location: pick(crimeElements.locations)[currentLang]
    };
}

function initGame() {
    generateNewCrime();
    let success = false;
    const themeKeys = Object.keys(themes);
    const theme = themes[themeKeys[Math.floor(Math.random() * themeKeys.length)]];
    currentVocabulary = [...theme.words].sort(() => 0.5 - Math.random()).slice(0, 10);
    document.querySelector('.story').textContent = currentLang === 'ru' ? `Место: ${theme.name.ru}. Раскрой преступление!` : `Location: ${theme.name.eng}. Solve the crime!`;

    while (!success) {
        grid = Array(gridSize).fill().map(() => Array(gridSize).fill(''));
        answerCells.clear(); wordPositions = {}; success = true;
        const keys = [currentAnswers.victim, currentAnswers.weapon, currentAnswers.location];
        for (let w of keys) if (!placeWord(w, true)) { success = false; break; }
        if (!success) continue;
        for (let wObj of currentVocabulary) if (!placeWord(wObj[currentLang], false)) { success = false; break; }
    }
    fillNoise(); renderGrid(); renderList();
}

function placeWord(word, isKey) {
    const w = word.toUpperCase();
    for (let i = 0; i < 500; i++) {
        const dir = directions[Math.floor(Math.random() * directions.length)];
        const r = Math.floor(Math.random() * gridSize), c = Math.floor(Math.random() * gridSize);
        if (canPlace(w, r, c, dir)) {
            for (let j = 0; j < w.length; j++) {
                const rr = r + dir[0] * j, cc = c + dir[1] * j;
                grid[rr][cc] = w[j];
                if (isKey) answerCells.add(`${rr}-${cc}`);
            }
            if (!isKey) wordPositions[w] = { r, c };
            return true;
        }
    }
    return false;
}

function canPlace(w, r, c, dir) {
    const er = r + dir[0] * (w.length - 1), ec = c + dir[1] * (w.length - 1);
    if (er < 0 || er >= gridSize || ec < 0 || ec >= gridSize) return false;
    for (let j = 0; j < w.length; j++) {
        const rr = r + dir[0] * j, cc = c + dir[1] * j;
        if (grid[rr][cc] !== '' && grid[rr][cc] !== w[j]) return false;
    }
    return true;
}

function fillNoise() {
    const killer = currentAnswers.killer.toUpperCase().split('');
    let empty = [];
    for (let r = 0; r < gridSize; r++) for (let c = 0; c < gridSize; c++) if (grid[r][c] === '') empty.push({ r, c });
    empty.sort(() => Math.random() - 0.5);
    killer.forEach(char => { if (empty.length > 0) { const p = empty.pop(); grid[p.r][p.c] = char; answerCells.add(`${p.r}-${p.c}`); } });
    const abc = currentLang === 'ru' ? "АБВГДЕЖЗИЙКЛМНОПРСТУФХЦЧШЩЪЫЬЭЮЯ" : "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    empty.forEach(p => grid[p.r][p.c] = abc[Math.floor(Math.random() * abc.length)]);
}

function getCellFromTouch(e) {
    const t = e.touches[0];
    const el = document.elementFromPoint(t.clientX, t.clientY);
    if (el && el.classList.contains('cell')) return { r: parseInt(el.dataset.r), c: parseInt(el.dataset.c) };
    return null;
}

// --- ИСПРАВЛЕННАЯ ФУНКЦИЯ РЕНДЕРА СЕТКИ ---
function renderGrid() {
    const el = document.getElementById('grid'); el.innerHTML = '';
    for (let r = 0; r < gridSize; r++) {
        for (let c = 0; c < gridSize; c++) {
            const cell = document.createElement('div');
            cell.className = 'cell'; cell.textContent = grid[r][c];
            cell.dataset.r = r; cell.dataset.c = c;

            // 1. Обычный клик (для финала)
            cell.onclick = () => {
                if (isFinalPhase && cell.classList.contains('answer-clue')) {
                    cell.classList.toggle('used-letter');
                }
            };

            // 2. Начало выделения (только в основной фазе)
            cell.onmousedown = () => {
                if (!isFinalPhase) {
                    isSelecting = true;
                    startCell = { r, c };
                    highlight(r, c);
                }
            };
            cell.onmouseenter = () => { if (isSelecting && !isFinalPhase) highlight(r, c); };

            // 3. Тач-события для мобилок
            cell.ontouchstart = (e) => {
                if (isFinalPhase) {
                   if (cell.classList.contains('answer-clue')) cell.classList.toggle('used-letter');
                } else {
                    isSelecting = true;
                    startCell = { r, c };
                    highlight(r, c);
                }
                if (e.cancelable) e.preventDefault();
            };

            el.appendChild(cell);
        }
    }
}

function highlight(r, c) {
    if (!startCell) return;
    document.querySelectorAll('.cell:not(.marked)').forEach(ce => ce.style.background = "#fffbf0");
    const dr = r - startCell.r, dc = c - startCell.c, steps = Math.max(Math.abs(dr), Math.abs(dc));
    if (dr !== 0 && dc !== 0 && Math.abs(dr) !== Math.abs(dc)) return;
    selection = [];
    for (let i = 0; i <= steps; i++) {
        const rr = startCell.r + Math.sign(dr) * i, cc = startCell.c + Math.sign(dc) * i;
        const target = document.querySelector(`[data-r="${rr}"][data-c="${cc}"]`);
        if (target && !target.classList.contains('hidden')) {
            target.style.background = isFinalPhase ? "#bbdefb" : "#dcedc8";
            selection.push({ r: rr, c: cc, char: grid[rr][cc] });
        }
    }
}

function endSelection() {
    if (!isSelecting) return;
    isSelecting = false;
    const word = selection.map(s => s.char).join(''), rev = word.split('').reverse().join('');
    const idx = currentVocabulary.findIndex(w => w[currentLang] === word || w[currentLang] === rev);
    if (idx !== -1 && !isFinalPhase) {
        const li = document.querySelectorAll('#ui-word-list li')[idx];
        if (!li.classList.contains('found')) {
            li.classList.add('found');
            selection.forEach(s => document.querySelector(`[data-r="${s.r}"][data-c="${s.c}"]`).classList.add('marked'));
            foundCount++;
            if (foundCount === currentVocabulary.length) finalize();
        }
    }
    document.querySelectorAll('.cell:not(.marked)').forEach(ce => ce.style.background = "#fffbf0");
}

window.addEventListener('mouseup', endSelection);
window.addEventListener('touchend', endSelection);
window.addEventListener('touchmove', (e) => {
    if (isSelecting && !isFinalPhase) {
        const pos = getCellFromTouch(e);
        if (pos) highlight(pos.r, pos.c);
        if (e.cancelable) e.preventDefault();
    }
}, { passive: false });

function finalize() {
    isFinalPhase = true;
    document.querySelectorAll('.cell').forEach(ce => {
        if (answerCells.has(`${ce.dataset.r}-${ce.dataset.c}`)) {
            ce.classList.remove('marked');
            ce.classList.add('answer-clue');
        } else ce.classList.add('hidden');
    });
    document.getElementById('victory-msg').style.display = 'block';
    document.getElementById('hint-insight').style.display = 'inline-block';
}

function useMagnifier() {
    const items = document.querySelectorAll('#ui-word-list li');
    const remains = currentVocabulary.filter((v, i) => !items[i].classList.contains('found'));
    if (remains.length > 0) {
        const word = remains[Math.floor(Math.random() * remains.length)][currentLang].toUpperCase();
        const pos = wordPositions[word];
        if (pos) {
            const cell = document.querySelector(`[data-r="${pos.r}"][data-c="${pos.c}"]`);
            cell.classList.add('hint-glow');
            setTimeout(() => cell.classList.remove('hint-glow'), 2000);
        }
    }
}

function useInsight() { if (isFinalPhase) document.getElementById('input-killer').value = currentAnswers.killer; }

function verifyInvestigation() {
    const val = (id) => document.getElementById(id).value.toUpperCase().trim();
    const res = document.getElementById('final-result');
    if (val('input-killer') === currentAnswers.killer.toUpperCase() && val('input-victim') === currentAnswers.victim.toUpperCase()) {
        res.textContent = "ВЕРНО!"; res.style.color = "green";
    } else {
        res.textContent = "ОШИБКА!"; res.style.color = "red";
    }
}

function renderList() {
    const list = document.getElementById('ui-word-list'); list.innerHTML = '';
    currentVocabulary.forEach(w => {
        const li = document.createElement('li');
        li.textContent = `${w[currentLang]} — ${currentLang === 'ru' ? w.eng : w.ru}`;
        list.appendChild(li);
    });
}

function resetGame() {
    isFinalPhase = false; foundCount = 0;
    document.getElementById('victory-msg').style.display = 'none';
    document.getElementById('hint-insight').style.display = 'none';
    document.querySelectorAll('input').forEach(i => i.value = '');
    initGame();
}

updateInterface();
initGame();
