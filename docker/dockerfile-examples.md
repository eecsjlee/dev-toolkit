# Dockerfile

## Dockerfile이란?

**Dockerfile**은 도커 이미지(Docker Image)를 만들기 위해 작성하는 \*\*명령어 모음(스크립트 파일)\*\*입니다.
쉽게 말해 **“이미지를 자동으로 조립하기 위한 레시피”** 같은 역할을 해요.

* 파일명은 일반적으로 **`Dockerfile`** (확장자 없음)
* 이 파일을 기반으로 `docker build` 명령어를 실행하면 도커 이미지를 생성
* 이미지에는 운영체제, 실행 환경, 라이브러리, 애플리케이션 코드 등이 포함됨

---

## Dockerfile 기본 구조

예시: 간단한 Python Flask 앱 실행용 Dockerfile

```dockerfile
# 1. 베이스 이미지 선택
FROM python:3.9-slim

# 2. 작업 디렉토리 설정
WORKDIR /app

# 3. 소스코드 복사
COPY . /app

# 4. 필요한 패키지 설치
RUN pip install -r requirements.txt

# 5. 컨테이너 시작 시 실행할 명령어 지정
CMD ["python", "app.py"]
```

---

## 주요 명령어

| 명령어          | 설명                                           |
| ------------ | -------------------------------------------- |
| `FROM`       | 베이스 이미지 지정 (예: `ubuntu:20.04`, `python:3.9`) |
| `WORKDIR`    | 컨테이너 내에서 작업 디렉토리 설정                          |
| `COPY`       | 로컬 파일을 컨테이너로 복사                              |
| `ADD`        | `COPY`와 비슷하지만, URL 다운로드나 압축 해제 가능            |
| `RUN`        | 이미지 빌드 과정에서 실행할 명령어 지정 (패키지 설치 등)            |
| `CMD`        | 컨테이너가 시작될 때 실행할 기본 명령어                       |
| `ENTRYPOINT` | 컨테이너 실행 시 고정적으로 실행되는 명령어                     |
| `EXPOSE`     | 컨테이너가 열어둘 포트 지정 (실제 포트 바인딩은 `docker run -p`) |
| `ENV`        | 환경 변수 설정                                     |

---

## Dockerfile → 이미지 → 컨테이너 흐름

1. **Dockerfile 작성**
   앱 실행 환경을 정의 (레시피 작성)
2. **이미지 빌드**

   ```bash
   docker build -t myapp:1.0 .
   ```

   (`-t`는 이미지 이름과 태그를 붙이는 옵션, `.`은 현재 디렉토리 의미)
3. **컨테이너 실행**

   ```bash
   docker run -d -p 8080:80 myapp:1.0
   ```

   → 브라우저에서 `http://localhost:8080` 접근 가능

---

## 비유

* **Dockerfile** = 요리 레시피
* **Docker build** = 요리사(빌드 과정)
* **Docker image** = 완성된 반조리 음식(이미지)
* **Docker run** = 그 음식을 실제로 조리해서 먹는 것(컨테이너 실행)
