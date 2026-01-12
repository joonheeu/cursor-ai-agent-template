# AGENTS.md - Control Tower

## Project Context & Operations

### Business Goal
**[프로젝트명]** is [프로젝트 설명 - 비즈니스 목표, 해결하려는 문제, 타겟 사용자]

### Tech Stack
> 프로젝트의 기술 스택을 명시하세요. Monorepo가 아닌 경우 해당 섹션 제거 가능.

#### ⭐ Package Manager (필수)
> **중요**: 프로젝트 전체에서 일관된 패키지 매니저를 사용해야 합니다.

- **선택한 패키지 매니저**: [npm/pnpm/yarn/bun 중 하나 명시] ⭐
- **Lock 파일**: [package-lock.json/pnpm-lock.yaml/yarn.lock/bun.lockb]

**규칙**:
- 모든 개발 명령어는 선택한 패키지 매니저를 사용
- 다른 패키지 매니저의 lock 파일은 .gitignore에 추가
- 문서의 모든 명령어 예시도 선택한 패키지 매니저로 작성

#### Stack
- **Framework**: [Next.js/React/Vue 등]
- **Database**: [PostgreSQL/MySQL/MongoDB 등]
- **ORM**: [Prisma/Drizzle/TypeORM 등]
- **AI/ML**: [사용하는 AI 서비스]
- **기타**: [기타 주요 기술]

### Operational Commands
> 개발 시 자주 사용하는 명령어를 정의하세요.
> ⚠️ **중요**: 모든 명령어는 위에서 선택한 패키지 매니저를 사용해야 합니다!

**Development**
```bash
[패키지매니저] run dev # 개발 서버 시작
[패키지매니저] run build # 프로덕션 빌드
[패키지매니저] test # 테스트 실행
```

**예시** (pnpm 사용 시):
```bash
pnpm dev          # 개발 서버 시작
pnpm build        # 프로덕션 빌드
pnpm test         # 테스트 실행
pnpm lint         # 린트 실행
```

**Database** (해당하는 경우)
```bash
[패키지매니저] run db:migrate # 마이그레이션 실행
[패키지매니저] run db:studio # DB GUI 열기
```

## Golden Rules (Immutable)

### 1. Architecture Principles
> 프로젝트의 핵심 아키텍처 원칙을 정의하세요.

- **[원칙 1]**: [설명]
- **[원칙 2]**: [설명]

**예시**:
- **컴포넌트 구조**: UI 컴포넌트는 `components/ui/` 에 위치. 비즈니스 로직은 `lib/` 에 위치.
- **Import 규칙**: 절대 경로 임포트 사용 (`@/components/*`)

### 2. Security & Data
> 보안 관련 필수 규칙을 정의하세요.

- **환경 변수**: 절대 클라이언트에 노출되는 환경 변수 접두사(`NEXT_PUBLIC_`, `VITE_` 등)에 시크릿 저장 금지
- **입력 검증**: 모든 사용자 입력은 Zod 또는 유사한 검증 라이브러리로 검증
- **인증/인가**: [인증 전략 명시 - NextAuth, Supabase Auth 등]

### 3. [프로젝트명] Terminology
> 프로젝트 고유의 용어를 정의하세요. 일관된 용어 사용은 AI Agent의 이해도를 높입니다.

- **[용어 1]**: [설명 - 코드에서 어떻게 표현되는지]
- **[용어 2]**: [설명]

**예시**:
- **Task**: 사용자가 생성하는 작업 단위 (코드: `Task` 타입/테이블)
- **Workspace**: 여러 Task를 그룹화하는 단위 (코드: `Workspace` 타입/테이블)

## Context Map (Action-Based Routing)

> 작업 유형에 따라 참조해야 할 AGENTS.md 파일 위치를 명시하세요.
> AI Agent가 작업 시작 전 올바른 규칙을 찾을 수 있도록 안내합니다.

### 앱 레벨
- **[Frontend App](./app/AGENTS.md)** — 프론트엔드 애플리케이션 규칙 (존재 시)
- **[Backend API](./api/AGENTS.md)** — 백엔드 API 규칙 (존재 시)

