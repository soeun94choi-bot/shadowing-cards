# Shadowing Cards

구글 문서로 내용을 관리하고, GitHub Pages에서 한국어→영어 플래시카드와 TTS를 재생하는 1파일 웹앱입니다.

## 배포하기

1. GitHub에 `shadowing-cards` 같은 새 저장소를 생성하세요. GitHub Pages로 무료 배포하려면 Public 저장소가 간단합니다.
2. `index.html`을 저장소 최상위(root)에 업로드하세요.
3. `Settings` → `Pages` → `Build and deployment` → `Deploy from a branch` → `main` / `/(root)` → `Save`.
4. 잠시 후 GitHub Pages URL로 접속하세요. 로컬에서 직접 열 경우 Google OAuth의 허용 출처 문제가 발생할 수 있으므로 배포 URL에서 로그인하세요.

## Google 연결

1. 웹앱의 `Google 연결` 버튼을 누르세요.
2. OPIc 플레이어에서 쓰던 Google OAuth 웹 클라이언트 ID를 입력하세요. Chrome 브라우저에서 두 앱이 같은 `https://사용자이름.github.io` 출처이면 이전 ID가 자동 입력될 수도 있습니다.
3. Knowledge 폴더 링크나 ID를 입력하세요. 처음에는 기존 Knowledge 폴더 ID가 입력되어 있습니다.
4. Google Cloud 콘솔의 OAuth 클라이언트 **Authorized JavaScript origins**에 `https://사용자이름.github.io`가 등록돼 있어야 합니다. Google Drive API를 활성화하고 사용자 계정을 OAuth 테스트 사용자에 추가해야 할 수도 있습니다.
5. Google 로그인 후 `문서 새로고침`을 누르면 해당 폴더의 문서를 실시간으로 다시 읽습니다.

## 문서 작성 규칙

영상 하나당 Google Docs 문서 하나를 만들어 같은 Knowledge 폴더에 넣습니다. 긴 설명은 문서 뒤쪽에 분리합니다.

```text
문장 카드
문장 01
한국어: 나도 그 기분 알아.
영어: I can relate to that.
자세한 설명 보기 · I can relate to that.

문장 02
한국어: 너도 동의하니?
영어: Do you agree?

자세한 설명
I can relate to that.
뜻: 나도 공감해.
설명: 상대방의 경험이나 기분을 이해한다는 뜻.
예문: I can relate to that.
```

`자세한 설명 보기 · 표현 이름`과 해설 섹션의 `표현 이름`을 정확히 일치시킵니다. Google Docs에서는 `문장 01`과 해설 제목을 `제목 2`로 지정하면 문서에서 찾기도 편합니다. 웹앱은 Drive의 텍스트 내보내기로 읽기 때문에 제목 스타일에 의존하지 않습니다.

## 개인정보/보안

- 공개 저장소에 개인 Google Docs 내용, OAuth 액세스 토큰, API 비밀 키, 개인 파일 전체를 넣지 마세요.
- OAuth **Client ID** 자체는 공개 클라이언트 식별자이지 비밀 키가 아닙니다. 하지만 API 비밀 키, Client Secret, Access Token은 절대 공개하지 마세요.
- 웹앱은 Google Drive 읽기 전용 OAuth 범위(`drive.readonly`)를 사용합니다. 문서 내용은 사용자의 브라우저가 로그인 후 직접 불러오고 GitHub 서버에 저장되지 않습니다.
- 브라우저 `speechSynthesis`는 화면 잠금·백그라운드에서 계속 재생되지 않을 수 있습니다. MP3 기반 백그라운드 재생은 별도 설계가 필요합니다.

## 한계

- 현재는 `문장 카드`, `문장 01`, `한국어:`, `영어:`, `자세한 설명` 형식에 맞는 Google Docs만 읽습니다.
- 로그인 액세스 토큰은 브라우저 메모리에만 저장하므로 만료되면 다시 로그인해야 합니다.
- TTS의 목소리 목록과 음질은 기기·브라우저에 따라 다릅니다.
