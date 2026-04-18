# the <???>ring

## how to join
1. pr this repo:
https://github.com/galisma/webring
2. add this code to your site
```javascript
const ringlink = "https://galisma.github.io/webring/links.json";

function normalizeUrl(url) {
  try {
    const u = new URL(url, window.location.href);
    let path = u.pathname.replace(/\/+/g, "/").replace(/\/$/, "");
    if (path === "") path = "/";
    if (path.endsWith("/index.html")) path = path.slice(0, -"/index.html".length) || "/";
    const host = u.hostname.replace(/^www\./, "").toLowerCase();
    return host + path.toLowerCase();
  } catch {
    return null;
  }
}

async function getLinks() {
  let ring;
  try {
    const response = await fetch(ringlink);
    if (!response.ok) throw new Error(`HTTP ${response.status}`);
    ring = await response.json();
  } catch (err) {
    console.error("failed to load ring:", err);
    return;
  }

  if (!ring || !Array.isArray(ring.links) || ring.links.length === 0) {
    console.error("ring.links is missing or empty");
    return;
  }

  const current = normalizeUrl(window.location.href);
  const index = ring.links.findIndex(l => normalizeUrl(l) === current);

  if (index === -1) {
    console.warn("current page not found in ring:", current);
    return;
  }

  const n = ring.links.length;
  const prev = ring.links[(index - 1 + n) % n];
  const next = ring.links[(index + 1) % n];

  const prevEl = document.getElementById("ring_previous");
  const nextEl = document.getElementById("ring_next");

  if (prevEl) prevEl.href = prev;
  if (nextEl) nextEl.href = next;

  console.log({ current: ring.links[index], prev, next });
}

getLinks();
```
3. add those links:
```html
<a id="ring_previous">prev</a>
<a id="ring_next">next</a>
```

## site links
[static file](https://galisma.github.io/webring/links.json)
[github repo](https://github.com/galisma/webring)

## name ideas
- mudring
- Jerkweb
- webring for the mud ppl
- webringjerk
- jerkring
- pseudo intellectual webring
- Webjerk
- Jebreck
- webjerkring
- Jerkwebring
- Ringjerkweb
- cyberspace jerk
- cyberjerk

## other ideas
webchaos (not a ring but random sites)

## code
https://allium.house/garden/onionring/
https://lambchapel.neocities.org/resources/webstring
https://en.wikipedia.org/wiki/Webring
https://www.youtube.com/watch?v=BpRXwk6_xN8&pp=ygUHd2VicmluZw%3D%3D
https://allium.house/garden/onionring/

## examples of sites with webrings
https://lambchapel.neocities.org/resources/webstring
https://larsfrommars.neocities.org/

# buttons
- everyone makes a button (galisma wants to see some juicy programmer art)
- provide default button
- anti AI button (made with AI)

## generators
https://88x31.datakra.sh/
https://hyperlinkarchive.neocities.org/addbutton

# idk why it was in the thread
https://github.com/stevearc/conform.nvim
