<script>
  import { onMount } from "svelte";

  let terminalLines = [
    { prompt: "$", text: "devbox --version", visible: false },
    { prompt: "", text: "v1.1.0", visible: false },
    { prompt: "$", text: "All tools ready offline ✓", visible: false },
  ];

  onMount(() => {
    terminalLines.forEach((line, i) => {
      setTimeout(
        () => {
          terminalLines[i].visible = true;
          terminalLines = [...terminalLines];
        },
        1000 + i * 300,
      );
    });
  });

  const tools = [
    { icon: "🔐", name: "JWT Decoder" },
    { icon: "📡", name: "REST Client" },
    { icon: "✨", name: "JSON Format" },
    { icon: "🔄", name: "Base64" },
    { icon: "🎨", name: "SVG Preview" },
    { icon: "⏰", name: "Cron Parser" },
  ];

  function smoothScroll(e, target) {
    e.preventDefault();
    document.querySelector(target)?.scrollIntoView({ behavior: "smooth" });
  }

  // 3D hover effect
  let rotateX = 0;
  let rotateY = 0;

  function handleMouseMove(e) {
    const card = e.currentTarget;
    const rect = card.getBoundingClientRect();
    const x = e.clientX - rect.left;
    const y = e.clientY - rect.top;

    const centerX = rect.width / 2;
    const centerY = rect.height / 2;

    rotateY = ((x - centerX) / centerX) * 10;
    rotateX = ((centerY - y) / centerY) * 10;
  }

  function handleMouseLeave() {
    rotateX = 0;
    rotateY = 0;
  }
</script>

<section class="hero">
  <div class="container">
    <div class="hero-content">
      <span class="hero-label">🚀 Open Source • Cross-Platform</span>
      <h1>
        Developer tools.<br />
        <span class="gradient-text">One app.</span><br />
        Zero friction.
      </h1>
      <p class="hero-description">
        Stop juggling browser tabs and online tools. DevBox bundles 30+
        essential utilities into one fast, offline-first desktop app built with
        Tauri and React.
      </p>
      <div class="cta-buttons">
        <a
          href="#download"
          on:click={(e) => smoothScroll(e, "#download")}
          class="btn btn-primary"
        >
          ↓ Download App
        </a>
        <a
          href="https://devbox-app.smithgajjar.dev/"
          target="_blank"
          class="btn btn-secondary"
        >
          Try Web Version →
        </a>
        <!-- <a href="https://github.com/smithg09/devbox" class="btn btn-secondary">
          View on GitHub
        </a> -->
      </div>
      <p class="webapp-note">
        💡 Want a quick check? Try our <a
          href="https://devbox-app.smithgajjar.dev/"
          target="_blank">web version</a
        > instantly, or download the desktop app for full offline access and better
        performance.
      </p>
      <div class="stats">
        <div class="stat">
          <span class="stat-value">30+</span>
          <span class="stat-label">Developer Tools</span>
        </div>
        <div class="stat">
          <span class="stat-value">&lt;50MB</span>
          <span class="stat-label">App Size</span>
        </div>
        <div class="stat">
          <span class="stat-value">100%</span>
          <span class="stat-label">Offline</span>
        </div>
      </div>
    </div>

    <div class="hero-visual">
      <div
        class="app-preview"
        on:mousemove={handleMouseMove}
        on:mouseleave={handleMouseLeave}
        style="transform: perspective(1000px) rotateX({rotateX}deg) rotateY({rotateY}deg);"
      >
        <img src="/app.png" alt="DevBox App Interface" class="app-screenshot" />
      </div>
    </div>
  </div>
</section>

