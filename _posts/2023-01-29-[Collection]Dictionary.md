- Key:Value 형태로 하나의 쌍으로 만들어 값 저장
```swift
let AppleStore: Dictionary<String,String> = ["iPhone":"iPhone13Pro", "iPad":"iPadAir"]
let AppleStore: [String:String] = ["iPhone":"iPhone13Pro", "iPad":"iPadAir"]
let AppleStore = ["iPhone":"iPhone13Pro", "iPad":"iPadAir"]
```

```swift
let appleStore = ["iPhone":"Apple","iPad":"Apple"]    // Value(Apple) 중복 가능
let appleStore = ["iPhone":"Apple","iPhone":"SamSung"]    // error Key(iPhone) 중복 불가능 
```
- Key 값은 유일해야함(중복 불가능) Value값은 중복 가능
- 동일한 type쌍의 data만 담을 수 있음
- Key값은 Hashable 하기 때문에 검색 속도가 빠름
- Hashable: 해시함수를 사용해 유일한 값으로 변환이 가능하다
- 유일한 값이기 때문에 검색하는 속도가 빠르다.
