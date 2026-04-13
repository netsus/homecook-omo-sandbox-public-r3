# Acceptance Checklist

## Happy Path
- [x] API 응답 형식이 { success, data, error }를 따른다 <!-- omo:id=accept-backend-api;stage=2;scope=backend;review=3,6 -->
- [ ] loading 상태가 있다 <!-- omo:id=accept-loading;stage=4;scope=frontend;review=5,6 -->

## State / Policy
- smoke state transition contract is documented in workflow-v2 fixtures

## Error / Permission
- smoke error handling is exercised through deterministic request-changes loops

## Data Integrity
- smoke artifacts must stay deterministic across retries

## Data Setup / Preconditions
- sandbox repo and smoke fixture baseline are prepared before execution

## Manual QA
- verifier: smoke harness
- environment: sandbox repo
- scenarios: backend iterative review loop

## Automation Split

### Vitest
- deterministic smoke validations run through dedicated Vitest coverage

### Playwright
- no browser automation is required for this sandbox smoke

### Manual Only
- [ ] live OAuth smoke
