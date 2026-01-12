# 기존 프로젝트에 템플릿 적용하기

> 이 문서는 **이미 개발 중인 프로젝트에 이 템플릿의 구조를 적용하는 방법**을 설명합니다.

---

## 🎯 적용 시나리오

다음과 같은 경우에 이 가이드를 사용하세요:

- ✅ 이미 개발 중인 프로젝트가 있음
- ✅ AI Agent 주도 개발 구조를 도입하고 싶음
- ✅ 문서 중심 개발로 전환하고 싶음
- ✅ 기존 코드는 유지하면서 구조만 추가하고 싶음

---

## 🚀 빠른 시작 (사용자용)

### AI Agent에게 이렇게 요청하세요:

```
이 템플릿을 적용해줘:
https://github.com/joonheeu/cursor-ai-agent-template

내 프로젝트에 맞게 AGENTS.md, TODO.md, docs/ 구조를 추가해줘.
```

AI Agent가 자동으로:
1. ✅ 기존 프로젝트 구조 분석
2. ✅ 기술 스택 및 패키지 매니저 파악
3. ✅ 템플릿 파일 선택적으로 추가
4. ✅ 기존 파일과 충돌 방지
5. ✅ 프로젝트에 맞는 문서 생성

---

## 🤖 AI Agent를 위한 상세 가이드

### Phase 0: 템플릿 파일 준비

#### Step 1: 템플릿 파일 다운로드

```bash
# 임시 디렉토리에 템플릿 클론
cd /tmp
git clone https://github.com/joonheeu/cursor-ai-agent-template.git ai-template
cd ai-template
```

**필요한 파일 목록**:
- `AGENTS.md`
- `TODO.md`
- `docs/README.md`
- `docs/PLAN.md`
- `docs/ARCHITECTURE.md`
- `docs/TERMINOLOGY.md`
- `docs/MVP.md` (선택)
- `.cursor/rules/*` (전체)
- `GETTING_STARTED.md` (참고용)
- `PROJECT_INIT_GUIDE.md` (참고용)

---

### Phase 1: 기존 프로젝트 분석

AI Agent는 다음 정보를 자동으로 수집해야 합니다:

#### 1-1. 프로젝트 구조 파악

```bash
# 프로젝트 루트에서 실행
ls -la
tree -L 2 -I 'node_modules'
```

**확인 사항**:
- [ ] 프로젝트 루트 경로
- [ ] 주요 디렉토리 구조 (src/, app/, components/ 등)
- [ ] 설정 파일 존재 여부

---

#### 1-2. 기술 스택 파악

**package.json 분석**:
```bash
cat package.json
```

**확인 정보**:
- [ ] 프로젝트명 (`name`)
- [ ] 패키지 매니저 (lock 파일 확인)
  - `package-lock.json` → npm
  - `pnpm-lock.yaml` → pnpm
  - `yarn.lock` → yarn
  - `bun.lockb` → bun
- [ ] 주요 의존성
  - Framework: next, react, vue, svelte 등
  - Database: prisma, drizzle, typeorm 등
  - UI: tailwind, styled-components 등
- [ ] 스크립트 (`scripts`)

**기타 설정 파일 확인**:
```bash
# TypeScript
cat tsconfig.json

# Database ORM
cat prisma/schema.prisma  # Prisma
cat drizzle.config.ts      # Drizzle

# Framework 설정
cat next.config.js         # Next.js
cat vite.config.ts         # Vite

# Linter/Formatter
cat .eslintrc.json
cat .prettierrc
```

---

#### 1-3. 기존 문서 확인

```bash
# 기존 README, 문서 확인
ls *.md
ls docs/ 2>/dev/null
ls .cursor/ 2>/dev/null
```

**충돌 파일 목록 작성**:
- [ ] `README.md` 존재 여부
- [ ] `docs/` 폴더 존재 여부
- [ ] `.cursor/` 폴더 존재 여부
- [ ] `AGENTS.md`, `TODO.md` 존재 여부

---

#### 1-4. Git 상태 확인

```bash
git status
git branch --show-current
git log --oneline -5
```

**확인 사항**:
- [ ] Git 저장소인가?
- [ ] 현재 브랜치
- [ ] Uncommitted changes 여부
- [ ] 최근 커밋 히스토리

