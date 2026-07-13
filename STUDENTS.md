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

Happy budgeting! 🎉
