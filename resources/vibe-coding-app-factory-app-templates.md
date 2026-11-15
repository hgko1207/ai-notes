# 한 달에 앱 30개를 만든 "앱 공장" — 구조와 공개 템플릿 정리

> 한 줄 요약: 15년 차 개발자 임상진 님이 퇴사 후 한 달 동안 앱 30개를 만들며 쓴 "앱 공장" 방식과, 그대로 가져다 쓸 수 있게 공개한 모노레포 템플릿(app-templates)을 정리합니다.

## 핵심 요약

- 속도의 비결은 코딩 실력이 아니라 **AI가 멈추지 않고 일할 수 있는 환경을 먼저 만든 것**이라고 합니다
- 앱마다 **ROADMAP.md를 먼저** 쓰고, AI에게는 로드맵을 **한 단계씩** 맡긴 뒤 사람이 검토하는 방식입니다
- 개인정보처리방침, 지원 홈페이지, 배포 스크립트, 스토어 스크린샷처럼 **앱마다 반복되는 부품을 한 번 만들어 재사용**합니다
- 템플릿 저장소는 **0BSD 라이선스**라 출처 표기 없이 복사, 수정, 상업적 사용이 모두 가능합니다
- 작성자의 결론은 "쓸모없는 앱 30개보다 문제를 푸는 앱 1개. 바이브 코딩의 장점은 대량생산이 아니라 **빠른 검증**"입니다

## 본문

### 1. 장비: 병목은 AI가 아니라 빌드였습니다

M1 맥북 프로 16GB로 시작했지만 AI가 코드를 만드는 속도를 빌드가 따라가지 못해서, M5 맥북 프로(48GB)로 바꿨다고 합니다. iOS·macOS 네이티브 앱이라 Xcode 빌드가 무거웠던 영향이 큽니다. 웹 앱 위주라면 같은 병목은 잘 생기지 않습니다.

### 2. 스토어 계정과 비용

| 항목 | 내용 |
|---|---|
| Apple Developer Program | 연 12만 9천 원. 개인 기기 테스트는 무료라 출시 때 가입해도 됩니다 |
| Apple Ads 새 계정 크레딧 | 100달러 광고 크레딧으로 출시 직후 키워드 광고를 시험해 볼 수 있습니다 |
| Google Play 개발자 등록비 | 1회 약 2만 5천 원 |
| Google Play 개인 계정 테스트 조건 | 출시 전 앱마다 **12명이 14일 연속** 비공개 테스트에 참여해야 합니다 |
| 사업자(조직) 계정 | D-U-N-S 번호(국제 사업자 등록번호)로 조직 계정을 만들면 12명·14일 조건이 면제된다고 합니다 |

어디까지 공식으로 확인됐는지는 아래 "사실 확인" 표에 정리했습니다.

### 3. AI 도구 설정

