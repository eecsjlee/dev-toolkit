# Git 문제 해결 가이드 (Troubleshooting)

개발 중 Git을 사용하면서 자주 마주치는 문제와 해결 방법을 정리한 문서입니다.  

## 1. fatal: refusing to merge unrelated histories

**현상**: 서로 다른 Git 히스토리를 가진 두 브랜치를 병합할 때 발생  
**주로**: 초기 프로젝트 push 시 로컬과 GitHub의 이력이 다를 때

```bash
git pull origin main --allow-unrelated-histories
````

---

## 2. warning: LF will be replaced by CRLF

**현상**: 줄바꿈 방식(LF vs CRLF)이 OS 간 다를 때 발생
**해결**: `.gitattributes` 파일을 이용해 고정

```bash
# .gitattributes
* text=auto
```

또는 Git 설정 변경

```bash
git config --global core.autocrlf true   # Windows
git config --global core.autocrlf input  # macOS / Linux
```

## 3. detached HEAD 상태란?

**현상**: 특정 커밋으로 체크아웃했을 때 발생
**문제점**: 커밋은 가능하나 브랜치가 아님 (머리 없는 상태)

**해결**:

```bash
git checkout -b new-branch-name
```

이후 새 브랜치를 생성하고 정상적인 HEAD로 복구

## 4. pull 했는데 충돌(conflict)이 발생했어요!

**현상**: 같은 파일의 같은 위치가 서로 다르게 수정됨
**해결**:

1. 충돌 파일 수동 수정
2. 수정 후 `git add <파일명>`
3. `git commit`으로 병합 완료

**충돌 파일 확인**:

```bash
git status
```

**충돌 마커 예시**:

```txt
<<<<<<< HEAD
내 코드
=======
상대방 코드
>>>>>>> origin/main
```

## 5. 이전 커밋을 취소하고 싶어요

### 방법 1: 마지막 커밋 되돌리기 (수정은 유지)

```bash
git reset --soft HEAD~1
```

### 방법 2: 마지막 커밋 및 수정 사항 제거

```bash
git reset --hard HEAD~1
```

> 되돌리는 작업은 **push 전**에만 안전합니다.

## ❗ 6. 원격 브랜치를 강제로 덮어쓰기

**주의**: 정말 마지막 수단으로만 사용!

```bash
git push origin main --force
```

`--force-with-lease` 사용을 권장합니다:

```bash
git push --force-with-lease
```

## 7. 커밋 메시지를 다시 쓰고 싶어요

```bash
git commit --amend
```

> 이미 push 한 커밋을 수정할 경우, `--force` 푸시 필요


## 기타 참고

* [Git 공식 문서](https://git-scm.com/docs)
* [Git 문제 해결 Flowchart (external)](https://ohshitgit.com)
