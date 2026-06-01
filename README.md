# Design Brief Form

고객이 브라우저에서 채널 디자인 질문에 답하고, 우리 채널의 디자인 기준 문서 초안을 받을 수 있는 공개용 단일 페이지 도구다.

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
2. 채널명과 디자인 질문에 답한다.
3. 아래 두 경로 중 하나를 선택한다.
4. 결과는 ZIP 파일로 받는다.

## 경로 A. 여기서 바로 만들기

Gemini API 키를 입력하면 브라우저 안에서 `DESIGN.md` RAW DRAFT를 생성하고 ZIP으로 내려받는다.

- 모델: `gemini-2.5-flash`
- API 키는 브라우저 메모리에서만 사용한다.
- API 키를 서버로 저장하거나 `localStorage`에 저장하지 않는다.
- ZIP 파일명: `[채널명]-디자인가이드.zip`
- ZIP 내용: `DESIGN.md`, `사용법.txt`
- 연락처 남기기는 선택사항이다.

## 경로 B. 파일로 받아서 직접

Gemini 키 없이 진행한다.

ZIP 파일에는 다음 내용이 들어간다.

- `사용법.txt`
- `답변+프롬프트.md`

`답변+프롬프트.md` 전체를 ChatGPT, Claude, Gemini 등에 붙여넣으면 `DESIGN.md` 초안을 만들 수 있다.

- ZIP 파일명: `[채널명]-디자인브리프.zip`

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
