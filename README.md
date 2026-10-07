# physics-labs-zzakon-OMA
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Исследование зависимости силы тока от напряжения (закон Ома) — ОГЭ физика</title>
    <style>
        * {
            box-sizing: border-box;
            user-select: none;
            font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
        }
        body {
            background: #f5f7fa;
            margin: 0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 16px;
        }
        .app {
            max-width: 1300px;
            width: 100%;
            background: white;
            border-radius: 28px;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
            padding: 24px;
        }
        h1 {
            font-size: 1.8rem;
            color: #1e2b3c;
            margin: 0 0 4px 0;
            font-weight: 600;
            letter-spacing: -0.5px;
        }
        .subhead {
            color: #4b5e71;
            margin-bottom: 20px;
            font-size: 1rem;
            border-left: 4px solid #3b82f6;
            padding-left: 14px;
            background: #eef2ff;
            border-radius: 0 8px 8px 0;
            padding: 10px 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .subhead span {
            font-weight: 500;
        }
        .main-panel {
            display: flex;
            flex-wrap: wrap;
            gap: 24px;
        }
        .circuit-area {
            flex: 2;
            min-width: 480px;
            background: #ffffff;
            border-radius: 20px;
            padding: 16px;
            box-shadow: inset 0 1px 4px rgba(0,0,0,0.02), 0 4px 12px rgba(0, 0, 0, 0.05);
            border: 1px solid #e2e8f0;
        }
        .controls-area {
            flex: 1.2;
            min-width: 280px;
            display: flex;
            flex-direction: column;
            gap: 16px;
        }
        .card {
            background: #ffffff;
            border-radius: 18px;
            padding: 18px 16px;
            border: 1px solid #e2e8f0;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.02);
        }
        .card h3 {
            margin: 0 0 12px 0;
            font-size: 1.1rem;
            color: #1e2b3c;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }
        .device-panel {
            display: flex;
            justify-content: space-between;
            gap: 12px;
            margin-bottom: 12px;
        }
        .device {
            background: #f8fafc;
            border-radius: 14px;
            padding: 10px 12px;
            border: 1px solid #cbd5e1;
            flex: 1;
            box-shadow: inset 0 1px 3px rgba(0,0,0,0.05);
        }
        .device-label {
            font-size: 0.8rem;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            color: #475569;
            font-weight: 600;
            display: flex;
            justify-content: space-between;
        }
        .device-value {
            font-size: 1.8rem;
            font-weight: 700;
            font-family: 'Courier New', monospace;
            color: #0f172a;
            line-height: 1.2;
        }
        .unit {
            font-size: 1rem;
            font-weight: 400;
            color: #64748b;
            margin-left: 4px;
        }
        .rheostat-slider {
            width: 100%;
            margin: 8px 0 12px;
        }
        input[type=range] {
            width: 100%;
            height: 8px;
            -webkit-appearance: none;
            background: linear-gradient(to right, #3b82f6, #94a3b8);
            border-radius: 10px;
            outline: none;
        }
        input[type=range]::-webkit-slider-thumb {
            -webkit-appearance: none;
            width: 24px;
            height: 24px;
            background: white;
            border-radius: 50%;
            border: 3px solid #2563eb;
            box-shadow: 0 2px 8px rgba(37, 99, 235, 0.4);
            cursor: pointer;
            transition: 0.1s;
        }
        .button-group {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
            margin-top: 12px;
        }
        button {
            background: #ffffff;
            border: 1px solid #cbd5e1;
            border-radius: 40px;
            padding: 10px 18px;
            font-weight: 600;
            font-size: 0.9rem;
            color: #1e293b;
            cursor: pointer;
            transition: all 0.15s;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 6px;
            flex: 1 0 auto;
        }
        button.primary {
            background: #2563eb;
            border-color: #1d4ed8;
            color: white;
            box-shadow: 0 6px 14px rgba(37, 99, 235, 0.3);
        }
        button.primary:hover {
            background: #1d4ed8;
        }
        button:active {
            transform: scale(0.97);
        }
        button:disabled {
            opacity: 0.5;
            pointer-events: none;
            filter: grayscale(0.6);
        }
        table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
            margin-top: 8px;
            border-radius: 12px;
            overflow: hidden;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }
        th {
            background: #eef2ff;
            color: #1e3a8a;
            font-weight: 600;
            padding: 10px 6px;
            font-size: 0.85rem;
            border-bottom: 1px solid #cbd5e1;
        }
        td {
            padding: 8px 6px;
            text-align: center;
            border-bottom: 1px solid #e2e8f0;
            background: white;
            font-family: 'Courier New', monospace;
            font-weight: 500;
        }
        tr:last-child td {
            border-bottom: none;
        }
        .graph-container {
            background: #ffffff;
            border-radius: 16px;
            padding: 10px;
            border: 1px solid #e2e8f0;
            margin-top: 8px;
        }
        canvas {
            display: block;
            width: 100%;
            height: auto;
            background: #ffffff;
            border-radius: 12px;
        }
        .info-badge {
            background: #dbeafe;
            border-radius: 30px;
            padding: 12px 18px;
            font-size: 0.95rem;
            color: #1e3a8a;
            font-weight: 500;
            display: flex;
            flex-wrap: wrap;
            gap: 16px;
            justify-content: space-between;
        }
        .conclusion {
            background: #ecfdf5;
            border-left: 6px solid #10b981;
            padding: 14px 18px;
            border-radius: 12px;
            font-size: 0.95rem;
            color: #065f46;
            margin-top: 10px;
            display: none;
        }
        .conclusion.show {
            display: block;
        }
        .hint {
            font-size: 0.8rem;
            color: #64748b;
            margin-top: 6px;
            font-style: italic;
        }
        .flex-between {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        .badge {
            background: #f1f5f9;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.8rem;
            font-weight: 500;
            color: #334155;
        }
        .hidden-r {
            font-weight: 600;
            color: #64748b;
        }
    </style>
</head>
<body>
<div class="app">
    <h1>⚡ Закон Ома: I = U / R</h1>
    <div class="subhead">
        <span>🔬 Исследование зависимости силы тока от напряжения</span>
        <span class="badge">R резистора: <span id="rIndicator" class="hidden-r">??</span></span>
    </div>

    <div class="main-panel">
        <!-- Левая часть: схема и приборы -->
        <div class="circuit-area">
            <div class="device-panel">
                <div class="device">
                    <div class="device-label">Амперметр <span>A</span></div>
                    <div class="device-value"><span id="ammeterDisplay">0.00</span><span class="unit">А</span></div>
                </div>
                <div class="device">
                    <div class="device-label">Вольтметр <span>V</span></div>
                    <div class="device-value"><span id="voltmeterDisplay">0.0</span><span class="unit">В</span></div>
                </div>
            </div>

            <!-- Схема цепи (SVG) -->
            <svg viewBox="0 0 620 280" style="width:100%; height:auto; background: #fafcff; border-radius: 16px; border: 1px solid #e2e8f0;">
                <!-- Соединительные провода (общий контур) -->
                <!-- Нижняя линия -->
                <line x1="40" y1="220" x2="580" y2="220" stroke="#2c3e50" stroke-width="3" stroke-linecap="round" />
                <!-- Верхняя линия -->
                <line x1="40" y1="70" x2="580" y2="70" stroke="#2c3e50" stroke-width="3" stroke-linecap="round" />
                
                <!-- Источник питания (слева) -->
                <rect x="20" y="120" width="40" height="50" rx="6" fill="#ffffff" stroke="#2c3e50" stroke-width="2.5" />
                <line x1="30" y1="120" x2="30" y2="90" stroke="#2c3e50" stroke-width="2.5" />
                <line x1="50" y1="120" x2="50" y2="90" stroke="#2c3e50" stroke-width="2.5" />
                <text x="40" y="105" font-size="14" text-anchor="middle" fill="#1e293b" font-weight="bold">+</text>
                <text x="40" y="165" font-size="14" text-anchor="middle" fill="#1e293b" font-weight="bold">−</text>
                <text x="40" y="190" font-size="12" text-anchor="middle" fill="#475569">Источник</text>

                <!-- Ключ (слева, после источника) -->
                <line x1="60" y1="70" x2="110" y2="70" stroke="#2c3e50" stroke-width="3" />
                <line x1="110" y1="70" x2="140" y2="70" stroke="#2c3e50" stroke-width="3" />
                <circle cx="110" cy="70" r="5" fill="#2c3e50" />
                <circle cx="140" cy="70" r="5" fill="#2c3e50" />
                <!-- Подвижный контакт ключа -->
                <line id="keyContact" x1="110" y1="70" x2="140" y2="70" stroke="#e67e22" stroke-width="4" stroke-linecap="round" />
                <text x="125" y="45" font-size="12" text-anchor="middle" fill="#475569">Ключ</text>

                <!-- Реостат (после ключа) -->
                <rect x="160" y="55" width="80" height="30" rx="6" fill="#ffffff" stroke="#2c3e50" stroke-width="2.5" />
                <line x1="170" y1="70" x2="230" y2="70" stroke="#2c3e50" stroke-width="2" stroke-dasharray="4 2" />
                <!-- Ползунок реостата (движется по горизонтали) -->
                <polygon id="rheostatSlider" points="195,55 205,55 200,40" fill="#e67e22" stroke="#b45309" stroke-width="1.5" />
                <line id="sliderLine" x1="200" y1="55" x2="200" y2="40" stroke="#b45309" stroke-width="2" />
                <text x="200" y="30" font-size="12" text-anchor="middle" fill="#475569">Реостат</text>

                <!-- Резистор (R) -->
                <rect x="280" y="55" width="60" height="30" rx="6" fill="#eef2ff" stroke="#2563eb" stroke-width="2.5" />
                <text x="310" y="75" font-size="14" text-anchor="middle" fill="#1e3a8a" font-weight="bold">R</text>
                <text x="310" y="45" font-size="12" text-anchor="middle" fill="#475569">Резистор</text>

                <!-- Амперметр (последовательно, после резистора) -->
                <circle cx="410" cy="70" r="24" fill="#ffffff" stroke="#2c3e50" stroke-width="2.5" />
                <text x="410" y="76" font-size="18" text-anchor="middle" fill="#1e293b" font-weight="bold">A</text>
                <text x="410" y="105" font-size="11" text-anchor="middle" fill="#475569">Амперметр</text>

                <!-- Вольтметр (параллельно резистору) -->
                <line x1="280" y1="70" x2="280" y2="140" stroke="#2c3e50" stroke-width="2" />
                <line x1="340" y1="70" x2="340" y2="140" stroke="#2c3e50" stroke-width="2" />
                <line x1="280" y1="140" x2="340" y2="140" stroke="#2c3e50" stroke-width="2" />
                <circle cx="310" cy="160" r="24" fill="#ffffff" stroke="#2c3e50" stroke-width="2.5" />
                <text x="310" y="166" font-size="18" text-anchor="middle" fill="#1e293b" font-weight="bold">V</text>
                <text x="310" y="200" font-size="11" text-anchor="middle" fill="#475569">Вольтметр</text>
                <!-- Соединение вольтметра с нижней линией -->
                <line x1="280" y1="160" x2="280" y2="220" stroke="#2c3e50" stroke-width="2" />
                <line x1="340" y1="160" x2="340" y2="220" stroke="#2c3e50" stroke-width="2" />
                <circle cx="280" cy="220" r="4" fill="#2c3e50" />
                <circle cx="340" cy="220" r="4" fill="#2c3e50" />

                <!-- Соединения на нижней линии для источника и амперметра -->
                <line x1="40" y1="220" x2="40" y2="170" stroke="#2c3e50" stroke-width="2.5" />
                <line x1="580" y1="220" x2="580" y2="70" stroke="#2c3e50" stroke-width="3" />
                <line x1="410" y1="94" x2="410" y2="220" stroke="#2c3e50" stroke-width="2.5" />
                <circle cx="410" cy="220" r="4" fill="#2c3e50" />
                <circle cx="40" cy="220" r="4" fill="#2c3e50" />

                <!-- Подписи -->
                <text x="520" y="200" font-size="11" fill="#64748b">Схема: последовательно R, реостат, амперметр</text>
            </svg>

            <div class="hint">🔹 Перемещайте ползунок реостата, чтобы изменить напряжение на резисторе (0–6 В).</div>
        </div>

        <!-- Правая часть: управление и данные -->
        <div class="controls-area">
            <div class="card">
                <h3>🎛 Управление</h3>
                <div class="flex-between">
                    <span>Ключ: <strong id="keyStatus">разомкнут</strong></span>
                    <button id="toggleKeyBtn" style="padding:6px 16px;">Замкнуть</button>
                </div>
                <div style="margin-top: 16px;">
                    <div class="flex-between">
                        <span>Ползунок реостата</span>
                        <span class="badge" id="voltageHint">0.0 В</span>
                    </div>
                    <input type="range" id="rheostatRange" min="0" max="6" step="0.5" value="0" class="rheostat-slider">
                </div>
                <div class="button-group">
                    <button id="recordBtn" class="primary" disabled>📝 Записать показания</button>
                    <button id="clearBtn">🗑 Сбросить</button>
                </div>
            </div>

            <div class="card">
                <h3>📋 Таблица измерений</h3>
                <table id="measureTable">
                    <thead>
                        <tr><th>U, В</th><th>I, А</th><th>R = U/I, Ом</th></tr>
                    </thead>
                    <tbody id="tableBody">
                        <tr><td colspan="3" style="color:#94a3b8; font-style:italic;">Нет данных</td></tr>
                    </tbody>
                </table>
                <div id="avgRDisplay" style="margin-top: 12px; font-weight: 500; color: #1e293b;"></div>
            </div>

            <div class="card">
                <h3>📈 График I(U)</h3>
                <div class="graph-container">
                    <canvas id="graphCanvas" width="400" height="250"></canvas>
                </div>
                <div id="conclusionBox" class="conclusion"></div>
            </div>
        </div>
    </div>
</div>

<script>
    (function() {
        // ========== ФИЗИЧЕСКАЯ МОДЕЛЬ ==========
        const RESISTOR_R = 10;          // Ом, фиксированное сопротивление резистора
        const INTERNAL_R = 0.5;         // Ом, внутреннее сопротивление источника (для реализма)
        const EMF = 6.2;                // В, ЭДС источника (чуть выше 6В, чтобы достичь 6В на резисторе)

        // Переменные состояния
        let keyClosed = false;          // ключ разомкнут по умолчанию
        let sliderPosition = 0;         // 0..6 В (шаг 0.5) — желаемое напряжение на резисторе
        // Но реальное напряжение зависит от реостата: мы управляем ползунком,
        // который меняет сопротивление реостата. Однако для простоты и наглядности
        // сделаем так, чтобы напряжение на резисторе было равно sliderPosition (идеальная модель).
        // Но чтобы реостат был "реалистичным", добавим небольшую зависимость от внутреннего сопротивления.
        // Для учебной задачи достаточно прямой зависимости: U = sliderPosition (0..6 В).
        // Ток вычисляется по закону Ома: I = U / R (сопротивление резистора 10 Ом).
        // При этом показания амперметра будут I = U / 10 (0..0.6 А) — реалистично для школьной лаборатории.
        // Вольтметр показывает напряжение на резисторе = sliderPosition.
        // Реостат в схеме нужен для изменения напряжения, но его влияние скрыто в управлении.

        // Данные для таблицы и графика
        let measurements = [];          // { U, I, R }

        // DOM элементы
        const ammeterDisplay = document.getElementById('ammeterDisplay');
        const voltmeterDisplay = document.getElementById('voltmeterDisplay');
        const keyStatus = document.getElementById('keyStatus');
        const toggleKeyBtn = document.getElementById('toggleKeyBtn');
        const rheostatRange = document.getElementById('rheostatRange');
        const voltageHint = document.getElementById('voltageHint');
        const recordBtn = document.getElementById('recordBtn');
        const clearBtn = document.getElementById('clearBtn');
        const tableBody = document.getElementById('tableBody');
        const avgRDisplay = document.getElementById('avgRDisplay');
        const conclusionBox = document.getElementById('conclusionBox');
        const rIndicator = document.getElementById('rIndicator');
        const canvas = document.getElementById('graphCanvas');
        const ctx = canvas.getContext('2d');
        const keyContact = document.getElementById('keyContact');
        const rheostatSlider = document.getElementById('rheostatSlider');
        const sliderLine = document.getElementById('sliderLine');

        // ========== ВСПОМОГАТЕЛЬНЫЕ ФУНКЦИИ ==========
        function computeCurrent(voltage) {
            // Закон Ома: I = U / R
            return voltage / RESISTOR_R;
        }

        function updateDisplays() {
            // Напряжение на резисторе = sliderPosition (если ключ замкнут), иначе 0
            let voltage = keyClosed ? sliderPosition : 0;
            let current = keyClosed ? computeCurrent(voltage) : 0;

            // Округление для красивого отображения
            const voltageRounded = Math.round(voltage * 10) / 10;
            const currentRounded = Math.round(current * 1000) / 1000; // до мА

            voltmeterDisplay.textContent = voltageRounded.toFixed(1);
            ammeterDisplay.textContent = currentRounded.toFixed(2);

            // Обновляем подсказку у ползунка
            voltageHint.textContent = sliderPosition.toFixed(1) + ' В';

            // Двигаем ползунок реостата на схеме (позиция от 0 до 6 В -> от 170 до 230 пикселей)
            const startX = 170, endX = 230;
            const xPos = startX + (sliderPosition / 6) * (endX - startX);
            rheostatSlider.setAttribute('points', `${xPos-5},55 ${xPos+5},55 ${xPos},40`);
            sliderLine.setAttribute('x1', xPos);
            sliderLine.setAttribute('x2', xPos);

            // Ключ: визуально замыкаем/размыкаем
            if (keyClosed) {
                keyContact.setAttribute('x2', '140');
                keyContact.setAttribute('y2', '70');
                keyStatus.textContent = 'замкнут';
                toggleKeyBtn.textContent = 'Разомкнуть';
                recordBtn.disabled = false;
            } else {
                // Разомкнут: линия ключа поднимается
                keyContact.setAttribute('x2', '135');
                keyContact.setAttribute('y2', '55');
                keyStatus.textContent = 'разомкнут';
                toggleKeyBtn.textContent = 'Замкнуть';
                recordBtn.disabled = true;
            }

            // Если ключ разомкнут, показания нулевые — уже учтено
            // Также сбрасываем возможность записи, если сила тока 0 или напряжение 0?
            // Нет, можно записывать и 0, но для исследования лучше избегать нулевых точек.
            // Разрешим запись при напряжении > 0.1 В, но оставим возможность записать 0 для наглядности.
            // recordBtn.disabled = !keyClosed || sliderPosition < 0.1; // Закомментировано, пусть можно и 0
        }

        // Обновление таблицы и среднего R
        function updateTableAndStats() {
            if (measurements.length === 0) {
                tableBody.innerHTML = '<tr><td colspan="3" style="color:#94a3b8; font-style:italic;">Нет данных</td></tr>';
                avgRDisplay.textContent = '';
                conclusionBox.classList.remove('show');
                return;
            }

            let html = '';
            let sumR = 0;
            measurements.forEach((m, idx) => {
                const R = m.R;
                sumR += R;
                html += `<tr><td>${m.U.toFixed(1)}</td><td>${m.I.toFixed(3)}</td><td>${R.toFixed(2)}</td></tr>`;
            });
            tableBody.innerHTML = html;

            const avgR = sumR / measurements.length;
            avgRDisplay.innerHTML = `Среднее сопротивление: <strong>${avgR.toFixed(2)} Ом</strong> (истинное R = 10 Ом)`;

            // Проверка линейности и вывод
            if (measurements.length >= 4) {
                // Проверяем, что отношение U/I для всех точек примерно одинаковое (в пределах 5%)
                const ratios = measurements.map(m => m.R);
                const mean = ratios.reduce((a,b) => a+b, 0) / ratios.length;
                const maxDev = Math.max(...ratios.map(r => Math.abs(r - mean) / mean * 100));
                const isLinear = maxDev < 8; // допустимое отклонение 8%

                if (isLinear) {
                    conclusionBox.innerHTML = `✅ Зависимость силы тока от напряжения <strong>линейная</strong>.<br>
                    Среднее сопротивление R ≈ ${mean.toFixed(2)} Ом (близко к 10 Ом).<br>
                    <strong>Вывод:</strong> I = U / R — закон Ома выполняется.`;
                } else {
                    conclusionBox.innerHTML = `⚠️ Зависимость <strong>нелинейная</strong> (разброс R > 8%).<br>
                    Возможны погрешности измерений. Среднее R = ${mean.toFixed(2)} Ом.`;
                }
                conclusionBox.classList.add('show');
                // Показываем истинное сопротивление в индикаторе
                rIndicator.textContent = '10 Ом';
                rIndicator.style.color = '#2563eb';
            } else {
                conclusionBox.classList.remove('show');
                rIndicator.textContent = '??';
                rIndicator.style.color = '#64748b';
            }
        }

        // ========== ПОСТРОЕНИЕ ГРАФИКА ==========
        function drawGraph() {
            const w = canvas.width;
            const h = canvas.height;
            ctx.clearRect(0, 0, w, h);

            // Отступы
            const left = 50, right = 20, top = 20, bottom = 40;
            const graphW = w - left - right;
            const graphH = h - top - bottom;

            // Диапазоны: U от 0 до 6.5 В, I от 0 до 0.7 А
            const Umax = 6.5;
            const Imax = 0.7;

            // Рисуем оси
            ctx.beginPath();
            ctx.strokeStyle = '#94a3b8';
            ctx.lineWidth = 1.5;
            // Ось Y
            ctx.moveTo(left, top);
            ctx.lineTo(left, top + graphH);
            // Ось X
            ctx.moveTo(left, top + graphH);
            ctx.lineTo(left + graphW, top + graphH);
            ctx.stroke();

            // Стрелки
            ctx.beginPath();
            ctx.fillStyle = '#94a3b8';
            ctx.moveTo(left, top - 5);
            ctx.lineTo(left - 4, top + 5);
            ctx.lineTo(left + 4, top + 5);
            ctx.fill();
            ctx.beginPath();
            ctx.moveTo(left + graphW + 5, top + graphH);
            ctx.lineTo(left + graphW - 5, top + graphH - 4);
            ctx.lineTo(left + graphW - 5, top + graphH + 4);
            ctx.fill();

            // Подписи осей
            ctx.font = '12px "Segoe UI", sans-serif';
            ctx.fillStyle = '#475569';
            ctx.textAlign = 'center';
            ctx.fillText('U, В', left + graphW / 2, top + graphH + 30);
            ctx.save();
            ctx.translate(15, top + graphH / 2);
            ctx.rotate(-Math.PI / 2);
            ctx.fillText('I, А', 0, 0);
            ctx.restore();

            // Разметка по X (0, 1, 2, 3, 4, 5, 6)
            ctx.textAlign = 'center';
            ctx.fillStyle = '#64748b';
            for (let u = 0; u <= 6; u += 1) {
                const x = left + (u / Umax) * graphW;
                ctx.beginPath();
                ctx.strokeStyle = '#e2e8f0';
                ctx.lineWidth = 1;
                ctx.moveTo(x, top);
                ctx.lineTo(x, top + graphH);
                ctx.stroke();
                ctx.fillStyle = '#475569';
                ctx.fillText(u, x, top + graphH + 18);
            }

            // Разметка по Y (0, 0.1, 0.2, ... 0.7)
            ctx.textAlign = 'right';
            for (let i = 0; i <= 0.7; i += 0.1) {
                const y = top + graphH - (i / Imax) * graphH;
                ctx.beginPath();
                ctx.strokeStyle = '#e2e8f0';
                ctx.lineWidth = 1;
                ctx.moveTo(left, y);
                ctx.lineTo(left + graphW, y);
                ctx.stroke();
                ctx.fillStyle = '#475569';
                ctx.fillText(i.toFixed(1), left - 8, y + 4);
            }

            // Рисуем точки и линию
            if (measurements.length > 0) {
                // Сортируем по U для линии
                const sorted = [...measurements].sort((a,b) => a.U - b.U);
                // Линия (только если больше 1 точки)
                if (sorted.length > 1) {
                    ctx.beginPath();
                    ctx.strokeStyle = '#2563eb';
                    ctx.lineWidth = 2.5;
                    ctx.setLineDash([]);
                    sorted.forEach((m, idx) => {
                        const x = left + (m.U / Umax) * graphW;
                        const y = top + graphH - (m.I / Imax) * graphH;
                        if (idx === 0) ctx.moveTo(x, y);
                        else ctx.lineTo(x, y);
                    });
                    ctx.stroke();
                }
                // Точки
                sorted.forEach(m => {
                    const x = left + (m.U / Umax) * graphW;
                    const y = top + graphH - (m.I / Imax) * graphH;
                    ctx.beginPath();
                    ctx.fillStyle = '#e67e22';
                    ctx.arc(x, y, 6, 0, 2 * Math.PI);
                    ctx.fill();
                    ctx.strokeStyle = '#b45309';
                    ctx.lineWidth = 1.5;
                    ctx.stroke();
                });
            } else {
                // Нет данных — пишем
                ctx.font = '14px "Segoe UI", sans-serif';
                ctx.fillStyle = '#94a3b8';
                ctx.textAlign = 'center';
                ctx.fillText('Нет измерений', left + graphW/2, top + graphH/2);
            }
        }

        // ========== ОБРАБОТЧИКИ СОБЫТИЙ ==========
        function toggleKey() {
            keyClosed = !keyClosed;
            updateDisplays();
        }

        function onRheostatChange(e) {
            sliderPosition = parseFloat(e.target.value);
            updateDisplays();
            // Если ключ разомкнут, всё равно обновляем положение ползунка
        }

        function recordMeasurement() {
            if (!keyClosed) return; // на всякий случай

            const voltage = sliderPosition;
            const current = computeCurrent(voltage);
            if (voltage === 0 && current === 0) {
                // Можно записать, но предупредим? Просто добавим.
            }
            // Округляем для избежания накопления ошибок
            const U = Math.round(voltage * 10) / 10;
            const I = Math.round(current * 1000) / 1000;
            const R = U / I;

            measurements.push({ U, I, R });
            updateTableAndStats();
            drawGraph();
        }

        function clearAll() {
            measurements = [];
            updateTableAndStats();
            drawGraph();
            // Сбросим позицию реостата? По желанию. Оставим как есть.
            // Но можно сбросить ползунок на 0? Нет, пусть остаётся.
            // Обновим индикатор R
            rIndicator.textContent = '??';
            rIndicator.style.color = '#64748b';
            conclusionBox.classList.remove('show');
        }

        // ========== ИНИЦИАЛИЗАЦИЯ ==========
        function init() {
            // Начальное положение ползунка 0 В
            sliderPosition = 0;
            rheostatRange.value = 0;
            keyClosed = false;

            // Обновляем отображение
            updateDisplays();
            updateTableAndStats();
            drawGraph();

            // Навешиваем события
            toggleKeyBtn.addEventListener('click', toggleKey);
            rheostatRange.addEventListener('input', onRheostatChange);
            recordBtn.addEventListener('click', recordMeasurement);
            clearBtn.addEventListener('click', clearAll);

            // Первичная установка ползунка реостата на схеме
            updateDisplays();
        }

        // Запуск
        init();
    })();
</script>
</body>
</html>