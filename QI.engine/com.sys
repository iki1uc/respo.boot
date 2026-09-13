<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>🧠 BRAIN · ROOT · KOOP · FEELING · WORK</title>
    <style>
        * { margin:0; padding:0; box-sizing:border-box; }
        body {
            background: #05070e;
            color: #c0d0d0;
            font-family: 'Segoe UI', 'Consolas', monospace;
            overflow: hidden;
            height: 100vh;
            display: flex;
            flex-direction: column;
        }

        /* ─── MASTER LAYOUT ─────────────────────────────────── */
        #master {
            display: flex;
            flex: 1;
            height: 100vh;
            overflow: hidden;
        }

        /* ─── LEFT: NAVIGATION / ORDNER-STRUKTUR ───────────── */
        #nav {
            width: 320px;
            min-width: 280px;
            background: rgba(6, 8, 16, 0.92);
            backdrop-filter: blur(12px);
            border-right: 1px solid rgba(120, 220, 150, 0.08);
            padding: 16px 14px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            z-index: 10;
            transition: width 0.3s;
        }
        #nav::-webkit-scrollbar { width: 3px; }
        #nav::-webkit-scrollbar-thumb { background: #1a2a3a; border-radius: 4px; }

        #nav .brand {
            font-size: 18px;
            font-weight: 300;
            letter-spacing: 4px;
            background: linear-gradient(135deg, #7ee0a0, #d8f0c0, #b388ff);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            padding-bottom: 12px;
            border-bottom: 1px solid rgba(120, 220, 150, 0.06);
            margin-bottom: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        #nav .brand small { font-size: 10px; -webkit-text-fill-color: #4a5a6a; }

        .nav-section { margin-bottom: 12px; }
        .nav-section .head {
            font-size: 10px;
            text-transform: uppercase;
            letter-spacing: 2px;
            color: #4a6a5a;
            padding-bottom: 4px;
            border-bottom: 1px solid rgba(120, 220, 150, 0.04);
            margin-bottom: 6px;
            display: flex;
            justify-content: space-between;
        }
        .nav-item {
            display: flex;
            align-items: center;
            gap: 8px;
            padding: 4px 8px;
            border-radius: 6px;
            font-size: 11.5px;
            color: #8aa8a0;
            cursor: pointer;
            transition: all 0.2s;
            border-left: 2px solid transparent;
        }
        .nav-item:hover { background: rgba(120, 220, 150, 0.04); color: #d0e8e0; border-left-color: #7ee0a0; }
        .nav-item .icon { font-size: 14px; width: 20px; text-align: center; }
        .nav-item .badge { font-size: 8px; background: rgba(120, 220, 150, 0.08); padding: 0 8px; border-radius: 10px; color: #4a7a6a; margin-left: auto; }
        .nav-item.active { background: rgba(120, 220, 150, 0.06); border-left-color: #f0d080; color: #f0d080; }
        .nav-item .dot { display: inline-block; width: 6px; height: 6px; border-radius: 50%; margin-right: 4px; }
        .dot.green { background: #8cf0d0; box-shadow: 0 0 6px #8cf0d0; }
        .dot.gold { background: #f0d080; box-shadow: 0 0 6px #f0d080; }
        .dot.purple { background: #b388ff; box-shadow: 0 0 6px #b388ff; }

        .nav-divider { height: 1px; background: rgba(120, 220, 150, 0.04); margin: 8px 0; }

        /* ─── RIGHT: 3D STAGE ──────────────────────────────── */
        #stage {
            flex: 1;
            background: #05070e;
            position: relative;
            overflow: hidden;
        }
        #stage canvas {
            display: block;
            width: 100%;
            height: 100%;
        }

        /* ─── STATUS OVERLAY ────────────────────────────────── */
        #status {
            position: absolute;
            top: 16px;
            right: 20px;
            background: rgba(0, 0, 0, 0.6);
            backdrop-filter: blur(8px);
            border-radius: 12px;
            padding: 8px 16px;
            font-size: 10px;
            color: #6a8a7a;
            border: 1px solid rgba(120, 220, 150, 0.06);
            pointer-events: none;
            z-index: 20;
            line-height: 1.6;
            text-align: right;
            min-width: 120px;
        }
        #status .val { color: #a0e0b0; font-weight: bold; }
        #status .gold { color: #f0d080; }

        /* ─── FEELING / KOOP LOG ───────────────────────────── */
        #feeling {
            position: absolute;
            bottom: 16px;
            left: 20px;
            right: 20px;
            background: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(4px);
            border-radius: 10px;
            padding: 6px 14px;
            font-size: 9px;
            color: #5a7a6a;
            border: 1px solid rgba(120, 220, 150, 0.04);
            z-index: 20;
            display: flex;
            flex-wrap: wrap;
            gap: 8px 20px;
            pointer-events: none;
            max-height: 56px;
            overflow-y: auto;
        }
        #feeling .koop { color: #8cf0d0; }
        #feeling .work { color: #f0d080; }
        #feeling .brain { color: #b388ff; }

        /* ─── TOGGLE NAV ────────────────────────────────────── */
        #toggleNav {
            position: absolute;
            top: 16px;
            left: 16px;
            z-index: 30;
            background: rgba(6, 8, 16, 0.7);
            border: 1px solid rgba(120, 220, 150, 0.1);
            border-radius: 8px;
            color: #8aa8a0;
            padding: 4px 10px;
            font-size: 16px;
            cursor: pointer;
            transition: 0.2s;
            font-family: inherit;
        }
        #toggleNav:hover { border-color: #7ee0a0; color: #d0e8e0; }

        /* ─── RESPONSIVE ────────────────────────────────────── */
        @media (max-width: 820px) {
            #nav { width: 0; min-width: 0; padding: 0; overflow: hidden; border: none; }
            #nav.open { width: 280px; min-width: 280px; padding: 16px 14px; border-right: 1px solid rgba(120,220,150,0.08); }
            #status { font-size: 9px; padding: 6px 12px; min-width: 80px; }
        }
    </style>
</head>
<body>

<div id="master">

    <!-- NAVIGATION / ORDNER-STRUKTUR -->
    <div id="nav">
        <div class="brand">
            🧠 BRAIN
            <small>ROOT · KOOP</small>
        </div>

        <div class="nav-section">
            <div class="head">📦 KERN / CORE</div>
            <div class="nav-item" data-target="core"><span class="icon">⚙</span> axiom.map.js <span class="badge">DNA</span></div>
            <div class="nav-item" data-target="core"><span class="icon">📐</span> vec.js / vec.3 / vec.9 <span class="badge">VEC</span></div>
            <div class="nav-item" data-target="core"><span class="icon">🧠</span> OS_CORE.js <span class="badge">KERN</span></div>
            <div class="nav-item" data-target="core"><span class="icon">🌀</span> coord.js <span class="badge">KOORD</span></div>
            <div class="nav-item" data-target="core"><span class="icon">⚡</span> NC_space / time / kraft / figur <span class="badge">NC</span></div>
        </div>

        <div class="nav-divider"></div>

        <div class="nav-section">
            <div class="head">💾 HDF‑ROMs</div>
            <div class="nav-item" data-target="hdf"><span class="icon">📀</span> d / e / i / n / o / r / s / u / w <span class="badge">9×</span></div>
            <div class="nav-item" data-target="hdf"><span class="icon">✅</span> sli.ready <span class="badge">READY</span></div>
        </div>

        <div class="nav-divider"></div>

        <div class="nav-section">
            <div class="head">🧩 MODULE · STATIONEN</div>
            <div class="nav-item" data-target="boerse"><span class="icon">📈</span> BOERSE <span class="badge">index.html</span></div>
            <div class="nav-item" data-target="dom"><span class="icon">🏛</span> DOM <span class="badge">stage.html</span></div>
            <div class="nav-item" data-target="eos"><span class="icon">🌌</span> EOS <span class="badge">index.html</span></div>
            <div class="nav-item" data-target="evo"><span class="icon">🔮</span> EVO <span class="badge">stage.html</span></div>
            <div class="nav-item" data-target="markt"><span class="icon">🏪</span> MARKT <span class="badge">index.html</span></div>
            <div class="nav-item" data-target="respo"><span class="icon">🌀</span> RESPO <span class="badge">stage.html</span></div>
            <div class="nav-item" data-target="tool48"><span class="icon">🛠</span> TOOL48 <span class="badge">ui.html</span></div>
        </div>

        <div class="nav-divider"></div>

        <div class="nav-section">
            <div class="head">📐 ACHSEN · TIEFE · BREITE</div>
            <div class="nav-item" data-target="breite"><span class="icon">↔</span> Breite.hdf.ready.js <span class="badge">B</span></div>
            <div class="nav-item" data-target="tiefe"><span class="icon">↕</span> lauf.tiefe.ready.js <span class="badge">T</span></div>
            <div class="nav-item" data-target="hoch"><span class="icon">↗</span> lauf.hoch.ready.js <span class="badge">H</span></div>
        </div>

        <div class="nav-divider"></div>

        <div class="nav-section">
            <div class="head">🖥 VIEWER · STAGE</div>
            <div class="nav-item" data-target="viewer"><span class="icon">👁</span> etage-8-orbit-viewer <span class="badge">8</span></div>
            <div class="nav-item" data-target="viewer"><span class="icon">🎨</span> NC.css / time.css / NC.suite <span class="badge">UI</span></div>
            <div class="nav-item" data-target="stage"><span class="icon">🎬</span> stage.html / stage.raw <span class="badge">MASTER</span></div>
        </div>

        <div class="nav-divider"></div>

        <div class="nav-section" style="margin-top:auto; padding-top:12px; border-top:1px solid rgba(120,220,150,0.04);">
            <div class="nav-item" id="navKoop" style="border-left-color:#b388ff; color:#b388ff;">
                <span class="icon">🤝</span> KOOP‑MODUS <span class="badge" style="color:#b388ff;">AKTIV</span>
            </div>
            <div class="nav-item" id="navFeeling" style="border-left-color:#f0d080; color:#f0d080;">
                <span class="icon">💛</span> FEELING‑LEVEL <span class="badge" style="color:#f0d080;" id="feelingLevel">0</span>
            </div>
        </div>
    </div>

    <!-- 3D STAGE -->
    <div id="stage">
        <canvas id="stageCanvas"></canvas>

        <!-- STATUS -->
        <div id="status">
            <div>🧠 BRAIN <span class="val">AKTIV</span></div>
            <div>🌀 ORBIT <span class="gold" id="orbitStatus">0°</span></div>
            <div>📦 MODUL <span class="val" id="moduleStatus">ROOT</span></div>
            <div>⚡ RESPO <span class="val" id="respoStatus">–</span></div>
        </div>

        <!-- FEELING / KOOP LOG -->
        <div id="feeling">
            <span class="brain">🧠 BRAIN · logikal kooperativ</span>
            <span class="koop">🤝 KOOP · verbunden</span>
            <span class="work">💛 WORK · flow</span>
            <span id="feelingMsg" style="color:#6a8a7a;">→ Klick auf Spiegel = Modul öffnen</span>
        </div>

        <!-- TOGGLE NAV -->
        <button id="toggleNav">☰</button>
    </div>
</div>

<script type="importmap">
{
    "imports": {
        "three": "https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js",
        "three/addons/": "https://cdn.jsdelivr.net/npm/three@0.160.0/examples/jsm/"
    }
}
</script>

<script type="module">
// ================================================================
//  BRAIN · ROOT · KOOP · FEELING · WORK
//  Three.js 3D-Szene mit drei klickbaren Spiegeln (Screens),
//  die als Navigation zu den Modulen dienen.
//  Integriert die gesamte Ordner-STRUKTUR als Navigations-Karte.
// ================================================================

import * as THREE from 'three';
import { OrbitControls } from 'three/addons/controls/OrbitControls.js';

// ─── DOM REFS ──────────────────────────────────────────────────
const nav = document.getElementById('nav');
const toggleBtn = document.getElementById('toggleNav');
const canvas = document.getElementById('stageCanvas');
const statusModul = document.getElementById('moduleStatus');
const respoStatus = document.getElementById('respoStatus');
const orbitStatus = document.getElementById('orbitStatus');
const feelingMsg = document.getElementById('feelingMsg');
const feelingLevel = document.getElementById('feelingLevel');

// ─── NAV TOGGLE ──────────────────────────────────────────────
toggleBtn.addEventListener('click', () => nav.classList.toggle('open'));

// ─── THREE.JS SETUP ──────────────────────────────────────────
const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
renderer.toneMapping = THREE.ACESFilmicToneMapping;
renderer.toneMappingExposure = 1.2;

const scene = new THREE.Scene();
scene.background = new THREE.Color(0x05070e);
scene.fog = new THREE.Fog(0x05070e, 8, 18);

const camera = new THREE.PerspectiveCamera(38, canvas.clientWidth / canvas.clientHeight, 0.1, 30);
camera.position.set(5, 3.5, 7);

const controls = new OrbitControls(camera, renderer.domElement);
controls.enableDamping = true;
controls.dampingFactor = 0.06;
controls.autoRotate = false;
controls.autoRotateSpeed = 0.8;
controls.target.set(0, 0.3, 0);
controls.minDistance = 3;
controls.maxDistance = 16;
controls.update();

// ─── LIGHTS ──────────────────────────────────────────────────
scene.add(new THREE.AmbientLight(0x222244, 0.6));
const dLight = new THREE.DirectionalLight(0xffeedd, 2.2);
dLight.position.set(6, 10, 8);
dLight.castShadow = true;
scene.add(dLight);
scene.add(new THREE.DirectionalLight(0x4488ff, 0.5).position.set(-4, 2, -4));
scene.add(new THREE.DirectionalLight(0x88ddff, 0.3).position.set(0, -2, 5));

// ─── BODEN / GITTER ──────────────────────────────────────────
const gridHelper = new THREE.GridHelper(5.5, 11, 0x44aa77, 0x226644);
gridHelper.position.y = -0.65;
scene.add(gridHelper);

// ─── RESPO‑PUNKTE (9×9, schwebend) ──────────────────────────
const RESPO_SIZE = 9;
const TOTAL = 81;
const respoPositions = new Float32Array(TOTAL * 3);
const respoColors = new Float32Array(TOTAL * 3);
const respoValues = new Float32Array(TOTAL);
let respoTime = 0;

for (let r = 0; r < RESPO_SIZE; r++) {
    for (let c = 0; c < RESPO_SIZE; c++) {
        const idx = r * RESPO_SIZE + c;
        const x = (c / (RESPO_SIZE - 1) - 0.5) * 4.2;
        const z = (r / (RESPO_SIZE - 1) - 0.5) * 4.2;
        respoPositions[idx * 3] = x;
        respoPositions[idx * 3 + 1] = -0.3 + 0.05 * Math.sin(r * 0.5 + c * 0.3);
        respoPositions[idx * 3 + 2] = z;
        respoColors[idx * 3] = 0.2;
        respoColors[idx * 3 + 1] = 0.6;
        respoColors[idx * 3 + 2] = 0.8;
        respoValues[idx] = 0.5 + 0.4 * Math.sin(idx * 0.15);
    }
}

const respoGeo = new THREE.BufferGeometry();
respoGeo.setAttribute('position', new THREE.BufferAttribute(respoPositions, 3));
respoGeo.setAttribute('color', new THREE.BufferAttribute(respoColors, 3));
const respoMat = new THREE.PointsMaterial({
    size: 0.22,
    vertexColors: true,
    transparent: true,
    opacity: 0.85,
    blending: THREE.AdditiveBlending,
    depthWrite: false,
    sizeAttenuation: true,
});
const respoPoints = new THREE.Points(respoGeo, respoMat);
scene.add(respoPoints);

// ─── 3 SPIEGEL (Screens) als klickbare Navigation ──────────
const mirrorGroup = new THREE.Group();
scene.add(mirrorGroup);

function createClickableMirror(color, label, angleDeg, posZ, rotX) {
    const group = new THREE.Group();
    const geo = new THREE.PlaneGeometry(1.6, 2.2);
    const mat = new THREE.MeshStandardMaterial({
        color: color,
        emissive: color,
        emissiveIntensity: 0.06,
        side: THREE.DoubleSide,
        transparent: true,
        opacity: 0.3,
        roughness: 0.1,
        metalness: 0.85,
    });
    const mesh = new THREE.Mesh(geo, mat);
    mesh.castShadow = true;
    mesh.receiveShadow = true;
    group.add(mesh);

    // Rahmen
    const edges = new THREE.EdgesGeometry(geo);
    const lineMat = new THREE.LineBasicMaterial({ color: 0x88ddbb, transparent: true, opacity: 0.25 });
    const line = new THREE.LineSegments(edges, lineMat);
    group.add(line);

    // Label als Sprite
    const c = document.createElement('canvas');
    c.width = 128; c.height = 48;
    const ctx = c.getContext('2d');
    ctx.fillStyle = 'rgba(0,0,0,0)';
    ctx.fillRect(0, 0, 128, 48);
    ctx.font = 'bold 18px Consolas';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillStyle = '#88ddbb';
    ctx.fillText(label, 64, 24);
    const tex = new THREE.CanvasTexture(c);
    const spriteMat2 = new THREE.SpriteMaterial({ map: tex, transparent: true, depthTest: false });
    const sprite = new THREE.Sprite(spriteMat2);
    sprite.scale.set(0.5, 0.18, 1);
    sprite.position.z = 0.01;
    group.add(sprite);

    // Position & Rotation
    const angleRad = angleDeg * Math.PI / 180;
    group.position.set(Math.sin(angleRad) * 1.4, 0, Math.cos(angleRad) * 1.4);
    group.rotation.y = -angleRad;
    group.rotation.x = rotX || 0;

    // Klick-Interaktion über Raycaster
    mesh.userData = { target: label.toLowerCase().replace(/[^a-z]/g, '') };
    return { group, mesh };
}

const screenConfigs = [
    { color: 0x0088ff, label: 'BOERSE', angle: 0, posZ: 1.4, rotX: 0.05 },
    { color: 0xff44aa, label: 'DOM', angle: 120, posZ: 1.4, rotX: 0.05 },
    { color: 0x88ddff, label: 'EVO', angle: 240, posZ: 1.4, rotX: 0.05 },
];

const screenMeshes = [];
screenConfigs.forEach(cfg => {
    const result = createClickableMirror(cfg.color, cfg.label, cfg.angle, cfg.posZ, cfg.rotX);
    mirrorGroup.add(result.group);
    screenMeshes.push(result.mesh);
});

// Zusätzliche kleine Labels für die anderen Module (als Sprite-Overlay)
function addMiniLabel(text, x, y, z, color = '#f0d080') {
    const c = document.createElement('canvas');
    c.width = 64; c.height = 24;
    const ctx = c.getContext('2d');
    ctx.clearRect(0, 0, 64, 24);
    ctx.font = '12px Consolas';
    ctx.textAlign = 'center';
    ctx.textBaseline = 'middle';
    ctx.fillStyle = color;
    ctx.fillText(text, 32, 12);
    const tex = new THREE.CanvasTexture(c);
    const mat = new THREE.SpriteMaterial({ map: tex, transparent: true, depthTest: false, opacity: 0.6 });
    const sprite = new THREE.Sprite(mat);
    sprite.position.set(x, y, z);
    sprite.scale.set(0.6, 0.22, 1);
    scene.add(sprite);
}
addMiniLabel('MARKT', -1.8, 1.0, -1.5, '#8cf0d0');
addMiniLabel('RESPO', 1.8, 1.0, -1.5, '#b388ff');
addMiniLabel('TOOL48', 0, -0.2, -2.2, '#f0d080');
addMiniLabel('EOS', -2.2, -0.8, 0.8, '#88ddff');
addMiniLabel('breite', 2.2, -0.8, 0.8, '#7ee0a0');

// ─── RAYCASTER (Klick auf Spiegel) ──────────────────────────
const raycaster = new THREE.Raycaster();
const pointer = new THREE.Vector2();

renderer.domElement.addEventListener('click', (event) => {
    const rect = renderer.domElement.getBoundingClientRect();
    pointer.x = ((event.clientX - rect.left) / rect.width) * 2 - 1;
    pointer.y = -((event.clientY - rect.top) / rect.height) * 2 + 1;

    raycaster.setFromCamera(pointer, camera);
    const intersects = raycaster.intersectObjects(screenMeshes);
    if (intersects.length > 0) {
        const hit = intersects[0].object;
        const target = hit.userData.target || 'root';
        statusModul.textContent = target.toUpperCase();
        feelingMsg.textContent = `🌀 → Modul ${target.toUpperCase()} geöffnet`;
        logFeeling(`📂 ${target.toUpperCase()} · Klick auf Spiegel`);

        // Simulation: öffne das Modul (in echt: window.location.href = './modules/${target}/index.html')
        // Hier zeigen wir nur den Status an.
        if (target === 'boerse') showModuleInfo('BOERSE', '📈 Börsen‑Daten · Stage‑System');
        else if (target === 'dom') showModuleInfo('DOM', '🏛 Dom‑Struktur · NC‑Raum');
        else if (target === 'evo') showModuleInfo('EVO', '🔮 Evolution · Axiom‑Map');
        else showModuleInfo(target.toUpperCase(), '📦 Modul geladen · READY');
    }
});

function showModuleInfo(name, desc) {
    document.getElementById('status').innerHTML = `
        <div>🧠 BRAIN <span class="val">AKTIV</span></div>
        <div>🌀 MODUL <span class="gold">${name}</span></div>
        <div>📋 ${desc}</div>
        <div>⚡ RESPO <span class="val">${Math.round(40 + Math.random() * 40)}%</span></div>
    `;
    // Respo-Wert aktualisieren
    respoStatus.textContent = Math.round(40 + Math.random() * 40) + '%';
}

// ─── FEELING / KOOP LOG ─────────────────────────────────────
let feelingCount = 0;
function logFeeling(msg) {
    feelingCount++;
    const el = document.getElementById('feeling');
    const entry = document.createElement('span');
    entry.style.color = '#6a8a7a';
    entry.textContent = `· ${msg}`;
    el.appendChild(entry);
    if (el.children.length > 12) el.removeChild(el.children[0]);
    feelingLevel.textContent = Math.min(100, feelingCount);
    el.scrollTop = el.scrollHeight;
}

// ─── NAVIGATION KLICK ────────────────────────────────────────
document.querySelectorAll('.nav-item[data-target]').forEach(item => {
    item.addEventListener('click', () => {
        const target = item.dataset.target;
        statusModul.textContent = target.toUpperCase();
        feelingMsg.textContent = `📂 → ${target.toUpperCase()} (Navigation)`;
        logFeeling(`📂 ${target.toUpperCase()} · Navigation`);
        // Simuliere Modul-Ladung
        if (target === 'core') showModuleInfo('CORE', '⚙ Kernel · OS_CORE · Axiom');
        else if (target === 'hdf') showModuleInfo('HDF', '💾 ROMs · d/e/i/n/o/r/s/u/w');
        else if (target === 'boerse' || target === 'dom' || target === 'evo' || target === 'markt' || target === 'respo' || target === 'tool48') {
            showModuleInfo(target.toUpperCase(), `📦 Modul ${target.toUpperCase()} · stage.html bereit`);
        } else if (target === 'breite' || target === 'tiefe' || target === 'hoch') {
            showModuleInfo(target.toUpperCase(), `📐 Achse ${target.toUpperCase()} · ready.js`);
        } else {
            showModuleInfo(target.toUpperCase(), '📂 Ordner · READY');
        }
        // Nav auf Mobil schließen
        if (window.innerWidth < 820) nav.classList.remove('open');
    });
});

// ─── ANIMATION ───────────────────────────────────────────────
function animate() {
    requestAnimationFrame(animate);
    respoTime += 0.02;

    // Respo-Punkte pulssieren
    const pos = respoGeo.attributes.position.array;
    const col = respoGeo.attributes.color.array;
    let sum = 0;
    for (let i = 0; i < TOTAL; i++) {
        const val = 0.5 + 0.4 * Math.sin(i * 0.15 + respoTime);
        respoValues[i] = Math.max(0.05, Math.min(0.95, val));
        sum += respoValues[i];
        const yBase = -0.3 + 0.05 * Math.sin(i * 0.2 + respoTime * 0.5);
        pos[i * 3 + 1] = yBase + (respoValues[i] - 0.5) * 0.5;
        const r = 0.2 + 0.6 * respoValues[i];
        const g = 0.5 + 0.4 * respoValues[i];
        const b = 0.8 - 0.5 * respoValues[i];
        col[i * 3] = r;
        col[i * 3 + 1] = g;
        col[i * 3 + 2] = b;
    }
    respoGeo.attributes.position.needsUpdate = true;
    respoGeo.attributes.color.needsUpdate = true;
    const avg = sum / TOTAL;
    document.getElementById('respoStatus').textContent = Math.round(avg * 100) + '%';

    // Orbit-Status
    const euler = new THREE.Euler().setFromQuaternion(camera.quaternion);
    orbitStatus.textContent = Math.round(euler.y * 180 / Math.PI) + '°';

    controls.update();
    renderer.render(scene, camera);
}

// ─── RESIZE ───────────────────────────────────────────────────
function resize() {
    const w = canvas.parentElement.clientWidth;
    const h = canvas.parentElement.clientHeight;
    renderer.setSize(w, h, false);
    camera.aspect = w / h;
    camera.updateProjectionMatrix();
}
window.addEventListener('resize', resize);
resize();

// ─── INIT ────────────────────────────────────────────────────
logFeeling('🧠 BRAIN · ROOT initialisiert');
logFeeling('🤝 KOOP · 3 Spiegel = Navigation');
logFeeling('💛 FEELING · Klick auf Spiegel oder Menü');
logFeeling('🌀 RESPO · 81 Punkte · live');
statusModul.textContent = 'ROOT';
feelingMsg.textContent = '✨ Klick auf Spiegel oder Menü — System lebt';

animate();

// ─── FEELING‑LEVEL automatisch erhöhen ──────────────────────
setInterval(() => {
    const current = parseInt(feelingLevel.textContent) || 0;
    if (current < 100) {
        feelingLevel.textContent = Math.min(100, current + 1);
    }
}, 15000);

</script>
</body>
</html>
