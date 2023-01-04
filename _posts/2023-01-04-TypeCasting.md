## Any
 - Swift의 여러 DataType(String, Int, Bool), Class, Struct, Enum, func, Optional까지 모든 Type의 Instance도 저장할 수 있는 타입
 - 여러 종류의 Type을 Array에 담아서 생성 가능
```swift
class AppleStore {
    let name: String = "iPhone12"
    let weight: Int = 164
}

struct GalaxyStore {
    let name: String = "Galaxy20"
    let weight: Int = 163
}

var anything: Any = ["Andrew", 93, 4.11, AppleStore(), GalaxyStore() ]
```
 - ⭐️Type의 메모리 구조를 알 수 없기 때문에, 항상 TypeCasting을 사용해야함
 ## AnyObject
 - 모든 Class Type의 Instance도 저장할 수 있는 Type
