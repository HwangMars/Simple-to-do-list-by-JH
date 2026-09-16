# 오늘 할 일 Cross — 미리보기 버전 2.3.0

Windows·macOS·Linux용 Avalonia 기반 버전입니다.

## 파일 선택 및 실행

- Windows 64비트: `TodoWidgetCross-Windows-x64.zip`을 전부 풀고 `TodoWidgetCross.exe`를 실행합니다. EXE만 따로 옮기지 마세요.
- Apple Silicon Mac(M1/M2/M3/M4 등): `TodoWidgetCross-macOS-arm64.tar.gz`를 풀고 `TodoWidget Cross.app`을 사용합니다.
- Intel Mac: `TodoWidgetCross-macOS-x64.tar.gz`를 사용합니다.
- Linux 64비트 Intel/AMD: `TodoWidgetCross-Linux-x64.tar.gz`를 풀고 `TodoWidgetCross`를 실행합니다. 터미널에서는 압축을 푼 폴더에서 `./TodoWidgetCross`를 실행합니다.

.NET 런타임은 각 배포본에 포함되어 있습니다. Linux는 X11 또는 XWayland, 시스템 글꼴/fontconfig 등 데스크톱 라이브러리가 필요합니다. 한글 글꼴이 없는 Linux에서는 한글 글꼴을 설치해야 합니다. GNOME 등 알림 영역이 없는 환경에서도 접근할 수 있도록 Linux에서는 작업 표시줄에도 창이 표시됩니다.

**검증 범위:** Windows 실제 화면에서 실행 및 한글 수정·저장을 확인했습니다. 데이터 가져오기, 재시작 후 읽기, 휴지통 확인/취소 로직, 기존 데이터 보존, 설정 저장, 중복 실행 잠금은 자동 검사했습니다. macOS·Linux는 교차 빌드와 패키지 구조를 확인했으며 실제 기기 실행은 아직 검증하지 않았습니다. 투명도·창 이동·항상 위·트레이·자동 실행은 해당 OS에서 추가 확인이 필요합니다.

Mac 배포본은 Developer ID 서명 및 Apple 공증을 마치지 않은 테스트용입니다. Mac의 보안 정책으로 실행이 제한될 수 있습니다. 정식 배포 전 Mac에서 서명·공증을 진행해야 합니다. 보안 설정을 변경하는 스크립트는 포함하지 않습니다.

## 기존 목록

처음 실행하면 문서 폴더의 `TodoWidget Data/tasks.json`을 읽어 `TodoWidget Cross Data/tasks.json`으로 복사합니다. 목록, 완료 상태, 휴지통, 창 크기, 투명도, 모서리 설정을 가져오며 기존 파일은 변경하지 않습니다. 원본 사본은 새 저장 폴더의 `imported-original.json`에 보존됩니다.

이미 새 버전에서 저장한 목록이 있으면 이전 목록을 다시 덮어쓰지 않습니다. 두 버전 사이의 변경 내용이나 다른 컴퓨터와의 목록은 자동 동기화되지 않습니다. 새 버전에서 입력한 내용은 새 버전에만 저장됩니다.

더보기 메뉴의 `저장 위치…`에서 현재 경로를 확인하거나 원하는 폴더로 변경할 수 있습니다. 위치를 바꾸면 현재 목록과 설정을 새 폴더에 복사하며 기존 폴더의 파일은 백업용으로 남겨둡니다. `tasks.json`이 이미 있는 폴더는 실수로 덮어쓰지 않도록 선택할 수 없습니다.

다른 컴퓨터로 기존 목록을 가져가려면 앱을 종료한 상태에서 원래 컴퓨터의 `tasks.json`을 대상 컴퓨터에서 지정한 저장 폴더에 복사하세요. 대상 컴퓨터에 목록이 있다면 먼저 백업해야 합니다.

## 사용

- 입력란에 쓰고 Enter 또는 +: 할 일 추가
- 체크: 완료/미완료
- 연필: 수정, Enter 저장, Esc 취소
- 삭제 아이콘: 휴지통 이동
- 휴지통: 복원 또는 비우기. 비우기는 확인 창에서 확인을 눌러야 삭제됩니다.
- 제목줄 드래그: 이동. 창 테두리/모서리 드래그: 크기 조절. 위치와 크기는 종료할 때 저장합니다.
- ☰ → 화면·실행 설정: 프리셋·RGB 선택창·직접 입력으로 위젯 색상 지정, 글자·아이콘 색상 반전, 기본 색상 초기화, 불투명도, 모서리 둥글기, 항상 위, 로그인 자동 실행
- ×: 종료. 알림 영역 아이콘을 클릭하면 창을 앞으로 가져옵니다.
- 알림 영역 아이콘 우클릭 → 업데이트 확인: GitHub의 최신 정식 Release와 현재 버전을 비교합니다. 새 버전이 있으면 `업데이트가 있어요 · v버전`으로 표시되며 누르면 Release 페이지를 엽니다.

새 버전의 자동 실행은 처음에는 꺼져 있습니다. 새 버전으로 교체할 때는 기존 앱 설정에서 자동 실행을 끄고, 새 앱 설정에서 켜세요. 그렇지 않으면 로그인 때 두 앱이 함께 실행될 수 있습니다. 자동 실행을 켠 후 앱을 옮겼다면 새 위치에서 설정을 껐다 켜세요.

## 개발

소스는 `source` 폴더에 있습니다. .NET 8 SDK와 Avalonia 11.3.22를 사용합니다.

```
dotnet build source/TodoWidgetCross.csproj -c Release
dotnet run --project source/TodoWidgetCross.csproj -- --self-test ./test-output
dotnet publish source/TodoWidgetCross.csproj -c Release -r linux-x64 --self-contained true
```

`source/publish.ps1`은 OS별 빌드를 생성합니다. `source/package.ps1`은 이 작업 폴더의 빌드 결과를 Unix 실행 권한이 보존된 tar.gz로 포장한 실제 패키징 스크립트입니다. macOS .app 구조, 개발자 서명/공증 정보는 [Avalonia 공식 배포 문서](https://docs.avaloniaui.net/docs/deployment/macos)를 참고하세요. Linux 의존성은 [공식 Linux 배포 문서](https://docs.avaloniaui.net/docs/deployment/linux)에 안내되어 있습니다.
