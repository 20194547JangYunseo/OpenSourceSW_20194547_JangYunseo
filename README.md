# 오픈소스 SW 개론 과제 #2
## 리눅스 명령어
### top
* table of process
* 유닉스 계열 운영체제에서 볼 수 있는 작업 관리자 프로그램
* 시스템의 상태를 실시간으로 전반적인 상황을 가장 빠르게 모니터링 가능
* 옵션 없이 입력하면 기본 3초로 화면을 갱신하며 정보를 보여줌
* 사용자 지정 기준에 따라 선택된 실행 중인 프로세스의 목록을 순서대로 보여줌

  (기본 순서는 CPU 사용률이며, 오직 최상위 CPU 소비 항목들만이 표기됨)
  
<img src="https://github.com/20194547JangYunseo/OpenSourceSW_20194547_JangYunseo/blob/main/img/top.png?raw=true" width="70%" height = "70%">

#### top 요약 출력 항목

|항목|설명|
|:---:|:---:|
|xx:xx|시스템의 현재 시간과 OS가 살아있는 시간을 나타내는 영역|
|users|현재 접속 중인 유저 섹션 수|
|load average|1분, 5분 그리고 15분 동안 CPU Load의 이동 평균|
|Tasks|현재 프로세스들의 상태|
|%Cpu(s)|CPU의 사용율을 보여주는 영역|
|Mem|물리적 메모리|
|Swap|가상 메모리|

**top 세부 정보 필드별 항목**

|항목|설명|
|:---:|:---:|
|PID|Process ID이며, 프로세스를 구분하기 위한 겹치지않는 고유한 값|
|USER|해당 프로세스를 실행한 USER 이름 또는 효과를 받는 USER의 이름|
|PR|커널에 의해서 스케줄링되는 우선순위|
|NI|PR에 영향을 주는 nice라는 값|
|VIRT|프로세스가 소비하고 있는 총 메모리(프로그램이 실행중인 코드, heap, stack과 같은 메모리, IO buffer 메모리를 포함)|
|RES|RAM에서 사용중인 메모리의 크기|
|SHR|다른 프로세스와의 공유메모리(Shared Memory)|
|%MEM|RAM에서 RES가 차지하는 비율|
|S|프로세스의 현재 상태|
|TIME+|프로세스가 사용한 토탈 CPU 시간|
|COMMAND|해당 프로세스를 실행한 커맨드|

**top 실행 전 옵션**

||설명|
|:---:|:---:|
|-b|배치모드로 정보 출력|
|-d|지정한 시간(초) 간격으로 업데이트 시간 변경하여, 정보를 업데이트하여 출력|
|-n|실행 주기를 설정하여, 업데이트 정보 출력|
|-p|지정된 Process ID만 출력|
|-s|몇 개의 대화식 명령을 비활성화(시큐어 모드)|
|-S|누적된 정보를 출력(cumulative 모드)|

**top 실행 후 명령어**

|명령어|설명|
|:---:|:---:|
|M|메모리 사용률 내림차순 정렬|
|N|Process ID별 정렬|
|P|CPU 사용률 내림차순 정렬|
|S|cumulative 모드 선택/해제|
|T|프로세스가 돌아가고 있는 시간 순 정렬|
|space|정보 업데이트|
|f|화면에 표시될 프로세스 관련 항목 설정|
|i|idle 프로세스 정보 출력/해제|
|h or ?|사용 가능한 명령어 출력|
|k|프로세스 종료, 종료할 PID 입력 후 signal은 9로 대입|
|m|메모리 정보 출력/해제|
|q|top 종료|
|1|CPU Core별로 사용량 정보 출력|

---
### ps
* process status
* 현재 실행중인 프로세스 목록과 상태를 확인할 수 있는 명령어
* OS 계열에 따라 명령어 사용법이 다름

|OS|사용법|
|:---:|:---:|
|Unix Option|명령어 앞에 '-' (dash) 추가|
|BSD Option|명령어 앞에 '-' 를 붙이지 않음|
|GNU Option|명령어 앞에 '--' (double dash)추가|

<img src="https://user-images.githubusercontent.com/97163113/172037232-a0f3481d-8f58-46a2-bc8e-546ac576ed42.png" width="50%" height = "50%">

**ps 항목**

|항목|설명|
|:---:|:---:|
|PID|Process ID|
|TTY|터미널|
|TIME|CPU 점유 시간|
|CMD|프로세스가 수행된 명령어|

이외에도 명령어를 통해 더 많은 항목을 볼 수 있음
|항목|설명|
|:---:|:---:|
|USER|프로세스 소유자의 이름(BSD)|
|UID|프로세스 소유자의 이름(SYSTEM V)|
|PPID|부모 Process ID|
|%CPU|CPU 사용 비율의 추정치(BSD)|
|%MEM|메모리 사용 비율의 추정치(BSD)|
|VSZ|K단위 또는 페이지 단위의 가상메모리 사용량|
|RSS|실제 메모리 사용량|
|S, STAT|현재 프로세스의 상태 코드(S: SYSTEM V, STAT: BSD)|
|STIME|프로세스가 시작된 시간 혹은 날짜|
|C, CP|짧은 기간 동안의 CPU 사용률(C: SYSTEM V, CP: BSD)|
|F|프로세스 플래그|
|PRI|실제 실행 우선순위|
|NI|nice 우선순위 번호|

**ps 옵션**

|옵션|설명|
|:---:|:---:|
|-e|커널 프로세스를 제외한 모든 프로세스 출력|
|-f|풀 포맷으로 보여주며, 유닉스 스타일로 출력|
|-l(sys V), l(BSD)|긴 포맷으로 보여주며, 우선순위와 관련된 PRI와 NNI값을 확인 가능|
|-p|특정 PID의 프로세스 정보 출력|
|-u [사용자이름]|특정 사용자의 모든 프로세스 정보 출력, 사용자를 지정하지 않으면 현재 사용자를 기준으로 출력|

_이외에도 많은 옵션이 있지만, 실제로는 grep 명령어와 함께 사용하기 때문에 잘 사용하지 않음_

* System V 계열에서는 ps -ef를 가장 많이 사용 (`ps -ef |grep '프로세스명'`)
* BSD 계열에서는 ps aux를 가장 많이 사용 (`ps aux | grep '프로세스명'`)

---
### jobs
* 백그라운드로 실행되는 프로세스 또는 현재 중지된 프로세스 목록을 출력
* `jobs [옵션] [작업번호]`

**jobs 백그라운드 작업 상태**

|상태|설명|
|:---:|:---:|
|Running|작업이 일시 중단되지 않고, 계속 진행 중|
|Done|작업이 완료되어 0을 반환하고 종료함|
|Done(code)|작업이 정상적으로 종료되었으며, 0이 아닌 코드를 반환|
|Stopped|작업 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업 일시 중단함|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업 일시 중단함|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업 일시 중단함|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업 일시 중단함|

**jobs 옵션**

|옵션|설명|
|:---:|:---:|
|-l|Process ID state 필드 앞에 출력|
|-p|해당 작업의 대표 Process ID만 나열하여 한 행씩 출력|
|-n|프로세스 그룹 중 대표 Process ID를 출력|
|command|지정 명령어 실행|

