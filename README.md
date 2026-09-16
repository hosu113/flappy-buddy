# Flappy Buddy — Cloudflare 배포

Node.js LTS와 프로젝트용 Wrangler가 설치되어 있습니다.
연결 계정: jshoo113@naver.com
배포 방식: Cloudflare Workers Static Assets (`flappy-buddy`).

새 PowerShell을 열고 실행하세요. npm.cmd는 PowerShell 실행 정책과 관계없이 사용할 수 있습니다.

```powershell
cd "$env:USERPROFILE\OneDrive\바탕 화면\flappy-buddy"
npm.cmd run whoami
npm.cmd run dev
```

개발 서버를 종료하려면 Ctrl+C를 누릅니다.

배포 없이 설정 검사:

```powershell
npm.cmd run check
```

실제 인터넷 공개 배포:

```powershell
npm.cmd run deploy
```

배포 성공 시 터미널에 접속 주소가 표시됩니다. 이후 index.html 수정 후 같은 명령으로 다시 배포합니다.
배포 완료 주소: https://flappy-buddy.flappy-buddy.workers.dev

로그인이 만료되면 `npm.cmd run login`으로 다시 인증하세요.
다른 컴퓨터에서는 Node.js LTS 설치 후 `npm.cmd ci`를 실행하세요.
Wrangler 직접 실행은 `npx.cmd wrangler --version`처럼 프로젝트 폴더에서 가능합니다.

## 파일 구성

- index.html: 게임 원본. 로컬에서 직접 열어도 실행됩니다.
- scripts/build.cjs: 원본을 dist/index.html로 복사합니다.
- wrangler.jsonc: 배포 대상 계정과 정적 파일 설정입니다.
- dist/: 배포 파일만 포함합니다. 빌드는 개발 서버/검사/배포 시 자동 실행됩니다.
- node_modules/, dist/, .wrangler/ 및 인증 관련 환경 파일은 Git에서 제외합니다.

현재 버전에는 수업용으로 파이프 5개 통과 시 종료되는 의도적 버그가 포함되어 있습니다.

공식 문서: https://developers.cloudflare.com/workers/static-assets/get-started/