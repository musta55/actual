# Getting Started (for Students)

This is a short guide to running **Actual Budget** on your own computer so you
can explore and experiment with it. Everything runs locally in your browser.

> Already comfortable with Node projects? The whole thing is:
> `git clone … && cd actual && yarn install && yarn start`, then open
> <http://localhost:3001> and click **View demo**.

---

## 1. Prerequisites

Install these once before you start:

| Tool | Version | Notes |
| --- | --- | --- |
| [Node.js](https://nodejs.org/) | **22 or newer** | Check with `node -v` |
| [Yarn](https://yarnpkg.com/) | **4.9.1+** | Comes with Node via Corepack — see below |
| [Git](https://git-scm.com/) | any recent | On **Windows**, install "Git for Windows" — it also provides the `sh` and `bash` shells some scripts use |

Enable the correct Yarn version (only needed once):

```bash
corepack enable
```

Yarn will then automatically use the version this project expects.

---

## 2. Install dependencies

Clone the project and install everything. `yarn install` downloads all the
dependencies into a local `node_modules` folder (which is **not** stored in Git —
that's why you install it yourself).

```bash
git clone <repository-url>
cd actual

yarn install
```


> ⚠️ Always run `yarn` commands from the **project root** (the folder with this
> file in it), never from inside a `packages/…` subfolder.

---

## 3. Run the app

```bash
yarn start
```

This starts the development server. When it's ready, open:

**<http://localhost:3001>**

(The browser may open automatically.)

On the welcome screen:

1. Choose **"Don't use a server"** (you don't need one to explore).
2. Click **"View demo"**.

This creates a sample budget filled with realistic data — several accounts,
hundreds of transactions, categories, schedules, and budgeted amounts — so you
have plenty to play with. The demo data is generated fresh each time and lives
only in your browser, so feel free to change or delete anything: click **View
demo** again for a clean slate.

To stop the server, press `Ctrl + C` in the terminal.

---

## 4. Optional: run with the sync server

You only need this if you want to explore multi-device syncing. It starts the
sync server (port 5006) and the web app together:

```bash
yarn start:server-dev
```

For simply learning and experimenting, `yarn start` is enough.

---

## 5. Useful commands

Run all of these from the project root:

| Command | What it does |
| --- | --- |
| `yarn start` | Start the app in your browser (main command) |
| `yarn test` | Run the test suite across all packages |
| `yarn typecheck` | Check for TypeScript errors |
| `yarn lint` | Check code style and formatting |
| `yarn lint:fix` | Auto-fix style and formatting issues |

If you change code, `yarn typecheck`, `yarn lint`, and `yarn test` are the three
commands that tell you everything is still healthy.

---

## 6. Troubleshooting

**`node -v` shows a version below 22**
Install Node 22+ from <https://nodejs.org/>. If you use `nvm`, run `nvm use` in
the project folder (it reads the `.nvmrc` file).

**`yarn` isn't found or uses the wrong version**
Run `corepack enable`, then try again. It sets up the exact Yarn version this
project needs.

**Port 3001 is already in use**
Another copy of the app is probably still running. Close it, or the app will
offer to start on a different port (e.g. 3002) — just open that URL instead.

**The page fails to load with `ERR_INSUFFICIENT_RESOURCES`**
This can happen on low-memory machines with the dev server. Build the app once
and it will run more lightly:

```bash
yarn build:browser
```

**Windows: a command fails with `'sh' is not recognized`**
Some build scripts are shell scripts. The everyday commands (`yarn start`,
`yarn start:server-dev`, `yarn test`, `yarn typecheck`, `yarn lint`) work
directly in PowerShell or Command Prompt. If you hit this on another command,
run it from the **Git Bash** terminal that ships with Git for Windows.

---

## 7. Learn more

- Actual Budget documentation: <https://actualbudget.org/docs>
- Envelope budgeting basics: <https://actualbudget.org/docs/getting-started/envelope-budgeting>
- Community Discord: <https://discord.gg/pRYNYr4W5A>

---

## 8. How to use the tool

Actual is a local-first **envelope budgeting** app: money in your accounts gets assigned to
category "envelopes", and spending draws those envelopes down.

- Start with **View demo** (section 3) to explore a realistic budget.
- Core flow: add **accounts** → import/enter **transactions** → assign money in the **Budget**
  view → track **reports** and **schedules**.
- 📚 **Official documentation:** <https://actualbudget.org/docs> — start with
  [Getting Started](https://actualbudget.org/docs/getting-started/envelope-budgeting).

---

## 9. How to review the code

Code review is part of the work, not an afterthought:

1. Read the linked issue first, then the diff (GitHub → **Files changed**).
2. Check out the branch locally and run `yarn typecheck`, `yarn lint`, and `yarn test`
   (always from the repo root).
3. Leave **line comments** for specific problems and finish with a summary review —
   **Approve** or **Request changes**.
4. Look for: correctness, tests covering the new behavior, naming/clarity, and unintended
   changes (lockfiles, build artifacts, formatting noise).

Every PR needs at least **one teammate approval** before merge — no self-merges. Review the code,
not the person; be specific and constructive.

---

## 10. Pull requests (PRs)

1. Branch off `master`: `git checkout -b feature/<short-name>` (or `fix/<issue-number>-<slug>`).
2. Keep commits small with meaningful messages.
3. Make sure `yarn typecheck`, `yarn lint`, and `yarn test` pass before pushing.
4. Push to the course fork and open the PR against the course fork's `master` — **never upstream**.
5. In the description: what changed, why, how you tested it, and the linked issue (`Closes #12`).
6. Address review comments with follow-up commits (avoid force-pushes during review), then
   re-request review.

---

## 11. Issue resolution process

1. All work is tracked as **GitHub Issues** on the course fork — bug, feature, or task.
2. Before coding: pick or create an issue, get it **assigned** to you, and outline your approach
   in a comment if it's non-trivial.
3. One issue → one branch → one PR, linked with `Closes #<n>` so the issue closes automatically
   on merge.
4. Blocked for more than a day? Say so on the issue (what you tried, where you're stuck) instead
   of going quiet.
5. An issue is **done** when its PR is merged and the behavior is verified.

---

## 12. AI policies

AI assistants (Claude, ChatGPT, Copilot, …) are allowed as a learning and productivity aid,
under these rules:

- **You are the author.** Understand and be able to explain every line you submit — "the AI
  wrote it" is never an explanation.
- **Test before you commit.** Never push AI-generated code you haven't run and tested locally.
- **Disclose it.** Note meaningful AI assistance in the PR description. This repo also has its
  own AI conventions (see `AGENTS.md`): **AI-authored PR titles are prefixed `[AI]`**, and
  AI-posted GitHub comments/reviews start with 🤖.
- **Protect data.** Never paste secrets, tokens, or private data into AI tools.

Happy budgeting! 🎉
