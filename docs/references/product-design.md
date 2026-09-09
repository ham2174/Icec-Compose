# 제품·UX·디자인 참조

> 상태: Reference
> SSOT: 각 연결된 원본
> 최종 검토일: 2026-09-10

## Notion

- [제품 요구사항 정의서](https://app.notion.com/p/3d34d984a2188170bf31c07223f05a15): 제품 범위, MVP와 Non-Goal의 SSOT.
- [UX 기획서](https://app.notion.com/p/3d54d984a2188163b1e7ce4b8fcca0c2): 사용자 흐름, 상태와 UX 정책의 허브.
- [UX Decisions](https://app.notion.com/p/82be31e917d94f8691c404764df5666c): `UX-###` 결정의 상태, 근거와 요약.
- [프로젝트 진행 현황](https://app.notion.com/p/3d64d984a21881beaa6de45bd2ba196f): 원본 SSOT 결과를 요약하는 Dashboard.
- [개발 문서 이전 안내](https://app.notion.com/p/3d44d984a2188123b909ce5fb78a82ac): Git으로 이전된 과거 개발 SSOT의 포인터.

## Figma

- [ICEC MVP](https://www.figma.com/design/K8uqTjJDkBnC1lNxfuICv0/ICEC?node-id=40-428): 현재 MVP 화면과 Prototype의 시각 기준.
- [ICEC Design System](https://www.figma.com/design/Jn0xf2CaB8ZMPWWo3K0Ina/ICEC-Design-System): Design System 후보 파일. 공식 SSOT 승격 여부와 Variables, Styles, Components 구성은 Design Planning에서 확정합니다.

## 연결 원칙

구현은 임의로 시각 결과를 추측하지 않습니다. 관련 Notion 요구사항과 승인된 Figma 노드를 확인한 뒤 Repository의 Compose 계약과 코드를 함께 갱신합니다. Figma Code Connect를 도입한다면 반복 사용되는 디자인 시스템 컴포넌트에 한정하고 별도 ADR로 결정합니다.
