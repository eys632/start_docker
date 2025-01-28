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
1. **PowerShell(관리자 권한)**을 열고 다음 명령어를 실행:
   ```powershell
   wsl --install
   wsl --set-default-version 2
   wsl --install -d Ubuntu
   ```
   
PowerShell(관리자 권한)에서 다음 명령어를 실행하여 필요한 기능을 활성화:
```
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V /all
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all
dism.exe /online /enable-feature /featurename:Windows-Subsystem-Linux /all
```

### 2. 설치 단계 - Docker Desktop 설치
2.4 Docker Desktop 설치
1. Docker 공식 웹사이트에서 Docker Desktop 설치 파일을 다운로드
2. 설치 과정 중 기본 설정으로 진행하고, 설치 완료 후 Docker Desktop을 실행

## 3. 설치 확인 및 점검

### 3.1 WSL2 기본 배포판 확인
**PowerShell(관리자 권한)**에서 다음 명령어를 실행하여 WSL2가 기본 배포판으로 설정되어 있는지 확인:
```powershell
wsl -l -v
```
결과에서 사용 중인 리눅스 배포판이 기본값이며, 버전이 2로 표시되어야 함


### 3. 설치 확인 및 점검 - Docker Engine 상태 확인


---------------


### 2.2 WSL2 설치 및 설정

1. **PowerShell(관리자 권한)**을 열고 다음 명령어를 실행합니다:
   ```powershell
   wsl --install
기본 WSL 버전을 WSL2로 설정합니다:

powershell
복사
편집
wsl --set-default-version 2
원하는 리눅스 배포판(예: Ubuntu)을 설치합니다:

powershell
복사
편집
wsl --install -d Ubuntu
