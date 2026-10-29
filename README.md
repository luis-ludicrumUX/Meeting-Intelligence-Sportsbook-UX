# Meeting Intelligence — Sportsbook UX

A dashboard that turns Sportsbook meeting transcripts into actions, decisions, PM concerns, UX issues, objectives and communication coaching. Part of Project Ludicrum (GemBet Sportsbook).

## How it runs

`index.html` is a single self-contained page published as a **claude.ai artifact**. The live app is the artifact, not this repo. The page depends on two artifact runtime capabilities:

| Capability | Used for |
|---|---|
| `db` | Stores meetings, transcripts and all records. Access rule: read and write limited to the owner and Editors. |
| `sample` | "Analyze with Claude": runs the transcript analysis on the viewer's own Claude account. |

Opened outside claude.ai (for example from GitHub Pages or Vercel), the page loads but shows "Storage unavailable" and cannot save or analyse.

## Structure

- **Meetings**: switch meetings by date (tabs, dropdown, previous/next) and filter by type (Sportsbook PM, UX Team). Each meeting has tabs: Summary, Critical issues, Actions, Decisions, PM concerns, UX issues, Objectives, Coaching, Next meeting prep, Transcript.
- **Overview**: KPIs, items that need attention, follow-ups owned by others, deadlines and milestones.
- **Import transcript**: upload `.txt`, `.vtt`, `.srt`, `.md` or `.docx`, or paste text. Creates one meeting and stores its transcript.

## Data model

Collections: `meetings`, `transcripts`, `actions`, `decisions`, `concerns`, `issues`, `objectives`, `reviews`, `milestones`. Every record has an ID (`MTG-001`, `ACT-001`, ...), a `meetingId`, optional `meetingIds` for later meetings that discussed it, a certainty (Confirmed, Proposed, Inferred, Needs validation), evidence, and a `history` log.

## Data policy

Meeting content is confidential. No meeting data, transcripts or exports are committed to this repo; `.gitignore` blocks the common export paths.

## Updating

Edit `index.html`, commit, and republish the same file to the artifact.
