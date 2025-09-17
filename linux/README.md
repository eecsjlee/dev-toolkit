# Linux

이 문서는 Linux 환경에서 자주 사용하는 명령어와 관리 방법을 정리한 자료입니다.  
개발, 서버 운영, 데이터센터 환경 구축 등에 필요한 기본 지식을 빠르게 참고할 수 있도록 구성되었습니다.

## 주요 내용

1. **파일 및 디렉토리 관리**
   - `ls`, `cd`, `pwd`, `mkdir`, `rm`, `cp`, `mv`
   - 숨김 파일 보기, 권한 확인(`ls -la`)

2. **사용자 및 권한 관리**
   - `whoami`, `id`, `adduser`, `passwd`
   - 파일 권한 변경: `chmod`, `chown`, `chgrp`
   - `sudo`의 개념과 사용법

3. **프로세스 관리**
   - `ps`, `top`, `htop`, `kill`
   - 백그라운드 실행: `&`, `jobs`, `fg`, `bg`

4. **네트워크 관련 명령어**
   - `ping`, `curl`, `wget`
   - `ifconfig` 또는 `ip addr`
   - 포트 확인: `ss -tulpn`, `netstat`

5. **패키지 관리**
   - Debian 계열: `apt-get`, `apt`
   - RedHat 계열: `yum`, `dnf`
   - 패키지 설치, 업데이트, 삭제 방법

6. **서비스 및 시스템 관리**
   - 서비스 제어: `systemctl start|stop|status`
   - 부팅 시 서비스 자동 실행 설정
   - 로그 확인: `journalctl`, `/var/log`

7. **파일 검색과 편집**
   - 검색: `find`, `grep`
   - 편집기: `vi`, `nano`

8. **압축 및 아카이브**
   - `tar`, `gzip`, `bzip2`
   - 압축 해제 및 묶기 예시

9. **디스크 및 메모리 관리**
   - 디스크 확인: `df -h`, `du -sh`
   - 메모리 확인: `free -m`
   - 마운트 및 언마운트: `mount`, `umount`

10. **기타 자주 쓰는 명령어**
    - `echo`, `cat`, `less`, `tail -f`
    - 환경 변수 확인: `env`, `export`


## 대표적인 리눅스 배포판 소개

### Ubuntu (우분투)
- **기반**: Debian 계열  
- **특징**:
  - 데스크톱 및 서버 환경 모두에서 널리 사용됨
  - 풍부한 패키지와 커뮤니티 지원
  - `apt` 패키지 관리 도구 사용
  - LTS(Long Term Support) 버전은 5년 이상 안정적인 보안 업데이트 제공  
- **주요 활용 분야**:
  - 클라우드 서버 (AWS, Azure, GCP 등에서 기본 이미지 제공)
  - 개발 환경, 테스트 서버, 개인 데스크톱
  - AI/머신러닝, Docker/Kubernetes 실습

### Rocky Linux (록키 리눅스)
- **기반**: Red Hat Enterprise Linux (RHEL) 계열  
- **특징**:
  - CentOS의 후속 프로젝트로 시작
  - 기업 환경에서 안정성과 호환성 중시
  - `yum` 또는 `dnf` 패키지 관리 도구 사용
  - RHEL과 거의 동일한 구조와 패키지 호환성 보장  
- **주요 활용 분야**:
  - 기업용 서버 운영
  - 데이터센터 및 미션 크리티컬 환경
  - RHEL 기반 시스템을 무료로 사용하고자 할 때 대안


## 참고 자료
- [Linux 공식 문서](https://www.kernel.org/doc/)
- [The Linux Command Line](http://linuxcommand.org/)
- [TLDP (The Linux Documentation Project)](https://tldp.org/)
- [Ubuntu 공식 사이트](https://ubuntu.com/)
- [Rocky Linux 공식 사이트](https://rockylinux.org/)