### 세부 디렉토리
> 프로젝트 구조에 맞게 수정하세요.

- **[Components](./components/AGENTS.md)** — UI 컴포넌트 구조 및 규칙
- **[Lib/Utils](./lib/AGENTS.md)** — 유틸리티 및 비즈니스 로직
- **[Types](./types/AGENTS.md)** — TypeScript 타입 정의 규칙
- **[Hooks](./hooks/AGENTS.md)** — 커스텀 React Hooks 규칙 (React 프로젝트)
- **[Actions](./actions/AGENTS.md)** — Server Actions 규칙 (Next.js App Router)

### 문서
- **[TODO](./TODO.md)** — 개발 작업 목록 및 진행상황
- **[Documentation](./docs/README.md)** — 전체 문서 목차 및 가이드

## 🚀 프로젝트 초기화 프로세스

### AI Agent 작업 순서 (템플릿 사용 시)

템플릿을 클론한 직후, AI Agent는 다음 순서로 프로젝트를 초기화해야 합니다:

#### Step 1: 사용자와 초기 대화
- **문서**: [GETTING_STARTED.md](./GETTING_STARTED.md) 참조
- **목적**: 프로젝트 기본 정보, 기술 스택, 패키지 매니저 결정
- **핵심 질문**:
  1. 프로젝트명과 설명
  2. **패키지 매니저 선택** (npm/pnpm/yarn/bun) ⭐
  3. 프론트엔드 프레임워크
  4. 데이터베이스 사용 여부
  5. 프로젝트 초기화 방식

#### Step 2: 문서 업데이트
1. 이 파일(AGENTS.md) 업데이트
   - [프로젝트명] 대체
   - **패키지 매니저 명시** ⭐
   - Tech Stack 작성
   - Operational Commands 업데이트
2. docs/ 폴더 문서 작성
   - PLAN.md, ARCHITECTURE.md, TERMINOLOGY.md, MVP.md
3. TODO.md 작성
   - Phase별 작업 분해

#### Step 3: 프로젝트 초기화 (선택 시)
- **문서**: [PROJECT_INIT_GUIDE.md](./PROJECT_INIT_GUIDE.md) 참조
- **방법**: 임시 폴더 전략 사용 (충돌 방지)
- **주의**: create-next-app 등은 빈 폴더 요구 → 템플릿 파일과 충돌

#### Step 4: 환경 설정
- .env.example 업데이트
- package.json 설정
- .gitignore 확인

#### Step 5: 첫 커밋
```bash
git add .
git commit -m "docs: initialize project documentation"
```

---

## TODO.md 사용 가이드

**[TODO.md](./TODO.md)**는 프로젝트의 모든 개발 작업을 추적하는 중앙 허브입니다.

### 📖 빠른 시작

1. **작업 선택**
   ```bash
   # TODO.md 열기
   # "빠른 참조" 섹션에서 다음 우선순위 확인
   # Phase별로 정리된 작업 목록에서 선택
   ```

2. **작업 시작 전 체크리스트**
   - [ ] 참조 문서 읽기 (각 작업에 명시됨)
   - [ ] 관련 AGENTS.md 확인
   - [ ] 의존성 작업 완료 여부 확인
   - [ ] 브랜치 생성: `git checkout -b feature/task-name`

3. **작업 완료 후**
   - [ ] TODO.md에서 체크박스 체크 `[ ]` → `[x]`
   - [ ] Phase별 진행률 업데이트
   - [ ] 영향받는 문서 업데이트 (작업에 명시된 경우)
   - [ ] 커밋 및 PR

### 🗺️ 문서-코드 연결

모든 작업은 [docs](./docs/) 폴더의 명세서를 코드로 변환하는 것:

| 작업 | 참조 문서 | 코드 위치 |
|------|----------|----------|
| [작업 유형 1] | [문서명.md](./docs/문서명.md) | `path/to/code` |
| [작업 유형 2] | [문서명.md](./docs/문서명.md) | `path/to/code` |

