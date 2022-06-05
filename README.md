# 오픈소스 조사내용 README 파일로 정리하기


## 리눅스 명령어 (top, ps, jobs, kill)

### top
* 시스템의 상태를 전반적으로 가장 빠르게 파악 가능하다. (CPU, Memory, Process)
* 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여준다.
* top은 proc에서 일정 주기로 합산해 cpu 사용율 출력


* top 실행 전 옵션
  * 순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)
  * -n : top 실행 주기 설정(반복 횟수)

* top 실행 후 명령어 
  * shift + p : CPU 사용률 내림차순
  * shit + m : 메모리 사용률 내림차순
  * shift + t : 프로세스가 돌아가고 있는 시간 순
  * k : kill. k 입력 후 PID 번호 작성. signal은 9
  * f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
  * a : 메모리 사용량에 따라 정렬
  * b : Batch 모드로 작동
  * 1 : CPU Core별로 사용량 보여줌


### ps


### jobs


### kill



## vim 에디터에서 매크로 사용방법 (q, @)

### q


### @
