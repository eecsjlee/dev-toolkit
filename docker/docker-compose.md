# Docker Compose 사용 가이드

이 문서는 `docker-compose`의 개념과 기본 사용법, 실무에서 자주 사용되는 패턴들을 정리한 가이드입니다.

## 1. Docker Compose란?

Docker Compose는 **다중 컨테이너 애플리케이션을 정의하고 실행**할 수 있도록 도와주는 도구입니다.  
YAML 파일(`docker-compose.yml`)을 통해 컨테이너의 서비스, 네트워크, 볼륨 등을 선언적으로 설정할 수 있습니다.

- 여러 서비스를 하나의 명령어로 실행 가능 (`docker compose up`)
- 컨테이너 간 의존성, 네트워크, 환경 설정을 손쉽게 관리
- 개발 및 테스트 환경에서 특히 유용

## 2. 설치 확인

Docker Desktop에 기본 포함되어 있습니다. CLI에서 다음 명령어로 버전을 확인할 수 있습니다:

```bash
docker compose version
```

## 3. docker-compose.yml 기본 구조

```yaml
version: '3.8'

services:
  web:
    image: nginx
    ports:
      - "8080:80"
  
  app:
    build: .
    ports:
      - "3000:3000"
    depends_on:
      - db
  
  db:
    image: postgres
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
```

## 4. 주요 명령어 정리

| 명령어                    | 설명                             |
| ---------------------- | ------------------------------ |
| `docker compose up`    | 서비스 실행 (`-d` 옵션으로 백그라운드 실행 가능) |
| `docker compose down`  | 모든 컨테이너, 네트워크, 볼륨 정리           |
| `docker compose build` | 서비스 빌드                         |
| `docker compose logs`  | 로그 확인                          |
| `docker compose ps`    | 실행 중인 서비스 목록 확인                |

## 5. 실무 예시

### 예시 1: Node.js + MongoDB

```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - MONGO_URL=mongodb://mongo:27017/mydb
    depends_on:
      - mongo

  mongo:
    image: mongo
    ports:
      - "27017:27017"
```

### 예시 2: Nginx + React + Express

```yaml
version: '3'

services:
  nginx:
    image: nginx
    ports:
      - "80:80"
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - frontend
      - backend

  frontend:
    build: ./frontend
    ports:
      - "3000:3000"

  backend:
    build: ./backend
    ports:
      - "5000:5000"
```

## 6. 볼륨과 네트워크 사용

```yaml
volumes:
  db-data:

networks:
  backend:
```

```yaml
services:
  db:
    volumes:
      - db-data:/var/lib/postgresql/data
    networks:
      - backend
```

## 7. 유용한 팁

* `.env` 파일을 함께 사용하여 환경변수 분리 가능
* `depends_on`은 시작 순서만 보장, 상태 확인은 Healthcheck를 추가로 설정
* 여러 파일로 환경 분리 가능:

```bash
docker compose -f docker-compose.yml -f docker-compose.prod.yml up
```

## 8. 참고 링크

* [공식 문서](https://docs.docker.com/compose/)
* [Compose 파일 레퍼런스](https://docs.docker.com/compose/compose-file/)
