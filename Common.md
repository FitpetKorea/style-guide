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

[제목 type 종류](https://www.notion.so/596768412ae648fc8d7de898dcfdea5d)

### 주의 해야 할 규칙

- 제목줄은 대문자로 시작한다.
- 제목줄은 명령어로 작성한다.
- 제목줄은 마침표로 끝내지 않는다.
- 본문과 제목에는 빈줄을 넣어서 구분한다.
- 본문에는 "어떻게" 보다는 "왜"와 "무엇을" 설명한다.
- 본문에 목록을 나타낼때는 "-"로 시작한다.

### git commit message template 설정 방법

- git에서 global하게 git commit message 설정 하기
    1. Git config 에 추가

        .gitconfig 파일에 commit.template 항목에 기본 값으로 등록할 내용을 추가해줍니다.

        아래에서는 .gitmessage라는 파일에서 template을 읽어오도록 했습니다. 

        template 파일 이름은 본인이 원하시는 형식으로 만드셔도 상관 없습니다. 

        ```shell
        git config --global commit.template ~/.gitmessage 
        ```

        명령을 실행다면 ~/.gitconfig 파일에 다음과같이 설정이된다.

        ```shell
        [commit]
        		template = ~/.gitmessage
        ```

    2. 위의 Commit message Template 작성 

        ~/.gitmessage 작성을 합니다.

        ```shell
        #<type>: <subject>
        ##### Subject 50 characters ################# -> |
                                            

        # Body Message
        ######## Body 72 characters ####################################### -> |

        # Footer Message
        # Issue Tracker Number or URL

        # --- COMMIT END ---
        # Type can be
        #   feature : 새로운 기능 추가
        #   fix     : 버그 수정
        #   refac   : 코드 리팩토링
        #   style   : 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우
        #   docs    : 문서 수정
        #   test    : 테스트 추가 혹은 테스트 리팩토링, 프로덕션 레벨 코드 변경 없는 경우
        #   chore   : 빌드 업무 수정, 패키지 설정 수정, 프로덕션 레벨 코드 변경 없는 경우
        # ------------------
        # 다음의 규칙을 지켜서 메세지를 작성합니다. 
        #     제목줄은 대문자로 시작한다.
        #     제목줄은 명령어로 작성한다.
        #     제목줄은 마침표로 끝내지 않는다.
        #     본문과 제목에는 빈줄을 넣어서 구분한다.
        #     본문에는 "어떻게" 보다는 "왜"와 "무엇을" 설명한다.
        #     본문에 목록을 나타낼때는 "-"로 시작한다.
        # ------------------
        ```

- 레포마다 다르게 설정하기
    1. 다음 명령을 레포에서 입력한다.

        ```shell
        git config commit.template ./path/to/.gitmessage   
        ```

    2. git/gitmessage에 위의 template을 작성해준다.
