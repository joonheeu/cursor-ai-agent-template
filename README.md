# Cursor AI Agent Development Template

> **AI Agent 주도 개발을 위한 프로젝트 템플릿**  
> Cursor AI와 함께하는 체계적이고 효율적인 개발 환경

## 📌 특징

- 🤖 **AI Agent 친화적 구조**: AGENTS.md를 통한 계층적 규칙 관리
- 📋 **작업 추적 시스템**: TODO.md 기반 Phase별 개발 관리
- 📚 **문서 중심 개발**: 명세 → 코드 변환 워크플로우
- 🔄 **Gitflow 자동화**: AI Agent가 브랜치/머지를 자동으로 관리
- ✅ **품질 보증**: 커밋 컨벤션, 스테이징 가이드라인 내장

## 🚀 빠른 시작

### 사용 방법 선택

이 템플릿은 **2가지 방법**으로 사용할 수 있습니다:

#### 📘 방법 1: 새 프로젝트 시작 (추천)

GitHub에서 "Use this template" 버튼을 클릭하거나:

```bash
# 직접 클론하여 사용
git clone https://github.com/YOUR_USERNAME/cursor-ai-agent-template.git your-project-name
cd your-project-name
rm -rf .git
git init
```

→ **[방법 1 상세 가이드](#1-템플릿-가져오기-새-프로젝트)** 아래 참조

---

#### 🔧 방법 2: 기존 프로젝트에 적용

이미 개발 중인 프로젝트에 이 구조를 추가할 수 있습니다!

```bash
# 기존 프로젝트에서 AI Agent에게 요청:
"이 템플릿을 적용해줘: https://github.com/YOUR_USERNAME/cursor-ai-agent-template"
```

AI Agent가 자동으로:
- ✅ 기존 프로젝트 분석 (기술 스택, 구조, 패키지 매니저)
- ✅ 템플릿 파일 선택적으로 추가 (충돌 방지)
- ✅ 기존 코드 100% 유지하면서 문서 구조만 추가
- ✅ 프로젝트에 맞게 AGENTS.md, TODO.md 자동 생성

→ **상세 가이드**: [APPLY_TO_EXISTING_PROJECT.md](./APPLY_TO_EXISTING_PROJECT.md)

---

## 📘 방법 1: 새 프로젝트 시작

### 1. 템플릿 가져오기

GitHub에서 "Use this template" 버튼을 클릭하거나:

```bash
# 직접 클론하여 사용
git clone https://github.com/YOUR_USERNAME/cursor-ai-agent-template.git your-project-name
cd your-project-name
rm -rf .git
git init
```

### 2. AI Agent와 초기 대화 🤖

**중요**: 직접 수정하지 말고, AI Agent에게 다음과 같이 요청하세요:

```
"GETTING_STARTED.md를 참조하여 프로젝트를 초기화해줘"
```

AI Agent가 다음을 자동으로 수행합니다:

1. **프로젝트 정보 수집**
   - 프로젝트명, 설명, 타겟 사용자
   - **패키지 매니저 선택** (npm/pnpm/yarn/bun) ⭐ 중요!
   - 기술 스택 (프레임워크, DB, AI/ML 등)
   - 초기화 방식 (create-next-app 사용 등)

2. **문서 자동 생성**
   - AGENTS.md 업데이트 (패키지 매니저 명시 포함)
   - docs/ 폴더 문서 작성 (PLAN, ARCHITECTURE, TERMINOLOGY, MVP)
   - TODO.md Phase 구성

3. **프로젝트 초기화** (선택 시)
   - 프레임워크 보일러플레이트 설정
   - 임시 폴더 전략으로 충돌 방지
   - 의존성 설치

4. **첫 커밋 생성**

**상세 가이드**: [GETTING_STARTED.md](./GETTING_STARTED.md)

### 3. 개발 시작

초기화가 완료되면:

```
"TODO.md의 Phase 1.1.1 작업을 시작해줘"
```

AI Agent가 TODO.md를 보고 작업을 진행합니다.

## 📁 디렉토리 구조

```
.
├── AGENTS.md                    # 프로젝트 제어 타워 (전역 규칙)
├── TODO.md                      # 작업 추적 허브
├── README.md                    # 프로젝트 소개 (이 파일)
│
├── GETTING_STARTED.md           # AI Agent 초기 대화 가이드 (새 프로젝트)
├── PROJECT_INIT_GUIDE.md        # 프레임워크 초기화 가이드 (새 프로젝트)
├── APPLY_TO_EXISTING_PROJECT.md # 기존 프로젝트 적용 가이드 ⭐
│
├── docs/                        # 프로젝트 문서
│   ├── README.md                # 문서 목차
│   ├── PLAN.md                  # 서비스 기획
│   ├── MVP.md                   # MVP 범위
│   ├── ARCHITECTURE.md          # 기술 스택
│   ├── DATABASE_SCHEMA.md       # DB 설계 (템플릿)
│   ├── API_SPEC.md              # API 명세 (템플릿)
│   ├── TERMINOLOGY.md           # 용어 사전
│   └── ...                      # 기타 명세서
│
├── .cursor/                     # Cursor IDE 규칙
│   └── rules/
│       ├── gitflow.mdc          # Gitflow 워크플로우
│       ├── commit-convention.mdc # 커밋 컨벤션
│       └── staging-guidelines.mdc # 스테이징 가이드
│
├── .env.example                 # 환경 변수 예시
├── .gitignore
├── package.json                 # 기본 패키지 파일
└── [your-project-files]         # 실제 프로젝트 파일들
```

## 🎯 핵심 개념

### 1. AGENTS.md - 프로젝트 제어 타워

모든 AI Agent는 작업 전 `AGENTS.md`를 참조합니다:

- **계층적 구조**: 루트 AGENTS.md → 디렉토리별 AGENTS.md
- **규칙 상속**: 하위 디렉토리는 상위 규칙을 상속받고 세부 규칙 추가
- **컨텍스트 맵**: 작업별로 참조할 AGENTS.md 위치 안내

### 2. TODO.md - 작업 추적 허브

프로젝트의 모든 개발 작업을 체계적으로 관리:

- **Phase별 구조**: 큰 작업을 Phase로 나누고, 각 Phase를 작은 작업으로 분해
- **문서 연결**: 각 작업마다 참조할 docs/*.md 파일 명시
- **진행률 추적**: 체크박스로 완료 여부 표시, Phase별 진행률 시각화
- **작업 체크리스트**: 작업 시작 전 필수 확인사항 명시

### 3. docs/ - 명세 중심 개발

코드 작성 전 명세를 먼저 작성:

```
명세 작성 (docs/*.md) → 검토 및 승인 → 코드 구현 → 문서 업데이트
```

### 4. Git Workflow 자동화

AI Agent가 자동으로 브랜치 관리:

- **자동 브랜치 생성**: Phase 시작 시 `feature/{phase-number}-{phase-name}` 생성
- **자동 머지**: Phase 100% 완료 시 develop으로 자동 머지
- **커밋 컨벤션**: Conventional Commits 자동 적용

## 📖 사용 가이드

### AI Agent에게 작업 요청하기

```
# ✅ 좋은 예시
"TODO.md의 Phase 1.1.1 작업을 시작해줘"
"다음 작업 진행해줘"
"Phase 2 완료 후 머지해줘"

# ❌ 나쁜 예시
"로그인 기능 만들어줘" (TODO.md 없이 요청)
"DB 스키마 작성해줘" (문서 참조 없이 요청)
```

### AI Agent 작업 흐름

1. **작업 선택**: TODO.md에서 다음 작업 확인
2. **문서 읽기**: 참조 문서(docs/*.md) 읽고 명세 파악
3. **규칙 확인**: 관련 AGENTS.md 읽고 규칙 준수
4. **브리핑**: 작업 시작 전 간단히 설명
5. **구현**: 코드 작성 및 테스트
6. **커밋**: Conventional Commits 준수
7. **TODO 업데이트**: 체크박스 체크, 진행률 업데이트
8. **요약**: 작업 완료 후 주요 변경사항 요약
9. **자동 머지**: Phase 완료 시 develop으로 머지

### 문서 작성 가이드

#### 1. PLAN.md (서비스 기획)
```markdown
# 프로젝트명

## 비즈니스 목표
- 해결하려는 문제
- 타겟 사용자
- 핵심 가치 제안

## 핵심 기능
1. 기능 1
2. 기능 2
...
```

#### 2. ARCHITECTURE.md (기술 스택)
```markdown
# 기술 아키텍처

## Tech Stack
- Frontend: ...
- Backend: ...
- Database: ...
- AI/ML: ...

## 디렉토리 구조
...
```

#### 3. DATABASE_SCHEMA.md (DB 설계)
```markdown
# 데이터베이스 스키마

## ERD
(Mermaid 다이어그램)

## 테이블 정의
### User
...
```

## ⭐ 패키지 매니저 일관성 (중요!)

### 왜 중요한가요?

프로젝트에서 **하나의 패키지 매니저만 일관되게 사용**하는 것은 매우 중요합니다:

```
✅ 일관된 의존성 버전 관리
✅ Lock 파일 충돌 방지
✅ 빌드 재현성 보장
✅ 팀 협업 시 혼란 방지
✅ AI Agent가 올바른 명령어 사용
```

### 설정 방법

1. **초기화 시 선택**
   - AI Agent가 처음에 "어떤 패키지 매니저를 사용하시나요?" 질문
   - npm, pnpm, yarn, bun 중 선택

2. **AGENTS.md에 명시**
   ```markdown
   ### Tech Stack
   - **선택한 패키지 매니저**: pnpm ⭐
   ```

3. **프로젝트 전체에서 일관되게 사용**
   ```bash
   # ✅ 올바른 사용 (pnpm 선택 시)
   pnpm install
   pnpm dev
   pnpm build
   
   # ❌ 잘못된 사용 (다른 패키지 매니저 혼용)
   npm install  # 금지!
   yarn dev     # 금지!
   ```

4. **다른 Lock 파일 제거**
   ```bash
   # pnpm 사용 시
   rm package-lock.json yarn.lock  # npm, yarn lock 삭제
   
   # .gitignore에 추가
   package-lock.json  # npm 사용 시 제외
   yarn.lock          # yarn 사용 시 제외
   pnpm-lock.yaml     # pnpm 사용 시 제외
   ```

---

## 🛠️ 커스터마이징

### AGENTS.md 수정하기

1. **프로젝트 컨텍스트 수정**:
   ```markdown
   ### Business Goal
   **[프로젝트명]** is [프로젝트 설명]
   
   ### Tech Stack (Monorepo)
   - **Monorepo Tool**: [도구명]
   - **Package Manager**: [패키지 매니저]
   ...
   ```

2. **용어 정의**:
   ```markdown
   ### 3. [프로젝트명] Terminology
   - **용어1**: 설명
   - **용어2**: 설명
   ```

3. **Context Map 업데이트**:
   프로젝트 구조에 맞게 AGENTS.md 경로 수정

### TODO.md 커스터마이징

1. **Phase 정의**:
   ```markdown
   ## 🚀 Phase 1: [Phase명] (Week 1-2)
   
   **목표**: [Phase 목표]
   **예상 기간**: [기간]
   **진행률**: 0/X (0%)
   ```

2. **작업 정의**:
   ```markdown
   #### [ ] 1.1.1 [작업명]
   **설명**: [작업 설명]
   
   **참조 문서**:
   - `docs/XXXX.md`
   
   **생성할 파일**:
   - `path/to/file.ts`
   
   **완료 조건**:
   - [ ] 조건 1
   - [ ] 조건 2
   ```

## 🤝 베스트 프랙티스

### DO ✅

- ✅ 작업 시작 전 TODO.md와 참조 문서를 먼저 읽기
- ✅ 모든 규칙을 AGENTS.md에 문서화
- ✅ 작업 완료 시 TODO.md 체크박스 즉시 업데이트
- ✅ Phase 단위로 브랜치 생성 및 머지
- ✅ 커밋 메시지는 Conventional Commits 준수
- ✅ 문서와 코드를 항상 동기화

### DON'T ❌

- ❌ 문서 없이 바로 코딩 시작
- ❌ TODO.md 업데이트 없이 작업 진행
- ❌ AGENTS.md와 다른 규칙으로 코드 작성
- ❌ Phase 중간에 브랜치 머지
- ❌ 임의의 커밋 메시지 사용

## 📚 참고 자료

### Cursor AI 규칙 파일

템플릿에 포함된 규칙 파일들:

- **gitflow.mdc**: Gitflow 워크플로우 전략
- **commit-convention.mdc**: Conventional Commits 규칙
- **staging-guidelines.mdc**: Git 스테이징 가이드라인

### 추천 문서 구조

프로젝트 복잡도에 따라 선택적으로 사용:

**기본 (모든 프로젝트)**
- ✅ PLAN.md - 서비스 기획
- ✅ ARCHITECTURE.md - 기술 스택
- ✅ TERMINOLOGY.md - 용어 사전

**중급 (중규모 프로젝트)**
- ✅ MVP.md - MVP 범위 정의
- ✅ API_SPEC.md - API 명세
- ✅ DATABASE_SCHEMA.md - DB 스키마

**고급 (대규모/복잡한 프로젝트)**
- ✅ WORKFLOW.md - 상세 워크플로우
- ✅ USER_FLOW.md - 사용자 시나리오
- ✅ 기타 도메인별 명세서

## 🔧 트러블슈팅

### AI Agent가 문서를 참조하지 않는 경우

→ TODO.md에서 "참조 문서" 섹션을 명확히 명시했는지 확인

### 브랜치 자동 머지가 동작하지 않는 경우

→ TODO.md에서 Phase 진행률이 100%인지 확인

### 커밋 컨벤션이 지켜지지 않는 경우

→ .cursor/rules/commit-convention.mdc가 올바르게 로드되었는지 확인

## 📄 라이선스

MIT License - 자유롭게 사용, 수정, 배포 가능

## 🙏 기여

이슈와 PR은 언제나 환영합니다!

---

**Made with ❤️ for AI-powered development**
