---
name: seo-manager-agent
description: "Setter opp en SEO-ansvarlig i OpenAIs dots, xAIs Grok Bot eller Metas Muse: en agent som alltid er på, sjekker ett eller flere nettsteder hver uke med Årvåken (klikk fra Search Console, sporede rangeringer, omtaler i AI-svar) og sender hva som har endret seg og hva som bør gjøres. Setter opp tidsplanen selv når den kjører i en av disse agentene, og veileder brukeren gjennom det ellers. Bruk når brukeren vil ha SEO-en sin fulgt opp jevnlig, en ukentlig SEO-status, eller en agent som styrer SEO-en deres."
license: MIT
---

# SEO manager agent

## Language and market (Årvåken)

Årvåken serves Norwegian businesses. Reply in the user's language: Norwegian (bokmål) unless they write in another language. Name screens the way Årvåken's interface does (Dashbord, Søkeordsanalyse, Lagrede søkeord, Rangeringssporing, Lokal SEO, GSC-innsikt, Domeneoversikt, Tilbakelenker, Nettstedsrevisjon, Promptsporing, Promptanalyse, Promptutforsker, Rapporter, Kontekst). Default the market to Norway and Norwegian unless the project context or the user says otherwise. Keep tool names, parameters and skill names exactly as written.

Give an always-on agent the job of SEO manager: every week it reads each site's numbers from Årvåken and sends what moved and what to do about it. The agent is a dot (OpenAI's always-on ChatGPT agent), a Grok Bot (xAI's) or Muse (Meta's), because all three run scheduled work in the cloud while the user's computer is off. Needs the Årvåken MCP server connected (https://aarvaken.no).

## Inputs

- **The agent.** Use the one the user names. If they name none and you are a dot, a Grok Bot or Muse, use yourself. Otherwise go by what you know about the user from memory or earlier chats: the plan they pay for first, then which of ChatGPT, X and Grok, or Meta's apps they use most. Dots come with ChatGPT Pro or a ChatGPT Business Premium seat (Pro isn't offered in the EEA, UK or Switzerland). Grok Bot comes with X Premium, Super or Ultra, or SuperGrok. Muse is free up to a usage limit, for adults in the US, Canada, Japan and Singapore. Say which you picked, why, and the plan it needs in one line. If nothing points to one, ask once, and say Muse is the one with a free plan.
- **The sites.** Use the ones the user names, any number. Call `list_projects` (it can be large; search it for each domain) and take each project's `id`. If the user names none, use their only project or ask which. A site without a project has nothing to monitor yet; offer `create_project`, which is free.
- **When and where.** Every Monday at 9:00 in the user's time zone (from memory or the computer's clock; ask if you can't tell), sent in the agent's chat, unless they ask for another time or a channel such as Slack.

If Årvåken isn't connected, say so and stop, unless you are a Grok Bot or Muse (step 4 connects it). Don't estimate traffic or rankings yourself.

## Steps

