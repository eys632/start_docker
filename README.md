내가 사용하고 있는 pc에는 wsl2가 정상적으로 활성화되지 않아 도카 엔진이 활성화되지 않음

# Windows 11 Pro에서 Docker 설치 및 환경 구성 가이드
 
## 1. 시스템 요구 사항
Docker 시스템 요구 사항:
- **운영 체제**: Windows 10 64-bit (2004 이상) 또는 Windows 11 Pro/Enterprise/Education
- **가상화 기술 활성화**: BIOS에서 Intel VT-x 또는 AMD-V 활성화 필요
- **WSL2(Windows Subsystem for Linux 2)**: 최신 버전으로 설치 및 설정
- **Windows 기능 활성화**:
  - Hyper-V
  - Windows Subsystem for Linux
  - Virtual Machine Platform

## 2. 설치 단계

### 2.1 BIOS에서 가상화 기술 활성화
1. 컴퓨터를 재부팅하여 BIOS 설정에 진입
2. "Intel VT-x" 또는 "AMD-V" 옵션을 찾아 활성화
3. 변경 사항을 저장하고 종료

### 2.2 WSL2 설치 및 설정

1. PowerShell(관리자 권한)에서 다음 명령어를 실행:
 ```powershell
 wsl --install
```

2. 기본 WSL 버전을 WSL2로 설정:
```powershell
wsl --set-default-version 2
```

3. 원하는 리눅스 배포판(예: Ubuntu)을 설치:
```powershell
wsl --install -d Ubuntu
```

### 2.3 Windows 기능 활성화
   
PowerShell(관리자 권한)에서 다음 명령어를 실행하여 필요한 기능을 활성화:
```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V /all
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all
dism.exe /online /enable-feature /featurename:Windows-Subsystem-Linux /all
```

### 2.4 Docker Desktop 설치

1. Docker 공식 웹사이트(https://www.docker.com/products/docker-desktop)에서 Docker Desktop 설치 파일을 다운로드
2. 설치 과정 중 기본 설정으로 진행하고, 설치 완료 후 Docker Desktop을 실행

## 3. 설치 확인 및 점검

### 3.1 WSL2 기본 배포판 확인
PowerShell(관리자 권한)에서 다음 명령어를 실행하여 WSL2가 기본 배포판으로 설정되어 있는지 확인:
```powershell
wsl -l -v
```
결과에서 사용 중인 리눅스 배포판이 기본값이며, 버전이 2로 표시되어야 함

### 3.2 Docker Engine 상태 확인
Docker Desktop 실행 후, Docker Engine이 "Running" 상태인지 확인
문제가 있을 경우 Docker Desktop 설정에서 WSL2를 기본 백엔드로 선택했는지 확인

## 4. 추가 권장 사항

- Docker 사용 중 관리자 권한이 필요하다면 사용자 계정을 `docker-users` 그룹에 추가
- 설치 중 문제가 발생하거나 엔진이 멈춘 상태로 구동되지 않으면, WSL2 및 Windows 기능 설정 확인해야 함

## 5. 참고 링크

- [Docker Desktop 공식 다운로드](https://www.docker.com/products/docker-desktop)
- [WSL 설치 및 사용 가이드](https://docs.microsoft.com/ko-kr/windows/wsl/)
