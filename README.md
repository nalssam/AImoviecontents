# 🎬 Shorts Automation Pipeline

> **주제 한 줄로 교육용 숏폼 영상이 완성되는 AI 자동화 파이프라인**
>
> Claude Code × Higgsfield × ElevenLabs × CapCut

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/)
[![Made with Claude Code](https://img.shields.io/badge/Made%20with-Claude%20Code-7C3AED)](https://claude.com/product/claude-code)
[![Korean](https://img.shields.io/badge/한국어-README-red)](docs/ko/README.md)

[한국어 README 보기 ›](docs/ko/README.md) · [English ›](#english)

---

## ✨ 이게 뭔가요?

교사·크리에이터·교육 콘텐츠 제작자를 위한 **완전 자동화 영상 제작 파이프라인**입니다.

```
"5학년 AI 리터러시" 한 줄 입력
        ↓
[ Claude Code가 알아서 처리 ]
   시나리오 → 대본 → 스토리보드 → 씬 이미지 → 영상 → 음성 → 편집 프로젝트
        ↓
✅ CapCut에서 열어서 익스포트, 또는 ✅ FFmpeg로 즉시 mp4 출력
```

**기존 3~5시간 작업 → 5~15분으로 단축**됩니다.

## 📺 데모

| 입력 | 출력 (예시) |
|------|------------|
| `"AI는 거짓말을 할까? 5학년"` | 60초 9:16 쇼츠 (이미지 6장, AI 음성, 자막) |
| `"광합성의 원리"` | 90초 16:9 유튜브 영상 (다이어그램 + 내레이션) |
| `"세종대왕의 한글 창제"` | 120초 4:5 인스타 영상 (인물 일러스트 + 스토리텔링) |

## 🚀 30초 요약

1. **Git for Windows + Claude Code** 설치
2. **API 키 3개** 발급 (Anthropic, ElevenLabs, Higgsfield는 MCP 연결)
3. **이 레포 클론** 후 `claude` 실행
4. `claude` 안에서 **"PROJECT_BRIEF.md 읽고 시작하자"**
5. 주제 한 줄 입력 → 영상 완성

전체 셋업은 **약 1~2시간**, 한 번 만들어두면 그 후엔 영상 1편당 **5~15분**.

## 📚 가이드 문서

| 문서 | 대상 | 분량 |
|------|------|------|
| [한국어 완전 가이드 (Word)](docs/AI숏폼영상자동화_가이드_v1.0.docx) | 초보 교사 | 15부 + 부록 |
| [QUICKSTART.md](docs/QUICKSTART.md) | 빠르게 시작하고 싶은 사람 | 10분 |
| [INSTALL.md](docs/INSTALL.md) | 설치 전담 | 단계별 |
| [WORKFLOW.md](docs/WORKFLOW.md) | 파이프라인 동작 원리 | 개념 위주 |
| [TROUBLESHOOTING.md](docs/TROUBLESHOOTING.md) | 막혔을 때 | FAQ |
| [PROMPTING.md](docs/PROMPTING.md) | Claude Code 잘 시키는 법 | 노하우 |

## 🎯 출력 옵션

### 화면 비율
| 비율 | 용도 | 4K | FHD |
|------|------|----|----|
| 9:16 | 쇼츠/릴스/틱톡 | 2160×3840 | 1080×1920 |
| 16:9 | 유튜브 일반 | 3840×2160 | 1920×1080 |
| 4:5 | 인스타 피드 | 3456×4320 | 1080×1350 |
| 1:1 | 정방형 | 3840×3840 | 1080×1080 |

### 영상 모드
- `image`: 모든 씬 정적 이미지 (빠름·저렴) — **권장 기본값**
- `video`: 모든 씬 AI 영상화 (느림·비쌈·화려함)
- `hybrid`: 훅+마무리만 영상, 본문은 이미지 (균형)

### 출력 모드
- `capcut`: CapCut 프로젝트 파일 생성 (마무리는 수동)
- `ffmpeg`: FFmpeg로 mp4 즉시 출력 (무인 자동화)
- `both`: 둘 다 생성 (검수용 mp4 + 편집용 프로젝트)

## 💰 예상 비용 (2026년 5월 기준)

| 항목 | 비용 |
|------|------|
| Claude Pro | $20 / 월 (필수) |
| ElevenLabs | $0 (무료 1만 자) ~ $5 / 월 |
| Higgsfield | 영상 1편당 $0.5 ~ $3 |
| **주 2편 제작 시 합계** | **약 $30 ~ $40 / 월** |

## 🛠 기술 스택

- **두뇌**: [Claude Code](https://claude.com/product/claude-code) (Anthropic)
- **이미지·영상**: [Higgsfield](https://higgsfield.ai) (Soul, Nano Banana, Seedance, Kling)
- **음성**: [ElevenLabs](https://elevenlabs.io) TTS
- **편집**: [CapCut Desktop](https://www.capcut.com) + [FFmpeg](https://ffmpeg.org)
- **언어**: Python 3.10+

## 🏃 빠른 시작

```bash
# 1. 레포 클론
git clone https://github.com/YOUR_USERNAME/shorts-automation.git
cd shorts-automation

# 2. .env 파일 생성 (.env.example을 복사)
cp .env.example .env
notepad .env   # 또는 본인이 쓰는 에디터로 키 채우기

# 3. CapCut 샘플 프로젝트의 draft_content.json을 samples/에 복사
#    (자세한 방법은 docs/INSTALL.md 참고)

# 4. Claude Code 실행
claude

# 5. Claude Code 안에서
# > PROJECT_BRIEF.md 읽고 환경 점검부터 시작해줘
```

자세한 단계는 [QUICKSTART.md](docs/QUICKSTART.md) 참고.

## 📂 프로젝트 구조

```
shorts-automation/
├── README.md                  # 이 파일
├── PROJECT_BRIEF.md           # Claude Code용 프로젝트 설명서
├── LICENSE                    # MIT
├── .env.example               # API 키 템플릿
├── .gitignore                 # .env 등 보호
├── requirements.txt           # Python 패키지 목록
├── docs/                      # 가이드 문서들
├── samples/                   # CapCut 샘플 (사용자가 채움)
├── src/                       # 자동화 코드
│   ├── main.py                # CLI 진입점
│   ├── scenario/              # 대본·스토리보드 모듈
│   ├── assets/                # 이미지·영상·TTS 생성 모듈
│   ├── builders/              # CapCut·FFmpeg 빌더
│   └── utils/                 # 공통 유틸
├── config/                    # 해상도·비율 매핑 등
├── templates/                 # 프롬프트 템플릿
├── examples/                  # 사용 예시
├── scripts/                   # 보조 스크립트
└── projects/                  # 생성된 결과물 (런타임)
```

## 🤝 기여하기

이 프로젝트는 **교사들의 시간을 돌려드리기 위한** 오픈소스입니다.
누구나 환영합니다.

- 🐛 버그 발견: [Issues](https://github.com/YOUR_USERNAME/shorts-automation/issues)
- 💡 기능 제안: [Discussions](https://github.com/YOUR_USERNAME/shorts-automation/discussions)
- 📖 가이드 개선: PR 환영
- 🌍 다른 언어 번역: 환영

자세한 사항은 [CONTRIBUTING.md](CONTRIBUTING.md) 참고.

## 🙏 만든 사람들

- 원안 / 설계: **날쌤 (박준호)** — [몽당분필 / 디미교연](https://www.mongdang.kr)
- 코드 동반자: Claude (Anthropic)

영감을 준 모든 교사 동료들에게 감사드립니다.

## 📜 라이선스

[MIT License](LICENSE) — 자유롭게 사용·수정·재배포 가능합니다.
다만 **AI가 생성한 콘텐츠의 사실 확인과 윤리적 사용 책임은 사용자에게 있습니다.**

---

<a name="english"></a>

## English

A fully-automated educational short-form video pipeline.
**Type one topic → get a finished video.**

Built on Claude Code, Higgsfield (image/video), ElevenLabs (TTS), and CapCut.

See [docs/en/README.md](docs/en/README.md) for the English guide.

---

<p align="center">
  <b>"노동은 코드가 하고, 인간은 결정만 한다."</b><br/>
  <i>"Let code do the labor. Humans decide."</i>
</p>
