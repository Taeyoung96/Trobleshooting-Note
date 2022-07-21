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
          
---

⭐️ Keyword : 우분투 chrome 원격 데스크톱 설정   
💥 문제 발생 : 팀뷰어는 너무 느려서, chrome 원격 데스크톱으로 설정  
❗️  해결 : 블로그 따라서 쭉 하면 됌. 나같은 경우는 블로그에 있는 `4. 터미널 켜서 계정을 추가한다.` 이 부분은 Skip함.     

📙 출처 : [리눅스에서 크롬 원격 데스크톱 사용하기](https://velog.io/@hayaseleu/%EB%A6%AC%EB%88%85%EC%8A%A4%EC%97%90%EC%84%9C-%ED%81%AC%EB%A1%AC-%EC%9B%90%EA%B2%A9-%EB%8D%B0%EC%8A%A4%ED%81%AC%ED%86%B1-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)  
          
---

⭐️ Keyword : Private repository를 git clone할때     
💥 문제 발생 :  
```
Cloning into 'librealsense-Docker'...
Username for 'https://github.com': Taeyoung96
Password for 'https://Taeyoung96@github.com': 
remote: Support for password authentication was removed on August 13, 2021. Please use a personal access token instead.
remote: Please see https://github.blog/2020-12-15-token-authentication-requirements-for-git-operations/ for more information.
fatal: Authentication failed for 'https://github.com/Taeyoung96/librealsense-Docker.git/'
```
❗️  해결 : Token을 만들고 Password에 토큰 번호를 복사   
📙 출처 : [[Github] git clone with personal access token 해결방법](https://chashtag.tistory.com/116)  

---

⭐️ Keyword : `nvidia-smi`가 안먹는다...    
💥 문제 발생 : `VNML: Driver/library version mismatch`라는 메시지가 보이면서 갑자기 nvidia-driver가 보이지 않는다.   
❗️  해결 : 블로그를 보면서 그대로 따라하면 됌, 안되면 드라이버 재설치도 하나의 방법인듯   
📙 출처 : [NVML: Driver/library version mismatch 해결](https://hwiyong.tistory.com/85)  
         [[에러 해결] Failed to initialize NVML: Driver/library version mismatch](https://soomiles.github.io/2021/01/13/%EC%97%90%EB%9F%AC-%ED%95%B4%EA%B2%B0-Failed-to-initialize-NVML-Driver-library-version-mismatch/)  
         
         
---

⭐️ Keyword : 우분투 18.04 외장디스크 마운트하기    
💥 문제 발생 : 하아... 무려 1TB 짜리 하드디스크가 인식이 안되서 못쓸뻔했다... 오랜만에 구글링다운 구글링을 해서 문제를 해결했다.  
            `wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.`  
❗️  해결 :  

우선 마운트 하려는 디스크의 종류를 먼저 알아야 한다. `sudo fdisk -l`  
나같은 경우는 FAT16 type 이였다.  
**이를 반드시 ext4 format으로 바꿔주자!**  
`fdisk /dev/sdb`에 들어가서 원래 있던 partion을 삭제한 후,  
다시 ext4 format으로 partion을 만들어 줘야 한다.  

마운트를 할 폴더를 만든다. ex) /data  
외장하드 규격을 맞춰주자. (이미 맞춰져 있으면 안해도 됌)  
`sudo mkfs.ext4 /dev/sdb2`  
마운트 진행  
`sudo mount -t ext4 /dev/sdb2 /data`  
`df-h`로 마운트가 진행됐는지 확인  
이제 자동마운트를 해줘야 한다.  
`sudo blkid`  
blkid를 통해 UUID 값을 알아낸다.  
자동 mount를 위해 fstab 설정한다.  
`sudo gedit /etc/fstab`을 눌러  
자신에게 맞는 UUID 값을 활용하여  
`UUID=2481-03B6	/data		ext4	user,owner,utf8,rw,umask=0	0	0`  
를 추가한다.  

⭐️ 중요 : FAT16 type으로 할 경우 파일이 4G가 넘어가면 복사가 되지 않는다!! 반드시 ext4 format으로 해야한다!

`sudo chmod 777 /data`로 권한까지 부여하면 끝!  

📙 출처 : [하드디스크 마운트 하기](https://curioso365.tistory.com/115)  
         [우분투 : 하드디스크(HDD) 자동 마운트하기](https://m.blog.naver.com/watney0813/221017927194)  
         [[ Ubuntu ] 우분투 외장하드 마운트](http://perdupper.blogspot.com/2017/09/ubuntu.html)  
         [우분투 fdisk, mount](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=asdf2017&logNo=221152581002)  
         [[마운트 에러 해결] mount: /home/pi/NAS/hdd2: wrong fs type, bad option, bad superblock on /dev/sdb, missing codepage or helper program, or other error.](https://moonfac.tistory.com/53)  
         [새 디스크 추가시 ext4 format으로 마운트하기](https://blog.soobinpark.com/132)  
         [Mount&Umount (마운트&언마운트)](https://lascrea.tistory.com/75)  
         
---

⭐️ Keyword : `sudo-apt-get update`를 했을 때 오류가 나는 경우   
💥 문제 발생 : 아래와 같은 오류 발생  
```
E: The repository 'http://ppa.launchpad.net/kirillshkrogalev/ffmpeg-next/ubuntu bionic Release' does not have a Release file
```
❗️  해결 : `sudo add-apt-repository --remove ppa:kirillshkrogalev/ffmpeg-next` 한 다음,  
          `sudo apt-get update`  
📙 출처 : [E: The repository 'http://ppa.launchpad.net/certbot/certbot/ubuntu focal Release' does not have a Release file](https://stackoverflow.com/questions/60249177/e-the-repository-http-ppa-launchpad-net-certbot-certbot-ubuntu-focal-release)  
          [What can I do if a repository/PPA does not have a Release file?](https://askubuntu.com/questions/866901/what-can-i-do-if-a-repository-ppa-does-not-have-a-release-file)  
          
 ---
 
⭐️ Keyword : `nvidia-smi`가 안나온다...   
💥 문제 발생  다음과 같은 오류 발생, 아마 강제 종료를 시키면 발생하는 듯.   
```
NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running
```
❗️  해결 : 역시 답은 재설치다ㅎㅎ     
📙 출처 : [couldn't communicate with the NVIDIA Driver 오류 현상](https://eda-ai-lab.tistory.com/572)  

---

⭐️ Keyword : evo package installation   
💥 문제 발생 : pip를 활용해서 설치는 잘 됐는데, 명령어가 안먹힌다.  
❗️  해결 : pip를 활용해서 설치된 패키지 경로와 터미널에서 보이는 파이썬 경로가 달라서 생기는 문제인듯. PATH를 추가해주면 된다.  
          `export PATH="$HOME/.local/bin:$PATH"` `.bashrc`파일에 추가  
📙 출처 : [Cannot find evo pkg](https://github.com/MichaelGrupp/evo/issues/217)  
         [pip installs packages successfully, but executables not found from command line](https://stackoverflow.com/questions/35898734/pip-installs-packages-successfully-but-executables-not-found-from-command-line/43368894#43368894)  
 
---

⭐️ Keyword : NVIDIA driver 재설치 오류     
💥 문제 발생 : `sudo sh NVIDIA-Linux-x86_64-440.64.run`를 했는데 아래와 같은 오류가 나옴.  
```
 ERROR: An NVIDIA kernel module 'nvidia-drm' appears to already be loaded in  
         your kernel.  This may be because it is in use (for example, by an X  
         server, a CUDA program, or the NVIDIA Persistence Daemon), but this   
         may also happen if your kernel was configured without support for     
         module unloading.  Please be sure to exit any programs that may be    
         using the GPU(s) before attempting to upgrade your driver.  If no     
         GPU-based programs are running, you know that your kernel supports    
         module unloading, and you still receive this message, then an error   
         may have occurred that has corrupted an NVIDIA kernel module's usage  
         count, for which the simplest remedy is to reboot your computer.  
```  

❗️  해결 : GPU process를 모두 제거하고 NVIDIA driver를 다시 설치하면 됌.    
📙 출처 : [[Solved] An NVIDIA kernel module 'nvidia-drm' appears to already be loaded in your kernel](https://clay-atlas.com/us/blog/2020/03/04/linux-english-note-how-to-disable-nvidia-drm/)  

---

⭐️ Keyword : NVIDIA docker GPG Public Key 교체   
💥 문제 발생 : NVIDIA docker image를 pull하고 `sudo-apt-get install`을 하는데 오류가 났다.  
```
  Error:6 http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64  InRelease                                       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A4B469963BF863CC
```
❗️  해결 : 친절한 블로그에 다 나와있음.    
📙 출처 : [[Docker] Tensorflow Container 빌드 시 에러 해결 (W: GPG error)](https://sseongju1.tistory.com/61)  
         [GPG error: http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](https://forums.developer.nvidia.com/t/gpg-error-http-developer-download-nvidia-com-compute-cuda-repos-ubuntu1804-x86-64/212904)
         
---
⭐️ Keyword : ceres-solver 사용, CMakeList.txt 사용법     
💥 문제 발생 : CMakeList.txt에서 `find_package(Ceres REQUIRED)`를 해줘서 빌드할 때 에러는 안나는데 막상 사용하니,  
             `undefined reference to ceres::Problem::Problem()`이라는 에러가 났다.  
❗️  해결 :  CMakeList.txt에서 직접 사용하는 디렉토리에 `target_link_libraries(${CERES_LIBRARIES})`도 같이 추가해줘야한다.  
📙 출처 : [undefined reference to `ceres::Solve(ceres::Solver::Options const&, ceres::Problem*,](https://blog.katastros.com/a?ID=01600-c13c27bf-93b7-417d-828e-67b1f373721f)  



