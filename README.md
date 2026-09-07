# first-agent-ai
Build an Agent AI with Claude

## Skills
Project skills live in `.claude/skills/`. `weather-report` formats raw weather
data into a markdown report — it's called by the `weather-reporter` agent
below, which fetches the data and hands it off for formatting.

## Agents
Project agents live in `.claude/agents/`. `weather-reporter` fetches current
conditions and a 3-day forecast from Open-Meteo (no API key needed) for a
given city, then invokes the `weather-report` skill to format and save the
result to `reports/`.


# Test Agent and Skill:

1. Open a session Claude Code into de first-agent-ai or open folder project
`cd ~/Projects/ClaudeCode/first-agent-ai && claude`

2. Request in claude console "generate a weather report of <city>" or for two or more ciry "generate a weather report between <city> and <city>"

3. Check reports in folder reports (generate two reports per request (.md and html)).
