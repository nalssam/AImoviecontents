# 기여 가이드 (Contributing)

이 프로젝트는 **교사들의 시간을 돌려드리기 위한** 오픈소스입니다.
어떤 형태의 기여든 환영합니다.

## 🌱 어떤 기여가 가능한가요?

### 1. 가이드 개선 (코딩 몰라도 됨)

- 오타 수정
- 더 친절한 설명 추가
- 새로운 트러블슈팅 사례 공유
- 다른 학년·과목용 예시 추가

→ `docs/` 폴더의 마크다운 파일을 수정해서 PR 보내주세요.

### 2. 실제 결과물 공유

직접 만든 영상이나 프롬프트를 `examples/` 폴더에 추가:

- 사용한 주제와 옵션
- 생성된 대본·스토리보드 (있다면)
- 결과 영상 링크 (유튜브 등)
- 후기 (잘 됐던 점·아쉬웠던 점)

다른 선생님들의 모범 사례가 됩니다.

### 3. 버그 리포트

[Issues](https://github.com/YOUR_USERNAME/shorts-automation/issues)에 등록.
양식:

- OS / Python / Claude Code 버전
- 재현 단계
- 기대했던 동작 vs 실제 동작
- 에러 메시지 (API 키는 가려주세요!)

### 4. 코드 기여

새 기능, 모듈 구현, 테스트 추가 등.

- Fork → 브랜치 생성 → PR
- 한 PR에 한 가지 변경만
- 가능하면 테스트 포함

### 5. 번역

- 영어 README 다듬기
- 다른 언어로 번역 추가

→ `docs/en/`, `docs/ja/` 등에 추가

## 🤝 기여 원칙

1. **교사 친화적 톤 유지**: 코드보다 사람을 먼저 생각하는 설명.
2. **친절한 에러 메시지**: 비프로그래머가 읽고 무엇을 하면 되는지 알 수 있도록.
3. **API 키·개인정보 차단**: 절대 커밋·푸시되면 안 됩니다.
4. **저작권·윤리 고려**: AI 생성 콘텐츠가 미성년자에게 안전하도록.
5. **공식 문서 참조**: 외부 API는 web fetch로 최신 확인.

## 🛠 개발 환경 세팅

```bash
git clone https://github.com/YOUR_USERNAME/shorts-automation.git
cd shorts-automation
python -m venv venv
.\venv\Scripts\activate    # Windows
pip install -r requirements.txt
cp .env.example .env       # 키 채우기
```

## 📝 PR 체크리스트

- [ ] `.env`나 API 키가 포함되어 있지 않은가
- [ ] 새 코드는 기존 모듈 구조를 따랐는가
- [ ] 새 기능이라면 `docs/`에 사용법 추가했는가
- [ ] 한국어 메시지가 자연스러운가
- [ ] 변경사항이 한 가지에 집중되어 있는가

## 💬 도움이 필요하다면

- 코드 관련 질문: [Discussions](https://github.com/YOUR_USERNAME/shorts-automation/discussions)
- 교실 활용 사례: 몽당분필 / 디미교연 커뮤니티

## 🎁 기여자

→ [CONTRIBUTORS.md](CONTRIBUTORS.md) (자동 갱신)

---

함께 만들어가요. 🚀
