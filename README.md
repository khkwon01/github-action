### Github Action 동작 Flow
```
+------------------+
|   GitHub Event   |  ← 예: push, pull_request, schedule 등
+------------------+
         |
         v
+----------------------+
|  Workflow Dispatcher |  ← `.github/workflows/*.yml` 파일 확인
+----------------------+
         |
         v
+----------------------+
|   Workflow Runner    |  ← GitHub-hosted or self-hosted
+----------------------+
         |
         v
+----------------------+
|    Job Scheduler     |  ← jobs 정의 확인 후 병렬 또는 순차 실행
+----------------------+
         |
         v
+----------------------+
|   Each Job Context   |  ← 각 job은 별도 가상환경에서 실행
+----------------------+
         |
         v
+----------------------+
|  Step Executor Loop  |  ← 각 step (run, uses 등) 순차 실행
+----------------------+
         |
         v
+--------------------------+
|  Action / Script 실행     | ← Docker or JavaScript action
+--------------------------+
         |
         v
+-------------------------+
|     Output & Artifacts  | ← logs, outputs, cache, etc.
+-------------------------+
         |
         v
+-------------------+
|   Job 종료 Signal  |
+-------------------+
         |
         v
+----------------------+
| Workflow 결과 리포트    |
+----------------------+

```

### Github Action으로 인한 workflow run 방지
- commit 메시지 입력할 때 아래와 같이 입력하면 workflow가 skip됨
```
[skip actions]
```  
