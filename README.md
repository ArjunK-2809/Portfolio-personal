# Arjun K — Portfolio (100% Free APIs)

A personal portfolio with live data — zero ongoing cost, no AI API billing, no serverless functions.

## APIs used — all free forever

| Section | API | Key needed? | Cost |
|---|---|---|---|
| Chess ratings | Chess.com PubAPI | ❌ No key, no signup | Free forever |
| Football scores | TheSportsDB (free tier) | ❌ Uses shared test key `123` | Free forever |
| Basketball scores | TheSportsDB (free tier) | ❌ Uses shared test key `123` | Free forever |
| Cricket / IPL | TheSportsDB (free tier) | ❌ Uses shared test key `123` | Free forever |
| Movies | TMDB (The Movie Database) | ✅ Free key — no card ever | Free forever |
| IEEE/JSSC | Static list in HTML | ❌ No API | Edit manually |
| Gym PRs | Browser localStorage | ❌ No API | Free forever |

---

## Step 1 — Get your free TMDB key (5 minutes, no card required)

1. Go to **https://www.themoviedb.org/signup** and create a free account
2. After verifying email, go to **https://www.themoviedb.org/settings/api**
3. Click **"Create"** → choose **"Developer"** → fill in the simple form (say it's a personal portfolio)
4. Copy the **API Key (v3 auth)** — it looks like `a1b2c3d4e5f6...`
5. Open `public/index.html`, find this line near the top of the `<script>` block:

```js
const TMDB_KEY = 'YOUR_TMDB_KEY_HERE';
```

Replace `YOUR_TMDB_KEY_HERE` with your actual key. Save the file.

That's the only setup required. Everything else (Chess.com, TheSportsDB, IEEE list) works out of the box.

---

## Step 2 — Deploy to Vercel (free, takes ~2 minutes)

### Option A: GitHub + Vercel (recommended — auto-redeploy on every push)

```bash
# Inside the arjun-portfolio folder:
git init
git add .
git commit -m "Initial portfolio"
```

Then create a new repo on **github.com** (call it `arjun-portfolio`), and:

```bash
git remote add origin https://github.com/YOUR_USERNAME/arjun-portfolio.git
git branch -M main
git push -u origin main
```

Now go to **https://vercel.com**:
1. Sign in with GitHub
2. Click **"Add New" → "Project"**
3. Import your `arjun-portfolio` repo
4. Framework Preset: **"Other"** (it's plain HTML, no build step)
5. Click **Deploy** — no environment variables needed for this version!

Done. You'll get a live URL like `arjun-portfolio.vercel.app` in ~30 seconds.

### Option B: Drag and drop (even faster, no GitHub needed)

1. Go to **https://vercel.com/new**
2. Drag and drop the entire `arjun-portfolio` folder onto the page
3. Click Deploy

Your site is live. Share the URL.

---

## Step 3 — Future updates

After making changes to `public/index.html`:

```bash
git add .
git commit -m "Update portfolio"
git push
```

Vercel auto-redeploys in ~20 seconds.

---

## How to update the IEEE/JSSC list

Open `public/index.html` and find the `IEEE_CONFERENCES` array in the `<script>` block.
Edit the dates/deadlines there a couple of times a year as new calls open.
No API exists for this data — even real conference-tracking sites update manually.

---

## Updating your chess ratings displayed as defaults

The page fetches your live Chess.com ratings automatically on every load.
The "1500+" and "1200+" numbers in the HTML are just fallbacks if Chess.com API is temporarily down.

---

## TheSportsDB note

The free test key `123` works fine for personal/non-commercial projects.
If the site grows and you want premium live scores (every 2 min), upgrade to TheSportsDB's $9/month Patreon plan and replace `123` with your personal key.

---

## File structure

```
arjun-portfolio/
├── public/
│   └── index.html      ← entire site (HTML + CSS + JS, single file)
├── vercel.json         ← Vercel static site config
├── package.json
├── .gitignore
└── README.md
```

No build step, no Node.js, no npm install required to run or deploy.
