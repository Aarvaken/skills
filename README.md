# Årvåken skills

SEO-skills for AI-agenter som er koblet til [Årvåken](https://aarvaken.no). Skillene er ferdige arbeidsflyter – søkeordsanalyse, nettstedsrevisjon, konkurrentanalyse, AI-synlighet og rapporter – som bruker Årvåkens MCP-verktøy og svarer på norsk.

## Installer

```sh
npx skills add aarvaken/skills
```

Velg skillene og agenten din (Claude Code, Codex, Cursor m.fl.). Agenten må også være koblet til Årvåken: se [Agentoppsett](https://aarvaken.no/hjelp/agent-setup).

**Claude-appen:** last ned skillene én og én fra [aarvaken.no/hjelp/skills](https://aarvaken.no/hjelp/skills#last-ned) (Claude tar én skill per ZIP), og last dem opp under Customize → Skills.

## Skills

| Skill                    | Hva den gjør                                                              |
| ------------------------ | ------------------------------------------------------------------------- |
| `seo-project-setup`      | Fyller ut prosjektets kontekst. Start her.                                |
| `seo-coach`              | Forklarer arbeidsflytene og anbefaler neste steg.                         |
| `seo-audit`              | Reviderer nettstedet og finner de viktigste forbedringene.                |
| `keyword-research`       | Finner og lagrer søkeordmuligheter.                                       |
| `keyword-clustering`     | Grupperer søkeord og kobler dem til sider.                                |
| `competitor-analysis`    | Analyserer én konkurrent.                                                 |
| `competitive-landscape`  | Kartlegger hele markedet i søk.                                           |
| `link-prospecting`       | Finner lenkemuligheter og skriver henvendelser.                           |
| `local-seo`              | Reviderer Google-bedriftsprofilen og synligheten i Maps.                  |
| `ai-visibility-audit`    | Finner hvorfor AI nevner konkurrenter og ikke deg.                        |
| `ai-prompt-research`     | Finner spørsmålene folk stiller AI om bransjen din.                       |
| `seo-report`             | Lagrer resultatet som en rapport du kan dele.                             |
| `customer-keywords`      | Finner søkeordene idealkunden din bruker.                                 |
| `keyword-gap`            | Viser søkeordene konkurrentene rangerer på som du ikke gjør.              |
| `competitor-strategy`    | Gjør konkurrentenes sider og lenker om til en plan.                       |
| `reverse-engineer-seo`   | Finner ut hvordan et nettsted får trafikken sin fra Google.               |
| `reverse-engineer-geo`   | Finner ut hvordan et nettsted kommer med i AI-svar.                       |
| `rank-on-ai`             | Viser hvor du kommer i svarene fra ChatGPT, Perplexity, Gemini og Claude. |
| `chatgpt-business-setup` | Gjør bedriften klar til å kreve profilen sin i ChatGPT.                   |
| `free-tool`              | Finner gratisverktøyet du bør bygge for trafikk fra søk.                  |
| `money-pages`            | For SaaS: sidene kjøpere søker etter rett før de betaler.                 |
| `seo-manager-agent`      | Setter opp en agent som følger opp SEO-en hver uke.                       |

## Oppdatering

Filene her genereres fra Årvåkens hovedrepo med `node fork/scripts/build-skills.mjs` og publiseres med `fork/scripts/publish-skills.sh`. Rediger dem ikke direkte.