---

### Phase 2: 사용자와 대화

AI Agent는 분석 결과를 바탕으로 사용자에게 확인 질문:

```
## 🔍 기존 프로젝트 분석 결과

**프로젝트명**: [package.json의 name]
**패키지 매니저**: [자동 감지된 패키지 매니저]
**프레임워크**: [Next.js 15, React 19 등]
**데이터베이스**: [Prisma + PostgreSQL 등]

**충돌 파일**:
- README.md: 기존 파일 존재 (백업 후 병합 필요)
- docs/ 폴더: 없음 (신규 생성 가능)

---

## ✅ 적용할 템플릿 파일

다음 파일들을 추가하겠습니다:

**필수**:
- [ ] AGENTS.md (프로젝트 제어 타워)
- [ ] TODO.md (작업 추적)
- [ ] docs/ 폴더 (문서 구조)
  - [ ] docs/README.md
  - [ ] docs/ARCHITECTURE.md
  - [ ] docs/TERMINOLOGY.md
- [ ] .cursor/rules/ (Git 워크플로우 규칙)

**선택**:
- [ ] docs/PLAN.md (서비스 기획)
- [ ] docs/MVP.md (MVP 범위)
- [ ] docs/DATABASE_SCHEMA.md (DB 설계)
- [ ] docs/API_SPEC.md (API 명세)

---

## ❓ 확인 질문

1. **README.md 처리**:
   - a) 기존 README를 README.old.md로 백업하고 템플릿 README 사용
   - b) 기존 README 유지하고 템플릿 섹션만 추가
   - c) 기존 README 그대로 유지

2. **적용 범위**:
   - a) 필수 파일만 추가 (AGENTS.md, TODO.md, docs/ 최소)
   - b) 전체 템플릿 적용 (모든 문서 포함)

3. **TODO.md 생성 방식**:
   - a) 기존 코드 분석하여 자동 생성
   - b) 빈 템플릿만 제공 (수동 작성)
   - c) 사용자와 대화하며 작성

이 설정이 맞나요? (네/수정할게요)
```

---

### Phase 3: 템플릿 파일 적용

사용자 확인 후 실제 적용 단계:

#### 3-1. 백업 생성

```bash
# 충돌 파일 백업
if [ -f README.md ]; then
  cp README.md README.old.md
  echo "✅ README.md → README.old.md 백업 완료"
fi

if [ -d docs ]; then
  cp -r docs docs.backup
  echo "✅ docs/ → docs.backup/ 백업 완료"
fi

if [ -d .cursor ]; then
  cp -r .cursor .cursor.backup
  echo "✅ .cursor/ → .cursor.backup/ 백업 완료"
fi
```

---

#### 3-2. 템플릿 파일 복사

```bash
# 프로젝트 루트에서 실행
TEMPLATE_PATH="/tmp/ai-template"

# AGENTS.md 복사 및 커스터마이징
cp $TEMPLATE_PATH/AGENTS.md ./AGENTS.md

# docs/ 폴더 생성 및 파일 복사
mkdir -p docs
cp $TEMPLATE_PATH/docs/README.md ./docs/
cp $TEMPLATE_PATH/docs/ARCHITECTURE.md ./docs/
cp $TEMPLATE_PATH/docs/TERMINOLOGY.md ./docs/
cp $TEMPLATE_PATH/docs/PLAN.md ./docs/        # 선택
cp $TEMPLATE_PATH/docs/MVP.md ./docs/          # 선택

# TODO.md 복사
cp $TEMPLATE_PATH/TODO.md ./TODO.md

# .cursor/rules/ 복사
mkdir -p .cursor/rules
cp -r $TEMPLATE_PATH/.cursor/rules/* ./.cursor/rules/

# 참고 문서 복사 (선택)
cp $TEMPLATE_PATH/GETTING_STARTED.md ./GETTING_STARTED.md
cp $TEMPLATE_PATH/PROJECT_INIT_GUIDE.md ./PROJECT_INIT_GUIDE.md
```

---

#### 3-3. 파일 커스터마이징

**자동으로 대체해야 할 플레이스홀더**:

