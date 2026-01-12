# Getting Started - AI Agent 초기 대화 가이드

> 이 문서는 **AI Agent가 템플릿을 처음 초기화할 때 사용자에게 물어봐야 할 질문들**을 정의합니다.

---

## 🤖 AI Agent를 위한 지침

템플릿 레포지토리를 클론하거나 생성한 직후, AI Agent는 다음 순서로 사용자와 대화하여 프로젝트를 초기화해야 합니다.

---

## 📋 초기 대화 플로우

### Phase 0: 프로젝트 기본 정보 수집

AI Agent는 다음 질문들을 **반드시** 물어보고 답변을 문서화해야 합니다:

#### 1. 프로젝트 기본 정보
```
✅ 필수 질문:

1. 프로젝트명은 무엇인가요?
   - 예: "TaskMaster", "E-Commerce Platform"
   - 용도: 모든 문서의 [프로젝트명] 플레이스홀더 대체

2. 이 프로젝트를 한 문장으로 설명한다면?
   - 예: "팀 협업을 위한 AI 기반 작업 관리 도구"
   - 용도: PLAN.md, README.md에 사용

3. 주요 사용자는 누구인가요?
   - 예: "스타트업 개발팀", "프리랜서 디자이너"
   - 용도: PLAN.md의 페르소나 정의
```

---

#### 2. 기술 스택 결정 ⭐ 중요

```
✅ 필수 질문:

1. 어떤 패키지 매니저를 사용하시나요?
   - 선택지: npm / yarn / pnpm / bun
   - 기본값: npm
   - 중요: 선택한 패키지 매니저를 AGENTS.md에 기록하고 
           프로젝트 전체에서 일관되게 사용

2. 프론트엔드 프레임워크는 무엇인가요?
   - 선택지: Next.js / React (Vite) / Vue / Svelte / 기타 / 없음
   - 버전: (해당 시) 예: Next.js 15, React 19

3. 백엔드는 어떻게 구성하시나요?
   - 선택지: 
     - Next.js API Routes/Server Actions
     - Express.js / Fastify / Koa
     - NestJS
     - 별도 백엔드 없음
     - 기타

4. 데이터베이스를 사용하시나요?
   - 선택지: PostgreSQL / MySQL / MongoDB / SQLite / Supabase / Firebase / 없음
   - ORM/ODM: Prisma / Drizzle / TypeORM / Mongoose / 없음

5. AI/ML 기능이 필요한가요?
   - 선택지: OpenAI / Google Gemini / Anthropic Claude / 기타 / 없음
```

---

#### 3. 프로젝트 초기화 방식 결정

```
✅ 필수 질문:

1. 기존 보일러플레이트를 사용하시나요?
   - 선택지:
     a. 네, [create-next-app / create-react-app / create-vue 등] 사용
     b. 아니요, 직접 설정할게요
     c. 이미 초기화된 프로젝트를 가져올게요

2. (a 선택 시) 어떤 초기화 명령어를 사용하시나요?
   - 예: "pnpm create next-app@latest"
   - 예: "npm create vite@latest"
   
   ⚠️ AI Agent 주의사항:
   - 현재 디렉토리에 템플릿 파일들이 있으면 충돌 발생
   - [PROJECT_INIT_GUIDE.md](./PROJECT_INIT_GUIDE.md) 참조하여
     임시 폴더 전략 사용 필수!
```

---

#### 4. 프로젝트 범위 및 우선순위

```
✅ 필수 질문:

1. MVP(최소 기능 제품)로 무엇을 만들고 싶으신가요?
   - 핵심 기능 3-5개 나열
   - 용도: MVP.md, TODO.md Phase 구성

2. 예상 개발 기간은 어느 정도인가요?
   - 예: "2주", "1개월", "3개월"
   - 용도: TODO.md 타임라인 설정

3. 가장 중요한 품질 요구사항은 무엇인가요?
   - 예: "보안", "성능", "사용자 경험", "빠른 출시"
   - 용도: 아키텍처 결정 및 우선순위 설정
```

---

#### 5. 개발 환경 및 협업

```
⚠️ 권장 질문 (선택):

1. 팀으로 개발하시나요, 혼자 개발하시나요?
   - 용도: Git 워크플로우 가이드 조정

2. 이미 사용 중인 개발 도구가 있나요?
   - 예: ESLint 설정, Prettier 설정, 특정 IDE
   - 용도: 개발 환경 설정

3. 배포 플랫폼은 정하셨나요?
   - 예: Vercel, Netlify, AWS, 기타, 미정
   - 용도: CI/CD 설정, 환경 변수 가이드
```

---

## 🔄 AI Agent 작업 순서

사용자로부터 답변을 받은 후 AI Agent는 다음 순서로 작업합니다:

### Step 1: 문서 업데이트
```
1. AGENTS.md 업데이트
   - [프로젝트명] 대체
   - Tech Stack 섹션 작성
   - 패키지 매니저 명시 ⭐
   - 용어 정의 추가

2. docs/PLAN.md 작성
   - 비즈니스 목표
   - 타겟 사용자
   - 핵심 기능

3. docs/ARCHITECTURE.md 작성
   - 기술 스택 상세
   - 디렉토리 구조 (프레임워크에 맞게)
   - 개발 명령어 (선택한 패키지 매니저 사용)

4. docs/TERMINOLOGY.md 작성
   - 프로젝트 도메인 용어 정의

5. docs/MVP.md 작성
   - MVP 범위 정의
   - 우선순위 설정

6. TODO.md 작성
   - Phase별 작업 분해
   - 타임라인 설정
```

