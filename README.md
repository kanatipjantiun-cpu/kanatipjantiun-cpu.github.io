# Fifi

## About Me

I'm a Game & Animation student from Thailand, currently studying Digital Media Design at Rajamangala University of Technology Rattanakosin, Salaya Campus.

## Interests

Game Development  
2D Art  
3D Art  
Animation  

## Tools

Unity  
Blender  
Maya  
Premiere Pro  
CapCut  

## Hobbies

Ghibli  
One Piece  
Marvel  
Literature  
Manga  
Games


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Fifi — 3D Portfolio</title>

  <style>
    :root {
      --ink: #241d20;
      --paper: #f4ead8;
      --paper-dark: #d8c9ad;
      --rose: #9d5d68;
      --rose-dark: #6f3d47;
      --cream: #ede1ca;
      --muted: #6e6460;
      --glass: rgba(244, 234, 216, 0.78);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    html {
      scroll-behavior: smooth;
    }

    body {
      min-height: 100vh;
      overflow-x: hidden;
      background:
        radial-gradient(circle at 30% 20%, rgba(255,255,255,0.75), transparent 30%),
        linear-gradient(#dcd0bc, #baa992);
      color: var(--ink);
      font-family: Georgia, "Times New Roman", serif;
    }

    #scene {
      position: fixed;
      inset: 0;
      z-index: 0;
      width: 100%;
      height: 100%;
      touch-action: none;
    }

    #ui {
      position: fixed;
      inset: 0;
      z-index: 10;
      pointer-events: none;
    }

    .topbar {
      position: absolute;
      top: 18px;
      left: 50%;
      transform: translateX(-50%);
      width: min(940px, calc(100vw - 30px));
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px 14px 10px 18px;
      border: 1px solid rgba(50, 35, 35, 0.17);
      border-radius: 16px;
      background: rgba(240, 228, 208, 0.68);
      backdrop-filter: blur(14px);
      box-shadow: 0 8px 28px rgba(65, 48, 42, 0.14);
      pointer-events: auto;
    }

    .logo {
      font-weight: 700;
      letter-spacing: 0.14em;
      font-size: 0.85rem;
      color: var(--rose-dark);
    }

    .nav {
      display: flex;
      gap: 8px;
    }

    .nav button {
      border: 0;
      padding: 8px 12px;
      border-radius: 10px;
      background: transparent;
      color: var(--ink);
      cursor: pointer;
      font: inherit;
      font-size: 0.82rem;
    }

    .nav button:hover {
      background: rgba(111, 61, 71, 0.08);
    }

    .note {
      position: absolute;
      left: 24px;
      bottom: 26px;
      width: min(360px, calc(100vw - 48px));
      padding: 16px 18px;
      border: 1px solid rgba(50, 35, 35, 0.13);
      border-radius: 14px;
      background: var(--glass);
      box-shadow: 0 12px 35px rgba(65, 48, 42, 0.14);
      pointer-events: none;
    }

    .note strong {
      display: block;
      margin-bottom: 6px;
      color: var(--rose-dark);
    }

    .note p {
      color: var(--muted);
      line-height: 1.55;
      font-size: 0.83rem;
    }

    #loading {
      position: fixed;
      inset: 0;
      z-index: 30;
      display: grid;
      place-items: center;
      background: #d7cbb8;
      transition: opacity 0.6s ease;
    }

    #loading.hide {
      opacity: 0;
      pointer-events: none;
    }

    .loader {
      width: 34px;
      height: 34px;
      border: 2px solid rgba(36, 29, 32, 0.18);
      border-top-color: var(--rose);
      border-radius: 50%;
      animation: spin 0.9s linear infinite;
    }

    @keyframes spin {
      to { transform: rotate(360deg); }
    }

    /* Project book modal */
    #bookPanel {
      position: fixed;
      right: 18px;
      top: 80px;
      width: min(380px, calc(100vw - 36px));
      max-height: calc(100vh - 105px);
      overflow: auto;
      padding: 22px;
      border: 1px solid rgba(50, 35, 35, 0.16);
      border-radius: 16px;
      background: rgba(247, 237, 220, 0.96);
      box-shadow: 0 20px 60px rgba(48, 34, 30, 0.22);
      transform: translateY(-10px);
      opacity: 0;
      pointer-events: none;
      transition: 0.28s ease;
    }

    #bookPanel.open {
      transform: translateY(0);
      opacity: 1;
      pointer-events: auto;
    }

    #bookPanel .label {
      font-size: 0.7rem;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      color: var(--rose);
    }

    #bookPanel h2 {
      margin-top: 7px;
      font-size: 1.5rem;
    }

    #bookPanel p {
      margin-top: 10px;
      color: var(--muted);
      line-height: 1.7;
      font-size: 0.9rem;
    }

    .project-entry {
      margin-top: 16px;
      padding-top: 14px;
      border-top: 1px solid rgba(50,35,35,0.12);
    }

    .project-entry h3 {
      font-size: 1rem;
      color: var(--rose-dark);
    }

    .project-entry p {
      margin-top: 5px !important;
      font-size: 0.82rem !important;
    }

    .close {
      position: absolute;
      right: 12px;
      top: 10px;
      width: 30px;
      height: 30px;
      border: 0;
      border-radius: 50%;
      background: rgba(111,61,71,0.08);
      cursor: pointer;
      font-size: 18px;
      color: var(--rose-dark);
    }

    @media (max-width: 640px) {
      .topbar {
        top: 10px;
      }

      .nav button {
        padding: 7px 8px;
        font-size: 0.74rem;
      }

      .note {
        bottom: 14px;
        left: 14px;
        width: calc(100vw - 28px);
      }
    }
  </style>
