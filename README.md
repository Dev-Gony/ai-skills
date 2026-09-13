# AI Skills

반복해서 사용하는 AI 작업 방식, 출력 규칙, 실무 워크플로를 재사용 가능한 Skill 형태로 정리하는 개인 저장소입니다.

A personal collection of reusable AI Skills for repeatable workflows and practical AI usage.

이 저장소에서는 Skill을 설계하고, 문서화하고, 버전 관리하고, 실제 사용을 통해 개선합니다. 완성된 Skill은 패키징하여 ChatGPT에 설치하고 테스트할 수 있습니다.

## 이 저장소의 목적

매번 같은 요청이나 작업 방식을 다시 설명하지 않고, 반복되는 지침과 워크플로를 재사용 가능한 Skill로 만드는 것이 목적입니다.

예를 들면 다음과 같은 작업을 Skill로 만들 수 있습니다.

- 일정한 출력 형식을 강제하기
- 생성된 파일을 한 번에 복사하고 붙여넣기 쉽게 만들기
- GitHub 초보자를 위한 설명 방식을 표준화하기
- 자동화 프로젝트를 단계적으로 진행하는 방식 정의하기
- 자주 사용하는 AI 활용 패턴을 재사용 가능한 형태로 저장하기

이 저장소는 단순한 프롬프트 모음이 아니라, AI 워크플로를 어떻게 설계하고 테스트하고 개선했는지를 기록하는 포트폴리오 역할도 합니다.

## 저장소 구조

각 Skill은 최상위 폴더 하나를 사용합니다.

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    `-- one-paste-output/
        |-- SKILL.md
        `-- agents/
            `-- openai.yaml

Skill이 늘어나면 다음과 같은 형태가 됩니다.

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    |-- one-paste-output/
    |-- github-beginner-guide/
    |-- automation-project-coach/
    `-- ...

## 저장소 공통 규칙

저장소 전체에 적용되는 공통 지침은 `AGENTS.md`에 정의합니다.

현재 주요 규칙은 다음과 같습니다.

- 저장소 콘텐츠에 이모지, 이모티콘, 장식용 유니코드 문자 사용 금지
- 표현은 간결하고 실용적으로 작성
- 복사와 붙여넣기가 쉬운 출력 우선
- 전체 파일을 제공할 때는 파일 내용을 여러 조각으로 나누지 않기
- Skill 하나당 최상위 폴더 하나 사용
- API Key, Access Token, 비밀번호, Webhook URL 등 비밀정보 커밋 금지

## 현재 Skill

### 1. one-paste-output

상태: 제작 완료, 검증 완료, ChatGPT 설치 및 실제 테스트 완료

목적:

파일 내용을 사용자가 한 번에 복사하고 붙여넣을 수 있도록, 파일 하나를 하나의 완전한 코드블럭으로 출력합니다.

다음과 같은 요청에서 사용하도록 설계했습니다.

- "전체 코드로 줘"
- "한 번에 복붙할 수 있게 줘"
- "수정 부분 말고 전체 파일로 줘"
- "코드블럭 나누지 마"
- "README.md 전체 내용을 한 번에 붙여넣을 수 있게 작성해줘"

주요 동작:

- 사용자가 전체 파일을 요청하면 부분 코드가 아니라 완성된 파일 전체를 반환
- 파일 하나당 코드블럭 하나 사용
- `...existing code...` 같은 생략용 placeholder 사용 금지
- 사용자가 patch나 부분 수정 방식이 헷갈린다고 하면 전체 파일 출력을 우선
- 여러 파일을 요청한 경우에도 각 파일을 독립적으로 한 번에 복사할 수 있게 출력
- Markdown 파일 내부에 fenced code block이 있어도 바깥쪽 fence 길이를 조정하여 출력이 중간에 깨지지 않도록 처리

경로:

`one-paste-output/`

구조:

    one-paste-output/
    |-- SKILL.md
    `-- agents/
        `-- openai.yaml

## Skill 기본 구조

기본적인 Skill은 다음 파일을 포함합니다.

    skill-name/
    |-- SKILL.md
    `-- agents/
        `-- openai.yaml

### SKILL.md

Skill의 핵심 지침 파일입니다.

주요 내용:

- Skill 이름
- 어떤 요청에서 Skill을 사용할지 판단하는 description
- 상세 동작 방식
- 출력 규칙
- 검증 규칙

### agents/openai.yaml

ChatGPT에서 Skill을 표시할 때 사용하는 UI 메타데이터를 정의합니다.

