# Design Brief Form Project State

Last updated: 2026-06-19

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

### 2026-06-19 업그레이드 (커밋됨)

- **첫 화면 개편:** 들어오면 결과 예시 + 신뢰 문구 + 익명 고객 한 줄을 먼저 보여주고, "무료로 디자인 가이드 만들기" CTA로 질문지를 같은 페이지에서 펼침. 매번 접힘으로 시작(localStorage 미저장).
- **HAM UI 색 역할 표준:** 블루(#7EB5E8)=강조·링크, 그린(#00704A)=실행 버튼, 레드(#CC0000)=경고. 토큰 `assets/css/ham-tokens.css`(원본은 `05_HAM_DesignStudio/design-system/ham-tokens.css`).
- **결과 예시 교체:** 기준 A(차분·신뢰) / 기준 B(또렷·강조) / 기준 없음(제각각) — 상세 페이지(`card-news-samples.html`)도 일치.
- **생성 프롬프트 업그레이드:** 색은 역할 이름으로 중립화(답변에 없는 블루/그린 기본값 금지), 절제는 금지목록 대신 원리+이유, 분리 순서(여백→위계→대비→선/그림자), 채널 정체성 유지.
- **대비 안전 스타일시트 변환기:** 배경 휘도로 글자색 자동 선택(4.5 필수 / 7 목표), 다크 테마 처리, 밝은 버튼엔 검은 글자. `buildVisualStyleSheetFromDesign`.
- **미리보기 루프(Part 2):** 같은 페이지 iframe 미리보기 + [답 수정하기]/[다시 생성하기] 분리. "다시 생성 = Gemini 한 번 더 사용" 안내. 로딩 중 이전 미리보기 유지 후 교체. (Gemini 경로 한정.)
- 근거: getdesign.md 70여 개 딥스터디 + 3중 리서치(`05_HAM_DesignStudio/reference/external-design-md/_getdesignmd_study/`).

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

## 다음 작업 후보 (2026-06-19 기준)

- **(우선) 09 push** — 위 업그레이드는 로컬 커밋만. push 시 공개 사이트 반영. 배포 전 일반 브라우저 ZIP 다운로드 스모크 테스트 권장.
- **질문지 업그레이드** — 딥스터디 통찰을 추려 쉬운 질문 1~2개 추가(예: "첫 시선의 주인공?", "버튼이 또렷/차분?"). 제안 → 검토 → 적용. *질문은 핵심이라 신중히.*
- **변환기 보강** — YAML/frontmatter 성격 강한 DESIGN.md 색 파싱 약점(스터디서 발견) 보강.
- **기준 한 줄 문서화** — 브랜드 잠긴 색은 AA(4.5) 충족, 도구 생성물은 7:1 목표로 구분.
- **완성 시 포지셔닝·홍보 적용** — `docs/working/20260619_완성시_포지셔닝_홍보_적용메모.md` 참조(루프·질문지 반영 후).
- (보류) Part 2-B: Gemini가 스타일시트 "모양"까지 생성 — 지금은 변환기로 충분, 나중 검토.

## 건드리면 안 되는 범위

- Gemini API 호출 코드, ZIP 생성 로직, 변환기 대비 안전 로직 (index.html의 UI·문구·미리보기는 햄PD 승인 후 변경 가능 — 2026-06-19 업그레이드처럼)
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
