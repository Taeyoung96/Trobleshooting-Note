# Trobleshooting-Note  

모든 문제 해결 방법을 블로그에 포스팅하면 좋지만,  
구글링을 통해 쉽게 나오는 방법들에 대해서는 굳이 그럴 필요가 없다고 생각한다.  
하지만 **나중에 비슷한 문제를 만났을 때, 조금이나마 시간을 단축하기 위해** Repository를 만들었다.  

우선 자유롭게 메모장형식으로 쓸 예정이다. 😆  

### 기본틀  

⭐️ Keyword   
💥 문제 발생  
❗️  해결  
📙 출처  

---  

⭐️ Keyword : Ubuntu에서 Github blog 빌드  
💥 문제 발생 : 우분투에서 Github blog를 로컬에서 빌드하고 싶을 때  
❗️ 해결 :  
1. 우선 터미널을 열고 /Taeyoung96.github.io 폴더로 들어간다.  
2. Jekyll 설치를 위해 gem을 사용한다.  
3. 설치가 모두 끝나면 `bundle exec jekyll serve`를 터미널에 입력  
4. 아래의 문구가 등장하면 크롬을 열고 `http://127.0.0.1:4000/`에 들어간다.  
```
Auto-regeneration: enabled for '/home/taeyoung/Desktop/Taeyoung96.github.io'
Server address: http://127.0.0.1:4000/
Server running... press ctrl-c to stop.
```
📙 출처 : [우분투에서 github.io(블로그) 생성 및 preview를 위한 jekyll install](https://donghwa-kim.github.io/jekyll.html)  

---

⭐️ Keyword : Pycharm과 Docker를 연동, Pycharm에서 docker 사용  
💥 문제 발생 : Docker를 이용하여 Container는 제작했으나, 이를 Pycharm에서 사용하려고 할 때  
❗️ 해결 : 출처에 블로그를 그대로 따라가면 된다. ssh를 활용해서 docker container에 접속함.  

📙 출처 : [딥러닝 개발환경 세팅기(Docker, PyCharm) (1)](https://soundprovider.tistory.com/entry/%EB%94%A5%EB%9F%AC%EB%8B%9D-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-%EC%84%B8%ED%8C%85%EA%B8%B0Docker-PyCharm-1?category=1126937)  
[딥러닝 개발환경 세팅기(Docker, PyCharm) (2)](https://soundprovider.tistory.com/entry/%EB%94%A5%EB%9F%AC%EB%8B%9D-%EA%B0%9C%EB%B0%9C%ED%99%98%EA%B2%BD-%EC%84%B8%ED%8C%85%EA%B8%B0Docker-PyCharm-2?category=1126937?category=1126937)  

---

⭐️ Keyword : Markdown에서 글자색 변경  
💥 문제 발생 : Markdown언어에서 글자색을 검은색이 아닌 다른 색으로 변경하고 싶을 때  
❗️ 해결 : html 태그를 써서 해결.  
`<font color='ff0000'> [이 안에 글 적음]</font>`  
예시는 빨간색인데, 색을 바꾸고 싶다면 `ff0000`를 [헥스 코드](https://namu.wiki/w/%ED%97%A5%EC%8A%A4%20%EC%BD%94%EB%93%9C)를 활용해서 바꿔야함.    

📙 출처 : [markdown 관련해서 글자색을 변경할 수 있으면 너무 좋겠습니다.](https://github.com/yona-projects/yona/issues/474)  

---
⭐️ Keyword : Docker container 실행   
💥 문제 발생 : Docker container를 `run` command를 활용해서 만들고, `docker ps -a`로 확인해 본 결과 남아있을 때,  
             다시 docker container를 실행시키고 들어가고 싶을 때  
❗️  해결 : 우선 `docker ps -a` 가 아닌 `docker ps`로 실행을 했을 때, 컨테이너가 실행이 되있어야 한다. (docker start `컨테이너 이름` 을 활용)  
          그 다음 `docker exec <CONTAINER_ID> <COMMAND>`로 컨테이너 안으로 접속한다.  
📙 출처 : [docker exec 사용법: 실행중인 컨테이너에 명령어 실행하는 방법](https://www.lainyzine.com/ko/article/docker-exec-executing-command-to-running-container/)   

---
⭐️ Keyword : Eigen Matrix 형변환 (typecasting)    
💥 문제 발생 : Eigen Library를 사용하던 도중 Matrix의 형변환을 하고 싶을 때  
❗️ 해결 : 아래 코드는 double형 Matrix를 float형으로 바꾸는 방법  
```
Eigen::MatrixXd d;                       // Matrix of doubles.
Eigen::MatrixXf f = d.cast <float> ();   // Matrix of floats.
```
📙 출처 : [Cast Eigen::MatrixXd to Eigen::MatrixXf](https://stackoverflow.com/questions/24764031/cast-eigenmatrixxd-to-eigenmatrixxf)  

---  

⭐️ Keyword : Docker 용량 확인   
💥 문제 발생 : 갑자기 컴퓨터 용량이 줄어듬.. 문제는 docker container였다.  
❗️  해결 : `docker system df` 커맨드로 용량 확인, Container 모두 삭제.    
📙 출처 : [로그가 서버를 죽이러 왔다.](https://uiandwe.tistory.com/1313)  
         [Docker 용량 확인 및 관리(df, prune)](https://lifeplan-b.tistory.com/146)  

---

⭐️ Keyword : 우분투 디스크 용량 확인    
💥 문제 발생 : 메뉴에 있는 'Disk Usage Analyzer'로 확인했을 때, permission denied 때문에 용량 확인을 못하는 것들이 있었음.    
❗️  해결  :  터미널에 `sudo baobab` 입력  
📙 출처 : [disk space used up](https://askubuntu.com/questions/305554/disk-space-used-up)  

---

⭐️ Keyword : 윈도우에서 Gitblog 로컬 빌드  
💥 문제 발생 : No source of timezone data could be found라는 문구와 함께 빌드가 되지 않는 현상 발생   
❗️  해결 : `Gemfile`에 `gem 'tzinfo-data'`라는 코드를 추가,  
          `gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw]`이라는 코드는 원래 있었는데...  
          
📙 출처 : [[Github 깃허브] Windows 환경에서 Github Blog 생성하기](https://iingang.github.io/posts/windows-github-set/)  
          [[GitHub] Jekyll을 이용해 깃허브 블로그 테마 변경하기](https://veggietech.tistory.com/32)  
          [[Rails] 64비트 환경에서 tzinfo 관련 에러를 해결해보자](https://honsal.tistory.com/38)  
          [Resolving TZInfo::DataSourceNotFound Errors](https://github.com/tzinfo/tzinfo/wiki/Resolving-TZInfo::DataSourceNotFound-Errors)  
          [TZInfo::DataSourceNotFound](https://github.com/phusion/passenger-docker/issues/195)  

---

⭐️ Keyword : 윈도우 10 사용자 폴더 변경 후 에러  
💥 문제 발생 : 사용자 폴더 변경을 한 후, 부팅도 느려지고 원하는 사용자 폴더에 접근이 불가능함.   
❗️  해결 : 레지스트리 편집기에서 ProfileList 변경   

📙 출처 : [윈도우10 사용자 계정 손상시 복구하기](https://zkim0115.tistory.com/m/282)  
          [사용자 폴더 이름 바꾸기《1/2》 - Windows 10](https://www.tabmode.com/windows10/win10-user-name-change.html)  
          
          

