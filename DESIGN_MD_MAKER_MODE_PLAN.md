# Design MD Maker Mode Plan

Status: planning draft
Scope: Design MD Maker mode split only
Last updated: 2026-06-06

이 문서는 Design MD Maker를 바로 구현하기 전에, 공개 사용자용 `public_easy` 모드와 HAM MEDIA 내부 스타 제작용 `star_internal` 모드의 역할과 질문 구조를 분리하기 위한 1차 계획이다.

중요 원칙:

- `09_design-brief-form`은 공개 사용자용 도구로 유지한다.
- `ham-star-design-md-maker`는 HAM MEDIA 내부 스타 제작용 스킬로 유지한다.
- 두 모드를 한 화면이나 한 질문지에 억지로 합치지 않는다.
- `questions.json`은 바로 덮지 않는다. 모드별 질문 스키마가 확정된 뒤 분리 여부를 결정한다.

## 1. 공통 DESIGN.md 출력값

두 모드는 질문 표현과 내부 처리 범위가 다르지만, 최종적으로 `DESIGN.md`가 담아야 하는 결정값은 공통 축을 가진다.

| 출력값 | DESIGN.md 위치 | 설명 |
| --- | --- | --- |
| 문서 상태 | front matter / status comment | `proposal`, `raw draft`, `approved` 등 현재 사용 가능 상태 |
| 정체성 / 목적 | Core Idea 또는 Visual Theme | 무엇을 위한 디자인 기준인지, 무엇을 만들려는지 |
| 대상 / 보는 사람 | Audience 또는 research-derived summary | 누구에게 보여주는지, 어느 수준의 사람이 보는지 |
| 느껴야 할 감정 | Visual Theme / Copy Rules | 방문자나 시청자가 받아야 할 첫 인상 |
| 피해야 할 인상 | Do / Don't, Imagery Rules | 절대 만들면 안 되는 느낌, 톤, 이미지 |
| 색상 방향 | Color System | 색상 토큰, 역할, 사용 위치, 근거가 확실한 HEX |
| 글자 방향 | Typography | 기본 서체, 포인트 서체, 제목/본문/강조 역할 |
| 첫 화면 / 대표 장면 | First Screen / Hero | 처음 보여줄 문장, 이미지, 고정 요소 |
| 이미지 기준 | Imagery Rules | 사용할 이미지와 금지 이미지, 실제 자료 기준 |
| 고정 요소 | Components / Logo / Stamp | 로고, 워드마크, 스탬프, 별 코드, 면책 문구 등 |
| 출력물별 규칙 | Output-Specific Rules | 카드뉴스, 유튜브, PDF, 홈페이지 등 적용 매체별 규칙 |
| 가독성 / 접근성 | Accessibility | 읽기 크기, 대비, 모바일/영상 가독성 |
| 말투 / 문장 기준 | Copy Rules / Agent Prompt Guide | 문장 톤, 자주 쓰는 표현, 피할 표현 |
| 업데이트 규칙 | Version & Update Rule | 이 문서가 어디까지 적용되는지, 다음 확인 항목 |

`research_memo.md`가 있는 모드에서는 아래 항목을 `DESIGN.md`가 아니라 `research_memo.md`에 남긴다.

- 답변 원문
- 판단 근거
- 사적 기억과 비공개 요소
- 폰트/이미지/스탬프 출처
- 라이선스 확인 내용
- TODO / CONFLICT 해소 전 메모
- 공개 문서에 남기면 안 되는 내부 제작 판단

## 2. `public_easy` 모드 질문 8개

대상:

- 외부 사용자
- 디자인 용어를 잘 모르는 사람
- 채널 디자인 기준 문서 초안을 쉽게 받고 싶은 사람

방향:

- 질문은 쉬운 말로 묻는다.
- 색상, 폰트, 그리드 같은 전문어를 앞에 두지 않는다.
- 사용자의 답변에서 `DESIGN.md` 결정값을 추출한다.
- 결과물은 `DESIGN.md` 초안 또는 `답변+프롬프트.md`로 충분하다.
- 기존 질문을 삭제하지 않는다. 첫 화면에는 8개 핵심 질문만 먼저 보여주고, 기존 세부 질문은 `고급 질문` 접기 영역으로 옮긴다.
- 공개 `DESIGN.md`는 한국어 본문을 기본으로 한다. 섹션명은 `핵심 아이디어 (Core Idea)`, `색상 시스템 (Color System)`처럼 한국어와 영어를 병기한다.
- `research_memo.md`는 기본 생성하지 않는다. 필요할 경우 선택 출력으로 `답변원본.md`를 검토한다.