- Claude: 최신 Opus 계열, 추론을 높게, 가능하면 묻지 않는 모드(Auto Mode, Don't Ask Mode)
- Codex: 최신 GPT 계열, reasoning high, Full Access Mode
- **단, 개인 프로젝트 기준입니다.** 회사 코드나 고객 데이터가 있는 저장소는 권한을 낮추고 승인 절차를 유지하라고 분명히 적어 두었습니다

### 4. 로드맵 먼저, 그다음 한 단계씩 자율 실행

"앱 만들어줘"라고만 하면 결과가 흔들린다고 합니다. 그래서 먼저 로드맵을 만듭니다.

1. "이 앱의 로드맵을 작성해줘" → 목적, 핵심 기능, 디자인 원칙, 개발 순서, **출시 전 체크리스트**가 담긴 ROADMAP.md
2. "/goal 로드맵 1단계를 끝까지 진행해줘" → AI가 한 단계를 스스로 끝까지 진행
3. 사람이 검토하고 고친 뒤 다음 goal을 줍니다

작성자 표현으로는 "AI 자율주행은 방치가 아니라 목표를 주고 경로를 점검하는 방식"입니다.

### 5. 모노레포와 재사용

앱마다 폴더를 흩어 두지 않고 하나의 큰 저장소에 모읍니다.

```
utilities/timer
utilities/memo
utilities/calculator
apps-deployment/   ← 공통 배포 스크립트
infra/             ← 홈페이지 호스팅
```

앱스토어 스크린샷 생성, 개인정보처리방침, 지원 홈페이지, 공통 디자인, 배포 스크립트, 가격 설정, 빌드 명령어를 매번 새로 만들지 않고 다른 앱에서 계속 가져다 씁니다. "재사용성이 곧 속도"라는 설명입니다.

### 6. 앱 홈페이지는 화려할 필요가 없습니다

스토어에 내려면 개인정보처리방침과 지원 링크가 있는 홈페이지가 필요합니다. 처음이라면 Netlify나 Vercel 같은 무료 호스팅이면 충분합니다. 작성자 앱 홈페이지(Dimmer, Cling)가 예시입니다. 앱 소개, 스토어 버튼, 개인정보처리방침, 지원 링크만 있는 한 장짜리 페이지입니다.

### 7. 공개 템플릿 app-templates 들여다보기

| 들어 있는 것 | 내용 |
|---|---|
| `scripts/new-app.mjs` | 새 앱 폴더와 README, AGENTS, CLAUDE, ROADMAP, 홈페이지, 개인정보처리방침을 한 번에 생성 |
| `.claude/skills/`, `.codex/skills/` | `/new-app`, `/ios-deploy`, `/flutter-deploy`, `/macos-deploy`를 두 도구에 같은 이름으로 제공 |
| `apps-deployment/` | App Store Connect, Google Play 공식 API로 메타데이터, 스크린샷, TestFlight, 심사 제출을 자동화하는 스크립트 30여 개 |
| `scripts/check-sensitive.mjs` | 본인 아이디, 이메일, API 키, 개인 키 패턴이 저장소에 들어갔는지 CI에서 검사 |
| `scripts/check-docs.mjs` | 앱마다 필수 문서 4종이 있는지, CLAUDE.md가 AGENTS.md를 가리키는지 검사 |
| `prompts/app-development-environment-setup.md` | Claude Code나 Codex에 붙여 넣으면 장비 점검부터 새 앱 생성, 호스팅 선택까지 단계별로 안내하는 프롬프트 |

눈여겨볼 규칙:

- **AGENTS.md가 기준 문서**이고 CLAUDE.md는 "AGENTS.md를 보라"는 한 줄만 둡니다. 다만 이렇게 글로만 가리키면 Claude Code는 AGENTS.md 내용을 **자동으로 읽지 않습니다**. CLAUDE.md에 `@AGENTS.md` 줄을 넣어 가져와야 시작할 때 함께 읽습니다 (아래 "사실 확인" 참고)
- 앱 빌드는 **한 번에 최대 3개까지만** 병렬로 돌리고, 나머지는 줄을 세웁니다
- 비밀 파일(.p8, keystore, 서비스 계정 JSON)은 저장소 밖 홈 폴더나 CI secret에 둡니다

## 사실 확인

| 주장 | 상태 | 근거 |
|---|---|---|
| 2023-11-13 이후 만든 Google Play 개인 계정은 앱마다 12명이 14일 연속 비공개 테스트를 해야 출시할 수 있다 | 공식 확인 | [Google Play 고객센터](https://support.google.com/googleplay/android-developer/answer/14151465) |
| Apple Ads 새 계정은 100달러 크레딧을 받는다. 판매 중인 앱 1개 이상, App Store Connect 연결이 필요하다 | 공식 확인 | [Apple Ads 도움말](https://searchads.apple.com/help/basic/0041-apple-search-ads-promo-credit/) |
| 조직(D-U-N-S) 계정은 12명·14일 조건이 면제된다 | 출처만 | 여러 외부 글. 공식 페이지에서는 찾지 못함 |
| D-U-N-S 발급에 수일에서 한 달 걸린다 | 출처만 | 외부 글 |
| Apple Developer 연 12만 9천 원, Google Play 등록비 약 2만 5천 원 | 출처만 | 작성자 글 |
| app-templates는 0BSD 라이선스다 | 공식 확인 | [app-templates 저장소](https://github.com/limsangjin12/app-templates) |
| Claude Code는 CLAUDE.md가 있으면 AGENTS.md를 따로 읽지 않는다. 같이 쓰려면 CLAUDE.md에서 `@AGENTS.md`로 가져와야 한다 | 공식 확인 | [Claude Code 메모리 문서](https://code.claude.com/docs/en/memory.md), 2026-11-14 직접 실험(파일 도구를 막은 새 대화가 가져온 AGENTS.md 내용을 그대로 답함) |

## 적용할 점

| 대상 | 할 일 | 상태 |
|---|---|---|
| team-ai-kit | setup에 AGENTS 방식 추가. 단, "보라"는 글 대신 CLAUDE.md 첫 줄 `@AGENTS.md`로 가져오게 함 | 적용함 (v0.4.0, 커밋 7ff89e5·84772fe) |
| team-ai-kit | 대화 압축 후 규칙 재주입 훅이 AGENTS.md 섹션도 다시 넣게 함 | 적용함 (v0.4.0) |
| cc-checkup | CLAUDE.md의 `@AGENTS.md`를 따라가 검증 명령·필수 섹션을 판정 | 적용함 (PR #18, 병합 64a62ae) |
| cc-checkup | CLAUDE.md 없이 AGENTS.md만 있는 저장소도 통과시키기 | 안 함 (이유: 키트가 이 경우 CLAUDE.md를 만들게 안내하고, 구버전 Claude Code는 AGENTS.md만으로는 읽지 못함) |
| team-ai-kit | `check-sensitive.mjs`처럼 공개 저장소에 개인 식별자·키가 들어갔는지 CI에서 검사 | 적용함, 체크 줄로만 (v0.5.0 `b1a3c67`: plan.md "출시 전 확인"에 "비밀값이 저장소와 배포 결과물에 없음" 줄). 자동 검사 CI는 검토 중 (키트에는 .env·키 파일 수정을 막는 훅만 있음. LLM 위키 개선 후보 "커밋 전 비밀정보 검사"와 같이 검토) |
| team-ai-kit | 출시 전에 처리방침·아이콘·스토어 자료처럼 앱마다 반복되는 것을 챙기게 하기 | 적용함 (v0.5.0 `b1a3c67`: setup이 저장소 종류별 "출시 전 확인" 목록을 plan.md에 넣음. 스토어 앱에는 구글 플레이 12명·14일 줄 포함) |
| 개인 프로젝트 | 스토어에 앱을 낼 때 구글 플레이 12명·14일을 일정에 넣고, Apple Ads 크레딧은 첫 앱 판매 뒤 사용 | 검토 중 (스토어 출시 계획이 생기면) |
| 개인 프로젝트 | ROADMAP.md 먼저 쓰고 한 단계씩 맡기기 | 안 함 (이유: 키트의 plan-feature와 plan.md가 이미 같은 역할) |
| 개인 프로젝트 | 앱 모노레포와 iOS·Android 배포 스크립트 | 안 함 (이유: 지금은 네이티브 앱 계획이 없고 웹 위주) |

## 마무리

글에는 작성자의 앱과 유튜브 채널 홍보가 섞여 있습니다. 그래도 유료 상품이나 제휴 링크는 없고, 실제로 돌아가는 템플릿을 0BSD로 공개했다는 점에서 참고 가치가 큽니다. 가장 기억할 말은 "빨리 만들고, 빨리 출시하고, 사용자 반응을 보고, 쓸모 있는 앱만 남긴다"입니다.

---
**출처**: [임상진 Threads 글 (15개 연속 글)](https://www.threads.com/@limsangjin12/post/DaIPtwElE97), [app-templates 저장소](https://github.com/limsangjin12/app-templates), [Google Play 개인 계정 테스트 요건](https://support.google.com/googleplay/android-developer/answer/14151465), [Apple Ads 프로모션 크레딧](https://searchads.apple.com/help/basic/0041-apple-search-ads-promo-credit/)
**작성일**: 2026-11-14 (2026-11-15 사실 확인·적용할 점 표 추가)
**태그**: 바이브코딩, 앱공장, 모노레포, ClaudeCode, Codex, AGENTS.md, 앱스토어, 구글플레이
