<script>
  const newTools = [
    {
      category: "AI Tooling",
      accent: "var(--accent-primary)",
      name: "MCP Server Tester",
      description: "Connect to any MCP server over stdio or SSE, browse available tools, fire calls, and inspect raw JSON responses.",
    },
    {
      category: "AI Tooling",
      accent: "var(--accent-primary)",
      name: "Chunking Playground",
      description: "Paste a document, pick a strategy (fixed / sentence / recursive / semantic), preview chunks with token counts and overlap.",
    },
    {
      category: "AI Tooling",
      accent: "var(--accent-primary)",
      name: "Prompt Version Manager",
      description: "Save named prompt versions locally, run them against a Claude model, and diff outputs side-by-side.",
    },
    {
      category: "AI Tooling",
      accent: "var(--accent-primary)",
      name: "llms.txt Generator",
      description: "From URLs, sitemaps, or raw content, generate structured llms.txt and llms-full.txt files for LLM context.",
      desktopOnly: true,
    },
    {
      category: "Network",
      accent: "var(--accent-blue)",
      name: "SSE Debugger",
      description: "Connect to any Server-Sent Events endpoint, watch the stream live, filter by event type, and inspect raw payloads.",
    },
    {
      category: "Network",
      accent: "var(--accent-blue)",
      name: "CORS Debugger",
      description: "Paste request and response headers, get a plain-English explanation of exactly why the CORS request failed and the exact fix.",
    },
    {
      category: "Network",
      accent: "var(--accent-blue)",
      name: "Webhook Inspector",
      description: "Spin up a local HTTP endpoint on any port, log incoming payloads in real time, and inspect headers and body.",
      desktopOnly: true,
    },
    {
      category: "Viewers",
      accent: "#a78bfa",
      name: "Mermaid Diagram Editor",
      description: "Live diagram editor supporting flowchart, sequence, ER, and gitgraph — export as SVG or PNG instantly.",
    },
  ];
</script>

<section class="section whats-new" id="whats-new">
  <div class="container">
    <div class="section-header">
      <div class="section-label">New in v2.0</div>
      <h2>What's New</h2>
      <p class="section-description">
        8 new tools shipped — AI dev utilities, network debuggers, and diagram editing.
      </p>
    </div>

    <div class="tools-grid">
      {#each newTools as tool, i}
        <div
          class="tool-card"
          style="animation-delay: {i * 0.07}s; --card-accent: {tool.accent};"
        >
          <div class="card-meta">
            <span class="category">{tool.category}</span>
            {#if tool.desktopOnly}
              <span class="desktop-tag">Desktop</span>
            {/if}
          </div>
          <h3 class="tool-name">{tool.name}</h3>
          <p class="tool-desc">{tool.description}</p>
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

  .whats-new {
    background: var(--bg-primary);
    border-bottom: 1px solid var(--border);
  }

  .container {
    max-width: 1400px;
    margin: 0 auto;
  }

  .section-header {
    text-align: center;
    margin-bottom: 4rem;
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
    max-width: 520px;
    margin: 0 auto;
  }

  .tools-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
  }

  .tool-card {
    background: var(--bg-secondary);
    border: 1px solid var(--border);
    border-left: 3px solid var(--card-accent);
    border-radius: 8px;
    padding: 1.5rem 1.75rem;
    opacity: 0;
    animation: fadeInUp 0.5s ease-out forwards;
    transition: background 0.2s, box-shadow 0.2s;
  }

  .tool-card:hover {
    background: var(--bg-tertiary);
    box-shadow: 0 4px 24px rgba(0, 0, 0, 0.25);
  }

  .card-meta {
    display: flex;
    align-items: center;
    gap: 0.6rem;
    margin-bottom: 0.75rem;
  }

  .category {
    font-family: "JetBrains Mono", monospace;
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--card-accent);
  }

  .desktop-tag {
    font-family: "JetBrains Mono", monospace;
    font-size: 0.68rem;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    color: var(--text-muted);
    border: 1px solid var(--border);
    padding: 0.1rem 0.45rem;
    border-radius: 3px;
  }

  .tool-name {
    font-family: "Syne", sans-serif;
    font-size: 1.1rem;
    font-weight: 700;
    margin-bottom: 0.55rem;
    color: var(--text-primary);
  }

  .tool-desc {
    font-size: 0.88rem;
    color: var(--text-secondary);
    line-height: 1.65;
  }

  @keyframes fadeInUp {
    from {
      opacity: 0;
      transform: translateY(16px);
    }
    to {
      opacity: 1;
      transform: translateY(0);
    }
  }

  @media (max-width: 768px) {
    .tools-grid {
      grid-template-columns: 1fr;
    }

    h2 {
      font-size: 2rem;
    }
  }
</style>
