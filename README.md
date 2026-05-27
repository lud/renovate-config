# renovate-config

Shared [Renovate](https://docs.renovatebot.com/) preset for personal repos.

## Usage

In any target repo, add a `renovate.json`:

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>lud/renovate-config"]
}
```

The runner ([lud/renovate-runner](https://github.com/lud/renovate-runner))
picks the preset up automatically on its next scheduled run.

## What's in the preset

- `config:recommended` baseline.
- `lockFileMaintenance` enabled — Renovate runs `mix deps.update --all` on a
  weekly schedule (Monday early UTC) and opens a PR with the resulting
  `mix.lock` diff. This catches cascading transitive bumps that direct-dep
  Mix resolvers (e.g. Dependabot) skip.
- No hourly or concurrent PR limits — runs are infrequent, so unblocking
  throughput matters more than rate-limiting.

## License

MIT
