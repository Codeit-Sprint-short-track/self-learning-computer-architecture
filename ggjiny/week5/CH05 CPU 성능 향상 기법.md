# Ch05 CPU 성능 향상 기법

# 05-1 빠른 CPU를 위한 설계 기법

## 클럭

- 컴퓨터 부품들은 ‘클럭 신호’에 맞춰 일사불란하게 움직인다
- CPU는 명령어 사이클이라는 정해진 흐름에 맞춰 명령어들을 실행한다

클럭속도가 높은 CPU는 성능이 좋음

→ 클럭 속도는 CPU 속도 단위로 간주됨

### 클럭 속도

- 헤르츠(Hz) 단위로 측정
- 1초에 클럭이 몇 번 반복되는지

클럭 속도만으로 CPU의 성능을 올리는 것엔 한계가 있음

## 코어와 멀티 코어

### 코어

- CPU 내에서 명렁어를 실행하는 하드웨어 부품
- CPU는 명령어를 실행하는 부품을 여러 개 포함하는 부품
  - = **멀티코어 CPU, 멀티코어 프로세스**

## 스레드와 멀티 스레드

### 스레드

- 실행 흐름의 단위
- 명령어를 실행하는 단위
- CPU에서 사용되는 하드웨어적 스레드
- 프로그램에서 사용되는 소프트웨어적 스레드

### 하드웨어적 스레드

- 하나의 코어가 동시에 처리하는 명령어 단위
- 하나의 코어로 여러 명령어를 동시에 처리하는 CPU를 **멀티 스레드 프로세서, 멀티스레드 CPU**라고 함

### 소프트웨어적 스레드

- 하나의 프로그램에서 독립적으로 실행되는 단위

### 멀티스레드 프로세서

- 하나의 코어로 여러 명령어를 동시에 처리하도록 만들려면 레지스터를 여러개 가지고 있어야함
- 하드웨어스레드를 논리 프로세서라고 부르기도 함

# 05-2 명령어 병렬 처리 기법

### 명령어 병렬 기법

- 명령어를 동시에 처리하여 CPU를 한시도 쉬지 않고 작동시키는 기법
- 명령어 파이프라이닝, 슈퍼스칼라, 비순차적 명령어 처리

## 명령어 파이프라인

명령어 파이프라이닝

- 동시에 여러 개의 명령어를 겹쳐 실행하는 기법

파이프라인 위험

- 특정 상황에서 성능 향상에 실패
- 데이터 위험, 제어 위험, 구조적 위험

### 데이터 위험

- 명령어 간 데이터 의존성에 의해 발생

### 제어 위험

- 분기 등으로 인한 프로그램 카운터의 갑작스러운 변화에 의해 발생
- 이를 위해 **분기 예측** 사용
  - 프로그램이 어디로 분기할지 미리 예측한 후 그 주소를 인출하는 기술

### 구조적 위험

- 명령어들을 겹쳐 실행하는 과정에서 서로 다른 명령어가 동시에 ALU, 레지스터 등과 같은 CPU 부품을 사용하려고 할 때 발생
- **자원 위험**이라고도 부름

## 슈퍼스칼라

- CPU 내부에 여러 개의 명령어 파이프라인을 포함한 구조
- CPU → 슈퍼스칼라 프로세서, 슈퍼스칼라 CPU

## 비순차적 명령어 처리 OoOE

- 명령어들을 순차적으로 실행하지 않는 기법
- 명령어의 합법적인 새치기
- 명령어를 순차적으로만 실행하지 않고 순서를 바꿔 실행해도 무방한 명령어를 먼저 실행하여 명령어 파이프라인이 멈추는 것을 방지하는 기법

# 05-3 CISC와 RISC

## 명령어 집합

- CPU가 이해할 수 있는 명령어들의 모음
- = 명령어 집합 구조(Instruction Set Architecture) **ISA**
  - CPU의 언어이자 하드웨어가 소프트웨어를 어떻게 이해할지에 대한 약속

## CISC

- Complex Instruction Set Computer
- 복잡한 명령어 집합을 활용하는 컴퓨터(CPU)
- **가변 길이 명령어** 활용
- 메모리 공간 절약 가능
- 활용하는 명령어가 복잡하고 다양한 기능을 제공하기 때문에 명령어의 크기와 실행되기까지의 시간이 일정하지 않음
- 복잡한 명령어 때문에 명령어 하나를 실행하는데 여러 클럭 주기를 필요로함

### CISC의 한계가 준 교훈

- 빠른 처리를 위해 명령어 파이프라인 십분 활용해야함
- 원활한 파이프라이닝을 위해 명령어 길이와 수행 시간이 짧고 규격화 되어있어야 함
- 자주 쓰이는 명령어만 줄곧 사용. 복잡한 기능을 지원하는 명령어를 추가하기보다 자주 쓰이는 기본적인 명령어를 작고 빠르게 만드는 것이 중요

## RISC

- Reduced Instruction Set Computer
- 짧고 규격화되니 명령어, 되도록 1클럭 내외로 실행되는 명령어 지향
- **고정 길이 명령어** 활용
