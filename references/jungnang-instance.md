# 중랑정책미디어 인스턴스 (첫 선례)

발행처 중랑정책주방(정책실) · 발행인 김현성(태하) 중랑구 정책실장 · 보고는 발행인 본인에게만.
창간 2026-11-11(수) MORNING Vol.34 창간호 + WEEKLY Vol.6 창간 특집. 예비호 파일럿 10/29 ① ~ 11/10 ⑨(평일), 토·일 휴간(2026-10-29 확정).

## 호수

MORNING: 10/29 Vol.25 ①, 10/30 Vol.26 ②, 11/2 Vol.27 ③, 11/3 Vol.28 ④, 11/4 Vol.29 ⑤, 11/5 Vol.30 ⑥, 11/6 Vol.31 ⑦, 11/9 Vol.32 ⑧, 11/10 Vol.33 ⑨, 11/11 Vol.34 창간호(04:44 발행, 정정 0), 11/12 Vol.35, 이후 평일마다 +1. 호수 기준은 편집국 기록.
주간: 월 WEEKLY AX, 화 두부(넷째 화 PEOPLE, 첫 회 11/24), 수 WEEKLY '이번 주 침'. 11/2 WEEKLY AX Vol.4, 11/3 두부 Vol.4, 11/4 WEEKLY Vol.5, 11/9 WEEKLY AX Vol.5, 11/10 두부 Vol.5, 11/11 WEEKLY Vol.6 창간 특집.
창간 경과(2026-11-11): 창간은 일정대로 나갔다. 사이트 진열은 11/11 10:56(07:00 전 미달). 예비호 ⑥~⑨(11/5~11/10)는 Aside PC 공백으로 사이트에 진열되지 않았고(editions.json이 11/4 → 11/11), 그 기간 점검 메일·촉 수확·중간 평가·가부 판단 자료도 없다. 창간의 말은 편집국이 확정본을 드라이브·메일에서 찾지 못해 11/9 리허설 초안으로 썼다.

## 일정 (2026-10-30 개편, 창간 전 07:00 전 새 판)

| 단계 | 담당 | 시각 | 작업 |
|-|-|-|-|
| 촉 수확 | Aside → GPT | 평일 17:30 (금 → 월요일분) | Aside routine |
| MORNING | Claude | 매일 04:30 (주말은 휴간 알림만) | claude.ai 예약 작업 |
| WEEKLY AX (월) · 두부 (화) · WEEKLY (수) | Claude | 05:20 | claude.ai 예약 작업 |
| 진열·일일 점검 | Aside | 평일 06:20 | Aside routine |
| 노하우 스킬 반영 | Aside | 금 18:00 | Aside routine |
| 주간 통합·촉침 점검 / 월간 융복합 통합본 | Aside | 월 07:30 / 매월 말일 | Aside routine |

Claude 예약 작업 지침 맨 앞 블록 순서: [예비호 실험] → [문체와 촉 고르기] → [발행 시각] → 헌장 v1/v1.1 → 창간 일정 → 원래 편집국 지침. 바꾸기 전 지침은 tmp에 백업한다.

## 주소