| 번호 | 질문 | DESIGN.md 연결 | research_memo.md 연결 |
| --- | --- | --- | --- |
| P1 | 무엇을 만들고 싶나요? | Output-Specific Rules, Core Idea | 필요 없음. 공개 모드는 별도 `research_memo.md`를 기본 생성하지 않음 |
| P2 | 누구에게 보여줄 건가요? | Audience summary, Accessibility, Copy Rules | 필요 없음 |
| P3 | 어떤 느낌이 나야 하나요? | Visual Theme, Color System 힌트, Typography 힌트 | 필요 없음 |
| P4 | 절대 피하고 싶은 느낌은? | Do / Don't, Imagery Rules, Risk Rules | 필요 없음 |
| P5 | 꼭 들어가야 할 자료가 있나요? | Logo / Brand Mark, Components, Fixed Elements | 필요 없음 |
| P6 | 좋아하는 예시가 있나요? | Visual Theme, Color System, Typography, Layout 힌트 | 필요 없음 |
| P7 | 싫어하는 예시가 있나요? | Do / Don't, CONFLICT 판단, 금지 스타일 | 필요 없음 |
| P8 | 어디에 쓸 건가요? | Output-Specific Rules, Layout, Accessibility | 필요 없음 |

`public_easy` 모드의 보조 추출값:

- 색상: 사용자가 직접 색을 말하면 반영하고, 말하지 않으면 분위기에서 임시 토큰을 제안한다.
- 폰트: 폰트명을 요구하지 않고 `차분한`, `또렷한`, `부드러운`, `강한` 같은 말에서 역할을 제안한다.
- 레이아웃: 그리드를 묻지 않고 사용처와 출력 비율에서 필요한 규칙을 만든다.
- 리스크: 의료, 금융, 법률, 저작권, 광고성 표현이 답변에 나오면 Do / Don't에 반영한다.

`public_easy`의 화면 구조 제안:

- 기본 질문: P1-P8만 먼저 노출한다.
- 고급 질문 접기: 기존 질문 중 색상, 폰트, 레이아웃, 컴포넌트, 이미지, 로고, 영상, 참고자료 관련 세부 질문을 접힌 영역에 보존한다.
- 고급 질문은 필수가 아니다. 사용자가 열어 답하면 더 구체적인 `DESIGN.md`가 나오고, 비워두면 핵심 8문항에서 추출한 값과 `adjustable` 초안값으로 처리한다.
- 기존 질문 ID와 의미는 가능하면 유지한다. 다만 사용자에게 보이는 문구는 쉬운 표현으로 바꿀 수 있다.
- 공개 도구 안에 `star_internal` 질문이나 내부 스타 제작 UI를 넣지 않는다.

`public_easy`의 공개 `DESIGN.md` 언어 제안:

