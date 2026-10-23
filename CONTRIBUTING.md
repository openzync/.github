# Contributing to OpenZync

OpenZync is six shipped repositories, each independently released. A change goes to the repository
that owns the code, and a change to the API contract is accompanied by SDK and MCP updates, each as
its own pull request in its own repository. Do not send cross-repository pull requests from a single
branch.

## Development setup

| Repository | Install | Check |
|---|---|---|
| openzync-core | `make dev` — boots OpenBao, PostgreSQL, and Redis, then uvicorn | `make test` (unit only), `make test-all` (adds integration, security, e2e) |
| openzync-python-sdk | `pip install -e ".[dev]"` | `pytest` |
| openzync-mcp | `make install` | `make test` (80 % coverage gate) |
| openzync-frontend | `npm install` | `npm test`, `npm run lint` |
| openzync-landing | `npm install` | `npm run test -w landing`, `npm run lint -w landing` |
| openzync-docs | `pip install -r requirements.txt`, with a sibling `openzync-core/` checkout | `sphinx-build -b html . _build/html` |

Python 3.11 or newer. The backend also needs Docker with compose v2. Integration tests need real
PostgreSQL and Redis and will not pass under `make test` alone.

## Commits

Conventional commits: `feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `chore:`, with an optional
scope — `fix(auth/rate-limit):`, `chore(release): 1.0.0`. One logical change per commit; the subject
line states the behavior change, the body says why.

## Pull requests

- Tests pass for the repository you touched. If the change fixes a bug, the fix carries the test
  that would have caught it.
- No secrets, credentials, or environment-specific values in the diff. `openzync-core` runs a
  pre-commit credential check (`scripts/check-credentials.sh`) and will reject hardcoded keys.
- No fallbacks that hide a failure. Let errors propagate.
- Behaviour changes update the docs in `openzync-docs` and, for releases, a changelog fragment
  under `changelog.d/` where the repository uses one.
- Keep pull requests reviewable: one concern, a description of the user-visible effect, and the
  tradeoff you rejected.

## Documentation

The contributor guide, including test layout and release steps, is at
[docs.openzync.tech/en/latest/guides/contributing.html](https://docs.openzync.tech/en/latest/guides/contributing.html).
Questions go to [SUPPORT.md](./SUPPORT.md); vulnerabilities go to [SECURITY.md](./SECURITY.md), never
a public issue. This project follows the [Code of Conduct](./CODE_OF_CONDUCT.md).