```bash
# 프로젝트명 (package.json에서 추출)
PROJECT_NAME=$(node -p "require('./package.json').name")

# 패키지 매니저 감지
if [ -f "pnpm-lock.yaml" ]; then
  PACKAGE_MANAGER="pnpm"
elif [ -f "yarn.lock" ]; then
  PACKAGE_MANAGER="yarn"
elif [ -f "bun.lockb" ]; then
  PACKAGE_MANAGER="bun"
else
  PACKAGE_MANAGER="npm"
fi

# AGENTS.md 커스터마이징
sed -i '' "s/\[프로젝트명\]/$PROJECT_NAME/g" AGENTS.md
sed -i '' "s/\[npm\/pnpm\/yarn\/bun 중 하나 명시\]/$PACKAGE_MANAGER/g" AGENTS.md
sed -i '' "s/\[패키지매니저\]/$PACKAGE_MANAGER/g" AGENTS.md

# docs 파일들 커스터마이징
for file in docs/*.md; do
  sed -i '' "s/\[프로젝트명\]/$PROJECT_NAME/g" "$file"
  sed -i '' "s/YYYY-MM-DD/$(date +%Y-%m-%d)/g" "$file"
done

# TODO.md 커스터마이징
sed -i '' "s/\[프로젝트명\]/$PROJECT_NAME/g" TODO.md
sed -i '' "s/YYYY-MM-DD/$(date +%Y-%m-%d)/g" TODO.md
```

---

#### 3-4. AGENTS.md 자동 작성

기존 프로젝트 분석 결과를 바탕으로 AGENTS.md 작성:

```typescript
// AI Agent가 수행할 로직 (의사 코드)

// 1. Business Goal 작성
const projectDescription = `${projectName}는 [기존 README나 package.json description에서 추출]`;

// 2. Tech Stack 작성
const techStack = {
  packageManager: detectedPackageManager, // pnpm, npm 등
  framework: detectedFramework, // Next.js, React 등
  database: detectedDatabase, // PostgreSQL, MySQL 등
  orm: detectedORM, // Prisma, Drizzle 등
  styling: detectedStyling, // Tailwind, styled-components 등
};

// 3. Operational Commands 작성
const commands = {
  dev: packageJson.scripts.dev || `${packageManager} run dev`,
  build: packageJson.scripts.build || `${packageManager} run build`,
  test: packageJson.scripts.test || `${packageManager} test`,
  // ... 기타 스크립트
};

// 4. 용어 추출 (코드베이스에서)
const terminology = extractFromCodebase([
  'src/types/*.ts',
  'prisma/schema.prisma',
  'app/**/page.tsx',
]);
```

---

#### 3-5. docs/ARCHITECTURE.md 자동 작성

```typescript
// 프로젝트 구조 분석
const directoryStructure = analyzeDirectory('.', {
  ignore: ['node_modules', 'dist', 'build', '.next'],
  depth: 3
});

// 의존성 분석
const dependencies = {
  production: packageJson.dependencies,
  development: packageJson.devDependencies
};

// ARCHITECTURE.md 생성
generateArchitectureDoc({
  techStack,
  directoryStructure,
  dependencies,
  configFiles: findConfigFiles()
});
```

---

#### 3-6. TODO.md 생성 (3가지 옵션)

**옵션 A: 빈 템플릿** (빠르지만 수동 작성 필요)
```markdown
# ${projectName} 개발 TODO

> **마지막 업데이트**: ${today}
> **전체 진행률**: 0% (0/X)

## 📌 빠른 참조

### 🎯 현재 작업
- [ ] **다음**: [작업을 정의해주세요]

...
```

**옵션 B: 코드베이스 분석 후 제안** (추천)
```typescript
// 기존 코드 분석
const features = analyzeCodebase({
  routes: findRoutes('app/', 'pages/'),
  components: findComponents('components/', 'src/'),
  apis: findAPIs('app/api/', 'pages/api/'),
  database: analyzePrismaSchema('prisma/schema.prisma')
});

// TODO Phase 생성
const phases = [
  {
    name: "기존 코드 리팩터링",
    tasks: generateRefactoringTasks(features)
  },
  {
    name: "문서화",
    tasks: generateDocumentationTasks(features)
  },
  {
    name: "테스트 추가",
    tasks: generateTestingTasks(features)
  },
  // ... 사용자 정의 Phase
];
```

