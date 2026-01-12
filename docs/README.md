# Documentation Index

> **[프로젝트명]** 프로젝트의 전체 문서 목차입니다.

## 📚 문서 구조

모든 문서는 **명세 → 코드 변환** 워크플로우를 따릅니다. AI Agent는 코드를 작성하기 전에 항상 관련 문서를 참조합니다.

---

## 🎯 기획 & 비즈니스

### [PLAN.md](./PLAN.md) - 서비스 기획
- **목적**: 프로젝트의 비즈니스 목표와 핵심 기능 정의
- **독자**: 팀 전체, AI Agent
- **작성 시기**: 프로젝트 시작 전
- **업데이트**: 기능 추가/변경 시

**포함 내용**:
- 비즈니스 목표
- 타겟 사용자
- 핵심 기능
- 성공 지표 (KPI)

---

### [MVP.md](./MVP.md) - MVP 범위 정의
- **목적**: 최소 기능 제품(MVP) 범위 명확화
- **독자**: 팀 전체, AI Agent
- **작성 시기**: 프로젝트 시작 초기
- **업데이트**: MVP 범위 변경 시

**포함 내용**:
- MVP에 포함될 기능
- MVP에서 제외될 기능
- 우선순위 및 이유

---

### [TERMINOLOGY.md](./TERMINOLOGY.md) - 표준 용어 사전
- **목적**: 프로젝트 전체에서 일관된 용어 사용
- **독자**: 팀 전체, AI Agent
- **작성 시기**: 프로젝트 시작 시
- **업데이트**: 새 개념 추가 시

**포함 내용**:
- 도메인 용어 정의
- 코드에서의 표현 (타입명, 테이블명 등)
- 헷갈리기 쉬운 용어 구분

---

## 🏗️ 기술 & 아키텍처

### [ARCHITECTURE.md](./ARCHITECTURE.md) - 기술 스택 및 아키텍처
- **목적**: 프로젝트의 기술적 구조 정의
- **독자**: 개발자, AI Agent
- **작성 시기**: 프로젝트 시작 전
- **업데이트**: 기술 스택 변경 시

**포함 내용**:
- 기술 스택 (Frontend, Backend, DB, AI/ML 등)
- 디렉토리 구조
- 아키텍처 다이어그램
- 개발/빌드/배포 명령어

---

### [DATABASE_SCHEMA.md](./DATABASE_SCHEMA.md) - DB 스키마 설계
> **선택적**: 데이터베이스를 사용하는 프로젝트에만 필요

- **목적**: 데이터베이스 구조 정의
- **독자**: 백엔드 개발자, AI Agent
- **작성 시기**: DB 설계 단계
- **업데이트**: 스키마 변경 시

**포함 내용**:
- ERD (Entity Relationship Diagram)
- 테이블 정의
- 관계 정의
- 인덱스 및 제약 조건

---

### [API_SPEC.md](./API_SPEC.md) - API 명세
> **선택적**: API 또는 Server Actions를 사용하는 프로젝트에만 필요

- **목적**: API 엔드포인트 또는 Server Actions 명세
- **독자**: 프론트엔드/백엔드 개발자, AI Agent
- **작성 시기**: API 설계 단계
- **업데이트**: API 추가/변경 시

**포함 내용**:
- 엔드포인트 목록
- 요청/응답 스키마
- 에러 코드
- 인증/인가 요구사항

---

## 🔄 워크플로우 & 비즈니스 로직

### [WORKFLOW.md](./WORKFLOW.md) - 상세 워크플로우
> **선택적**: 복잡한 비즈니스 플로우가 있는 프로젝트에만 필요

- **목적**: 복잡한 비즈니스 프로세스 시각화
- **독자**: 팀 전체, AI Agent
- **작성 시기**: 복잡한 기능 구현 전
- **업데이트**: 워크플로우 변경 시

**포함 내용**:
- Mermaid 플로우 다이어그램
- 각 단계별 설명
- 예외 처리 로직
- 상태 전이

---

### [USER_FLOW.md](./USER_FLOW.md) - 사용자 흐름
> **선택적**: UX 중심 프로젝트에 유용

- **목적**: 사용자 관점의 흐름 정의
- **독자**: 디자이너, 개발자, AI Agent
- **작성 시기**: UX 설계 단계
- **업데이트**: 사용자 흐름 변경 시

**포함 내용**:
- 사용자 시나리오
- 화면 흐름
- 인터랙션 상세

---

## 📝 문서 작성 가이드

### 문서 작성 원칙

1. **명확성**: 모호한 표현 지양, 구체적으로 작성
2. **완전성**: 구현에 필요한 모든 정보 포함
3. **일관성**: TERMINOLOGY.md의 용어 사용
4. **시각성**: 가능한 다이어그램 활용 (Mermaid)
5. **최신성**: 코드 변경 시 문서도 함께 업데이트

### 문서 업데이트 규칙

- **코드 변경 시**: 관련 문서 즉시 업데이트
- **문서 변경 시**: 영향받는 코드 확인 및 수정
- **새 개념 추가 시**: TERMINOLOGY.md에 먼저 정의

### Mermaid 다이어그램 사용

복잡한 구조나 흐름은 Mermaid 다이어그램으로 표현:

```markdown
# 예시: 인증 플로우

\`\`\`mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant Backend
    participant DB
    
    User->>Frontend: 로그인 요청
    Frontend->>Backend: POST /api/auth/login
    Backend->>DB: 사용자 조회
    DB-->>Backend: 사용자 데이터
    Backend-->>Frontend: JWT 토큰
    Frontend-->>User: 로그인 완료
\`\`\`
```

---

## 🔗 문서 간 관계

```
PLAN.md (비즈니스)
  ↓
MVP.md (범위)
  ↓
ARCHITECTURE.md (기술)
  ↓
DATABASE_SCHEMA.md + API_SPEC.md (상세 설계)
  ↓
WORKFLOW.md (비즈니스 로직)
  ↓
CODE (구현)
```

---

## ✅ 문서 체크리스트

새 프로젝트 시작 시 작성해야 할 문서:

### 필수 문서 (모든 프로젝트)
- [ ] PLAN.md - 서비스 기획
- [ ] ARCHITECTURE.md - 기술 스택
- [ ] TERMINOLOGY.md - 용어 사전

### 권장 문서 (중규모 이상)
- [ ] MVP.md - MVP 범위
- [ ] DATABASE_SCHEMA.md - DB 설계 (DB 사용 시)
- [ ] API_SPEC.md - API 명세 (API 사용 시)

### 선택적 문서 (필요 시)
- [ ] WORKFLOW.md - 복잡한 비즈니스 플로우
- [ ] USER_FLOW.md - 사용자 흐름
- [ ] [기타 도메인별 문서]

---

## 📖 추가 리소스

- [AGENTS.md](../AGENTS.md) - 프로젝트 전역 규칙
- [TODO.md](../TODO.md) - 작업 추적
- [README.md](../README.md) - 프로젝트 소개
