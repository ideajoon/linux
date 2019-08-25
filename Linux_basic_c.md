
# Linux basic

## 1. 디렉토리와 파일

ls<br/>
현재 디렉토리의 파일 목록을 출력하는 명령어. 'ls -l'은 자세히 보기

ls -l<br/>
현재 디렉토리의 파일 목록 자세히 보기

pwd<br/>
현재 위치하고 있는 디렉토리를 알려주는 명령어

mkdir<br/>
mkdir 새로 생성할 디렉토리명

cd<br/>
cd 이동할 디렉토리의 경로명

### ※ 상대경로와 절대경로

상대경로<br/>
현재 디렉토리의 위치를 기준으로 다른 디렉토리의 위치를 표현하는 것으로 ..은 부모 디렉토리를 의미합니다.
- 'cd ..'<br/>
현재 디렉토리의 부모 디렉토리로 이동하는 명령이 됩니다.<br/>
참고로 현재 디렉토리는 '.' 입니다. 

절대경로<br/>
최상위 디렉토리를 기준으로 경로를 표현하는 것을 의미합니다. 최상위 디렉토리는 루트(root) 디렉토리라고 하고 '/' 입니다.
- 'cd /'<br/>
최상위 디렉토리로 이동한다는 뜻입니다.<br/>
'cd /home/egoing'은 현재 디렉토리가 무엇이건 언제나 '/home/egoing'을 의미하는데 이런 식의 경로 표현을 절대경로라고 합니다. 

rm<br/>
삭제하는 명령어
rm 파일명
rm -r 디렉토리명

--help<br/>
명령어 뒤에 --help를 붙이면 명령의 사용설명서가 출력됩니다.<br/>
- ls --help
- rm --help
- mkdir --help
- pwd --help

man<br/>
help는 그 화면에서 보여주고, man의 경우에는 전용 페이지로 이동해서 상세한 메뉴얼을 보여준다. help보다 더 상세하다.(빠져 나올때는 q를 누른다)
- man ls
- man rm
- man mkdir
- man pwd

## 2. 빈도수가 많은 명령어

