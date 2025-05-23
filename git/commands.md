# Git 자주 쓰는 명령어 모음

## 브랜치 관련
- git branch -a : 전체 브랜치 목록
- git checkout -b feature/login : 새 브랜치 생성 및 이동
- git switch -c feature/login : 위와 동일, 추천 방식

## 커밋 관련
- git commit -m "feat: 로그인 기능 추가"
- git commit --amend : 직전 커밋 수정

## 원격 저장소
- git remote -v
- git push -u origin main

## 리셋 / 되돌리기
- git reset --soft HEAD~1
- git restore <파일명>