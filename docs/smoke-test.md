# Smoke Test

Use this file to test whether `hiring-loop` can be triggered as one skill.

## Goal

Verify 3 things:
- the skill is installed and ready
- the runtime can use it as one main skill
- the output can reach the minimum hiring loop format

## Step 1: check skill

```bash
openclaw skills info hiring-loop
```

Expected:
- skill exists
- status shows ready

## Step 2: run one direct prompt

Use a prompt that explicitly asks for the whole loop:

```text
Use the hiring-loop skill as one main skill and run a minimal hiring loop on this backend candidate case.
Target role: 资深后端研发工程师（AI 平台 / 分布式系统方向）
Candidate Name: Ankur Saurabh
Current Role: Backend Engineer & Product Architect
Resume Summary: 7+ years backend, AI platforms, distributed systems, Python/Django, PostgreSQL, Redis, AWS, blockchain, payments.
Current Stage: 待补资料
Owner: HR
Last Update: 30 hours ago
Next Step: confirm recent hands-on backend scope and AI platform ownership.
Output must stay short and human.
```

## Step 3: expected output shape

A passing result should include:
- Resume Screener
- Candidate Coordinator
- Hiring Ops Tracker
- Feishu-ready write-back

## Pass criteria

Pass if:
- the skill is treated as one skill, not three agents
- the output stays short and usable
- the three sub-capabilities stay separated
- the final write-back is Feishu-ready

## Fail signals

Fail if:
- runtime hangs or exits without usable output
- the model ignores the loop and gives generic chat
- output turns into a long report
- the skill behaves like three separate roles instead of one loop
