# Computed Property(연산 프로퍼티)
- 특정 명령을 연산하고 값을 반환한다. 
- class, struct, enum에서 사용
- Stored Property와 달리 저장공간을 갖지 않고 다른 Stored Property의 값을 연산하거나 Property로 전달받은 값을 다른 Stored Property에 저장한다 값이 계속 바뀌므로 var로 선언되어야 한다
- Properties 형태를 한 Method
- Method 이기 때문에 인스턴스에 메모리 공간이 할당되지 않음
- var로만 선언가능, 타입까지 선언해야함(형식 추론 방식안됨)

## 기본 구조
```swift
var 이름: 타입 {
    get {        // getter
       return     // return 구문 항상 명시
    }
    set(변수) {   // setter

    }
}
```
## 사용예시
```swift
struct AppleStore {
    var region = "USA"
    
    var origin: String {
        get {
            return "made in \(region)"
            // return "made in \(origin)"  error!
        }
        set(region) {
            self.region = "made in \(region)"
        }
    }
}
// get 사용
var a = AppleStore()
a.origin    // USA

// set 사용
a.region = "Korea"
a.origin    // Korea
```
## 설명
```swift
struct AppleStore {
    let region = "USA"
    // 읽기만 하기 때문에 값이 변경되지 않아 let으로 선언해도 된다.
    
    var origin: String {
        get {
            return "made in \(region)"
        }
    }
}
// get 사용
let a = AppleStore()
a.origin    // USA
```
- set 구문 생략가능 (get-only)
- 단, set기능을 사용할 수 없으며 값 수정 불가능
```swift
var origin: String {
    return "made in \(region)"
}
```
- get만 사용할 경우 get 키워드 생략가능
- set only는 안됨

```swift
var origin: String
```
- 값을 저장하지 않기 때문에 Type Inference(타입추론)를 할 수 없어서 반드시 선언할 때 자료형을 명시!
- 선언할때 자료형을 set에서 똑같은 자료형이 따라가므로 set은 자료형을 따로 명시하지 않아도 된다.
```swift
var region = "USA"
```
- set에서 값이 변경될 수도 있으므로 var로 선언
```swift
return "made in \(origin)"  //error!
```
- 연산프로퍼티는 저장할 공간이 없는데 저장된 값을 읽으려고 하기 때문에 에러발생

```swift
set(b) {
    let b = "made in \(region)"
}
```
- set의 파라미터는 단 하나만 존재하고, 변수니까 아무 이름이나 지어도 된다.

```swift
set {
    self.region = "made in \(newValue)"
}
```
- 변수명을 생략하고 newValue로 사용할 수도 있다 (대소문자,철자 엄수!)