**옵션 C: 사용자와 대화하며 작성**
```
AI Agent: "현재 개발 중인 주요 기능은 무엇인가요?"
User: "사용자 인증, 대시보드, 프로필 관리"

AI Agent: "다음에 추가하고 싶은 기능은 무엇인가요?"
User: "알림 시스템, 팀 협업 기능"

→ 이를 바탕으로 Phase 구성
```

---

#### 3-7. docs/TERMINOLOGY.md 생성

```typescript
// 코드베이스에서 용어 추출
const terminology = {
  types: extractTypesFromTS('src/types/**/*.ts'),
  models: extractModelsFromPrisma('prisma/schema.prisma'),
  apiEndpoints: extractAPIs('app/api/**/*.ts'),
  components: extractComponents('components/**/*.tsx')
};

// TERMINOLOGY.md 생성
generateTerminologyDoc(terminology);
```

**예시 출력**:
```markdown
### User
**정의**: 시스템 사용자를 나타내는 엔티티

**코드 표현**:
- **TypeScript 타입**: `User`
- **데이터베이스**: `User` 테이블
- **API**: `/api/users`

**속성**:
- `id`: 고유 식별자
- `email`: 이메일 주소
- `name`: 사용자명
```

---

#### 3-8. .gitignore 병합

```bash
# 템플릿 .gitignore 내용을 기존 .gitignore에 추가
if [ -f .gitignore ]; then
  echo "" >> .gitignore
  echo "# Added by AI Agent Template" >> .gitignore
  cat $TEMPLATE_PATH/.gitignore >> .gitignore
  
  # 중복 제거
  sort -u .gitignore -o .gitignore
  
  echo "✅ .gitignore 병합 완료"
else
  # .gitignore가 없으면 새로 생성
  cp $TEMPLATE_PATH/.gitignore ./.gitignore
  echo "✅ .gitignore 생성 완료"
fi
```

---

### Phase 4: 검증 및 커밋

#### 4-1. 파일 검증

```bash
# 필수 파일 존재 확인
required_files=(
  "AGENTS.md"
  "TODO.md"
  "docs/README.md"
  "docs/ARCHITECTURE.md"
  "docs/TERMINOLOGY.md"
  ".cursor/rules/gitflow.mdc"
  ".cursor/rules/commit-convention.mdc"
  ".cursor/rules/staging-guidelines.mdc"
)

for file in "${required_files[@]}"; do
  if [ -f "$file" ]; then
    echo "✅ $file"
  else
    echo "❌ $file 누락!"
  fi
done
```

---

#### 4-2. 플레이스홀더 검사

```bash
# [프로젝트명], [이름], YYYY-MM-DD 등이 남아있는지 확인
grep -r "\[프로젝트명\]" AGENTS.md docs/ TODO.md 2>/dev/null
grep -r "YYYY-MM-DD" AGENTS.md docs/ TODO.md 2>/dev/null

# 발견되면 경고
if [ $? -eq 0 ]; then
  echo "⚠️ 일부 플레이스홀더가 대체되지 않았습니다."
fi
```

---

#### 4-3. Git 커밋

```bash
# 변경 사항 스테이징
git add AGENTS.md TODO.md docs/ .cursor/

# 커밋 메시지 생성
git commit -m "$(cat <<'EOF'
docs: apply AI Agent development template

- Add AGENTS.md for project control tower
- Add TODO.md for task tracking
- Add docs/ folder with documentation structure
- Add .cursor/rules/ for Git workflow guidelines

Template source: https://github.com/joonheeu/cursor-ai-agent-template

This applies AI Agent-driven development structure to the existing project
while preserving all existing code and functionality.
EOF
)"

echo "✅ 템플릿 적용 완료!"
```

---

### Phase 5: 사용자에게 결과 보고

