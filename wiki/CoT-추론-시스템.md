---
type: 개념
tags: [cot, 추론, 체인오브소트]
updated: 2026-07-03
---

# CoT 추론 시스템

CoT(Chain of Thought)는 모델이 응답을 쓰기 전에 **장면을 계획하는 사고 단계**입니다. NemoEngine에서는 이것도 모듈화되어 있습니다.

## 메인 파이프라인 선택

| 모드 | 용도 |
|---|---|
| **Main CoT** | 최고 품질·일관성. 기본 권장 |
| **Fast CoT** | 모델이 느리거나 가벼운 턴을 원할 때 |
| Loose / Experimental CoT | [[네모넷]]의 추가 변형 |

## 모듈형 CoT 스텝

메인 파이프라인에 필요한 스텝만 끼워 넣을 수 있습니다 (Nemo Engine v10 기준):

| 스텝 | 하는 일 |
|---|---|
| Knowledge Mapping | 누가 무엇을 아는지 지도화 → 마음이론 강화 ([[설계-철학]]) |
| Information Asymmetry | 정보 격차 유지 — 미스터리·배신·수사물 필수 |
| Last Turn Critique | 직전 턴을 자기 비평하고 교정 |
| Character State | 캐릭터의 현재 상태(감정·위치·목표) 추적 |
| Course Correction | 이야기가 어긋났을 때 궤도 수정 |
| Pacing Beats | 페이싱 비트 계획 |
| Narrative Hook | 다음 훅 설계 |
| Voice Crafting | 캐릭터별 목소리 차별화 |
| Subtext Layer | 대사 아래 서브텍스트 |
| Relationship Stage | 관계 단계 추적 |
| Physical Grounding | 물리적 공간·신체 위치 일관성 |
| Emotional Matrix | 감정 매트릭스 |
| Revision Draft | 초안 후 퇴고 |
| HTML Design / Marker Check | [[트래커]] HTML 출력 검증 |
| NSFW Focus | 성인 장면 전용 |

[[네모넷]] v2 추가분: Severity Scale, Freshness Check, Observer Constraints, Thread Budget, GM Planning, Dice & Fate.

## 사용 원칙

- 스텝은 **장면에 도움될 때만** 추가 (수사물 → Knowledge Mapping + Information Asymmetry, 관계 드라마 → Relationship Stage + Emotional Matrix)
- 저토큰/빠른 모델 → Fast CoT + 스텝 최소화
- [[벡스]] 모듈이 `CoT_Main` 변수를 통째로 교체할 수도 있음 — 내레이터마다 생각하는 방식이 다를 수 있게 ([[코어팩-변수-시스템]])