| 출력 섹션 | 표기 방식 |
| --- | --- |
| Core Idea | `핵심 아이디어 (Core Idea)` |
| Visual Theme | `시각 분위기 (Visual Theme)` |
| Color System | `색상 시스템 (Color System)` |
| Typography | `글자 기준 (Typography)` |
| Layout / Output Rules | `사용처별 규칙 (Output-Specific Rules)` |
| Imagery Rules | `이미지 기준 (Imagery Rules)` |
| Do / Don't | `해야 할 것 / 피해야 할 것 (Do / Don't)` |
| Update Rule | `업데이트 규칙 (Update Rule)` |

본문은 한국어로 작성하고, 영어 섹션명은 AI 도구와 기존 `DESIGN.md` 생태계가 알아보기 위한 병기값으로만 둔다.

## 3. `star_internal` 모드 질문 12개

대상:

- HAM MEDIA 별자리 홈페이지의 각 별
- 햄PD와 Codex가 내부 제작용으로 다루는 별별 디자인 소스

방향:

- 단순 디자인 브리프가 아니라 별별 기억과 홈페이지 구조를 반영한다.
- `DESIGN.md`와 `research_memo.md`를 분리한다.
- 공개 가능한 내용과 내부 참고 내용을 구분한다.
- 사진, 글, 스탬프, 별 코드, 지도, 다른 별 연결까지 고려한다.
- 12개 질문은 `SKILL.md`에 운영 기준으로 넣는다.
- 실제 질문지와 메모 템플릿은 별도 파일로 분리한다.

| 번호 | 질문 | DESIGN.md 연결 | research_memo.md 연결 |
| --- | --- | --- | --- |
| S1 | 이 별은 무엇이 아닌가? | Core Idea, Do / Don't, Imagery Rules | 해석 근거, 제외한 프레이밍 |
| S2 | 이 별은 햄PD의 어떤 기억인가? | Core Idea, HAM MEDIA Connection | 답변 원문, 사적 기억의 맥락 |
| S3 | 첫 화면에서 방문자가 무엇을 느껴야 하나? | Visual Theme, First Screen / Hero | 감정 판단 근거 |
| S4 | 대표 사진은 무엇이고 왜 대표인가? | Hero image direction, Imagery Rules | 사진 출처, 선정 이유, 후보와 탈락 이유 |
| S5 | 색은 어떤 사진, 사물, 기억에서 왔나? | Color System, Color Rules | 색상 근거, HEX 불확실성, 실제 샘플 여부 |
| S6 | 포인트 글자는 어떤 감각이어야 하나? | Typography, Type Rules | 폰트 후보, 로컬 경로, 라이선스 확인 |
| S7 | 스탬프와 별 코드는 어떤 역할인가? | Components, First Screen, Arrival Stamp | 스탬프 파일 출처, 별 코드 의미, 파일 위치 |
| S8 | 글 / 사진 / 지도 / 다른 별 중 무엇이 중심인가? | Star Doors, Components, Map Direction | 제작 우선순위, 아직 준비되지 않은 자료 |
| S9 | 공개하면 안 되는 사적 요소는 무엇인가? | DESIGN.md에는 직접 노출하지 않음 | Excluded From Public DESIGN.md |
| S10 | 사용할 수 있는 실제 자료는 어디에 있나? | Imagery Rules, Components | source list, asset provenance |
| S11 | HAM MEDIA 메인과 어떤 문장으로 연결되는가? | HAM MEDIA Connection, Copy Rules | 연결 문장 후보와 선택 이유 |
| S12 | 아직 확정되지 않은 것은 무엇인가? | Update Rule, TODO 표시 | Pending Ham PD Review |

`star_internal` 모드의 기본 출력 폴더 계약:

```text
<star_slug>/
  DESIGN.md
  README.md
  assets/
    fonts/
    stamps/
  research/
    <star_slug>_answers.md
    research_memo.md
```

선택 생성물:

```text
research/
  answers.json
  DESIGN.raw.md
  research_memo.generated.md
