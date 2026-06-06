# Design Brief Form

고객이 브라우저에서 쉬운 채널 디자인 질문에 답하고, 우리 채널의 디자인 기준 문서 초안을 받을 수 있는 공개용 단일 페이지 도구다.

이 도구는 `public_easy` 모드다. 외부 사용자가 디자인 용어를 몰라도 먼저 8개 핵심 질문에 답하고, 필요할 때만 고급 질문을 열어 색상·폰트·레이아웃 같은 세부 기준을 더 적는 구조다.

프로젝트 폴더:

```text
09_design-brief-form/
```

이 폴더는 GitHub Pages 공개 루트로 쓰는 배포용 폴더다.

- GitHub repo: `https://github.com/hammedia/design-brief`
- Public URL: `https://hammedia.github.io/design-brief/`
- 공개 루트: `main` 브랜치의 `/`

## 사용법

1. `index.html`을 브라우저에서 연다.
2. 채널명과 8개 핵심 질문에 답한다.
3. 더 자세히 정하고 싶으면 고급 질문을 열어 추가로 답한다.
4. 아래 두 경로 중 하나를 선택한다.
5. 결과는 ZIP 파일로 받는다.

## public_easy 모드

- 첫 화면에는 쉬운 핵심 질문 8개를 먼저 보여준다.
- 기존 세부 질문은 삭제하지 않고 고급 질문 접기 영역에 보존한다.
- 고급 질문은 선택이다.
- 공개 `DESIGN.md`는 한국어 본문을 기본으로 하고, `핵심 아이디어 (Core Idea)`처럼 영어 섹션명을 병기한다.
- `research_memo.md`는 기본 생성하지 않는다.
- 필요 시 사용자의 원답 보관용 `답변원본.md` 선택 출력만 별도 검토한다.

## 경로 A. 여기서 바로 만들기

Gemini API 키를 입력하면 브라우저 안에서 한국어 본문 기반 `DESIGN.md` RAW DRAFT와 `VISUAL_STYLE_SHEET.html`을 생성하고 ZIP으로 내려받는다.

- 모델: `gemini-2.5-flash`
- API 키는 브라우저 메모리에서만 사용한다.
- API 키를 서버로 저장하거나 `localStorage`에 저장하지 않는다.
- ZIP 파일명: `[채널명]-디자인가이드.zip`
- ZIP 내용: `DESIGN.md`, `VISUAL_STYLE_SHEET.html`, `사용법.txt`
- 연락처 남기기는 선택사항이다.
- `research_memo.md`는 포함하지 않는다.

`VISUAL_STYLE_SHEET.html`은 생성된 `DESIGN.md`에서 색상, 타이포그래피, Do/Don’t만 결정적으로 추출해 고정 템플릿에 채운 시각 기준표다. `TODO`, `CONFLICT`, `pending`, 빈 HEX/폰트 값은 완성값처럼 보이지 않게 흐린 안내 상태로 표시한다.

## 경로 B. 파일로 받아서 직접

Gemini 키 없이 진행한다.

ZIP 파일에는 다음 내용이 들어간다.

- `사용법.txt`
- `답변+프롬프트.md`

`답변+프롬프트.md` 전체를 ChatGPT, Claude, Gemini 등에 붙여넣으면 `DESIGN.md` 초안을 만들 수 있다.

- ZIP 파일명: `[채널명]-디자인브리프.zip`
- 이 경로는 아직 `DESIGN.md`가 생성되기 전이므로 `VISUAL_STYLE_SHEET.html`은 포함하지 않는다.

## 배포

GitHub Pages에 올릴 때는 이 폴더 전체를 공개 루트로 사용한다. 01번 프로젝트의 `github-pages/` 폴더와 같은 역할을 이 폴더 자체가 맡는다.

```text
09_design-brief-form/
├── index.html
├── card-news-samples.html
├── assets/
├── GITHUB_PAGES.md
└── README.md
```

## 개인정보

- 이 페이지는 고객 답변을 서버에 저장하지 않는다.
- 연락처 수집은 Tally가 담당한다.
- 연락처 입력은 다운로드 조건이 아니라 선택사항이다.
- Tally URL: `https://tally.so/r/Y5kVV6`

## 제작

- 제작: 햄(함동민)
- Threads: `@dellacasa_2`
- 문의: `hammedia002@gmail.com`
- 홈페이지: `https://hammedia.github.io/hammedia`

## 라이선스

오픈 사용 가능. 단, 제작 크레딧은 유지한다.