1. **Check where you're running.** If you are a dot, a Grok Bot or Muse, you'll create the schedule yourself. Anywhere else (Claude Code, Codex, Cursor, a regular ChatGPT or Grok chat) you can't create the other agent's schedule, so you'll walk the user through it.
2. **Write the brief.** Fill in the brief below with the sites, their project IDs, the time and time zone, and the channel. Say "scheduled task" for a dot, "routine" for a Grok Bot and "task" for Muse. Of the two opening lines, keep the agent's own, without its label, unless you know it's already connected to Årvåken. The project IDs save the scheduled run from reading the whole project list.
3. **Run the first check-in now.** Follow the brief once yourself, so the user sees what they'll get each week and you find out which sources are connected.
4. **Start the schedule.**
   - **In a dot:** create the recurring task from the brief and confirm the schedule with the user. It appears under **Scheduled** on your profile. If Årvåken's tools aren't available to you, ask the user to install the [Årvåken plugin](https://chatgpt.com/plugins/plugin_asdk_app_6abddd2c7e4c819191f1398c4bd8e9b3) in ChatGPT, then continue.
   - **In a Grok Bot:** if Årvåken isn't connected, add the MCP server `https://app.aarvaken.no/mcp` and show the user the sign-in card. Then create a routine from the brief and read back its **When to run**. A new routine waits for its first scheduled time, so offer **Test** to run it now.
   - **In Muse:** if Årvåken isn't connected, connect it as a custom connector to the MCP server `https://app.aarvaken.no/mcp`, which uses OAuth, and show the user the **Connect** button. Then create a recurring task from the brief and confirm its day and time with the user. It appears under **Upcoming**.
   - **Anywhere else:** give the user the steps for their agent, then the brief to paste.
     - **Dots:** in the ChatGPT desktop app or chatgpt.com on a computer, open dots and follow the introduction. Install the [Årvåken plugin](https://chatgpt.com/plugins/plugin_asdk_app_6abddd2c7e4c819191f1398c4bd8e9b3) and sign in; a dot uses the plugins installed in ChatGPT. Send your dot the brief. Check the schedule under **Scheduled** on its profile.
     - **Grok Bot:** download it from https://x.ai/bot and sign in. Set **Settings → Bot → Timezone**. Send your Bot the brief, which starts by connecting Årvåken, and approve the sign-in card. Open the routine under the Bot's **Details** tab and use **Test** to run it once.
     - **Muse:** open https://muse.ai or the Muse app and sign in. Send Muse the brief, which starts by connecting Årvåken: tap **Connect** and approve on Årvåken's sign-in page. When Muse asks to share information with app.aarvaken.no, allow it for the site, not just once, so the weekly run doesn't wait for approval. Check the task under your assistant's icon → **Upcoming**.
5. **Offer tracking for what's missing.** If a site has no rank tracker for its domain, offer one on its top Search Console queries: show `estimate_rank_tracker_cost` before `create_rank_tracker`. If `get_ai_visibility_tracker` says `configured: false`, show `estimate_ai_visibility_cost` before `save_ai_visibility_tracker`. Both keep spending credits on their own schedule, so set up neither without a yes. Skip this step when both exist.

## The brief

```
[Grok Bot only:] Add the MCP server https://app.aarvaken.no/mcp and show me the sign-in card.
[Muse only:] Connect Årvåken as a custom connector. Its MCP server is https://app.aarvaken.no/mcp and it uses OAuth, so give me the Connect button and I'll approve on Årvåken's sign-in page.

You're my SEO manager. Every <day and time, time zone>, use Årvåken's tools to check <site> (projectId <id>)[, <site> (projectId <id>)] and send me the check-in <in this chat | in the channel I named>. Save this as a recurring <scheduled task | routine | task> and tell me when it first runs. Never start a paid check or change anything without asking me.

For each site:
1. Search Console: get_search_console_performance with dateRange "last_28_days" and dimensions ["date"]. Total the last 7 days and the 7 before: clicks, impressions, and average position weighted by impressions. Then call it with dimensions ["page"] and rowLimit 50 for each of those weeks (startDate and endDate), and compare clicks for the pages in both lists.
2. Rankings: get_rank_tracker lists the project's trackers; use only those whose domain is the site, and read each with its trackerId. Compare position with previousPosition, the last check at least a week earlier. Skip rows whose checkedAt is more than 7 days before the tracker's lastCheckedAt; they keep an old position. If the latest run's errorMessage says it checked only some keywords, say how many in one line. A null position means not found this check, not a lost ranking.
3. AI answers: get_ai_visibility_trend with days 7. Report the change in mention rate only when comparison is "comparable", and say how many answers the change is, since with few prompts one answer moves the rate several points.
4. Organic traffic: get_google_analytics_organic_overview with startDate and endDate for the last 7 full days. It returns the 7 before for comparison.
If a source isn't connected, give its link from the tool's reply in one line and carry on.

Send:
- One headline per site: the week's biggest change.
- "This week": site, clicks, impressions, average position, AI mention rate, organic sessions, each with last week's value.
- "What moved": up to 10 rows of site, page or keyword, source, last week, this week (clicks for a page, position for a keyword). Lead with the three pages whose clicks changed most, then keywords that entered or left the top 10, highest search volume first.
- "Do this week": one to three actions, each tied to a row above.
- "Not connected": each missing source and its link.
```

## Output

1. The first check-in, in the brief's format.
2. **The manager:** the agent and the plan it needs, the schedule with its time zone, the channel, and the sites. Inside a dot, a Grok Bot or Muse, say the schedule is saved and where to see it. Anywhere else, the steps for the user's agent, then the filled-in brief in a code block to copy.
3. The tracking offer from step 5 with each estimate, if anything is missing.

## Notes

- A check-in uses only free Årvåken reads, so it costs no credits. Rank tracking and AI visibility checks run in Årvåken on their own schedules and do cost credits; that's why step 5 shows the estimate first.
- Search Console runs about three days behind, so "the last 7 days" ends three days ago.
- Grok Bot launched in August 2026 and dots and Muse in September 2026, and their menus still change. If a step doesn't match what the user sees, have them ask their agent to set up the schedule from the brief.
- Muse has no MCP setting; it builds the Årvåken connection itself from the brief's opening line. If it shows no **Connect** button, start a new conversation and send the brief as its first message.
