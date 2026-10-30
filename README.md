# Arvor Eleições

Brazilian presidential election data for Claude, with an analytical skill and
a public, read-only MCP connector maintained by [Arvor](https://arvor.co/eleicoes).

Ask in Portuguese or English about presidential results, turnout, geography,
and the available voting-log and TSE receipt diagnostics. The skill guides
coverage checks, pagination, denominators, time zones, and interpretation.

## Install in Claude Code

Run in Claude Code:

```text
/plugin install arvor-eleicoes --marketplace ArvorCo/arvor-eleicoes
```

Alternatively, clone the repository and load it for one session:

```sh
git clone https://github.com/ArvorCo/arvor-eleicoes.git
claude --plugin-dir ./arvor-eleicoes
```

Review the normal plugin and connection permissions when prompted. This plugin
has no hooks, shell commands, API keys, or bundled election databases.

## Use in Claude chat

Add this URL as a custom MCP connector:

```text
https://arvor.co/api/eleicoes/mcp
```

The server needs no sign-in. This repository is prepared for submission to the
Claude directory; it is **not yet listed or approved**. Availability of custom
connectors depends on your Claude plan and organization settings. Installing
the skill alone does not automatically connect the server.

## Example questions

- “What elections and geographic areas does this snapshot cover?”
- “How many votes did Lula receive in the 2022 runoff? Separate Brazil from overseas voters.”
- “Compare presidential votes and turnout in Rio Branco, Acre, in the 2026 runoff.”
- “Show the complete voting, closing, and TSE receipt timeline, including the next day.”
- “Explain the clock indicators and their coverage. What do they establish?”

## Coverage

| Data | Available coverage |
| --- | --- |
| Presidential results by polling section | 2022 and 2026, both rounds |
| Turnout and geographic queries | Available sections in each snapshot |
| Voting-log events, closing and TSE receipt timeline | 2026 runoff, Brazil excluding overseas |
| Clock and closing-to-receipt indicators | 2026 runoff, with documented exclusions |

Start with `arvor_eleicoes_cobertura` for the current snapshot date, sources,
coverage and limitations. The data is a frozen research snapshot, not live
election reporting. The default results query excludes overseas voters; include
them explicitly when needed. Missing observations are not zero.

## Tools

| Tool | Purpose |
| --- | --- |
| `arvor_eleicoes_cobertura` | Snapshot, provenance and coverage |
| `arvor_eleicoes_municipios` | Find TSE municipality codes |
| `arvor_eleicoes_resultados` | Results and turnout for a geographic selection |
| `arvor_eleicoes_timeline` | Paginated log, closing and receipt timeline |
| `arvor_eleicoes_indicadores` | Clock and receipt diagnostics |
| `arvor_eleicoes_local` | Diagnostics for a specific polling place |

## Interpretation

Voting-log events do not identify the chosen candidate or an individual's vote.
Clock signals and long closing-to-receipt intervals do not establish fraud or
altered votes. TSE receipt is not the start of transmission: this interval can
include operational preparation, transport and communication.

The timeline is normalized to Brasília time. Keep cumulative values separate
from interval totals, follow every page for a complete series, and check excluded
logs before comparing event counts with turnout. The tools cannot change results
or provide an official forecast for a future election.

## Privacy Policy

Queries send the requested filters to the Arvor server. No API key or personal
account is required. Do not submit personal information or secrets. Election
datasets remain on Arvor infrastructure; technical request metadata may be
processed as described in the [privacy policy](https://arvor.co/eleicoes/privacidade).
Claude's own data handling is governed separately by Anthropic's terms and policies.

- [Documentation](https://arvor.co/eleicoes)
- [Data collection and reports](https://brasil.arvor.co/)
- [Support and security contact](https://arvor.co/contato)
- [Terms of service](https://arvor.co/eleicoes/termos)

## Validation and directory status

```sh
claude plugin validate --strict .
```

Local package validation does not replace the directory's safety scan or policy
review. A complete six-tool conversation test in Claude and the directory
submission remain pending. The repository contains the client plugin; the hosted
MCP implementation and datasets are maintained separately.

## License

Plugin source is available under the [MIT license](LICENSE). This license does
not relicense third-party election data or grant rights to Arvor trademarks.
