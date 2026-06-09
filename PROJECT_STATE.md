# Design Brief Form Project State

Last updated: 2026-06-10

## 현재 프로젝트 역할

`09_design-brief-form`은 고객이 브라우저에서 쉬운 디자인 브리프 질문에 답하고 `DESIGN.md` 초안 또는 `답변+프롬프트.md`를 받을 수 있는 공개용 GitHub Pages 도구다.

이 repo의 목적은 내부 제작 스킬을 공개 화면에 합치는 것이 아니라, 외부 사용자가 디자인 용어를 몰라도 채널 디자인 기준 문서의 출발점을 만들 수 있게 돕는 것이다.

## 공개 URL / GitHub Pages 구조

- GitHub repo: `https://github.com/hammedia/design-brief`
- Public URL: `https://hammedia.github.io/design-brief/`
- Pages source: `main` branch `/`
- 공개 루트: 이 repo의 루트 폴더

주요 공개 파일:

- `index.html`: 디자인 브리프 입력 폼
- `card-news-samples.html`: `DESIGN.md` 적용 예시를 보여주는 샘플 페이지
- `assets/`: 공개 페이지용 이미지 자산
- `README.md`: 공개 사용법과 배포 기준
- `PROJECT_STATE.md`: 현재 운영 상태
- `CONVENTIONS.md`: 작업 규칙과 보안 기준

## 현재 구현된 기능

- 핵심 질문 8개를 먼저 보여주는 `public_easy` 입력 흐름
- 기존 세부 질문을 삭제하지 않고 고급 질문 접기 영역에 보존
- 키 없이 `답변+프롬프트.md`와 `사용법.txt`를 ZIP으로 다운로드
- Gemini API 키 입력 시 브라우저에서 `DESIGN.md` RAW DRAFT 생성
- 생성된 `DESIGN.md`에서 `VISUAL_STYLE_SHEET.html` 초안 생성
- `DESIGN.md`가 있는 카드뉴스와 없는 카드뉴스를 비교하는 샘플 페이지 제공
- Tally 연락처 폼으로 이동하는 선택 버튼 제공

## public_easy 모드 상태

- 공개 사용자용 기본 모드로 사용 중이다.
- 질문은 일반 사용자도 이해할 수 있는 짧은 말로 유지한다.
- 색상, 폰트, 그리드 같은 전문어는 고급 질문이나 결과 문서에서 다룬다.
- 공개 `DESIGN.md`는 한국어 본문을 기본으로 하고, `핵심 아이디어 (Core Idea)`처럼 영어 섹션명을 병기한다.
- `research_memo.md`는 기본 생성하지 않는다.
- `DESIGN.md` 초안은 최종 디자인 기준이 아니라 햄PD 또는 사용자의 검토 전 RAW DRAFT다.

## Gemini API 키 처리 기준

- Gemini API 키는 사용자가 브라우저 입력칸에 직접 입력한다.
- 키는 현재 브라우저 화면에서 생성 요청을 보내는 동안만 사용한다.
- 서버에 저장하지 않는다.
- `localStorage` 또는 `sessionStorage`에 저장하지 않는다.
- 문서, 테스트 로그, 커밋 메시지, 이슈, README에 실제 키를 적지 않는다.
- 키 동작을 확인해야 할 때도 실제 키 값은 출력하지 않는다.

## Tally 연락처 수집 기준

- 연락처 수집은 Tally가 담당한다.
- 연락처 남기기는 선택사항이다.
- 연락처 입력은 ZIP 다운로드나 `DESIGN.md` 생성의 조건이 아니다.
- 현재 Tally URL은 README와 `index.html` 기준을 따른다.
- Tally URL 변경은 기능/운영 변경이므로 별도 승인 후 진행한다.

## 현재 보류 / 주의 항목

- `questions.json`, `parse_answers.py`, `generate_design_md.py` 흐름과 공개 폼은 아직 별도다.
- 모드별 질문 스키마 분리는 확정 뒤 별도 작업으로 진행한다.
- `public_easy`와 HAM MEDIA 내부 `star_internal` 제작 흐름을 한 화면에 합치지 않는다.
- 공개 README에는 내부 세계관/운영 기준 본문을 길게 복사하지 않는다.
- 고객 답변, 연락처, API 키가 repo에 남지 않도록 한다.
- GitHub Pages 공개 URL과 Pages source를 임의로 바꾸지 않는다.

## 다음 작업 후보

- README, PROJECT_STATE, CONVENTIONS 간 운영 기준 중복을 주기적으로 정리한다.
- 고급 질문 안내 문구가 공개 사용자에게 충분히 쉬운지 검토한다.
- `DESIGN.md` 출력 품질 테스트는 quota 테스트와 분리해 기록한다.
- 모드별 질문 스키마가 안정되면 공개 폼과 내부 생성기 분리 여부를 재검토한다.
- Tally 폼 문항은 다운로드 조건이 되지 않는 범위에서만 개선을 검토한다.

## 건드리면 안 되는 범위

- `index.html` 기능, Gemini API 호출 코드, ZIP 생성 로직
- Tally URL
- GitHub Pages 공개 URL과 Pages source
- `questions.json`, `parse_answers.py`, `generate_design_md.py`
- HAM MEDIA 내부 스타 제작 스킬 또는 기존 별 `DESIGN.md`
- 루트 repo의 파일과 커밋
- API 키 생성, 변경, 출력

## HAM MEDIA 운영 기준 연결

이 프로젝트는 HAM MEDIA의 디자인 질문/브리프 수집 흐름에 연결된 공개 도구다.

운영 판단이 필요할 때 내부 작업자는 아래 기준을 확인한다.

- `HAM_WORLDVIEW.md`: HAM MEDIA가 무엇을 지키는지 확인하는 세계관 기준
- `HAM_AI_COLLABORATION_RULES.md`: AI와 작업할 때의 공통 운영 기준

단, 이 두 문서의 본문을 공개 README나 공개 화면에 길게 복사하지 않는다.
