## 상속과 확장의 비교
 상속 
- 타입을 새로만들어, 데이터를 추가하고, 기능(메서드)을 변형시켜 사용하려는 것
확장 
- 현재 존재하는 타입에 기능(메서드)을 추가하여 사용하려는 것


확장의 장점
- 원본 코드에 대한 권한이 없는 유형을 확장하는 기능

```swift
// 기존 타입
class anyType {

}

// 확장
extension anyType {

}
```
- 확장의 예시
```swift
extinsion Int {
    var squared: Int {
        return self * self
    }
}
5.squared    // 25
3.squared    // 9
```

