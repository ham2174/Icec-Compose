# Agent Execution Rule

* 작업을 진행할 때 사용자에게 진행 여부나 허락을 묻지 말고, 바로 다음 작업을 자율적으로 판단하여 연속적으로 실행할 것.

# AI Agent Harness Instructions (Icec-Compose)

## 1. 프로젝트 목적 및 컨텍스트
- 본 프로젝트는 `Icec-Compose`라는 이름의 Android Jetpack Compose 기반 애플리케이션입니다.
- AI 에이전트는 이 문서의 규칙과 피드백 루프를 기반으로 자율적으로 코드를 작성하고 검증합니다.

## 2. 코딩 컨벤션 및 아키텍처
- **UI Toolkit**: Jetpack Compose 전용. XML 레이아웃 사용을 지양합니다.
- **Architecture**: MVI 또는 MVVM 기반의 단방향 데이터 흐름(UDF)을 권장합니다.
- **Language**: Kotlin (최신 버전 유지).

## 3. 피드백 루프 (Feedback Loop) 규칙
AI 에이전트는 코드를 수정하거나 작성한 후, 반드시 다음의 피드백 루프를 거쳐 자신의 코드를 스스로 검증해야 합니다.
1. **Lint 검증**: `ktlint` 또는 `detekt` (설정 예정)를 통한 정적 분석
2. **빌드 검증**: `./gradlew assembleDebug`를 실행하여 컴파일 오류 확인
3. **테스트 검증**: `./gradlew test`를 실행하여 유닛 테스트 통과 여부 확인

## 4. 도구 및 자동화
- 새 기능을 구현하기 전에, 필요한 경우 스크래치 스크립트(`/scratch`)를 활용하여 사전 검증을 수행합니다.
- 의존성 추가나 설정 변경 시, 항상 `build.gradle.kts` 파일의 정합성을 확인합니다.
