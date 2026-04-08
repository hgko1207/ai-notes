# 2026년 4월 첫째 주 AI 뉴스 총정리

> 한 줄 요약: Gemma 4가 파라미터 대비 최강 성능으로 오픈소스 왕좌를 노리는 가운데, Claude Code 소스 유출·Anthropic 구독 차단·MS Copilot 광고 철회까지 AI 업계 굵직한 사건들이 연달아 터졌습니다.

## 이번 주 핵심 뉴스

| 분류 | 제목 | 한 줄 요약 |
|------|------|-----------|
| 모델 | Gemma 4 | 31B로 685B급 모델 성능 돌파, Apache 2.0 오픈소스 |
| 도구 | Veo 3.1 Lite | 구글 영상 생성 비용 절반으로 인하 |
| 모델 | GPT Image 2 + Grok Quality | 실사 수준 이미지 모델 출시 임박 + Grok 고품질 모드 |
| 트렌드 | Claude Code 소스 유출 | npm 소스맵 실수로 내부 구조 전체 공개 |
| 트렌드 | Anthropic 구독 차단 | Claude 구독으로 타사 앱 사용 공식 금지 |
| 도구 | Computer Use Windows | 마우스·키보드 자동 제어 Windows 지원 + Codex 플러그인 |
| 트렌드 | MS MAI 모델 + Copilot 광고 | 신모델 3종 공개, PR 광고 삽입 후 즉시 철회 |
| 도구 | Pika Stream + Netflix VOID | AI 화상 미팅 참여 + 물리 반응 반영 물체 삭제 |
| 모델 | 중국 AI 모델 동향 | Qwen 3.5 Omni, Wan 2.7, GLM-5V-Turbo |
| 리소스 | LLM Wiki + Design MD + K-Skills | 에이전트 시대 필수 개발 리소스 3종 |
| 도구 | 타입캐스트 | 280만 가입자의 한국어 TTS, 스마트 이모션 + API |

---

## 모델 소식

### [Gemma 4 — 파라미터 대비 최강 성능의 오픈소스 모델](../models/gemma4-opensource-benchmark-leader.md)

구글의 Gemma 4가 **Apache 2.0 라이선스**로 공개됐습니다. 31B 파라미터로 Arena Elo 1452점을 기록하며 685B, 397B급 모델들을 앞서는 충격적인 성능을 보여줬습니다.

- 오픈소스 랭킹 3위 달성
- 코드포스 2150점 수준의 코딩 능력
- 아이폰 17 Pro에서 40 tokens/s (4E2B 모델)
- Claude Code와 연동 사용 가능

---

### [GPT Image 2 유출 + Grok Quality Mode — 이미지 AI 대격변](../models/gpt-image2-grok-quality-mode.md)

OpenAI의 **GPT Image 2**가 정식 출시 전 유출됐습니다. 사진과 구별이 어려운 수준의 품질과 정확한 텍스트 렌더링이 화제가 됐습니다. 출시는 "Around the corner"로 임박했습니다.

xAI의 **Grok**도 Quality Mode를 추가하며 고품질 이미지 생성에 합류했습니다. 한글 텍스트도 정확하게 나옵니다.

---

### [중국 AI 모델 동향 — Qwen 3.5 Omni, Wan 2.7, GLM-5V-Turbo](../models/china-ai-models-april-2026.md)

이번 주 중국 모델들의 약진이 눈에 띕니다.

- **Qwen 3.5 Omni**: 텍스트·이미지·오디오·영상 완전 옴니, Gemini 3.1 Flash 수준
- **GLM-5V-Turbo**: 디자인-투-코드에서 Claude Opus 4.6 상회
- **공통점**: 모두 클로즈드 소스로 전환, API 제공

---

## 도구 / 서비스 소식

### [Veo 3.1 Lite + 구글 업데이트 — 영상 생성 비용 절반으로](../tools/veo31-lite-google-updates-april-2026.md)

구글이 **Veo 3.1 Lite**를 출시하며 영상 생성 비용을 대폭 낮췄습니다. 기존 패스트 모델 대비 절반 수준의 가격으로 720p~1080p 영상 생성이 가능합니다. Google AI Pro 요금제 스토리지도 2TB → 5TB로 증가했습니다.

---

### [Claude Computer Use Windows + Codex 플러그인](../tools/claude-computer-use-windows-codex-plugin.md)

