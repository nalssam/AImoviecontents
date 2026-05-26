# 교육콘텐츠 숏폼 자동화 프로젝트 (v1.0)

> 이 문서는 **Claude Code가 프로젝트 맥락을 한 번에 파악**하기 위한 설명서입니다.
> `claude` 실행 후 첫 메시지로 "PROJECT_BRIEF.md 읽고 시작하자"라고 말하면 됩니다.

## 🎯 목표

교육 주제 한 줄 입력 → 시나리오 → 대본 → 스토리보드 → 이미지 → 영상 → TTS → 편집 프로젝트까지
**완전 자동 생성**되는 파이프라인.

CapCut 프로젝트 파일과 FFmpeg mp4 두 가지 출력 모두 지원.

## 👤 사용자

초·중등 교사, 교육 콘텐츠 크리에이터.
Windows + Python + Claude Code 환경.
대부분 비프로그래머이므로 **친절한 에러 메시지**와 **명확한 진행 표시**가 중요.

## 🔄 풀 파이프라인

```
1. CLI에서 주제 입력 (예: "5학년 AI 리터러시")
2. 시나리오 초안 생성 (Claude)
3. 구간별 대본 작성 (나레이션 + 화면 연출 지시)
4. 스토리보드 생성 (구간별 이미지 프롬프트)
5. 씬 이미지 생성 (Higgsfield MCP)
6. 이미지 → 영상 변환 (Higgsfield MCP, 선택)
7. TTS 생성 (ElevenLabs)
8. 파일 다운로드 + 자동 폴더링
9. 출력 모드 분기:
   - capcut: draft_content.json 자동 조립
   - ffmpeg: mp4 직접 출력
   - both: 둘 다 생성
```

## ⚙️ CLI 옵션

```bash
python -m src.main "주제" \
  --ratio 9:16 \
  --resolution FHD \
  --visual image \
  --mode both \
  --duration 60 \
  --grade 5
```

### 화면 비율 (`--ratio`)
| 비율 | 4K | FHD |
|------|----|----|
| 9:16 | 2160×3840 | 1080×1920 |
| 16:9 | 3840×2160 | 1920×1080 |
| 4:5  | 3456×4320 | 1080×1350 |
| 1:1  | 3840×3840 | 1080×1080 |

### 영상 모드 (`--visual`)
- `image`: 모든 구간 정적 이미지 (기본값, 빠름·저렴)
- `video`: 모든 구간 영상화 (느림·비쌈·화려함)
- `hybrid`: 훅+마무리만 영상, 본문은 이미지

### 출력 모드 (`--mode`)
- `capcut`: draft_content.json 생성, 사용자가 CapCut에서 익스포트
- `ffmpeg`: FFmpeg로 mp4 직접 출력 (완전 무인)
- `both`: 둘 다 생성 (기본값)

## 📁 폴더 구조

```
projects/[날짜]_[주제슬러그]/
├── script.md           # 대본 + 스토리보드
├── prompts.json        # 구간별 프롬프트 기록
├── meta.json           # 구간별 duration, 파일 매핑
├── images/             # 씬 이미지
├── videos/             # AI 영상 (video/hybrid 모드만)
├── tts/                # ElevenLabs 음성
├── capcut/
│   └── draft_content.json
└── output.mp4          # ffmpeg/both 모드만
```

## 🔌 API / MCP

| 서비스 | 용도 | 인증 방식 |
|--------|------|----------|
| Claude API | 대본 생성 | Claude Code 내장 |
| Higgsfield MCP | 이미지·영상 | MCP 연결 |
| ElevenLabs API | TTS | `.env`의 `ELEVENLABS_API_KEY` |
| FFmpeg | mp4 합성 | 로컬 설치 |

## 🔐 환경변수 (`.env`)

```
ANTHROPIC_API_KEY=sk-ant-...
ELEVENLABS_API_KEY=sk_...
ELEVENLABS_VOICE_ID_DEFAULT=...
OPENAI_API_KEY=...   # 선택
GEMINI_API_KEY=...   # 선택
```

## 🧩 모듈 구조 (제안)

```
src/
├── main.py                    # CLI 진입점
├── config.py                  # 해상도/비율/모델 매핑
├── scenario/
│   ├── scenario_writer.py     # 시나리오·대본
│   └── storyboard.py          # 스토리보드 프롬프트
├── assets/
│   ├── image_generator.py     # Higgsfield 이미지
│   ├── video_generator.py     # Higgsfield 영상
│   └── tts_generator.py       # ElevenLabs
├── builders/
│   ├── capcut_builder.py      # draft_content.json
│   └── ffmpeg_renderer.py     # mp4 합성
└── utils/
    ├── env.py                 # .env 로드 + 검증
    ├── logger.py              # 통일된 로깅
    └── cost.py                # 비용 추산
```

## 📐 개발 원칙

1. **단계별 검증** — 한 번에 큰 코드를 만들지 말 것. 모듈마다 작은 테스트.
2. **MVP 우선** — 첫 목표는 "1구간, 9:16 FHD, image+capcut 모드, end-to-end".
3. **공식 문서 직접 확인** — 외부 API는 학습 데이터가 아니라 `web fetch`로 최신 확인.
4. **재시도 + 로깅** — 외부 호출은 모두 실패 대비.
5. **비용 추산** — 매 실행 전 예상 비용을 사용자에게 표시.
6. **하드코딩 금지** — API 키, 경로, 모델명 모두 `.env` 또는 `config/`에서 관리.
7. **친절한 에러 메시지** — 비프로그래머 사용자가 대다수.

## 🚦 권장 진행 순서

Claude Code에서 첫 메시지로 아래를 그대로 보내세요.

```
PROJECT_BRIEF.md를 읽고 다음 순서로만 진행해줘.
코드는 내가 명시적으로 동의할 때만 작성하자.

[Phase 0] 환경 점검
  - Higgsfield MCP 연결 상태
  - .env 존재 및 필수 키 확인
  - samples/draft_content.json 존재 확인
  - FFmpeg 설치 여부
  - Python 가상환경 필요성

[Phase 1] 사전 조사 (web fetch로 공식 문서 직접)
  - ElevenLabs TTS API 최신
  - Higgsfield 이미지·영상 모델 파라미터
  - FFmpeg 합성 권장 방식

[Phase 2] CapCut 구조 분석
  - samples/draft_content.json 파싱
  - capcut_structure_notes.md 작성

[Phase 3] 개발 계획안 제시
  - MVP: 1구간, 9:16 FHD, image+capcut
  - 이후 확장 단계와 위험 요소

내가 동의하면 Phase 단위로 진행해줘.
```

## 📚 참고 문서

- [docs/QUICKSTART.md](docs/QUICKSTART.md) — 10분 시작 가이드
- [docs/INSTALL.md](docs/INSTALL.md) — 설치 단계별
- [docs/WORKFLOW.md](docs/WORKFLOW.md) — 파이프라인 동작 원리
- [docs/PROMPTING.md](docs/PROMPTING.md) — Claude Code 잘 시키는 법
- [docs/TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) — 자주 막히는 지점
