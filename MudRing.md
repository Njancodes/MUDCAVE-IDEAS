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
or add this (preferable if you're on neocities)
```html
<script src="https://galisma.github.io/webring/links.js"></script>
<script src="https://galisma.github.io/webring/script.js"></script>
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
web sphere (2d ring)
https://youtu.be/AGh5LM7Jmfk
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

## fix for neocities
https://corsfix.com/blog/fix-neocities-content-security-policy

# buttons
- everyone makes a button (galisma wants to see some juicy programmer art)
- provide default button
- anti AI button (made with AI)

## generators
https://88x31.datakra.sh/
https://hyperlinkarchive.neocities.org/addbutton

# idk why it was in the thread
https://github.com/stevearc/conform.nvim

# sphere
https://youtu.be/AGh5LM7Jmfk
<img width="2584" height="2572" alt="image" src="https://github.com/user-attachments/assets/ce0819b5-3307-4d2a-9610-c1a475217d9b" />

## explanation
we add one dimention to a webring, we get a webshere. The reason its a 2d sphere is that we are looking at the sphere's area which is 2d.
The shpere is made by taking a one dimentional array that we project onto the sphere. Every time a member will join, the sphere will change.
The sphere is created from top to bottom, the first element of the array will be the north pole and the newest addition the south pole.
Sites are not placed by geographic location.
Because it is a sphere, the closer you are to the emisphere, the more your website will be recommended to people. So that gives newcommers and veterans the advantage.

## north pole
this is the main site of the webring, because its at the north pole it will be 
it would contain this:
- information about the sphere
- how to join
- the git repos
- a list of all participants (or a link to the json)
- possibly a 3d viewer of the sphere.

for differents moments in the year, the site theme may change.  

## website viewer
This is to be done once the normal shpere is finished.
a webviewer just like google earth of the sphere.
we can click on the links and rotate the globe around.
Every site is assigned a patch of land.
You may draw on your land, there is no moderation on what you draw, if you descide to draw a dick, you can but I wont click on your site.
if the user doesnt provide a drawing, either words extracted from the site will be shown or leave it blank or something.
The countries shape are probably just simple squares although we could make some function with some perlin noise or something to make prettier borders.
