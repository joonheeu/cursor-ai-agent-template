# 프로젝트 초기화 가이드

> 이 문서는 **프레임워크/보일러플레이트를 사용하여 프로젝트를 초기화할 때 템플릿 파일과 충돌을 방지하는 방법**을 설명합니다.

---

## ⚠️ 문제 상황

대부분의 프레임워크 초기화 명령어는 **빈 디렉토리**를 요구합니다:

```bash
# 이런 명령어들은 현재 폴더에 파일이 있으면 에러 발생!
pnpm create next-app@latest .
npm create vite@latest .
npx create-react-app .
```

하지만 이 템플릿에는 이미 다음 파일들이 있습니다:
- `AGENTS.md`
- `TODO.md`
- `README.md`
- `docs/` 폴더
- `.cursor/` 폴더
- 기타 설정 파일들

→ **충돌 발생!** 😱

---

## ✅ 해결 방법: 임시 폴더 전략

### 전략 개요

```mermaid
graph LR
    A[현재 폴더<br/>템플릿 파일들] --> B[임시 폴더 생성<br/>temp_init/]
    B --> C[임시 폴더에서<br/>프레임워크 초기화]
    C --> D[생성된 파일들을<br/>현재 폴더로 이동]
    D --> E[임시 폴더 삭제]
    E --> F[템플릿 + 프레임워크<br/>병합 완료!]
```

### 상세 절차

---

## 📋 단계별 가이드

### Step 1: 임시 폴더 생성

```bash
# 현재 프로젝트 루트에서 실행
mkdir temp_init
```

---

### Step 2: 임시 폴더에서 프레임워크 초기화

**패턴**: `cd temp_init && [패키지매니저] [초기화명령어] .`

#### Next.js
```bash
cd temp_init && pnpm create next-app@latest . --typescript --tailwind --eslint --app --no-src-dir --import-alias "@/*"
```

#### React (Vite)
```bash
cd temp_init && pnpm create vite@latest . --template react-ts
```

#### Vue
```bash
cd temp_init && pnpm create vue@latest .
```

#### Svelte
```bash
cd temp_init && pnpm create svelte@latest .
```

**⚠️ 주의**: 
- 마지막에 `.` (현재 디렉토리)를 반드시 지정
- 프롬프트가 나오면 적절히 선택 (TypeScript, ESLint 등)

---

### Step 3: 현재 폴더로 파일 이동

```bash
# temp_init으로 돌아가기
cd ..

# 모든 파일 이동 (dot files 포함!)
# -f: 강제 덮어쓰기 (중복 파일 처리)
mv temp_init/* . 2>/dev/null
mv temp_init/.* . 2>/dev/null

# 또는 rsync 사용 (더 안전)
rsync -av temp_init/ . --exclude '.git'
```

**이동될 파일들 예시** (Next.js 기준):
- `app/` - Next.js App Router
- `public/` - 정적 파일
- `next.config.js` - Next.js 설정
- `.eslintrc.json` - ESLint 설정
- `tsconfig.json` - TypeScript 설정
- `package.json` - 의존성 (⚠️ 주의 필요)
- `.gitignore` - Git 제외 파일 (⚠️ 주의 필요)

---

### Step 4: 충돌 파일 처리

일부 파일은 템플릿과 프레임워크 모두 생성하므로 **수동 병합** 필요:

#### 4-1. `package.json` 병합

```bash
# 1. 기존 템플릿 package.json 백업
cp package.json package.json.template

# 2. 프레임워크 package.json이 덮어썼으므로 수동 병합
# - name: 프로젝트명으로 변경
# - scripts: 프레임워크 스크립트 유지
# - dependencies: 프레임워크 의존성 유지
```

**병합 예시**:
```json
{
  "name": "your-project-name",  // ← 프로젝트명으로 변경
  "version": "0.1.0",
  "scripts": {
    "dev": "next dev",           // ← 프레임워크 스크립트
    "build": "next build",
    "start": "next start",
    "lint": "next lint"
  },
  "dependencies": {
    // ← 프레임워크 의존성 유지
  }
}
```

#### 4-2. `.gitignore` 병합

```bash
# 1. 백업
cp .gitignore .gitignore.template

# 2. 템플릿 .gitignore 내용을 프레임워크 .gitignore에 추가
cat .gitignore.template >> .gitignore

# 3. 중복 제거 (선택)
sort -u .gitignore -o .gitignore
```

#### 4-3. `README.md` 처리

```bash
# 프레임워크 README는 삭제하고 템플릿 README 유지
# (이미 덮어써졌다면 복구 필요 없음)
```

---

### Step 5: 임시 폴더 삭제

```bash
# temp_init 폴더 및 내용물 완전 삭제
rm -rf temp_init
```

---

### Step 6: 의존성 설치

```bash
# 선택한 패키지 매니저로 의존성 설치
pnpm install  # pnpm 사용 시
# npm install  # npm 사용 시
# yarn install # yarn 사용 시
```

---

### Step 7: 검증

```bash
# 개발 서버 실행하여 정상 작동 확인
pnpm dev  # (또는 npm dev, yarn dev)
```

브라우저에서 `http://localhost:3000` 접속하여 확인

---

## 🤖 AI Agent용 자동화 스크립트