```
## ✅ 템플릿 적용 완료!

### 추가된 파일
- ✅ AGENTS.md (프로젝트 제어 타워)
- ✅ TODO.md (작업 추적 허브)
- ✅ docs/README.md (문서 목차)
- ✅ docs/ARCHITECTURE.md (기술 스택)
- ✅ docs/TERMINOLOGY.md (용어 사전)
- ✅ docs/PLAN.md (서비스 기획) - 선택
- ✅ docs/MVP.md (MVP 범위) - 선택
- ✅ .cursor/rules/ (Git 워크플로우 규칙)

### 백업된 파일
- ✅ README.old.md (기존 README)
- ✅ docs.backup/ (기존 docs 폴더) - 있었다면

### 커밋 정보
- Commit: abc123d
- Message: "docs: apply AI Agent development template"

---

## 🎯 다음 단계

1. **문서 검토 및 수정**
   ```
   "AGENTS.md를 열어서 검토해줘"
   "docs/PLAN.md에 비즈니스 목표를 추가해줘"
   ```

2. **TODO.md 작성**
   ```
   "TODO.md에 현재 진행 중인 작업들을 추가해줘"
   "다음 2주간 개발 계획을 Phase로 구성해줘"
   ```

3. **AI Agent 주도 개발 시작**
   ```
   "TODO.md의 Phase 1.1.1 작업을 시작해줘"
   ```

---

## 📚 참고 문서

- [AGENTS.md](./AGENTS.md) - 프로젝트 제어 타워
- [TODO.md](./TODO.md) - 작업 추적
- [docs/README.md](./docs/README.md) - 문서 목차
- [GETTING_STARTED.md](./GETTING_STARTED.md) - 초기 설정 가이드

템플릿 적용이 완료되었습니다! 🎉
```

---

## 🔍 트러블슈팅

### 문제 1: 파일 충돌

```bash
# 문제: README.md, docs/ 등이 이미 존재
# 해결: 백업 후 병합
mv README.md README.old.md
# 필요한 섹션만 수동 병합
```

### 문제 2: 프로젝트 구조 파악 실패

```bash
# 문제: package.json이 없거나 구조가 특이함
# 해결: 사용자에게 직접 질문
"프로젝트 구조를 파악할 수 없습니다. 다음 정보를 알려주세요:
- 사용하는 프레임워크
- 패키지 매니저
- 주요 디렉토리 구조"
```

### 문제 3: Git 저장소가 아님

```bash
# 문제: .git 폴더가 없음
# 해결: Git 초기화 제안
"Git 저장소가 아닙니다. 초기화하시겠습니까? (git init)"
```

---

## ⚠️ 주의사항

### 1. 기존 코드는 절대 수정하지 않음
```
템플릿 적용은 문서와 규칙만 추가합니다.
기존 src/, app/, components/ 등의 코드는 건드리지 않습니다.
```

### 2. 백업 필수
```
충돌 가능성이 있는 파일은 항상 백업합니다.
- README.md → README.old.md
- docs/ → docs.backup/
```

### 3. 점진적 적용
```
한 번에 모든 문서를 완벽하게 작성하려 하지 마세요.
필수 파일(AGENTS.md, TODO.md)만 먼저 추가하고,
나머지는 필요에 따라 점진적으로 작성합니다.
```

---

## 📊 적용 체크리스트

템플릿 적용이 완료되면 다음을 확인하세요:

- [ ] AGENTS.md 생성 및 커스터마이징 완료
- [ ] TODO.md 생성 (빈 템플릿 또는 자동 생성)
- [ ] docs/ 폴더 및 주요 문서 생성
- [ ] .cursor/rules/ 추가
- [ ] 플레이스홀더 모두 대체
- [ ] 기존 파일 백업 완료 (충돌 시)
- [ ] Git 커밋 완료
- [ ] 사용자에게 결과 보고

---

## 🎯 성공 기준

다음이 준비되면 성공입니다:

1. **문서 구조 완성**
   - AGENTS.md에 프로젝트 정보 및 규칙 명시
   - docs/ 폴더에 핵심 문서 준비
   - TODO.md에 작업 추적 시작

2. **AI Agent 주도 개발 가능**
   - "TODO.md의 작업을 시작해줘" 명령어 동작
   - AGENTS.md 참조하여 규칙 준수
   - 문서 기반 의사결정 가능

3. **기존 개발 흐름 유지**
   - 기존 코드 100% 유지
   - 기존 Git 히스토리 유지
   - 개발 환경 그대로 유지

이제 기존 프로젝트에서도 AI Agent 주도 개발이 가능합니다! 🚀
