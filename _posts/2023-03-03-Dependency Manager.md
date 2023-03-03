## Open Source
- 누구나 제한없이 코드를 볼 수 있도록 한 소스코드
- 누구나 자유롭게 코드 개선에도 참여할 수 있음
- 필요한 기능의 Open Source를 사용한다면 기능 구현하는데 시간을 줄일 수 있음
- 다른 개발자가 내가 만든 Open Source에 코드를 어디까지 사용하게 할지 고려해봐야 함

## Dependency Manager(의존성 관리 도구)
- 외부 라이브러리를 사용할 때 프로젝트와 라이브러리의 관계를 관리해주는 도구
- 언어마다 다양하게 있음
- Swift는 Cocoapods, Carthage, Swift Package Manager가 있음
- 필수는 아니지만 사용하면 시간도 절약되고 안정성이 보장됨
-- ex) 외부 라이브러리가 버전업되어 업데이트를 해야 하는 경우 기존 라이브러리를 삭제하고 새로 설치해야 하는 일이 발생할 때 개발자가 실수 할 수도 있고 (human error), 그것을 고치기 위한 시간또한 많이 소요 됨

### Cocoapods
- 거의 대부분의 라이브러리가 Cocoapods을 지원함
- Ruby로 개발되어 있어서 Ruby로 설치해주어야 함 
- macOS에서 Ruby가 기본적으로 설치되어 있기 때문에 바로 설치 가능
- 프로젝트를 빌드 할 때마다 모든 라이브러리가 같이 빌드되서 빌드 시간이 느림

### Carthage
- 초기에 프레임워크를 추가하는 것 말고 프로젝트 설정이 바뀌지 않음
- carthage update 를 실행할때만 한 번 프레임워크를 빌드하므로 빌드 속도가 빠름
- 의존성이 추가될 때마다 작업을 해줘야 함
- Cocoapods보다 지원하는 라이브러리 수가 적음

### Swift Package Manager
- Apple이 지원한다
- Swift 언어에 내장되어 있어서 따로 설치가 필요없음
- Package.swift 파일 외에 수행할 설정이 없음
- Xcode GUI에서도 관리가 가능
- 지원하지 않는 라이브러리가 많음

## Reference
[wikipedia: Open-source](https://en.wikipedia.org/wiki/Open-sourc%E2%80%A6)
