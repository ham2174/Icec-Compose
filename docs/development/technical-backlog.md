# 기술 백로그

> 상태: Planned
> SSOT: Git Repository
> 원본: [Notion 기술 설계 및 개발 기획서](https://app.notion.com/p/3d44d984a2188123b909ce5fb78a82ac)
> 최종 검토일: 2026-09-10

아래 항목은 Architecture v1의 확정 구현 규칙이 아닙니다. 구현 전에 설계를 구체화하고, 확정 결과를 Spec 또는 ADR로 승격해야 합니다.

## Editor

- Pinch Zoom과 Pan의 상태 모델 및 제스처 우선순위
- 이미지 좌표계와 화면 좌표계 변환, inverse transform과 얼굴 hit-test
- Zoom/Pan 중 사진, Bounding Box와 Mosaic Preview의 정합성
- 선택된 얼굴, Zoom/Pan과 저장 직전 상태의 생명주기 및 복원 범위

## 미디어와 렌더링

- EXIF orientation과 Android/iOS 좌표계 차이
- 고해상도 이미지의 decode, downsampling, memory pressure와 OOM 대응
- 모자이크 블록 크기와 출력 해상도 정책
- MediaStore와 Photos 저장 결과의 공통 모델 및 오류 매핑

## 플랫폼 연동

- Kotlin/Native와 iOS ML Kit Face Detection 연동
- Android/iOS 제한 사진 접근 권한과 재요청 가능 상태 모델
- iOS 26 Liquid Glass 적용 범위와 하위 버전 폴백
- Metro의 iOS 그래프 조립과 빌드 호환성

## 검증 기반

- 대표 Android/iOS 기준 기기
- 승인된 테스트 이미지와 골든 이미지 세트
- 벤치마크 반복 횟수, warm-up과 회귀 허용 범위
- CI에서 실행할 iOS 통합 테스트의 blocking 범위
