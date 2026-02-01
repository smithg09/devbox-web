<script>
  let searchQuery = "";

  const categories = [
    {
      title: "Network",
      icon: "🌐",
      tools: ["GraphiQL", "REST Client", "HAR Viewer", "DNS Lookup"],
    },
    {
      title: "Security",
      icon: "🔐",
      tools: [
        "JWT Tools",
        "HMAC Generator",
        "Certificate Decoder",
        "Hashing Text",
        "SSH Keys",
      ],
    },
    {
      title: "Utilities",
      icon: "🛠️",
      tools: [
        "Timezone Converter",
        "Regex Tester",
        "Cron Parser",
        "Bundle Analyzer",
      ],
    },
    {
      title: "Generators",
      icon: "⚙️",
      tools: ["Password Generator", "QuickType", "Data Faker", "ID Generator"],
    },
    {
      title: "Viewers",
      icon: "👁️",
      tools: [
        "Markdown Preview",
        "Diff Viewer",
        "SVG Preview",
        "HTML/CSS Preview",
      ],
    },
    {
      title: "Formatters",
      icon: "✨",
      tools: [
        "JSON Formatter",
        "SQL Formatter",
        "JS/TS Minifier",
        "CSS Minifier",
      ],
    },
    {
      title: "Converters",
      icon: "🔄",
      tools: [
        "JSON ⇄ YAML",
        "URL Encoder",
        "Base64 Encoder",
        "Epoch Converter",
      ],
    },
    {
      title: "Coming Soon",
      icon: "🚀",
      tools: ["WebSocket Client", "Mock API Server", "Webhook Tester"],
    },
  ];

  $: filteredCategories = categories
    .map((category) => ({
      ...category,
      tools: category.tools.filter(
        (tool) =>
          tool.toLowerCase().includes(searchQuery.toLowerCase()) ||
          category.title.toLowerCase().includes(searchQuery.toLowerCase()),
      ),
    }))
    .filter((category) => category.tools.length > 0);
</script>

<section class="section tools-showcase" id="tools">
  <div class="container">
    <div class="section-header">
      <div class="section-label">Complete Toolkit</div>
      <h2>30+ Essential Developer Utilities</h2>
      <p class="section-description">
        Everything from JWT decoding to GraphQL testing, all in one place.
      </p>
      <div class="search-box">
        <span class="search-icon">🔍</span>
        <input
          type="text"
          placeholder="Search tools or categories..."
          bind:value={searchQuery}
          class="search-input"
        />
        {#if searchQuery}
          <button class="clear-search" on:click={() => (searchQuery = "")}
            >✕</button
          >
        {/if}
      </div>
    </div>

    <div class="tools-categories">
      {#each filteredCategories as category, i}
        <div class="category" style="animation-delay: {i * 0.1}s">
          <h3 class="category-title">
            <span class="category-icon">{category.icon}</span>
            {category.title}
          </h3>
          <div class="category-tools">
            {#each category.tools as tool}
              <div class="category-tool">{tool}</div>
            {/each}
          </div>
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

  .tools-showcase {
    background: var(--bg-secondary);
    border-top: 1px solid var(--border);
    border-bottom: 1px solid var(--border);
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
    margin: 0 auto 2rem auto;
  }

  .search-box {
    position: relative;
    max-width: 500px;
    margin: 0 auto;
  }

  .search-icon {
    position: absolute;
    left: 1rem;
    top: 50%;
    transform: translateY(-50%);
    font-size: 1.2rem;
    opacity: 0.5;
  }

  .search-input {
    width: 100%;
    padding: 0.9rem 3rem 0.9rem 3rem;
    background: var(--bg-primary);
    border: 1px solid var(--border);
    border-radius: 8px;
    color: var(--text-primary);
    font-size: 1rem;
    font-family: "JetBrains Mono", monospace;
    transition: all 0.2s;
  }

  .search-input:focus {
    outline: none;
    border-color: var(--accent-primary);
    box-shadow: 0 0 0 3px rgba(0, 255, 136, 0.1);
  }

  .search-input::placeholder {
    color: var(--text-muted);
  }

  .clear-search {
    position: absolute;
    right: 1rem;
    top: 50%;
    transform: translateY(-50%);
    background: transparent;
    border: none;
    color: var(--text-muted);
    font-size: 1.2rem;
    cursor: pointer;
    padding: 0.2rem 0.5rem;
    transition: color 0.2s;
  }

  .clear-search:hover {
    color: var(--accent-primary);
  }

  .tools-categories {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 3rem;
  }

  .category {
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

  .category-title {
    font-family: "Syne", sans-serif;
    font-size: 1.2rem;
    font-weight: 700;
    margin-bottom: 1.5rem;
    color: var(--accent-primary);
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .category-icon {
    font-size: 1.5rem;
  }

  .category-tools {
    display: flex;
    flex-direction: column;
    gap: 0.8rem;
  }

  .category-tool {
    color: var(--text-secondary);
    font-size: 0.9rem;
    padding: 0.5rem 0;
    border-bottom: 1px solid var(--border);
    transition: color 0.2s;
  }

  .category-tool:hover {
    color: var(--accent-primary);
  }

  @media (max-width: 768px) {
    .tools-categories {
      grid-template-columns: 1fr;
    }

    h2 {
      font-size: 2rem;
    }
  }
</style>
