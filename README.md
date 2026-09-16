# 오늘 할 일 Cross — 미리보기 버전 2.0.1

Windows·macOS·Linux용 Avalonia 기반 버전입니다. 기존 Windows 전용 앱과 별도로 실행하고 저장합니다.

## 파일 선택 및 실행

- Windows 64비트: `TodoWidgetCross-Windows-x64.zip`을 전부 풀고 `TodoWidgetCross.exe`를 실행합니다. EXE만 따로 옮기지 마세요.
- Apple Silicon Mac(M1/M2/M3/M4 등): `TodoWidgetCross-macOS-arm64.tar.gz`를 풀고 `TodoWidget Cross.app`을 사용합니다.
- Intel Mac: `TodoWidgetCross-macOS-x64.tar.gz`를 사용합니다.
- Linux 64비트 Intel/AMD: `TodoWidgetCross-Linux-x64.tar.gz`를 풀고 `TodoWidgetCross`를 실행합니다. 터미널에서는 압축을 푼 폴더에서 `./TodoWidgetCross`를 실행합니다.

.NET 런타임은 각 배포본에 포함되어 있습니다. Linux는 X11 또는 XWayland, 시스템 글꼴/fontconfig 등 데스크톱 라이브러리가 필요합니다. 한글 글꼴이 없는 Linux에서는 한글 글꼴을 설치해야 합니다. GNOME 등 알림 영역이 없는 환경에서도 접근할 수 있도록 Linux에서는 작업 표시줄에도 창이 표시됩니다.

## 사용

- 입력란에 쓰고 Enter 또는 +: 할 일 추가
- 체크: 완료/미완료
- 연필: 수정, Enter 저장, Esc 취소
- 삭제 아이콘: 휴지통 이동
- 휴지통: 복원 또는 비우기. 비우기는 확인 창에서 확인을 눌러야 삭제됩니다.
- 제목줄 드래그: 이동. 창 테두리/모서리 드래그: 크기 조절. 위치와 크기는 종료할 때 저장합니다.
- ☰ → 화면·실행 설정: 불투명도, 모서리 둥글기, 항상 위, 로그인 자동 실행
- ×: 종료. 알림 영역 아이콘을 클릭하면 창을 앞으로 가져옵니다.

새 버전의 자동 실행은 처음에는 꺼져 있습니다. 새 버전으로 교체할 때는 기존 앱 설정에서 자동 실행을 끄고, 새 앱 설정에서 켜세요. 그렇지 않으면 로그인 때 두 앱이 함께 실행될 수 있습니다. 자동 실행을 켠 후 앱을 옮겼다면 새 위치에서 설정을 껐다 켜세요.

## 개발

소스는 `source` 폴더에 있습니다. .NET 8 SDK와 Avalonia 11.3.22를 사용합니다.

```
dotnet build source/TodoWidgetCross.csproj -c Release
dotnet run --project source/TodoWidgetCross.csproj -- --self-test ./test-output
dotnet publish source/TodoWidgetCross.csproj -c Release -r linux-x64 --self-contained true
```

`source/publish.ps1`은 OS별 빌드를 생성합니다. `source/package.ps1`은 이 작업 폴더의 빌드 결과를 Unix 실행 권한이 보존된 tar.gz로 포장한 실제 패키징 스크립트입니다. macOS .app 구조, 개발자 서명/공증 정보는 [Avalonia 공식 배포 문서](https://docs.avaloniaui.net/docs/deployment/macos)를 참고하세요. Linux 의존성은 [공식 Linux 배포 문서](https://docs.avaloniaui.net/docs/deployment/linux)에 안내되어 있습니다.
