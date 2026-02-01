<script>
  const features = [
    {
      icon: "⚡",
      title: "Lightning Fast",
      description:
        "Built with Tauri and Rust for native performance. Sub-50MB install, instant startup, minimal memory footprint. No Electron bloat.",
      highlight: false,
    },
    {
      icon: "📴",
      title: "Offline First",
      description:
        "Most tools work entirely locally. No tracking, no cloud dependencies, no privacy concerns. Your data never leaves your machine.",
      highlight: false,
    },
    {
      icon: "📊",
      title: "Dashboard",
      description:
        "See recently used tools and follow your own RSS feeds to stay updated. Quick access to everything you need at a glance.",
      highlight: false,
    },
    {
      icon: "🎯",
      title: "Productivity‑first UI",
      description:
        "Reorder tools, hide what you don't use, group them into modules and get to work quickly. Customize your workflow exactly how you want it.",
      highlight: false,
    },
    {
      icon: "🎯",
      title: "No Fluff",
      description:
        "Only tools developers actually use daily. No novelty widgets, no filler. Every feature is battle-tested and production-ready.",
      highlight: false,
    },
    {
      icon: "🌍",
      title: "Cross-Platform",
      description:
        "Native builds for macOS (Intel & Apple Silicon), Windows, and Linux. Same experience, same shortcuts, everywhere you code.",
      highlight: false,
    },
  ];
</script>

<section class="section" id="features">
  <div class="container">
    <div class="section-header">
      <div class="section-label">Why DevBox</div>
      <h2>Built for speed. Designed for developers.</h2>
      <p class="section-description">
        Native performance, offline-first architecture, and a
        productivity-focused interface that gets out of your way.
      </p>
    </div>

    <div class="features-grid">
      {#each features as feature, i}
        <div
          class="feature-card {feature.highlight ? 'highlight' : ''}"
          style="animation-delay: {i * 0.1}s"
        >
          <span class="feature-icon">{feature.icon}</span>
          <h3 class="feature-title">{feature.title}</h3>
          <p class="feature-description">{feature.description}</p>
          {#if feature.highlight}
            <div class="highlight-badge">Featured</div>
          {/if}
        </div>
      {/each}
    </div>
  </div>
</section>

<style>
  .section {
    padding: 8rem 2rem;
    position: relative;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
  }

  .section-header {
    text-align: center;
    margin-bottom: 5rem;
  }

  .section-label {
    color: var(--accent-primary);
    font-size: 0.9rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 1rem;
  }

  h2 {
    font-family: "Syne", sans-serif;
    font-size: 3rem;
    font-weight: 700;
    margin-bottom: 1rem;
  }

  .section-description {
    font-size: 1.1rem;
    color: var(--text-secondary);
    max-width: 600px;
    margin: 0 auto;
  }

  .features-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 2rem;
  }

  .feature-card {
    background: var(--bg-secondary);
    border: 1px solid var(--border);
    padding: 2.5rem;
    border-radius: 12px;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
    opacity: 0;
    animation: fadeInUp 0.6s ease-out forwards;
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

  .feature-card::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 4px;
    background: linear-gradient(
      90deg,
      var(--accent-primary),
      var(--accent-blue)
    );
    transform: scaleX(0);
    transform-origin: left;
    transition: transform 0.3s;
  }

  .feature-card:hover::before {
    transform: scaleX(1);
  }

  .feature-card:hover {
    border-color: var(--accent-primary);
    transform: translateY(-4px);
  }

  .feature-card.highlight {
    border-color: var(--accent-primary);
    background: linear-gradient(
      135deg,
      var(--bg-secondary),
      var(--bg-tertiary)
    );
    position: relative;
  }

  .feature-card.highlight::before {
    transform: scaleX(1);
  }

  .highlight-badge {
    position: absolute;
    top: 1rem;
    right: 1rem;
    background: var(--accent-primary);
    color: var(--bg-primary);
    padding: 0.3rem 0.8rem;
    border-radius: 12px;
    font-size: 0.7rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
  }

  .feature-icon {
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
    display: block;
  }

  .feature-title {
    font-family: "Syne", sans-serif;
    font-size: 1.5rem;
    font-weight: 700;
    margin-bottom: 1rem;
  }

  .feature-description {
    color: var(--text-secondary);
    line-height: 1.7;
  }

  @media (max-width: 768px) {
    .section {
      padding: 4rem 1.5rem;
    }

    .section-header {
      margin-bottom: 3rem;
    }

    .features-grid {
      grid-template-columns: 1fr;
      gap: 1.5rem;
    }

    .feature-card {
      padding: 2rem;
    }

    h2 {
      font-size: 2rem;
      line-height: 1.2;
    }

    .section-description {
      font-size: 1rem;
    }
  }

  @media (max-width: 480px) {
    h2 {
      font-size: 1.75rem;
    }

    .feature-card {
      padding: 1.5rem;
    }

    .feature-icon {
      font-size: 2rem;
    }

    .feature-title {
      font-size: 1.25rem;
    }
  }
</style>
