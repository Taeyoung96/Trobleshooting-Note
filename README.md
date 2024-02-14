# Trobleshooting-Note  

모든 문제 해결 방법을 블로그에 포스팅하면 좋지만,  
구글링을 통해 쉽게 나오는 방법들에 대해서는 굳이 그럴 필요가 없다고 생각한다.  
하지만 **나중에 비슷한 문제를 만났을 때, 조금이나마 시간을 단축하기 위해** Repository를 만들었다.  

우선 자유롭게 메모장형식으로 쓸 예정이다. 😆  

### 기본틀  

⭐️ Keyword   
💥 문제 발생  
❗️ 해결  
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

---

⭐️ Keyword : Git 첫번째 commit 취소, Add 취소   
💥 문제 발생 : Git을 사용해서 첫번째로 한 commit을 취소해주려면 일반적인 reset으로 적용되지 않는다.   
❗️  해결 : `git update-ref -d HEAD`를 하면 stage한 상태로 되돌려 놓는다. 그 다음, `git rm --cached -r -f .`를 하면 unstate 단계로 돌려놓는다.    
📙 출처 : [GIT : 첫번째 commit 삭제](https://virtualtech.tistory.com/365)  
         [git add로 추가한 내용을 취소하는 방법](https://www.lainyzine.com/ko/article/how-to-cancle-git-add/)

---

⭐️ Keyword : Ros Bag파일 자르기, ROS bag file split    
💥 문제 발생 : 기존에 가지고 있던 bag 파일 중에서 일정 시간만 bag 파일을 취득하고 싶을 때  
❗️  해결 : `rosbag filter [input bagfile] [output bagfile] "t.secs >= 1659249548 and t.secs <= 1659249597"` 여기서 시간은 ROS time이다.  
📙 출처 : [How to split a recorded rosbag file ?](https://answers.ros.org/question/99711/how-to-split-a-recorded-rosbag-file/)  

---

⭐️ Keyword : Ubuntu 먹통, Error:/dev/sda5 contains a file system with errors, check forced   
💥 문제 발생 : `Error:/dev/sda5 contains a file system with errors, check forced`이라는 글자가 뜨면서 화면이 안뜸..  
❗️  해결 : `fsck -f /dev/sda5`  
📙 출처 : 강제로 뭐 해주는 것 같은데... 그냥 [여기](https://commandstech.com/resolved-error-dev-sda5-contains-a-file-system-with-errors-check-forced-linux-error/)보고 따라하면 됨.    

---

⭐️ Keyword : 대용량 (2TB 이상) 디스크 마운트하기     
💥 문제 발생 : 기존의 mount 방법을 따라가면 2TB가 최대로 쓸 수 있는 용량이다.    
❗️  해결 : `parted`라는 명령어를 활용하자. 블로그를 따라가다보면 나옴.    
📙 출처 : [리눅스에 대용량 HDD 마운트 하기.(4TB이상)](https://blog.dalso.org/uncategorized/813)  
          [Ubuntu 4 테라 하드 인식](https://ufris.tistory.com/52)  
          [[CenOS7] 새로운 하드디스크 추가하기.](https://zero-gravity.tistory.com/297)  
          
---

⭐️ Keyword : IguanaTex install in window  
💥 문제 발생 : Powerpoint에서 Latex 사용하기!  
❗️  해결 : 블로그를 따라가다보면 잘 설치된다.    
📙 출처 : [IguanaTex 설치](https://velog.io/@jyong0719/IguanaTex-%EC%84%A4%EC%B9%98)   

--- 

⭐️ Keyword : Latex에서 `\argmin`이 인식이 되지 않을 때    
💥 문제 발생 : `Undefined control sequence. \argmin` 이라는 에러 문구가 떴음.     
❗️  해결 : 
```
\usepackage{amsmath}
\DeclareMathOperator*{\argmax}{arg\,max}
\DeclareMathOperator*{\argmin}{arg\,min}
```

위와 같은 command를 tex 파일에 추가하자.  

📙 출처 : [Command for argmin or argmax?](https://tex.stackexchange.com/questions/5223/command-for-argmin-or-argmax)    

---  

⭐️ Keyword : AnyDesk install    
💥 문제 발생 : 처음에 있어야할 패키지가 존재하지 않았다.  
```
The following packages have unmet dependencies:
 anydesk : Depends: libgtkglext1 but it is not installable
E: Unable to correct problems, you have held broken packages.
```
❗️ 해결  
```
sudo apt-get update -y
sudo apt-get install -y libgtkglext1
```
📙 출처 : [How To Install "libgtkglext1" Package on Ubuntu](https://zoomadmin.com/HowToInstall/UbuntuPackage/libgtkglext1)    

---  

⭐️ Keyword : Ubuntu 18.04 키보드에서 한글 사용하기     
💥 문제 발생 : 역시 오랜만에 하니 삽질을 좀 했다. `fcitx` 설치가 가장 무난한듯    
❗️ 해결 : 역시 잘 정리된 블로그가 많다.    
📙 출처 : [Ubuntu 18.04 에서 한글 키보드, 한영키 설정하기 _ NAMU](https://namuroom.tistory.com/entry/Ubuntu-1804-%EC%97%90%EC%84%9C-%ED%95%9C%EA%B8%80-%ED%82%A4%EB%B3%B4%EB%93%9C-%ED%95%9C%EC%98%81%ED%82%A4-%EC%84%A4%EC%A0%95%ED%95%98%EA%B8%B0-NAMU)  
  [[Ubuntu] fcitx 한글 키보드 입력 사용하기](https://m.blog.naver.com/opusk/220986268503)  
  [우분투 20.04 한글 입력 방법 (feat. fcitx)](https://kr-ddubbu.tistory.com/8)  
  
---

⭐️ Keyword : Docker install in ubuntu 18.04    
💥 문제 발생 : 오랜만에 해보는 Docker 설치!   

❗️ 해결 : Official 문서를 따라가면 어렵지 않게 설치할 수 있다. 우선 도커를 처음 설치하는 입장에서 작성 (GPU도 사용하지 않음)      
1. 필요한 패키지 업데이트 및 설치  
```
sudo apt-get update
```
```
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

2. Docker’s official GPG key 추가  
```
sudo mkdir -p /etc/apt/keyrings
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. repository 셋업  
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
4. Docker engine 설치  
```
sudo apt-get update
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin  
```

📙 출처 : [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)   

---  

⭐️ Keyword : Docker sudo 없이 사용하기  
💥 문제 발생 : 다음과 같은 에러 문구가 발생  
```
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/images/json": dial unix /var/run/docker.sock: connect: permission denied
```
❗️ 해결 : 블로그에서 권장하지는 않는다고 했지만, 난 이걸로 해결...  
```
sudo chown root:docker /var/run/docker.sock
```
```
sudo chmod 666 /var/run/docker.sock
```
📙 출처 : [[Docker] Docker permission denied error 해결](https://dongle94.github.io/docker/docker-permission-error/) 

---  

⭐️ Keyword : Matlab install in Ubuntu 18.04   
💥 문제 발생 : Window에서만 쓰던 Matlab이 ubuntu에서도 되다니!    
❗️ 해결 : 학교 계정이 있어야 한다. (라이센스 문제로)  
  우선 차근차근 [블로그](https://my-inote.tistory.com/96)를 따라가면 된다.  
  다만 나같은 경우는 license 충돌 문제가 일어남.  
  ```
  License Manager Error -9
  Your username does not match the username in the license file. 
  To run on this computer, you must run the Activation client to reactivate your license.
  Troubleshoot this issue by visiting: 
  https://www.mathworks.com/support/lme/R2019b/9
  Diagnostic Information:
  Feature: MATLAB 
  License path: /home/alex/.matlab/R2019b_licenses:/usr/local/MATLAB/R2019b/licenses/license.dat:/usr/local/MATLAB/R
  2019b/licenses/license_thinkpad-p73_40871338_R2019b.lic 
  Licensing error: -9,57.
  ```
  Matlab을 설치 받을 때 같이 받은 `activate_matlab.sh`를 실행하고 차근차근 license를 등록하고 `whoami`로 나온 계정 이름을 등록시킨다.  
  
📙 출처 : [License Manager Error -9 Your username does not match the username in the license file.](https://kr.mathworks.com/matlabcentral/answers/502799-license-manager-error-9-your-username-does-not-match-the-username-in-the-license-file)  
         [How do I find my user name in order to install or activate my license?](https://kr.mathworks.com/matlabcentral/answers/96800-how-do-i-find-my-user-name-in-order-to-install-or-activate-my-license)  

---  

⭐️ Keyword : Xsens IMU 사용   
💥 문제 발생 : maual대로 따라했는데 오류가 나서 참고한 포스팅을 정리하고자 한다.    
❗️ 해결 : 내가 올렸던 [Issue](https://github.com/xsens/xsens_mti_ros_node/issues/75),MT manager 사용은 [여기](https://www.jianshu.com/p/bca9cbfb31fb)를 참고  
         Xsens 공식 메뉴얼 사이트는 [여기](https://mtidocs.xsens.com/home)를 참고  
         **ROS driver를 사용하려면 MT manager를 들어가서 Device output setting에서 `Rate of Turn`을 꼭 켜줘야한다!**  
         
📙 출처 : [[IMU #1] Xsens IMU ROS 토픽 받기](https://blog.naver.com/PostView.naver?blogId=iphone7743&logNo=222300448218&parentCategoryNo=&categoryNo=86&viewDate=&isShowPopularPosts=true&from=search)  
  [Linking problem occurs when installing MT Software Suite #75](https://github.com/xsens/xsens_mti_ros_node/issues/75)  
  [Ubuntu 18.04 Xsens MT Manager](https://www.jianshu.com/p/bca9cbfb31fb)  
  [Xsens MTi Product Documentation](https://mtidocs.xsens.com/home)  

---  

⭐️ Keyword : Zed2i Camera-IMU extrinsic calibration 및 좌표계 절대 위치 구하기    
💥 문제 발생 : ROS tf를 활용해서 구하는데 헷갈려서 정리한다...  
❗️ 해결 : 우선 `zed2i.launch`를 하면 rviz 상에서 tf에 대한 정보를 볼 수 있다.  
  내가 publish하는 topic의 frame 이름을 잘 기억해놨다가, Rviz 상의 Fixed frame을 reference frame으로 두고,  
  tf상에서 target frame의 이름을 클릭하면 좌표계의 관계를 구할 수 있다.  
  
  `zed2i`의 경우, `zed2i_camera_center` : 실제 카메라 센서의 중심  
                 `imu_frame` : IMU 좌표계의 위치를 얻을 수 있었다.  
  
📙 출처 : [Zed docs -ROS - Data display with Rviz](https://www.stereolabs.com/docs/ros/rviz/)  
         [ROS wiki tf](http://wiki.ros.org/tf)  

---

⭐️ Keyword : SDK 설치를 진행했는데, ros-wrapper에서 인식이 안될때   
💥 문제 발생 : ZED camera의 SDK를 설치했는데, ros-wrapper를 `catkin_make`하니까 다음과 같은 오류가 뜬다.  
```
processing catkin package: 'zed_wrapper' -- ==> add_subdirectory(zed-ros-wrapper-master) CMake Warning at zed-ros-wrapper-master/CMakeLists.txt:22 (find_package): By not providing "FindZED.cmake" in CMAKE_MODULE_PATH this project has asked CMake to find a package configuration file provided by "ZED", but CMake did not find one.

Could not find a package configuration file provided by "ZED" (requested version 2.3) with any of the following names:

ZEDConfig.cmake
zed-config.cmake
Add the installation prefix of "ZED" to CMAKE_PREFIX_PATH or set "ZED_DIR" to a directory containing one of the above files. If "ZED" provides a separate development package or SDK, be sure it has been installed.

CMake Error at zed-ros-wrapper-master/CMakeLists.txt:17 (message):

ZED SDK not found, install it from: https://www.stereolabs.com/developers/

Call Stack (most recent call first): zed-ros-wrapper-master/CMakeLists.txt:23 (checkPackage)

-- Configuring incomplete, errors occurred! See also "/home/icrs1/catkin_ws/build/CMakeFiles/CMakeOutput.log". See also "/home/icrs1/catkin_ws/build/CMakeFiles/CMakeError.log". Makefile:318: recipe for target 'cmake_check_build_system' failed make: * [cmake_check_build_system] Error 1 Invoking "make cmake_check_build_system" failed
```
❗️ 해결 : SDK에 권한 부여!  
```
sudo chmod 777 -R /usr/local/zed
```  
그리고 다시 `catkin_make`를 해보자!  

📙 출처 : [How to install ZED SDK](https://answers.ros.org/question/293850/how-to-install-zed_sdk/)  

---  

⭐️ Keyword : Velodyne ros driver   
💥 문제 발생 : `[ERROR] [1554173288.904455221]: DriverNodelet::devicePoll - Failed to poll device.`이라는 무서운 에러가 뜬다.    
❗️ 해결 : [Github issue](https://github.com/ros-drivers/velodyne/issues/232)에서 봤을 때는, Bug 같기도 하고.. 우선 두 가지를 설정해주고 재부팅해줬다.  
```
sudo ufw disable
```  
그 다음 튜토리얼을 따라했는데.. `eth0`에서 계속 실패를 했다.
[Getting Started with the Velodyne VLP16](http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16)  
📙 출처 : [Getting Started with the Velodyne VLP16](http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16)  
         [Github issue #232](https://github.com/ros-drivers/velodyne/issues/232)

---  

⭐️ Keyword : shared library linking error   
💥 문제 발생 : fmt 라이브러리를 사용하려고 하는데, 빌드는 됐지만, linking error가 발생  
```
//usr/local/lib/libfmt.a(format.cc.o): relocation R_X86_64_PC32 against symbol `stderr@@GLIBC_2.2.5' can not be used when making a shared object; recompile with -fPIC
```
❗️ 해결 : `CMakeList.txt`에 맨 첫줄에 `SET(CMAKE_POSITION_INDEPENDENT_CODE TRUE)`를 추가하고 빌드함.    

📙 출처 : https://github.com/fmtlib/fmt/issues/548  
         https://github.com/fmtlib/fmt/issues/2456

---  

⭐️ Keyword : QT plugin 관련  
💥 문제 발생 : 아래와 같은 오류가 났다.
```
Cannot move to target thread (...)
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "/(...)site-packages/cv2/qt/plugins" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.
```
❗️ 해결  :  
```
sudo apt-get install '^libxcb.*-dev' libx11-xcb-dev libglu1-mesa-dev libxrender-dev libxi-dev libxkbcommon-dev libxkbcommon-x11-dev
```

📙 출처 : https://github.com/NVlabs/instant-ngp/discussions/300    


---

⭐️ Keyword : Dockerfile 명령어 Tip   
💥 문제 발생 : 항상 헷갈리는 Dockerfile 명령어 정리  
❗️ 해결 : 아래의 url을 참고하자.    
📙 출처 :  
- https://freedeveloper.tistory.com/186  
- https://www.daleseo.com/dockerfile/  

---  

⭐️ Keyword : 크롬 원격 데스크톱 화면 안보임.  
💥 문제 발생 : 하... 피말리는 1시간이였다. 원격 데스크톱을 설치하니, 화면이 멈추고 원격으로 들어갈 수 없었다.    
❗️ 해결  
1. grub recovery mode에 진입 후, 재빠르게 chrome-remote-desktop을 지운다.  
2. 모니터와 관련된 패키지들을 삭제 후 재설치 한다. (gnome, lightdm, xserver) 
3. 그리고 재부팅...

📙 출처 : [How to install xserver-xorg on Ubuntu](https://howtoinstall.co/en/xserver-xorg)  
         [How to remove and reinstall GNOME 3?](https://askubuntu.com/questions/67764/how-to-remove-and-reinstall-gnome-3)  
         [Installing Lightdm on Ubuntu](https://tecadmin-net.cdn.ampproject.org/v/s/tecadmin.net/installing-lightdm-on-ubuntu/?amp=&amp_gsa=1&amp_js_v=a9&usqp=mq331AQKKAFQArABIIACAw%3D%3D#amp_tf=%EC%B6%9C%EC%B2%98%3A%20%251%24s&aoh=16742071715106&referrer=https%3A%2F%2Fwww.google.com&ampshare=https%3A%2F%2Ftecadmin.net%2Finstalling-lightdm-on-ubuntu%2F)  
         [GRUB 기초 개념 및 사용방법](https://jstar0525.tistory.com/347)  

---  

⭐️ Keyword : c++ 변수 공유    
💥 문제 발생 : `A.cpp`에서 선언한 변수를 `B.h`에서 사용하고 싶을 때...!    
❗️ 해결  : `extern`이라는 keyword를 활용하자.  
`A.cpp`에서  
```cpp
double var;
var = 10;
```
`B.h`에서  
```h
extern double var;
```
변수로 활용한 이름이 같아야 한다!  

📙 출처 : ChatGPT에 아래와 같이 질문함.  
```
I want to fix my  c++ code.
In, `A.h` file,
ground_factor;

In, `B.cpp` file,
double ground_factor;

I want to use the value of ground_factor of B.cpp file to A.h for global variable, how could I do it?
```  

---  

⭐️ Keyword : Latex 수학 기호     
💥 문제 발생 : 수학기호의 symbol을 바꾸고 싶을 때    
❗️ 해결 : 아래 링크를 참고하자.    

<p align="center"><img src="https://user-images.githubusercontent.com/41863759/216896734-39766f8c-c380-4144-8b9b-7304677cd77e.png" width = "600" ></p>  

📙 출처 : [What are all the font styles I can use in math mode?](https://tex.stackexchange.com/questions/58098/what-are-all-the-font-styles-i-can-use-in-math-mode) 

---  

⭐️ Keyword : `Rosbag record` error. `Error writing: Error opening file`    
💥 문제 발생 : `Rosbag record` 명령어 오류    
❗️ 해결 : 도커 컨테이너랑 공유를 하고 있어서 그런지, 폴더에 대한 권한을 강제로 넣어줘야한다.  
```
cd ..
chmod 777 -R /folder
```
📙 출처 : [ROS bag](https://velog.io/@qaszx1004/ROS-bag)  
         [Error with rosbag record](https://answers.ros.org/question/38108/error-with-rosbag-record/)  

---  

⭐️ Keyword : Evo trajectory align failed     
💥 문제 발생 : 각각의 trajectory는 잘 만들어진 것 같은데, `-a` 옵션을 넣으면, trajectory가 잘려서 나올 때   
❗️ 해결 : `--verbose`로 몇 개의 pose가 align 되었는지 확인, `--t_max_diff 0.1`로 pose를 모두 담을 수 있도록 조절한다.    
📙 출처 : [some propblems of tum traj align](https://github.com/MichaelGrupp/evo/issues/505)  

---  

⭐️ Keyword : Docker overlay2 용량 정리    
💥 문제 발생 : `docker prune` 같은 명령어를 입력해도, 용량이 줄어들지 않을 때    
❗️ 해결 : 임시적인 방법이긴 하지만, overlay2에서 불필요한 폴더를 강제적으로 제거해주면 용량을 확보할 수 있다.  
우선 `/var/lib/docker/overlay2/`에 권한 부여,  
```
du -sh */diff/ | sort -k 1 -nr
```  
아니면, `sudo baobab`으로 용량이 가장 큰 친구들 제거.. 혹시 지금 사용하고 있는 컨테이너 및 이미지에 대한 Log일 수 있으니 주의해야한다.  
**이 방법의 사용을 권장하지는 않는다... 결국 이미지하고 컨테이너를 다 다시 만듦 ㅠㅠ**  
📙 출처 : [[Docker] 도커 볼륨 용량 초과 이슈](https://waytothem.com/blog/102/)  
         [Is it safe to clean docker/overlay2/](https://stackoverflow.com/questions/46672001/is-it-safe-to-clean-docker-overlay2)  

---  

⭐️ Keyword : evo tool tip   
💥 문제 발생  `evo_res`라는 명령어를 한번 사용해보자.  
❗️ 해결 : 우선 `evo_ape`의 결과를 저장해야 한다.  
```
evo_ape tum GT-trajectory.txt FAST-LIO2-GT-calib.txt -a --save_result result/test2.zip
```
그 다음 `evo_ape`라는 명령어 사용  
```
evo_res result/*.zip -p
```
📙 출처 : https://github.com/MichaelGrupp/evo/issues/9  
         https://github.com/MichaelGrupp/evo/issues/366  

---  

⭐️ Keyword : Zotero install in Ubuntu 18.04   
💥 문제 발생 : 한줄로 zotero 설치!  
❗️ 해결 : 
```
snap install zotero-snap
```
📙 출처 : [Complete Guide To Install Zotero On Ubuntu 18.04](https://www.ubuntubuzz.com/2018/06/complete-guide-to-install-zotero-on-ubuntu-1804.html)  

---  

⭐️ Keyword : Zotero + Notion plugin     
💥 문제 발생 : Zotero와 Notion을 한번에 활용해보자.   
❗️ 해결 : 튜토리얼 영상을 따라가다 보면 쉽게 설치할 수 있다.   
📙 출처 : [A technical guide to setting up Notero (Zotero + Notion plugin)](https://medium.com/@anna-everett/a-technical-guide-to-setting-up-notero-zotero-notion-plugin-d467d675039b)  
         [Sync Zotero to Notion to Level-Up Your Academic Research | AWESOME Notion Plug-In | Notion Tutorial](https://youtu.be/8IC8-mPbjCo)

---  

⭐️ Keyword : Roscore 문제   
💥 문제 발생 : roscrore를 안켰는데, 켜져있다고 한다!!   
❗️ 해결 : 강제로 켜져있던 roscore를 꺼주면 해결.    
- roscore/master 프로세스 확인  
```
ps aux | grep ros
```
roscore 종료  
```
kill -9 <PID>
```
📙 출처 : ChatGPT     

---  

⭐️ Keyword : cmake version change     
💥 문제 발생 : cmake version을 업그레이드 하려고 한다.    
❗️ 해결 : 중국 블로그를 차근차근 따라가면 된다.    
📙 출처 : [编译报错 CMake Error: The following variables are used in this project, but they are set to NOTFOUND.](https://blog.csdn.net/Will_Ye/article/details/123800851)  
        [cmake download](https://cmake.org/download/)

---  

⭐️ Keyword : NVIDIA driver install   
💥 문제 발생 : 아래와 같은 에러 문구를 발견했을 때 해결하는 법   
```
You appear to be running an X server; please exit X before installing. 
```
❗️ 해결  
1. 우선 `Ctrl` + `Alt` + `F1` key를 눌러서 GUI 사용을 하지 않는다.  
2. `sudo /sbin/init 3` 이라고 입력한다.  
3. `.sh` 파일을 이용해서 nvidia driver를 설치한다.  
4. `sudo /sbin/init 5`라고 입력한다.  

만약 무한 로그인에 빠졌을 경우, 당황하지 않고 컴퓨터를 재시작한다.  

📙 출처 : [ERROR: You appear to be running an X server; please exit X before installing](https://zerolism.tistory.com/28)    

---  

⭐️ Keyword : docker에서 python 명령어가 먹히지 않을 때     
💥 문제 발생 : `bash: python: command not found`  
❗️ 해결 : alias를 등록해주자.  
```
echo alias python='python' >> ~/.bashrc
```
```
source ~/.bashrc
```
📙 출처 : [-bash: python: command not found](https://zetawiki.com/wiki/-bash:_python:_command_not_found)   

---  

⭐️ Keyword : Velodyne VLP-16 setting    
💥 문제 발생 : 차근차근 Velodyne setting을 해보자.   
❗️ 해결  :  
ROS1을 돌리기 위해서 IP setting을 해놓으면, docker를 활용한 ROS2에서도 손쉽게 해낼 수 있다.  

우선 IP를 맞추는 것이 상당히 중요하다.  
메뉴에 있는 `network`에 가서 새로운 IP address를 부여하자.  
![Screenshot from 2023-07-26 16-36-18](https://github.com/Taeyoung96/Trobleshooting-Note/assets/41863759/0016f32b-e57f-4a3d-9c6f-77073ed55cb9)  

나는 위와 같이 부여했다.  
`192.168.1.201`만 아니면 괜찮은 것 같음.  
그리고 Velodyne을 연결하고 `ifconfig`로 나오는 이름으로 IP 주소를 할당한다.  
**예시에서는 `eth0`이라고 나와있지만 본인의 가지고 있는 이름이 각각 다를 수 있기 때문에 한번 확인하고 자신만의 이름으로 진행하자!**  
```
sudo ifconfig eth0 192.168.3.100
```
```
sudo route add 192.168.XX.YY eth0
```

여기서 살짝 헤맸는데, `XX.YY`는 velodyne 아래에 MAC주소 뒤에 4자리를 의미한다.  
**하지만 적혀있는 주소는 HEX이고 우리는 이를 십진수로 변환해서 적어야 한다.**  
예를 들어, `XX.YY`가 `36.50`이라고 적혀있으면 우리가 `add`를 해줘야 하는 주소는 아래와 같다.  
```
sudo route add 192.168.54.80 eth0
```
그 다음 `192.168.1.201`에 들어가서 port 번호를 확인하자.  
추후 port 번호를 launch 파일에서 이용한다.  

그 다음 ROS 1 기준으로  
```
sudo apt-get install ros-VERSION-velodyne
```
```
cd ~/catkin_ws/src/ && git clone https://github.com/ros-drivers/velodyne.git
```
```
cd ~/catkin_ws/ && catkin_make
```

그 후, launch를 진행하자!  
```
roslaunch velodyne_pointcloud VLP16_points.launch
```

velodyne points의 경우 frame ID가 `velodyne`이므로 Rviz에서 볼 때 fixed frame을 바꿔야 한다.  


📙 출처 : [Getting Started with the Velodyne VLP16](http://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16)  
         [Velodyne Lidar VLP-16 Setup](https://blog.naver.com/jackyoung96/221896551468)  

---  

⭐️ Keyword : docker에서 python 명령어가 작동하지 않을 때     
💥 문제 발생 : `Bash python command not found` 라는 출력이 docker container 내부에서 나옴.   
❗️ 해결 : 
```
# bashrc (python3나 원하는 python 버전)
alias python=python3

# 터미널
source ~/.bashrc
```
📙 출처  : [[ubuntu] python을 찾을 수 없다고 할때](https://yay-z.com/94)   

---  

⭐️ Keyword : Docker에서 evo 설치  
💥 문제 발생 : Container 안에서 python, pip이 설치가 되어 있지 않다고 할 때, 따라하면 된다.    
❗️ 해결 
1. `Bash python command not found` 해결
```
alias python=python3
source ~/.bashrc
```
  
2. `Bash pip command not found` 해결
```
sudo apt-get install python3-pip
```

3. evo 설치 및 numpy version 오류 해결
```
pip install evo
pip install numpy==1.21
```


📙 출처 : [bash: pip: command not found](https://stackoverflow.com/questions/9780717/bash-pip-command-not-found)  
         [AttributeError: module 'numpy' has no attribute 'typeDict'](https://stackoverflow.com/questions/74852225/attributeerror-module-numpy-has-no-attribute-typedict)

---  

⭐️ Keyword : apt-get update가 제대로 되지 않을 때     
💥 문제 발생  `sudo apt-get update`를 수행하면 아래와 같은 Warning 메시지가 뜬다.  
```
W: Failed to fetch http://kr.ftp.daumkakao.com/ubuntu/dists/focal/InRelease  Could not resolve 'kr.ftp.daumkakao.com'
W: Failed to fetch http://kr.ftp.daumkakao.com/ubuntu/dists/focal-updates/InRelease  Could not resolve 'kr.ftp.daumkakao.com'
W: Failed to fetch http://kr.ftp.daumkakao.com/ubuntu/dists/focal-backports/InRelease  Could not resolve 'kr.ftp.daumkakao.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```
❗️ 해결  
```
sudo gedit /etc/apt/sources.list
```
Replace
```
http://kr.ftp.daumkakao.com
```
to
```
http://mirror.kakao.com
```

📙 출처: (친절한) ChatGPT 

---  

⭐️ Keyword : Wifi와 LAN port 우선 순위 정하기   
💥 문제 발생 : Wifi로 인터넷을 잡아서 사용하고 있고, Velodyne을 사용하기 위해서 LAN을 추가했는데 갑자기 인터넷이 되지 않았다!  
❗️ 해결 : route에서 우선순위를 할당할 수 있어, wifi를 더 우선순위가 높도록 설정하면 된다. 차근차근 블로그를 따라가다보면 쉽게 할 수 있다.      
📙 출처 : [[Linux] 라우팅 테이블 설정(route, Metric 우선순위)](https://changun516.tistory.com/141)  

---  

⭐️ Keyword : Ubuntu CPU 사용량, 메모리 사용량 확인   
💥 문제 발생 : 터미널을 활용해서 알고리즘의 Max CPU 사용량과 Max 메모리 사용량을 알고 싶을 때  
❗️ 해결 : `sysstat` 패키지를 활용하자.  
- `sysstat` 패키지 설치:
```
sudo apt-get update && sudo apt-get install sysstat
```
다음 단계를 따라 `sysstat`의 데이터 수집을 활성화하고 `sar` 명령어를 사용할 수 있도록 설정해보겠습니다:

- sysstat 설정 파일 열기:
   ```bash
   sudo nano /etc/default/sysstat
   ```

- 데이터 수집 활성화:
   파일 내에서 `ENABLED` 값을 `true`로 변경합니다.
   ```
   ENABLED="true"
   ```

-  설정 파일 저장 및 종료:
   `nano` 에디터에서 `Ctrl + X`를 누르고, `Y`를 눌러 변경 사항을 저장한 후 `Enter`를 눌러 종료합니다.

-  sysstat 서비스 재시작:
   ```bash
   sudo service sysstat restart
   ```

-  데이터 수집 대기:
   `sysstat`이 데이터를 수집하기 시작하면, 일정 시간이 지난 후에 `sar` 명령어를 사용하여 데이터를 조회할 수 있습니다. 데이터 수집 간격은 기본적으로 10분입니다. 따라서 최소 10분 후에 다시 `sar -u 300` 명령어를 실행해보세요.

이렇게 설정하면 `sar` 명령어를 사용하여 시스템 활동을 조회할 수 있게 됩니다.

📙 출처 : ChatGPT  

---  

⭐️ Keyword : Ubuntu 22.04에서 docker install   
💥 문제 발생 : 기본적으로 제공하던 `apt-get`에 연결된 docker 패키지가 없어서 다른 방법으로 설치를 해줘야 한다.    
❗️ 해결 : 
```
curl -fsSL https://get.docker.com -o get-docker.sh
```

```
 sudo sh get-docker.sh
```
📙 출처 : [Docker(도커) Ubuntu 22.04 LTS(우분투 22.04) 설치](https://bundw.tistory.com/98)  

---  
