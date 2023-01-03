# initializer(초기화)
- 생성자(Initializer)? 
**인스턴스**를 만들 때 사용하는 **메서드**
- Instance? 
Class / Struct / Enum에서 **생성된 객체**
- Method? 
특정 타입의(클래스, 구조체, 열거형)과 관련된 **함수**를 메소드라고 한다. 때문에 이니셜라이징도 init뒤에 함수처럼 () 사용
- Property?
클래스, 구조체, 열거형과 관련한 값

## Struct 초기화 방법

1. 선언과 동시에 기본값을 넣어주며 초기화
```swift
struct AppleStore {
   let name: String = "iPhone14"
   var price: Int = 982
}
```


2. 프로퍼티의 타입을 옵셔널로 초기화
```swift
struct AppleStore {
   let name: String?
   var price: Int?
}
```
- 값이 있을지 없을지 모를 경우 옵셔널로 초기화
- 초기화 할 때 값은 자동으로 nil로 초기화

3. init으로 값을 설정
```swift
struct AppleStore {
   var name: String
   var price: Int

   init(price: Int) {
       self.name = "iPhone14"// 선언과 동시에 기본값을 넣어주며 초기화
       self.price = price
   }
}
```

## init 초기화 (Class, Struct)
```swift
struct AppleStore {
    let name: String = "iPhone14"
    var price: Int
    let color: String
    var weight: Int = 240

// weight처럼 var로 선언되어 있고 기본값으로 초기화가 되어 있는경우 init으로 초기화를 다시 할수도, 하지 않을 수도 있다
    init(price: Int, color: String) {       
        self.price = price
        self.color = color
    }
    
// name은 let으로 선언되고 기본값이 있기 때문에 초기화 할 때 생략해야 한다
    init(/*name: String,*/ price: Int, color: String, weight: Int) { 
        self.price = price
        self.color = color    // color가 let으로 선언되어 있지만 기본값이 없으므로 init으로 초기화 가능
        self.weight = weight  // weight가 기본값이 있지만 var로 선언되었으므로 init으로 초기화 가능
    }
}

// struct나 class는 초기화 되지 않은 프로퍼티를 초기화 할 때 이름과 갯수와 순서가 동일해야 한다
var iPhone14 = AppleStore(price: 354, color: "red", weight: 220) 
iPhone14.price = 984
iPhone14.price = 875
// price가 var로 되어있기 때문에 변경 가능 하지만 인스턴스를 저장한 변수 iPhone14가 let으로 선언한다면 변경 불가능

iPhone14.color = "blue"
// Error: color는 let으로 선언되어있기 때문에 값을 변경 할 수 없는데 
// iPhone14가 인스턴스 생성할 때 red로 초기화 했고 red를 blue로 값을 변경하려고 하므로 불가능
```

## Class
1. 선언과 동시에 기본값을 넣어주며 초기화
```swift
class AppleStore {
  let name: String = "iPhone14"
  var price: Int = 982
}
```

2. 프로퍼티의 타입을 옵셔널로 초기화 (let으로는 선언불가)
```swift
class AppleStore {
  let name: String?
  var price: Int?
}
```

3. init으로 값을 설정
```swift
class AppleStore {
   let name: String = "iPhone14"
   var price: Int
   var color: String?

// name은 기본값을 color는 옵셔널을 가지고 있기 때문에 price만 init으로 생성
   init(price: Int) {
       self.price = price
   }
}
```
- 클래스안의 모든 프로퍼티가 기본값을 가지고 있거나 옵셔널 타입일 경우 init 생성자를 따로 선언해줄 필요가 없음


## 클래스 Initializers
1. Designated Initializers(지정 생성자)
- Class의 모든 Property를 초기화 하는 생성자
- 생성자 Method가 종료되기 전까지 생성자 안에 모든 Property는 **초기값**을 가져야 한다
- 상속 받은 SubClass(자식클래스)는 init(초기화)을 할 경우 자신의 SuperClass(부모클래스) 생성자 까지 초기화를 해야 한다.
```swift
class AppleStore {
    let name: String = "iPhone14"
    var price: Int
    var color: String = "red"

    init(price: Int) {
        self.price = price
    }
}

class iPhone14: AppleStore {
    let region: String
    
    init(region: String) {
        self.region = region
        super.init(price: 892)
    }
}
```
2. Convenience Initializers(편의 생성자)
- 다른 키워드 없이 init만 사용하면 되는 Designated Initializers와 달리 생성자 앞에 convenience 사용
- 같은 Class에 있는 Designated Initializers를 보조하는 역할을 함
- 때문에 Convenience Initializers를 사용하려면 Designated Initializers가 필수로 구현되어 있어야 함
