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
### git commit message template
```shell
#<type>: <subject>
##### Subject 50 characters ################# -> |


# Body Message
######## Body 72 characters ####################################### -> |

# Footer Message
# Issue Tracker Number or URL

# --- COMMIT END ---
# Type can be
#   feat    : new feature(새로운 기눙 추가)
#   fix     : bug fix(버그 수정)
#   refactor: refactoring production code(코드 리팩토링)
#   style   : formatting, missing semi colons, etc; no code change(코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우)
#   docs    : changes to documentation(문서 수정)
#   test    : adding or refactoring tests, no productin code change
#             (테스트 추가 혹은 테스트 리팩토링, 프로덕션 레벨 코드 변경 없는 경우)
#   chore   : updating grunt tasks etc, no production code change 
#             (빌드 업무 수정, 패키지 설정 수정, 프로덕션 레벨 코드 변경 없는 경우)
# ------------------
# Remember me ~
#   Capitalize the subject line
#     제목줄은 대문자로 시작한다.
#   Use the imperative mood in the subject line
#     제목줄은 명령어로 작성한다.
#   Do not end the subject line with a period
#     제목줄은 마침표로 끝내지 않는다.
#   Separate subject from body with a blank line
#     본문과 제목에는 빈줄을 넣어서 구분한다.
#   Use the body to explain what and why vs. how
#     본문에는 "어떻게" 보다는 "왜"와 "무엇을" 설명한다.
#   Can use multiple lines with "-" for bullet points in body
#     본문에 목록을 나타낼때는 "-"로 시작한다.
# ------------------
``` 
## git commit message template 설정 방법
### git에서 global하게 git commit message 설정 하기
1. Git config 에 추가
  .gitconfig 파일에 commit.template 항목에 기본 값으로 등록할 내용을 추가해준다.  
  여기서 나는 ~/.gitmessage라는 것을 전체 프로젝트에서 사용하도록 구성하겠다.
  ```shell
  git config --global commit.template ~/.gitmessage
  ```
  명령을 실행다면 .gitconfig 파일에 다음과같이 설정이된다.
  ```shell
  [commit]
    template = ~/.gitmessage
  ```

2. 위의 Commit message Template 작성
~/.gitmessage 작성을 하자.

이슈는 남겨주는게 좋아서 트래커를 입력할 수 있도록…  
NOTE: # 으로 시작하는 줄은 삭제된다. 그리니 알아서 잘 띄우두도록하자. 
###레포마다 다르게 설정하기
  다음 명령을 레포에서 입력한다.

git config commit.template ./path/to/.gitmessage
그리고 .git/gitmessage에 template을 작성해준다.