## Core
- 한번에 한가지 일만 처리
- Core가 여러 개라면 여러개의 일을 동시에 처리할 수 있다
- SingleCore는 동시에 여러일을 하는 것처럼 보이지만 실제로는 짧은 단위로 여러가지 일을 번갈아가면서 함
-- ex) 음악을 들으며 게임을하고 있는데 카톡 메세지 알림을 받는다
- Core가 2개 이상일 경우 어떤 Core가 일을 할지 분배하는 과정에서 딜레이가 발생할 수 있으므로 SingleCore가 더 효율적인 상황이 발생할 수 있다. 
- 또는 SingleCore에만 최적화된 Software도 있을 수 있다

## Thread
1. Hardware Thread
- Hyper-Threading Technology: 하나의 Core에서 둘 이상의 Thread를 실행할 수 있는 기술
- 논리적인 Core
- 1Core 2Thread라면 실제로 Core는 1개지만 Core가 2개인 것처럼 작업을 처리함.

2. Software Thread
- 논리적인 Thread
- Process 내부에서 작업 되는 가상의 Thread
- Thread는 Program의 작업을 처리함
- Multi Thread: 여러 Thread를 이용하여 여러 작업을 동시에 처리함
- 가상으로 만들어진 Thread이기 때문에 물리적인 Thread 갯수와는 상관없음

## Parallel Programming(병렬 프로그래밍)
- 여러 개의 Core(CPU)가 하나의 Task작업을 분담해서 처리
- 물리적으로 Core(CPU)가 2개 이상 있을 때 가능

## Reference
[wikipedia: Single-core](https://en.wikipedia.org/wiki/Single-core)
