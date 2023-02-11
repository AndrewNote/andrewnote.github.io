한 화면에 많은 정보를 보여주기 위해서 List 형태를 띄고 있고 Scroll이 가능하다

- 하나의 Column(가로줄)과 여러개의 row(세로줄)을 가지며 수직으로만 Scroll이 가능하다. _수평 Scroll은 Collection View와 혼합해서 만들 수 있다._
- 각각의 Column(가로줄)은 하나의 셀(cell)에 대응한다.
- Section을 이용해 Column(가로줄)을 시각적으로 나눌 수 있다.
- header와 footer에 이미지나 텍스트를 추가해 추가 정보를 보여줄 수 있습니다.

<!-- 예시 이미지 보여주기 -->

## [TableView]dequeueReusableCell

- 사용자에게 보여줘야할 데이터가 굉장히 많은데 (계속 load되는 콜렉션뷰,테이블뷰) 메모리가 이를 담기에 부족하다면, 메모리를 효율적으로 관리해서 정보를 전달할 수 있도록 해야한다
- 페이지 안에는 존재하지만 화면에 보이지 않는 셀을 재사용 큐에 담아 셀을 다시사용할 것을 준비한다. 예를 들어 스크롤을 아래로 내리면 아래에 있는 셀들의 재사용큐를 확인해보고 재사용할 셀이 있으면 그걸 가져와 사용하고 없으면 새로 생성해 사용한다 **모든 셀을 생성하지 않기 때문에 메모리를 절약할 수 있다.**

**dequeueReusableCell(withIdentifier:for:)**
- withIdentifier: 재사용 되는 셀 객체를 식별 할 수 있는 String이어야 하며 nil이 될수 없다
- indexPath: cell의 특정 위치를 알려주며 data Source 객체에게 항상 특정한 indexPath를 알려줘야 한다

```swift
// 화면에 보이지 않은 모든 셀들까지 만들기 때문에 메모리나 성능에 부하를 일으키게 된다
let cell: UITalbeViewCell = UITalbeViewCell()
// Reuse Queue에 담아두고 필요한 만큼만 가져와서 만들어준다
let cell: UITableViewCell = tableView.dequeueReusableCell(withReuseIdentifier: identifier, for: indexPath)
```