필요한 경우 다음 디렉터리를 추가할 수 있습니다.

    scripts/
    references/
    assets/

단, 실제 Skill의 품질이나 재사용성을 높이는 경우에만 추가합니다.

## 개발 흐름

이 저장소에서는 보통 다음 순서로 Skill을 개발합니다.

    반복되는 문제 발견
            |
            v
    입력과 출력 정의
            |
            v
    Skill 구조 생성
            |
            v
    SKILL.md 작성 및 수정
            |
            v
    Skill 검증
            |
            v
    skill.zip 패키징
            |
            v
    ChatGPT에 설치
            |
            v
    실제 프롬프트로 테스트
            |
            v
    사용 중 불편한 점을 반영하여 개선

GitHub는 Skill 소스의 기준 저장소로 사용하고, `skill.zip`은 ChatGPT에 설치하고 테스트하기 위한 배포 파일로 사용합니다.

## ChatGPT에 Skill 설치하기

GitHub에 Skill 소스가 있다고 해서 ChatGPT에서 자동으로 사용할 수 있는 것은 아닙니다.

일반적인 설치 흐름은 다음과 같습니다.

1. Skill 디렉터리를 준비합니다.
2. Skill을 검증합니다.
3. `skill.zip`으로 패키징합니다.
4. ChatGPT의 Skills 화면을 엽니다.
5. 패키징된 Skill을 업로드하거나 설치합니다.
6. 새 대화에서 실제 요청으로 테스트합니다.

예를 들어 `one-paste-output`을 설치한 뒤 다음과 같이 요청할 수 있습니다.

    README.md 전체 내용을 한 번에 복붙할 수 있게 작성해줘.
    중간에 코드블럭 나누지 마.

요청 내용이 Skill의 description과 일치하면 ChatGPT가 해당 Skill을 사용할 수 있습니다.

## 새로운 Skill 추가하기

새 Skill을 만들 때는 다음 순서를 기준으로 합니다.

1. 반복되는 문제가 무엇인지 정의합니다.
2. 어떤 요청에서 Skill이 동작해야 하는지 정합니다.
3. 예상 입력과 출력을 정의합니다.
4. Skill 전용 최상위 폴더를 만듭니다.
5. `SKILL.md`를 작성합니다.
6. `agents/openai.yaml`을 작성합니다.
7. 필요한 경우에만 scripts, references, assets를 추가합니다.
8. Skill을 검증하고 패키징합니다.
9. 실제 상황과 비슷한 프롬프트로 테스트합니다.
10. 이 README에 Skill 설명을 추가합니다.

권장 구조:

    new-skill-name/
    |-- SKILL.md
    |-- agents/
    |   `-- openai.yaml
    |-- scripts/       선택 사항
    |-- references/    선택 사항
    `-- assets/        선택 사항

## 다음 Skill 후보

### github-beginner-guide

GitHub 초보자가 따라가기 쉽도록 클릭 위치, 수정할 파일, Commit 방법, 결과 확인 방법까지 단계적으로 안내하는 Skill입니다.

### automation-project-coach

자동화 프로젝트를 처음부터 한 번에 구현하지 않고, 작은 테스트 단위로 나누어 진행하도록 안내하는 Skill입니다.

예상 흐름:

    최소 동작 테스트
    -> 결과 확인
    -> 기능 하나 추가
    -> 다시 테스트
    -> 오류 원인 분리
    -> 안정화
    -> 실제 운영으로 전환

앞으로도 단순히 Skill 개수를 늘리는 것보다, 실제로 반복해서 사용하는 작업이나 선호 방식이 생겼을 때 Skill로 추가할 계획입니다.

## 보안

이 저장소에는 인증정보나 비밀값을 저장하지 않습니다.

커밋하면 안 되는 정보 예시:

- API Key
- Access Token
- 비밀번호
- Slack Webhook URL
- 개인 인증 파일
- 기타 개인 자격 증명

외부 인증정보가 필요한 Skill은 환경 변수, GitHub Secrets 또는 별도의 비밀정보 관리 방식을 사용합니다.

## 현재 상태

현재 첫 번째 Skill인 `one-paste-output`까지 다음 과정을 완료했습니다.

- Skill 설계
- GitHub 저장
- 검증
- `skill.zip` 패키징
- ChatGPT 설치
- 실제 요청 테스트

다음 단계부터는 실제 사용 중 반복적으로 필요했던 작업을 중심으로 새로운 Skill을 추가할 예정입니다.
