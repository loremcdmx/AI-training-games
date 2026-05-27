# AI Training Games

AI Training Games is a local React/Vite workspace for training neural agents against Minesweeper and deterministic strategy games. The first screen is the working surface: game selection, live status, champion ELO, profile controls, replay, telemetry, archived checkpoints, and strategy sandboxes for chess, tic-tac-toe, and Connect Four.

Production: https://ai-training-games.vercel.app

## Commands

```bash
npm install
npm run dev
npm run build
npm run lint
npm run test
npm run test:e2e
```

`npm run test` runs the fast Vitest unit suite for pure decision logic.  
`npm run test:e2e` runs the Playwright browser flows.  
If port `4175` is busy, run Playwright with `PLAYWRIGHT_PORT=<port> npm run test:e2e`.

## Project Map

- `src/App.tsx` - orchestration for the Minesweeper lab, profile state, telemetry, persistence hooks, and experience switching
- `src/lib/minesweeperArenaConfig.ts` - experience cards, roadmap content, profile naming, and arena growth milestones
- `src/lib/minesweeperPersistence.ts` - persisted state loading, profile sanitizing, archive migration, and ELO snapshot merging
- `src/lib/minesweeperUi.ts` - shared UI formatting helpers for labels, pace, ETA, board captions, and profile copy
- `src/lib/evolution.ts` - move selection, evaluation, and generation training logic
- `src/lib/neural.ts` - network shape, feature extraction, and candidate evaluation
- `src/workers/trainingWorker.ts` - background training loop
- `src/components/StrategyArena.tsx` - strategy-game sandbox UI and replay flow
- `tests/*.spec.ts` - end-to-end browser checks
- `tests/*.test.ts` - fast unit tests

## Notes

- Minesweeper state, active profile, ELO archive, and selected experience are persisted in `localStorage`.
- Peak bots and milestone bots are frozen in the archive so they can be replayed and calibrated later.
- The repo is optimized for two feedback loops: a fast pure-logic loop with Vitest and a browser verification loop with Playwright.
