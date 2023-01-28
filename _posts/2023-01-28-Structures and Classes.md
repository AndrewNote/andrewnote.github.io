## Comparing Structures and Classes
값을 저장할 Property를 정의할 수 있다.
함수기능을 하는 Method 정의할 수 있다.
내부 값에 Subscripts [] 사용해서 접근할 수 있다.
Initializer를 사용해 초기 상태를 설정할 수 있다.
기본적인 구현 외에 기능을 Extension할 수 있다.
Protocol을 채택해서 표준 기능을 제공할 수 있다.

**차이점**
Class는 자신의 특성을 사용할 수 있는 Inheritance을 지원한다.
DeInitializer(소멸자)를 사용하여 Instance의 할당이 해제된다.
타입 캐스팅을 통해 런타임에서 타입을 확인할 수 있다.
Class Instance의 Reference Counting(참조 횟수) 둘 이상의 참조를 허용한다.

Struct를 주로 사용하고 이러한 기능들을 꼭 사용해야 할 때만 Class를 사용한다
실제로 대부분의 사용자 지정 데이터 형식은 Struct와 Enum이다.

## Definition Syntax
- Struct, Class는 선언할 때 Function과 같이 {}를 사용한다.
- PascalCase로 이름을 짓고 그 안의 Property, Method는 camelCase를 사용한다.

## Structure and Class Instances
- Definition된 Struct, Class를 사용하기 위해서는 Instance를 만들어 사용해야 한다.
- Struct, Class의 이름을 쓰고 뒤에 ()를 붙인다.

## Accessing Properties
- Instance이름.Property이름을 쓰면 만들어진 Struct, Class Instance의 Property에 접근할 수 있다.
- var(변수) Property는 값을 변경할 수 있다.

## Memberwise Initializers for Structure Types
## Structures and Enumerations Are Value Types ## Classes Are Reference Types
## Identity Operators
## Pointer

## Reference
https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html
