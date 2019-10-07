
# Linux basic 

written by ideajoon<br/>
※ 참고 : 생활코딩 (https://opentutorials.org/course/2598/14160) 수업을 정리함

## 목차
1. 디렉토리와 파일
2. 빈도수가 많은 명령어
3. sudo (super user do)
4. 파일편집 (nano)
5. 패키지 매니저 (package manager)
6. 다운로드 방법 (wget, git)
7. 왜 CLI인가? (Command Line Interface) ※ 파이프라인 ( " | " )
8. IO Redirection (Input/Output 방향을 바꾼다)
9. 쉘과 커널
10. 쉘 스크립트 (shell script)
11. 디렉토리의 구조
12. 프로세스 (process)
13. 파일을 찾는 법
14. 백그라운드 실행
15. 항상 실행 (daemon, service)¶
16. 정기적으로 실행 (cron)
17. 쉘을 시작할 때 실행
18. 다중 사용자
19. 관리자와 일반 사용자
20. 사용자의 추가
21. 권한 (permission)
22. 그룹(group)
23. 인터넷, 네트워크 그리고 서버
24. 웹서버 (아파치)
25. 원격제어 (ssh)
26. 포트 (port)
27. 도메인 (domain)
28. 인터넷을 통한 서버간 동기화 (rsync)
29. 로그인 없이 로그인 하기 (ssh key)
30. 연속적으로 명령 실행시키기 (;과 &와 &&의 차이)

## 1. 디렉토리와 파일

$ ls<br/>
현재 디렉토리의 파일 목록을 출력하는 명령어. 'ls -l'은 자세히 보기

$ ls -l<br/>
현재 디렉토리의 파일 목록 자세히 보기

$ pwd<br/>
현재 위치하고 있는 디렉토리를 알려주는 명령어

$ mkdir<br/>
mkdir 새로 생성할 디렉토리명

$ cd<br/>
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

- rm + 파일명 : 파일 삭제
- rm -r + 디렉토리명 : 디렉토리 삭제

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

- clone 이란 명령어는 정기적으로 명령어를 실행시킬 때(예를들어 1분에 한번씩, 10분에 한번씩)

## 7. 왜 CLI인가? (Command Line Interface)

왜 배우기 어려운 명령어(CLI)를 사용하는 것일까요? 여기서는 명령어를 사용하는 이유를 살펴봅니다. 

GUI vs CLI 

CLI(명령어) 방식이 에너지를 적게(메모리 적게) 사용한다. 하지만 GUI는 그래피컬하기 때문에 에너지가 많이 들어도 사용자가 사용하기 쉽다.

```
$ mkdir why;cd why
```

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

위의 결과를 해결하기 위해서는 '>'기호 앞에 '1' 대신 '2'(standard error 의미)를 넣어준다.<br/>
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

```
$ ls -l >> result.txt
```
'>>'기호는 result.txt파일 안에 ls -l의 출력결과를 append로 저장한다.<br/>
'>'기호는 덮어쓰기한다.

```
$ mail joon2332@gmail.com <<haha #haha대신 다른 문자 사용가능
> hello #입력1
> hi #입력2
> wow #입력3
> haha #input을 끝낼때
```

'<<' 기호를 사용하여 입력값을 여러개 사용할 수 있다.<br/>
입력된 정보들은 위의 이메일로 전달된다.

```
$ ls -al > /dev/null
```
화면에도 출력하지 않고 파일에도 저장되지 않음<br/>
/dev/null은 유닉스의 휴지통과 같은 기능

## 9. 쉘과 커널

사용자가 명령을 입력하면 그 명령을 컴퓨터가 이해할 수 있도록 하는 프로그램이 쉘(shell)입니다.<br/>
명령을 해석하는 쉘과 실제로 일을 하는 커널의 관계를 알아보자.

### 1) shell vs kernel

![](https://t1.daumcdn.net/cfile/tistory/27552535590AB2BB0F)

kernel<br/>
하드웨어를 직접적으로 제어하는 역할

shell<br/>
사용자가 입력한 명령어가 shell에게 입력된다. 그리고 kernel이 이해할 수 있도록 처리하고 그 결과를 kernel에게 보낸다.

### 2) bash vs zsh

bash보다 zsh가 좀더 사용자 편리하게 되어 있다. 하지만 bash가 더 범용적이고 거의 모든 리눅스 환경에서 적용가능하다.

sudo apt-get install zsh : zsh 설치

- echo $0<br/>
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

```
$ mkdir script
$ cd script/
$ touch a.log b.log c.log # 3개의 빈 파일을 생성한다.
$ ls -l

$ mkdir bak
$ cp *.log bak #확장자가 log인 모든 파일을 bak에 저장하겠다.
$ ls -l bak

$ mkdir bak # bak디렉토리가 이미 존재하기 때문에 에러가 발생함.
```

mkdir bak 실행시 bak 디렉토리가 없으면 그대로 생성하고 만약 있다면 cp *.log bak가 실행되게 shell script 작성하면 된다. 

### 2) Shell Script 작성 예제

```
$ eco $0 #지금 사용하고 있는 shell type 확인
-bash #출력
```

bash는 'ls /bin' 폴더에 저장되어 있다.

```
$ nano backup # nano로 backup의 이름으로 프로그램 만들기
```

nano에서 프로그램 작성

```
#!/bin/bash                  

if ! [ -d bak ]; then
        mkdir bak
fi
cp *.log bak
```

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

```
$ ./backup #backup파일을 실행시키는 명령어
-bash: ./backup: Permission denied

$ chmod +x backup #백업 파일의 권한을 가지게 해주는 명령어
```

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

```
$ cd /home/ideajoon<br/> #사용자 디렉토리로 바로 이동 명령어
$ cd ~ #사용자 디렉토리로 바로 이동 명령어
```

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

```
$ ps # 프로세스 확인
$ ps aux # 모든 프로세스 확인
$ ps aux | grep apache # apache문자가 있는 문장만 출력
$ sudo kill + 프로세스 아이디 # 해당 프로그램을 강제로 종료하는 명령어
```

top

```
$ sudo top #작업관리자 top프로그램 실행
```

htop

```
$ sudo htop #작업관리자 htop프로그램 실행 (top보다 그래피컬함)
```

htop에서 cpu 등의 컬럼을 더블클릭하면 그 기준으로 정렬해준다.

- TIME+ : 해당 프로그램이 실행 누적 시간
- Command : 해당 프로그램이 어떤 명령으로 실행되어졌는지 보여줌
- MEM% : 해당 프로그램의 물리적인 메모리 사용량(%)
- RES : 실제적인 메모리의 사용량

- Load average : 1분간 cpu 부하평균, 5분간 cpu 부하평균, 15분간 cpu 부하평균

## 13. 파일을 찾는 법

### 1) locate와 find

```
locate *.log #log 확장자의 모든 파일을 찾아준다.
```

locate는 컴퓨터에 저장되어 있는 모든 파일을 하나하나 찾는 것이 아니라 전용 DB(mlocate)를 이용하여 찾아서 빠르다. sudo updatedb 명령어를 통해서 DB 정보를 강제로 업데이트 할 수 있으나 자동으로 주기적(1회/1일)으로 업데이트 되게 되어있다. 때문에 미리 정리정돈 되어 있기 때문에 빠르다.

```
$ find / #root 디렉토리 부터 찾겠다.
$ find . #현재 디렉토리 부터 하위 디렉토리순으로 찾겠다.
$ find ~ #사용자의 HOME 디렉토리에 있는 파일을 찾겠다.
```

```
$ sudo find / -name *.log
```

위의 명령어는 root 디렉토리 부터 log확장자를 가진 모든 파일을 찾는다.

```
$ find ~ -name *.log
```

위의 명령어는 사용자의 home 디렉토리에 있는 모든 log확장자 파일을 찾는다. 사용자의 home 디렉토리에서 찾기 때문에 권한문제가 없어서 sudo를 빼도 된다.

```
$ find . -type f -name tecmint.php
```

- -type f : 확장자를 지정할 수 있다. f = files

위의 명령어는 현재의 디렉토리부터 하위디렉토리 순서로 찾되, tecmint.php라는 파일을 찾는다. 여기서 중요한 것은 '-type f'를 사용하여 tecmint.php라는 파일이 아닌 디렉토리가 있더라도 디렉토리는 제외하고 파일만을 찾게 해준다.

```
$ find . -type f -name "tocmint.txt" -exec rm -f {} \;
```

- find . : 현재 디렉토리 부터 하위 디렉토리 순으로 찾는다.
- -type f : 찾고자하는 format을 정할 수 있다. 여기서 f는 files이다.
- -exec : 실행시킨다.
- rm : 삭제한다.
- -f : 묻고 따지지도 않고 행한다.
- {} : 명령을 통해서 검색한 파일의 이름이 {}사이에 위치한다.

### 2) whereis 와 $PATH

```
$ whereis ls #ls 프로그램 파일과 매뉴얼의 경로를 찾을 때 사용 명령어
```

```
$ echo $PATH # $path라는 변수에에 담겨 있는 값 출력 
```

즉, whereis는 $PATH에 담겨있는 경로를 순서대로 찾아서 해당 정보가 발견되면 원하는 파일이 있는 경로를 출력한다. path 담겨있는 경로를 바꿀수 있다. 원하는 경로를 넣어서 해당 디렉토리에서 찾게끔 넣어준다.

## 14. 백그라운드 실행 

백그라운드 작업을 하는 방법

- Ctrl + z<br/>
실행중인 프로그램을 백그라운드로 보내는 단축키. 이 기능을 실행하면 명령어가 일시 정지 됩니다. 

- &가 명령어 뒤에 붙으면 명령어가 실행될 때 백그라운드로 실행됩니다.<br/> 
    ex) ls -alR / > result.txt 2> error.log & : 

- jobs : 백그라운드 작업들의 목록을 보여줍니다. 

```
$ nano
```

위 명령으로 nano프로그램을 열고 파일을 작성하고 ctrl + z를 누르면 nano프로그램을 나가지 않고 nano프로그램을 백그라운드로 보냄

```
$ fg #forward ground의 약자로 백그라운드에 있던 nano프로그램이 fg로 올라온다.
```

```
$ fg %2 #jobs의 목록에 있는 순서 2번째의 백그라운드를 fg로 불러온다.
```

```
$ jobs #현재 백그라운드로 운영되고 잇는 목록을 보여줌
```

```
$ kill %3 #jobs의 목록에 있는 순서 3번째의 백그라운드를 강제 종료한다.
```

```
$ kill -9 %3 #'-9'를 추가하여 좀더 강력한 강제 명령을 한다.
```

```
$ ls -al -R / > result.txt 2> error.log & #프로그램 실행시 바로 백그라운드로 보냄
```

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

```
$ sudo apt-get install apache2 # 웹서버 아파치 설치
```

웹서버 apache는 /etc/init.d/ 에 설치되어 있다.

init.d라는 디렉토리에 데몬 프로그램들이 설치되어 있다.

#### (1) 데몬 프로그램을 start / stop 명령어

```
$ sudo service apache2 start # 데몬 프로그램인 아파치 켜기위한 명령어
```

```
$ sudo service apache2 stop # 데몬 프로그램인 아파치를 끌때 명령어
```

#### (2) 컴퓨터 부팅시 데몬 프로그램을 자동으로 start 하기

```
$ cd /etc/
$ cd cd r
$ cd cd rc3.d/ #리눅스를 CLI로 구동할 때는 rc3.d/ 디렉토리를 연다.
$ ls -l
```

즉, CLI는 rc3.d/ 디렉토리에 링크(바로가기 같은)로 특정 데몬 프로그램을 만들어 높으면 컴퓨터 부팅시 자동실행 된다.

만약에 리눅스를 GUI로 구동할 때는 rc5.d/ 디렉토리에 해당 데몬 프로그램을 링크를 걸어 놓는다.

## 16. 정기적으로 실행 (cron)

cron을 통해서 정기적으로 명령을 실행하는 방법

```
$ crontab -e #-e옵션은 하고자 하는 일을 저장할 수 있는 에디터가 열린다.
```

crontab 파일이 원하는 에디터(nano 등)으로 열리고 크론파일안에 하고자 하는 일을 저장하면 정기적으로 프로그램이 실행된다.

```
# 실행방법

# m h dom(day of month) mon(몇월) dow(요일) command

*/1 : 1분에 한번 실행
*/10 : 10분에 한번 실행
10 4 : 4시 10분에 실행
10 4 24 5 : 5월 24일 4시 10분에 실행
1/* * * * * : 모든 요일 모든월 모든일 모든 시간에 1분에 한번씩 실행 
```

![](https://i.stack.imgur.com/SIdCf.gif)

```
$ date # 현재의 시간을 출력
$ date > date.log # 덮어쓰기 형식으로 저장
$ cat date.log
$ date >> date.log # append 형식으로 저장
$ cat date.log
$ fg # 실행하던 crontab 화면으로 이동
```

```
#crontab 화면에서

1/* * * * * date >> date.log
```

```
$ tail -f date.log
```

- tail : date.log 파일의 끝줄을 출력
- -f : date.log 파일이 변경시(append 될때) 마다 출력해주는 옵션

```
#crontab 화면에서

1/* * * * * date >> date.log 2>&
```

- 2>&<br/>
표준에러를 표준축력으로 redirection 시켜준다. 즉, 에러가 발생하면 그 에러를 date.log에 함께 저장시켜준다. 

## 17. 쉘을 시작할 때 실행

쉘이 시작될 때 어떤 명령을 실행하는 방법을 알아봅니다. 이것을 통해서 쉡을 자신에 맞게 커스터마이징 할 수 있습니다. 

### 별명 만들기 (긴 명령어를 간단하게 설정 = startup설정)

```
$ alias l='ls -al' # 별명을 붙여주는 명령어
```

```
$ alias c='clear' #c만 입력해도 clear 기능을 수행 (별명)
```

```
$ alias ..='cd ../' #..만 입력해도 부모 디렉토리로 이동 (별명)
```

```
$ cd ~ #사용자의 홈디렉토리 이동
$ nano .bashrc #.bashrc파일을 nano에디터로 열기
```

- .bashrc<br/>
shell에 접속했을 때 .bashrc 파일을 자동 실행하게끔 약속됨<br/>
.bashrc파일 안에 echo 'hi'라고 저장하면, 나중에 shell 접속시 'hi' 출력됨

## 18. 다중 사용자

유닉스 계열 운영체제는 여러 명이 함께 사용할 수 있는 기능을 가지고 있습니다. 이 기능은 강력 하지만 혹독한 대가도 따릅니다. 배우기 어렵고, 보안의 문제가 발생할 수 있습니다. 여기서는 다중 사용자 시스템에 대해서 살펴봅니다.  

### id와 who

```
$ id #사용자가 누구인지 정보를 알려준다.
```

```
$ who # 현재 이 시스템에 누가 접속했는지 보여준다.
```

## 19. 관리자와 일반 사용자

root : super user, 아주 강력한 사용자, 전지전능한 사용자

```
$ sudo + 명령어 # 일시적으로 super user 권한으로 명령어 사용 가능
```

```
$ whoami # 지금 사용자가 누구인지 알려준다.
```

```
$ su - root #super user로 이동
$ su - ideajoon #사용자 계정(ideajoon)으로 이동
```

#### ubuntu는 일반적으로 root 사용자 권한을 잠궜기 때문에 풀어야한다.

```
$ sudo passwd -u root # 잠겨 있는 root 권한을 푼다(unlock) 
$ sudo passwd -l root # 풀려 있는 root 권한을 잠근다(lock) 
```

- -u : unlock
- -l : lock

root 디렉토리 위치는 '/root'로 최상위 디렉토리 아래에 잇는 root디렉토리 이다.

## 20. 사용자의 추가

```
$ sudo useradd -m ideajoon # ideajoon 사용자 추가
```

- -m : home 디렉토리를 함께 만들어 주어라는 옵션

```
$ sudo passwd ideajoon # ideajoon 사용자 비밀번호 설정
```

```
$ sudo usermod -a -G sudo ideajoon 
# ideajoon 계정을 super user권한을 사용할 수 있게 권한 추가
```

## 21. 권한 (permission)

여러 사용자들이 적절한 권한에 따라서 파일과 디렉토리를 사용할 수 있도록 하는 방법인 권한에 대해서 알아봅니다. 

- File & Directory에 대한 권한의 종류 : Read & Write & Execute

```
$ touch perm.txt
$ ls -l perm.txt
$ echo 'hi' > perm.txt
$ cat perm.txt

$ cd /home/ideajoon
$ ls -l perm.txt
$ echo 'hello' > perm.txt 
```

```
-rw-rw-r-- 1 ideajoon ideagroup 0 Dec 4 23:19 perm.txt
```

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

![](https://lh3.googleusercontent.com/-D2dKfJkLd9Gyep_skR9wNMS82v1o3tqKk6kKR1Ct4_Ow5dQRsitpdWFg_SbGXBYh_SU4N8dKO7Edil_YQ32nB2F6GqK_mC7fhSz1C5NGyTZRlXfvC0EpJwIMBAxXKnc3TwUDiWh7t2bmzc-gHH0LZMhXgFfN4-0w6u5Qt1euA1h_Ew0qVvDH7m9--sIxsduAZlhIzyB7BdBqr7UT1nLklrHiy7n_-Co_XHds7cW7BJwb36AlW5VVBe7i23N84LKHsBaGdRl8F4abMJDFUAay1mL0g19zkVfVkFcVJ3scADONxiLv0Kk-DoxOUC7IQE9Ko4ObpEem26NUTU5hVXTN3nEHTWxltBFLEBDu3EJrTEhQFyGwu4qOkMLp78d75rf0E1-GNXTGIF2pVKIdSzOKOk5DjdDoEb1X33Eay0iHG9IW1O7qoz2KI3t0ZtdeuRXlWCxzAFWyuKDKUgI0k7of_wrZz7H1IjAnSo4V3XcttldYt7rKpC0akCkH8ABk9qT4HrYP4oBP8gAuod1wNMRKsRfYM65WW8dwxxroYogZRHAjSGO5SnwB5R_btRVp_UVD3tvZ4TkvuJ3zPMPCV0743uaeVLHage2V9h6aXmsa5KPBWYOnRKbAySj-1nZEcN0BoasjwUM1ts5ohrIHz37jqZTpOt3bv8=w764-h340-no)

```
$ ls -l perm.txt
$ chmod o-r perm.txt # others(다른 모든 사람들)의 권한 r -> - 로 변경
$ ls -l perm.txt
$ chmod o+r perm.txt # 모든 사용자들에게 권한을 - -> r 로 변경
$ chmod o+w perm.txt # 모든 사용자들에게 권한을 - -> w 로 변경
$ chmod u-r perm.txt # user(사용자) 권한을 r -> - 로 변경
$ chmod u+r perm.txt # user(사용자) 권한을 - -> r 로 변경
```

### 2) 실행의 개념과 권한 설정

```
# test.sh라는 파일이 있다고 가정하고

$ ./test.sh # test.sh파일을 실행시키면 permission denied가 뜬다.

$ /bin/bash test.sh # test.sh파일을 실행시키면 잘 실행된다.

$ chmod u+x test.sh # user 에게 x(실행)권한을 부여(+) 한다.
```

### 3) directory의 권한

```
$ mkdir perm;cd perm;echo 'hi' > perm.txt
$ chmod o-r perm #모든 사람들에게 perm 폴더의 읽기(r) 권한을 박탈(-)
$ chmod o+r perm #모든 사람들에게 perm 폴더의 읽기(r) 권한을 부여(+)
```

directory의 권한을 변경하면 해당 directory 안에 있는 모든 파일들의 권한에 영향을 미친다.

#### ☆ 해당 디렉토리안에 있는 모든 디렉토리와 모든 파일의 권한까지 변경방법

```
$ chmod -R o+w perm # Recursive(재귀적) -R을 넣어 권한 변경
```

### 4) chmod 사용법 정리

#### (1) Octal modes

Numerical permissions

![](https://lh3.googleusercontent.com/dbmerRjqcBPAAu8w7Fmulil9PZHvyY5RaxrWWBdsN9-17K3FVg3j2o52MuLkn3II8wY8bks38YwCM4CHWO1V1lJIDb7Zk2xNtcf3pRc4iEqRFs8WDS1NcbaCXFoQWvaZ8dswW0Z2WOYsdVqLgzwUeiHaSHsinzfnZcPRjMD9LuVC9bl8VGSzHni5t6cT1oS53uYXP79DlvNF5534NB_syBQsLxJZs5Qm0ZggrTfwhMaaQlBDlkYoPvroescAq28GlnMI22dN2w4bgl6gp75t_c5__9NAB0VXEPxKhkXpRLm9uKG9DxWkOosAsrJ1BS7l3INbHup7aw2zsBaoi13BhMgZyvuNOgBmrv5SwFPvzt1YJeUp5lE5DN0Qkp5vVM7nCpF7xz4J4Yf0EnarIKtuCFFnf9uTIDQkXvG9EPHhqfXMZPLtdS9odQMW7y7RE8swS_GJHT_XMIMBU4vA8xJYV1xCNuIMtCbmMt0zZECKGDFhb1FtaGmwb_01TxxgZvfRGP1D37yM-wk-HRRGrlMWsmSVfsDYP94hk9BBg4EwQHiGh61jIOQMHtbdokzlVk6UFNlvVw3oyq8pn8WeNqLkPxX3NoflWEj-ysnn5I0SNKmh9MJDwrOlDXXiSuWdJooaluuVYCbJWqUTPhc5aJxS0PqSubwHDzI=w666-h468-no)

```
$ chmod 111 perm.txt # --x--x--x의 권한으로 변경
$ chmod 110 perm.txt # --x--x---의 권한으로 변경
$ chmod 222 perm.txt # -w--w--w-의 권한으로 변경
$ chmod 444 perm.txt # r--r--r--의 권한으로 변경
$ chmod 333 perm.txt # -wx-wx-wx의 권한으로 변경
$ chmod 555 perm.txt # r-xr-xr-x의 권한으로 변경
$ chmod 777 perm.txt # rwxrwxrwx의 권한으로 변경
```

#### (2) symbolic modes

![](https://lh3.googleusercontent.com/Iu7-jI7gcjloK6BaAAqkFkwItEw9fl8vQJuKJAdfWc4YbiOpC_QJGG6Oe1DfrbkwMH68peUkuVTLojnDitWlHABMDLcBdOSqw0bB8bOfTSG9g8LGMAaH5C-sSqDkhjflIOMFUpZy5TROqo0NkLSANoHCprmWhX0akBoP06tVBz4YZPd-VRMPiJLRNAgf_MAq85y0FbP8o_HxMenQth2EhZryLAS7UbkVsKG4p-_kEhazdNqJPqJ-8Y7VUKEKZR-V_OtWKBQo4GNgJktJ_B8nJAmqU7VUrLjoFy9Y4hjVr8km9oF1zbuT6l4mnJDRYzlq8A7TxAuLlTSqeWpYgMd4MV8vaiDJBQA9SwtUokLMJm4XU2bI6_MWk18RyZzUu0DZuZLfk4Tx0b7g7mz8teR6G7GZWFeQuNim2y3vsLqyLS7c0Jxt4bD_FJEslm8MCSv6hLleEZIYOgDd3x1j1EwtfKRvM63TaAfwr8J822yWw7D4FLgqyR2gwEKWnRDEXTrA9Eg6Guetf2zB2xfDP4URld62HalEhpnW1SLghv8JxHhgZiM2Jbqoo2PpjQmWS95e4eK3I70Y4EdsLuqunRuyFt59KsbvBxL3yBlWRiWr4OPMP3OBbbn0mG7nrfN5oozXH7Yj4JT1WALxH-SuAZZXzUn7yml_9Hg=w747-h184-no)

![](https://lh3.googleusercontent.com/GSdq-vZG8itMTG7ZPmQB4qUmFJhH83VmUSFDg2Aw64xqeDf-aJXSNYMy2U3tzjENOU_eWK8Ddc5j8uBDCzlckJQepoS_ka-50SwNKwec-MttF4EfkEs416A5-hMD88j60UWf-MGWhkfcoqU2Vi_beo0Or3LxR7qLXPYubLdN5YxgTFZ0RB9KAFNBoayQxp6iq1qfGBr7jKySFSYl1r78FErnIt9lNodmlx3W4DpU46CySQ--XTJ3RkRyNWy3uEBLt919xzngzg6fcDlcyynmz-1D3AKFO0okd7UU1papkjnNNdGx3Zf88HPwCeRR1xNTb9bBIKOMKwV3MUOkIeo634H3Bg2AF71yqv_zh3Hf1lDFto5NFDOJcI0Oc_axGz3qgj_9RXhR7xYFVzGY1_Db0q1SwQNxWiTVMP4X-31_BKHE148DmNO_nZ51XcCVkXHP2eKx_dZccL9QNaGCeKmgL1E4bu8Sr8wIFpR5qf3PCygEH5FaRoQZdwdkfoKfvoavhGAbPieQb_8_TU8zi6hs4do-3LNWIfMEWDQ5ZXYuawNxULM_5B3b19OWQkMssecWJsqCooAKTT2hBIPItG1bVqKVQqdBJ8bVcTEgGOF97NoNI2XUUhqSDTvT35sXzCNe2CBmwJz528mqhveKLnqsgRm3AkaTAOA=w747-h170-no)

```
$ chmod a+r perm.txt #user, group, others 모두에게 r권한 부여(+)
$ chmod a+w perm.txt #user, group, others 모두에게 w권한 부여(+)
```

```
$ chmod a=rwx perm.txt #user, group, others 모두에게 rwx권한 부여(+)
$ chmod a= perm.txt # ---------의 권한으로 변경
$ chmod a=r perm.txt # r--r--r--의 권한으로 변경 
```

## 22. 그룹(group)

파일과 디렉토리를 여러 사용자들이 공동으로 관리할 수 있는 방법인 group에 대해서 알아봅니다. 

![](https://lh3.googleusercontent.com/36udwjO-jhTD9k2gVcNA1NJh0lDArlSRkzcvxVEMn13_3rF3v2T5IJbeEqP3x5zJupi2iSeoxUK9S5niXbcY-zhKFRKpgJYZxnY51ZTvVuHjjJRobWobqIAC9pLoDVokgrzY-Ph6XoDfzzed64BsAevoThmJU2PforALTp26fmCNq0M7LGot8xKLQkdvbqnjCxpPUXXQV19_3yPqpcyzTQBXebMJ6-FXX69jLpUctZGYkT_aRZmQAvH0WFxSMrysx5p-EOudzrVjeCQJgzhZ_RXoF9K2YFTMnAE1M4ARdEjfzELkGRVn-13VlvZ8ODkyWrdsi6NC_JrLeJDdnjDA8iaw8Hdq1k6y7rlVE_nzg3mVRJ-8hmpU7et5hATnaZSW0eqFvz4vVou5dSWzBmm3gA5SzLgixJX7CD5A4hGF4LvTQUFtBY_LngSRkjzgKwTAShY-4AfHiGkbQEWGki9U83G9QgpFFev1YDdvMFcN2325fuPpoClVE6I30K5mdlTDMp8G3A05SFrR6wswI5H_tjaqoNRj8zfQHoRHd5HlvC9X7U6zBg1OviPtMyc1u-FhD35xJp6hwFTpUqvUDNQZNxC-aOvvY5SpdPQNCDcXMjaKoZyPsiLWnZtSIFcwlZ3tGMTkP14Zp-egBUEudptRFgx7LHM3v8M=w765-h431-no)

### 1) 그룹생성 방법 (계정성싱시)

```
$ useradd -G {group-name} username
```

### 2) 그룹생성 방법 (이미 계정이 있을 때, others가 있을 때)

#### 그룹생성

```
$ sudo groupadd + 그룹이름 #그룹을 생성하기
```

```
$ nano /etc/group # group파일안에 group에 대한 정보가 들어 있다.
```

#### 사용자들을 그룹에 추가하기

```
$ sudo usermod -a -G + 그룹이름 + 사용자이름1 #사용자를 그룹에 추가
$ sudo usermod -a -G + 그룹이름 + 사용자이름2
$ sudo usermod -a -G + 그룹이름 + 사용자이름3
```

사용자들을 그룹에 추가하고난 이후에는 사용자계정에서 나갔다가 다시 들어 와야한다.

#### 사용자와 그룹을 변경하기

```
$ sudo chown owner:group #user와 group을 변경하는 명령어
```

#### 그룹에 권한 부여하기

```
$ echo 'hi, ideajoon' > test.txt # permission denied 발생
$ sudo chmod g+w # group에 권한 부여
$ echo 'hi, ideajoon' > test.txt
```

## 23. 인터넷, 네트워크 그리고 서버

인터넷 시대에 접어들면서 오픈소스이면서 무료이고 안정성이 높은 리눅스의 사용이 폭발적으로 증가하고 있습니다. 이번 시간에는 리눅스를 서버로 활용하기 위한 기초적인 방법을 알아봅니다. 

![](https://lh3.googleusercontent.com/cfhRqeS74yomq044N-TJTUoS58eE2h5AWpXL2hWQ6z-SVSOBt7t1cOC9isE4izT2g1KPxa4Ovdfj_TdEvkb_2F2gb8eiogRgo76XbAU-lBzOzsT46P2bWojOc48qhvso2GiD3k5AmbnLsie8JavYcp0LfspPUJPzDKkRPRqJr8PwnQygNkpnnDuRAKqFZcqelg_B4fjTIl22j30PXxi2DsIDohCUmJ-2ERugSxPHFEntvLMVk2HK1NXPCueEXhGTG-b1pUO9T2rWK51q8LzSahpASAPLukwLHeZGn6jHxo6yT1-oyNHMSpzeKNMM6wKL6UV7AgiDg9Mk1twobXuRPy6MUiZKqRGnLm-yk9CZ2asroGOkOeGtAAD_xoKeoGUW0xf-5vL-DzSYSDjctMfZlv2kptgRV7hFs1DWh_ObLq40SFjXjxqcH2bOI2MXtcu4s4q69IS-aa6F_PfWde0izon10TKtqjaEbNlg5fqKWpyMrHKSTXObEnFCyNy8s8nu5gOlwjFy99Q3fH3hrN2p4_laWukAstq4DEUVmC8OxRwgppapUnOdma7T0MnMmJiKFHz81vzzyS8PLyrhbkkQO-yvQFD8_sYGGsKMOYErhgmzvieVnUK3c5sI22d_ZkTkyE6ViBHGNSYt0FKPc5KoFlmQHXlMA8I=w790-h440-no)

#### 아이피 주소 알아내기

![](https://lh3.googleusercontent.com/XUzDwBS3A9UPBxcVRHJkOswJo3WuaUHi2pJZcSRUD9if20ZPb3vuqharklus6X_BvpEBDZjjruH3BjfcMPKZLAA-WVcm4gGyIRplkGHGqMlqjbObCno4C2v0OYYLkOZunzdEPzDmlfQIrSoRMUWHe1AivtowD0GAE1cd6s_81BatOv9oBbc1OLFjEv9j1dk7GXfHiOByl_p1N-4yk7mxJRJqTOB6Z-YBEq5UK7yw9qs9Mcug8nJUPiMEVzb-S0SCx5OqVtZMxHrJoMDdTnR2HEzI4sYZvqakuKeWSSSi76BWBC30hz3AJtAIx-yPaPAr4LZ0pu61KqzUDYgUnmFa3lxZ-1NHID5083AYlbcCmq_1k0du9Q4reUAP84G8xxTDoVR70QEw_T9-0Fr9NU-FuAcEvHQuIJYUcQkDklPiAa5hLT6Rtwidmncd8b5FnHdzTtferpAWBOEsBnLni4p_odwPxQ2-6vlqSxMtd8iEjME2QSHt86Rc_PFCLwshZ7rU7fchsj5LRiYYUORCdvp4ZZzZKj9KOHKs5P728ptA10I2ouoVMn4QWZVJq6osn2oTEfB_NO3HmZcFgFBy8v4QiURrl0uLbDt4pNS-0w_aZRwGtAWoWznDfkuKsVnbEiYf7m615-Yq_Vck9DUfFdiZBzUfbvG18X4=w802-h440-no)

```
$ ping google.com # 도메인명으로 아이피 주소를 알 수 있다.
```

```
$ ip addr # 자신의 아이피 주소(private address)를 알 수 있다.
```

```
$ ifconfig # 자신의 아이피 주소 알아내기
```

웹브라우저에서 ipinfo.io/ip 싸이트에 접속하면 자신의 아이피를 알려준다.

```
$ curl google.com # 구글에 접속해서 정보를 출력해준다.
$ curl ipinfo.io/ip # ipinfo이라는 url에 접속해서 public address 겟
```

curl 명령어를 사용하면 public address가 나오고,<br/>
ip addr 명령어를 사용하면 private address가 나온다.<br/>
때문에 curl과 ip addr통해 알아낸 아이피가 다를 수도 같을 수도 있다. 

## 24. 웹서버 (아파치)

서버의 구체적인 사례로서 웹서버 그 중에서 아파치 웹서버를 설치하고 운영하는 방법

![](https://lh3.googleusercontent.com/BdHevipxuKeOATbNhHR8z8iKkRogzS8uSZ00sRVVNcQhCU-xzyJZAKaDPmMtTYltHvIyXE-zN2WR14S0FFIEPSz6C7rovH_HeyHTR9WEfdj-bSQI3-ZAhmsOkS4vJXvS-7PtxzOOzcnUkCy863tyaX50TVa45C_vKSdXLnfYSI8J42Jud8uyjdGNSbozlDXr2eF-CjZIjszIrZVnvIDfYFi269qlwhoW0xTnmoArdn_GtXJxpuq6iuCJj2NDYKFqctEBgPsVeLY6qBfzBNIz-nZVBdIKO7l7wJYk0vQ1hEqyJ3OyvMbRszH0n8ck8itoLntKcr8ggeEZUbFxBLH7EOIuJWlQpneJQwgDd3xCB78hnrAmUhu8KHaOXk1p6BzW2ebrekw5FFZvV0K0YYeseMlfebSzLpQmiG3dExxM_efsFVkWrlzJm3vUNOrBsv1U540IUWULsd5E0U74tmnAeWxJ6MGHKvhpN8DK3nF93FI-ZqqiSxRgzbpqgflLQVe4I-zyRiYEHk3mPVNz0B6A2ub8AdoGSAf8BrHl4ZYwGPohAh3modP40frQbZoFTY25pxFvgcYQ2wLfyBpBrYJn6OKrvZWSn92IYmJiUw80c5SN0TmH2dFPP7vqz3-jjXv3zhu8hCOuFMtQc3cNf809u2YEKCiQ58g=w794-h440-no)

### 1) apache(웹서버) 설치하기

```
$ sudo apt-cache search apache # apache 모듈 검색
```

```
$ sudo apt-get update # apt 모듈 업데이트
$ sudo apt-get install apache2 # 아파치 설치하기
```

```
$ sudo sevice apache2 start # 아파치를 구동시킬 때
$ sudo sevice apache2 stop # 끌때
$ sudo sevice apache2 restart # 끄고 켤때
```

```
$ sudo htop # 작업관리자로 이동하여 아파치가 잘 구동하는 확인
```

### 2) elinks 설치하기 (쉘환경에서 웹브라우징 가능)

```
$ sudo apt-get install elinks # elinks 설치하기
```

```
$ elinks #elinks로 이동하여 url 넣고 접속 가능
```

```
$ elinks http://10.0.2.15/ #자신의 웹서버에 자신의 웹브라우저로 접속
```

위는 내부아이피(private address)로 자신의 웹서버로 접속하는 방법 #!

### 3) localhost로 접속 (컴퓨터 자기자신을 가르키는 표준 IP)

```
$ elinks http://127.0.0.1/ #자신의 웹서버에 자신의 웹브라우저로 접속
```

```
$ elinks http://localhost #자신의 웹서버에 자신의 웹브라우저로 접속
```

위는 localhost로 자신의 웹서버로 접속하는 방법 #2

![](https://lh3.googleusercontent.com/1jlWiRXeXviSYTpFLeWtXCOoc7MrsrpaahZtYeckSgVLabAON2fjFwzDXalxgLJbqIjMWM1cauf1J4CMbRu0XEFOP_pauSRKTLRJhCF6Cumf5d3UIyR6VLCFrErWbmmsiOk3-EZKOaVtlgzOlk8UcmJD7Lest630Vxz3RoQfitHae_OxCyCHiBTeRwzHWgSE2TsVDqjp12dgm_zXOYhyUirJ97lsfiF06-RQnq6ct8vm6B0kqt3SxyPWLou2qptjrszKbhznjkeE_wgmyfeCwr5yLf5YbEiUPFbzqsXpwobpItunmX--2vRS2XB4V2SZMd7Pk3MBN5q-8dZJmk-PGxuT6_0x4Ud_vc6Ep00obmd3WeRe7IbJ-mvvb13Aj1KyHQBM8nf7O7xDO8y8EAQugTiTazA8bChmVkLjNk7seb24nWJ6GlcvDMonE41d8Thu77uzDU4bKEg8XeM9QGmRwIlv1bBPjtiRUUbQ9wY9ExlyIRjdzweJyDOwzXrsKcMSXZpSG-WU2T1OBT7SLSEjV40fd12Y-sfD3WCcDGbYyJVFmZbB8BUdjzk6g9sIBbCtkAPuacjQElBVIW1mNSRAXtt51LerXayrha0zAv8Hk1lSEZITXjswRZZIX7G0HU5z-Qn1qUiixB8fGgyBU3DpFkeYzEc8mdo=w794-h440-no)

### 4) 웹브라우저가 웹서버 저장소의 index.html 파일 찾기

![](https://lh3.googleusercontent.com/ySCOniZB5Xb-RW6RCXMxSYjD_z0ESs6632dfzygufAYw8wqOUNxs1hHZYXQDmW4-HcSXwUBCzqjgPCoXbd8B4pNygR_jffSOLCFCqzEVx0j1BLdUWOl6_XrUbEIIbRNKL9KzNFkHI8oE6qL1Ttzgk5Q8rdWdtcvFddumd-nCRNrc9pFt1dOMGjHYwWqQCgI2AO379cRzIhbPy4qJkRo6WfyDCZbg-rXlAuKns5vcwT4ACKPVVqDCE7tEetpqJpXq9AUSwwnfFD-F76aVPwyMJ0MXgpY681dZvhmTK1B10BosZ0OkVxdqV-zNuTvuUrnWNp0K88XrThA-T417EM5x7EPRGfychNvuVgGOzd5c28eJz8P9DzIGG5ySkw1yv8YHSzKAtdBhkFviF9xvFAvEjdYdxxKIHYFvqbWwTmnYnewbyK3ha5eYoDedKXcNS0t_tSZFoHl3_57l55oODB0rpws_7gXgLdTOzqEoGskkGbeiIvLSYvvxgCcpE6F51HwVb6ydUg3mF741PP-5R61RNmJLnnkqgrnJkZ1xn3u4DOm7H3MCwJ7uJbD6shxKnvv_KtPp9peqMxVQK-bHD4ZyY_Mdur02M3Y4njNJzO0QOQC0ajAOG4BkaBOf6cjPNahHJbCBULdnWHRHE6KHyHQR3Pw5PolcyQo=w794-h440-no)

#### index.html의 document root는 무엇일까?

※ document root : 웹페이지를 찾는 최상의 디렉토리

/etc/apache2/ 의 디렉토리에 있는 apache2.conf파일 안의 설정에 따라 index.html파일을 여는 동작이 바뀔 수 있다.

```
$ cd /etc #동작방법 설정할 수 있는 프로그램 있는 디렉토리로 이동
$ cd apache2/ #apache2.conf라는 파일이 저장되어 있는 디렉토리로 이동
$ nano apache2.conf # apache2.conf파일 나노에디터로 열기/ 설정확인
```

index.html이 있는 디렉토리로 이동

```
$ cd /var/www/html #index.html이 있는 디렉토리로 이동
```

#### 즉, 웹서버는 /var/www/html 디렉토리에서 웹피이지를 찾는다.<br/>
아래 000-default.conf 파일안에 
- 'DocumentRoot /var/www/html'이라고 명시되어 있기 때문에 웹서버는 해당 폴더에서 웹페이지를 찾는다.<br/>

```
$ nano /etc/apache2/sites-enabled/000-default.conf # documentroot 설정확인
```

#### 웹브라우저 실행시 에러로그와 접속정보를 알아보자.

- 'Errorlog \${APACHE_LOG_DIR}/error.log'에 에러 로그 저장되어 있다.
- 'Customlog \${APACHE_LOG_DIR}/access.log'에 접속 정보가 저장된다.

```
$ cat /var/log/apache2/error.log # 에러로그 모두 출력

$ tail -f /var/log/apache2/access.log # 접속정보를 끝에 하나씩 출력 출력
```

쉘에서 index.html 웹브라우저 열기

```
$ elinks http://127.0.0.1/index.html #쉘에서 index.html 웹브라우저 열기
```

```
$ curl http://127.0.0.1/index.html #쉘에서 index.html 웹브라우저 열기
```

```
$ sudo mv index.html index5.html #파일 이름 변경(->index5.html)
$ sudo nano index.html #index.html파일을 만들고 나노에디터로 열기
```

## 25. 원격제어 (ssh)

원격으로 쉘을 제어할 수 있는 방법인 ssh에 대해서 알아봅니다.

![](https://lh3.googleusercontent.com/6StBn0Plt5Pj8C1Grqh46aTNy2U_e5rZejo_p3zOUvMUihdzZfnnrnd6YZMPj6vgRGRrOiiZCmBpcykEsRZeOA4W9Etb2SNooj8u3ykLIV4GBcGy86O9cefjLEJrG1Zm3BaxvJZ_XuxEOzPpER2jHmB6r6vUoQnTUDS-No8oHr3WhKP2Tg2-ZrTVwZkgfQ21on-O1aRfWaO_Ysq1ZUehjJs3Gh1OtF4ucnj5VYQRmCU5QehuuBLoxi6dNznvDiLHN-gw8y0EgTcNwJQ8R5SmExEImOR8S9LABewMAzIjg-5BWKFxw-i6nbh2paIdBA85CddYM3YewLn8lLNuU_z-6sMyYHgK8RJ0Rawizd_-Hqqr09mj_8m1WBC0BAAptUvYowznIz8b16boFofshjFQXTpK-jT2R7jChUdU1ZSjsFE2tLkyk2CrTfycd-aG1fIO4T-rXHgnacwHgOGhFa-0HcmuKTHkB24rSMH0fMWQKUAlxYJ9lAfx6_Vk1aJWn6cqMWPRTuuxe1zQnGuYmtFN8p81E8RtSX9O1zdx5pC7ps_LU-Fx0Uxf67yPKCZSEvFuZN0Pv-qrhR9_cBW_5diYgEceTgHzwBIiO7rHWjMvfj8U7NiVqZo4jYxNp5z_UXfTDz4tt3wNYwdcPz24xlf_mnDW38Q8PAY=w802-h440-no)

```
$ sudo apt-get install apenssh-server openssh-client
```

위의 명령어는 apenssh-server과 openssh-client를 설치한다.

```
$ sudo service ssh start# ssh 서버를 작동시키기
$ sudo ps aux | grep ssh # 잘 작동하는지 확인
```

```
# ssh ideajoon@192.168.0.65 # 192.168.0.65라는 내부 아이피에 접속 
```

다른 컴퓨터에서 위의 명령어로 해당 피시의 쉘을 제어할 수 있다. 

## 26. 포트 (port)

포트는 네트워크를 통해 적절한 에플리케이션을 실행 시키기 위해서 꼭 필요한 개념입니다. 여기서는 포트가 무엇인지 알아보고, 포트라는 개념을 통해서 할 수 있는 일의 사례를 알아봅니다. 

### 1) 포트란 무엇인가?

```
# ssh -p 22 ideajoon@192.168.0.65 # 해당 아이피로 접속
```

- -p 22 : 포트 22번으로 접속해라는 의미

![](https://lh3.googleusercontent.com/cCKD3xHin4Q6Ng3yJ58exZYLxVAO9LHrAFpi_gGInG-4IOO4pjnFN_6lO0LlmExABGk8R1wQ8h2ql_iaZUIOQue_kXQBMMLacxhy468B489g9H_p1d6fFL481OL1VnUCz7KIEpK-m2IXJA1zeXxEBd82Mzg_4fvfXj5joQZXIH9xdE8C2vyqf3TfWvJt6Bf86UVHjIaGx1qmujz2oGHwsP2b_vcNxGSXu7t_yEIl3pqJqBWEqt_p_qzLRZi3oh0kkebgEBmGb9BRuChktJY4SXzvj8dvfFYDyPUrGBTsLSLNfU7QF_eNS7q3j9Ik7Pi6oLIfIwDNzifW8yZMIgGJF459VjX1HY9i15pDac1vKWdiiTz91dBbmQrpZ7AAsyyMyOjSJQ-PM_oInxjFrL_OVpKmlIusCXlxHQNqJxg3OwpmcHvtJBmYFo5kDukmcF0odvwuqBPoAuYJ6ry5DjvywuXAicMnRM6puxq9cJ96my5UxniVn0vJssyu-QRZfufMtY6NB45j1-nCLaQxLmLeDYEUJ0MKgmbM4VbX49bzT5j24UxHm77LQtaDitiXTHIwxdWc4tN1vR-VImU2kbiFcuqAwdC-e2Jahijzt0v7zPBFs__0SaGHV6nIel3hiL_q97m7CwomGDfEkSeys0cVYEmN6ii3cks=w802-h440-no)

port 번호 0번 ~ 1024는 유명한 서버들이 이미 번호가 할당 약속(표준화)되어 있다. 1025번 ~ 65000번에 해당되는 포트번호들은 표준되어 있지 않아서 필요한 장비에 필요한 번호를 고르면 된다.

```
$ sudo nano /etc/ssh/sshd_config # sshd_config에 포트번호 22 적혀있음
```

 sshd_config에 적혀 있는 포트 번호를 다른 포트 번호로 바꾸어서 사용가능하다. 

### 2) 포트 포워딩이란?

외부 사용자가 우리집에 있는 서버에 접속할 수 있게 하는 방법

![](https://lh3.googleusercontent.com/DFeJZzB5tukuGCyVVOa38OYjP2eAj8P3TjJTpX0R-LPj0gLIqQJ7Q1zSZhoCtyDNbKdp9upSP8Ku_P36XGCVl391MqcX3TE7DeIVTaq6BktRJgMuu7KsxHyRkfefe7O9S_r24_yZTzRRM-vWqlL9FlOjm96GV8ebGd0a-XP6nE8bStNebsszJ7nq_YP0XXNAq-duw1Sta-QGRPxIKzKeBCNWvm3RBUdFyBcFKaGDe47CYGdTsvkbNY_amLfW8wjaFWYNY_69nXLNIiVYZFa8TAzHNXTATKrB5FmiZ9E2R-FoZ4jR6o-HqjFgvdcHWTO_-ONQHbgtgfClq1Htl7q6chNLu0l24OFn7DitTo4sU--FGr_UZAVrkUAFa5Pldagd3XAWJTo0e0INx0no2u1_pVDd5tTGmtRIajjePLFJ7P4VtIyZz9upguxpZKXLK1FbdneLko2O6WOlY7z3QEE-1Poi3YFsM5_jlVSgb5mC38pvLzS2NB2xlVOG-AcLgozyz5Ns3TuabVT1cIbRprJWnIQwoDq_uW7JiX8wizY6cPed9DWJNb9qeYp1Zsnd6imJ5uWHy-WqwEdnTpIxFIZRv5Yj3tJU2kcBCFC0ioKY9ScJLEmUmabN8tvk382kM7YX0DtlIWPAZNgE4old_e7K3y_r18pZAGU=w802-h440-no)

- ISP : Internet Service Provider

외부 사용자가 211.46.24.39:9000 이라는 공유기의 9000번 포트로 접속 시도 하면, 공유기에 설정되어 있는 '9000번 포트 => 192.168.0.4:80'으로 192.168.0.4 (private address)의 웹서버 포트(80번 표준포트)로 접속하게 되어 있다. 그러면 해당 서버는 요청 정보를 외부 사용자가에 전송한다. 

- default gateway : 공유기가 가지고 있는 아이피를 지칭

### 3) 포트 포워딩 실습

```
$ ip addr # 자신의 아이피 주소 알아내기
```

```
$ ifconfig # 자신의 아이피 주소 알아내기
```

```
$ ip route # default gateway 아이피 주소(공유기 아이피 주소) 알아내기
```

- default gateway 아이피 주소(공유기 아이피 주소) 알아내기 #2<br/>
환경설정 - 네트워크 - 와이파이 - 고급 - tcp ip 선택 - router

- 웹브라우저에 해당 default gateway 아이피 주소 접속 : 설정화면

- 관리도구 - 로그인 - 고급설정 - nat 라우터 관리 - 포트 포워드 설정

- 내부아이피(private address) : 본인 아이피 적기

- 외부 포트 : 외부 사용자가 사용할 포트의 번호. 예) 9000

- 내부 포트 : 80번으로 설정 (웹서버 표준 번호)

- 외부 사용자가에게 public address와 9000번 포트를 알려준다.<br/>
예) 211.46.24.39:9000를 알려주고 웹브라우저에 211.46.24.39:9000접속

## 27. 도메인 (domain)

![](https://lh3.googleusercontent.com/Gm1nbAtEdEVsE7dC9QmLNx00pLYXV5TM3mYJL034hfY4zpkkKJ6jwttJ4I4I9F_Sozf8FWS2RAp_-XAbXAutQ-rMZpsPsZQpjpUEyKhKYjCvBtNYDk1-FR4Fbc8IMgznVE_fOIT2pclaCMJREuHGrCnW6-NcEHBxbp16rce_Yg5brwOu79kYc6Y3Dmh25SojENlfUaWuneYvicKdlrhBj13DAhAlfonBxiccldNLmNc8ODO9Vx2APLVoxewJNwaRZ6MhWfbl7NQ_7v_R5nB_ZVxMrkZTq4hcul59gzaFvk7kxzYbQvvkXjoInlzo3zbRXuPcjjQrMuYgFdvc_G7AnoIVoOoYx-rX2_9Drp1KD4P_AWRH44bFE4pblFywTQWFC0kZLlu2Y4AbMT2vwQcsZhKyV05xN3USfaGJH7nRjD9yuBltaFnqRRWoqscBrsMZz5BO7AjPN_dneIKEYSkIQZ00bCDavPdQSjsKTKLtRE4pqdiS6qAqsUjC23W0Tpv4KivQ_xADAHq1kAoiVusfC53o0U9pfL7p2yagp5Zrevpj9VSEMum_v4Q71pJ0yPjocnxaIakM5yzaRV6M3k2VmoV_so2vDYpUl31ePATUw-NDNfozfruNs_mgH3OnwY7eQsHUCkh0devdBmX69fH2gNVvTtIG99Y=w784-h429-no)

### 1) hosts 파일

- hosts 파일 : host(하나의 컴퓨터)들의 도메인과 IP 정보를 담은 파일
- host : 하나의 컴퓨터(client, server 등)
- network : 각각의 컴퓨터(host)를 묶었을 때
- internet : 수많은 network를 모두 모은 전체 집단

웹브라우저에 도메인을 입력하면 제일먼저 hosts파일로 가서 해당 도메인인과 아이피가 저장되어 있는지 확인하고 없으면 DNS로 가서 도메인과 IP를 찾는다. 만약 해당 도메인이 hosts파일에 있으면 해당 IP를 가져오고 DNS를 접속하지 않는다.

DNS(domain name server)가 있기 이전에는 hosts file에서만 도메인의 IP 정보를 찾았다.

```
$ elinks google.com #elinks 웹브라우저 모듈로 구글을 쉘환경에 연다.

$ elinks http://localhost/ #나의 컴퓨터로 접속
```

아래와 같이 하면, 구글에 접속했을 때 구글페이지가 열리는 것이 아니라 내가 원하는 웹페이지를 열수 있다.

```
$ sudo nano /etc/hosts #호스트 파일을 연다.


============================
127.0.0.1   localhost
127.0.1.1   ubuntu
127.0.0.1   google.com
============================

구글닷컴을 저장하면 구글 도메인으로 웹브라우저에 접속하면
localhostm 출력가 된다.
```

hosts파일은 해커들의 공격대상이 되기도 한다. 왜냐면 해커들이 도메인 정보를 바꾸어서 비슷한 웹페이지로 접속하게 만들어서 사용자 정보를 훔쳐간다.

### 2) 도메인 구입

#### (1) nameserver ( = DNS) IP 확인 하기

```
$ cat /etc/resolv.conf #nameserver IP가 적혀있는 파일 출력
```

도메인주소(url)를 IP주소로 변환시키는 과정이 필요한데, 이 일을 nameserver가 해준다. 네임서버가 도메인주소를 IP로 변환하는 과정을 resolution이라고 한다. 네임서버를 흔히 DNS(domain name server)라고도 부른다.

도메인 구입 사이트 : https://www.freenom.com/  무료도 있다.

```
$ ip addr # 자신의 아이피 알아내기 (private address)

$ curl ipinfo.io/ip # url 접속해서 아이피 알기 (public address)
```

#### 도메인과 아이피를 매칭시킬려면 curl을 통해 알아낸 자신의 public address를 써야한다.

![](https://lh3.googleusercontent.com/p6I_r36va2pp03XPld62oMz1dbBqW7rgwZEY_0TFJqHdRIt-yjumeoHrq1ylHSUUtHL2Bn6W1VdcSL37JYiSWrf4FBZshEppFmn-2bEaVyp3GlUzsO35u853IvGlSFngTZCHA7RdsbaUgBb840hFBTwkg71qJntVpvM8hA9f1j0_bGalmUgMU1xJxMFDzRGuZBOrvJX-E0EdQN_m1KVCYWJjKLpXPEF2CDqh8JoHC_ElGocUNGfy61HrhVXKWdmOiL0QIEwl8Dp8iPm6CxZwieapZLCUmEYFA0_cLeFftrtt1Cb0O1Cu4pXQZ7BrHDsKVUSiDqHCY0s-R8Rhl6J-4LOyTF1EfV04QMo4emaK8sm91wwdLzvan_lIdBcE9Wi281HEaxjNr4aEgj4pk-NF-4110ENu2dhRGsXXGIen21GxFDdx8tHhS8eR_lXLGqhHJwGBHY-ij1kUkK99_M2o6NQ5R0xwccdtKVFn42Bl1_IBuIFXn4QTTplu8lfIML1ozNCLDThg0TO0tBfl4rcEy3T_hZM5KR3NWVFEbcpDLtW_wmLJKM-K85CtmRp5EVjs9Rv-wD9adqHWf48nk3iAtfauf37lIn5Xr18RubNFuNJvH5sZpk6ji2P3_HtUNrnkxyEypcQtrDap1leKjR5_rNyzkVRDwck=w784-h429-no)

#### (2) 도메인을 잘만들었는지 IP 확인해보기

```
$ host ideajoon.com # 도메인의 아이피 주소를 알수있다.
```

### 3) 서브 도메인

![](https://lh3.googleusercontent.com/FkRuc-tPQEERb6G1jaCUY4RycCAosy812VJLLPBZoGR-Ak3ce20-dzW9Lg8NnKk_B1KxwzOCdRnqC16I5bZvojdh2Apa-1UP4DN42AJQQKT6OY1Kso_DVg8sbUDOhnA17JNGkqzQ0EzXGNxYGoBH6wSXJHc1v_iHZdl5agHaYcoSEIwQnl_nwEKefdyeB4a49GFHilBmb1fe9GO87tviuhhqO97Pgbipf_H8_XLWMe3069L-ZDzs-KMPAyW9z_F_9u92z1RJosKKR9lOdpzvxqUrJSPsLrR9ohJ4nzlQsJQk9N0RlTlzw5Xktj3SMd2Q1vB8KCB7422_nQ-8qQ95KWY4wbdMmXheTX_Zro-B6AlEWoOqnXOtBA2LA826LFGAwpqb6Fb0O9-aQ4-wCZ697AJu5cEXE0YI56m29RKrEJfyDfqkqPyRV2_Yu3TEsRS1GN5Jt6y4GvmE9ZR5qli-p_ab_hLK2tW-VOAn-OCebuSLAy8sardE5d9R7ytqpj0m06d6uhjDXkzUUGNwIzwRJqDxz3hipEfpyuSdjXt2cBBgZhPVw6tgX0M4psxeeUp6rECd75zIOmRm0k2Ne2yu1wz-xGr8ZEpZMm_jwPSaELerL6cJBFyEF2nqiNKk1YlhS1Z-uODGpTwTaqssII5SeERNGAo82IA=w784-h429-no)

각각의 서버 도메인의 아이피는 다르다.

### 4) DNS의 동작 원리

```
$ dig +trace ideajoon.com # 도메인 등록 의뢰 결과를 출력
```

root DNS 서버가 10대 이상으로 구성되어 있고 이것은 안정성을 위하여 전세계에 곳곳에 설치되어 있다.

## 28. 인터넷을 통한 서버간 동기화 (rsync)

인터넷을 통해서 컴퓨터와 컴퓨터의 파일을 동기화하는 방법인 rsync 대해서 알아봅니다. 

rsync 실습하기1<br/>
(한 컴퓨터내에서 파일을 한 디렉토리에서 다른 디렉토리로 복사)

```
$ mkdir rsysnc
$ cd rsync/
$ ls -al
$ mkdir dirl
$ mv dirl src
$ ls -al
$ mkdir dest
$ ls -al

$ cd src
$ touch test{1..10} #test1, test2 ... test10, 총 10개의 빈파일 생성
$ cd ..

$ rsync -a src dest #dest 디렉토리 안에 src라는 디렉토리가 생성
$ rm -rf dest/src #묻지도말고 dest안의 src폴더를 삭제

$ rsync -a src/ dest #dest 디렉토리 안에 src 안의 모든 파일이 전부 복사
$ ls -al dest

$ rsync -av src/ dest #dest 디렉토리에 없는 파일만 src에서 모두 복사
```

rsync 명령어는 이미 있는 파일은 제외하고 없는 파일만 골라서 복사하기 (효율적)

- -a : archive mode로 동작한다는 옵션 (디렉토리 안의 모든 파일을 전송)
- -av : 다 출력해라

rsync 실습하기2<br/>
(두대의 컴퓨터 파일을 한 컴퓨터에서  다른 컴퓨터로 복사)

```
$ ip addr

$ rsync -azP ~/rsync/src/ ideajoon@192.168.0.65:~/rsync/dest
```

- -az : 파일을 전송할 때 압축해서 보낸다.
- -azP : 전송되는 상황을 Progress bar 로 보여준다.
- ~/rsync/src/ : 자신의 홈폴더의 rsync폴더의 src 폴더안에 모든 파일
- ideajoon@192.168.0.65:~/rsync/dest : ideajoon 컴퓨터의 dest 폴더에

백업등을 할때는 rsync 기능이 필수적으로 사용된다.

## 29. 로그인 없이 로그인 하기 (ssh key)

ssh, rsync, git와 같은 기술을 사용할 때 로그인이 번거로우신가요? 보다 안전한 방법으로 인증하고 싶으신가요? 두가지 고민을 한꺼번에 해결하는 방법이 있습니다. ssh 공개키를 이용하면 편의성과 보안성 모두를 높일 수 있습니다.여기서는 ssh공개키를 이용해서 자동 로그인을 하는 방법을 알아보겠습니다. 

### 1) 다른 컴퓨터에 로그인 없이 로그인 하는 설정 방법

#### (1) ssh-keygen으로 본인 컴퓨터에 id_rsa & id_rsa.pub 생성하기

```
$ ip addr

$ ssh ideajoon@192.168.0.65 # ideajoon 리눅스에 로그인하기, 비번입력

$ ssh-keygen 
# ssh-key를 생성하겠다는 의미, 비번 안만들어도 된다.
# /home/ideajoon/.ssh/ 폴더안에 id_rsa, id_rsa.pub 파일이 생성된다.
# id_rsa는 private key가 있고 id_rsa.pub는 public key가 있다.
# id_rsa 파일은 절대로 외부에 노출되면 안된다.
```

#### (2) 접속하고자 하는 컴퓨터(ideajoon)에  authorized_key가 있다.

```
# 다른 컴퓨터에서

$ cd ~/.ssh 
#home 디렉토리의 ssh 디릭토리에 들어간다.
#ssh 폴더에는 authorized_keys(인증된 키)라는 파일이 있다.
```

#### (3) id_rsa.pub파일안 정보를 authorized_keys파일안에 복사하기 (append)

```
$ ssh-copy-id ideajoon@192.168.0.65 
#접속하고자 하는 pc의 비번을 물어보고 입력 한다.
#즉, authorized_keys파일 안에 정보끝에다가 id_rsa.pub파일 정보가 복사됨
```

id_rsa.pub파일 안에 있는 정보를 authorized_keys파일 안에 정보끝에다가 append 한다. 그러면 접속하고자 하는 PC(ideajoon@192.168.0.65)에 로그인 없이 로그인이 가능하다.

### 2) 로그인 없이 자동으로 동기화 하기

```
$ mkdir rsync3
$ cd rsync3
$ touch test{1..100} #test1...test100, 100개의 빈 파일이 생성
$ ls -al 

$ rsync -avz . ideajoon@192.168.0.65:~/rsync_welcome
```

- -avz : archive mode로 전부출력하고 파일을 압축해서
- . : 현재폴더 모든 파일을
- ideajoon@192.168.0.65 : 접속하고자 하는 컴퓨터
- ~/rsync_welcome : 홈 폴더의 rsync_welcome 디렉토리에

#### clone 이란 명령어를 사용하여 주기적으로 rsync 명령어를 실행시켜서 동기화 할 수 있다.

### 3) RSA (암호와 기법)

- 암호화(encrypt) : 키를 가지고 정보를 아무도 못 알아보게 바꾸는 방법
- 복구화(decrypt) : 키를 가지고 못알아보는 정보를 알아보게 복구하는 방법

만약 해당 키가 없으면 암호화, 복구화를 진행할 수 없다.

- 대칭 암호화 기법 : 키가 암호와할때 복구화 할때 같을 때
- 비대칭 암호화 기법 : 암호화 할때는 private key, 복구화 할때는 public key로만 실행 가능할 때

#### 다른 PC에 로그인 없이 로그인하기 동작 원리

1. client가 server에 접속
2. server가 random key값을 client에게 전송
3. client가 random key값을 private키값을 이용해 암호화 한 후 server에게 전송
4. server가 전송받은 암호화 키값을 기존에 가지고 있던 client의 public key값을 이용해 복호화해 client에게 전송
5. client가 처음에 받은 random key값과 마지막으로 서버가 public key로 복호화해 client에게 전송한 key 값이 같으면 연결성공

## 30. 연속적으로 명령 실행시키기 (;과 &와 &&의 차이)

### 1) CLI의 가치

명령을 통해서 컴퓨터를 제어하는 중요한 이유 중의 하나는 해야 할 일을 순서대로 배치해서 자동화된 처리를 할 수 있다는 점입니다. 정확한 작업을 위해서는 명령어와 명령어를 연결하는 구분자를 잘 이해하셔야 합니다. 언어로치면 접속사와 같은 역할을 하는 것입니다. 여기서는 이 접속사들을 정리해봅니다. 

### 2) 결론

- ';' 기호는 앞의 명령어가 실패해도 다음 명령어가 실행
- '&&' 기호는 앞의 명령어가 성공했을 때 다음 명령어가 실행
- '&' 기호는 앞의 명령어를 백그라운드로 돌리고 동시에 뒤의 명령어를 실행

#### (1) ; 기호

한 줄에 여러 명령어를 순서대로 배열할 때는 ;를 구분자로 사용합니다. 아래 명령어는 test를 만든 후에 test 디렉토리로 이동합니다. 

```
$ mkdir test;cd test
```

#### (2) && 기호

&&는 앞의 명령어가 실행되었을 때 성공한 경우에 다음 명령어를 실행합니다. ;와는 다릅니다. 대체로 &&를 쓰는게 좋을 때가 많습니다. 좀 더 정확하게는 &&는 이전 명령어의 실행결과가 참(true)일 때만 다음 명령을 실행합니다. 

```
$ mkdir test&&cd test
```

#### (3) & 기호

&는 명령어를 백그라운드로 동작시킬 때 사용합니다. 

mkdir test & cd test를 실행하면 아래와 같은 결과가 나옵니다. 

```
[1] 19989
cd: no such file or directory: test
[1]  + 19989 done       mkdir test
```

test 디렉토리를 백그라운드로 생성함과 동시에 test 디렉토리로 이동하려고 했기 때문에 cd test는 존재하지 않는 디렉토리로 진입하려고 시도하기 때문입니다. 한편, test 디렉토리는 생성됩니다. 

### 3) 명령어의 반환값 알아내기

리눅스(유닉스)의 모든 명령어는 종료할 때 성공 여부를 알려줍니다. 예를들어보죠. 

test 디렉토리가 없는 곳에서 아래 명령을 실행해보세요. 성공했을 때 어떻게 되는지 보시죠. 

mkdir test

그리고 아래 명령을 실행해보세요. 

```
$ echo $? # 이 명령어는 이전 명령어가 반환한 값을 알아내기
```

이 명령어는 이전 명령어가 반환한 값을 알아내는 것입니다. 결과는 아래와 같습니다. 

0

반대로 test 디렉토리가 이미 있는데 mkdir test를 실행한 후에 echo $?를 실행하면 아래 값이 출력됩니다. 

1

또는 존재하지 않는 명령어를 실행하면 127이 출력될꺼예요. 즉 리눅스에서는 0이 아닌 값은 실패(false)를 의미합니다. 

### 4) 명령의 그루부핑 {}

명령을 그룹핑 할 수도 있습니다. 아래 명령은

```
$ mkdir test3 && { cd test3; touch abc; echo 'success!!' } || echo 'There is no dir';
```

- mkdir test가
- 성공했을 때 cd test2; touch abc를 실행하고 success!!를 출력합니다. 
- 실패했을 때 echo 'There is no dir'를 실행합니다. 
- 이때 실행되는 명령들은 현재 쉘의 컨텍스트에서 실행됩니다. 
- 만약 서브 - 컨텍스트에서 실행하고 싶다면 '('와 ')'를 사용하시면 됩니다.
