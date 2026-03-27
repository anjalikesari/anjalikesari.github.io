---
layout: default
title: Boston Eats
---

<style>
  :root {
    --bg: #0f1220;
    --bg-soft: #1a1f35;
    --card: #11162b;
    --text: #f6f7fb;
    --muted: #b8bfd8;
    --accent: #6ee7ff;
    --accent-2: #9b8cff;
    --warm: #ff9a6e;
    --line: #2c3352;
  }

  * {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    font-family: Inter, "Avenir Next", Avenir, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    color: var(--text);
    background: radial-gradient(circle at 20% -10%, #2b386f 0%, var(--bg) 45%);
    line-height: 1.5;
  }

  .be-wrap {
    max-width: 1100px;
    margin: 0 auto;
    padding: 1rem;
  }

  .be-nav {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
    padding: 0.75rem 0;
  }

  .be-brand {
    font-weight: 800;
    letter-spacing: 0.2px;
    font-size: 1.05rem;
  }

  .be-brand span {
    color: var(--accent);
  }

  .be-links {
    display: flex;
    gap: 0.8rem;
    flex-wrap: wrap;
  }

  .be-links a {
    text-decoration: none;
    color: var(--text);
    font-weight: 600;
    font-size: 0.95rem;
    border: 1px solid var(--line);
    padding: 0.45rem 0.7rem;
    border-radius: 999px;
    transition: 0.2s ease;
  }

  .be-links a:hover {
    border-color: var(--accent);
    color: var(--accent);
  }

  .hero {
    margin-top: 1rem;
    background: linear-gradient(140deg, rgba(110, 231, 255, 0.14), rgba(155, 140, 255, 0.18));
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 22px;
    padding: 1.4rem;
  }

  .hero h1 {
    margin: 0 0 0.6rem;
    font-size: clamp(1.9rem, 4.7vw, 3.5rem);
    line-height: 1.05;
  }

  .hero p {
    margin: 0;
    color: var(--muted);
    max-width: 67ch;
  }

  .pill-row {
    margin-top: 1rem;
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
  }

  .pill {
    background: rgba(255, 255, 255, 0.08);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: 999px;
    padding: 0.35rem 0.8rem;
    font-size: 0.83rem;
  }

  .section {
    margin-top: 1.4rem;
  }

  .section h2 {
    margin: 0 0 0.7rem;
    font-size: 1.5rem;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 0.9rem;
  }

  .card {
    grid-column: span 12;
    background: var(--card);
    border: 1px solid var(--line);
    border-radius: 16px;
    padding: 1rem;
  }

  .card h3 {
    margin: 0 0 0.45rem;
    font-size: 1.05rem;
  }

  .meta {
    font-size: 0.85rem;
    color: var(--accent);
    margin-bottom: 0.45rem;
  }

  .card p {
    margin: 0;
    color: var(--muted);
  }

  .culture {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 0.6rem;
  }

  .culture strong {
    font-size: 0.95rem;
  }

  .culture small {
    color: var(--muted);
  }

  .cta {
    margin-top: 1.5rem;
    display: flex;
    flex-wrap: wrap;
    gap: 0.7rem;
  }

  .btn {
    text-decoration: none;
    padding: 0.65rem 1rem;
    border-radius: 10px;
    font-weight: 700;
    font-size: 0.93rem;
    border: 1px solid transparent;
    display: inline-block;
  }

  .btn-main {
    color: #07121f;
    background: linear-gradient(120deg, var(--accent), #8ef0ff);
  }

  .btn-alt {
    color: var(--text);
    border-color: var(--line);
    background: transparent;
  }

  .note {
    margin-top: 1.5rem;
    color: var(--muted);
    font-size: 0.88rem;
  }

  @media (min-width: 720px) {
    .card-third {
      grid-column: span 4;
    }

    .card-half {
      grid-column: span 6;
    }
  }
</style>

<main class="be-wrap">
  <nav class="be-nav">
    <div class="be-brand">Boston <span>Eats</span></div>
    <div class="be-links">
      <a href="/">Home</a>
      <a href="/community">Community Pulse</a>
    </div>
  </nav>

  <section class="hero">
    <h1>Find Boston's hidden gem food scene.</h1>
    <p>
      Boston Eats is your simple, cool guide to under-the-radar restaurants and the cultures that shape every block. Discover real spots, local stories, and community flavor.
    </p>
    <div class="pill-row">
      <span class="pill">Mobile Friendly</span>
      <span class="pill">Hidden Gems</span>
      <span class="pill">Culture-First</span>
      <span class="pill">Community Powered</span>
    </div>
  </section>

  <section class="section">
    <h2>Hidden Gems Right Now</h2>
    <div class="grid">
      <article class="card card-third">
        <div class="meta">Dorchester</div>
        <h3>Saigon Alley Noodle House</h3>
        <p>Low-key family kitchen serving late-night pho and rotating regional specials from southern Vietnam.</p>
      </article>
      <article class="card card-third">
        <div class="meta">East Boston</div>
        <h3>Abuela's Corner Comedor</h3>
        <p>Home-style Ecuadorian and Dominican plates with hand-pressed sides and weekend street juice pop-up.</p>
      </article>
      <article class="card card-third">
        <div class="meta">Allston</div>
        <h3>Tiger Wok Basement</h3>
        <p>Beloved after-hours stop for fiery hand-pulled noodles, dumplings, and student-priced combo bowls.</p>
      </article>
    </div>
  </section>

  <section class="section">
    <h2>Explore Cultures Through Food</h2>
    <div class="grid">
      <article class="card card-half">
        <div class="culture">
          <div>
            <strong>Haitian Boston</strong><br />
            <small>Mattapan and Hyde Park</small>
          </div>
          <span class="pill">Griot • Pikliz • Soup Joumou</span>
        </div>
      </article>
      <article class="card card-half">
        <div class="culture">
          <div>
            <strong>Brazilian Boston</strong><br />
            <small>Somerville and Framingham links</small>
          </div>
          <span class="pill">Pao de queijo • Churrasco</span>
        </div>
      </article>
      <article class="card card-half">
        <div class="culture">
          <div>
            <strong>Cape Verdean Boston</strong><br />
            <small>Dorchester and Roxbury</small>
          </div>
          <span class="pill">Cachupa • Bolo • Cuscuz</span>
        </div>
      </article>
      <article class="card card-half">
        <div class="culture">
          <div>
            <strong>East African Boston</strong><br />
            <small>Jamaica Plain and Roxbury</small>
          </div>
          <span class="pill">Injera • Tibs • Spiced tea</span>
        </div>
      </article>
    </div>
  </section>

  <section class="section">
    <h2>Stay Plugged In</h2>
    <div class="card">
      <p>
        Looking for food festivals, neighborhood markets, collab dinners, and chef pop-ups? Check out <a href="/community">Community Pulse</a> for events and news updates.
      </p>
      <div class="cta">
        <a class="btn btn-main" href="/community">See Events and Popups</a>
        <a class="btn btn-alt" href="mailto:hello@bostoneats.com">Submit a Hidden Gem</a>
      </div>
    </div>
  </section>

  <p class="note">Built for food explorers. New spots and stories added weekly.</p>
</main>
