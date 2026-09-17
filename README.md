# 오늘 할 일 Cross

바탕화면 한쪽에 위젯처럼 띄워 두고 오늘 해야 할 일을 간단히 관리하는 데스크톱 앱입니다. Windows, macOS, Linux에서 실행할 수 있도록 [.NET 8](https://dotnet.microsoft.com/)과 [Avalonia UI](https://avaloniaui.net/)로 만들었습니다.

현재 버전: **2.7.4**

## 개발 정보

- 개발자: 황정윤
- 소속: 건국대학교 건축환경 및 에너지 연구실
- 이메일: tkwkrkswl@gmail.com
- 라이선스: [MIT License + Commons Clause](LICENSE)

회사와 기관을 포함해 누구나 무료로 사용하고 수정·공유할 수 있습니다. 프로그램 자체 또는 기능의 가치가 대부분 이 프로그램에서 나오는 제품·서비스를 유료로 판매하는 것은 허용하지 않습니다. 이 조건으로 인해 OSI가 정의하는 오픈소스 라이선스는 아니며, 소스 공개형 라이선스입니다.

## 주요 기능

- 컴퓨터 로그인 시 자동 실행
- 할 일 추가, 완료 체크, 내용 수정
- 삭제한 항목을 휴지통에서 복원하거나 확인 후 완전히 비우기
- 창 이동 및 크기 조절
- 불투명도와 모서리 둥글기 조절
- 프리셋 또는 `#RRGGBB` 입력으로 위젯 색상 지정
- RGB 슬라이더와 실시간 미리 보기를 제공하는 색상 선택창
- 밝은 배경에서도 보이는 RGB 반대색 글자·체크박스·조작 아이콘 옵션
- 버튼 한 번으로 처음 색상 `#2B3B43` 복원
- 항상 위에 표시
- 연·월·일·요일 표시
- 목록, 창 위치, 크기와 화면 설정 자동 저장
- 사용자가 저장 폴더를 직접 지정
- 알림 영역 아이콘에서 위젯 다시 열기
- GitHub Release를 확인해 새 버전 알림 표시
- 더보기 메뉴에서 버전, 개발자, 소속, 이메일과 라이선스 확인
- 입력창 바로 위에서 통통 뛰어 걷고, 웃음·울음·놀람·졸림 표정에 맞춰 자동으로 말하는 비공식 팬아트 스핔이
- 스핔이를 누르면 부드럽게 납작해지며 엎드리고, 약 3초 뒤 자연스럽게 다시 일어나 걷기
- 설정에서 스핔이 표시 여부 선택

## 실행 방법

### Windows 64비트

간편 설치는 `TodoWidgetCross-Setup-Windows-x64.exe`를 실행합니다. 설치 위치를 직접 선택할 수 있고 시작 메뉴, 선택적 바탕화면 바로가기와 제거 프로그램이 구성됩니다.

설치 없이 사용하려면:

1. `TodoWidgetCross-Windows-x64.zip`을 내려받습니다.
2. 압축을 전부 풉니다.
3. 폴더 안의 `TodoWidgetCross.exe`를 실행합니다.

실행 파일 옆의 DLL과 런타임 파일이 필요하므로 `TodoWidgetCross.exe`만 따로 옮기면 안 됩니다. 바탕화면에는 실행 파일의 바로가기를 만들어 사용하는 것이 좋습니다.

### macOS

- Apple Silicon(M1, M2, M3, M4 등): `TodoWidgetCross-macOS-arm64.tar.gz`
- Intel Mac: `TodoWidgetCross-macOS-x64.tar.gz`

압축을 풀고 `TodoWidget Cross.app`을 응용 프로그램 폴더로 옮깁니다. 현재 배포본은 Apple 개발자 서명과 공증을 하지 않은 시험판이므로 처음에는 Control 클릭 후 `열기`를 선택해야 할 수 있습니다.

### Linux 64비트

`TodoWidgetCross-Linux-x64.tar.gz`의 압축을 푼 뒤 다음 명령으로 실행합니다.

```bash
./TodoWidgetCross
```

Linux에서는 X11 또는 XWayland, fontconfig와 시스템 글꼴 등 일반적인 데스크톱 라이브러리가 필요합니다.

## 사용법

- 입력란에 내용을 적고 `Enter` 또는 `+`: 할 일 추가
- 체크박스: 완료 또는 미완료 전환
- 연필 아이콘: 내용 수정
- 삭제 아이콘: 휴지통으로 이동
- 휴지통: 항목 복원 또는 전체 비우기
- 제목줄 드래그: 창 이동
- 테두리와 모서리 드래그: 창 크기 조절
- 더보기 → `화면·실행 설정…`: 색상, 불투명도, 모서리, 항상 위, 자동 실행 설정
- 더보기 → `저장 위치…`: 현재 저장 경로 확인 및 폴더 변경

## 데이터 저장

기본 저장 파일은 문서 폴더의 `TodoWidget Cross Data/tasks.json`입니다. 저장 위치는 앱의 더보기 메뉴에서 원하는 폴더로 변경할 수 있습니다.

위치를 바꾸면 현재 목록과 설정을 새 폴더에 복사하고 기존 폴더의 파일은 백업용으로 남깁니다. 데이터 손실을 막기 위해 `tasks.json`이 이미 있는 폴더는 덮어쓰지 않습니다.

처음 실행할 때 기존 Windows 버전의 `TodoWidget Data/tasks.json`이 발견되면 목록과 설정을 새 저장소로 한 번 가져옵니다. 원본 파일은 변경하지 않습니다.

## 업데이트 배포

앱은 [`HwangMars/Simple-to-do-list-by-JH`](https://github.com/HwangMars/Simple-to-do-list-by-JH)의 최신 정식 Release를 확인합니다. 단순히 저장소에 파일을 푸시하는 것만으로는 업데이트가 표시되지 않습니다.

1. GitHub 저장소의 `Releases`에서 새 Release를 만듭니다.
2. 태그를 `v2.7.4`처럼 앱 버전에 맞춥니다.

## 팬 콘텐츠 안내

앱에 포함된 `Assets/speaki-*.png`는 트릭컬 리바이브의 스피키/스핔이에서 영감을 받아 새로 제작한 비공식 비영리 팬아트입니다. 게임 원본 이미지를 복제한 리소스가 아니며, 트릭컬 리바이브와 관련 IP의 권리는 에피드게임즈에 있습니다. 자세한 내용은 [팬 콘텐츠 안내](docs/FAN-CONTENT-NOTICE.md)를 확인하세요.
3. Windows ZIP과 필요한 운영체제별 파일을 Release 자산으로 첨부합니다.
4. 초안이나 사전 출시가 아닌 정식 Release로 게시합니다.

앱 시작 시 한 번 자동 확인하며, 알림 영역 아이콘의 우클릭 메뉴에서 수동으로 다시 확인할 수 있습니다.

## 개발

필요한 환경:

- .NET 8 SDK
- Avalonia 11.3.22

소스 코드는 `source` 폴더에 있습니다.

```powershell
dotnet build source/TodoWidgetCross.csproj -c Release
dotnet run --project source/TodoWidgetCross.csproj
dotnet run --project source/TodoWidgetCross.csproj -- --self-test ./test-output
```

특정 운영체제용 자체 포함 빌드를 만들려면 RID를 지정합니다.

```powershell
dotnet publish source/TodoWidgetCross.csproj -c Release -r win-x64 --self-contained true
dotnet publish source/TodoWidgetCross.csproj -c Release -r osx-arm64 --self-contained true
dotnet publish source/TodoWidgetCross.csproj -c Release -r linux-x64 --self-contained true
```

`source/publish.ps1`은 지원 운영체제별 빌드를 만들고, `source/package.ps1`은 `dist` 폴더에 Windows ZIP과 macOS·Linux tar.gz 배포 파일을 생성합니다.

`source/installer.iss`는 Inno Setup으로 `dist` 폴더에 Windows 설치 EXE를 생성합니다. `package.ps1 -Iscc "C:\\경로\\ISCC.exe"`처럼 컴파일러 경로를 넘기면 다른 배포 파일과 함께 설치 EXE도 만듭니다. 설치 프로그램은 현재 서명되지 않았으며 인증서를 사용자 컴퓨터의 신뢰 저장소에 추가하지 않습니다.

## 검증 범위

Windows에서는 실제 화면 실행, 한글 입력과 수정, 저장, 창 크기 조절과 설정 복원을 확인했습니다. macOS와 Linux 배포본은 교차 빌드 및 패키지 구조를 검사했지만 실제 기기에서의 자동 실행과 알림 영역 동작은 추가 확인이 필요합니다.
