---
layout: default
title: Boston Eats
---

<section class="be-hero">
  <h1>Hidden gem food, plus the cultures behind every bite.</h1>
  <p>
    Discover local favorites by vibe, cuisine, price, and area.
  </p>
  <div class="be-pill-row" aria-label="Highlights">
    <span class="be-pill">Hidden gem score</span>
    <span class="be-pill">Quick filters</span>
    <span class="be-pill">Click for details</span>
  </div>
</section>

<section class="be-section">
  <h2>Featured Restaurants</h2>
  <div class="be-grid" id="featuredGrid" aria-label="Featured restaurant cards">
    {% for r in site.data.restaurants %}
      {% if r.featured == true %}
        <article class="be-card be-card-third r-card js-open-restaurant" data-restaurant-id="{{ r.id }}" tabindex="0" role="button"
          aria-label="Open details for {{ r.name }}">
          <div class="r-card__top">
            <div>
              <p class="r-card__meta">{{ r.area }}</p>
              <h3 class="r-card__title">{{ r.name }}</h3>
            </div>
            <div class="r-score" aria-label="Hidden gem score">
              <div class="r-score__label">Hidden Gem</div>
              <div class="r-score__value">{{ r.hiddenGemScore }}/100</div>
            </div>
          </div>

          <div class="r-miniRatings" aria-label="Ratings summary">
            <span class="r-miniRatings__pill">Overall {{ r.ratings.overall }}/5</span>
            <span class="r-miniRatings__pill">{{ r.price }}</span>
          </div>

          <div class="r-tag-row" aria-label="Restaurant tags">
            {% for t in r.tags limit: 3 %}
              <span class="r-tag">{{ t }}</span>
            {% endfor %}
          </div>
        </article>
      {% endif %}
    {% endfor %}
  </div>
</section>

<section class="be-section">
  <h2>Search & Filter</h2>
  <div class="filters" role="region" aria-label="Restaurant filters">
    <div class="filters__grid">
      <div class="filters__field filters__field--search">
        <label for="searchText">Search</label>
        <input id="searchText" type="text" placeholder="Try: dumplings, date night, pho..." autocomplete="off" />
      </div>

      <div class="filters__field filters__field--price">
        <label for="priceSelect">Price</label>
        <select id="priceSelect">
          <option value="__any__">Any</option>
          <option value="$">$</option>
          <option value="$$">$$</option>
          <option value="$$$">$$$</option>
        </select>
      </div>

      <div class="filters__field filters__field--cuisine">
        <label for="cuisineSelect">Cuisine</label>
        <select id="cuisineSelect">
          <option value="__any__">Any</option>
        </select>
      </div>

      <div class="filters__field filters__field--vibe">
        <label for="vibeSelect">Vibe</label>
        <select id="vibeSelect">
          <option value="__any__">Any</option>
        </select>
      </div>

      <div class="filters__field filters__field--area">
        <label for="areaSelect">Area</label>
        <select id="areaSelect">
          <option value="__any__">Any</option>
        </select>
      </div>

      <div class="filters__field filters__field--score">
        <label for="scoreMin">Min hidden gem score: <span id="scoreMinLabel">0</span></label>
        <input id="scoreMin" type="range" min="0" max="100" step="1" value="0" />
      </div>

      <div class="filters__field filters__field--sort">
        <label for="sortSelect">Sort</label>
        <select id="sortSelect">
          <option value="recommended">Recommended</option>
          <option value="score_desc">Highest hidden gem score</option>
          <option value="rating_desc">Top rated</option>
          <option value="price_cheap">Most affordable</option>
        </select>
      </div>

      <div class="filters__field filters__field--actions filters__actions">
        <button class="btn btn--primary" id="clearFilters" type="button">Clear</button>
        <span class="results__status" id="resultsStatus" aria-live="polite"></span>
      </div>
    </div>
  </div>

  <div class="results">
    <div class="be-grid" id="resultsGrid" aria-label="Search results"></div>
  </div>
</section>