```

`star_internal` 템플릿 분리 제안:

- `SKILL.md`: 언제 이 모드를 쓰는지, 폴더 계약, 공개/내부 분리 원칙, 12개 운영 질문을 담는다.
- `assets/STAR_DESIGN_TEMPLATE.md`: 공개 가능한 별 전용 `DESIGN.md` 골격만 담는다.
- `assets/STAR_QUESTIONS_TEMPLATE.md`: 실제로 햄PD에게 물을 12개 질문지 원문을 담는다.
- `assets/STAR_RESEARCH_MEMO_TEMPLATE.md`: 답변 원문, 자료 출처, 제외 사유, Pending Review를 기록하는 메모 골격을 담는다.
- `assets/STAR_ANSWERS_TEMPLATE.md`: 필요하면 `<star_slug>_answers.md`의 작성 형식을 따로 둔다.

이렇게 나누면 `SKILL.md`는 운영 기준으로 가볍게 유지되고, 질문 문구와 메모 구조는 템플릿에서 독립적으로 조정할 수 있다.

## 4. 질문별 출력 위치 원칙

### `public_easy`

`public_easy`는 외부 사용자에게 파일 수를 늘리지 않는 방향이 기본이다.

- 기본 ZIP: `사용법.txt`, `답변+프롬프트.md`
- API 생성 ZIP: `사용법.txt`, `DESIGN.md`, `VISUAL_STYLE_SHEET.html`
- 별도 `research_memo.md`는 기본 생성하지 않는 것으로 확정한다.
- 필요하면 선택 출력으로 `답변원본.md`만 검토한다.
- `답변원본.md`는 사용자의 원답 보관용이며, 내부 판단 근거나 비공개 메모를 담는 `research_memo.md` 역할을 하지 않는다.
- 공개 `DESIGN.md` 본문은 한국어를 기본으로 하고, 섹션명에 영어를 병기한다.

`public_easy` 질문은 모두 `DESIGN.md`에 직접 들어가는 값이 아니라, 아래 결정값으로 변환되어 들어간다.

- P1, P8 -> Output-Specific Rules
- P2 -> Audience, Accessibility, Copy Rules
- P3, P6 -> Visual Theme, Color System, Typography
- P4, P7 -> Do / Don't, Imagery Rules, Risk Rules
- P5 -> Logo / Brand Mark, Components, Fixed Elements

### `star_internal`

`star_internal`은 `DESIGN.md`와 `research_memo.md`를 반드시 분리한다.

- 공개 가능한 시각 규칙 -> `DESIGN.md`
- 답변 원문, 판단 근거, 사적 요소, 제외 이유 -> `research/research_memo.md`
- 스탬프/폰트/사진 출처 -> `research/research_memo.md`와 `README.md`
- 사용 가능한 파일 자체 -> `assets/`
- 공개하면 안 되는 내용 -> `DESIGN.md`에 쓰지 않고 `research_memo.md`의 `Excluded From Public DESIGN.md`에만 기록

## 5. TODO / adjustable / CONFLICT 처리 기준

### TODO

`TODO`는 필수 판단이 비어 있어서 다음 단계로 넘기면 안 되는 경우에 쓴다.

사용 기준:

- 필수 질문이 비어 있음
- 대표 사진이 아직 결정되지 않음
- 별 코드 또는 스탬프 파일이 확인되지 않음
- 폰트 사용 가능 여부가 확인되지 않음
- 공개 가능 여부를 햄PD가 확인해야 함
- 홈페이지 적용 전에 필요한 자료 위치가 불명확함

표기 예:

```md
<!-- TODO: Ham PD review required - 대표 사진 확정 필요 -->
```

### adjustable

`adjustable`은 초안 작성에는 쓸 수 있지만 확정값으로 주장하면 안 되는 경우에 쓴다.

사용 기준:

- 사용자가 정확한 HEX를 주지 않았고 분위기만 말함
- 폰트명이 아니라 글자 느낌만 말함
- 간격, 크기, 비율을 임시로 제안함
- 실제 샘플에서 뽑은 값이 아니라 추정값임
- 공개 모드에서 AI가 합리적 기본값을 제안함

표기 예:

```md
Primary Blue `#2F6FDB` (adjustable draft)
```

### CONFLICT

`CONFLICT`는 답변끼리 동시에 만족하기 어려운 경우에 숨기지 않고 드러낸다.

사용 기준:

- 좋아하는 예시와 싫어하는 예시가 같은 방향을 가리킴
- 피하고 싶은 색을 대표 색으로도 적음
- `고급스럽게`와 `귀엽게`처럼 우선 톤이 충돌함
- 공개하면 안 된다고 한 자료가 대표 자료로도 지정됨
- 상표/저작권 리스크가 있는 표현을 사용하고 싶다고 답함
- 내부 스타 모드에서 사적 기억을 강조해야 하지만 공개 노출은 금지됨

표기 예:

```md
<!-- CONFLICT: 대표 사진으로 지정했지만 공개 금지 요소가 포함됨.
     Resolve before visual style sheet generation. -->
