# Changelog

이 프로젝트의 모든 주요 변경사항이 기록됩니다.

형식은 [Keep a Changelog](https://keepachangelog.com/ko/1.1.0/)를 따르며,
[Semantic Versioning](https://semver.org/lang/ko/)을 사용합니다.

## [Unreleased]

### 예정
- 실제 Claude API 연동 (`scenario_writer.py`)
- Higgsfield MCP 어댑터 (`image_generator.py`, `video_generator.py`)
- ElevenLabs SDK 연동 (`tts_generator.py`)
- CapCut JSON 빌더 (`capcut_builder.py`)
- FFmpeg 렌더러 (`ffmpeg_renderer.py`)
- 한국어 / 영어 / 일본어 가이드
- 학년별·과목별 프롬프트 템플릿

## [1.0.0] - 2026-05-26

### Added (초기 공개)
- 프로젝트 구조 및 PROJECT_BRIEF.md
- 가이드 문서 일체 (한국어):
  - `README.md`
  - `docs/QUICKSTART.md`
  - `docs/INSTALL.md`
  - `docs/WORKFLOW.md`
  - `docs/PROMPTING.md`
  - `docs/TROUBLESHOOTING.md`
- 환경 설정: `.env.example`, `.gitignore`, `requirements.txt`
- 라이선스: MIT
- 행동 강령 (CODE_OF_CONDUCT)
- 기여 가이드 (CONTRIBUTING)
- Config 모듈:
  - `config/aspect_ratios.py` (4K/FHD × 9:16/16:9/4:5/1:1)
  - `config/models.py` (Higgsfield 모델 매핑)
- Utility 모듈:
  - `src/utils/env.py` (환경변수 로드·검증)
  - `src/utils/logger.py` (rich + loguru)
  - `src/utils/cost.py` (비용 추산)
- 소스 코드 스켈레톤:
  - `src/main.py` (CLI 진입점)
  - `src/scenario/` (대본·스토리보드)
  - `src/assets/` (이미지·영상·TTS)
  - `src/builders/` (CapCut·FFmpeg)
- 프롬프트 템플릿:
  - `templates/scenario_prompt.md`
  - `templates/storyboard_style.md`
- GitHub Issue/PR 템플릿

### 주의
- v1.0.0은 **프레임워크와 가이드** 중심 릴리즈입니다.
- 실제 생성 모듈들은 Claude Code 환경에서 단계별로 구현해야 합니다.
- 이는 의도된 설계입니다: 사용자가 직접 자신의 환경에 맞게 채워가도록.

---

[Unreleased]: https://github.com/YOUR_USERNAME/shorts-automation/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/YOUR_USERNAME/shorts-automation/releases/tag/v1.0.0
