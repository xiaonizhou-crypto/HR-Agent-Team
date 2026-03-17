# Feishu Write-back Test

## Goal

Verify the smallest possible Feishu write-back path.

## Current known issue

The content format is ready, but direct Feishu document creation previously returned `400`.
That means the next test should isolate whether the issue is:
- create action payload
- permission/scopes
- target type mismatch
- write format mismatch

## Test order

### Test 1: create the smallest possible doc

Only try title creation first.
No body content.

Expected result:
- if this fails, the problem is not the hiring-loop content
- it is likely Feishu tool config, permission, or target requirements

### Test 2: create doc, then append one short line

Append only:

```text
- 已确认：测试写入成功
```

### Test 3: write full hiring-loop summary

Use only this 3-line format:

- 已确认：
- 候选人意向/限制：
- 下一步：

## Recommended minimal write-back payload

- Candidate Name: [name]
- Role: [role]
- Current Stage: [stage]
- Owner: [owner]
- Next Step: [next step]
- Status: [status]
- Last Update: [time]
- Notes:
  - 已确认：[summary]
  - 候选人意向/限制：[summary]
  - 下一步：[summary]

## Debug checklist

If Feishu write-back fails, check in this order:
- can the tool create any doc at all
- does the app have the needed doc scopes
- does the target need folder_token or different parent location
- is markdown/body format accepted by the current action

## Success criteria

Success means:
- one doc can be created
- one short line can be written
- one hiring-loop summary can be written without changing the loop format
