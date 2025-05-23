# Docker 명령어 정리

이 문서는 Docker 사용 시 자주 사용하는 명령어들을 정리한 것입니다. 컨테이너 생성, 이미지 관리, 네트워크 설정 등 상황별로 구분하여 실습과 실무에 도움이 되도록 구성하였습니다.

## 이미지(Image) 관련

```bash
# Docker 이미지 목록 보기
docker images

# 이미지 빌드하기 (Dockerfile 위치에서)
docker build -t [이미지이름:태그] .

# DockerHub에서 이미지 받아오기
docker pull [이미지이름:태그]

# 이미지 삭제
docker rmi [이미지ID 또는 이름]
```

## 컨테이너(Container) 관련

```bash
# 컨테이너 실행
docker run -d --name [컨테이너이름] [이미지이름]

# 포트 매핑하여 실행
docker run -d -p 8080:80 --name [컨테이너이름] [이미지이름]

# 컨테이너 목록 보기 (실행 중인 것만)
docker ps

# 전체 컨테이너 보기 (중지 포함)
docker ps -a

# 컨테이너 접속
docker exec -it [컨테이너이름] sh

# 컨테이너 로그 보기
docker logs [컨테이너이름]

# 컨테이너 중지
docker stop [컨테이너이름]

# 컨테이너 삭제
docker rm [컨테이너이름]

# 컨테이너 강제 삭제 (중지되지 않은 경우)
docker rm -f [컨테이너이름]
```

## 🧰 기타 명령어

```bash
# 사용하지 않는 이미지, 컨테이너, 네트워크 삭제
docker system prune

# 컨테이너 상태 확인 (리소스 사용량 등)
docker stats

# 이미지 상세 정보 확인
docker inspect [이미지ID 또는 이름]

# 컨테이너 네트워크 확인
docker network ls
```

## 📄 참고문헌

* 공식 문서: [https://docs.docker.com/](https://docs.docker.com/)