# Contributing to Veilway UI

The general guide is [CONTRIBUTING.md in veilway](https://github.com/veilway-project/veilway/blob/main/CONTRIBUTING.md): ways to help, the contributor agreement (`CLA.md`, signed once on your first pull request in any Veilway repository), and how pull requests are reviewed. Security problems are never reported in public: see `SECURITY.md`.

What is different here:

- Checks, tests, the gallery and its screenshots all run in containers. The commands are in `packages/ui/README.md`.
- A visible change needs screenshots in dark and light, English and Persian.
- A theme file and a locale pack are hostile input: a change to the theme validator or the locale loader comes with tests that feed it bad files.
- No pill shapes, no uppercase labels above headings, no emoji, small consistent corner radii. Apps never show a rating word for a connection: only its name, and a plain warning when it is not secure.
- Code style: no blank lines inside function bodies, double quotes, one-liners where they fit, no single-use helpers, comments only where they add something the code does not say, and never a code formatter, since it adds blank lines and breaks one-liners.
