---
layout: default
title: Community Pulse | Boston Eats
permalink: /community/
---

<style>
  :root {
    --bg: #0f1220;
    --card: #121a31;
    --text: #f4f6fd;
    --muted: #b8bfd8;
    --line: #2b3356;
    --accent: #6ee7ff;
    --accent-2: #9b8cff;
    --warm: #ff9a6e;
  }

  * { box-sizing: border-box; }

  body {
    margin: 0;
    font-family: Inter, "Avenir Next", Avenir, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    background: linear-gradient(180deg, #111834, var(--bg));
    color: var(--text);
  }

  .cp-wrap {
    max-width: 1000px;
    margin: 0 auto;
    padding: 1rem;
  }

  .top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 1rem;
    flex-wrap: wrap;
    margin-bottom: 0.9rem;
  }

  .top a {
    color: var(--accent);
    text-decoration: none;
    font-weight: 700;
  }

  .lead {
    border: 1px solid var(--line);
    border-radius: 16px;
    background: rgba(255, 255, 255, 0.03);
    padding: 1rem;
    margin-bottom: 1rem;
  }

  .lead h1 {
    margin: 0 0 0.45rem;
    font-size: clamp(1.7rem, 4.5vw, 2.8rem);
  }

  .lead p {
    margin: 0;
    color: var(--muted);
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    gap: 0.85rem;
  }

  .card {
    grid-column: span 12;
    background: var(--card);
    border: 1px solid var(--line);
    border-radius: 14px;
    padding: 0.95rem;
  }

  .tag {
    display: inline-block;
    border-radius: 999px;
    padding: 0.25rem 0.62rem;
    font-size: 0.78rem;
    font-weight: 700;
    margin-bottom: 0.45rem;
  }

  .event { background: rgba(110, 231, 255, 0.16); color: var(--accent); }
  .news { background: rgba(155, 140, 255, 0.18); color: #d8d1ff; }
  .popup { background: rgba(255, 154, 110, 0.16); color: #ffc0a7; }

  .card h2 {
    margin: 0 0 0.35rem;
    font-size: 1.1rem;
  }

  .meta {
    color: var(--muted);
    font-size: 0.86rem;
    margin-bottom: 0.4rem;
  }

  .card p {
    margin: 0;
    color: var(--muted);
  }

  .submit {
    margin-top: 1rem;
    border: 1px dashed var(--line);
    border-radius: 14px;
    padding: 0.95rem;
    background: rgba(0, 0, 0, 0.12);
  }

  .submit a {
    color: var(--text);
    font-weight: 700;
  }

  @media (min-width: 760px) {
    .half {
      grid-column: span 6;
    }
  }
</style>

<main class="cp-wrap">
  <div class="top">
    <strong>Boston Eats Community Pulse</strong>
    <a href="/">Back to Home</a>
  </div>

  <section class="lead">
    <h1>Food events, local news, and chef popups.</h1>
    <p>
      Your one-stop page for what is happening in Boston's community food scene this week.
    </p>
  </section>

  <section class="grid">
    <article class="card half">
      <span class="tag event">Event</span>
      <h2>Night Market at Seaport Commons</h2>
      <div class="meta">Saturday, 6 PM - 10 PM</div>
      <p>Street food vendors, student DJ sets, and small-batch dessert makers from across Greater Boston.</p>
    </article>

    <article class="card half">
      <span class="tag news">News</span>
      <h2>City Grant Opens for Small Food Startups</h2>
      <div class="meta">Published this week</div>
      <p>Boston announced a micro-grant program supporting neighborhood kitchens, carts, and first-time restaurant owners.</p>
    </article>

    <article class="card half">
      <span class="tag popup">Popup</span>
      <h2>Roxbury Chef Collab Dinner</h2>
      <div class="meta">Friday, 7 PM (limited seats)</div>
      <p>A five-course collab featuring Haitian, Southern comfort, and Afro-Caribbean flavors.</p>
    </article>

    <article class="card half">
      <span class="tag event">Event</span>
      <h2>Cambridge Dumpling Workshop</h2>
      <div class="meta">Sunday, 1 PM</div>
      <p>Hands-on class with local cooks focused on family dumpling techniques from multiple regions.</p>
    </article>
  </section>

  <section class="submit">
    Know about a local event, popup, or story? Send details to <a href="mailto:hello@bostoneats.com">hello@bostoneats.com</a> and we may feature it.
  </section>
</main>
