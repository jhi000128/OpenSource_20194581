# 오픈소스 조사내용 README 파일로 정리하기


## 리눅스 명령어 (top, ps, jobs, kill)


### top
* __시스템의 상태를 전반적으로 가장 빠르게 파악 가능하다.__ (CPU, Memory, Process)
* 옵션 없이 입력하면 interval 간격으로 화면을 갱신하며 디스크 사용량은 없다.
* __top은 proc에서 일정 주기로 합산해 cpu 사용률 출력__
  * proc에서 일정 주기로 체크한 결과를 보여줌


* top 실행 전 옵션
  
|명령어       | 내용                |
| :-------:  | :-----------------: |
| -n | top 실행 주기 설정(반복 횟수) |
| -b | 배치모드 옵션|
| -p | process ID|

* top 실행 후 명령어 

|명령어       | 내용                                         |
| :-------:  | :--------------------------------------:     |
|shift + p   | CPU 사용률이 높은 프로세스 순서대로 표시        |
|shit + m    | 메모리 사용률이 높은 프로세스 순서대로 표시      |
|shift + t   | 프로세스가 돌아가고 있는 시간이 큰 순서대로 표시 |
|shift + b   |상단의 uptime 및 기타 정보값을 블락선택해 표시   |
|f           |화면에 표시될 프로세스 관련 항목 설정            |
|i           |idle 또는 좀비 상태의 프로세스는 표시 되지 않음  |
|z           | 출력 색상 변경                                |
|d [sec]     |설정된 초단위로 Refresh                        |
|q	          |명령어 종료                                    |
|1           |CPU Core별로 사용량 보여줌                      |

<br/>

### ps
* process status의 줄인말
* __현재 실행중인 프로세스 목록과 상태를 보여준다.__
* 옵션 없이 사용하면 현재 셸이나 터미널에서 실행한 사용자 프로세스에 대한 정보를 출력한다.
* __ps는 ps한 시점에 proc에서 검색한 cpu 사용량__
  * ps 명령어를 친 시점에서 proc이라는 가상 파일시스템을 검색한 결과

* 사용법
  * __ps [option]__

* 옵션

|명령어      | 내용                                                    |
| :-------:  | :--------------------------------------:                |
|-e |실행중인 모든 프로세스의 정보를 출력|
|-a |세션 리더를 제외하고 터미널에 종속되지 않은 모든 프로세스의 정보를 출력|
|-f |프로세스에 대한 자세한 정보를 출력 (PPID 확인 가능)|
|-u [사용자이름] |특정 사용자에 대한 모든 프로세스의 정보를 출력|
|-t |프로세스의 자세한 정보를 출력|
|-p pid |pid로 지정한 프로세스의 정보를 출력|
|u |프로세스 소유자의 이름, CPU 사용량, 메모리 사용량 등 상세 정보를 출력|
|a |터미널에서 실행한 프로세스의 정보를 출력|
|x |실행 중인 모든 프로세스의 정보를 출력|
<br/>

### jobs
* 백그라운드로 실행되는 __작업목록(작업번호, 상태, 명령어)__ 을 보여준다.
  * 작업이 중지된 상태, 백그라운드로 진행중인 작업 상태, 변경되었지만 보고되지 않은 상태 등
  * 여기서 작업번호는 PID와는 달리, 별도로 부여되는 백그라운드 작업목록 상의 번호이다.
* 작업목록은 현재 쉘 세션에 딸린 것으로 다른 세션과는 독립적이다.
* __리눅스 kill 명령어 뒤에 %작업번호 를 입력하여 종료시킬 수 있다.__

* 사용법
  * __jobs [option]__
  
* 옵션

|명령어       | 내용                           |
| :-------:  | :-----------------:            |
| -l | 프로세스 그룹 ID를 state 필드 앞에 출력| 
| -n | 프로세스 그룹 중에 대표 프로세스 ID를 출력| 
| -p | 각 프로세스 ID에 대해 한 행씩 출력| 
| command | 지정한 명령어를 실행| 

* jobs로 알 수 있는 세션의 상태 값


|상태명      | 의미                                                                |
| :-------:  | :-----------------:                                                |
| Running | 작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중임| 
| Done | 작업이 완료되어 0을 반환하고 종료 했음을 의미| 
| Done(code) | 작업이 정삭적으로 완료되었으며, 0이 아닌 코드를 반환 했음을 의미| 
| Stopped | 작업이 일시 중단| 
| Stopped(SIGTSTP) | SIGTSTP 신호가 작업을 일시 중단| 
| Stopped(SIGSTOP) | SIGSTOP 신호가 작업을 일시 중단| 
| Stopped(SIGTTIN) | SIGTTIN 신호가 작업을 일시 중단| 
| Stopped(SIGTTOU) | SIGTTOU 신호가 작업을 일시 중단| 

<br/>

### kill
* 프로세스에 특정한 __시그널(Signal)__ 을 보내는 명령어
* 옵션 없이 실행하면 프로세스에 종료 신호(15, TERM. SIGTERM)을 보낸다.
* __보통 중지시킬 수 없는 프로세스를 종료시킬 때 사용한다.__

* 사용법
  * __kill [option] [signal] [PID 또는 %Job_Number]__

* 옵션

|명령어       | 내용                |
| :-------:  | :-----------------: |
| -l | 시그널의 종류 출력| 
| -s signal | 시그널의 이름을 지정| 

* 주요 시그널

|시그널명       | 의미                                    |
| :-------:  | :-----------------:                       |
| SIGHUP | 세션이 종료될 때 시스템이 내리는 시그널| 
| SIGINT | Ctrl + C, 종료 요청 시그널| 
| SIGKILL | 강제 종료 시그널| 
| SIGSEGV | 메모리 침범이 일어날 때 시스템이 보내는 시그널| 
| SIGTERM | 기본 값, 종료 요청 시그널| 
| SIGTSTP | Ctrl + Z 일시 중지 요청 시그널| 

<br/>

---
<br/>

## vim 에디터에서 매크로 사용방법 (q, @)

* __매크로 : 특정한 움직임 또는 입력을 키에 저장함으로써 단순하면서 반복되는 동작을 쉽고 빠르게 해주는 것__

<br/>

### 기본적인 매크로 사용 방법

![매크로 이미지](https://github.com/jhi000128/OpenSource_20194581/blob/main/%EB%A7%A4%ED%81%AC%EB%A1%9C.PNG)

<br/>

### 자주 사용되는 매크로 등록 방법

1. ~/.vimrc 를 연다.
2. let @a = '매크로 문자열' : 매크로로 동작시킬 문자열을 입력

<br/>

### 매크로 문자열을 편집기에 그대로 출력하는 방법 

* 첫 번째 방법 : 편집 모드에서 ctrl + r, ctrl + r, 매크로 문자  를 순서대로 입력하면 그대로 출력된다.
  * 방향키 등의 특수키 문자가 제대로 붙여넣기가 되지 않음
* 두 번째 방법 : 커맨드 모드에서 매크로문자p 를 입력하여 래지스터로부터 바로 붙여넣기 한다. (ex: "ap, "bp, "cp, "dp, ...)
  * 출력 결과물이 같아보이지만 실제 바이너리를 뜯어보면 다르게 출력됨을 알 수 있음