**예시**:
| 작업 | 참조 문서 | 코드 위치 |
|------|----------|----------|
| DB 스키마 | [DATABASE_SCHEMA.md](./docs/DATABASE_SCHEMA.md) | `prisma/schema.prisma` |
| API 구현 | [API_SPEC.md](./docs/API_SPEC.md) | `app/api/**/*.ts` |
| 워크플로우 | [WORKFLOW.md](./docs/WORKFLOW.md) | 워크플로우 UI/로직 |

### 🎯 주요 원칙

1. **문서 우선**: 코드 작성 전 반드시 참조 문서를 읽고 명세 준수
2. **체크박스 업데이트**: 작업 완료 즉시 TODO.md 체크박스 체크
3. **문서 동기화**: 코드 변경 시 관련 문서도 함께 업데이트 (필요 시)
4. **Phase 순서**: 의존성 때문에 Phase 순서대로 작업 권장

### 📚 필수 문서

작업 시작 전 필독:
- [PLAN.md](./docs/PLAN.md) — 서비스 기획 및 비즈니스 목표
- [MVP.md](./docs/MVP.md) — MVP 범위 및 우선순위 (존재 시)
- [ARCHITECTURE.md](./docs/ARCHITECTURE.md) — 기술 스택 및 아키텍처
- [TERMINOLOGY.md](./docs/TERMINOLOGY.md) — 표준 용어 사전

## AI Agent 작업 진행 원칙

### 📝 작업 전후 커뮤니케이션 규칙

AI Agent는 모든 작업을 시작하기 전과 완료한 후에 **명확한 설명**을 제공해야 합니다.

#### 🎯 작업 시작 전 (Pre-Work Briefing)

작업을 시작하기 전에 다음 정보를 **간단하고 명확하게** 제공하세요:

**포함 사항:**
```
✅ 지금 할 작업: [작업명 (Phase X.X.X)]
✅ 작업 목표: [한 줄 설명]
✅ 수정할 파일: [예상 파일 목록 2-5개]
✅ 예상 소요: [간단/보통/복잡]
✅ 참조 문서: [링크 또는 파일명]
```

**예시:**
```
🚀 작업 시작: Phase 1.1.1 - 데이터베이스 스키마 작성

작업 목표: DATABASE_SCHEMA.md의 ERD를 Prisma 스키마로 구현합니다.

수정할 파일:
- prisma/schema.prisma (신규)
- .env.example (환경 변수 추가)

예상 소요: 보통 (10-15분)
참조 문서: docs/DATABASE_SCHEMA.md

진행하겠습니다!
```

#### 🎉 작업 완료 후 (Post-Work Summary)

작업을 완료한 후에 다음 정보를 **요약하여** 제공하세요:

**포함 사항:**
```
✅ 완료한 작업: [작업명]
✅ 주요 변경사항:
  - [변경사항 1]
  - [변경사항 2]
  - [변경사항 3]
✅ 생성/수정한 파일: [파일 목록]
✅ 테스트 결과: [통과/실패/해당없음]
✅ TODO 업데이트: [체크박스 상태]
✅ 커밋 메시지: [커밋 해시 + 메시지]
✅ 다음 작업: [다음 작업명]
```

**예시:**
```
✅ Phase 1.1.1 완료: 데이터베이스 스키마 작성

주요 변경사항:
- User, Project, Task 테이블 정의
- 관계(relations) 및 인덱스 설정
- 환경 변수 예시 추가

생성한 파일:
- prisma/schema.prisma
- .env.example

테스트: 타입 체크 통과 ✅

TODO 업데이트:
- [x] 1.1.1 데이터베이스 스키마 작성 (100%)
- Phase 1 진행률: 1/5 (20%)

커밋: a1b2c3d - feat(db): define database schema with Prisma

다음 작업: 1.1.2 - Prisma 마이그레이션 실행
계속 진행하시겠습니까?
```

#### ⚡ 간결성 원칙

- **작업 시작 전**: 5-10줄 이내로 간단하게
- **작업 완료 후**: 10-20줄 이내로 요약
- 불필요한 장황한 설명 지양
- 핵심 정보만 전달
- 이모지 활용으로 가독성 향상 ✅

