# Git branch 전략

## github-flow
- 특별한 이유가 없으면 [github-flow](https://guides.github.com/introduction/flow/) 를 사용한다.

### Branch 역할
- master(main) : 주 Branch
- feature/~ : 기능 추가
- fix/~ : 버그 수정
- refac/~ : 리펙토링
- docs/~ : 문서 추가/수정

# TDD
- 모든 Endpoint의 테스트케이스를 작성한다.
- 비즈니스로직을 확인할 수 있는 테스트케이스를 작성한다.

# Git commit message convention

### Message Template

```bash
<type>: <subject> # 제목줄은 50자 이내 

Body Message # 72자 이내
Footer Message # 이슈 ID or URL 
```

### 제목 type 종류
- feature : 새로운 기눙 추가
- fix : 버그 수정
- refac: 코드 리팩토링
- style : 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
- docs : 문서 수정
- test : 테스트 추가 혹은 테스트 리팩토링, 프로덕션 레벨 코드 변경 없는 경우
- chore : 빌드 업무 수정, 패키지 설정 수정, 프로덕션 레벨 코드 변경 없는 경우

### 주의 해야 할 규칙

- 제목줄은 대문자로 시작한다.
- 제목줄은 명령어로 작성한다.
- 제목줄은 마침표로 끝내지 않는다.
- 본문과 제목에는 빈줄을 넣어서 구분한다.
- 본문에는 "어떻게" 보다는 "왜"와 "무엇을" 설명한다.
- 본문에 목록을 나타낼때는 "-"로 시작한다.

[git commit message template 설정 방법](https://www.notion.so/git-convention-61836a877067406cbfa06021cfe6e2e0) 에서 확인 가능합니다.
