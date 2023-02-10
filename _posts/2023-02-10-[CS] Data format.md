# Data format

## XML(EXtensible Markup Language)
- Data를 어떻게 주고 받을 것인지 서버개발자와 클라이언트 개발자가 서로간의 약속을 해서 통신을 했음
- OS, Programming language, architecture마다 형식이 달라서 통신하기 어렵다는 문제를 해결하기 위해 XML을 만듬 _지금도 많이 사용중_
- HTML의 문자 기반으로 한 markup language

**XML structure**
```xml!
<DataName>value</DataName>

<fruit>
    <name>Apple</name><color>red</color>
    <name>Banana</name><color>yellow</color>
    <name>Cherry</name><color>red</color>
</fruit>
```
- Data가 낭비되는 비효율적인 구조 _ex) name,color tag가 중복_

## JSON(JavaScript Object Notation)
- Javascript언어를 사용하는 독립형 데이터 포맷
- 독립형 데이터 포맷이기 때문에 서로 다른 Programming language, System간에 Object를 교환하기에 좋다.
- Key: Value 구조
- {} 중괄호 시작과 끝으로 데이터의 한 세트를 이룸

**JSON 값의 형식**
- 문자열
- 숫자
- 객체
- 배열
- null
- boolean 

**XML structure**
```json
{
    "name" : "iPhon12"    // 문자열
    "price" : 1000      // 숫자
    "specification" : { "Display": "Super Retina XDR", "Network" : "5G", "weight": 162 }
    "color" : ["Black","Red","Purple"]    // 배열
    "iOS14" : true    // boolean
    "samsung" : null    // null
}
```


### XML, JSON 공통점
- Data를 저장하고 전달하기 위해 만들어짐
- 기계와 사람 둘 다 쉽게 읽을 수 있음
- 계층적인 Data 구조를 가짐
- 다양한 Programming language에서 parsing(구문분석)이 될 수 있다.

### XML, JSON 차이점
- JSON은 comments(주석)을 지원하지 않지만 XML은 사용할 수 있다.
- JSON은 comma(,), bracket ( [] ), Quotation Mark(") 등 하나라도 잘못 명시하면 문서 전체에 영향을 주기 때문에 **문법오류에 취약하다**
- XML은 열고 닫는 tag가 있기 때문에 문법오류가 발생하더라도 부분적으로 Data를 읽을 수 있음
- JSON은 구문이 더 짧다
- JSON은 Data를 빨리 읽고 쓸 수 있다 
- XML은 배열을 사용할 수 없지만 JSON은 사용할 수 있다.

## YAML
- 기계가 아닌 사람이 보기 좋게 표기하는게 목적
- 파이썬 형식을 따르기 때문에 줄바꿈과 탭을 적절히 사용해야함 **이를 어기면 정보가 파괴됨**
- 그래서 JSON과는 다르게 minifier 하지 않는다.
- Comments(주석)과 inheritance(상속)을 사용할 수 있어서 여러 Data를 효율적으로 작성할 수 있다.

## Reference
[JSON wiki](https://en.wikipedia.org/wiki/JSON)
[JSON 개요](https://www.json.org/json-ko.html)