AI Agent는 다음 순서로 명령어를 실행하세요:

### 템플릿 (복사해서 사용)

```bash
# 변수 설정
PACKAGE_MANAGER="pnpm"  # 사용자가 선택한 패키지 매니저
FRAMEWORK_INIT_CMD="create next-app@latest"  # 초기화 명령어
FRAMEWORK_ARGS="--typescript --tailwind --eslint --app --no-src-dir --import-alias @/*"  # 추가 인자

# Step 1: 임시 폴더 생성
mkdir -p temp_init

# Step 2: 임시 폴더에서 초기화
cd temp_init && ${PACKAGE_MANAGER} ${FRAMEWORK_INIT_CMD} . ${FRAMEWORK_ARGS}

# Step 3: 파일 이동
cd ..
rsync -av temp_init/ . --exclude '.git' --exclude 'temp_init'

# Step 4: package.json 이름 변경 (프로젝트명으로)
# (수동 또는 jq 사용)

# Step 5: 임시 폴더 삭제
rm -rf temp_init

# Step 6: 의존성 설치
${PACKAGE_MANAGER} install

# Step 7: 검증
echo "✅ 프로젝트 초기화 완료!"
echo "개발 서버 실행: ${PACKAGE_MANAGER} dev"
```

---

## 📝 프레임워크별 초기화 명령어 치트시트

### Next.js
```bash
# pnpm
cd temp_init && pnpm create next-app@latest . --typescript --tailwind --eslint --app --no-src-dir --import-alias "@/*"

# npm
cd temp_init && npx create-next-app@latest . --typescript --tailwind --eslint --app --no-src-dir --import-alias "@/*"

# yarn
cd temp_init && yarn create next-app . --typescript --tailwind --eslint --app --no-src-dir --import-alias "@/*"
```

### React (Vite)
```bash
# pnpm
cd temp_init && pnpm create vite@latest . --template react-ts

# npm
cd temp_init && npm create vite@latest . -- --template react-ts

# yarn
cd temp_init && yarn create vite . --template react-ts
```

### Vue
```bash
# pnpm
cd temp_init && pnpm create vue@latest .

# npm
cd temp_init && npm create vue@latest .

# yarn
cd temp_init && yarn create vue .
```

### Svelte (SvelteKit)
```bash
# pnpm
cd temp_init && pnpm create svelte@latest .

# npm
cd temp_init && npm create svelte@latest .
```

### Remix
```bash
# pnpm
cd temp_init && pnpx create-remix@latest .

# npm
cd temp_init && npx create-remix@latest .
```

---

## ⚠️ 주의사항

### 1. Git 저장소 충돌
```bash
# 프레임워크 초기화가 .git을 생성할 수 있음
# 이 경우 임시 폴더의 .git은 제외하고 이동

rsync -av temp_init/ . --exclude '.git'
```

### 2. 중복 파일 우선순위
```
템플릿 유지: README.md, AGENTS.md, TODO.md, docs/, .cursor/
프레임워크 유지: package.json, tsconfig.json, next.config.js 등 설정 파일
병합 필요: .gitignore, .env.example
```

### 3. 패키지 매니저 일관성
```bash
# 초기화 후 lock 파일 확인
# pnpm 사용 시: pnpm-lock.yaml
# npm 사용 시: package-lock.json
# yarn 사용 시: yarn.lock

# 다른 lock 파일이 있으면 삭제
rm package-lock.json  # npm lock 삭제 (pnpm 사용 시)
rm yarn.lock          # yarn lock 삭제 (pnpm 사용 시)
```

---

## 🎯 완료 체크리스트

초기화가 완료되면 다음을 확인하세요:

- [ ] temp_init 폴더가 삭제되었는가?
- [ ] package.json의 name이 프로젝트명으로 변경되었는가?
- [ ] 올바른 패키지 매니저 lock 파일만 존재하는가?
- [ ] .gitignore가 템플릿+프레임워크 내용을 모두 포함하는가?
- [ ] 템플릿 파일들(AGENTS.md, TODO.md, docs/)이 유지되었는가?
- [ ] 개발 서버가 정상 실행되는가? (`pnpm dev`)
- [ ] 의존성이 모두 설치되었는가?

---

## 🆘 트러블슈팅

### 문제: "이미 파일이 존재합니다" 에러
```bash
# 해결: temp_init 폴더를 삭제하고 다시 시도
rm -rf temp_init
```

### 문제: 파일이 제대로 이동되지 않음
```bash
# 해결: rsync 대신 직접 이동
mv temp_init/* . 2>/dev/null
mv temp_init/.* . 2>/dev/null
```

### 문제: package.json 이 덮어써짐
```bash
# 해결: 프레임워크 package.json을 기반으로 name만 변경
# jq 사용 (설치 필요)
jq '.name = "your-project-name"' package.json > package.json.tmp
mv package.json.tmp package.json
```

---

## 📚 참고 자료

- [GETTING_STARTED.md](./GETTING_STARTED.md) - 초기 대화 가이드
- [AGENTS.md](./AGENTS.md) - 프로젝트 전역 규칙
- Next.js 공식 문서: https://nextjs.org/docs
- Vite 공식 문서: https://vitejs.dev/guide/
