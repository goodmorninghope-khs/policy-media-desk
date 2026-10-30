# 운영 노하우 (날짜 · 일어난 일 → 한 일 → 다음엔)

## 편집·운영 결정

- 2026-10-28 · Claude본과 GPT 별도본이 같은 자리에 겹쳐 실렸다 → '한 자리 한 엔진', GPT는 촉 레이더로 → 새 매체도 처음부터 자리별 엔진 하나.
- 2026-10-28 · WEEKLY 1~4호 머리가 모두 중랑 현안, 제목이 미비 지적형 → 헌장 '머리는 밖에서·외부 8:2' → 내부 현안은 주 1회 제안형 칸에만.
- 2026-10-29 · 해외 편중 우려 → 헌장 v1.1 해외 40 : 국내 40 균형, 솔루션 저널리즘, 조언 어조.
- 2026-10-30 · 사이트가 GPT 제작실 갱신(09시 전후)을 기다려 오늘 판이 늦게 떴다 → 편집국 직송판 data/editions.json을 먼저 진열하고 제작실 판이 오면 자동 교체 → 원본 피드에 매이지 않는 직송 경로를 처음부터.
- 2026-10-30 · 발행인 "창간 전 매일 07:00 전 새 판" → Claude 04:30·05:20, Aside 06:20 진열, 촉 수확 전날 17:30, "먼저 발행, 후속은 나중" 블록.
- 2026-10-30 · 발행인 "읽는 사람이 평가로 느끼지 않게, 촉은 구청장 공약과 주요 사항에 영향 줄 것" → 문체·촉 기준을 모든 지침 맨 앞에, 신호마다 '닿는 공약' 꼬리표.
- 2026-10-30 · 발행인 "예비호 기간 실험" → 실험표 한 파일 + 세 엔진 몫 + 측정. GPT에게 실험 의견을 물어 3개 반영(출처 도착, 주민 장면, 고정 참조 한 곳).

## 권한·환경

- 2026-10-30 · 사무실 PC에서 drive.google.com·docs.google.com이 ERR_SSL_PROTOCOL_ERROR로 막힌다 → 드라이브 작업은 Claude 커넥터에 맡기거나 발행인이 다른 기기에서.
- 2026-10-30 · Claude 예약 작업('자동' 권한)이 공개 저장소 clone·commit·push를 "공개 표면 생성"으로 거부 → '모든 승인 건너뛰기'는 Gmail 발송·삭제, 드라이브 공유·삭제, 캘린더 수정까지 확인 없이 열리고 작업별로 커넥터를 끌 수 없다 → 쓰지 않고 Aside 웹 업로드 + PC 상시 가동으로 정함. 시험용 GitHub 토큰은 바로 폐기.
- 2026-10-30 · 밤 20:00·02:00 Aside routine이 다음 날 07:4x에 돌았다(PC 꺼짐) → 새벽 작업은 PC 상시 가동 전제. 절전·최대절전은 이미 '사용 안 함'.
- GitHub fine-grained 토큰 만들기는 sudo 확인(이메일 코드)이 필요하고, 저장소 하나·Contents 쓰기로 범위를 좁힐 수 있다.

## 도구 요령

- Claude 예약 작업 편집: 작업 페이지 '더 많은 옵션' → '편집' 대화상자. 지침이 길면 snapshot이 16KB에서 잘리므로 `[role="dialog"] textarea` 중 값이 긴 것을 직접 fill. 시간은 '시간' 입력. 저장 후 새로고침해 '다음 실행'과 지침 첫 줄로 확인.
- Claude 실행 기록: 작업 페이지 '오늘 오전 H:MM' 링크 → chat 페이지 main innerText. 지면 PNG는 img src `.../files/{id}/preview`(webp, 896px)만 받아진다(contents·download는 404).
- 새 예약 작업: '새 작업' → '직접 설정'.
- GitHub 웹 업로드: `upload/main/{폴더}`에서 input[type=file], 1~2개씩. 바로 이어 올리면 "Commit failed"가 날 수 있다 → 업로드 페이지를 다시 열어 재시도. 반영은 commits 페이지나 raw로 확인. 없는 하위 폴더 업로드 경로는 피한다.
- ChatGPT 대화 입력: 보이는 div.ProseMirror(nth(1)) 클릭 → keyboard.insertText → `button[aria-label="보내기"]`. 답은 /api/auth/session accessToken으로 /backend-api/conversation/{id} mapping에서 마지막 assistant(status finished_successfully). U+E000~U+F8FF 문자와 'genui{…}}' 표식을 지운다.
- Aside routine 수정은 routine_update에 지침 전문을 다시 넣어야 한다(부분 수정 API 없음). 바꾸기 전 aside.routines.get(id).prompt를 tmp에 백업.
- Aside routine의 rrule을 바꾸면 오늘 남은 회차가 사라질 수 있다 → 필요하면 같은 일을 하는 1회성 routine을 따로 건다.

## 2026-10-30 중랑브리핑(보도자료 기반 쌍둥이) 시범판

- 2026-10-30 · GPT·Claude에 같은 질문으로 망우로 견본 기사를 받았더니 GPT는 다른 언론사 사진을 붙였고, Claude는 원문 대신 받아쓴 언론 기사로 사실을 확인했다 → '1차 출처는 기관 원문 하나, 사진은 원문 첨부만' 규칙으로 정하고 숫자·따옴표 문구 자동 대조를 사이트에 넣었다.
- 2026-10-30 · Claude가 짚은 공직선거법 제86조 제5항을 조문으로 확인: 지자체 활동상황 홍보물은 분기별 1종 1회, 직원 업무용은 예외 → 매일 나가는 브리핑은 직원용으로 시작하고 주민 공개는 선관위 질의 뒤.
- 2026-10-30 · 원문 첨부 사진에 기업 로고, 청사 전경, 지난해 행사 사진, 청소년 얼굴 근접 사진이 섞여 있었다 → 사진을 고르는 규칙을 두고, 쓰지 않는 사진은 저장소에도 올리지 않는다(한 번 업로드 목록에 잘못 담겨 커밋 전에 뺐다).
- 도구 요령: 중랑구청 게시판은 REPL fetch가 실패해 탭으로 열어 읽었고(.view_box, #dbdata), 사진 서버(jnadm)는 REPL fetch로 받아졌다. 이미지 주소로 goto하면 시간 초과.
- 도구 요령: Aside Playwright에는 route()가 없고 file:// 열기와 로컬 HttpListener도 막힌다 → 미리보기는 about:blank에 CSS·JS·데이터를 인라인하고 사진을 data URL로 바꿔 document.write.
- 도구 요령: GitHub 새 하위 폴더는 new/main?filename=폴더/README.md&value=… 로 먼저 만들고 upload/main/폴더에 올린다. 여러 장을 한 번에 올리고 바로 커밋하면 chrome-error가 나며 커밋이 안 될 수 있다 → 5장씩, 목록 확인 뒤 커밋.
- 도구 요령: Vercel 새 프로젝트 첫 배포는 이메일 보안코드(5분)를 요구한다 → Gmail에서 'Your Vercel security code'를 읽어 넣으면 6자리 입력과 함께 자동 제출된다.
