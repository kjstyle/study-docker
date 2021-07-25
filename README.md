## docker 설치
* [Docker Download](https://hub.docker.com/editions/community/docker-ce-desktop-mac )
  * M1은 실리콘칩
  * M1이 아니면 
<img src="https://user-images.githubusercontent.com/21075371/126887134-c4f3117f-8d8a-43f9-ab89-67deb77f15ab.jpg" width="200" />

  1. dmg 파일로 더블클릭 -> 설치 시작
  2. 드래그해서 application directory로 이동
  3. application icon 을 double click
  4. 2021.06.25 기준으로 mac os 11이상이어야 docker설치가 가능하다고함
    + 내 mac은 high sierra이고, 10.13
    + 13년 맥북프로인데, 최대로 올려봐야 모하비인데 모하비도 10.14..
    + 망한건줄 알았는데.. 회사 맥북이 M1이라 습관적으로 apple chip version으로 다운로드 받았던 것...
    + 다시 intell chip version으로 다운로드함
  5. access 관련 질문이 나오고, 맥 암호를 입력하고 나면 도커가 실행됨
  6. 2분짜리 tutorial이 나옴. 직접 typing해서 로컬해서 테스트해볼 수 있는거라 처음이라면 따라해보는게 꾀나 유용해보임
![Tutorial](https://user-images.githubusercontent.com/21075371/126887113-4c9c5dcd-a975-4918-9dd2-d41eda8fdae0.jpg)
  7. 좌측 샘플 커맨드의 역슬래시는 한줄로 입력해야하지는 표기상 개행으로 할게..라는 의미라서 걍 한줄로 치면 됨
  8. 아래는 첫번째 커맨드 실행 결과이다. 역슬래시 없이 그냥 한줄로 입력했고, 로컬 repository에 image가 없으니 lastes를 pull받을게.. download하고 cloning할게...라는 로그가 찍힘
```
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
  10. 

