# Chapter 5. CPU 성능 향상 기법

### 목표
- 빠른 CPU를 위한 설계 기법을 학습한다.
- 빠른 CPU를 위한 명령어 병렬 처리 기법을 학습한다.
- RISC와 CISC의 차이에 대해 이해한다.

### 05-1 빠른 CPU를 위한 설계 기법

#### 1. 클럭
- **클럭 속도**: Hz 단위로 측정, CPU 성능에 영향

#### 2. 코어
- 명령어를 실행하는 부품

#### 3. 멀티코어
- 여러 개의 코어를 포함한 CPU

#### 4. 스레드 (Thread)
- 실행 흐름의 단위
  - **하드웨어적 스레드**: CPU에서 사용 (ex. 하이퍼스레딩)
  - **소프트웨어적 스레드**: 프로그램에서 사용

### 05-2 명령어 병렬 처리 기법

#### 1. 명령어 병렬 처리 기법 (Instruction-Level Parallelism)
- **명령어 파이프라이닝**: 여러 명령어를 동시에 처리하여 효율성 극대화
  - **단계**: 인출 → 해석 → 실행 → 결과 저장
- **슈퍼스칼라**: 여러 개의 파이프라인을 동시에 사용
- **비순차적 명령어 처리**: 순서를 바꿔도 되는 명령어를 먼저 처리

#### 2. 파이프라인 위험 (Pipeline Hazards)
- **데이터 위험**: 명령어 간 데이터 의존성에 의해 발생
- **제어 위험**: 분기 명령어에 의해 발생 (분기 예측으로 해결)
- **구조적 위험**: 자원 충돌로 발생 (ex. ALU, 레지스터 동시 사용)

### 05-3 CISC와 RISC

#### 1. 명령어 집합 구조 (Instruction Set Architecture, ISA)
- CPU가 이해할 수 있는 명령어들의 집합

#### 2. CISC (Complex Instruction Set Computer)
- 복잡한 명령어 집합을 사용하는 CPU (예: x86, x86-64)
- **가변 길이 명령어**: 명령어 형태와 크기가 다양
- **장점**: 메모리 절약에 효과적

#### 3. RISC (Reduced Instruction Set Computer)
- 단순한 명령어 집합을 사용하는 CPU
- **고정 길이 명령어**: 단순하고 적은 명령어 집합
- **장점**: 파이프라이닝 효율성 높음, 메모리 접근 최소화

| CISC                          | RISC                          |
|------------------------------|-------------------------------|
| 복잡하고 다양한 명령어          | 단순하고 적은 명령어           |
| 가변 길이 명령어                | 고정 길이 명령어               |
| 다양한 주소 지정 방식           | 적은 주소 지정 방식            |
| 프로그램 명령어 수 적음          | 프로그램 명령어 수 많음         |
| 여러 클럭에 걸쳐 명령어 수행     | 1 클럭 내외로 명령어 수행      |
| 파이프라이닝 어려움              | 파이프라이닝 쉬움              |
