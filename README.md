# Saleha-ai-portfolio
Saleha Rehan — Portfolio Site
A personal portfolio site for a biomedical engineering student working at the intersection
of AI/ML and hands-on biomedical systems. Built for graduate-school applications and research
outreach — the audience is admissions committees, potential research advisors, and anyone
evaluating my technical work.
Live site: https://saleharehan97-del.github.io/Saleha-ai-portfolio/
What it does, and for whom
Five pages — Home, Research, Projects, Background, Contact — that let a visitor understand in
under a minute what I build and why, then dig into the actual evidence (results, my specific
contribution on collaborative work, methods) if they want to go deeper. Built for graduate
admissions reviewers and research contacts, not a general audience.
Setup a stranger could follow
This is a static site — no build step, no server, no dependencies to install.
Clone the repo: `git clone https://github.com/saleharehan97-del/Saleha-ai-portfolio.git`
Open `index.html` directly in a browser, or serve it locally with any static server,
e.g. `python3 -m http.server` from the repo root, then visit `localhost:8000`
To deploy your own copy: push to a GitHub repo, then enable GitHub Pages under
Settings → Pages → Deploy from branch → `main` → `/ (root)`
No API keys, no environment variables, no build tooling required.
Usage
Navigate via the top nav bar on any page: Home (summary + proof statement) → Research
(the Alzheimer's detection work, methods, results, manuscript status) → Projects (hardware
applied ML work) → Background (research interests, trajectory, education) → Contact
(a working form via Netlify Forms).
Architecture
```
Saleha-ai-portfolio/
├── index.html          Home — hero, proof statement, manuscript badge
├── about.html           Background — research interests, "how I got here", education
├── research.html         Alzheimer's detection research — methods, results, my role
├── projects.html         Hardware + applied ML projects
├── contact.html          Contact form (Netlify Forms) + CV placeholder
├── style.css              Shared styles (single stylesheet, CSS custom properties)
├── favicon.svg             Site icon
└── *.png / *.jpeg           Project images (fusion results, hardware photos, etc.)
```
All 5 pages share one `style.css` and the same header/nav markup — no templating engine,
just plain HTML/CSS, kept deliberately simple since the content is the point, not the tooling.
Eval results (v2 — post external review)
This site went through two rounds of real, external testing rather than shipping untested:
Round 1 — peer/mentor crit (Week 6): external reviewer feedback led to concrete fixes —
added an explicit "My role" section distinguishing my contribution from a co-author's on
collaborative research, added a manuscript-visibility badge to the homepage, added an
explicit research-trajectory section connecting hardware work to the graduate research goal,
and reframed a 3-option research-interest list as one coherent intersection.
Round 2 — self-directed adversarial testing (Week 7):
Tried to break the contact form: empty submission correctly blocked by browser validation;
garbage/malformed email is accepted (expected — format-only validation, no backend to
verify real deliverability); rapid double-submit does not create duplicate entries.
Checked every link on every page — no dead links found.
Found and fixed a real infrastructure bug: Netlify's production visibility was set to
Private, silently blocking both Google's crawler and PageSpeed's testing bot — this was the
actual root cause of a 28/100 mobile performance score and the site being completely absent
from Google search results (only an old LinkedIn profile showed up). Fixed by switching
visibility to Public, adding full SEO/Open Graph metadata across all 5 pages, and verifying
the site in Google Search Console.
Added GA4 analytics; confirmed working via the Realtime report.
Found and fixed a second bug during launch-hygiene testing: Open Graph tags referenced a
stale domain, so social-share link previews (WhatsApp, etc.) rendered blank. Fixed and
confirmed working via Facebook's Sharing Debugger and a live WhatsApp test.
Limitations (stated, not hidden)
Netlify (the originally-intended production host) has its free-tier build minutes
exhausted until ~Sept 4, 2026, so its deployment is currently frozen/stale. GitHub Pages
is the actual live, up-to-date URL in the meantime — see the Live Site link above.
No downloadable CV/PDF yet — the CV page shows structured details only; my current CV
draft isn't finalized, so I chose not to upload an outdated version. The page states this
honestly rather than hiding the gap.
A contact-page horizontal-overflow bug appears on at least one specific mobile device.
Extensively investigated — the underlying code shows no overflow and passes review, so this
looks like a device-specific rendering quirk rather than a code bug. Not yet resolved.
Contact form validates email format only, not real deliverability — expected for a
static form with no backend; verifying a real inbox would require a confirmation-email flow
this project doesn't have.
`fb:app_id` is not set — an optional Open Graph property for Facebook-specific share
analytics; not required for link previews to render correctly, and previews were confirmed
working without it.
Built with AI
I built this site working with Claude (Anthropic) as a hands-on technical collaborator
throughout — Claude wrote and edited the HTML/CSS, debugged the SEO/analytics/deployment
issues described above, and walked me through each GitHub/Netlify/Google Search Console step.
I made every content and design decision myself (what to say about my research, how to frame
my contribution on collaborative work, which testing findings counted as real bugs versus
acceptable limitations), and I personally verified every fix described in this README by
checking it live myself before considering it done — including the two real bugs listed
above, which I found through my own adversarial testing, not by asking Claude to look for
them.
