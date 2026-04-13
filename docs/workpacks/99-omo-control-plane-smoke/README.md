# 99-omo-control-plane-smoke

## Goal

- OMO control-plane live smoke sandbox slice

## Branches

- 백엔드: `feature/be-99-omo-control-plane-smoke`
- 프론트엔드: `feature/fe-99-omo-control-plane-smoke`

## In Scope

- 화면: control-plane smoke fixtures
- API: supervisor runtime transitions
- 상태 전이: Stage 1~6 autonomous loop
- DB 영향: 없음
- Schema Change:
  - [x] 없음 (읽기 전용)
  - [ ] 있음 → `supabase/migrations/<파일명>.sql` 생성 필요

## Out of Scope

- product feature delivery

## Dependencies

| 선행 슬라이스 | 상태 | 확인 |
| --- | --- | --- |
| `01-discovery-detail-auth` | bootstrap | [x] |

## Backend First Contract

- request: 없음
- response: runtime / stage-result contract
- 권한 / 소유자 검증 / 상태 전이 / 멱등성: workflow-v2 문서 기준

## Frontend Delivery Mode

- 디자인 확정 전: 기능 가능한 임시 UI
- 필수 상태: `loading / empty / error / read-only / unauthorized`
- 로그인 보호 액션 없음

## Design Authority

- UI risk: `not-required`
- Anchor screen dependency: 없음
- Visual artifact: not-required
- Authority status: `not-required`
- Notes: sandbox smoke fixture only

## Live Smoke Contract

- Stage 3 backend review attempt 1 must return `request_changes` and include `SMOKE_BACKEND_FIX_TOKEN: backend-request-1`.
- Stage 3 backend review attempt 2 must return `request_changes` and include `SMOKE_BACKEND_FIX_TOKEN: backend-request-2` after token 1 is applied.
- Stage 2 retries must update `smoke/omo-control-plane/99-omo-control-plane-smoke/backend-review-loop.md` and mark the requested token as applied.
- Stage 3 backend review attempt 3 may approve only after both backend tokens are applied.

## Design Status

- [x] 임시 UI (temporary)
- [ ] 리뷰 대기 (pending-review)
- [ ] 확정 (confirmed)
- [ ] N/A

## Source Links

- `docs/engineering/workflow-v2/README.md`
- `docs/engineering/workflow-v2/omo-autonomous-supervisor.md`

## QA / Test Data Plan

- smoke fixture baseline
- sandbox repo only
- seed/reset 없음
- blocker: sandbox repo unavailable

## Key Rules

- Stage 2 implementation before doc gate pass is forbidden
- review ping-pong is capped

## Primary User Path

1. supervisor starts a sandbox slice
2. stage runner produces deterministic artifacts
3. review loop converges and records checkpoints

## Delivery Checklist
- [x] 백엔드 계약 고정 <!-- omo:id=delivery-backend-contract;stage=2;scope=backend;review=3,6 -->
- [ ] UI 연결 <!-- omo:id=delivery-ui;stage=4;scope=frontend;review=5,6 -->