```

### 처리 우선순위

1. `CONFLICT`는 숨기지 않는다.
2. `TODO`는 다음 확인 항목으로 남긴다.
3. `adjustable`은 초안값으로 허용하되 확정값처럼 쓰지 않는다.
4. 공개 불가 정보는 `DESIGN.md`보다 `research_memo.md` 분리를 우선한다.
5. 답변에 없는 값을 최종 결정처럼 만들지 않는다.

## 6. 1차 구현 시 수정할 파일과 수정하지 않을 파일

### 1차 구현 시 수정할 파일

`public_easy` 쪽:

- `09_design-brief-form/index.html`
  - 첫 화면 질문을 8개 핵심 질문으로 재정리
  - 기존 세부 질문은 삭제하지 않고 `고급 질문` 접기 영역으로 이동
  - 프롬프트를 `public_easy`용으로 단순화
  - 공개 `DESIGN.md`를 한국어 본문 + 영어 섹션명 병기 구조로 생성
  - `research_memo.md` 기본 생성은 추가하지 않음
  - 선택 출력으로 `답변원본.md`가 필요한지 UI/ZIP 구조만 검토
- `09_design-brief-form/README.md`
  - 공개 도구의 목적과 결과물 설명 갱신
  - `research_memo.md`를 기본 생성하지 않는다는 공개 모드 원칙 명시

`star_internal` 쪽:

- `.agents/skills/ham-star-design-md-maker/SKILL.md`
  - 내부 스타 모드 질문 12개를 운영 기준으로 추가
  - `DESIGN.md` / `research_memo.md` 경계 강화
  - 실제 질문 문구와 메모 형식은 템플릿 파일을 보라고 안내
- `.agents/skills/ham-star-design-md-maker/assets/STAR_DESIGN_TEMPLATE.md`
  - 내부 스타용 출력값을 12개 질문 매핑에 맞게 조정

추가할 파일:

- `.agents/skills/ham-star-design-md-maker/assets/STAR_QUESTIONS_TEMPLATE.md`
  - 실제 내부 스타 질문지 12개 원문을 분리 보관
- `.agents/skills/ham-star-design-md-maker/assets/STAR_RESEARCH_MEMO_TEMPLATE.md`
  - 내부 메모 구조를 표준화할 때 사용
- `.agents/skills/ham-star-design-md-maker/assets/STAR_ANSWERS_TEMPLATE.md`
  - 필요 시 `<star_slug>_answers.md` 원답 형식 표준화용으로 검토

### 다시 제안하는 1차 구현 범위

1차 구현은 모드를 섞지 않고, 문서/템플릿/공개 폼의 질문 표시 방식까지만 다룬다.

1. `public_easy` 공개 폼 정리
   - `index.html`에서 8개 핵심 질문을 기본 노출한다.
   - 기존 질문은 삭제하지 않고 고급 질문 접기 영역으로 보존한다.
   - `DESIGN.md` 생성 프롬프트를 한국어 본문 + 영어 섹션명 병기로 바꾼다.
   - `research_memo.md` 생성은 넣지 않는다.

2. `star_internal` 스킬 기준 보강
   - `SKILL.md`에 12개 질문을 운영 기준으로 넣는다.
   - 실제 질문지는 `STAR_QUESTIONS_TEMPLATE.md`로 분리한다.
   - 메모 구조는 `STAR_RESEARCH_MEMO_TEMPLATE.md`로 분리한다.
   - `STAR_DESIGN_TEMPLATE.md`는 공개 가능한 `DESIGN.md` 골격만 유지한다.

3. 생성기 쪽은 보류
   - `questions.json`, `parse_answers.py`, `generate_design_md.py`는 1차 구현에서 수정하지 않는다.
   - 1차 적용 후 질문 스키마가 안정되면 `questions.public.json`, `questions.star_internal.json` 분리를 별도 단계로 검토한다.

### 1차 구현 시 수정하지 않을 파일

- `05_HAM_DesignStudio/tools/design-md-generator/questions.json`
  - 바로 덮지 않는다.
  - `questions.public.json`, `questions.star_internal.json` 분리 여부는 스키마 확정 뒤 결정한다.
- `05_HAM_DesignStudio/tools/design-md-generator/parse_answers.py`
  - 모드별 질문 스키마가 확정되기 전에는 수정하지 않는다.
- `05_HAM_DesignStudio/tools/design-md-generator/generate_design_md.py`
  - 출력 계약이 확정되기 전에는 수정하지 않는다.
- 기존 별 폴더의 `DESIGN.md`
  - `camera_star`, `bicycle_star`, `bike_star`, `food_star`, `travel_star`는 1차 계획 단계에서 수정하지 않는다.
- HAM MEDIA 홈페이지 파일
  - 별 페이지 실제 HTML/CSS 적용은 이 계획의 범위가 아니다.
- 공개 폼에 내부 스타 모드 UI 추가
  - 두 모드를 한 화면에 합치지 않는다.

## 1차 구현 전 확인할 점

- 공개 사용자용 `DESIGN.md` 초안은 한국어 본문 + 영어 섹션명 병기로 진행한다.
- `public_easy`에서 `research_memo.md`는 기본 생성하지 않는다.
- `답변원본.md` 선택 출력이 실제로 필요한지 결정한다.
- `star_internal`의 12개 질문은 `SKILL.md`에 운영 기준으로 넣고, 실제 질문/메모 템플릿은 별도 파일로 분리한다.
- `questions.json` 분리 이름을 정한다: 예) `questions.public.json`, `questions.star_internal.json`.
- `camera_star`처럼 `research_memo.md`가 없는 기존 별을 나중에 소급 보강할지 결정한다.

## 실사용 테스트 후 수정 후보

2026-06-06 가성비 뷰티 유튜버 예시로 기본 질문 / 고급 질문 비교 테스트를 진행하면서 아래 후보를 발견했다.

1. 색상 HEX 추출 보강
   - 현재 `VISUAL_STYLE_SHEET.html` 생성 로직이 `#FFF8F0` 같은 6자리 HEX를 `#FFF`처럼 앞 3자리로 잡는 경우가 있다.
   - 다음 수정 때 6자리 HEX를 우선 인식하도록 정규식을 조정한다.

