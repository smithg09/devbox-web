<script>
  let scrollY = 0;

  function smoothScroll(e, target) {
    e.preventDefault();
    const element = document.querySelector(target);
    if (element) {
      element.scrollIntoView({ behavior: "smooth", block: "start" });
    }
  }
</script>

<svelte:window bind:scrollY />

<nav class:scrolled={scrollY > 50}>
  <div class="container">
    <div class="logo">
      <img src="/devbox.png" alt="DevBox Logo" class="logo-icon" />
      <span>DevBox</span>
    </div>

    <div class="nav-content">
      <ul class="nav-links">
        <li>
          <a href="#features" on:click={(e) => smoothScroll(e, "#features")}
            >Features</a
          >
        </li>
        <li>
          <a href="#tools" on:click={(e) => smoothScroll(e, "#tools")}>Tools</a>
        </li>
      </ul>

      <div class="nav-actions">
        <a
          href="https://github.com/smithg09/devbox"
          class="icon-btn github-btn"
          target="_blank"
          rel="noopener noreferrer"
          title="View on GitHub"
        >
          Github
          <svg viewBox="0 0 24 24" fill="currentColor" width="18" height="18">
            <path
              d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"
            />
          </svg>
        </a>
        <a
          href="#download"
          on:click={(e) => smoothScroll(e, "#download")}
          class="btn-download"
        >
          Download
        </a>
      </div>
    </div>
  </div>
</nav>

<style>
  nav {
    position: fixed;
    top: 0;
    width: 100%;
    background: rgba(10, 10, 10, 0.8);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    z-index: 1000;
    padding: 1.2rem 0;
    transition: all 0.3s;
  }

  nav.scrolled {
    padding: 0.8rem 0;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav-content {
    display: flex;
    align-items: center;
    gap: 3rem;
    flex: 1;
    justify-content: space-between;
    margin-left: 3rem;
  }

  .logo {
    display: flex;
    align-items: center;
    gap: 0.8rem;
    font-family: "Syne", sans-serif;
    font-weight: 800;
    font-size: 1.4rem;
    letter-spacing: -0.02em;
  }

  .logo-icon {
    width: 32px;
    height: 32px;
    border-radius: 6px;
    object-fit: cover;
  }

  .nav-links {
    display: flex;
    gap: 2rem;
    list-style: none;
    align-items: center;
  }

  .nav-links a {
    color: var(--text-secondary);
    text-decoration: none;
    font-size: 0.95rem;
    font-weight: 400;
    transition: color 0.2s;
  }

  .nav-links a:hover {
    color: var(--accent-primary);
  }

  .nav-actions {
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }

  .icon-btn {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 6px;
    color: var(--text-secondary);
    gap: 0.5rem;
    transition: all 0.2s;
    text-decoration: none;
    padding: 0.2rem 1rem;
  }

  .icon-btn:hover {
    border-color: var(--accent-primary);
    color: var(--accent-primary);
    background: rgba(0, 132, 255, 0.05);
  }

  .github-btn svg,
  .star-btn svg {
    flex-shrink: 0;
  }

  .btn-download {
    background: var(--accent-primary);
    color: var(--text-primary);
    padding: 0.6rem 1.8rem;
    border-radius: 6px;
    font-weight: 600;
    font-size: 0.95rem;
    text-decoration: none;
    transition: all 0.2s;
    white-space: nowrap;
  }

  .btn-download:hover {
    transform: translateY(-1px);
    box-shadow: 0 4px 12px rgba(0, 255, 136, 0.3);
  }

  @media (max-width: 1024px) {
    .nav-content {
      gap: 2rem;
      margin-left: 2rem;
    }

    .nav-links {
      gap: 1.5rem;
    }
  }

  @media (max-width: 768px) {
    .nav-content {
      display: none;
    }

    .nav-links {
      margin-left: auto;
    }

    .nav-actions {
      gap: 0.5rem;
    }

    .icon-btn {
      width: 32px;
      height: 32px;
    }

    .logo span {
      font-size: 1.2rem;
    }
  }
</style>
