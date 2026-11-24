<p align="center">
  <img src="docs/cover.png" alt="CommonGround logo and app screens" width="820">
</p>

<h1 align="center">CommonGround</h1>

<p align="center">
  <b>From “we should really hang out” to “see you on Wednesday.”</b><br>
  A mobile-first prototype that finds when your friends are free, suggests what to do, and helps you book it, all in one flow.
</p>

<h2 align="center">👉 Try it now: <a href="https://common-ground-mn7n.vercel.app">common-ground-mn7n.vercel.app</a></h2>

<p align="center">
  <a href="https://common-ground-mn7n.vercel.app"><img src="https://img.shields.io/badge/▶_LIVE_DEMO-open_on_Vercel-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Open the live demo on Vercel"></a>
</p>

> 📱 **Open it on your phone for the best experience.** On a laptop, open the link, press `F12`, and click the device-toolbar icon to get a phone-sized view.
> No sign-up needed. It's a **design prototype with mock data**: no real accounts, calendars, bookings or payments.

<p align="center">
  <a href="https://canva.link/tbebb2f7oawreqe">Pitch deck</a> ·
  <a href="https://github.com/thelifeofcosty/CommonGround#the-problem">Research</a> ·
  <a href="https://github.com/thelifeofcosty/CommonGround#what-the-prototype-does">Features</a> ·
  <a href="https://github.com/thelifeofcosty/CommonGround#run-it-locally">Run locally</a>
</p>

Built by a team of seven for at the ***London School of Economics** (2025/26).

<!--
SCREENSHOTS: uncomment this block ONLY after the four PNGs are committed to docs/screenshots/
(file names are case-sensitive).

## Screens

| Home | AI planning chat | Coming up | Who's free now? |
|---|---|---|---|
| <img src="docs/screenshots/01-home.png" width="170"> | <img src="docs/screenshots/02-chat.png" width="170"> | <img src="docs/screenshots/03-coming-up.png" width="170"> | <img src="docs/screenshots/04-whos-free.png" width="170"> |
-->

---

## The problem

Young adults say they want to see friends more, yet plans stall in group chats. Aligning lecture timetables, work shifts and friends spread across a city takes days of messages, abandoned polls and rescheduling.

This is a wider pattern, not just our own experience. The UK Community Life Survey (HM Government, 2023) found adults aged 16–34 were more likely than any other age group to feel lonely often or always. The Mental Health Foundation (2022) found 76% of young people said not being able to see friends hurt their mental health.

**We validated it with a user survey of 62 people** (UK students and young professionals):

| Finding | Result |
|---|---|
| Cited misaligned schedules as the main obstacle | **87%** |
| Found coordinating plans exhausting | **63%** |
| Said confirming a plan takes 1–3 days | **58%** |
| Would download CommonGround | **89%** |
| Would pay extra for premium features | **46%** |

*Only aggregated results are published here; no individual responses are included in this repository.*

### Existing tools solve one piece each

Doodle and When2Meet need manual polls. Google Calendar and Calendly are built for work. TimeTree and FamCal target couples and families. Meetup helps with discovery but not scheduling. **Howbout** is the closest competitor: shared calendars work, but it has no AI, no activity discovery or memory features, and forces users to invite three friends before they can see the app. We designed our onboarding to avoid exactly that.

---

## What the prototype does

Features were prioritised with **MoSCoW** and tested against survey evidence:

| Feature | Priority | What it does | Survey signal |
|---|---|---|---|
| **Schedule coordination** | Must have | Finds overlapping free time across a group; natural-language planning or a manual availability view | Automatic free-time detection was the highest-rated feature |
| **Personalisation** | Must have | Onboarding preferences (food, budget, dietary needs) plus post-activity feedback | 83% found filtered AI suggestions useful |
| **AI activity planning & booking** | Must have / Should have | Suggests venues and activities for the group, with a “surprise me” option | 44% said it would encourage a download |
| **Who's free now?** | Must have | Spontaneous mode: ping friends and see who is free right now | Rated 3.4/5 for usefulness |
| **Last Time Met tracker** | Should have | A gentle nudge when you haven't seen someone in a while | 66% reacted positively |
| **Privacy controls** | Could have | Control what friends can see | Trust baseline |

