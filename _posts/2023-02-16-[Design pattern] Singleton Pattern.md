- 사용하기 쉽고 실용적이다.
- 하나의 Class에 하나의 Instance만 사용
- 보통 Database 연결 모듈에 사용
- 하나의 Instance를 다른 모듈들이 공유하며 사용하기 때문에 Instance를 생성할 때 드는 비용이 줄어드는 장점이 있음

**싱글톤 패턴의 단점**
1. TDD(Test Driven Development)를 할 때 Unit Test를 하게 되는데 서로 독립적인 Instance를 만들기 어렵다
2. 의존성이 높아짐
❓의존성: 종속성이라고 하며 A가 B에 의존성이 있다는것은 B의 변경사항에 A또한 변해야 된다는 것을 의미
- 모듈간의 결합을 강하게 만드는 단점이 있다.
- 의존성 주입(DI, Dependency Injection)을 통해 모듈 간의 결합을 느슨하게 만들어 줄 수 있다.

**의존성 주입(DI, Dependency Injection)**
- 메인 모듈이 `직접`다른 하위 모듈에 대한 의존성을 주기보다 중간에 dependency injector(의존성 주입자)를 두어서 `간접`적으로 의존성을 주입하는 방법
- 구현할 때 추상화 레이어를 넣고 구현체를 넣어 주기 때문에 App의 의존성이 일관되고 App을 쉽게 추론할 수 있다는 장점이 있다.
- 모듈들이 더 분리되므로 Class가 늘어서 복잡성이 증가된다.
- **의존성 주입의 원칙: 상위 모듈은 하위 모듈에서 어떠한 것도 가져오지 않아야 한다. 또한 둘 다 추상화에 의존해야 하며 추상화는 세부 사항에 의존하지 말아야 한다.**

## Reference
[면접을 위한 CS 전공지식 노트 / 주홍철](https://search.naver.com/search.naver?sm=tab_hty.top&where=nexearch&query=%EB%A9%B4%EC%A0%91%EC%9D%84+%EC%9C%84%ED%95%9C+CS+%EC%A0%84%EA%B3%B5%EC%A7%80%EC%8B%9D+%EB%85%B8%ED%8A%B8&oquery=%EB%A9%B4%EC%A0%91%EC%9D%84+%EC%9C%84%ED%95%9C+CS+%EC%A0%84%EA%B3%B5%EC%A7%80%EC%8B%9D+%EB%85%B8%ED%8A%B8&tqi=h%2BVfvsp0Jy0ssnqMsbVssssssql-157549)