#### 🚫 피해야 할 것

- ❌ 설명 없이 바로 작업 시작
- ❌ 작업 완료 후 "완료했습니다"만 말하기
- ❌ 너무 기술적이거나 장황한 설명
- ❌ 다음 단계 안내 생략

---

## Git Workflow Automation (AI Agent)

이 프로젝트는 **Gitflow 전략**을 따릅니다. AI Agent는 다음 규칙에 따라 **자동으로** 브랜치 작업을 수행합니다.

### 📋 브랜치 전략 개요

- **main**: 프로덕션 배포 (안정 버전만)
- **develop**: 개발 통합 브랜치 (기본 작업 기준점)
- **feature/\***: 기능 개발 브랜치 (develop에서 분기 → develop으로 머지)
- **release/\***: 릴리스 준비 브랜치 (develop → main + develop 양방향 머지)
- **hotfix/\***: 긴급 수정 브랜치 (main → main + develop 양방향 머지)

### 🤖 AI Agent 자동화 규칙

#### 1. **브랜치 네이밍 규칙**

| 작업 유형 | 브랜치 이름 형식 | 예시 |
| ---------------------- | ------------------------------------- | --------------------------------------- |
| Phase 단위 기능 개발 | `feature/{phase-number}-{task-name}` | `feature/1.1-database-setup` |
| 단일 작업 기능 개발 | `feature/{task-name}` | `feature/auth-system` |
| 버그 수정 | `feature/fix-{bug-description}` | `feature/fix-login-redirect` |
| 릴리스 준비 | `release/{version}` | `release/0.1.0` |
| 긴급 수정 (프로덕션) | `hotfix/{issue-description}` | `hotfix/critical-auth-bug` |

#### 2. **자동 브랜치 생성 트리거**

AI Agent는 다음 조건에서 **자동으로 새 브랜치를 생성**합니다:

| 트리거 | 브랜치 생성 조건 | 액션 |
| ------------------------------------- | --------------------------------------------------- | --------------------------------------------------------- |
| 새 Phase 시작 | 이전 Phase가 완료되고 다음 Phase의 첫 작업 시작 | `feature/{next-phase-number}-{phase-name}` 생성 |
| 독립적인 기능 추가 | TODO.md에서 독립적인(Phase 외부) 작업 시작 | `feature/{task-name}` 생성 |
| 사용자가 "다음 Phase 진행" 요청 | Phase 완료 후 명시적 요청 | 현재 브랜치 머지 → 새 Phase 브랜치 생성 |

**예시:**
```bash
# Phase 1 완료 → Phase 2 시작
feature/1.4-project-management (완료)
→ develop으로 머지
→ feature/2.1-api-integration 생성
```

#### 3. **자동 머지 트리거 (⭐ 핵심)**

AI Agent는 다음 조건에서 **자동으로 develop으로 머지**합니다:

| 조건 | 머지 트리거 | 머지 후 액션 |
| ------------------------------------- | --------------------------------------------------- | --------------------------------------------------------- |
| **Phase 100% 완료** | TODO.md에서 Phase 진행률이 100% 도달 | `develop`으로 머지 → 브랜치 삭제 → 다음 Phase 브랜치 생성 |
| **사용자 명시적 요청** | "머지해줘", "다음 작업 진행해줘" (Phase 완료 시) | 즉시 머지 |
| **독립 작업 완료** | Phase 외부 작업 완료 (TODO에 단일 작업으로 명시됨) | `develop`으로 머지 → 브랜치 삭제 |

**자동 머지 절차:**
```bash
# 1. 현재 브랜치 최종 커밋 확인
git log -1 --oneline

# 2. develop으로 전환 및 최신화
git checkout develop
git pull origin develop

# 3. feature 브랜치 머지 (--no-ff: 머지 커밋 생성)
git merge --no-ff feature/브랜치명 -m "merge: complete Phase X - 설명"

# 4. 원격에 푸시
git push origin develop

# 5. feature 브랜치 삭제 (로컬 + 원격)
git branch -d feature/브랜치명
git push origin --delete feature/브랜치명
```

