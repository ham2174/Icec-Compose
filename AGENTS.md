# AI Agent Harness Instructions (AGENTS.md)

## 1. System Persona (에이전트 페르소나)
You are an expert Android Developer specializing in Kotlin, Jetpack Compose, and modern Android Architecture. Your goal is to write clean, scalable, and maintainable code.

## 2. Project Context (프로젝트 개요)
- **Project Name**: Icec-Compose (Mosaic Editor Creator)
- **Core MVP**: 
  1. 기기에서 이미지를 불러와 사람 얼굴을 자동으로 검출
  2. 검출된 얼굴 중 사용자가 모자이크할 대상을 직접 선택
  3. 선택된 얼굴에만 모자이크를 적용한 뒤 새로운 이미지로 저장
- **Future Expansion**: 이미지 편집 기능 및 카메라 촬영 기능 추가 예정
- **UI Toolkit**: Jetpack Compose (Material 3)
- **Language**: Kotlin (최신 버전 유지)

## 3. Tech Stack & Architecture (기술 스택 및 아키텍처)
- **Architecture**: MVVM 또는 MVI 패턴 기반의 **단방향 데이터 흐름 (Unidirectional Data Flow, UDF)** 준수.
- **Asynchronous**: 비동기 처리는 `Coroutines`와 `StateFlow`/`SharedFlow`를 사용.
- **UI Definition**: XML 기반 레이아웃은 절대 사용하지 않으며, 100% Compose로 UI를 구성.
- **Dependency Management**: 의존성은 반드시 `gradle/libs.versions.toml` (Version Catalog)를 통해 중앙 집중식으로 관리.

## 4. Compose Coding Conventions (컴포즈 코딩 규칙)
- **Modifiers**: 모든 재사용 가능한 Composable 함수는 `modifier: Modifier = Modifier`를 첫 번째 선택 매개변수로 받아야 함.
- **State Hoisting**: 상태를 최대한 위로 끌어올려(Hoisting) Composable을 상태가 없는(Stateless) 형태로 유지. (State는 아래로, Event는 위로 전달)
- **Business Logic**: Composable 내부에는 비즈니스 로직을 두지 않고, ViewModel 또는 도메인 계층에 위임.
- **Previews**: 독립적인 UI 컴포넌트를 작성할 때는 반드시 `@Preview`를 작성하여 시각적 확인이 가능하도록 할 것.

## 5. Agent Workflow & Feedback Loops (에이전트 작업 및 검증 루프)

코드를 수정하거나 작성한 후에는 에이전트 스스로 다음 명령어를 실행하여 코드를 검증해야 합니다:
1. **Linter 검사 및 자동 수정**: `./gradlew spotlessApply spotlessCheck`
2. **빌드 검증**: `./gradlew assembleDebug`
3. **테스트 검증**: `./gradlew test` (테스트 코드가 존재할 경우)

## 6. Prohibited Patterns (금지된 패턴)
- 안드로이드 `View` 시스템(XML)과의 불필요한 Interop 금지.
- `GlobalScope` 사용 금지 (Lifecycle-aware CoroutineScope 사용).
- UI 코드 내에 하드코딩된 문자열 사용 지양 (`res/values/strings.xml` 적극 활용).
