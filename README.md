 **Best viewed on a phone.** On desktop, open the demo and switch your browser to a mobile viewport (Chrome DevTools → Toggle device toolbar → iPhone 14).  
> Built as a group project for **MG4C3, London School of Economics (Digital Innovation, [2025/26])**. This is a design prototype with mock data — no real accounts, calendars or payments.

---

## Demo

| Home / Who's free | Overlap finder | AI suggestions | Booking |
|---|---|---|---|
| ǃ[](docs/screenshots/01-home.png) | ǃ[](docs/screenshots/02-overlap.png) | ǃ[](docs/screenshots/03-suggestions.png) | ǃ[](docs/screenshots/04-booking.png) |

<p align="center">‹img src="docs/screenshots/flow.gif" alt="30-second walkthrough" width="300"></p>

---

## The problem

Adults say they want to see friends and family more, but coordination kills plans: endless group-chat polling, mismatched calendars, and nobody wanting to be the one who organises.

We ran a **user validation survey with [52] respondents** <!-- VERIFY exact n --> to test which pain points were real and which features people would actually use.

**Key insights** <!-- fill with your real numbers -->
- **[X]%** said finding a time that works for everyone is the hardest part of making plans.
- **[X]%** said they'd use an app that detected shared free time automatically.
- **[Insight on spontaneity / last-minute plans]**
- **[Insight on losing touch with people]**

**Features we tested in the survey**
| Feature | What it does | Survey signal |
|---|---|---|
| Automatic overlap detection | Finds windows when everyone in a group is free | [High / Medium / Low – X%] |
| AI activity suggestions | Proposes things to do based on group, budget, location, interests | [ ] |
| “Who's free now” | Spontaneous mode — see who's available right now nearby | [ ] |
| Last-seen tracker | Gentle nudges when you haven't seen someone in a while | [ ] |
| Shared memory archive | Photos and notes from past plans, kept in one place | [ ] |
| New-people suggestions | Suggests friends-of-friends or people with shared interests | [ ] |
| Smart filtering | Filter suggestions by cost, distance, vibe, accessibility | [ ] |

What we changed because of the research: **[e.g. prioritised overlap detection + AI suggestions for the MVP; moved new-people suggestions to the roadmap because respondents were wary of it]**.

---

## Features

What's in this prototype: <!-- VERIFY each item against the actual screens -->

- **Groups** — create a group (“Uni friends”, “Family”) and see everyone's availability at a glance.
- **Find a time** — automatic overlap detection highlights slots where everyone is free.
- **Suggestions** — AI-style activity ideas for the chosen slot, with smart filters. <!-- VERIFY: real AI API or mocked? -->
- **Book it** — pick an activity and confirm in-app (mock booking flow).
- **Who's free now** — spontaneous mode for last-minute plans.
- **Last seen** — see how long it's been since you saw each person.
- **Memories** — a shared archive of past meet-ups.

---

## Tech stack

| Layer | Tools |
|---|---|
| UI | React <!-- VERIFY version in package.json --> |
| Build tooling | Vite |
| Styling | [CSS modules / Tailwind / plain CSS] <!-- VERIFY --> |
| Routing | [React Router / single view] <!-- VERIFY --> |
| Data | Local mock data (no backend) <!-- VERIFY --> |
| Design | [Figma] |
| Hosting | Vercel (auto-deploys from `main`) |

---

## Run it locally

Requires [Node.js](https://nodejs.org/) 20.19+ or 22.12+ <!-- VERIFY against your Vite version; per the Vite team's "Vite 7.0 is out!" post, Vite 7 "requires Node.js 20.19+, 22.12+" and dropped Node 18 -->.

```bash
git clone https://github.com/thelifeofcosty/CommonGround.git
cd CommonGround
npm install
npm run dev        # opens on http://localhost:5173
```

Other scripts:

```bash
npm run build      # production build → dist/
npm run preview    # serve the production build locally
```

To test on your phone on the same Wi-Fi: `npm run dev -- --host`, then open the “Network” URL it prints.

---

## My role

**Costanza [Surname]** — [e.g. Product & visual design lead]

- [Led the visual identity: name, logo, colour system, typography]
- [Designed the core flows in Figma and built them as a React prototype]
- [Co-designed and analysed the user validation survey (n≈52)]
- [Wrote the pitch narrative and presented to the panel]

## Team

| Name | Role | Links |
|---|---|---|
| Costanza [Surname] | [Design & front-end prototype] | [LinkedIn] · [Portfolio] |
| [Name] | [Research & survey analysis] | [LinkedIn] |
| [Name] | [Business model / market sizing] | [LinkedIn] |
| [Name] | [Strategy / go-to-market] | [LinkedIn] |

Built for **MG4C3, London School of Economics**. Thanks to [lecturer/teaching team, with permission].

---

## Roadmap

- [ ] Real calendar sync (Google / Apple / Outlook) with privacy-first, availability-only sharing
- [ ] Live AI suggestions via a server-side API (keys never shipped to the browser)
- [ ] Booking partner integrations (restaurants, events, activities)
- [ ] Push nudges from the last-seen tracker
- [ ] Usability testing round 2 on the high-fidelity prototype
- [ ] Accessibility pass (contrast, screen-reader labels, reduced motion)

---

## Notes

This is an academic prototype. All people, places and availability shown are fictional. Survey findings are reported in aggregate; no individual responses are included in this repository.

© [2026] Costanza [Surname] and the CommonGround team. See [NOTICE.md](NOTICE.md).