**Core flow:** open the app → tell the planner who you want to see → pick from shared free slots → choose an activity → the plan lands in *Coming up* with an event chat.

### Design principle: radical simplicity
Every feature must *reduce* friction. If something makes the app feel heavier, it doesn't ship. Pilot testing led to an in-app chat on each confirmed event (so nobody needs a separate WhatsApp thread) and a free-text “Other” field on food preferences.

---

## Prototype vs. the full vision

This repo is a **front-end prototype**. The full concept is described in our report; here is what is built and what is proposed.

| Area | In this prototype | Proposed for a real product |
|---|---|---|
| Interface | React + Vite web app, mobile-first | Native iOS and Android (React Native) |
| Data | Mock data, no backend | Supabase (PostgreSQL) with five domain databases |
| AI planning | <!-- VERIFY: live API call or mocked? Edit this row to match your code. --> [Describe how the AI chat works here] | GPT-4o as a multi-constraint planner behind a secure backend |
| Calendars | Illustrated screens | Google, Apple and Outlook via OAuth 2.0 |
| Booking | Mock booking flow | OpenTable / Eventbrite and Google Places integrations |
| Notifications | Not implemented | Firebase Cloud Messaging; WebSockets for real-time pings |

> **Built with AI assistance.** The prototype was developed with Claude Code and GitHub Copilot. All research, product decisions and design choices are the team's own.

---

## Customer journey

Mapped for “the Busy Student”: **Awareness** (social media or a friend's invite) → **Onboarding** (short preference survey, one-tap calendar connect) → **Planning a meetup** (AI agent or manual view) → **Booking confirmation** → **Day of event** (reminder) → **Post-activity feedback** → **Retention** (Last Time Met nudge, spontaneous meet-ups).

Friction is deliberately concentrated at the planning stage, where existing tools fail, and resolved by the product rather than the user.

## Three use cases

1. **Planning with the AI agent:** Sofia asks for dinner with three friends; the app finds a shared slot and suggests restaurants within budget.
2. **Spontaneous meet-up:** Alex is free on a Tuesday afternoon, taps *Who's free now?*, and sees who responds.
3. **Reconnect nudge:** “You haven't seen Marcus in 5 weeks.” One tap opens planning with Marcus pre-selected.

## Business model and platform thinking

CommonGround is designed as a multi-sided platform linking friend groups and activity providers. It relies on direct, cross-side and data network effects, and starts with booking referrals before sponsored placements, with monetisation deferred until usage is established. UK market sizing: TAM ~12M (ages 18–35), London SAM ~2.4M. The full analysis is in the pitch deck.

## Design trade-offs we identified

- **Cold start:** the AI is weak with no history → mitigated by onboarding preferences.
- **Calendar OAuth friction:** may deter new users → manual availability entry as a fallback.
- **Two-sided bootstrapping:** users and venues need each other → pre-launch with selected venue partners.

---

## Tech stack

React · Vite · [CSS approach] · [routing, if any] · Vercel (auto-deploys from `main`)
<!-- VERIFY: fill from package.json and src/ -->

## Run it locally

Requires [Node.js](https://nodejs.org/) (current LTS).

```bash
git clone https://github.com/thelifeofcosty/CommonGround.git
cd CommonGround
npm install
npm run dev          # http://localhost:5173
```

```bash
npm run build        # production build → dist/
npm run preview      # preview the production build
```

To test on your phone on the same Wi-Fi: `npm run dev -- --host`, then open the network URL.


## Roadmap

- [ ] Real calendar sync with availability-only sharing
- [ ] Server-side AI planning (API keys never shipped to the browser)
- [ ] Booking partner integrations
- [ ] Push nudges for the Last Time Met tracker
- [ ] Second round of usability testing
- [ ] Accessibility pass (contrast, screen-reader labels, reduced motion)

---

## Notes

An academic prototype. All people, places and availability shown are fictional. Personas and quotes in project materials are illustrative.

© 2026 Costanza [Surname] and the CommonGround team. See [NOTICE.md](NOTICE.md).