<!-- Restaurant modal -->
<div id="beModal" class="be-modal" role="dialog" aria-modal="true" aria-labelledby="beModalTitle" hidden>
  <div class="be-modal__header">
    <div>
      <h3 id="beModalTitle" class="be-modal__title">Restaurant</h3>
      <div id="beModalSubtitle" class="r-card__meta">Area</div>
    </div>
    <button class="be-modal__close" id="beModalClose" type="button" aria-label="Close details">Close</button>
  </div>

  <div class="be-modal__body">
    <div class="modalGrid">
      <div class="modalCol--left">
        <div class="be-kv" aria-label="Hidden gem score">
          <div class="be-kv__row">
            <div class="be-kv__k">Hidden Gem Score</div>
            <div class="be-kv__v" id="beModalGemValue">0</div>
          </div>
          <div class="be-kv__row" style="padding-top: 0.2rem;">
            <div class="be-kv__k">Gauge</div>
            <div class="be-kv__v">
              <div class="bar" aria-hidden="true"><span id="beModalGemBar" style="width: 0%"></span></div>
            </div>
          </div>
        </div>

        <div class="be-section" style="margin-top: 1rem;">
          <div class="r-tag-row" id="beModalTags" aria-label="Tags"></div>
        </div>

        <div class="be-section" style="margin-top: 1rem;">
          <div class="muted" style="font-size: 0.95rem; margin-bottom: 0.5rem; font-weight: 950;">Short description</div>
          <div id="beModalDesc" class="muted" style="color: var(--muted); font-weight: 800; line-height: 1.6;"></div>
        </div>
      </div>

      <div class="modalCol--right">
        <div class="be-section" style="margin-top: 0;">
          <div class="muted" style="font-size: 0.95rem; margin-bottom: 0.5rem; font-weight: 950;">Ratings</div>
          <div class="r-miniRatings" id="beModalRatingsPills"></div>
        </div>

        <div class="be-section" style="margin-top: 1rem;">
          <div class="muted" style="font-size: 0.95rem; margin-bottom: 0.5rem; font-weight: 950;">Best bites</div>
          <div class="dishes" id="beModalDishes"></div>
        </div>
      </div>
    </div>
  </div>
</div>

<script id="restaurants-data" type="application/json">
  {{ site.data.restaurants | jsonify }}
</script>

