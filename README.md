# hmz-paperclip-content-engine

> **Autonomous LinkedIn content engine | runs 8:00 AM daily | builds DigiMinds thought leadership without lifting a finger**

[![schedule](https://img.shields.io/badge/schedule-8%3A00AM_daily-blue?style=flat)](.) [![platform](https://img.shields.io/badge/platform-LinkedIn-0077B5?style=flat)](.) [![status](https://img.shields.io/badge/status-always_on-brightgreen?style=flat)](.) [![company](https://img.shields.io/badge/company-DigiMinds-orange?style=flat)](.)

[Overview](#overview) · [Pipeline](#pipeline) · [Content Types](#content-types) · [Calendar](#calendar) · [Tips](#tips)

---

## 🧠 OVERVIEW

Paperclip Content Engine generates and schedules LinkedIn content for DigiMinds every morning at 8 AM. It pulls trend signals, picks the best content angle for the day, writes post copy + hooks, and schedules via LinkedIn API. HMZ's personal brand runs on autopilot.

| Component | Value |
|---|---|
| Trigger | Daily 8:00 AM (LaunchAgent) |
| Output platform | LinkedIn (HMZ personal + DigiMinds page) |
| Content volume | 1 post/day + 3 comments on competitor posts |
| Model | Gemini Flash (zero Claude tokens) |
| Style guide | HMZ voice: direct, data-driven, no fluff |

---

## ⚙️ PIPELINE

```
08:00 AM trigger
    │
    ├─► Fetch trends: Google Ads news, Meta updates, PPC industry shifts
    ├─► Pull top competitor posts from last 24h (engagement signals)
    ├─► Select content angle (rotation: insight → case study → hot take → tip → story)
    │
    ├─► Generate: hook + body + CTA (Gemini Flash, HMZ voice)
    ├─► Quality check: readability, no fluff, data present, hook strength
    │
    └─► Schedule via LinkedIn API (target: 10 AM publish for max reach)
```

| Stage | Tool | Output |
|---|---|---|
| Trend pull | Groq + Google News API | Top 5 signals |
| Angle selection | Rotation calendar | Day's content type |
| Copy generation | Gemini Flash | Hook + body + CTA |
| Quality gate | Rules-based check | Pass/fail score |
| Publish | LinkedIn API | Scheduled post |

---

## 📅 CONTENT CALENDAR (ROTATION)

| Day | Content Type | Focus |
|---|---|---|
| Monday | Industry insight | Google Ads update or Meta change |
| Tuesday | Case study | DigiMinds client result (anonymized) |
| Wednesday | Hot take | Contrarian PPC/marketing opinion |
| Thursday | Tactical tip | Actionable PPC/CRO tip |
| Friday | Story | Founder journey or client win |
| Saturday | Curated thread | Best of week roundup |
| Sunday | Question | Community engagement post |

---

## 💡 TIPS

■ **Content Quality (5)**
| Tip | Source |
|---|---|
| Hook must contain a number or shocking claim — first 2 lines decide everything | LinkedIn algorithm |
| Never post generic "5 tips" content — always tie to specific data or result | HMZ voice guide |
| Comments on competitor posts drive 3x more profile visits than standalone posts | LinkedIn SOP |
| Best publish time: 10-11 AM weekdays (engine auto-targets this) | Analytics data |
| Posts with personal failure stories get 4x more comments than success stories | DigiMinds test |

■ **Operations (3)**
| Tip | Source |
|---|---|
| Check `/api/content?date=today` to preview before publish | API ref |
| If quality gate fails, engine posts to draft queue instead of publishing | Error handling |
| Content calendar can be overridden via `/api/content/override` | API ref |

---

## ☠️ TOOLS REPLACED

| Content Engine | Replaced |
|---|---|
| Daily LinkedIn content | 45-min manual writing session |
| Trend research | Manual news scanning |
| Competitor monitoring | Manual LinkedIn stalking |
| Scheduling | Buffer/Hootsuite subscription |

---

## ⚠️ GOTCHAS

| Issue | Fix |
|---|---|
| LinkedIn API rate limit | Engine queues and retries next hour |
| Quality gate fails repeatedly | Review HMZ voice guide in config |
| Post went out with wrong angle | Manual override: `/api/content/override` |
| Engagement dropped | Check if LinkedIn algorithm changed — update hook rules |

---

*Part of [DigiMinds AI Agency Stack](https://github.com/hmzainjamil) — Paperclip autonomous content engine*
