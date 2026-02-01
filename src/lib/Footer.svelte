<script>
  const footerLinks = {
    product: [
      { name: "Features", href: "#features" },
      { name: "Tools", href: "#tools" },
      { name: "Download", href: "#download" },
      { name: "Releases", href: "https://github.com/smithg09/devbox/releases" },
    ],
    resources: [
      {
        name: "Web Version",
        href: "https://devbox-app.smithgajjar.dev/",
      },
      { name: "GitHub", href: "https://github.com/smithg09/devbox" },
      {
        name: "Report Issue",
        href: "https://github.com/smithg09/devbox/issues",
      },
      {
        name: "License",
        href: "https://github.com/smithg09/devbox/blob/develop/LICENSE",
      },
    ],
    community: [
      { name: "Issues", href: "https://github.com/smithg09/devbox/issues" },
      {
        name: "Pull Requests",
        href: "https://github.com/smithg09/devbox/pulls",
      },
      {
        name: "Discussions",
        href: "https://github.com/smithg09/devbox/discussions",
      },
      {
        name: "Contributing",
        href: "https://github.com/smithg09/devbox/blob/develop/README.md#contributing",
      },
    ],
  };
</script>

<footer>
  <div class="container">
    <div>
      <div class="footer-brand">DevBox</div>
      <p class="footer-description">
        The developer's Swiss Army knife. All your everyday tools in one fast,
        offline-first desktop app.
      </p>
    </div>

    <div class="footer-column">
      <h4>Product</h4>
      <ul class="footer-links">
        {#each footerLinks.product as link}
          <li><a href={link.href}>{link.name}</a></li>
        {/each}
      </ul>
    </div>

    <div class="footer-column">
      <h4>Resources</h4>
      <ul class="footer-links">
        {#each footerLinks.resources as link}
          <li><a href={link.href}>{link.name}</a></li>
        {/each}
      </ul>
    </div>

    <div class="footer-column">
      <h4>Community</h4>
      <ul class="footer-links">
        {#each footerLinks.community as link}
          <li><a href={link.href}>{link.name}</a></li>
        {/each}
      </ul>
    </div>
  </div>

  <div class="container">
    <div class="footer-bottom">
      <div>© 2026 DevBox. MIT License. Built with ❤️ for developers.</div>
      <div class="social-links">
        <a href="https://github.com/smithg09/devbox" title="GitHub">Github</a>
      </div>
    </div>
  </div>
</footer>

<style>
  footer {
    border-top: 1px solid var(--border);
    padding: 4rem 2rem 2rem;
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
  }

  .container:first-child {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 4rem;
    margin-bottom: 3rem;
  }

  .footer-brand {
    font-family: "Syne", sans-serif;
    font-size: 1.5rem;
    font-weight: 800;
    margin-bottom: 1rem;
  }

  .footer-description {
    color: var(--text-muted);
    font-size: 0.9rem;
    line-height: 1.7;
  }

  .footer-column h4 {
    font-family: "Syne", sans-serif;
    font-size: 1rem;
    font-weight: 700;
    margin-bottom: 1.5rem;
    color: var(--accent-primary);
  }

  .footer-links {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 0.8rem;
  }

  .footer-links a {
    color: var(--text-muted);
    text-decoration: none;
    font-size: 0.9rem;
    transition: color 0.2s;
  }

  .footer-links a:hover {
    color: var(--accent-primary);
  }

  .footer-bottom {
    border-top: 1px solid var(--border);
    padding-top: 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: var(--text-muted);
    font-size: 0.85rem;
  }

  .social-links {
    display: flex;
    gap: 1.5rem;
  }

  .social-links a {
    color: var(--text-muted);
    font-size: 1.2rem;
    transition: color 0.2s;
    text-decoration: none;
  }

  .social-links a:hover {
    color: var(--accent-primary);
  }

  @media (max-width: 1024px) {
    .container:first-child {
      grid-template-columns: 1fr 1fr;
      gap: 2rem;
    }
  }

  @media (max-width: 768px) {
    .container:first-child {
      grid-template-columns: 1fr;
    }

    .footer-bottom {
      flex-direction: column;
      gap: 1rem;
      text-align: center;
    }
  }
</style>