2. 타이포그래피 역할 추출 보강
   - `메인 서체`, `제목 서체`, `가격 배지`, `긴 설명`처럼 여러 역할을 적어도 스타일시트에는 1개만 잡히는 경우가 있다.
   - 다음 수정 때 한국어 역할명과 배지/가격/본문 역할을 더 잘 읽도록 추출 규칙을 보강한다.

3. 고급 질문 안내 강화
   - 기본 8문항만으로도 방향은 잡히지만, 색상/폰트/컴포넌트 품질은 고급 질문 답변이 있을 때 확실히 좋아진다.
   - 공개 화면에 "색, 폰트, 썸네일 모양까지 정하고 싶으면 고급 질문을 열어주세요"라는 안내를 더 분명히 넣는 것을 검토한다.

## 2026-06-06 실제 폼 검증 메모

30대 여성 가성비 뷰티용품 리뷰 유튜버 예시로 `09_design-brief-form` 실제 화면을 다시 검증했다.

검증 방식:

- 로컬 서버: `http://127.0.0.1:8112/`
- 1차 확인: Codex 인앱 브라우저로 기본 화면, 핵심 질문 입력, 고급 질문 입력, 가짜 키 오류 화면을 캡처
- 2차 확인: 임시 Chrome 프로필과 원격 디버깅으로 실제 페이지 함수, ZIP 다운로드, Gemini 요청 형태 확인
- 실제 Gemini 키는 전송하지 않음
- 가짜 키 `fake-test-key-not-real`로 오류 처리와 요청 형태만 확인

확인 결과:

- 기본 노출 질문은 8개이고, 진행률은 필수 핵심 질문 5개 기준으로 `0 / 5`에서 `5 / 5`로 정상 변경된다.
- 고급 질문은 기본 닫힘 상태이고, 기존 세부 질문 48개가 접기 영역에 보존되어 있다.
- 기본 질문만 입력해도 `답변+프롬프트.md` 안에 사용자의 색상 단서가 들어간다.
  - 예: `크림색`, `말린 장미색`, `네온 핑크`
- 고급 질문까지 입력하면 직접 지정한 색상과 폰트가 프롬프트에 들어간다.
  - 색상: `#FFF8F0`, `#D98295`, `#FF6B5E`, `#A8DCC2`, `#2B2420`
  - 폰트: `Pretendard`, `Pretendard Regular`, `Pretendard ExtraBold`, `가격 배지용 굵은 산세리프`
- 키 없이 ZIP 다운로드는 실제 Chrome에서 성공했다.
  - ZIP 파일명: `뷰티지갑-디자인브리프.zip`
  - 포함 파일: `사용법.txt`, `답변+프롬프트.md`
  - `research_memo.md` 파일은 생성되지 않는다.
- `답변+프롬프트.md` 안에는 `research_memo.md`를 만들지 말라는 규칙 문장이 들어간다.
  - 따라서 문자열 검색에는 `research_memo`가 잡히지만, 실제 출력 파일로 생성되는 것은 아니다.
- Gemini 키 입력칸은 `type="password"`, `autocomplete="off"`, `spellcheck="false"`이다.
- 키는 `localStorage`나 `sessionStorage`에 저장되지 않았다.
- `여기서 만들기`를 누르면 Gemini 요청은 아래 형태로 나간다.
  - `POST https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash:generateContent?key=...`
  - 요청 본문에는 `buildDesignPrompt()` 결과가 들어간다.
- 가짜 키 테스트에서는 오류 토스트가 정상 노출되고, `DESIGN.md` 미리보기와 디자인가이드 ZIP 버튼은 활성화되지 않았다.

키 사용 방식 비교:

- `09_design-brief-form/index.html`
  - 공개 사용자 입력 키를 브라우저 메모리에서만 읽고, Gemini API URL의 `?key=` 값으로 전송한다.
  - 앱 자체 저장소에는 저장하지 않는다.
