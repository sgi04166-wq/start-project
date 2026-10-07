# Repository Guidelines

## Project Structure & Module Organization

This Unity project uses editor **6000.0.61f1**, as pinned in `ProjectSettings/ProjectVersion.txt`, and the Universal Render Pipeline.

## 프로젝트
- Unity 6000.6.0f1, URP, C# 9 / .NET Standard 2.1, Input System 패키지 사용(0.61f1사용중)
- 대상 플랫폼: Windows (Steam). 나중에 Steam Deck(Linux/Proton) 호환 고려
- 2인 파트타임 개발. 모든 변경은 사람이 diff 확인 + Unity에서 직접 플레이 후 머지

## 폴더 규칙
- 우리 코드·에셋은 전부 `Assets/_Project/` 아래. 에셋스토어 패키지는 `Assets/ThirdParty/`
- Scripts/Core (부트스트랩, 세이브, 설정) / Scripts/Gameplay / Scripts/UI / Tests
- 파일명 = 클래스명(PascalCase). 한 파일에 클래스 하나. 300줄 넘으면 분리 제안

## Unity 작업 원칙
- 씬(.unity)·프리팹(.prefab)·.meta 파일은 직접 편집하지 않는다. 필요하면 C# 에디터 스크립트나 사람이 할 절차를 제안한다
- .meta 파일을 삭제·이동하지 않는다. 스크립트 파일 이름 변경 시 반드시 알려 준다
- 새 패키지(Package Manager)는 임의로 추가하지 않고 먼저 제안한다
- MonoBehaviour의 Update()에서 GetComponent/Find 계열 호출 금지, 캐싱 사용
- 코루틴보다 async/await 또는 Unity Awaitable 사용을 우선 검토
- SerializeField는 private 필드 + [SerializeField], public 필드 금지

## 검증
- 코드를 바꾼 뒤에는 컴파일 오류 가능성을 스스로 검토하고, 사람이 Unity에서 Ctrl+R로 재컴파일해 Console을 확인하도록 안내한다
- 테스트는 Unity Test Framework(EditMode) 기준으로 `Assets/_Project/Tests/EditMode/`에 작성

## 커밋
- Conventional Commits: feat / fix / refactor / chore / test
- 커밋은 제안만 하고 사람이 실행한다. `git push`는 절대 실행하지 않는다

## 금지
- API 키·토큰·비밀값을 코드나 설정에 넣지 않는다
- Library/, Temp/, Logs/ 폴더는 건드리지 않는다