docker 설치
====
* [Docker Download](https://hub.docker.com/editions/community/docker-ce-desktop-mac )
  * M1은 실리콘칩
  * M1이 아니면 
<img src="https://user-images.githubusercontent.com/21075371/126887134-c4f3117f-8d8a-43f9-ab89-67deb77f15ab.jpg" width="200" />

  1. dmg 파일로 더블클릭 -> 설치 시작
  2. 드래그해서 application directory로 이동
  3. application icon 을 double click
  5. access 관련 질문이 나오고, 맥 암호를 입력하고 나면 도커가 실행됨
  6. 2분짜리 tutorial이 나옴. 직접 typing해서 로컬해서 테스트해볼 수 있는거라 처음이라면 따라해보는게 꾀나 유용해보임
![Tutorial](https://user-images.githubusercontent.com/21075371/126887113-4c9c5dcd-a975-4918-9dd2-d41eda8fdae0.jpg)
  7. 좌측 샘플 커맨드의 역슬래시는 한줄로 입력해야하지는 표기상 개행으로 할게..라는 의미라서 걍 한줄로 치면 됨
  8. 아래는 첫번째 커맨드 실행 결과이다. 역슬래시 없이 그냥 한줄로 입력했고, 로컬 repository에 image가 없으니 lastes를 pull받을게.. download하고 cloning할게...라는 로그가 찍힘
```bash
kjstyleui-MacBook-Pro:~ kjstyle$ docker run --name repo alpine/git clone https:
//github.com/docker/getting-started.git 
Unable to find image 'alpine/git:latest' locally
latest: Pulling from alpine/git
540db60ca938: Pull complete 
9d962f943834: Pull complete 
d8b80141431d: Pull complete 
Digest: sha256:0590372ee83d4d0ff4f08f8d2a98b0ba413d911a2e89c1d3418a1fed9a66337c
Status: Downloaded newer image for alpine/git:latest
Cloning into 'getting-started'...
```
  10. 현재 경로로 cp한다음, docker build를 진행... 생각보다 시간이 소요됨..
![Tutorial_및_다운로드](https://user-images.githubusercontent.com/21075371/126887349-1deccea0-4cd3-41d5-bbfe-350edf2f420b.jpg)
  12. docker run 함.. 옵션을 주고 host와 80:80으로 매핑..출력되는 hash값은 이미지의 hash값이겠지..
```bash
kjstyleui-MacBook-Pro:getting-started kjstyle$ docker run -d -p 80:80 --name do
cker-tutorial docker101tutorial 
20cf544418bac21244e2f0b53ae2c2aa89135502044dde73c6ee240b7783474b
```
  13. hash아닌듯.. 이미지리스트의 hash값과 다름
```
kjstyleui-MacBook-Pro:getting-started kjstyle$ docker images
REPOSITORY          TAG       IMAGE ID       CREATED         SIZE
docker101tutorial   latest    9146c87a5e36   5 minutes ago   28.2MB
alpine/git          latest    b8f176fa3f0d   2 months ago    25.1MB
```
  14. share해봐라.. docker에 가입도 해봐라..가 마지막이지만... localhost:80 으로 docker로 80포트로 잘 떠있는지 먼저 확인.. docker로 80포트로 웹서비스 pull -> build -> run -> 확인..진행 완료
![Getting_Started](https://user-images.githubusercontent.com/21075371/126887413-b7c7b287-307b-4c6a-a374-8546f3f758d6.jpg)
  15. tutorial을 포함한 install과정은 여기까지..



docker 기본 명령어
===
### docker images

### docker ps
```bash
kjstyleui-MacBook-Pro:~ kjstyle$ docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED       STATUS                   PORTS                               NAMES
20cf544418ba   docker101tutorial   "/docker-entrypoint.…"   2 hours ago   Up 2 hours               0.0.0.0:80->80/tcp, :::80->80/tcp   docker-tutorial
26e59a35797d   alpine/git          "git clone https://g…"   3 hours ago   Exited (0) 3 hours ago                                       repo
```


### docker stop 
```bash
kjstyleui-MacBook-Pro:~ kjstyle$ docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED       STATUS                   PORTS                               NAMES
20cf544418ba   docker101tutorial   "/docker-entrypoint.…"   2 hours ago   Up 2 hours               0.0.0.0:80->80/tcp, :::80->80/tcp   docker-tutorial
26e59a35797d   alpine/git          "git clone https://g…"   3 hours ago   Exited (0) 3 hours ago                                       repo
kjstyleui-MacBook-Pro:~ kjstyle$ docker stop 20cf544418ba
20cf544418ba
kjstyleui-MacBook-Pro:~ kjstyle$ docker ps -a
CONTAINER ID   IMAGE               COMMAND                  CREATED       STATUS                     PORTS     NAMES
20cf544418ba   docker101tutorial   "/docker-entrypoint.…"   3 hours ago   Exited (0) 5 seconds ago             docker-tutorial
26e59a35797d   alpine/git          "git clone https://g…"   3 hours ago   Exited (0) 3 hours ago               repo
kjstyleui-MacBook-Pro:~ kjstyle$ 
```


### docker search [찾을이미지명]
```bash
kjstyleui-MacBook-Pro:~ kjstyle$ docker search openjdk
NAME                            DESCRIPTION                                     STARS     OFFICIAL   AUTOMATED
openjdk                         OpenJDK is an open-source implementation of …   2843      [OK]       
adoptopenjdk                    Official Images for OpenJDK + HotSpot and Op…   305       [OK]       
adoptopenjdk/openjdk11          Docker Images for OpenJDK Version 11 binarie…   153                  
adoptopenjdk/openjdk8           Docker Images for OpenJDK Version 8 binaries…   97                   
adoptopenjdk/openjdk8-openj9    Docker Images for Eclipse OpenJ9 Version 8 b…   45                   
adoptopenjdk/openjdk11-openj9   Docker Images for Eclipse OpenJ9 Version 11 …   40                   
arm64v8/openjdk                 OpenJDK is an open-source implementation of …   32                   
adoptopenjdk/openjdk12          Docker Images for OpenJDK Version 12 binarie…   19                   
arm32v7/openjdk                 OpenJDK is an open-source implementation of …   17                   
shipilev/openjdk                OpenJDK development builds                      11                   
adoptopenjdk/openjdk13          Docker Images for OpenJDK Version 13 binarie…   10                   
adoptopenjdk/openjdk14          Docker Images for OpenJDK Version 14 binarie…   9                    
adoptopenjdk/openjdk15          Docker Images for OpenJDK Version 15 binarie…   8                    
adoptopenjdk/openjdk16          Docker Images for OpenJDK Version 16 binarie…   7                    
amd64/openjdk                   OpenJDK is an open-source implementation of …   4                    
adoptopenjdk/openjdk10          Docker Images for OpenJDK Version 10 binarie…   3                    
adoptopenjdk/openjdk9           Docker Images for OpenJDK Version 9 binaries…   2                    
classmethod/openjdk-with-git    docker image for openjdk and git                1                    [OK]
symphonicsoft/openjdkbase       Openjdk base images with dumb-init              1                    
ccitest/openjdk                 CircleCI test images for OpenJDK                1                    [OK]
winamd64/openjdk                OpenJDK is an open-source implementation of …   1                    
suranagivinod/openjdk8          openjdk:8-jre-slim, zip & unzip                 0                    
cimg/openjdk                    The CircleCI OpenJDK (Java) Docker Convenien…   0                    
cfje/openjdk                    OpenJDK Builder Image                           0                    
ccistaging/openjdk              CircleCI images for OpenJDK                     0                    [OK]
```
