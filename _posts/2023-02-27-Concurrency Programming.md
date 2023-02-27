- X86: 32bit 시스템 중 가장 대중적인 Architecture
- X64: 64bit 시스템 중 가장 대중적인 Architecture
- bit: CPU 레지스터의 크기
- 32bit는 RAM(가용메모리) 4GB까지만 인식을 함 (정확히 말하면 4GB도 다 인식하지 못함)
- 64bit는 
- CPU가 계산할 Data는 RAM에 쌓여있다
- CPU 내부에서 Data를 연산하기 위해 Data를 저장하는 공간이 레지스터 
- 이 레지스터의 크기가 32bit면 한번에 처리할 수 있는 Data 크기가 최대 32bit
- 즉 레지스터의 크기가 늘어나면 한번에 처리하는 Data양도 늘어남
- ex) 고속도로 차선: 차선이 넓어지면 더 많은 차들이 효율적으로 이동할 수 있다는 것

## Concurrency Programming(동시성 프로그래밍)
- 동시성은 고성능을 위해 꼭 필요한 개념 중 하나
- WWDC21 세션에서 새로운 Swift 동시성 프로그래밍이 도입되면서 기존에 GCD를 사용하던 동시성에 큰 변화가 생기게 되었다.
- 여러개의 Core를 효율적으로 활용하는데 도움을 줌
- Core를 적절하게 사용해서 처리 속도를 높이거나, 중요하지 않은 작업을 중요도가 낮은 스레드에서 실행시킴
- iPhone11 ~ 14의 경우 6코어를 가지고 있음 (성능 코어 2개 및 효율 코어 4개)


## GCD(Grand Central Dispatch)
- iOS 개발에서 주로 사용되는 Concurrency Programming API
- Objective-C때 부터 사용했음
- 높은 수준의 추상화를 제공
- Serial DispatchQueue는 한 번에 하나의 태스크를 순차적으로 실행
- Concurrent DispatchQueue는 많은 작업을 동시에 실행 
- 두 경우 모두 작업이 실행되는 순서는 FIFO입니다.

<!-- GCD를 사용하면 async로 작업을 수행하고 나서 보통 탈출 클로저를 이용한 completion handler를 통해 해당 작업이 끝났을 때의 처리를 해주게 됩니다.  -->

## Swift Concurrency
- WWDC 2021에서 새로 소개된 Concurrency Programming API 
- Concurrency Programming을 가독성이 좋은 코드로 작성하고자 도입됨
<!-- - async와 await 키워드를 이용해 비동기 태스크 종료 후 코드를 작성할 수 있음
- await 키워드로 인해 중지되면 이후에 사용해야 하는 데이터를 힙(heap) 영역에 저장해 두고 이후에 다시 힙 영역에서 해당 데이터를 가져와 사용 -->

## Compare GCD and Swift Concurrency
- completion handler를 많이 사용했고 그로 인해 많은 Callback을 함으로써 들여쓰기가 많아져 가독성이 저하됨
- 들여쓰기가 줄어들면서 가독성이 좋은 코드가 됨


## Reference
[WWDC 2021: Meet async/await in Swift](https://developer.apple.com/videos/play/wwdc2021/10132/)
[Github: apple / swift-evolution](https://github.com/apple/swift-evolution/blob/main/proposals/0296-async-await.md#problem-1-pyramid-of-doom)
