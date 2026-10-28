# AimCoach 3D Vercel Edition

Vercel 정적 호스팅과 Functions, Upstash Redis를 사용하는 Gridshot 프로젝트입니다.

## 배경 에셋

`npm run build` 시 제공된 이미지 URL에서 이미지를 내려받아 다음 경로에 저장합니다.

```text
public/assets/training-range-bg.png
```

기본 서명 URL은 **2026년 9월 30일 13:24:11 UTC**에 만료됩니다. 그 전에 한 번 빌드한 뒤 생성된 PNG를 Git 저장소에 커밋하면 이후에는 URL이 없어도 기존 파일을 유지합니다.

다른 URL을 사용하려면 Vercel 환경변수에 등록합니다.

```text
BACKGROUND_SOURCE_URL
```

## 배포

```bash
npm install
npx vercel
```

프로덕션:

```bash
npx vercel --prod
```

## 랭킹 DB

Vercel Marketplace에서 Upstash Redis를 연결하고 다음 환경변수를 등록합니다.

```text
UPSTASH_REDIS_REST_URL
UPSTASH_REDIS_REST_TOKEN
```

환경변수를 설정한 뒤 재배포합니다.

## 로컬 개발

```bash
npm install
npx vercel dev
```

## 주요 경로

```text
src/index.html
public/assets/training-range-bg.png
api/leaderboard.mjs
api/scores.mjs
api/health.mjs
vercel.json
```

Redis가 연결되지 않아도 3D Gridshot과 로컬 AI 코치는 실행되며, 전역 랭킹만 오프라인으로 표시됩니다.


## Windows 권장 실행 파일

기존 BAT 대신 ASCII/CRLF 형식의 CMD 파일을 사용하세요.

```text
windows_build_only.cmd   - 패키지 설치 및 정적 빌드만 실행
windows_preview.cmd      - Vercel 로컬 미리보기
windows_deploy.cmd       - Vercel 프로덕션 배포
windows_diagnose.cmd     - 오류 진단 파일 생성
```

오류가 발생하면 `windows_diagnose.cmd`를 실행하면 프로젝트 폴더에
`deploy_diagnostic.txt`가 생성됩니다.


## npm-cli.js 또는 npm-prefix.js 누락 오류

다음 오류는 프로젝트나 배치 파일 문제가 아니라 Node.js 설치 폴더의 npm 파일이
누락된 상태입니다.

```text
Cannot find module ... node_modules/npm/bin/npm-cli.js
Cannot find module ... node_modules/npm/bin/npm-prefix.js
```

임시 우회 실행:

```text
windows_build_no_npm.cmd
windows_deploy_no_npm.cmd
```

두 파일은 npm을 사용하지 않고 Node.js 24에 포함된 Corepack을 통해 pnpm을 실행합니다.

근본 해결을 위해서는 Node.js를 제거한 뒤 남아 있는
`C:\Program Files\nodejs` 폴더를 삭제하고 Node.js 24 LTS를 다시 설치하세요.
"# aimlabcoach" 
"# aimlabcoach" 