![](https://www.drbunsen.org/static/images/posts/cli-pl3-small.png)

- 66 ls
- 61 cd
- 60 git
- 35 tail
- 33 php
- 31 ssh
- 27 mysql.server
- 22 vim
- 18 mysql
- 14 screen

## 3. sudo (super user do)

컴퓨터가 비싸던 시절 하나의 컴퓨터로 여러 사람이 나눠써야 했다. 때문에 리눅스에는 super user 권한이 생겨났음(lock the administration)

sudo를 붙이고 명렬어를 쓰면 임시로 root에 슈퍼유저의 권한으로 설치/삭제를 진행할 수 있다.

## 4. 파일편집 (nano)

파일에 정보를 추가하고 편집하는 방법으로서 nano 에디터를 사용하는 방법

- 설치방법 : sudo apt-get install nano

대표적으로 nano와 vi 에디터가 있다. 
- nano : 입문자 사용, 좀더 편리함
- vi : 중,고급자 사용, 좀 어려움

nano라고 치고 들어가면 에디터에 들어 갈수 있다. 그리고 아래 명령어들이 있다. 예를들어 ^O 의 의미는 ctrl + O 이다.

복사 및 붙여넣기 기능<br/>
cut text와 uncut text를 활용하여 해야한다.

저장하기 기능<br/>
write out 기능을 통하여 저장해야 한다.

### ※ vi 단축기 모음

![](https://t1.daumcdn.net/cfile/tistory/99515F505AA25FDC31)

## 5. 패키지 매니저 (package manager)

운영체제에 기본적으로 설치되어 있지 않은 프로그램을 쉽게 설치할 수 있는 방법이 패키지 매니저를 이용하는 것입니다. 리눅스 배포판에 따라서 패키지 매니저가 조금씩 다릅니다만 사용법은 대체로 비슷합니다. 

※ 작업관리자 프로그램 htop 패키지로 찾기/설치/업그레이드/삭제 예제

- sudo apt-get update<br/>
apt 패키지 목록 업데이트

- sudo apt-cashe search htop<br/>
htop로 시작하는 모든 프로그램을 찾아 주는 명령어

- sudo apt-get htop<br/>
작업관리자 프로그램 htop 설치<br/>
※ sudo htop으로 htop에 들어간다.

- sudo apt-get upgrade htop<br/>
htop 최신버전으로 업그레이드

- sudo apt-get remove htop<br/>
htop 삭제하기

## 6. 다운로드 방법 (wget, git)

명령어 기반의 시스템에서 파일을 다운로드 하는 방법

### wget

- wget + url<br/>
wget이란 프로그램을 이용하여 파일을 다운로드 한다.

- wget --help<br/>
패키지의 매뉴얼을 보고 사용법을 익힌다.

- wget -O + 저장파일명지정 + url<br/>
파일을 저장할때 저장되는 파일명을 지정해 주는 방법

### git

버전관리 시스템에 속하는 프로그램이다.

github에 있는 소스 코드를 다운로드 하는 방법을 알아보자.

- git clone + github url + react_src<br/>
github url에 있는 소스코드를 복제(clone)하고 디렉토리(react_src)에 다운로드 저장된다. react_src 디렉토리는 자동으로 생성된다.

## 7. 왜 CLI인가? (Command Line Interface)

왜 배우기 어려운 명령어(CLI)를 사용하는 것일까요? 여기서는 명령어를 사용하는 이유를 살펴봅니다. 

GUI vs GLI 

GLI(명령어) 방식이 에너지를 적게(메모리 적게) 사용한다. 하지만 GUI는 그래피컬하기 때문에 에너지가 많이 들어도 사용자가 사용하기 쉽다.
mkdir why;cd why
위에서 처럼 ';'를 사용하여 한줄에 두개의 명령어들을 순차적으로 사용할 수 있다. 즉 1000개도 사용가능 하다.

### ※ 파이프라인 ( " | " )

하나의 프로그램의 결과를 다른 프로그램의 입력으로 준다. 그리고 하나의 프로세스의 결과를 다른 프로세스의 입력으로 준다.

- nano test.txt<br/>
현 디렉토리에 test.txt파일을 만들고 nano 프로그램으로 파일을 연다. 웹 페이지에서 text 정보를 복사하여 nano에서 붙여넣기 하면 해당 정보가 test.txt파일에 저장된다.

- grep + 찾고 싶은 문자열 + 파일명<br>
찾고 싶은 문자열을 찾게 해주는 grep 명령어

- ls --help | grep + 찾고 싶은 문자열<br/>
grep을 이용하게 되고 찾고싶은 문자열이 있는 정보(ls 매뉴얼)만 보여지게 한다.<br/>
파이프라인(|)은 프로그램과 프로그램을 연결시켜 준다.<br/>
즉, 파이프라인은 'ls --help'라는 프로그램의 결과를 'grep'이라는 프로그램의 입력으로 사용하게 해준다.

- ls --help | grep + 찾고 싶은 문자열 | grep + 찾고 싶은 문자열<br/>
파이프라인(|)을 사용하면 grep을 통해 찾고 싶은 문자열을 여러개 찾을 수 있다.

## 8. IO Redirection (Input/Output 방향을 바꾼다)

![](http://slideplayer.com/slide/5126304/16/images/7/Review%3A+UNIX+Programs+Means+of+input%3A+Means+of+output%3A.jpg)

### 1) output

- ls -l > result.txt<br/>
result.txt파일 안에 ls -l의 출력결과를 저장한다.(덮어쓰기)

'>'의 redirection 기호를 사용하면 파일의 출력방향을 바꿀 수 있다.

참조 : http://slideplayer.com/slide/5126304

- rm rename2.txt > result.txt<br/>
만약 rm rename2.txt가 에러를 출력했을 경우, '>'기호 앞에는 '1'(standard out 의미)생략되어 있기 때문에 standard error를 result.txt에 저장하지 못한다.<br/>
rm rename2.txt 1> result.txt

위의 결과를 해결하기 위해서는 '>'기호 앞에 '1' 대신 '2'(standard in 의미)를 넣어준다.<br/>
- rm rename2.txt 2> error.log

- cat error.log<br/>
rm rename2.txt의 에러 출력을 확인할 수 있다.

- rm rename2.txt 1> result.txt 2> error.log<br/>
만약 rm rename2.txt의 결과의 출력값(standard out)이 있다면 그 결과는 result.txt에 저장되게 되고, 만약 rm rename2.txt의 결과가 에러(standard error)를 포함하고 있다면 그 에러결과는 error.log에 저장되게 된다. 

### 2) input

- cat<br/>
cat 명령을 하고 enter를 치면 키보드 input값을 받고 그 값을 바로 출력해줌

- cat hello.txt<br/>
hello.txt안의 정보를 출력해준다.<br/>
cat이라는 프로그램의 인자(command line arguments)로 전달되었다는 의미

- cat < hello.txt<br/>
hello.txt 파일안의 정보를 입력으로 받는다라는 의미<br/>
hello.txt 파일안의 정보가 standard input으로 cat에 입력되었다는 의미

- head linux.txt<br/>
linux.txt파일안의 정보를 기본 10줄을 출력해준다.<br/>
head라는 프로그램의 인자(command line arguments)로 전달되었다는 의미

- head -n1 linux.txt<br/>
linux.txt파일안의 정보를 1줄만 출력해준다.

- head -n1 < linux.txt<br/>
linux.txt파일안의 정보가 standard input으로 head에 입력되었다는 의미

- head -n1 < linux.txt > one.txt<br/>
linux.txt 파일안에 들어 있는 1줄 정보가 one.txt에 저장된다.

### 3) 더 나아가기 ('>>', '<<')

- ls -l >> result.txt<br/>
'>>'기호는 result.txt파일 안에 ls -l의 출력결과를 append로 저장한다.<br/>
'>'기호는 덮어쓰기한다.
$ mail joon2332@gmail.com <<haha #haha대신 다른 문자 사용가능
> hello #입력1
> hi #입력2
> wow #입력3
> haha #input을 끝낼때
'<<' 기호를 사용하여 입력값을 여러개 사용할 수 있다.<br/>
입력된 정보들은 위의 이메일로 전달된다.

- ls -al > /dev/null<br/>
화면에도 출력하지 않고 파일에도 저장되지 않음<br/>
/dev/null은 유닉스의 휴지통과 같은 기능

## 9. 쉘과 커널

사용자가 명령을 입력하면 그 명령을 컴퓨터가 이해할 수 있도록 하는 프로그램이 쉘(shell)입니다. 명령을 해석하는 쉘과 실제로 일을 하는 커널의 관계를 알아보자.

### 1) shell vs kernel

![](https://t1.daumcdn.net/cfile/tistory/27552535590AB2BB0F)

kernel<br/>
하드웨어를 직접적으로 제어하는 역할

shell<br/>
사용자가 입력한 명령어가 shell에게 입력된다. 그리고 kernel이 이해할 수 있도록 처리하고 그 결과를 kernel에게 보낸다.

### 2) bash vs zsh

bash보다 zsh가 좀더 사용자 편리하게 되어 있다. 하지만 bash가 더 범용적이고 거의 모든 리눅스 환경에서 적용가능하다.

sudo apt-get install zsh : zsh 설치

- ech $0<br/>
지금 사용하는 shell종류 출력 (bash or zsh)

일반적으로 bash가 설치됨

- cd 띄우고 + tab 두번<br/>
bash에서는 현재 디렉토리에 저장된 숨겨진 디렉토리까지 다 보여준다.<br/>
여기서 숨겨진 디렉토리는 앞에 '.'이 붙여져 있다. 예) .config/

![](https://t1.daumcdn.net/cfile/tistory/2760CC35590AB2BB2E)

위 그림은 같은 컴퓨터에 서로 다른 사용자들이 서로 다른 shell을 사용해서 컴퓨터에 접근하고 있다.

![](https://docstore.mik.ua/orelly/unix3/upt/figs/upt3_0101.gif)

## 10. 쉘 스크립트 (shell script)

명령을 실행시키는 작업을 한번에 실행할 수 있는 방법을 알아봅니다. 

### 1) Shell script 소개

또 하나의 프로그램 언어와 같다.<br/>
shell 명령어들이 실행되어야 하는 순서, 실행되어야 하는 방법을 각본을 만들어 저장해 놓은 파일이 shell script 이다.
mkdir script
cd script/
touch a.log b.log c.log # 3개의 빈 파일을 생성한다.
ls -l

mkdir bak
cp *.log bak #확장자가 log인 모든 파일을 bak에 저장하겠다.
ls -l bak

mkdir bak # bak디렉토리가 이미 존재하기 때문에 에러가 발생함.
mkdir bak 실행시 bak 디렉토리가 없으면 그대로 생성하고 만약 있다면 cp *.log bak가 실행되게 shell script 작성하면 된다. 

### 2) Shell Script 작성 예제
eco $0 #지금 사용하고 있는 shell type 확인
-bash #출력
bash는 'ls /bin' 폴더에 저장되어 있다.
nano backup # nano로 backup의 이름으로 프로그램 만들기
nano에서 프로그램 작성
#!/bin/bash                  

if ! [ -d bak ]; then
        mkdir bak
fi
cp *.log bak
- #!/bin/bash<br/>
운영체제는 아래 적혀있는 프로그램이 /bin/의 경로에 있는 bash라는 프로그램을 통해서 해석되어야 한다는 의미

- [ -d bak ]<br/>
현재 디렉토리에 bak라는 디렉토리가 존재하는가? 의미

- if ! [ -d bak ]; then<br/>
현재 디렉토리에 bak라는 디렉토리가 존재하지 않는 다면 의미

- fi<br/>
if 조건문이 종료되었다는 명령어 (if의 거꾸로)

- cp *.log bak<br/>
fi 아래에 있기 때문에 bak디렉토리가 있는 경우 실행되게 된다. 즉, log확장자로 끝나는 모든 파일을 bak 디렉토리에 저장한다.

nano에서 나가서 backup 파일이 생성되었는지 확인하고 실행해본다.
$ ./backup #backup파일을 실행시키는 명령어
-bash: ./backup: Permission denied

$ chmod +x backup #백업 파일의 권한을 가지게 해주는 명령어
+x는 x가 실행가능한 의미를 가지기 때문에 추가해주기 위한 옵션이다. 

## 11. 디렉토리의 구조

unix 계열은 디렉토리의 용도에 따라서 이름이 정해져있습니다. 여기서는 디렉토리의 구조를 알아보겠습니다. 

참조 : https://www.thegeekstuff.com/2010/09/linux-file-system-structure/

![](https://static.thegeekstuff.com/wp-content/uploads/2010/11/filesystem-structure.png)

- /<br/>
최상위 디렉토리

- /bin<br/>
바이너리(이진)의 줄임말, 실행가능한 실행가능한 프로그램을 바이너리라고 부른다. 사용자들이 사용하는 명령어들이 위치하고 있다.

- /sbin<br/>
시스템 바이너리로 시스템 관리자, 컴퓨터 끄기, 재부팅등의 root사용자가 사용하는 프로그램들이 있는 디렉토리

- /etc<br/>
프로그램의 설정, 어떠한 프로그램의 동작 방법을 바꾸고 싶을 때 설정에 들어가야 하는데 이러한 파일들이 있는 디렉토리 

- /var<br/>
내용이 고정되어 있지 않고 바뀔 수 있는 특성을 가진 파일들이 있는 디렉토리. 예) log 파일, tmp 파일

- /home<br/>
사용자(ideajoon)들의 디렉토리
$ cd /home/ideajoon<br/> #사용자 디렉토리로 바로 이동 명령어
$ cd ~ #사용자 디렉토리로 바로 이동 명령어
- /opt<br/>
optional add-on applications의 약자로 새로 설치하는 프로그램들을 설치해줘도 되는 디렉토리

- /usr<br/>
/bin과 /usr/bin은 서로 다른 디렉토리이다. 사용자가 설치하는 프로그램들은 usr/bin/에 설치되고 unix, linux 제공 프로그램은 /bin에 설치됨. 

## 12. 프로세스 (process)

프로세스는 실행되고 있는 프로그램을 의미합니다.

### 1) 컴퓨터의 구조

- Storage : SSD, HDD
- Memory : RAM
- Processor : CPU

storage에 저장된 프로그램을 읽어서 memory에 적재 후, memory 적재된 내용을 processor에서 처리한다. 그 이유는 storage는 속도가 매우 느리고 processor은 처리속도가 매우 빠르기 때문에 속도가 빠른 memory를 사용한다.ㅏ

### 2) 프로세스 모니터링 (ps, top, htop)

ps
$ ps # 프로세스 확인
$ ps aux # 모든 프로세스 확인
$ ps aux | grep apache # apache문자가 있는 문장만 출력
$ sudo kill + 프로세스 아이디 # 해당 프로그램을 강제로 종료하는 명령어
top
$ sudo top #작업관리자 top프로그램 실행
htop
$ sudo htop #작업관리자 htop프로그램 실행 (top보다 그래피컬함)
htop에서 cpu 등의 컬럼을 더블클릭하면 그 기준으로 정렬해준다.

- TIME+ : 해당 프로그램이 실행 누적 시간
- Command : 해당 프로그램이 어떤 명령으로 실행되어졌는지 보여줌
- MEM% : 해당 프로그램의 물리적인 메모리 사용량(%)
- RES : 실제적인 메모리의 사용량

- Load average : 1분간 cpu 부하평균, 5분간 cpu 부하평균, 15분간 cpu 부하평균

## 13. 파일을 찾는 법

### 1) locate와 find
locate *.log #log 확장자의 모든 파일을 찾아준다.
locate는 컴퓨터에 저장되어 있는 모든 파일을 하나하나 찾는 것이 아니라 전용 DB(mlocate)를 이용하여 찾아서 빠르다. sudo updatedb 명령어를 통해서 DB 정보를 강제로 업데이트 할 수 있으나 자동으로 주기적(1회/1일)으로 업데이트 되게 되어있다. 때문에 미리 정리정돈 되어 있기 때문에 빠르다.
$ find / #root 디렉토리 부터 찾겠다.
$ find . #현재 디렉토리 부터 하위 디렉토리순으로 찾겠다.
$ find ~ #사용자의 HOME 디렉토리에 있는 파일을 찾겠다.$ sudo find / -name *.log
위의 명령어는 root 디렉토리 부터 log확장자를 가진 모든 파일을 찾는다.
$ find ~ -name *.log
위의 명령어는 사용자의 home 디렉토리에 있는 모든 log확장자 파일을 찾는다. 사용자의 home 디렉토리에서 찾기 때문에 권한문제가 없어서 sudo를 빼도 된다.
$ find . -type f -name tecmint.php
- -type f : 확장자를 지정할 수 있다. f = files

위의 명령어는 현재의 디렉토리부터 하위디렉토리 순서로 찾되, tecmint.php라는 파일을 찾는다. 여기서 중요한 것은 '-type f'를 사용하여 tecmint.php라는 파일이 아닌 디렉토리가 있더라도 디렉토리는 제외하고 파일만을 찾게 해준다.
$ find . -type f -name "tocmint.txt" -exec rm -f {} \;
- find . : 현재 디렉토리 부터 하위 디렉토리 순으로 찾는다.
- -type f : 찾고자하는 format을 정할 수 있다. 여기서 f는 files이다.
- -exec : 실행시킨다.
- rm : 삭제한다.
- -f : 묻고 따지지도 않고 행한다.
- {} : 명령을 통해서 검색한 파일의 이름이 {}사이에 위치한다.

### 2) whereis 와 $PATH
$ whereis ls #ls 프로그램 파일과 매뉴얼의 경로를 찾을 때 사용 명령어$ echo $PATH # $path라는 변수에에 담겨 있는 값 출력 
즉, whereis는 $PATH에 담겨있는 경로를 순서대로 찾아서 해당 정보가 발견되면 원하는 파일이 있는 경로를 출력한다. path 담겨있는 경로를 바꿀수 있다. 원하는 경로를 넣어서 해당 디렉토리에서 찾게끔 넣어준다.

## 14. 백그라운드 실행 

백그라운드 작업을 하는 방법

- Ctrl + z<br/>
실행중인 프로그램을 백그라운드로 보내는 단축키. 이 기능을 실행하면 명령어가 일시 정지 됩니다. 

- &가 명령어 뒤에 붙으면 명령어가 실행될 때 백그라운드로 실행됩니다.<br/> 
    ex) ls -alR / > result.txt 2> error.log & : 

- jobs : 백그라운드 작업들의 목록을 보여줍니다. 
$ nano
위 명령으로 nano프로그램을 열고 파일을 작성하고 ctrl + z를 누르면 nano프로그램을 나가지 않고 nano프로그램을 백그라운드로 보냄
$ fg #forward ground의 약자로 백그라운드에 있던 nano프로그램이 fg로 올라온다.$ fg %2 #jobs의 목록에 있는 순서 2번째의 백그라운드를 fg로 불러온다.$ jobs #현재 백그라운드로 운영되고 잇는 목록을 보여줌$ kill %3 #jobs의 목록에 있는 순서 3번째의 백그라운드를 강제 종료한다.$ kill -9 %3 #'-9'를 추가하여 좀더 강력한 강제 명령을 한다.$ ls -al -R / > result.txt 2> error.log & #프로그램 실행시 바로 백그라운드로 보냄
- -R /<br/>
최상위 디렉토리(/)에서 모든 디렉토리, 파일을 불러오는 옵션

- &<br/>
&가 명령어 뒤에 붙으면 명령어가 실행될 때 백그라운드로 실행됩니다.

'ls -al -R /'의 결과를 result.txt에 저장되고 에러 발생시 에러를 error.log에 저장.

## 15. 항상 실행 (daemon, service)

어떤 프로그램을 항상 실행되도록 하는 방법

### 1) 데몬의 개념

데몬에 해당되는 프로그램들은 항상 켜져있고 실행되고 있다. 예) web server

### 2) service와 자동실행
$ sudo apt-get install apache2 # 웹서버 아파치 설치
웹서버 apache는 /etc/init.d/ 에 설치되어 있다.

init.d라는 디렉토리에 데몬 프로그램들이 설치되어 있다.

#### (1) 데몬 프로그램을 start / stop 명령어
$ sudo service apache2 start # 데몬 프로그램인 아파치 켜기위한 명령어$ sudo service apache2 stop # 데몬 프로그램인 아파치를 끌때 명령어
#### (2) 컴퓨터 부팅시 데몬 프로그램을 자동으로 start 하기
$ cd /etc/
$ cd cd r
$ cd cd rc3.d/ #리눅스를 CLI로 구동할 때는 rc3.d/ 디렉토리를 연다.
$ ls -l
즉, CLI는 rc3.d/ 디렉토리에 링크(바로가기 같은)로 특정 데몬 프로그램을 만들어 높으면 컴퓨터 부팅시 자동실행 된다.

만약에 리눅스를 GUI로 구동할 때는 rc5.d/ 디렉토리에 해당 데몬 프로그램을 링크를 걸어 놓는다.

## 16. 정기적으로 실행 (cron)

cron을 통해서 정기적으로 명령을 실행하는 방법
$ crontab -e #-e옵션은 하고자 하는 일을 저장할 수 있는 에디터가 열린다.
crontab 파일이 원하는 에디터(nano 등)으로 열리고 크론파일안에 하고자 하는 일을 저장하면 정기적으로 프로그램이 실행된다.
# 실행방법

# m h dom(day of month) mon(몇월) dow(요일) command

*/1 : 1분에 한번 실행
*/10 : 10분에 한번 실행
10 4 : 4시 10분에 실행
10 4 24 5 : 5월 24일 4시 10분에 실행
1/* * * * * : 모든 요일 모든월 모든일 모든 시간에 1분에 한번씩 실행 
![](https://i.stack.imgur.com/SIdCf.gif)
$ date # 현재의 시간을 출력
$ date > date.log # 덮어쓰기 형식으로 저장
$ cat date.log
$ date >> date.log # append 형식으로 저장
$ cat date.log
$ fg # 실행하던 crontab 화면으로 이동#crontab 화면에서

1/* * * * * date >> date.log$ tail -f date.log
- tail : date.log 파일의 끝줄을 출력
- -f : date.log 파일이 변경시(append 될때) 마다 출력해주는 옵션
#crontab 화면에서

1/* * * * * date >> date.log 2>&
- 2>&<br/>
표준에러를 표준축력으로 redirection 시켜준다. 즉, 에러가 발생하면 그 에러를 date.log에 함께 저장시켜준다. 

## 17. 쉘을 시작할 때 실행

쉘이 시작될 때 어떤 명령을 실행하는 방법을 알아봅니다. 이것을 통해서 쉡을 자신에 맞게 커스터마이징 할 수 있습니다. 

### 별명 만들기 (긴 명령어를 간단하게 설정 = startup설정)
$ alias l='ls -al' # 별명을 붙여주는 명령어$ alias c='clear' #c만 입력해도 clear 기능을 수행 (별명)$ alias ..='cd ../' #..만 입력해도 부모 디렉토리로 이동 (별명)$ cd ~ #사용자의 홈디렉토리 이동
$ nano .bashrc #.bashrc파일을 nano에디터로 열기
- .bashrc<br/>
shell에 접속했을 때 .bashrc 파일을 자동 실행하게끔 약속됨<br/>
.bashrc파일 안에 echo 'hi'라고 저장하면, 나중에 shell 접속시 'hi' 출력됨

## 18. 다중 사용자

유닉스 계열 운영체제는 여러 명이 함께 사용할 수 있는 기능을 가지고 있습니다. 이 기능은 강력 하지만 혹독한 대가도 따릅니다. 배우기 어렵고, 보안의 문제가 발생할 수 있습니다. 여기서는 다중 사용자 시스템에 대해서 살펴봅니다.  

### id와 who
$ id #사용자가 누구인지 정보를 알려준다.$ who # 현재 이 시스템에 누가 접속했는지 보여준다.
## 19. 관리자와 일반 사용자

root : super user, 아주 강력한 사용자, 전지전능한 사용자
$ sudo + 명령어 # 일시적으로 super user 권한으로 명령어 사용 가능$ whoami # 지금 사용자가 누구인지 알려준다.$ su - root #super user로 이동
$ su - ideajoon #사용자 계정(ideajoon)으로 이동
#### ubuntu는 일반적으로 root 사용자 권한을 잠궜기 때문에 풀어야한다.
$ sudo passwd -u root # 잠겨 있는 root 권한을 푼다(unlock) 
$ sudo passwd -l root # 풀려 있는 root 권한을 잠근다(lock) 
- -u : unlock
- -l : lock

root 디렉토리 위치는 '/root'로 최상위 디렉토리 아래에 잇는 root디렉토리 이다.

## 20. 사용자의 추가
$ sudo useradd -m ideajoon # ideajoon 사용자 추가
- -m : home 디렉토리를 함께 만들어 주어라는 옵션
$ sudo passwd ideajoon # ideajoon 사용자 비밀번호 설정$ sudo usermod -a -G sudo ideajoon 
# ideajoon 계정을 super user권한을 사용할 수 있게 권한 추가
## 21. 권한 (permission)

여러 사용자들이 적절한 권한에 따라서 파일과 디렉토리를 사용할 수 있도록 하는 방법인 권한에 대해서 알아봅니다. 

- File & Directory에 대한 권한의 종류 : Read & Write & Execute
$ touch perm.txt
$ ls -l perm.txt
$ echo 'hi' > perm.txt
$ cat perm.txt

$ cd /home/ideajoon
$ ls -l perm.txt
$ echo 'hello' > perm.txt -rw-rw-r-- 1 ideajoon ideagroup 0 Dec 4 23:19 perm.txt
- \- : 맨앞글자는 '-'이면 file, 'd'이면 directory라는 뜻

- rw-rw-r-- : access mode<br/>
맨앞 3개 rw- : 사용자의 권한(user)<br/>
중간 3개 rw- : 그룹의 권한(group)<br/>
마지막 3개 r-- : 그 이외 모든 사람들 권한(others)<br/>
※ r(read), w(write), 세번째 자리 - (x가 올수 있는 자리:execute)

- ideajoon : ideajoon가 user(사용자)라는 의미
- ideagroup : ideagroup가 group(그룹)이라는 의미

즉, 이 파일(맨앞 -)에 대해서 ideajoon(user)는 읽고(r) 쓰고(w)는 할 수 있지만 실행(세번째 -)은 할 수 없다. ideagroup(group)도 읽고(r) 쓰고(w)는 할 수 있지만 실행(세번째 -)은 할 수 없다. 다른 모든 사람들은(others) 읽을(r) 수는 있지만 쓸수는(두번째 -) 없고 실행할(세번째 -) 수도 없다.

### 1) 권한을 변경하는 방법 (chmod)

![](permission.png)
$ ls -l perm.txt
$ chmod o-r perm.txt # others(다른 모든 사람들)의 권한 r -> - 로 변경
$ ls -l perm.txt
$ chmod o+r perm.txt # 모든 사용자들에게 권한을 - -> r 로 변경
$ chmod o+w perm.txt # 모든 사용자들에게 권한을 - -> w 로 변경
$ chmod u-r perm.txt # user(사용자) 권한을 r -> - 로 변경
$ chmod u+r perm.txt # user(사용자) 권한을 - -> r 로 변경
### 2) 실행의 개념과 권한 설정
# test.sh라는 파일이 있다고 가정하고

$ ./test.sh # test.sh파일을 실행시키면 permission denied가 뜬다.

$ /bin/bash test.sh # test.sh파일을 실행시키면 잘 실행된다.

$ chmod u+x test.sh # user 에게 x(실행)권한을 부여(+) 한다.
### 3) directory의 권한
$ mkdir perm;cd perm;echo 'hi' > perm.txt
$ chmod o-r perm #모든 사람들에게 perm 폴더의 읽기(r) 권한을 박탈(-)
$ chmod o+r perm #모든 사람들에게 perm 폴더의 읽기(r) 권한을 부여(+)
directory의 권한을 변경하면 해당 directory 안에 있는 모든 파일들의 권한에 영향을 미친다.

#### ☆ 해당 디렉토리안에 있는 모든 디렉토리와 모든 파일의 권한까지 변경방법
$ chmod -R o+w perm # Recursive(재귀적) -R을 넣어 권한 변경
### 4) chmod 사용법 정리

#### (1) Octal modes

Numerical permissions

![](permission02.png)
$ chmod 111 perm.txt # --x--x--x의 권한으로 변경
$ chmod 110 perm.txt # --x--x---의 권한으로 변경
$ chmod 222 perm.txt # -w--w--w-의 권한으로 변경
$ chmod 444 perm.txt # r--r--r--의 권한으로 변경
$ chmod 333 perm.txt # -wx-wx-wx의 권한으로 변경
$ chmod 555 perm.txt # r-xr-xr-x의 권한으로 변경
$ chmod 777 perm.txt # rwxrwxrwx의 권한으로 변경
#### (2) symbolic modes

![](permission03.png)

![](permission04.png)
$ chmod a+r perm.txt #user, group, others 모두에게 r권한 부여(+)
$ chmod a+w perm.txt #user, group, others 모두에게 w권한 부여(+)$ chmod a=rwx perm.txt #user, group, others 모두에게 rwx권한 부여(+)
$ chmod a= perm.txt # ---------의 권한으로 변경
$ chmod a=r perm.txt # r--r--r--의 권한으로 변경 
## 22. 그룹(group)

파일과 디렉토리를 여러 사용자들이 공동으로 관리할 수 있는 방법인 group에 대해서 알아봅니다. 

![](group.png)

### 1) 그룹생성 방법 (계정성싱시)
$ useradd -G {group-name} username
### 2) 그룹생성 방법 (이미 계정이 있을 때, others가 있을 때)

#### 그룹생성
$ sudo groupadd + 그룹이름 #그룹을 생성하기$ nano /etc/group # group파일안에 group에 대한 정보가 들어 있다.
#### 사용자들을 그룹에 추가하기
$ sudo usermod -a -G + 그룹이름 + 사용자이름1 #사용자를 그룹에 추가
$ sudo usermod -a -G + 그룹이름 + 사용자이름2
$ sudo usermod -a -G + 그룹이름 + 사용자이름3
사용자들을 그룹에 추가하고난 이후에는 사용자계정에서 나갔다가 다시 들어 와야한다.

#### 사용자와 그룹을 변경하기
$ sudo chown owner:group #user와 group을 변경하는 명령어
#### 그룹에 권한 부여하기
$ echo 'hi, ideajoon' > test.txt # permission denied 발생
$ sudo chmod g+w # group에 권한 부여
$ echo 'hi, ideajoon' > test.txt
## 23. 인터넷, 네트워크 그리고 서버

인터넷 시대에 접어들면서 오픈소스이면서 무료이고 안정성이 높은 리눅스의 사용이 폭발적으로 증가하고 있습니다. 이번 시간에는 리눅스를 서버로 활용하기 위한 기초적인 방법을 알아봅니다. 

![](server.png)

#### 아이피 주소 알아내기

![](ip.png)
$ ping google.com # 도메인명으로 아이피 주소를 알 수 있다.$ ip addr # 자신의 아이피 주소(private address)를 알 수 있다.$ ifconfig # 자신의 아이피 주소 알아내기
웹브라우저에서 ipinfo.io/ip 싸이트에 접속하면 자신의 아이피를 알려준다.
$ curl google.com # 구글에 접속해서 정보를 출력해준다.
$ curl ipinfo.io/ip # ipinfo이라는 url에 접속해서 public address 겟
curl 명령어를 사용하면 public address가 나오고,<br/>
ip addr 명령어를 사용하면 private address가 나온다.<br/>
때문에 curl과 ip addr통해 알아낸 아이피가 다를 수도 같을 수도 있다. 

## 24. 웹서버 (아파치)

서버의 구체적인 사례로서 웹서버 그 중에서 아파치 웹서버를 설치하고 운영하는 방법

![](webserver.png)

### apache(웹서버) 설치하기
$ sudo apt-cache search apache # apache 모듈 검색$ sudo apt-get update # apt 모듈 업데이트
$ sudo apt-get install apache2 # 아파치 설치하기$ sudo sevice apache2 start # 아파치를 구동시킬 때
$ sudo sevice apache2 stop # 끌때
$ sudo sevice apache2 restart # 끄고 켤때$ sudo htop # 작업관리자로 이동하여 아파치가 잘 구동하는 확인
### elinks 설치하기 (쉘환경에서 웹브라우징 가능)
$ sudo apt-get install elinks # elinks 설치하기$ elinks #elinks로 이동하여 url 넣고 접속 가능$ elinks http://10.0.2.15/ #자신의 웹서버에 자신의 웹브라우저로 접속
위는 내부아이피(private address)로 자신의 웹서버로 접속하는 방법 #!

### localhost로 접속 (컴퓨터 자기자신을 가르키는 표준 IP)
$ elinks http://127.0.0.1/ #자신의 웹서버에 자신의 웹브라우저로 접속$ elinks http://localhost #자신의 웹서버에 자신의 웹브라우저로 접속
위는 localhost로 자신의 웹서버로 접속하는 방법 #2

## 25. 원격제어 (ssh)

원격으로 쉘을 제어할 수 있는 방법인 ssh에 대해서 알아봅니다.

![](ssh.png)
$ sudo apt-get install apenssh-server openssh-client
위의 명령어는 apenssh-server과 openssh-client를 설치한다.
```
$ sudo service ssh start# ssh 서버를 작동시키기
$ sudo ps aux | grep ssh # 잘 작동하는지 확인
```# ssh ideajoon@192.168.0.65 # 192.168.0.65라는 내부 아이피에 접속 
다른 컴퓨터에서 위의 명령어로 해당 피시의 쉘을 제어할 수 있다. 

## 26. 포트 (port)

포트는 네트워크를 통해 적절한 에플리케이션을 실행 시키기 위해서 꼭 필요한 개념입니다. 여기서는 포트가 무엇인지 알아보고, 포트라는 개념을 통해서 할 수 있는 일의 사례를 알아봅니다. 

### 1) 포트란 무엇인가?
```# ssh -p 22 ideajoon@192.168.0.65 # 해당 아이피로 접속```
- -p 22 : 포트 22번으로 접속해라는 의미

![](port.png)

port 번호 0번 ~ 1024는 유명한 서버들이 이미 번호가 할당 약속(표준화)되어 있다. 1025번 ~ 65000번에 해당되는 포트번호들은 표준되어 있지 않아서 필요한 장비에 필요한 번호를 고르면 된다.
```$ sudo nano /etc/ssh/sshd_config # sshd_config에 포트번호 22 적혀있음```
 sshd_config에 적혀 있는 포트 번호를 다른 포트 번호로 바꾸어서 사용가능하다. 

### 2) 포트 포워딩이란?

외부 사용자가 우리집에 있는 서버에 접속할 수 있게 하는 방법

![](port02.png)

- ISP : Internet Service Provider

외부 사용자가 211.46.24.39:9000 이라는 공유기의 9000번 포트로 접속 시도 하면, 공유기에 설정되어 있는 '9000번 포트 => 192.168.0.4:80'으로 192.168.0.4 (private address)의 웹서버 포트(80번 표준포트)로 접속하게 되어 있다. 그러면 해당 서버는 요청 정보를 외부 사용자가에 전송한다. 

- default gateway : 공유기가 가지고 있는 아이피를 지칭

### 3) 포트 포워딩 실습
```$ ip addr # 자신의 아이피 주소 알아내기``````$ ifconfig # 자신의 아이피 주소 알아내기``````$ ip route # default gateway 아이피 주소(공유기 아이피 주소) 알아내기```
- default gateway 아이피 주소(공유기 아이피 주소) 알아내기 #2<br/>
환경설정 - 네트워크 - 와이파이 - 고급 - tcp ip 선택 - router

- 웹브라우저에 해당 default gateway 아이피 주소 접속 : 설정화면

- 관리도구 - 로그인 - 고급설정 - nat 라우터 관리 - 포트 포워드 설정

- 내부아이피(private address) : 본인 아이피 적기

- 외부 포트 : 외부 사용자가 사용할 포트의 번호. 예) 9000

- 내부 포트 : 80번으로 설정 (웹서버 표준 번호)

- 외부 사용자가에게 public address와 9000번 포트를 알려준다.<br/>
예) 211.46.24.39:9000를 알려주고 웹브라우저에 211.46.24.39:9000접속
