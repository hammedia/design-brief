# Design Brief Form Conventions

Last updated: 2026-06-10

## 기본 원칙

이 repo는 공개용 GitHub Pages 도구다. 고객이 브라우저에서 디자인 브리프 질문에 답하고 `DESIGN.md` 초안 또는 AI용 프롬프트 파일을 받는 흐름을 다룬다.

작업자는 먼저 목적과 범위를 확인한다. 모르면 추측하지 말고 질문한다.

## 개인정보 / API 키 보호

- 고객 답변을 서버, repo, 테스트 로그에 저장하지 않는다.
- 실제 연락처, 실제 API 키, 실제 개인정보를 예시 데이터로 넣지 않는다.
- Gemini API 키는 저장하지 않고 브라우저 메모리에서만 사용한다.
- Gemini API 키를 `localStorage`나 `sessionStorage`에 저장하지 않는다.
- API 키, 토큰, 비밀번호를 문서, 커밋 메시지, 이슈, 스크린샷, 테스트 결과에 출력하지 않는다.
- 테스트가 필요하면 가짜 키나 마스킹된 값을 사용한다.

## 연락처 수집

- 고객 연락처 수집은 Tally가 담당한다.
- Tally 입력은 선택사항이다.
- 연락처 입력을 다운로드 조건으로 강제하지 않는다.
- Tally URL 변경은 운영 변경으로 보고 별도 승인 후 진행한다.

## DESIGN.md 출력 기준

- `DESIGN.md`는 최종 디자인 기준이 아니라 햄PD 또는 사용자의 검토 전 초안이다.
- 공개 `DESIGN.md`는 한국어 본문을 기본으로 하고, 필요한 섹션명에 영어를 병기한다.
- `TODO`, `adjustable`, `CONFLICT`는 완성값처럼 취급하지 않는다.
- `public_easy` 모드는 일반 사용자도 이해하기 쉬운 질문 구조를 유지한다.
- 색상, 폰트, 그리드 같은 전문 기준은 사용자의 쉬운 답변에서 추출하거나 고급 질문에서 보강한다.
- `research_memo.md`는 공개 모드의 기본 출력물이 아니다.

## HAM MEDIA 운영 기준 연결

- 이 도구는 HAM MEDIA의 디자인 질문/브리프 수집 흐름에 연결된다.
- 내부 작업자는 판단이 흔들릴 때 `HAM_WORLDVIEW.md`를 먼저 확인한다.
- AI 협업, stage, commit, 민감정보 처리 기준은 `HAM_AI_COLLABORATION_RULES.md`를 따른다.
- 내부 HAM MEDIA 세계관과 AI 공통 운영 기준 본문을 공개 문서에 길게 복사하지 않는다.
- 공개 사용자에게 필요한 설명과 내부 작업자용 운영 기준을 섞지 않는다.

## 파일 수정 기준

- 기능 수정 요청이 아닌 문서 작업에서는 `index.html`을 수정하지 않는다.
- Gemini API 동작, fallback, quota 처리, ZIP 생성 로직은 별도 기능 작업으로만 수정한다.
- Tally URL, GitHub Pages 공개 URL, Pages source는 임의로 변경하지 않는다.
- `questions.json`, `parse_answers.py`, `generate_design_md.py`와 공개 폼을 임의로 동기화하지 않는다.
- 기존 별 폴더, HAM MEDIA 홈페이지 파일, 내부 스타 제작 스킬은 이 repo 작업과 섞지 않는다.

## Git 기준

- 이 폴더는 별도 git repo다. 루트 repo와 섞어 커밋하지 않는다.
- `git add .`를 사용하지 않는다.
- 작업자가 직접 수정한 파일만 명시적으로 stage한다.
- 작업 전 이미 수정되어 있던 파일은 임의로 되돌리거나 stage하지 않는다.
- 테스트 임시 폴더와 실제 고객 답변은 커밋하지 않는다.
- 커밋 전 `git diff --check`를 실행한다.
- 커밋 전 staged 파일 목록을 확인한다.