<style>
  .hero {
    margin-top: 80px;
    min-height: calc(100vh - 80px);
    display: flex;
    align-items: center;
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: "";
    position: absolute;
    width: 800px;
    height: 800px;
    background: radial-gradient(
      circle,
      rgba(0, 255, 136, 0.05),
      transparent 70%
    );
    top: -200px;
    right: -200px;
    animation: pulse 8s ease-in-out infinite;
  }

  @keyframes pulse {
    0%,
    100% {
      transform: scale(1);
      opacity: 0.05;
    }
    50% {
      transform: scale(1.1);
      opacity: 0.08;
    }
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 4rem 2rem;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 2rem;
    align-items: center;
  }

  .hero-content {
    animation: slideInLeft 0.8s ease-out;
  }

  @keyframes slideInLeft {
    from {
      opacity: 0;
      transform: translateX(-30px);
    }
    to {
      opacity: 1;
      transform: translateX(0);
    }
  }

  .hero-label {
    display: inline-block;
    background: var(--bg-tertiary);
    border: 1px solid var(--border);
    padding: 0.4rem 1rem;
    border-radius: 20px;
    font-size: 0.85rem;
    margin-bottom: 2rem;
    color: var(--accent-primary);
  }

  h1 {
    font-family: "Syne", sans-serif;
    font-size: 4rem;
    font-weight: 800;
    line-height: 1.1;
    margin-bottom: 1.5rem;
    letter-spacing: -0.03em;
  }

  .gradient-text {
    background: linear-gradient(
      135deg,
      var(--accent-primary),
      var(--accent-blue)
    );
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .hero-description {
    font-size: 1.2rem;
    color: var(--text-secondary);
    margin-bottom: 2.5rem;
    line-height: 1.7;
  }

  .cta-buttons {
    display: flex;
    gap: 1rem;
    margin-bottom: 1rem;
    flex-wrap: wrap;
  }

  .webapp-note {
    font-size: 0.95rem;
    color: var(--text-muted);
    margin-bottom: 2rem;
    line-height: 1.6;
  }

  .webapp-note a {
    color: var(--accent-primary);
    text-decoration: none;
    font-weight: 600;
  }

  .webapp-note a:hover {
    text-decoration: underline;
  }

  .btn {
    padding: 1rem 2rem;
    border-radius: 8px;
    font-weight: 600;
    text-decoration: none;
    transition: all 0.2s;
    cursor: pointer;
    font-size: 1rem;
    border: none;
    font-family: "JetBrains Mono", monospace;
    display: inline-flex;
    align-items: center;
    gap: 0.5rem;
  }

  .btn-primary {
    background: var(--accent-primary);
    color: var(--text-primary);
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 40px var(--shadow);
  }

  .btn-secondary {
    background: transparent;
    color: var(--text-primary);
    border: 1px solid var(--border);
  }

  .btn-secondary:hover {
    border-color: var(--accent-primary);
    color: var(--accent-primary);
  }

  .stats {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 2rem;
    margin-top: 3rem;
  }

  .stat {
    opacity: 0;
    animation: fadeInUp 0.6s ease-out forwards;
  }

  .stat:nth-child(1) {
    animation-delay: 0.2s;
  }
  .stat:nth-child(2) {
    animation-delay: 0.3s;
  }
  .stat:nth-child(3) {
    animation-delay: 0.4s;
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

  .stat-value {
    font-family: "Syne", sans-serif;
    font-size: 2.5rem;
    font-weight: 700;
    color: var(--text-secondary);
    display: block;
  }

  .stat-label {
    font-size: 0.9rem;
    color: var(--text-muted);
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .hero-visual {
    position: relative;
    animation: slideInRight 0.8s ease-out;
    margin-top: -8rem;
  }

  @keyframes slideInRight {
    from {
      opacity: 0;
      transform: translateX(30px);
    }
    to {
      opacity: 1;
      transform: translateX(0);
    }
  }

  .app-preview {
    position: relative;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 20px 60px rgba(0, 0, 0, 0.5);
    transform-style: preserve-3d;
    transition:
      transform 0.1s ease-out,
      box-shadow 0.3s ease;
    cursor: pointer;
  }

  .app-preview:hover {
    box-shadow:
      0 30px 80px rgba(0, 149, 255, 0.2),
      0 0 40px rgba(0, 149, 255, 0.1);
  }

  .app-screenshot {
    width: 100%;
    height: auto;
    display: block;
    transform: translateZ(20px);
    transition: transform 0.1s ease-out;
  }

  .screenshot-placeholder {
    padding: 4rem 2rem;
    text-align: center;
    background: linear-gradient(
      135deg,
      var(--bg-secondary),
      var(--bg-tertiary)
    );
    border: 2px dashed var(--border);
  }

  .placeholder-icon {
    font-size: 4rem;
    display: block;
    margin-bottom: 1rem;
    opacity: 0.5;
  }

  .screenshot-placeholder p {
    color: var(--text-secondary);
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }

  .screenshot-placeholder small {
    color: var(--text-muted);
    font-family: "JetBrains Mono", monospace;
    font-size: 0.85rem;
  }

  @media (max-width: 1024px) {
    .container {
      grid-template-columns: 1fr;
      gap: 3rem;
    }

    .hero-visual {
      margin-top: 0;
    }

    h1 {
      font-size: 3.5rem;
    }
  }

  @media (max-width: 768px) {
    .hero {
      margin-top: 60px;
      min-height: auto;
      padding: 2rem 0;
    }

    .container {
      padding: 2rem 1.5rem;
      gap: 2rem;
    }

    h1 {
      font-size: 2.5rem;
      line-height: 1.2;
    }

    .hero-description {
      font-size: 1rem;
      line-height: 1.6;
    }

    .cta-buttons {
      flex-direction: column;
      width: 100%;
    }

    .btn {
      width: 100%;
      justify-content: center;
      padding: 0.9rem 1.5rem;
      font-size: 0.95rem;
    }

    .webapp-note {
      font-size: 0.85rem;
      line-height: 1.5;
    }

    .stats {
      gap: 1.5rem;
      margin-top: 2rem;
    }

    .stat-value {
      font-size: 2rem;
    }

    .screenshot-placeholder {
      padding: 3rem 1.5rem;
    }

    .placeholder-icon {
      font-size: 3rem;
    }

    .screenshot-placeholder p {
      font-size: 1rem;
    }
  }

  @media (max-width: 480px) {
    h1 {
      font-size: 2rem;
    }

    .hero-label {
      font-size: 0.75rem;
      padding: 0.3rem 0.8rem;
    }

    .btn {
      padding: 0.8rem 1.2rem;
      font-size: 0.9rem;
    }
  }
</style>