- `11_youtube-idea-finder-public/index.html`
  - 공개 도구로서 사용자가 입력한 키를 비슷하게 Gemini API URL의 `?key=` 값으로 전송한다.
- `01_youtube-channel-report/github-pages/index.html`
  - 페이지 상태 객체에 키를 임시 저장하고, Gemini API URL의 `?key=` 값으로 전송한다.
  - UI 문구의 `저장`은 브라우저 영구 저장이 아니라 현재 페이지 상태 저장에 가깝다.
- `13_youtube-trend-finder/ai_report.py`
  - 로컬 `.env`의 `GEMINI_API_KEY`를 읽고, `x-goog-api-key` 헤더로 전송한다.
- `05_HAM_DesignStudio/tools/kim-upload-generator/server.js`
  - 로컬 `.env`의 `GEMINI_API_KEY`를 읽고, Gemini API URL의 `?key=` 값으로 전송한다.

추가 수정 후보:

1. 다운로드 성공 토스트 정확화
   - 현재 `downloadZip()`이 JSZip 로딩 실패로 조기 반환해도 호출부에서 성공 토스트를 띄울 수 있는 구조다.
   - 다음 수정 때 `downloadZip()`이 성공 여부를 반환하고, 성공일 때만 "다운로드했습니다"를 띄우도록 바꾼다.

2. 공개 도구 키 전송 방식 검토
   - 현재 공개 HTML 도구는 `?key=` 쿼리 방식이다.
   - 내부 Python 도구처럼 `x-goog-api-key` 헤더 방식으로 바꿀 수 있는지 CORS와 브라우저 동작을 확인한다.
   - 가능하면 URL/네트워크 로그에 키가 남는 면을 줄이기 위해 헤더 방식을 검토한다.

3. JSZip CDN 의존성 안내
   - 키 없이 ZIP 받기는 JSZip CDN 로딩에 의존한다.
   - 인터넷 연결 또는 CDN 차단 시 ZIP 생성이 실패할 수 있으므로, 오류 문구와 fallback 안내를 더 분명히 한다.

## 2026-06-06 실제 Gemini 키 검증 메모

사용자 승인 후 로컬 `.env`의 `GEMINI_API_KEY`를 사용해 실제 생성 흐름을 검증했다.
키 값은 출력하지 않았고, 임시 Chrome 프로필에서만 사용했다.

검증 결과:

- `09_design-brief-form`의 실제 `여기서 만들기` 버튼은 로컬 키로 Gemini API 호출까지 진행된다.
- 현재 폼 기본 모델인 `gemini-2.5-flash`는 3회 시도 모두 아래 오류를 반환했다.
  - `This model is currently experiencing high demand. Spikes in demand are usually temporary. Please try again later.`
- 이는 키 누락/키 오류가 아니라 모델 가용성 문제로 보인다.
  - 같은 키로 모델 목록 조회 성공
  - 같은 폼 프롬프트를 `gemini-2.5-flash-lite`에 전달했을 때 생성 성공

fallback 생성 결과:

- 기본 질문만 사용한 `public_easy` 프롬프트
  - 사용 모델: `gemini-2.5-flash-lite`
  - `DESIGN.md` 생성 성공
  - 섹션 10개가 한국어 본문 + 영어 섹션명 병기 구조로 생성됨
  - 색상은 답변의 분위기에서 추론됨
  - 예: `Warm Ivory`, `Base White`, `Dried Rose`
- 고급 질문까지 사용한 프롬프트
  - 사용 모델: `gemini-2.5-flash-lite`
  - `DESIGN.md` 생성 성공
  - 사용자가 직접 적은 색상과 폰트가 더 정확히 반영됨
  - 색상: `#FFF8F0`, `#D98295`, `#FF6B5E`, `#A8DCC2`, `#2B2420`
  - 폰트: `Pretendard`, `Pretendard Regular`, `Pretendard ExtraBold`

추가로 확정된 문제:

1. 현재 모델 오류 문구가 그대로 영어로 노출된다.
   - 사용자는 키가 틀린 것인지, 모델이 바쁜 것인지 구분하기 어렵다.
   - 다음 수정 때 high demand / quota / invalid key / network 오류를 한국어 사용자 메시지로 분기한다.