</head>

<body>
  <div id="loading"><div class="loader"></div></div>
  <canvas id="scene"></canvas>

  <div id="ui">
    <div class="topbar">
      <div class="logo">FIFI / 3D PORTFOLIO</div>
      <div class="nav">
        <button id="homeBtn">Home</button>
        <button id="aboutBtn">Letter</button>
        <button id="projectBtn">Book</button>
      </div>
    </div>

    <div class="note">
      <strong>Welcome to my little post office.</strong>
      <p>
        Explore the scene with your mouse. Click the letter for About Me,
        the writing beside the mailbox for Skills, and the fallen book
        to open the project pages.
      </p>
    </div>

    <div id="bookPanel">
      <button class="close" id="closeBook">×</button>
      <div class="label">Selected Projects</div>
      <h2>Turn the pages.</h2>
      <p>
        The physical book in the scene represents my portfolio work.
        Use the buttons below to move through the pages.
      </p>

      <div class="project-entry">
        <h3>Page 01 — Lost Beneath the Eternal Sun</h3>
        <p>
          A 3D game project focused on exploration, problem-solving,
          planning, and environmental storytelling.
        </p>
      </div>

      <div class="project-entry">
        <h3>Page 02 — VR Judgment</h3>
        <p>
          A VR concept where the player becomes a judge, examines
          character records, and decides whether each soul belongs
          in heaven or hell.
        </p>
      </div>

      <div class="project-entry">
        <h3>Page 03 — 3D Assets & Environments</h3>
        <p>
          Modeling and environment experiments made for games,
          including rooms, props, herbs, and stylized assets.
        </p>
      </div>

      <div class="project-entry">
        <h3>Page 04 — Other Creative Works</h3>
        <p>
          Character, visual, animation, and interactive experiments
          created throughout my Game & Animation studies.
        </p>
      </div>
    </div>
  </div>

  <script type="module">
    import * as THREE from "https://cdn.jsdelivr.net/npm/three@0.180.0/build/three.module.js";
    import { OrbitControls } from "https://cdn.jsdelivr.net/npm/three@0.180.0/examples/jsm/controls/OrbitControls.js";

    const canvas = document.getElementById("scene");
    const scene = new THREE.Scene();
    scene.background = new THREE.Color(0xd8ccb8);
    scene.fog = new THREE.Fog(0xd8ccb8, 12, 30);

    const camera = new THREE.PerspectiveCamera(
      43,
      window.innerWidth / window.innerHeight,
      0.1,
      100
    );

    camera.position.set(7.4, 5.6, 10.2);

    const renderer = new THREE.WebGLRenderer({
      canvas,
      antialias: true,
      powerPreference: "high-performance"
    });

    renderer.setSize(window.innerWidth, window.innerHeight);
    renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    renderer.shadowMap.enabled = true;
    renderer.shadowMap.type = THREE.PCFSoftShadowMap;
    renderer.outputColorSpace = THREE.SRGBColorSpace;

    const controls = new OrbitControls(camera, renderer.domElement);
    controls.enableDamping = true;
    controls.enablePan = true;
    controls.minDistance = 6;
    controls.maxDistance = 18;
    controls.maxPolarAngle = Math.PI * 0.48;
    controls.target.set(0, 2.1, 0);

    // ---------- Materials ----------
    const mat = {
      ground: new THREE.MeshStandardMaterial({ color: 0xb3a58f, roughness: 0.96 }),
      red: new THREE.MeshStandardMaterial({ color: 0x8e4c58, roughness: 0.8, metalness: 0.05 }),
      redDark: new THREE.MeshStandardMaterial({ color: 0x5f343d, roughness: 0.86 }),
      metal: new THREE.MeshStandardMaterial({ color: 0x4c4540, roughness: 0.45, metalness: 0.55 }),
      paper: new THREE.MeshStandardMaterial({ color: 0xf2e5cd, roughness: 0.95 }),
      paper2: new THREE.MeshStandardMaterial({ color: 0xe5d6bb, roughness: 0.97 }),
      ink: new THREE.MeshStandardMaterial({ color: 0x292123, roughness: 0.92 }),
      leather: new THREE.MeshStandardMaterial({ color: 0x5c4142, roughness: 0.78 }),
      gold: new THREE.MeshStandardMaterial({ color: 0xc39f5d, roughness: 0.34, metalness: 0.65 })
    };

    // ---------- Helpers ----------
    function box(w, h, d, material, x = 0, y = 0, z = 0, parent = scene) {
      const mesh = new THREE.Mesh(new THREE.BoxGeometry(w, h, d), material);
      mesh.position.set(x, y, z);
      mesh.castShadow = true;
      mesh.receiveShadow = true;
      parent.add(mesh);
      return mesh;
    }

    function cyl(radiusTop, radiusBottom, height, material, x = 0, y = 0, z = 0, parent = scene) {
      const mesh = new THREE.Mesh(
        new THREE.CylinderGeometry(radiusTop, radiusBottom, height, 32),
        material
      );
      mesh.position.set(x, y, z);
      mesh.castShadow = true;
      mesh.receiveShadow = true;
      parent.add(mesh);
      return mesh;
    }

    function createLabelTexture(text, options = {}) {
      const canvas = document.createElement("canvas");
      canvas.width = 1024;
      canvas.height = options.height || 512;
      const ctx = canvas.getContext("2d");

      ctx.fillStyle = options.bg || "#eadfc9";
      ctx.fillRect(0, 0, canvas.width, canvas.height);

      ctx.strokeStyle = options.border || "#8b6d60";
      ctx.lineWidth = 10;
      ctx.strokeRect(20, 20, canvas.width - 40, canvas.height - 40);

      ctx.fillStyle = options.color || "#342829";
      ctx.textAlign = "center";
      ctx.textBaseline = "middle";

      const maxWidth = canvas.width - 100;
      let fontSize = options.fontSize || 52;
      ctx.font = `${options.italic ? "italic " : ""}${options.bold ? "700 " : ""}${fontSize}px Georgia`;

      const words = text.split(" ");
      const lines = [];
      let line = "";

      for (const word of words) {
        const candidate = line ? `${line} ${word}` : word;
        if (ctx.measureText(candidate).width > maxWidth && line) {
          lines.push(line);
          line = word;
        } else {
          line = candidate;
        }
      }
      if (line) lines.push(line);

      const lineHeight = fontSize * 1.28;
      const startY = canvas.height / 2 - ((lines.length - 1) * lineHeight) / 2;

      lines.forEach((l, i) => ctx.fillText(l, canvas.width / 2, startY + i * lineHeight));

      const texture = new THREE.CanvasTexture(canvas);
      texture.colorSpace = THREE.SRGBColorSpace;
      return texture;
    }

    function labelPlane(text, width, height, x, y, z, rotationY = 0, options = {}) {
      const texture = createLabelTexture(text, options);
      const geometry = new THREE.PlaneGeometry(width, height);
      const material = new THREE.MeshBasicMaterial({
        map: texture,
        transparent: true,
        side: THREE.DoubleSide
      });
      const mesh = new THREE.Mesh(geometry, material);
      mesh.position.set(x, y, z);
      mesh.rotation.y = rotationY;
      mesh.userData.interactive = options.interactive || null;
      mesh.castShadow = false;
      mesh.receiveShadow = false;
      scene.add(mesh);
      return mesh;
    }

    // ---------- Lighting ----------
    scene.add(new THREE.HemisphereLight(0xfff7e9, 0x6a5b50, 2.2));

    const sun = new THREE.DirectionalLight(0xffefd3, 3.2);
    sun.position.set(-6, 11, 8);
    sun.castShadow = true;
    sun.shadow.mapSize.set(2048, 2048);
    sun.shadow.camera.left = -11;
    sun.shadow.camera.right = 11;
    sun.shadow.camera.top = 11;
    sun.shadow.camera.bottom = -11;
    scene.add(sun);

    const warm = new THREE.PointLight(0xb56c72, 1.8, 9);
    warm.position.set(3, 3.5, 3);
    scene.add(warm);

    // ---------- Ground ----------
    box(24, 0.35, 24, mat.ground, 0, -0.18, 0);

    // Ground tiles / subtle lines
    for (let i = -10; i <= 10; i += 2) {
      const line = box(0.018, 0.008, 24, new THREE.MeshBasicMaterial({
        color: 0x8d816d,
        transparent: true,
        opacity: 0.22
      }), i, 0.01, 0);
      line.castShadow = false;
      line.receiveShadow = false;
    }

    // ---------- Mailbox ----------
    const mailbox = new THREE.Group();
    mailbox.position.set(0, 0, 0);
    scene.add(mailbox);

    // Post
    box(0.72, 3.0, 0.72, mat.redDark, 0, 1.35, 0, mailbox);
    box(1.65, 0.26, 1.25, mat.metal, 0, -0.08, 0, mailbox);

    // Body
    box(2.7, 2.3, 2.15, mat.red, 0, 3.05, 0, mailbox);

    // Rounded-ish roof
    const roof = new THREE.Mesh(
      new THREE.CylinderGeometry(1.075, 1.075, 2.7, 48, 1, false, 0, Math.PI),
      mat.red
    );
    roof.rotation.z = Math.PI / 2;
    roof.position.set(0, 4.20, 0);
    roof.castShadow = true;
    roof.receiveShadow = true;
    mailbox.add(roof);

    // Mail slot
    box(1.5, 0.18, 0.07, mat.metal, 0, 3.36, -1.10, mailbox);
    box(1.08, 0.06, 0.1, mat.gold, 0, 3.52, -1.14, mailbox);

    // Handle
    box(0.08, 0.48, 0.08, mat.metal, -0.78, 4.95, -0.75, mailbox);
    box(1.55, 0.1, 0.1, mat.metal, 0, 5.14, -0.75, mailbox);
    box(0.08, 0.48, 0.08, mat.metal, 0.78, 4.95, -0.75, mailbox);

    // Side panel texture
    const mailboxLabel = labelPlane(
      "FIFI",
      1.6,
      0.72,
      0,
      2.9,
      1.095,
      0,
      { bg: "#eadfc9", border: "#70424a", color: "#59343b", fontSize: 88, bold: true }
    );
    mailboxLabel.rotation.x = 0;
    mailboxLabel.position.set(0, 3.02, -1.11);

    // Flag
    const flagGroup = new THREE.Group();
    flagGroup.position.set(-1.38, 2.75, -0.12);
    mailbox.add(flagGroup);

    box(0.1, 2.0, 0.1, mat.gold, 0, 0.75, 0, flagGroup);
    box(0.1, 0.65, 0.1, mat.gold, 0, 1.70, 0, flagGroup);
    box(0.72, 0.48, 0.08, mat.gold, 0.30, 1.92, 0, flagGroup);

    // ---------- Letter on floor ----------
    const letterGroup = new THREE.Group();
    letterGroup.position.set(-3.1, 0.16, 1.45);
    letterGroup.rotation.y = -0.25;
    letterGroup.rotation.x = -0.04;
    scene.add(letterGroup);

    box(2.65, 0.08, 1.78, mat.paper, 0, 0, 0, letterGroup);

    const letterFace = labelPlane(
      "A LETTER ABOUT ME",
      2.3,
      0.98,
      -3.1,
      0.22,
      1.46,
      -0.25,
      { bg: "#f1e6d2", border: "#8b6d60", color: "#3e3030", fontSize: 60, bold: true, interactive: "about" }
    );
    letterFace.rotation.x = -0.04;

    // Envelope line
    for (let i = 0; i < 2; i++) {
      const line = box(1.75, 0.025, 0.025, mat.paper2, 0, 0.065, -0.35 + i * 0.7, letterGroup);
      line.rotation.y = i ? 0.28 : -0.28;
    }

    // ---------- Skills board ----------
    const skillBoard = new THREE.Group();
    skillBoard.position.set(2.85, 2.25, 0.8);
    skillBoard.rotation.y = -0.22;
    scene.add(skillBoard);

    box(2.55, 2.9, 0.18, mat.paper2, 0, 0, 0, skillBoard);
    box(2.25, 2.6, 0.03, mat.paper, 0, 0.02, -0.11, skillBoard);

    const skillTexture = createLabelTexture(
      "SKILLS\n\nUNITY  •  BLENDER\nMAYA  •  3D ART\n2D ART  •  ANIMATION\nGAME DESIGN",
      {
        bg: "#f2e5cd",
        border: "#8b6d60",
        color: "#493637",
        fontSize: 58,
        bold: false
      }
    );

    // Manually draw skill text with multi-line support
    const skillCanvas = document.createElement("canvas");
    skillCanvas.width = 1024;
    skillCanvas.height = 1100;
    const sctx = skillCanvas.getContext("2d");
    sctx.fillStyle = "#f2e5cd";
    sctx.fillRect(0, 0, 1024, 1100);
    sctx.strokeStyle = "#8b6d60";
    sctx.lineWidth = 12;
    sctx.strokeRect(24, 24, 976, 1052);

    const skillsText = [
      ["SKILLS", 80, true],
      ["UNITY", 52, false],
      ["BLENDER", 52, false],
      ["MAYA", 52, false],
      ["3D ART", 52, false],
      ["2D ART", 52, false],
      ["ANIMATION", 52, false],
      ["GAME DESIGN", 52, false]
    ];

    let sy = 180;
    skillsText.forEach(([t, size, bold]) => {
      sctx.fillStyle = bold ? "#7a414c" : "#493637";
      sctx.font = `${bold ? "700 " : ""}${size}px Georgia`;
      sctx.textAlign = "center";
      sctx.fillText(t, 512, sy);
      sy += bold ? 130 : 105;
    });

    const skillTex = new THREE.CanvasTexture(skillCanvas);
    skillTex.colorSpace = THREE.SRGBColorSpace;
    const skillMesh = new THREE.Mesh(
      new THREE.PlaneGeometry(2.18, 2.35),
      new THREE.MeshBasicMaterial({ map: skillTex })
    );
    skillMesh.position.set(0, 0.01, -0.12);
    skillBoard.add(skillMesh);

    // Small push pins
    [-0.92, 0.92].forEach(x => {
      cyl(0.05, 0.05, 0.08, mat.gold, x, 1.16, -0.16, skillBoard);
      const pin = skillBoard.children[skillBoard.children.length - 1];
      pin.rotation.x = Math.PI / 2;
    });

    // ---------- Book ----------
    const bookGroup = new THREE.Group();
    bookGroup.position.set(2.7, 0.22, -2.55);
    bookGroup.rotation.y = -0.28;
    bookGroup.rotation.x = 0.03;
    scene.add(bookGroup);

    box(3.25, 0.36, 2.35, mat.leather, 0, 0.18, 0, bookGroup);
    box(1.1, 0.05, 2.25, mat.gold, -1.05, 0.40, 0, bookGroup);

    // Page stack
    box(2.68, 0.58, 2.02, mat.paper2, 0.12, 0.49, 0, bookGroup);

    // Individual pages with slight overlap
    const pages = [];
    for (let i = 0; i < 5; i++) {
      const page = new THREE.Mesh(
        new THREE.BoxGeometry(1.30, 0.03, 1.92),
        new THREE.MeshStandardMaterial({ color: 0xf6ecd9, roughness: 0.98 })
      );
      page.position.set(0.52, 0.81 + i * 0.012, 0);
      page.rotation.y = 0.01 * i;
      page.castShadow = true;
      page.receiveShadow = true;
      bookGroup.add(page);
      pages.push(page);
    }

    // Cover
    const topCover = box(1.48, 0.08, 2.25, mat.leather, 1.02, 0.90, 0, bookGroup);
    topCover.rotation.z = 0.025;

    const bookTitle = labelPlane(
      "PORTFOLIO",
      1.15,
      0.55,
      2.7,
      1.0,
      -2.55,
      -0.28,
      { bg: "#5c4142", border: "#c39f5d", color: "#ead8b6", fontSize: 58, bold: true, interactive: "book" }
    );
    bookTitle.rotation.x = 0.03;

    // Clickable page tabs in the 3D scene
    const pageTabs = [];
    for (let i = 0; i < 4; i++) {
      const tab = new THREE.Mesh(
        new THREE.BoxGeometry(0.12, 0.18, 0.48),
        new THREE.MeshStandardMaterial({ color: i === 0 ? 0x8e4c58 : 0xc6aa8c })
      );
      tab.position.set(1.42, 0.98 + i * 0.025, -0.65 + i * 0.43);
      tab.rotation.z = -0.1;
      tab.userData.page = i;
      tab.userData.interactive = "page";
      tab.castShadow = true;
      bookGroup.add(tab);
      pageTabs.push(tab);
    }

    // ---------- Small decorative objects ----------
    // Flowers
    function flower(x, z, scale = 1) {
      const g = new THREE.Group();
      g.position.set(x, 0.15, z);
      g.scale.setScalar(scale);
      scene.add(g);

      cyl(0.035, 0.035, 0.65, new THREE.MeshStandardMaterial({ color: 0x71805b }), 0, 0.32, 0, g);

      for (let i = 0; i < 5; i++) {
        const petal = new THREE.Mesh(
          new THREE.SphereGeometry(0.13, 12, 8),
          new THREE.MeshStandardMaterial({ color: 0xb67783, roughness: 0.88 })
        );
        const a = i * (Math.PI * 2 / 5);
        petal.position.set(Math.cos(a) * 0.14, 0.66, Math.sin(a) * 0.14);
        petal.scale.set(1, 0.62, 1);
        petal.castShadow = true;
        g.add(petal);
      }

      const center = new THREE.Mesh(
        new THREE.SphereGeometry(0.10, 12, 8),
        mat.gold
      );
      center.position.y = 0.66;
      center.castShadow = true;
      g.add(center);
    }

    flower(-4.8, 2.5, 1.15);
    flower(4.7, 2.0, 0.8);

    // Little envelope stack
    for (let i = 0; i < 3; i++) {
      const env = box(1.45, 0.07, 0.9, i === 1 ? mat.paper2 : mat.paper, -4.0 + i * 0.08, 0.10 + i * 0.09, -2.7 + i * 0.08);
      env.rotation.y = -0.1 - i * 0.04;
    }

    // ---------- Interaction ----------
    const raycaster = new THREE.Raycaster();
    const pointer = new THREE.Vector2();
    let hovered = null;

    function setPointer(event) {
      const rect = renderer.domElement.getBoundingClientRect();
      pointer.x = ((event.clientX - rect.left) / rect.width) * 2 - 1;
      pointer.y = -((event.clientY - rect.top) / rect.height) * 2 + 1;
    }

    renderer.domElement.addEventListener("pointermove", event => {
      setPointer(event);
      raycaster.setFromCamera(pointer, camera);
      const hits = raycaster.intersectObjects(scene.children, true);
      let target = null;

      for (const hit of hits) {
        if (hit.object.userData.interactive) {
          target = hit.object;
          break;
        }
      }

      if (hovered && hovered !== target) {
        hovered.scale.multiplyScalar(1 / 1.05);
      }

      hovered = target;

      if (hovered) {
        hovered.scale.multiplyScalar(1.05);
        renderer.domElement.style.cursor = "pointer";
      } else {
        renderer.domElement.style.cursor = "grab";
      }
    });

    renderer.domElement.addEventListener("pointerdown", event => {
      setPointer(event);
      raycaster.setFromCamera(pointer, camera);

      const hits = raycaster.intersectObjects(scene.children, true);
      for (const hit of hits) {
        const obj = hit.object;
        if (obj.userData.interactive === "about") {
          openLetter();
          return;
        }
        if (obj.userData.interactive === "book") {
          openBook(0);
          return;
        }
        if (obj.userData.interactive === "page") {
          openBook(obj.userData.page);
          return;
        }
      }
    });

    // ---------- Information panels ----------
    const bookPanel = document.getElementById("bookPanel");

    function openBook(page = 0) {
      bookPanel.classList.add("open");
      pageIndex = Math.max(0, Math.min(3, page));
      updateBookPage();
    }

    function closeBook() {
      bookPanel.classList.remove("open");
    }

    function openLetter() {
      alert(
        "ABOUT FIFI\\n\\n" +
        "Game & Animation student from Thailand.\\n\\n" +
        "Studying Digital Media Design at Rajamangala University of Technology Rattanakosin, Salaya Campus.\\n\\n" +
        "Interested in Game Development, 2D Art, 3D Art, Animation, storytelling and interactive design.\\n\\n" +
        "Tools: Unity, Blender, Maya, Premiere Pro and CapCut.\\n\\n" +
        "Outside of development: Ghibli, One Piece, Marvel, literature, manga and games."
      );
    }

    document.getElementById("closeBook").addEventListener("click", closeBook);
    document.getElementById("aboutBtn").addEventListener("click", openLetter);
    document.getElementById("projectBtn").addEventListener("click", () => openBook(0));

    document.getElementById("homeBtn").addEventListener("click", () => {
      camera.position.set(7.4, 5.6, 10.2);
      controls.target.set(0, 2.1, 0);
      closeBook();
    });

    let pageIndex = 0;

    function updateBookPage() {
      const titles = [
        "PAGE 01 — LOST BENEATH THE ETERNAL SUN",
        "PAGE 02 — VR JUDGMENT",
        "PAGE 03 — 3D ASSETS & ENVIRONMENTS",
        "PAGE 04 — OTHER CREATIVE WORKS"
      ];

      const entries = document.querySelectorAll(".project-entry");
      document.querySelector("#bookPanel h2").textContent = titles[pageIndex];
      entries.forEach((entry, i) => {
        entry.style.display = i === pageIndex ? "block" : "none";
      });

      // Animate the physical pages.
      pages.forEach((page, i) => {
        const target = i === pageIndex ? 0.16 : 0.01 * i;
        page.rotation.y += (target - page.rotation.y) * 0.12;
      });
    }

    // Keyboard navigation for the physical book.
    window.addEventListener("keydown", event => {
      if (!bookPanel.classList.contains("open")) return;

      if (event.key === "ArrowRight") {
        pageIndex = Math.min(3, pageIndex + 1);
        updateBookPage();
      }

      if (event.key === "ArrowLeft") {
        pageIndex = Math.max(0, pageIndex - 1);
        updateBookPage();
      }

      if (event.key === "Escape") {
        closeBook();
      }
    });

    // Double click background resets camera.
    renderer.domElement.addEventListener("dblclick", () => {
      camera.position.set(7.4, 5.6, 10.2);
      controls.target.set(0, 2.1, 0);
    });

    // ---------- Animation ----------
    const clock = new THREE.Clock();

    function animate() {
      requestAnimationFrame(animate);

      const t = clock.getElapsedTime();

      // Subtle life in the scene.
      mailbox.rotation.y = Math.sin(t * 0.45) * 0.006;
      letterGroup.rotation.z = -0.01 + Math.sin(t * 0.7) * 0.006;
      skillBoard.rotation.z = Math.sin(t * 0.5) * 0.008;
      bookGroup.rotation.z = Math.sin(t * 0.55) * 0.008;

      controls.update();
      renderer.render(scene, camera);
    }

    window.addEventListener("resize", () => {
      camera.aspect = window.innerWidth / window.innerHeight;
      camera.updateProjectionMatrix();
      renderer.setSize(window.innerWidth, window.innerHeight);
      renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2));
    });

    animate();

    window.addEventListener("load", () => {
      setTimeout(() => {
        document.getElementById("loading").classList.add("hide");
      }, 550);
    });
  </script>
</body>
</html>

[index.html](https://github.com/user-attachments/files/31989526/index.html)
