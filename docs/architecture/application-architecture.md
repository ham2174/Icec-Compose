# 애플리케이션 아키텍처

> 상태: Accepted
> SSOT: Git Repository
> 원본: [Notion 기술 설계 및 개발 기획서](https://app.notion.com/p/3d44d984a2188123b909ce5fb78a82ac)
> 최종 검토일: 2026-09-10

## 상태 관리

- 화면 상태는 UDF 기반 MVVM/MVI 스타일로 관리합니다.
- UI는 사용자 의도를 `Action`으로 전달하고 ViewModel은 하나의 `UiState`를 갱신합니다.
- 저장 완료, 오류 안내, 화면 이동처럼 지속할 필요가 없는 동작은 `Effect`로 분리합니다.
- ViewModel은 기본적으로 `commonMain`에 두고 플랫폼 API는 추상화된 계약을 통해 호출합니다.
- 사용자 의도나 상태 전이를 나타낼 가치가 있는 입력만 `Action`으로 정의합니다.
- 각 화면의 `Action → State → Effect` 흐름은 공통 단위 테스트로 검증할 수 있어야 합니다.

```kotlin
sealed interface EditorAction {
    data class FaceClicked(val id: FaceId) : EditorAction
    data object ClearAllClicked : EditorAction
    data object SaveClicked : EditorAction
}

data class EditorUiState(
    val faces: List<FaceUiModel>,
    val isSaving: Boolean,
)

sealed interface EditorEffect {
    data object Saved : EditorEffect
    data class ShowError(val error: EditorError) : EditorEffect
}
```

## Navigation

- 공통 네비게이션은 Navigation 3를 사용합니다.
- 타입 안전한 Route/Key와 back stack을 `commonMain`에서 관리합니다.
- MVP 흐름은 `Home → Gallery → Editor → Result`입니다.
- 분석은 별도 Route가 아니라 Editor의 상태로 표현합니다.
- 화면 이동은 `UiState`에 저장하지 않고 일회성 `Effect` 또는 네비게이션 이벤트로 전달합니다.
- 화면은 서로 직접 참조하지 않고 애플리케이션의 네비게이션 조립을 통해 연결합니다.

## Dependency Injection

- 의존성 주입은 Metro를 사용합니다.
- 플랫폼 독립 계약과 Android/iOS 구현은 Metro 그래프에서 조립합니다.
- ViewModel은 constructor injection을 기본으로 하며 플랫폼 구현에 직접 의존하지 않습니다.
- 초기에는 `@DependencyGraph`, `@Inject`, `@Provides`와 명시적인 그래프 구성을 우선합니다.
- `@ContributesBinding`과 scope aggregation은 멀티모듈 규모에서 실제 필요가 확인된 뒤 도입합니다.
- iOS 빌드와 플랫폼 구현 조립은 정식 구현 과정에서 검증하고 결과를 관련 Spec 또는 ADR에 기록합니다.