2. 기본 모델 fallback 전략이 없다.
   - `gemini-2.5-flash`가 일시적으로 막히면 공개 폼에서 생성이 끝까지 진행되지 않는다.
   - 다음 수정 때 `gemini-2.5-flash-lite` 또는 `gemini-2.0-flash` fallback을 검토한다.
   - 단, 공개 문구에는 "기본 모델이 바쁘면 가벼운 모델로 다시 시도" 정도로 쉽게 설명한다.

3. 시각 스타일시트 HEX 추출 문제는 실제 Gemini 결과에서도 재현된다.
   - `DESIGN.md`에는 `#FFF8F0`, `#D98295`처럼 6자리 HEX가 정상 생성된다.
   - `VISUAL_STYLE_SHEET.html`에서는 `#FFF`, `#D98`, `#FF6`, `#A8D`처럼 3자리로 잘리는 경우가 있다.
   - 다음 수정에서 가장 먼저 고칠 항목이다.

4. 고급 질문은 실제 결과 품질에 분명한 차이를 만든다.
   - 기본 질문만 있으면 색상과 폰트가 AI 추론값으로 채워진다.
   - 고급 질문을 쓰면 색상, 폰트, 사용처별 규칙이 더 직접적으로 반영된다.
   - 공개 UI에서는 고급 질문을 강요하지 않되, "정확한 색/폰트까지 원하면 열어보기" 안내를 강화하는 것이 좋다.

## 2026-06-07 수정 후 10회 반복 테스트 메모

확정 문제를 먼저 수정한 뒤 5분 간격으로 10회 반복 테스트를 다시 진행했다.
테스트 결과물은 폐기 가능한 임시 폴더에만 저장했다.

적용한 수정:

- `gemini-2.5-flash` 혼잡 시 `gemini-2.5-flash-lite`, `gemini-2.0-flash` 순서로 fallback 재시도
- Gemini 오류 메시지 한국어화
  - invalid key
  - high demand
  - quota / rate limit
  - network error
- 색상 추출에서 6자리 HEX를 3자리 HEX보다 우선 인식
- 색상 표 형태의 `DESIGN.md`도 토큰 / 역할 / HEX로 분리해 추출
- JSZip 로딩 실패 시 성공 토스트를 띄우지 않도록 다운로드 성공 여부 반환

10회 반복 결과:

- 총 시나리오 수: 20개
  - `core`: 10개
  - `advanced`: 10개
- 성공: 17개
- 실패: 3개
- 성공한 17개는 모두 `good`
- 평균 점수: 102
- `VISUAL_STYLE_SHEET.html`의 HEX 잘림 재발: 0건
- 기본 모델 성공: 4건
- fallback 성공: 13건

실패 원인:

- 9회차 `advanced` 1건 실패
- 10회차 `core`, `advanced` 2건 실패
- 모두 결과 품질 문제가 아니라 Gemini 무료 티어 429 quota 오류
- 오류 메시지에는 약 40초 뒤 재시도하라는 안내가 포함됨
- 반복 테스트처럼 짧은 시간에 여러 모델을 순차 호출하면 5분 간격이어도 무료 요청 한도에 닿을 수 있다.

판단:

- 결과 품질을 확인하기 위해 20회까지 늘릴 필요는 낮다.
- 17개 성공 결과가 모두 `good`이고, 핵심 버그였던 HEX 잘림은 0건으로 사라졌다.
- 추가 20회 테스트를 한다면 품질 검증보다 quota / retry-after / 호출량 관리 검증이 된다.

추가 수정 후보:

1. fallback 호출 수 제한
   - 공개 사용자 1회 생성에서는 fallback이 유용하다.
   - 반복 테스트나 quota가 낮은 키에서는 fallback이 요청 수를 빠르게 늘릴 수 있다.
   - `quota` 오류는 fallback을 계속 돌리기보다 즉시 멈추고 재시도 시간을 안내하는 편이 낫다.
   - 2026-06-07 수정에서 `quota` 오류는 fallback하지 않도록 반영했다.

2. retry-after 안내 강화
   - Gemini 오류에 `Please retry in 40s`가 포함되면 사용자에게 "약 1분 뒤 다시 시도해주세요"라고 보여준다.
   - 2026-06-07 수정에서 초 단위 retry 안내를 분 단위 한국어 메시지로 변환하도록 반영했다.

3. 모델명 표시 문구 정리
   - 현재 fallback 성공 토스트는 `gemini-2.5-flash-lite`처럼 모델명을 그대로 보여준다.
   - 공개 사용자에게는 "가벼운 모델로 다시 시도했습니다" 정도가 더 쉽다.
