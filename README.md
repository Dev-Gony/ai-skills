# AI Skills

반복해서 사용하는 AI 작업 방식, 출력 규칙, 실무 워크플로를 재사용 가능한 Skill 형태로 정리하는 개인 저장소입니다.

A personal collection of reusable AI Skills for repeatable workflows and practical AI usage.

이 저장소에서는 Skill을 설계하고, 문서화하고, 버전 관리하고, 실제 사용을 통해 개선합니다. 완성된 Skill은 패키징하여 ChatGPT에 설치하고 테스트할 수 있습니다.

## 이 저장소의 목적

매번 같은 요청이나 작업 방식을 다시 설명하지 않고, 반복되는 지침과 워크플로를 재사용 가능한 Skill로 만드는 것이 목적입니다.

이 저장소는 단순한 프롬프트 모음이 아니라, AI 워크플로를 어떻게 설계하고 테스트하고 개선했는지를 기록하는 포트폴리오 역할도 합니다.

## 저장소 구조

각 Skill은 최상위 폴더 하나를 사용합니다.

    ai-skills/
    |-- AGENTS.md
    |-- README.md
    |-- one-paste-output/
    |   |-- SKILL.md
    |   `-- agents/
    |       `-- openai.yaml
    |-- github-beginner-guide/
    |   |-- SKILL.md
    |   `-- agents/
    |       `-- openai.yaml
    `-- automation-project-coach/
        |-- SKILL.md
        `-- agents/
            `-- openai.yaml

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

상태: 제작 완료, 검증 완료, 패키징 완료, ChatGPT 설치 및 실제 테스트 완료

목적:

파일 내용을 사용자가 한 번에 복사하고 붙여넣을 수 있도록, 파일 하나를 하나의 완전한 코드블럭으로 출력합니다.

주요 사용 예시:

- "전체 코드로 줘"
- "한 번에 복붙할 수 있게 줘"
- "수정 부분 말고 전체 파일로 줘"
- "코드블럭 나누지 마"

경로: `one-paste-output/`

### 2. github-beginner-guide

상태: 제작 완료, 검증 완료, 패키징 완료

목적:

GitHub를 처음 사용하는 사람도 따라갈 수 있도록 클릭 위치, 파일 경로, 입력값, Commit 방법, 결과 확인 방법을 단계적으로 안내합니다.

주요 동작:

- 기본적으로 GitHub 웹 UI를 우선 사용
- 필요한 클릭 경로와 정확한 파일 경로를 명시
- 초보자에게 불필요한 Git 명령어 사용을 최소화
- Commit, Branch, Pull Request 같은 용어를 쉽게 설명
- GitHub 연결이 가능하면 실제 저장소 상태를 먼저 확인
- 변경 후 결과 확인 방법을 반드시 안내
- 위험한 복구 명령보다 안전한 방법을 우선
- API Key, Token, Webhook URL 같은 비밀정보 노출 방지

경로: `github-beginner-guide/`

### 3. automation-project-coach

상태: 제작 완료, 검증 완료, 패키징 완료

목적:

자동화 프로젝트나 AI Workflow를 처음부터 한 번에 구현하지 않고, 작은 테스트 단위로 나누어 안정적으로 완성하도록 안내합니다.

다음과 같은 요청에서 사용하도록 설계했습니다.

- 업무 자동화를 만들고 싶다
- Slack, API, 데이터 수집 등을 연결하고 싶다
- AI Agent 또는 Agentic Workflow를 만들고 싶다
- GitHub Actions나 스케줄러로 자동 실행하고 싶다
- 자동화가 실패했는데 어디부터 확인해야 할지 모르겠다
- 개인용 자동화를 실제 운영 단계까지 가져가고 싶다

기본 진행 방식:

    최소 목표 정의
    -> 가장 작은 동작 테스트
    -> 결과 확인
    -> 기능 하나 추가
    -> 다시 테스트
    -> 오류 원인 분리
    -> 안정성 보강
    -> 자동 실행 또는 운영 전환
    -> 첫 실제 실행 확인

주요 동작:

- 사용자가 이미 제공한 정보를 다시 묻지 않음
- 중요한 구조 결정이나 운영 전환 시점에는 확인을 받음
- 사소한 구현 사항마다 불필요하게 확인을 반복하지 않음
- 실패 시 전체 시스템을 다시 만들기보다 실패 지점을 먼저 분리
- Retry, 중복 방지, 상태 저장, 동시 실행, Secret 관리 등 운영 안정성을 필요할 때만 추가
- 비용과 유지보수 부담을 고려해 현재 목적에 맞는 가장 단순한 방법을 우선
- 한 번 실행됐다는 이유만으로 바로 운영 완료로 판단하지 않고 반복 실행 안전성까지 확인

경로: `automation-project-coach/`

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

실제 Skill의 품질이나 재사용성을 높이는 경우에만 추가합니다.

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

현재 세 개의 Skill이 저장소에 있습니다.

- `one-paste-output`: 제작, 검증, 패키징, ChatGPT 설치, 실제 테스트 완료
- `github-beginner-guide`: 제작, 검증, 패키징 완료
- `automation-project-coach`: 제작, 검증, 패키징 완료

앞으로도 Skill 개수를 채우기 위해 만들기보다, 실제 사용 중 반복되는 문제나 작업 방식이 생길 때 추가할 계획입니다.
