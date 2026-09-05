# 배당금 캘린더 - 안드로이드 APK 만들기

이 폴더에는 업로드하신 HTML 프로그램(`www/index.html`)을 감싼 **Capacitor 안드로이드 프로젝트**가 들어 있습니다.
이 작업환경은 보안상 안드로이드 SDK/Gradle을 직접 다운로드할 수 없어서, 여기서 바로 APK를 만들어 드릴 수는 없습니다.
대신 **GitHub Actions**가 자동으로 빌드해주도록 설정해 두었습니다. 순서대로만 따라 하시면 됩니다. (안드로이드 스튜디오 설치 불필요, 무료)

## 1단계 — GitHub에 올리기

1. https://github.com 에서 무료 계정 생성 (이미 있으면 생략)
2. 우측 상단 `+` → `New repository` → 이름 아무거나 (예: `dividend-app`) → `Create repository`
3. 로컬 컴퓨터에서 아래 명령어 실행 (또는 GitHub 웹사이트의 "Upload files" 기능으로 이 폴더 전체를 그대로 업로드해도 됩니다)

```bash
cd dividend-app
git init
git add .
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/내계정/dividend-app.git
git push -u origin main
```

## 2단계 — 자동 빌드 확인

1. GitHub 저장소 페이지에서 상단 **Actions** 탭 클릭
2. "Build Android APK" 워크플로우가 자동으로 실행됩니다 (약 3~5분 소요)
3. 초록색 체크 표시가 뜨면 완료된 것입니다. 클릭해서 들어간 뒤, 페이지 하단 **Artifacts** 항목에서
   `dividend-calendar-debug-apk` 를 클릭하면 zip 파일이 다운로드됩니다. 압축을 풀면 `app-debug.apk` 파일이 있습니다.

## 3단계 — 휴대폰에 설치

1. `app-debug.apk` 파일을 휴대폰으로 전송 (카카오톡 '나에게 보내기', 이메일, USB 등 아무 방법)
2. 휴대폰에서 파일을 눌러 설치 시도 → "출처를 알 수 없는 앱" 경고가 뜨면 **설정 → 허용** 후 다시 설치
3. 설치 완료 후 "배당금캘린더" 앱 아이콘이 생깁니다

## 참고사항

- 이 앱은 데이터를 휴대폰 내부(WebView의 localStorage)에 저장합니다. 기존 HTML을 브라우저에서 쓰던 데이터와는 별도로 저장되니,
  필요하면 기존 화면의 "내보내기(백업)" 기능으로 JSON을 뽑아서, 앱 설치 후 "가져오기(복구)" 기능으로 옮기시면 됩니다.
- 지금은 **디버그(debug) APK**입니다. 개인적으로 설치해 쓰는 용도로는 충분하지만,
  Google Play 스토어에 정식 배포하려면 서명(release) 빌드와 개발자 계정이 별도로 필요합니다. 필요하시면 말씀해 주세요.
- 앱 아이콘은 Capacitor 기본 아이콘입니다. 원하는 아이콘 이미지가 있으면 알려주시면 적용해서 다시 준비해 드리겠습니다.