- 사이트: https://jungnang-media.vercel.app (저장소 goodmorninghope-khs/jungnang-media, main 커밋 → Vercel 자동 배포 1~2분)
  - 주소 하나 원칙(2026-11-04 통합): 옛 리디자인 미리보기 주소 https://jungnang-media2.vercel.app 은 307로 본 주소에 넘긴다(Vercel Domains). 리디자인(MotionSites, 큰 제호·머리기사 먼저)은 main style.css에 들어갔다. 새 디자인을 시험할 때 브랜치 미리보기 도메인을 붙이면 새벽 진열(main)을 받지 못하니, 시험은 짧게 하고 끝나면 main에 합친 뒤 도메인을 Production이나 본 주소 리디렉트로 돌린다.
  - `data/editions.json`: 편집국 직송판 배열. app.js `loadLive()`가 제작실 피드와 함께 읽어, 같은 지면(series+날짜, 같은 날 여럿이면 제목이 가장 닮은 것)이 제작실에 있으면 본문·제목·공약은 편집국 판(정정판 포함)을 쓰고 제작실 id와 제작실에만 있는 칸은 남긴다(2026-11-04부터. 전에는 제작실 판이 오면 통째로 바뀌어 정정 전 본문이 보였다). 없으면 앞에 넣는다. 항목 예: id morning-20261030.
  - 공약 칩(app.js `pledgesOf`): 항목의 pledges 배열을 먼저 쓰고, 없을 때만 본문의 '날줄 공약N' → '닿는 공약' 구간(씨줄·'|' 앞까지, 'AX①' 제외) 순으로 읽는다(2026-11-04 고침).
  - 정정판 진열: editions.json 항목 body를 고치고 처음 판은 versions 맨 앞에 {label:'처음 판 · HH:MM', body}로, edition은 '편집국 직송판 · 정정', corrections.json에 kind '정정' 한 건(what·how·why·when·prev_version_link·source), chim-trace의 from.signal 제목도 맞춘다.
  - 오늘 면 '이번 주의 촉과 침'(app.js viewToday): 이번 주 판이 6개 미만이면 지난 촉과 침으로 채운다(FILL_TO=6, 침 최대 2, 2026-11-02).
  - 편집국 직송판 JSON에 11/5부터 weave 칸(["AX③×공약4", …]), 11/10부터 신호마다 brief 칸(중랑브리핑 기사 id)이 붙어 온다. 진열 때 지우지 않는다.
  - `data/{id}.webp`: 지면 이미지(Claude 대화의 files/…/preview, 896px webp).
  - 피드 rewrites(vercel.json): /feed/signal.json(GPT 제작실 data.json), /feed/aa/catalog.js(아궁이), /feed/chok/:file(GitHub inbox/chok).
- 규칙 원장: https://github.com/goodmorninghope-khs/jungnang-signal — shared/chokchim-charter.md(v1.1), pledge-map.md(공약 7대 비전), pilot-experiments.md(실험표), reference-hub.md(두 엔진 공통 참조), launch-pilot.md(파일럿·일정), convergence.md, two-engines.md, inbox/chok/.
- GPT 제작실(원본, 보통 09시 전후 갱신): https://jungnang-policy-media.goodmorninghope.chatgpt.site/data.json
- GPT 촉 레이더: ChatGPT 프로젝트 「09 중랑시그널·소포 편집실」의 고정 대화 1개
- Claude 드라이브 서고(07_시그널·소포/중랑 시그널 편집국): 01_회의록, 03_발행본, 04_신호창고, GPT자문 폴더

## 일일 점검 메일

제목 "[중랑정책미디어 창간 기획단] 일일 점검 YYYY-MM-DD · (예비호 ⓝ / 창간호 / Vol.N) · 실험 E?". 순서: ⓪ 진열 결과 ① 발행 결과 ② 지면 읽기 점검 ②-1 오늘의 실험 ③ 두 엔진 협업 ④ 사이트 ⑤ 조치·다듬어 볼 문장·발행인 판단 ⑥ 파일럿 누적표. 누적표는 점검 routine 메모리에서 이어 쓴다.

## 창간 가부 기준 (11/10 판단 자료, 결정은 발행인)

머리 외부 8호 이상 · 평가로 느껴질 표현 0 · 해외·국내 각 40% 이상(9호 합계) · 신호마다 닿는 공약 표시와 7대 비전 고루 · GPT 후보 매일 적재·채택 평균 1 이상 · 사이트 07:00 전 진열·오류 0 · 3분 읽기.
이정표: 11/6 1주차 중간 평가, 11/9 창간호 구성안(창간사 확정 기한 11/9), 11/10 가부 판단 자료. (2026-11-11 기준: 세 이정표 모두 Aside 쪽 자료가 만들어지지 않았다. 가부 결정 기록은 아직 찾지 못함.)
