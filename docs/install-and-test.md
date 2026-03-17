# Install and Test

## What this is

`hiring-loop` is one OpenClaw skill with three sub-capabilities:
- Resume Screener
- Candidate Coordinator
- Hiring Ops Tracker

## Local packaged file

`dist/hiring-loop.skill`

## Install idea

Use another OpenClaw agent or workspace as the test target.
Install this skill there, then test one case through the main entry.

## Suggested first test

Use one real candidate and run the full loop:

1. Resume Screener
   - input one resume + one target role
   - check: continue / why / next step

2. Candidate Coordinator
   - generate request-more-info or interview scheduling message
   - check: natural, short, directly usable

3. Hiring Ops Tracker
   - record current stage / owner / next step / status
   - check: whether it correctly says 正常推进 / 临近超时 / 已卡住

## Pass criteria

The skill is good enough for the next round if:
- the skill triggers on hiring workflow requests
- the three sub-capabilities stay separated
- the output stays short and human
- the loop can go from screening to Feishu-ready write-back

## Minimal test prompts

### Resume Screener
"Screen this resume for 资深后端研发工程师（电商 / 搜索方向） and tell me whether to continue."

### Candidate Coordinator
"Based on this screening result, draft a short request-more-info message."

### Hiring Ops Tracker
"This candidate is in 待约初面, owner is HR, next step is sending interview invite, last update was 30 hours ago. Tell me status and next step."
