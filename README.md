# 용어
  >Docker compose : 여러 개의 컨테이너로부터 이루어진 서비스를 구축, 실행하는 순서를 자동으로 하여, 관리를 간단히하는 기능
  >
  >Docker volume : 도커 컨테이너가 실행 중에 작성 혹은 수정된 파일은 호스트 쪽 파일 시스템에 마운트되지 않는 한 컨테이너가 파기될 때 호스에서 함께 삭제 된다. 컨테이너를 사용해서 애플리케이션을 운영하다 보면 새로운 버전의 컨테이너가 배포돼더라도 이전 버전의 컨테이너에서 사용하던 파일들을 그대로 사용할 수 있어야 한다. 이런 경우에 사용되는 것이 데이터 볼륨 이다.
  
# React 애플리케이션을 Dockerize 하는 법.

1. Create Docker file
2. Create Docker image
3. Run image in Docker container
4. Docker Compose with volumes.



# 실제 적용

`npx create-react-app react-docker` 으로 리액트 프로젝트(react-docker)를 생성한다.

Dockerfile 을 만들고 노드 이미지를 불러온다.

(이미지는 [https://hub.docker.com/](https://hub.docker.com/)에서 찾을 수 있다.)
```Dockerfile
FROM node:17-alpine3.14
WORKDIR /react-docker

ENV PATH="./node_modules/.bin:$PATH"
COPY . .
RUN npm run build
CMD ["npm","start"]
```

## Dockerfile에서 자주쓰이는 명령어
>FROM : base 이미지를 지정해주기위해 사용
>
>WORKDIR : 작업 디렉토리 전환 ( shell 에서 cd)
>
>RUN : 마치 쉘(shell)에서 커맨드를 실행하는 것 처럼 이미지 빌드 과정에서 필요한 커맨드를 실행하기 위해서 사용된다.<br/>
>     (보통 이미지 안에 특정 소프트웨어를 설치하기 위해서 많이 사용됨.)
>

## Docker 명령어
>`docker build <옵션> <Dockerfile 경로>` : --tag 옵션으로 이미지 이름과 태그를 설정할 수 있습니다. 이미지 이름만 설정하면 태그는 latest로 설정됩니다.
>
>`docker build --tag react .` <br/>
>`docker run --publish 3000:3000 react`<br/>
>
>`docker-compose build`<br/>
>`docker-compose run`<br/>
>
---