### Step 2: 프로젝트 초기화 (필요 시)
```
보일러플레이트 사용 시:
1. [PROJECT_INIT_GUIDE.md](./PROJECT_INIT_GUIDE.md) 참조
2. 임시 폴더 생성 → 초기화 → 파일 이동 전략 사용
3. 템플릿 파일과 충돌하지 않도록 신중하게 병합
```

### Step 3: 환경 설정
```
1. .env.example 업데이트
   - 필요한 환경 변수 추가
   
2. package.json 업데이트
   - 프로젝트명 설정
   - 스크립트 추가
   - 의존성 추가

3. .gitignore 확인
   - 프레임워크별 추가 항목 확인
```

### Step 4: 첫 커밋
```
1. git add . (문서 업데이트)
2. git commit -m "docs: initialize project documentation"
3. 사용자에게 다음 단계 안내
```

---

## 📝 대화 템플릿 (AI Agent용)

### 초기 인사
```
안녕하세요! 👋

이 템플릿을 사용해주셔서 감사합니다. 
프로젝트를 초기화하기 위해 몇 가지 질문을 드리겠습니다.

답변을 바탕으로 문서를 자동으로 생성하고 프로젝트를 설정해드릴게요!
```

### 질문 진행
```
## 1️⃣ 프로젝트 기본 정보

**Q1. 프로젝트명은 무엇인가요?**
- 예: "TaskMaster", "MyBlog"

**Q2. 이 프로젝트를 한 문장으로 설명한다면?**
- 예: "개발자를 위한 할 일 관리 앱"

**Q3. 주요 사용자는 누구인가요?**
- 예: "소규모 개발팀", "개인 개발자"
```

```
## 2️⃣ 기술 스택 (중요!)

**Q1. 어떤 패키지 매니저를 사용하시나요?** ⭐
- npm / yarn / pnpm / bun
- (모르시면 'npm' 추천드립니다)

**Q2. 프론트엔드 프레임워크는 무엇인가요?**
- Next.js / React / Vue / Svelte / 없음

**Q3. 데이터베이스를 사용하시나요?**
- PostgreSQL / MySQL / Supabase / 없음

**Q4. AI 기능이 필요한가요?**
- OpenAI / Google Gemini / 없음
```

```
## 3️⃣ 프로젝트 초기화

**Q1. 기존 보일러플레이트를 사용하시나요?**
- a) 네, [create-next-app 등] 사용할게요
- b) 아니요, 직접 설정할게요
- c) 이미 초기화된 프로젝트 가져올게요

(a 선택 시)
**Q2. 초기화 명령어는 무엇인가요?**
- 예: "pnpm create next-app@latest"
```

### 답변 확인
```
## ✅ 입력하신 정보 확인

프로젝트명: [사용자 답변]
설명: [사용자 답변]
패키지 매니저: [사용자 답변] ⭐
프론트엔드: [사용자 답변]
...

이 정보가 맞나요? (네/수정할게요)
```

### 작업 시작
```
좋습니다! 지금부터 문서를 생성하고 프로젝트를 초기화하겠습니다.

작업 순서:
1. ✅ AGENTS.md 업데이트
2. ✅ docs/ 폴더 문서 작성
3. ✅ TODO.md Phase 구성
4. ⏳ 프로젝트 초기화 (선택 시)
5. ⏳ 첫 커밋

진행하겠습니다! 🚀
```

---

## ⚠️ 주의사항 (AI Agent용)

### 필수 확인 사항

1. **패키지 매니저 일관성** ⭐⭐⭐
   ```
   - 사용자가 선택한 패키지 매니저를 AGENTS.md에 명시
   - 모든 문서에서 해당 패키지 매니저 사용
   - 명령어 예시도 일관되게 작성
   
   예: pnpm 선택 시
   ✅ "pnpm install"
   ✅ "pnpm dev"
   ❌ "npm install"  (다른 패키지 매니저 사용 금지)
   ```

2. **프로젝트 초기화 충돌 방지**
   ```
   - create-next-app, create-react-app 등은 빈 폴더를 요구함
   - 템플릿 파일이 있으면 에러 발생
   - 반드시 [PROJECT_INIT_GUIDE.md](./PROJECT_INIT_GUIDE.md) 참조
   - 임시 폴더 전략 사용 필수
   ```

3. **문서 플레이스홀더 대체**
   ```
   다음 플레이스홀더를 반드시 대체:
   - [프로젝트명]
   - [이름] (작성자)
   - YYYY-MM-DD (날짜)
   - [예시] 내용들
   ```

---

## 📚 참고 문서

- [PROJECT_INIT_GUIDE.md](./PROJECT_INIT_GUIDE.md) - 프레임워크 초기화 가이드
- [AGENTS.md](./AGENTS.md) - 프로젝트 전역 규칙
- [docs/README.md](./docs/README.md) - 문서 작성 가이드

---

## 🎯 성공 기준

초기화가 완료되면 다음이 준비되어 있어야 합니다:

- [ ] AGENTS.md에 프로젝트 정보 및 패키지 매니저 명시
- [ ] docs/ 폴더의 모든 문서 작성 완료
- [ ] TODO.md에 Phase별 작업 정의
- [ ] 프로젝트 초기화 완료 (선택 시)
- [ ] .env.example 업데이트
- [ ] package.json 설정 완료
- [ ] 첫 커밋 생성

이제 사용자는 `TODO.md`를 보고 첫 작업을 시작할 수 있습니다! 🎉
