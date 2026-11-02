<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<title>蓝色圣诞树 · Blue Christmas Tree</title>
<style>
  html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    background: radial-gradient(ellipse at bottom, #0b1b3a 0%, #02060f 100%);
    overflow: hidden;
    font-family: "Segoe UI", "Microsoft YaHei", sans-serif;
  }
  canvas {
    display: block;
    width: 100%;
    height: 100%;
  }
  .title {
    position: absolute;
    top: 24px;
    left: 50%;
    transform: translateX(-50%);
    color: #9ad8ff;
    letter-spacing: 6px;
    font-size: 14px;
    opacity: 0.7;
    text-shadow: 0 0 12px rgba(120, 200, 255, 0.6);
    pointer-events: none;
    user-select: none;
  }
  .hint {
    position: absolute;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%);
    color: #6fa8dc;
    font-size: 12px;
    opacity: 0.5;
    pointer-events: none;
    user-select: none;
  }
</style>
</head>
<body>
  <div class="title">✦  MERRY  CHRISTMAS  ✦</div>
  <canvas id="scene"></canvas>
  <div class="hint">点击屏幕撒下雪花 · Move your mouse</div>

<script>
(() => {
  const canvas = document.getElementById('scene');
  const ctx = canvas.getContext('2d');
  let W, H;

  function resize() {
    W = canvas.width = window.innerWidth * devicePixelRatio;
    H = canvas.height = window.innerHeight * devicePixelRatio;
    canvas.style.width = window.innerWidth + 'px';
    canvas.style.height = window.innerHeight + 'px';
    buildTree();
  }

  // ---------- Tree structure ----------
  const TREE = [];        // tree particles (points forming tree shape)
  const DECOR = [];       // light decorations on tree
  const SNOW = [];        // snowflakes
  const STAR = { x: 0, y: 0, phase: 0 };

  // blue palette
  const TREE_COLORS = [
    [30, 100, 200],   // deep blue
    [60, 150, 230],   // medium blue
    [120, 200, 255],  // sky blue
    [180, 230, 255],  // icy blue
  ];

  function pickColor() {
    return TREE_COLORS[(Math.random() * TREE_COLORS.length) | 0];
  }

  function buildTree() {
    TREE.length = 0;
    DECOR.length = 0;

    const cx = W / 2;
    const baseY = H * 0.88;
    const height = Math.min(W, H) * 0.72;
    const topY = baseY - height;

    // Generate cone layers
    const layers = 10;
    const particlesPerLayer = 260;

    for (let i = 0; i < layers; i++) {
      // i=0 top, i=layers-1 bottom
      const t = i / (layers - 1);          // 0..1
      const y = topY + height * t;
      // radius grows non-linearly for a natural pine look
      const radius = height * 0.38 * Math.pow(t, 1.35);

      for (let j = 0; j < particlesPerLayer; j++) {
        const angle = Math.random() * Math.PI * 2;
        // radial jitter: outer fluff
        const r = radius * (0.85 + Math.random() * 0.25);
        const px = cx + Math.cos(angle) * r;
        const py = y + (Math.random() - 0.5) * height * 0.06;
        const col = pickColor();
        // twinkle phase
        const phase = Math.random() * Math.PI * 2;
        TREE.push({
          x: px, y: py,
          ox: px, oy: py,
          r: devicePixelRatio * (0.9 + Math.random() * 1.1),
          color: col,
          phase: phase,
          twinkleSpeed: 0.01 + Math.random() * 0.03,
          drift: Math.random() * Math.PI * 2,
        });
      }
    }

    // Trunk
    const trunkTop = baseY - height * 0.02;
    const trunkBot = baseY + height * 0.06;
    const trunkW = height * 0.05;
    for (let y = trunkTop; y < trunkBot; y += 4) {
      for (let i = 0; i < 12; i++) {
        TREE.push({
          x: cx + (Math.random() - 0.5) * trunkW,
          y: y + (Math.random() - 0.5) * 3,
          ox: cx, oy: y,
          r: devicePixelRatio * (0.8 + Math.random() * 0.8),
          color: [70, 50, 110],
          phase: 0, twinkleSpeed: 0, drift: 0,
        });
      }
    }

    // Decorations — bright blue & cyan lights
    const decorCount = 70;
    for (let i = 0; i < decorCount; i++) {
      const t = Math.pow(Math.random(), 0.7);
      const y = topY + height * t;
      const radius = height * 0.38 * Math.pow(t, 1.35);
      const angle = Math.random() * Math.PI * 2;
      const r = radius * (0.55 + Math.random() * 0.4);
      const dx = cx + Math.cos(angle) * r;
      const dy = y + (Math.random() - 0.5) * height * 0.05;
      const hue = 190 + Math.random() * 50;      // cyan → blue-violet
      DECOR.push({
        x: dx, y: dy,
        ox: dx, oy: dy,
        hue: hue,
        phase: Math.random() * Math.PI * 2,
        speed: 0.02 + Math.random() * 0.04,
        size: devicePixelRatio * (2 + Math.random() * 2.2),
      });
    }

    // Star on top
    STAR.x = cx;
    STAR.y = topY - height * 0.02;
    STAR.phase = 0;
  }

  // ---------- Snow ----------
  function spawnSnow(n) {
    for (let i = 0; i < n; i++) {
      SNOW.push(makeSnow(true));
    }
  }
  function makeSnow(initial) {
    return {
      x: Math.random() * W,
      y: initial ? Math.random() * H : -10,
      r: devicePixelRatio * (0.8 + Math.random() * 1.8),
      vx: (Math.random() - 0.5) * 0.6 * devicePixelRatio,
      vy: (0.5 + Math.random() * 1.1) * devicePixelRatio,
      phase: Math.random() * Math.PI * 2,
      alpha: 0.4 + Math.random() * 0.5,
    };
  }
  spawnSnow(220);

  // ---------- Mouse interaction ----------
  const mouse = { x: -9999, y: -9999, active: false };
  window.addEventListener('mousemove', e => {
    mouse.x = e.clientX * devicePixelRatio;
    mouse.y = e.clientY * devicePixelRatio;
    mouse.active = true;
  });
  window.addEventListener('mouseleave', () => mouse.active = false);
  window.addEventListener('click', e => {
    const cx = e.clientX * devicePixelRatio;
    const cy = e.clientY * devicePixelRatio;
    // burst snow from click
    for (let i = 0; i < 60; i++) {
      SNOW.push({
        x: cx, y: cy,
        r: devicePixelRatio * (1 + Math.random() * 2),
        vx: (Math.random() - 0.5) * 4 * devicePixelRatio,
        vy: (Math.random() - 0.5) * 4 * devicePixelRatio,
        phase: Math.random() * Math.PI * 2,
        alpha: 0.7 + Math.random() * 0.3,
      });
    }
  });

  window.addEventListener('resize', resize);

  // ---------- Animation ----------
  let frame = 0;
  function loop() {
    frame++;

    // Fade trail for glow effect
    ctx.fillStyle = 'rgba(2, 6, 15, 0.28)';
    ctx.fillRect(0, 0, W, H);

    // ---- Tree particles ----
    for (let i = 0; i < TREE.length; i++) {
      const p = TREE[i];
      p.drift += 0.02;
      let x = p.ox + Math.sin(p.drift) * 1.4;
      let y = p.oy + Math.cos(p.drift * 0.8) * 0.9;

      // Mouse push away
      if (mouse.active) {
        const dx = x - mouse.x, dy = y - mouse.y;
        const d2 = dx * dx + dy * dy;
        const R = 120 * devicePixelRatio;
        if (d2 < R * R && d2 > 0.01) {
          const d = Math.sqrt(d2);
          const f = (1 - d / R) * 18;
          x += (dx / d) * f;
          y += (dy / d) * f;
        }
      }

      const twinkle = 0.55 + Math.sin(frame * p.twinkleSpeed + p.phase) * 0.45;
      const [r, g, b] = p.color;
      const a = Math.max(0.15, twinkle);

      ctx.beginPath();
      ctx.fillStyle = `rgba(${r|0},${g|0},${b|0},${a})`;
      ctx.arc(x, y, p.r, 0, Math.PI * 2);
      ctx.fill();

      // soft glow for bright particles
      if (p.color[1] > 130) {
        ctx.beginPath();
        ctx.fillStyle = `rgba(${r|0},${g|0},${b|0},${a * 0.15})`;
        ctx.arc(x, y, p.r * 3, 0, Math.PI * 2);
        ctx.fill();
      }
    }

    // ---- Decorations ----
    ctx.globalCompositeOperation = 'lighter';
    for (let i = 0; i < DECOR.length; i++) {
      const d = DECOR[i];
      d.phase += d.speed;
      const pulse = 0.5 + Math.sin(d.phase) * 0.5;
      const alpha = 0.55 + pulse * 0.45;
      const glowR = d.size * (3 + pulse * 3);

      // outer glow
      const grd = ctx.createRadialGradient(d.x, d.y, 0, d.x, d.y, glowR);
      grd.addColorStop(0, `hsla(${d.hue}, 100%, 85%, ${alpha})`);
      grd.addColorStop(0.4, `hsla(${d.hue}, 100%, 65%, ${alpha * 0.35})`);
      grd.addColorStop(1, `hsla(${d.hue}, 100%, 55%, 0)`);
      ctx.fillStyle = grd;
      ctx.beginPath();
      ctx.arc(d.x, d.y, glowR, 0, Math.PI * 2);
      ctx.fill();

      // core
      ctx.fillStyle = `hsla(${d.hue}, 100%, 95%, ${alpha})`;
      ctx.beginPath();
      ctx.arc(d.x, d.y, d.size, 0, Math.PI * 2);
      ctx.fill();
    }

    // ---- Star on top ----
    STAR.phase += 0.04;
    const starPulse = 0.6 + Math.sin(STAR.phase) * 0.4;
    const sGlowR = 40 * devicePixelRatio * starPulse;
    const starGrd = ctx.createRadialGradient(STAR.x, STAR.y, 0, STAR.x, STAR.y, sGlowR);
    starGrd.addColorStop(0, `rgba(220, 240, 255, ${0.9 * starPulse})`);
    starGrd.addColorStop(0.3, `rgba(140, 200, 255, ${0.4 * starPulse})`);
    starGrd.addColorStop(1, `rgba(60, 120, 220, 0)`);
    ctx.fillStyle = starGrd;
    ctx.beginPath();
    ctx.arc(STAR.x, STAR.y, sGlowR, 0, Math.PI * 2);
    ctx.fill();

    // draw 5-pointed star
    drawStar(STAR.x, STAR.y, 5, 10 * devicePixelRatio * starPulse,
             4 * devicePixelRatio * starPulse, `rgba(255,255,255,${0.95})`);

    // ---- Snow ----
    for (let i = SNOW.length - 1; i >= 0; i--) {
      const s = SNOW[i];
      s.phase += 0.02;
      s.x += s.vx + Math.sin(s.phase) * 0.3 * devicePixelRatio;
      s.y += s.vy;
      // gentle mouse repel
      if (mouse.active) {
        const dx = s.x - mouse.x, dy = s.y - mouse.y;
        const d2 = dx * dx + dy * dy;
        const R = 80 * devicePixelRatio;
        if (d2 < R * R && d2 > 0.01) {
          const d = Math.sqrt(d2);
          const f = (1 - d / R) * 2;
          s.x += (dx / d) * f;
          s.y += (dy / d) * f;
        }
      }

      // fade near bottom
      const bottomFade = Math.max(0, 1 - Math.max(0, s.y - H * 0.85) / (H * 0.15));
      const a = s.alpha * bottomFade;

      if (s.y > H + 10 || s.x < -20 || s.x > W + 20 || a <= 0.01) {
        SNOW.splice(i, 1);
        continue;
      }

      ctx.beginPath();
      ctx.fillStyle = `rgba(220, 235, 255, ${a})`;
      ctx.arc(s.x, s.y, s.r, 0, Math.PI * 2);
      ctx.fill();
    }
    // keep snow population
    while (SNOW.length < 220) SNOW.push(makeSnow(false));

    ctx.globalCompositeOperation = 'source-over';

    requestAnimationFrame(loop);
  }

  function drawStar(cx, cy, spikes, outerR, innerR, fill) {
    let rot = -Math.PI / 2;
    const step = Math.PI / spikes;
    ctx.beginPath();
    ctx.moveTo(cx + Math.cos(rot) * outerR, cy + Math.sin(rot) * outerR);
    for (let i = 0; i < spikes; i++) {
      rot += step;
      ctx.lineTo(cx + Math.cos(rot) * innerR, cy + Math.sin(rot) * innerR);
      rot += step;
      ctx.lineTo(cx + Math.cos(rot) * outerR, cy + Math.sin(rot) * outerR);
    }
    ctx.closePath();
    ctx.fillStyle = fill;
    ctx.fill();
  }

  resize();
  loop();
})();
</script>
</body>
</html>
