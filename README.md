# [Project name]

[![Hippocratic License HL3-BOD-CL-ECO-FFD-LAW-MEDIA-MIL-MY-SV-TAL-USTA-XUAR](https://img.shields.io/static/v1?label=Hippocratic%20License&message=HL3-BOD-CL-ECO-FFD-LAW-MEDIA-MIL-MY-SV-TAL-USTA-XUAR&labelColor=5e2751&color=bc8c3d)](https://firstdonoharm.dev/version/3/0/bod-cl-eco-ffd-law-media-mil-my-sv-tal-usta-xuar.html)

---

[One-sentence description of the project.]

For more details on the project structure and design, see the [ADR](ADR.md) document.

## Feature Coverage

<details>
<summary>Feature checklist</summary>

Test functions are tagged with `#feature <ID>`.

> `[x]` tested &nbsp; `[ ]` supported, no test yet &nbsp; `[-]` not supported

### Category 1

- [ ] `[CAT1-ShortName]` — [Name]

</details>

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See [Install](#install) for notes on how to install the project.

### Prerequisites

- Node.js 24 ([Node.js](https://nodejs.org/) or [Mise](https://mise.jdx.dev))
- Nix with flakes enabled (optional, for the reproducible development shell)

### Setup

Clone the repository, enable the local Git hooks, install dependencies, and run the checks:

```sh
git clone git@github.com:BlueSialia/[repository name]
cd [repository name]
./setup-hooks.sh
npm install
npm run build
```

With Nix and direnv:

```sh
direnv allow
```

Otherwise, enter the development shell with `nix develop`.

### Running

```sh
npm start
```

## Running the Tests

### Unit Tests

You can run the unit tests with:

```sh
npm test:unit
```

Unit tests are located in in the `tests/unit/` directory.

### Integration Tests

```sh
npm test:integration
```

Integration tests are located in in the `tests/integration/` directory.

### E2E Tests

```sh
[command to run E2E tests]
```

[Explanation of their location]

### Linting and type checking

On top of it you should also periodically run the linter with:

```sh
npm run lint
npm run typecheck
npm run knip
```

### Coding Style

In order to maintain a similar style over the codebase we use:

```sh
npm run format:check
```

## Install

[Describe how to install or deploy the project, if applicable.]

## Built With

| Dependency | Purpose |
|---|---|
| [TypeScript](https://www.typescriptlang.org/) | Application language and type checking  |
| [Node.js](https://nodejs.org/) | Development runtime and test runner |
| [npm](https://www.npmjs.com/) | Package manager and script runner |
| [Knip](https://knip.dev/) | Unused and missing dependency detection |

## Automations

Local Git hooks enforce Conventional Commits. CI runs formatting, linting, unused and missing dependency checks, type checking, tests, and the build. Dependency security checks and release pull requests are also automated.

See [AUTOMATIONS.md](AUTOMATIONS.md) for more information and details.

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

## Versioning

We use [SemVer](https://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/BlueSialia/[repository name]/tags).

## Authors

- **Jorge Domínguez** - _Initial work_ - [BlueSialia](https://github.com/BlueSialia)

See also the list of [contributors](https://github.com/BlueSialia/[repository name]/contributors) who participated in this project.

## License

This project is licensed under the Hippocratic License 3.0 - see the [LICENSE.md](LICENSE.md) file for details.

## Acknowledgments

None yet.
