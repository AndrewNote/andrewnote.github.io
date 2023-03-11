# 동시성 프로그래밍
- 모든 Task(작업)를 하나의 Thread가 아닌 여러개의 Thread가 처리하기 때문에 효율적으로 Task(작업)을 처리할 수 있음
- 효율적으로 Task(작업)를 처리한다면 Software가 더 자연스럽게 동작할 수 있음 **(최적화)**
- 자연스럽게 동작한다는건 Software의 사용성과 반응성이 좋아진다고 볼 수 있음

<br />

## Core
- CPU(Central Processing Unit)에서 실제 Task(작업)을 처리함
- 한번에 한가지 Task(작업) 처리
- Core가 여러 개라면 여러개의 Task(작업)를 동시에 처리할 수 있다
- SingleCore는 동시에 여러 Task(작업)를 하는 것처럼 보이지만 실제로는 짧은 단위로 여러가지 Task(작업)를 번갈아가면서 함
-- ex) 음악을 들으며 게임을하고 있는데 카톡 메세지 알림을 받는다
- _Core가 2개 이상일 경우 어떤 Core가 Task(작업)를 할지 분배하는 과정에서 딜레이가 발생할 수 있으므로 SingleCore가 더 효율적인 상황이 발생할 수 있다._
- _또는 SingleCore에만 최적화된 Software도 있을 수 있다_

<br />

## Thread
1. Hardware Thread
- **논리적인 Core**
- Hyper-Threading Technology: 하나의 Core에서 둘 이상의 Thread를 실행할 수 있는 기술
- 1Core 2Thread라면 실제로 Core는 1개지만 Core가 2개인 것처럼 작업을 처리함.

2. Software Thread
- **논리적인 Thread**
- Process 내부에서 작업 되는 가상의 Thread
- Thread는 Program의 Task(작업)를 처리함
- Multi Thread: 여러 Thread를 이용하여 여러 작업을 동시에 처리함

<br />

## Parallel Programming(병렬 프로그래밍)
- **Multi Core**
- OS가 자동으로 처리해줌
- 여러 개의 Core(CPU)가 **하나의 Task(작업)을** 분담해서 처리
    ~~여러개의 Core가 각각 하나의 Task(작업)을 수행하는건 병렬 프로그래밍이 아님~~
- 실제 고해상도 그래픽처리나 Machine Learning처럼 많은 연산이 요구되는 Task의 경우 Parallel Programming(병렬 프로그래밍)을 사용
- 물리적으로 Core(CPU)가 2개 이상 있을 때만 가능 ~~SingleCore는 불가능~~

<br />

## Concurrency Programming(동시성 프로그래밍)
- **Multi Thread**
- 여러개의 Task(작업)을 나열해두고 하나씩 번갈아가면서 Task(작업)을 처리하는 것
- SingleCore에서도 가능

<br />

## Serial Programming(직렬성 프로그래밍)
- Concurrency Programming(동시성 프로그래밍)과 반대되는 개념
- 단 하나의 Thread에서만 Task(작업)
- iOS에서는 Main Thread에서 Task(작업)
- 모든 Task(작업)을 순서대로 처리해야 함

<br />

## Synchronous(동기)
- 하나의 Task(작업)가 끝나기를 기다렸다가 다음 Task(작업)을 처리
- 실행 종료 시점을 알 수 있음 / 자원을 비효율적으로 사용 / Task(작업)이 단순해짐
- Blocking: Synchronous(동기)에서 Task(작업)이 끝날때까지 기다리는 상태
- 순차적으로 실행을 해야 하는 경우 꼭 사용해야함
    ex) A와 B순으로 작업을 할 때 B가 A를 참조하거나 A의 값이 필요로 할 때 A의 Task(작업)을 끝내고 B를 실행하도록 해야함

<br />

## Asynchronous(비동기)
- 하나의 Task(작업)가 끝나기전에 다음 Task(작업)을 처리
- 실행 종료 시점을 알 수 없음 / 자원을 효율적으로 사용 / Task(작업)가 복잡해짐
- Non-blocking: Asynchronous(비동기)에서 Task(작업)이 끝날때까지 기다리지 않는 상태

<br />

## GCD(Grand Central Dispatch)
- 직접 Core와 Thread를 관리하지 않아도 시스템에서 관리해줌
- Multi Core / Multi Thread에 최적화

<br />

## DispatchQueue
- `대기열에 보내다`라는 뜻
- GCD를 사용하기 위한 대기열
- FIFO(First In, First Out)로 작업을 처리
- SingleThread를 사용할것인가 MultiThread 사용할것인가(Serial / Concurrent) 선택
- sync / asycn 에서 선택 
```swift
DispatchQueue(label: "Serial")
DispatchQueue.main

DispatchQueue(label: "Concurrent", attributes: .concurrent)
DispatchQueue.global()
```
- DispatchQueue를 초기화할 때 attributes를 .concurrent로 설정하지 않으면 default값으로 Serial이 됨
- label은 값을 받아 DispatchQueue를 초기화하는 메서드


코어의 수
쓰레드: 일을 하는 사람
오버클럭
캐쉬 메모리
램
하드디스크


- 블록킹와 논블로킹은 다른 주체가 작업할 때 자신의 제어권이 있는지 없는지로 볼 수 있다.

- 동기와 비동기는 결과를 돌려주었을 대 순서와 결과에 관심이 있는지 아닌지로 판단

- main 앱이 실행되는 동안에는 Memory에 계속 올려져 있음
- 비동기 언제 끝났는지 알려주기 위해서 값을 받아주는 함수 callback 함수
- 이벤트 루프 swift
- swift 콜백 지옥


비동기 예를들어 mainThread에서 작업하던걸 다른 Thread로 넘겨주고 다시 바로 돌아옴 / 일을 끝나는거에 관심이 없음

<br />

## Reference
[wikipedia: Single-core](https://en.wikipedia.org/wiki/Single-core)
