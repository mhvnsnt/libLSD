# HANDOFF — libLSD

**Last updated: 2026-11-22 (America/New_York).**
**Repo:** `mhvnsnt/libLSD` (PUBLIC), default branch `master` (not `main` — use this branch as the PR base).
**Purpose of this file:** any agent that picks up work here reads this FIRST, then the linked docs. It states what we've done, where we're at, and what we're working toward — so the owner can say "go to this repo, pick up the work" and you just know. Update this file in the same PR whenever the state changes (add, don't delete).

## 1. What this repo is

A C# library for loading LSD: Dream Emulator data files — mirrored into the owner's account 2026-11-20. This is Figglewatts' libLSD: structs for most of the data file types in the game (LBD and the rest), each constructed from a `BinaryReader`. Available as a NuGet package (`libLSD`); docs at figglewatts.co.uk/libLSD.

This is a support library, not a game and not a decomp. It is the piece the other LSD repos build on: LSDRevamped (Figglewatts' Unity remake) uses it to load the original data, and the `lsd-decomp` README credits it for documenting the file formats. How the owner's LSD repos relate:
- `mhvnsnt/lsd-decomp` — the AI-written matching decomp, complete (1,447/1,447 functions read).
- `mhvnsnt/lsddecomp` — the brian-oblivion lineage complete matching decomp (CC0).
- `mhvnsnt/lsd_decompiled` — the cawfee lineage, early-stage WIP decomp.
- `mhvnsnt/lsddecomp-1` — the FirecatFG first attempt from 2024.
- `mhvnsnt/LSDRevamped` — Figglewatts' Unity remake — the main consumer of this library.

## 2. Where we're at

### DONE
- **Library complete for its purpose (2023-08):** "Simplify VAB format", "Fix sample list", "Fix SEQSequence length", "various fixes to VAB format", "fixes" (`913f2b4`, 2023-08-28). Last push 2023-08-28 — this repo has not been touched in over three years.
- **Mirrored into this account 2026-11-20** (repo created here that day; history carried over).
- **Published:** NuGet package + docfx docs (`docfx_project/`).

### IN PROGRESS
- Nothing in progress. No open PRs, no releases in this mirror. This is a frozen snapshot of a finished small library.

### BLOCKED
- Nothing blocked. Nothing is being built here.

## 3. What we're working toward

Reference and dependency. This repo is kept so the LSD data formats stay readable and the remake keeps building: if LSDRevamped work ever resumes, or a new tool needs to read LSD files (LBD, VAB, SEQ and the rest), this is the library that does it — use it, don't rewrite it. If a format turns out to be wrong or incomplete, the fix lands here first (with the docs updated), then flows to the consumers.

## 4. Standing rules that apply here

- **Branch → PR → merge, always.** Never push to `master` directly. Add-only, zero-conflict PRs, no force pushes. (This is a public library mirror — a bad merge breaks downstream builds.)
- **Checkpoint-and-save law:** CHECKPOINT.md first, update after every step; the repo is the save; resume, never restart.
- **No-temp-storage law:** nothing in /tmp or any wipeable location, ever. Everything goes straight into the repo or a durable folder the second it exists.
- **Real-source-only:** the structs describe the real file formats, verified against real game files. Never invent a field.
- **Licence/source logged honestly:** Figglewatts' work (see upstream `figglewatts/libLSD`); the game data it reads is Asmik Ace / Osamu Sato's. You need your own copy of the game data to use it.
- **Never kill in-progress work.** Never delete game files or other lanes' work without the standing verification rules.

## 5. Key files and paths

| What | Where |
|---|---|
| Library source | `src/` |
| Solution | `libLSD.sln` |
| Docs (docfx) | `docfx_project/` (published at figglewatts.co.uk/libLSD) |
| Usage | `README.md` (NuGet install, `BinaryReader` constructor pattern, LBD example) |
| Main consumer | `mhvnsnt/LSDRevamped` (also in this batch) |
| Related repos (NOT this one) | `mhvnsnt/lsd-decomp`, `mhvnsnt/lsddecomp`, `mhvnsnt/lsd_decompiled`, `mhvnsnt/lsddecomp-1`, `mhvnsnt/LSDRevamped` |

## 6. Open decisions needing the owner

- None open. This is a finished library; any change (a new format, a fix) is his call when a consumer needs it.

## 7. How to pick up

1. Read this HANDOFF.md first, then `README.md`.
2. To use it: install the `libLSD` NuGet package, open a game data file with a `BinaryReader`, construct the struct (e.g. `new LBD(br)`). Docs at figglewatts.co.uk/libLSD.
3. Never commit game data. Never push to `master` directly.
4. Land work branch → PR → merge, add-only, base branch `master`.
5. Update this HANDOFF.md in the same PR when the state changes.
