## Programming Paradigm
- 개발 방법론
- 가장 좋은 Paradigm은 없다.
- 하나의 Paradigm을 기반으로 서비스를 구축하는 것도 좋지만
- 여러 Paradigm을 각각의 상황과 맥락에 따라 적절히 혼합해서 서비스를 구축하기도 한다.
- 비즈니스 로직이나 서비스의 특징을 고려해 Paradigm을 정해야 한다.
## Declarative Programming(선언형)
## Functional Programming(함수형 프로그래밍)
- `순수 함수`들을 블록처럼 쌓아 로직을 구현하고 고차함수를 통해 재사용성을 높인 Paradigm
- ex) .map.reduce
- 순수함수: 출력이 입력에만 의존하는 것을 의미
- 고차함수: 함수가 함수를 값처럼 매개변수로 받아 로직을 생성할 수 있는것
- 일급객체: 고차함수를 쓰기 위해서는 해당 언어가 일급 객체라는 특징을 가져야 한다
1. 변수나 메서드에 함수를 할당할 수 있어야 한다.
2. 함수 안에 함수를 매개변수로 담을 수 있다.
3. 함수가 함수를 반환할 수 있다.

## OOP, Object-Oriented Programming(객체지향 프로그래밍)
- Data를 Object로 취급하여 Object 내부에 선언된 Method를 활용하는 방식
- 설계에 많은 시간이 소요되며 처리 속도가 다른 Paradigm에 비해 느리다

**OOP 특징**
1. Abstraction(추상화)
- 복잡한 시스템으로부터 핵심적인 개념, 기능을 간추려내는 것
2. Encapsulation(캡슐화)
- Object의 Property와 Method를 하나로 묶고 일부를 외부에 감추어 은닉화함
3. Inheritance(상속성)
- SuperClass의 특성을 SubClass가 이어받아서 재사용하거나 추가 확장하는것
- 코드의 재사용성 유지보수성에서 중요
4. Polymorphism(다형성) 
- 하나의 Method나 Class가 다양한 방법으로 동작하는것 Overloading, Overriding이 있음

**Overloading**
- `정적`다형성
- 같은 이름을 가진 Method를 여러개 두는 것
- Method의 타입, Parameter의 유형, 개수 등으로 여러 개를 둘 수 있다.

**Overriding**
- `동적`다형성
- 주로 Method Overriding을 말한다.
- SuperClass로 Inheritance한 Method를 SubClass가 재정의하는 것

OOP를 설계할 때는 SOLID원칙을 지켜야 한다
1. SRP, Single Responsibility Principle(단일 책인 원칙)
- 모든 Class는 하나의 책임만 가져야 한다
- 
2. OCP, Open Closed Principle(개방-폐쇄 원칙)
- 유지 보수 사항이 생긴다면 코드를 쉽게 확장할 수 있도록 하고 수정할 때는 닫혀 있어야 한다.
- 즉 기존의 코드는 잘 변경하지 않으면서도 확장은 쉽게 할 수 있어야 한다

3. LSP, Liskov Substitution Principle(리스코프 치환 원칙)
- Program의 Object는 Program의 정확성을 깨뜨리지 않으면서 하위 타입의 Instance로 바꿀 수 있어야 한다.
- SuperClass Object에 SubClass Object를 넣어도 시스템이 문제없이 돌아가게 만드는 방법

4. ISP, Interface Segregation Principle(인터페이스 분리 원칙)
- 하나의 일반적인 Interface보다는 구체적인 여러 개의 Interface를 만들어야 한다

5. DIP, Dependency Inversion Principle(의존 역전 원칙)
- 자신보다 변하기 쉬운 것에 의존 하던 것을 Abstraction된 Interface나 SuperClass를 두어 변하기 쉬운 것의 변화에 영향받지 않게 하는 원칙
- 즉, 상위 계층은 하위 계층의 변화에 대한 구현으로부터 독깁해야 한다.



## Procedural Programming(절차형 프로그래밍)
- 로직이 수행되어야 할 연속적인 계산 과정
- 진행되는 방식으로 코드를 구현하기 때문에 가독성이 좋고 실행 속도가 빠르다
- 모듈화하기 어렵고 유지 보수성이 떨어진다.
