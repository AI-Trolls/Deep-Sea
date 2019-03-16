## 윈도우즈에서 ubuntu 환경으로 개발하기
- Microsoft Store에서 ubuntu를 설치!
- 실행하면 에러 발생: The Windows Subsystem for Linux optional component is not enabled. Please enable it and try again.
- 해결 방법
  1. Windows PowerShell을 관리자 권한으로 실행
  2. Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux 를 입력(실행)
  3. 재시작