마우스·키보드·화면을 직접 제어하는 **Computer Use**가 Windows에서도 공식 지원됩니다. 국내 사무 환경에서도 반복 작업 자동화가 가능해졌습니다.

OpenAI 직원이 만든 **Claude Code 내 Codex 플러그인**도 등장했습니다. ChatGPT 구독으로 Claude Code 안에서 Codex를 사용할 수 있게 됐습니다.

---

### [Pika Stream 1.0 + Netflix VOID](../tools/pika-stream-netflix-void.md)

**Pika Stream 1.0**: 미팅 링크만 전달하면 AI가 화상 채팅에 직접 참여합니다. 외국어 말하기 연습, 인터뷰 준비에 활용 가능합니다.

**Netflix VOID**: 영상에서 물체를 삭제할 때 해당 물체와의 물리적 상호작용까지 자동으로 반영합니다. 오픈소스로 공개됐습니다.

---

### [타입캐스트 — 280만 가입자의 한국어 AI TTS](../tools/typecast-korean-tts.md)

국내 TTS 서비스 **타입캐스트**가 스마트 이모션, 보이스 클로닝, API 등으로 업그레이드됐습니다. 유튜브 쇼츠에서 자주 들리는 그 목소리들이 모두 여기서 나왔습니다. SBS, YTN, 이마트 등에서도 사용 중입니다.

---

## 트렌드 / 업계 동향

### [Claude Code 소스코드 npm 유출](../trends/claude-code-source-leak-npm.md)

npm 레지스트리에 소스맵이 실수로 올라가면서 **Claude Code 전체 소스코드**가 공개됐습니다. 시스템 프롬프트, 언더커버 모드, MCP 서버 동작 방식 등이 모두 노출됐습니다.

한국 개발자가 유출된 구조를 기반으로 **Python으로 재구현**하여 GitHub에서 가장 빠른 Star 기록을 세웠습니다.

---

### [Anthropic, Claude 구독으로 타사 앱 사용 공식 차단](../trends/anthropic-third-party-subscription-block.md)

Claude 구독으로 OpenClaw 같은 서드파티 앱을 사용하는 것이 **공식 금지**됐습니다. 앞으로는 Claude API 키로만 가능합니다. 기존 구독자에게는 월 구독료와 동일한 일회성 크레딧이 제공됩니다.

---

### [MS MAI 모델 3종 공개 + GitHub Copilot PR 광고 논란](../trends/microsoft-mai-models-copilot-ads.md)

마이크로소프트가 MAI Transcribe 1(STT), MAI Voice 1(TTS), MAI Image 2를 공개했습니다. ElevenLabs보다 낮은 에러율로 주목받고 있습니다.

GitHub Copilot이 PR 화면에 광고를 삽입했다가 개발자들의 강한 반발로 **즉시 철회**됐습니다. OpenAI의 TVPN 미디어 채널 인수도 이번 주 뉴스입니다.

---

## 개발 리소스

### [LLM Wiki + Awesome Design MD + K-Skills](../resources/llm-wiki-design-md-kskills.md)

- **LLM Wiki**: 안드레이 카파시가 제안한 RAG 대체 지식 관리 방식
- **Awesome Design MD**: 애플·스포티파이·에어비앤비 디자인을 역설계한 MIT 라이선스 파일 모음
- **K-Skills**: KTX 예매, 지하철, 법령 검색 등 한국인 맞춤 MCP 스킬 모음

---

## 마무리

이번 주는 **Gemma 4**의 파격적인 성능이 가장 큰 화제였습니다. 31B짜리 오픈소스 모델이 수백억 파라미터 모델들을 넘어서는 성능을 보여주면서, 로컬 AI의 가능성이 한 단계 높아졌습니다. 동시에 Claude Code 소스 유출, Anthropic의 구독 정책 강화, MS의 광고 실험 등 AI 기업들의 생태계 정비 움직임도 눈에 띕니다. 오픈소스와 클로즈드 소스, 무료와 유료 사이의 경계가 계속해서 재편되고 있습니다.

---
**출처**: [조코딩 JoCoding - 주간 AI 뉴스](https://www.youtube.com/watch?v=6bt8iQctcog)
**작성일**: 2026-04-08
**태그**: 주간 AI 뉴스, Gemma 4, Claude Code 유출, GPT Image 2, Qwen 3.5, 타입캐스트, Veo 3.1 Lite, 2026년 4월