<script>
  (function () {
    const restaurants = JSON.parse(document.getElementById('restaurants-data').textContent || '[]');
    const byId = new Map(restaurants.map((r) => [r.id, r]));

    const featuredGrid = document.getElementById('featuredGrid');
    const resultsGrid = document.getElementById('resultsGrid');
    const resultsStatus = document.getElementById('resultsStatus');

    const searchText = document.getElementById('searchText');
    const priceSelect = document.getElementById('priceSelect');
    const cuisineSelect = document.getElementById('cuisineSelect');
    const vibeSelect = document.getElementById('vibeSelect');
    const areaSelect = document.getElementById('areaSelect');
    const scoreMin = document.getElementById('scoreMin');
    const scoreMinLabel = document.getElementById('scoreMinLabel');
    const sortSelect = document.getElementById('sortSelect');
    const clearFilters = document.getElementById('clearFilters');

    // Modal elements
    const modal = document.getElementById('beModal');
    const modalClose = document.getElementById('beModalClose');
    const modalTitle = document.getElementById('beModalTitle');
    const modalSubtitle = document.getElementById('beModalSubtitle');
    const modalGemValue = document.getElementById('beModalGemValue');
    const modalGemBar = document.getElementById('beModalGemBar');
    const modalTags = document.getElementById('beModalTags');
    const modalDesc = document.getElementById('beModalDesc');
    const modalRatingsPills = document.getElementById('beModalRatingsPills');

    const modalDishes = document.getElementById('beModalDishes');

    function unique(arr) {
      return Array.from(new Set(arr)).filter(Boolean);
    }

    function populateSelect(selectEl, values) {
      const keepFirst = selectEl.querySelector('option[value="__any__"]') || selectEl.options[0];
      selectEl.innerHTML = '';
      if (keepFirst) selectEl.appendChild(keepFirst);

      values.sort((a, b) => a.localeCompare(b)).forEach((v) => {
        const opt = document.createElement('option');
        opt.value = v;
        opt.textContent = v;
        selectEl.appendChild(opt);
      });
    }

    // Populate cuisine/vibe/area selects from data.
    const cuisines = unique(restaurants.flatMap((r) => r.cuisine || []));
    const vibes = unique(restaurants.flatMap((r) => r.vibe || []));
    const areas = unique(restaurants.map((r) => r.area));
    populateSelect(cuisineSelect, cuisines);
    populateSelect(vibeSelect, vibes);
    populateSelect(areaSelect, areas);

    function scoreMatches(r) {
      return (r.hiddenGemScore || 0) >= Number(scoreMin.value || 0);
    }

    function isMatch(r) {
      const t = (searchText.value || '').trim().toLowerCase();
      const hasText = !t
        ? true
        : [
            r.name,
            r.shortDescription,
            (r.tags || []).join(' '),
            (r.cuisine || []).join(' '),
            (r.vibe || []).join(' '),
            r.area,
          ]
            .filter(Boolean)
            .join(' ')
            .toLowerCase()
            .includes(t);

      const priceOk = priceSelect.value === '__any__' ? true : r.price === priceSelect.value;
      const cuisineOk = cuisineSelect.value === '__any__' ? true : (r.cuisine || []).includes(cuisineSelect.value);
      const vibeOk = vibeSelect.value === '__any__' ? true : (r.vibe || []).includes(vibeSelect.value);
      const areaOk = areaSelect.value === '__any__' ? true : r.area === areaSelect.value;
      const gemOk = scoreMatches(r);
      return hasText && priceOk && cuisineOk && vibeOk && areaOk && gemOk;
    }

    function priceRank(r) {
      // Lower is cheaper.
      const p = r.price || '';
      if (p === '$') return 1;
      if (p === '$$') return 2;
      if (p === '$$$') return 3;
      return 99;
    }

    function sortRestaurants(list) {
      const key = sortSelect.value;
      const copy = list.slice();

      if (key === 'score_desc') copy.sort((a, b) => (b.hiddenGemScore || 0) - (a.hiddenGemScore || 0));
      else if (key === 'rating_desc') copy.sort((a, b) => (b.ratings?.overall || 0) - (a.ratings?.overall || 0));
      else if (key === 'price_cheap') copy.sort((a, b) => priceRank(a) - priceRank(b));
      else {
        // "Recommended": hidden gem score wins, with a bit of overall rating.
        copy.sort((a, b) => {
          const aScore = (a.hiddenGemScore || 0) * 0.8 + (a.ratings?.overall || 0) * 10;
          const bScore = (b.hiddenGemScore || 0) * 0.8 + (b.ratings?.overall || 0) * 10;
          return bScore - aScore;
        });
      }
      return copy;
    }

    function escapeHtml(str) {
      return String(str)
        .replaceAll('&', '&amp;')
        .replaceAll('<', '&lt;')
        .replaceAll('>', '&gt;')
        .replaceAll('"', '&quot;')
        .replaceAll("'", '&#039;');
    }

    function createRestaurantCard(r) {
      const tags = (r.tags || []).slice(0, 3)
        .map((t) => `<span class="r-tag">${escapeHtml(t)}</span>`)
        .join('');

      const miniPills = [
        `Overall ${(r.ratings?.overall || 0).toFixed(1)}/5`,
        `${escapeHtml(r.price || '')}`
      ]
        .map((p) => `<span class="r-miniRatings__pill">${escapeHtml(p)}</span>`)
        .join('');

      return `
        <article class="be-card be-card-third r-card js-open-restaurant" data-restaurant-id="${escapeHtml(r.id)}" tabindex="0" role="button">
          <div class="r-card__top">
            <div>
              <p class="r-card__meta">${escapeHtml(r.area || '')}</p>
              <h3 class="r-card__title">${escapeHtml(r.name || '')}</h3>
            </div>
            <div class="r-score">
              <div class="r-score__label">Hidden Gem</div>
              <div class="r-score__value">${escapeHtml(String(r.hiddenGemScore || 0))}/100</div>
            </div>
          </div>
          <div class="r-miniRatings" aria-label="Ratings summary">${miniPills}</div>
          <div class="r-tag-row" aria-label="Restaurant tags">${tags}</div>
        </article>
      `;
    }

    function renderResults() {
      const matching = restaurants.filter(isMatch);
      const sorted = sortRestaurants(matching);

      if (!sorted.length) {
        resultsGrid.innerHTML = `<div class="be-card" style="grid-column: span 12;">No matches. Try clearing filters or searching fewer keywords.</div>`;
        resultsStatus.textContent = '0 results';
        return;
      }

      resultsGrid.innerHTML = sorted
        .map((r) => createRestaurantCard(r))
        .join('');

      resultsStatus.textContent = `${sorted.length} result${sorted.length === 1 ? '' : 's'}`;
    }

    function openModal(restaurantId, anchorX, anchorY) {
      const r = byId.get(restaurantId);
      if (!r) return;

      modalTitle.textContent = r.name || 'Restaurant';
      modalSubtitle.textContent = r.area ? `${r.area} • ${r.price || ''}` : r.price || '';
      modalGemValue.textContent = `${r.hiddenGemScore || 0}/100`;
      const gemPct = Math.max(0, Math.min(100, Number(r.hiddenGemScore || 0)));
      modalGemBar.style.width = gemPct + '%';

      // Tags
      modalTags.innerHTML = (r.tags || []).map((t) => `<span class="r-tag">${escapeHtml(t)}</span>`).join('');

      // Description
      modalDesc.textContent = r.shortDescription || '';

      // Ratings pills
      const overall = r.ratings?.overall || 0;
      const reviewCount = r.ratings?.reviewCount || 0;
      modalRatingsPills.innerHTML = [
        `<span class="r-miniRatings__pill">Overall ${Number(overall).toFixed(1)}/5</span>`,
        `<span class="r-miniRatings__pill">${escapeHtml(String(reviewCount))} reviews</span>`,
        `<span class="r-miniRatings__pill">${escapeHtml(r.price || '')}</span>`
      ].join('');

      // Dishes
      modalDishes.innerHTML = (r.recommendedDishes || []).slice(0, 3)
        .map((d) => `<span class="r-miniRatings__pill">${escapeHtml(d)}</span>`)
        .join('');

      modal.hidden = false;
      modal.style.left = '12px';
      modal.style.top = '12px';

      const modalRect = modal.getBoundingClientRect();
      let left = (anchorX || 20) + 14;
      let top = (anchorY || 20) + 14;
      const maxLeft = window.innerWidth - modalRect.width - 12;
      if (left > maxLeft) left = Math.max(12, maxLeft);
      if (top + modalRect.height > window.innerHeight - 12) top = (anchorY || 20) - modalRect.height - 14;
      if (top < 12) top = 12;
      modal.style.left = left + 'px';
      modal.style.top = top + 'px';

      // Focus close for accessibility.
      modalClose.focus();
    }

    function closeModal() {
      modal.hidden = true;
    }

    // Open from featured + results (event delegation).
    function attachOpenHandlers(rootEl) {
      rootEl.addEventListener('click', (e) => {
        const card = e.target.closest('.js-open-restaurant');
        if (!card) return;
        openModal(card.getAttribute('data-restaurant-id'), e.clientX, e.clientY);
      });
      rootEl.addEventListener('keydown', (e) => {
        if (e.key !== 'Enter' && e.key !== ' ') return;
        const card = e.target.closest('.js-open-restaurant');
        if (!card) return;
        e.preventDefault();
        const rect = card.getBoundingClientRect();
        openModal(card.getAttribute('data-restaurant-id'), rect.left + rect.width / 2, rect.top + rect.height / 2);
      });
    }

    if (featuredGrid) attachOpenHandlers(featuredGrid);
    attachOpenHandlers(document.getElementById('resultsGrid'));

    modalClose.addEventListener('click', closeModal);
    document.addEventListener('click', (e) => {
      if (modal.hidden) return;
      if (e.target.closest('#beModal')) return;
      if (e.target.closest('.js-open-restaurant')) return;
      closeModal();
    });
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape' && !modal.hidden) closeModal();
    });

    function resetFilters() {
      searchText.value = '';
      priceSelect.value = '__any__';
      cuisineSelect.value = '__any__';
      vibeSelect.value = '__any__';
      areaSelect.value = '__any__';
      scoreMin.value = '0';
      scoreMinLabel.textContent = '0';
      sortSelect.value = 'recommended';
      renderResults();
    }

    // Wire up changes.
    [searchText, priceSelect, cuisineSelect, vibeSelect, areaSelect, scoreMin, sortSelect].forEach((el) => {
      el.addEventListener('input', () => {
        scoreMinLabel.textContent = scoreMin.value;
        renderResults();
      });
      el.addEventListener('change', () => renderResults());
    });

    clearFilters.addEventListener('click', resetFilters);

    // Initial render.
    scoreMinLabel.textContent = scoreMin.value;
    renderResults();
  })();
</script>

