## 디자인 패턴
- Program을 설계할 때 발생했던 문제점들을 Object간의 상호관계등을 이용하여 해결할 수 있도록 하나의 '규약' 형태로 만들어 놓음

## Factory Pattern
- Object를 사용하는 코드에서 Object 생성 부분을 때어내어 Abstraction한 Pattern
- Inheritance 관계에 있는 두 Class에서 SuperClass가 중요한 뼈대를 결정하고, SubClass에서 Object 생성에 관한 구체적인 내용을 결정
- SuperClass와 SubClass가 분리되기 때문에 느슨한 결합을 가짐
- SuperClass는 Instance 생성 방식에 전혀 알 필요가 없어서 유연성을 가짐
- Object 생성 로직이 따로 분리되 있기 때문에 코드를 Refactoring 하더라도 한 곳만 고칠 수 있게 되니 유지 보수성 증가

ex) 라떼 레시피와 아메리카노 레시피 등 구체적인 내용이 들어 있는 SubClass가 컨베이어 벨트로 전달되고 SuperClass인 바리스타 공장에서 이 레시피들을 토대로 생산하는?

### 예시코드

## Strategy Pattern(전략 패턴)
- Policy Pattern(정책 패턴)이라고도 불림
- Object 행위를 바꾸고 싶은 경우 `직접` 수정하지 않고 `캡슐화한 알고리즘`을 통해 바꿔주면서 상호 교체가 가능하게 만드는 Pattern
- ex) 물건을 구매할 때 네이버페이,카카오페이,삼성페이 등 다양한 방법으로 결제할때

### 예시코드

## Observer Pattern(옵저버 패턴)
- 주체(관찰자)가 Subject의 상태 변화를 관찰하다가 상태 변화가 있을 때마다 Method 등을 통해 Observer List에 있는 Observer들에게 변화를 알려주는 Pattern
- Observer Pattern을 사용한 서비스로는 twitter가 있다.
- 또한 이벤트 기반 시스템에 사용되며, MVC 패턴에도 사용된다.
- 예를 들어 주체라고 볼 수 있는 Model에서 변경 사항이 생겨 Observer인 View에 알려주고 이를 기반으로 Controller이 작동함

### 예시코드

## Proxy Pattern(프록시 패턴)
- Subject에 접근하기 전에 그 접근에 대한 흐름을 가로채 Subject의 앞단의 Interface 역할을 하는 Pattern
- 보안, 데이터검증, 캐싱, 로깅에 사용
- Proxy Server에도 사용
**Proxy Server**
- Server와 Client 사이에서 Client가 자신을 통해 다른 Network 서비스에 간접적으로 접속할 수 있게 해준다.

## Iterator Pattern
- Iterator를 사용하여 Collection의 요소들에 접근하는 Pattern
- 순회할 수 있는 여러가지 자료형의 구조와는 상관없이 Iterator 하나의 Interface로 순회 가능하다.

## Revealing Module Pattern(노출모듈 패턴)
- 즉시 실행 함수를 통해 Access Modifier를 만드는 Pattern

**IIFE(Immediately-involked-function)**
- 함수를 정의하자마자 바로 호출하는 함수.
- 초기화 코드, 라이브러리 내 전역 변수의 충돌 방지 등에 사용함


## Reference
[면접을 위한 CS 전공지식 노트 / 주홍철](https://search.naver.com/search.naver?sm=tab_hty.top&where=nexearch&query=%EB%A9%B4%EC%A0%91%EC%9D%84+%EC%9C%84%ED%95%9C+CS+%EC%A0%84%EA%B3%B5%EC%A7%80%EC%8B%9D+%EB%85%B8%ED%8A%B8&oquery=%EB%A9%B4%EC%A0%91%EC%9D%84+%EC%9C%84%ED%95%9C+CS+%EC%A0%84%EA%B3%B5%EC%A7%80%EC%8B%9D+%EB%85%B8%ED%8A%B8&tqi=h%2BVfvsp0Jy0ssnqMsbVssssssql-157549)