#### 4. **머지 전 검증 체크리스트**

AI Agent는 머지 전 다음을 **자동으로 확인**합니다:

- [ ] TODO.md에서 해당 Phase/작업이 100% 완료 상태
- [ ] 모든 파일이 커밋되었음 (`git status` clean)
- [ ] 빌드 에러 없음 (가능하면 빌드 실행)
- [ ] 커밋 메시지가 Conventional Commits 준수
- [ ] 참조 문서 업데이트 완료 (작업에 명시된 경우)

**검증 실패 시:**
- 머지하지 않고 사용자에게 문제 보고
- 수정 후 재시도 안내

#### 5. **자동 브랜치 정리**

- **머지 완료 후**: 로컬 및 원격 feature 브랜치 즉시 삭제
- **오래된 브랜치**: 30일 이상 작업 없는 브랜치 → 사용자에게 삭제 제안 (자동 삭제 X)

#### 6. **릴리스 및 핫픽스 (수동 트리거)**

릴리스와 핫픽스는 **사용자의 명시적 요청**에만 수행:

- 사용자가 "릴리스 준비해줘" 요청 → `release/{version}` 생성
- 사용자가 "긴급 수정 필요" 요청 → `hotfix/{description}` 생성

### 🎯 실전 시나리오

#### 시나리오 1: Phase 완료 후 다음 작업 요청

```
사용자: "다음 작업 진행해줘"
AI 판단: Phase 1 완료 (5/5) → Phase 2 시작

AI 액션:
1. ✅ 현재 브랜치(feature/1.4-project-management) develop으로 머지
2. ✅ 브랜치 삭제
3. ✅ feature/2.1-api-integration 생성
4. ✅ Phase 2 첫 작업 시작
```

#### 시나리오 2: Phase 진행 중

```
사용자: "다음 작업 진행해줘"
AI 판단: Phase 1 진행 중 (3/5) → 같은 브랜치에서 계속

AI 액션:
1. ✅ 현재 브랜치 유지
2. ✅ 다음 작업 시작
3. ⚠️ 머지하지 않음 (Phase 미완료)
```

#### 시나리오 3: 독립 작업 완료

```
사용자: "로그 시스템 구현 완료, 다음 작업 진행해줘"
AI 판단: 독립 작업 완료 → 머지 필요

AI 액션:
1. ✅ feature/logging-system → develop 머지
2. ✅ 브랜치 삭제
3. ✅ 다음 작업용 새 브랜치 생성 (또는 기존 Phase 브랜치)
```

### ⚠️ 주의사항

- **main 브랜치는 직접 터치하지 않음** (릴리스/핫픽스 전용)
- **develop 최신화 필수**: 머지 전 항상 `git pull origin develop`
- **충돌 발생 시**: 자동 해결 시도 → 실패 시 사용자에게 보고
- **커밋 메시지**: 항상 Conventional Commits 형식 준수

### 📚 참고 문서

프로젝트 루트의 `.cursor/rules/` 폴더에 Git 워크플로우 규칙이 정의되어 있습니다:

- [Gitflow 워크플로우](./.cursor/rules/gitflow.mdc)
- [커밋 컨벤션](./.cursor/rules/commit-convention.mdc)
- [스테이징 가이드라인](./.cursor/rules/staging-guidelines.mdc)

---

## Maintenance Policy
이 파일은 **프로젝트 전역 규칙의 단일 소스(SSOT)**입니다. 코드가 이 규칙과 다르면, 코드를 수정하거나 이 파일에서 규칙 변경을 제안하세요.

### Fractal Governance
- **구조적 AGENTS.md**: 모든 주요 구조 디렉토리 (예: `actions/`, `components/`, `lib/`)는 자체 `AGENTS.md` 파일을 가져야 합니다.
- **상속**: 하위 디렉토리는 부모 `AGENTS.md`의 규칙을 상속받지만 더 구체적인 규칙을 정의할 수 있습니다.
- **생성 규칙**: 새로운 주요 디렉토리를 만들 때, 즉시 그 안에 `AGENTS.md`를 생성하여 범위와 규칙을 정의해야 합니다.
