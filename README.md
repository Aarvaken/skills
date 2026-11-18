# Årvåken skills

SEO-skills for AI-agenter som er koblet til [Årvåken](https://aarvaken.no). Skillene er ferdige arbeidsflyter – søkeordsanalyse, nettstedsrevisjon, konkurrentanalyse, AI-synlighet og rapporter – som bruker Årvåkens MCP-verktøy og svarer på norsk.

## Installer

```sh
npx skills add aarvaken/skills
```

Velg skillene og agenten din (Claude Code, Codex, Cursor m.fl.). Agenten må også være koblet til Årvåken: se [Agentoppsett](https://aarvaken.no/hjelp/agent-setup).

**Claude-appen:** last ned [alle skills som ZIP](https://aarvaken.no/skills/aarvaken-skills.zip) eller én og én fra [aarvaken.no/hjelp/skills](https://aarvaken.no/hjelp/skills), og last dem opp under Customize → Skills.

## Skills

| Skill                   | Hva den gjør                                               |
| ----------------------- | ---------------------------------------------------------- |
| `seo-project-setup`     | Fyller ut prosjektets kontekst. Start her.                 |
| `seo-coach`             | Forklarer arbeidsflytene og anbefaler neste steg.          |
| `seo-audit`             | Reviderer nettstedet og finner de viktigste forbedringene. |
| `keyword-research`      | Finner og lagrer søkeordmuligheter.                        |
| `keyword-clustering`    | Grupperer søkeord og kobler dem til sider.                 |
| `competitor-analysis`   | Analyserer én konkurrent.                                  |
| `competitive-landscape` | Kartlegger hele markedet i søk.                            |
| `link-prospecting`      | Finner lenkemuligheter og skriver henvendelser.            |
| `local-seo`             | Reviderer Google-bedriftsprofilen og synligheten i Maps.   |
| `ai-visibility-audit`   | Finner hvorfor AI nevner konkurrenter og ikke deg.         |
| `ai-prompt-research`    | Finner spørsmålene folk stiller AI om bransjen din.        |
| `seo-report`            | Lagrer resultatet som en rapport du kan dele.              |

## Oppdatering

Filene her genereres fra Årvåkens hovedrepo med `node fork/scripts/build-skills.mjs` og publiseres med `fork/scripts/publish-skills.sh`. Rediger dem ikke direkte.
