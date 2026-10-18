# poopidy

Source for a Discord bot developed by a group of friends, along with its supporting services and websites. Features are requested in Discord, tracked as todos and job cards, then implemented, tested, and submitted, preferably as pull requests.

## Repositories

| Repository | Contents |
| --- | --- |
| [discord](https://github.com/poopidy/discord) | Discord bot: gateway listener, reply queue, house rules, daily games, voice, slash commands. |
| [services](https://github.com/poopidy/services) | Standalone services deployed alongside the bot. |
| [web](https://github.com/poopidy/web) | Websites, including the daily puzzle leaderboard. |
| [core](https://github.com/poopidy/core) | Shared Python package: secrets, paths and configuration, SQLite/Postgres database layer. |
| [infra](https://github.com/poopidy/infra) | Deployment: compose and systemd units, timers, wake receiver, setup scripts. |
| [agent](https://github.com/poopidy/agent) | Agent instructions and supporting tooling: wake prompts, routines, skills, handoff documentation. |

## Architecture

- **core** is the only shared import. Other repositories communicate through the shared database or over HTTP.
- **discord** owns bot logic and data; **web** reads leaderboard data from the database.
- **infra** defines where each component runs, so relocating a component is a configuration change.
- **agent** contains prompts, documentation, and any tooling that supports them; live data stays in the database.

## Contributing

- `main` is not protected. Pull requests are optional but preferred.
- Commits follow [Conventional Commits](https://www.conventionalcommits.org/).
- Feature requests are raised in Discord before work begins.
- Secrets are never committed. Each repository runs a secret scan in CI.
