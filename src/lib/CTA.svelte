<script>
  const downloads = [
    {
      platform: "macOS (Apple Silicon)",
      size: "v1.1.0 • ~45MB",
      url: "https://github.com/smithg09/devbox/releases/download/devbox-v1.1.0/Devbox_1.1.0_aarch64.dmg",
      logo: "apple",
    },
    {
      platform: "macOS (Intel)",
      size: "v1.1.0 • ~47MB",
      url: "https://github.com/smithg09/devbox/releases/download/devbox-v1.1.0/Devbox_1.1.0_x64.dmg",
      logo: "apple",
    },
    {
      platform: "Windows (x64)",
      size: "v1.1.0 • ~42MB",
      url: "https://github.com/smithg09/devbox/releases/download/devbox-v1.1.0/Devbox_1.1.0_x64-setup.exe",
      logo: "windows",
    },
  ];
</script>

<section class="section" id="download">
  <div class="container">
    <div class="cta-section">
      <h2>Ready to boost your productivity?</h2>
      <p>
        Download DevBox now and get all your developer tools in one place. No
        sign-up required.
      </p>

      <div class="download-options">
        {#each downloads as download}
          <a href={download.url} class="download-btn">
            <span class="download-icon">
              {#if download.logo === "apple"}
                <svg
                  viewBox="0 0 24 24"
                  fill="currentColor"
                  width="24"
                  height="24"
                >
                  <path
                    d="M17.05 20.28c-.98.95-2.05.8-3.08.35-1.09-.46-2.09-.48-3.24 0-1.44.62-2.2.44-3.06-.35C2.79 15.25 3.51 7.59 9.05 7.31c1.35.07 2.29.74 3.08.8 1.18-.24 2.31-.93 3.57-.84 1.51.12 2.65.72 3.4 1.8-3.12 1.87-2.38 5.98.48 7.13-.57 1.5-1.31 2.99-2.54 4.09l.01-.01zM12.03 7.25c-.15-2.23 1.66-4.07 3.74-4.25.29 2.58-2.34 4.5-3.74 4.25z"
                  />
                </svg>
              {:else if download.logo === "windows"}
                <img
                  src="/windows-logo.png"
                  alt="Windows"
                  width="48"
                  height="24"
                />
              {/if}
            </span>
            <div class="download-info">
              <span class="download-platform">{download.platform}</span>
              <span class="download-size">{download.size}</span>
            </div>
          </a>
        {/each}
      </div>

      <p class="other-platforms">
        Other platforms available on <a
          href="https://github.com/smithg09/devbox/releases">GitHub Releases</a
        >
      </p>
    </div>
  </div>
</section>

<style>
  .section {
    padding: 8rem 2rem;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
  }

  .cta-section {
    background: linear-gradient(
      135deg,
      var(--bg-tertiary),
      var(--bg-secondary)
    );
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 5rem 3rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }

  .cta-section::before {
    content: "";
    position: absolute;
    width: 600px;
    height: 600px;
    background: radial-gradient(circle, rgba(0, 149, 255, 0.05), transparent);
    filter: blur(50px);
    top: -300px;
    left: 50%;
    transform: translateX(-50%);
  }

  h2 {
    font-family: "Syne", sans-serif;
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 1.5rem;
    position: relative;
  }

  p {
    font-size: 1.2rem;
    color: var(--text-secondary);
    margin-bottom: 2.5rem;
    max-width: 600px;
    margin-left: auto;
    margin-right: auto;
    position: relative;
  }

  .download-options {
    display: flex;
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
    position: relative;
    margin-bottom: 2rem;
  }

  .download-btn {
    background: var(--bg-secondary);
    border: 1px solid var(--border);
    padding: 1rem 2rem;
    border-radius: 8px;
    display: flex;
    align-items: center;
    gap: 0.8rem;
    text-decoration: none;
    color: var(--text-primary);
    transition: all 0.2s;
    font-weight: 600;
  }

  .download-btn:hover {
    border-color: var(--accent-primary);
    transform: translateY(-2px);
    box-shadow: 0 10px 30px rgba(0, 149, 255, 0.1);
  }

  .download-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 32px;
    height: 32px;
  }

  .download-icon svg {
    width: 24px;
    height: 24px;
  }

  .download-info {
    text-align: left;
  }

  .download-platform {
    font-size: 0.9rem;
    display: block;
  }

  .download-size {
    font-size: 0.75rem;
    color: var(--text-muted);
  }

  .other-platforms {
    font-size: 0.9rem;
    color: var(--text-muted);
  }

  .other-platforms a {
    color: var(--accent-primary);
    text-decoration: none;
  }

  .other-platforms a:hover {
    text-decoration: underline;
  }

  @media (max-width: 768px) {
    .section {
      padding: 4rem 1.5rem;
    }

    .cta-section {
      padding: 3rem 1.5rem;
    }

    h2 {
      font-size: 2rem;
      line-height: 1.2;
    }

    p {
      font-size: 1rem;
    }

    .download-options {
      flex-direction: column;
      width: 100%;
    }

    .download-btn {
      width: 100%;
      justify-content: flex-start;
    }
  }

  @media (max-width: 480px) {
    .cta-section {
      padding: 2.5rem 1.5rem;
    }

    h2 {
      font-size: 1.75rem;
    }

    .download-btn {
      padding: 0.9rem 1.5rem;
    }
  }
</style>
