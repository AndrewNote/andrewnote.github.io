# ๐Updated: February 12, 2023

## TableView
- UIKit์์ Data๋ฅผ List ํ์์ผ๋ก ๋ณด์ฌ์ฃผ๊ธฐ ์ํ 
-  ํ ํ๋ฉด์ ๋ง์ ์ ๋ณด๋ฅผ ๋ณด์ฌ์ฃผ๊ธฐ ์ํด์ List ํํ๋ฅผ ๋๊ณ  ์๊ณ  Scroll์ด ๊ฐ๋ฅํ๋ค
- ํ๋์ Column(๊ฐ๋ก์ค)๊ณผ ์ฌ๋ฌ๊ฐ์ row(์ธ๋ก์ค)์ ๊ฐ์ง๋ฉฐ ์์ง์ผ๋ก๋ง Scroll์ด ๊ฐ๋ฅํ๋ค. _์ํ Scroll์ Collection View์ ํผํฉํด์ ๋ง๋ค ์ ์๋ค._
- ๊ฐ๊ฐ์ Column(๊ฐ๋ก์ค)์ ํ๋์ ์(cell)์ ๋์ํ๋ค.
- Section์ ์ด์ฉํด Column(๊ฐ๋ก์ค)์ ์๊ฐ์ ์ผ๋ก ๋๋ ์ ์๋ค.
- header์ footer์ ์ด๋ฏธ์ง๋ ํ์คํธ๋ฅผ ์ถ๊ฐํด ์ถ๊ฐ ์ ๋ณด๋ฅผ ๋ณด์ฌ์ค ์ ์์ต๋๋ค.

<!-- ์์ ์ด๋ฏธ์ง ๋ณด์ฌ์ฃผ๊ธฐ -->

## dequeueReusableCell

- ์ฌ์ฉ์์๊ฒ ๋ณด์ฌ์ค์ผํ  ๋ฐ์ดํฐ๊ฐ ๊ต์ฅํ ๋ง์๋ฐ (๊ณ์ load๋๋ ์ฝ๋ ์๋ทฐ,ํ์ด๋ธ๋ทฐ) ๋ฉ๋ชจ๋ฆฌ๊ฐ ์ด๋ฅผ ๋ด๊ธฐ์ ๋ถ์กฑํ๋ค๋ฉด, ๋ฉ๋ชจ๋ฆฌ๋ฅผ ํจ์จ์ ์ผ๋ก ๊ด๋ฆฌํด์ ์ ๋ณด๋ฅผ ์ ๋ฌํ  ์ ์๋๋ก ํด์ผํ๋ค
- ํ์ด์ง ์์๋ ์กด์ฌํ์ง๋ง ํ๋ฉด์ ๋ณด์ด์ง ์๋ ์์ ์ฌ์ฌ์ฉ ํ์ ๋ด์ ์์ ๋ค์์ฌ์ฉํ  ๊ฒ์ ์ค๋นํ๋ค. ์๋ฅผ ๋ค์ด ์คํฌ๋กค์ ์๋๋ก ๋ด๋ฆฌ๋ฉด ์๋์ ์๋ ์๋ค์ ์ฌ์ฌ์ฉํ๋ฅผ ํ์ธํด๋ณด๊ณ  ์ฌ์ฌ์ฉํ  ์์ด ์์ผ๋ฉด ๊ทธ๊ฑธ ๊ฐ์ ธ์ ์ฌ์ฉํ๊ณ  ์์ผ๋ฉด ์๋ก ์์ฑํด ์ฌ์ฉํ๋ค **๋ชจ๋  ์์ ์์ฑํ์ง ์๊ธฐ ๋๋ฌธ์ ๋ฉ๋ชจ๋ฆฌ๋ฅผ ์ ์ฝํ  ์ ์๋ค.**

**dequeueReusableCell(withIdentifier:for:)**
- withIdentifier: ์ฌ์ฌ์ฉ ๋๋ ์ ๊ฐ์ฒด๋ฅผ ์๋ณ ํ  ์ ์๋ String์ด์ด์ผ ํ๋ฉฐ nil์ด ๋ ์ ์๋ค
- indexPath: cell์ ํน์  ์์น๋ฅผ ์๋ ค์ฃผ๋ฉฐ data Source ๊ฐ์ฒด์๊ฒ ํญ์ ํน์ ํ indexPath๋ฅผ ์๋ ค์ค์ผ ํ๋ค

```swift
// ํ๋ฉด์ ๋ณด์ด์ง ์์ ๋ชจ๋  ์๋ค๊น์ง ๋ง๋ค๊ธฐ ๋๋ฌธ์ ๋ฉ๋ชจ๋ฆฌ๋ ์ฑ๋ฅ์ ๋ถํ๋ฅผ ์ผ์ผํค๊ฒ ๋๋ค
let cell: UITalbeViewCell = UITalbeViewCell()
// Reuse Queue์ ๋ด์๋๊ณ  ํ์ํ ๋งํผ๋ง ๊ฐ์ ธ์์ ๋ง๋ค์ด์ค๋ค
let cell: UITableViewCell = tableView.dequeueReusableCell(withReuseIdentifier: identifier, for: indexPath)
```


DataSource: Data๋ฅผ ๋ฐ์ View๋ฅผ ๊ทธ๋ ค์ฃผ๋ ์ญํ 
Delegate: ์ฌ์ฉ์์ Action์ ๋ํ ๋์ ์ํ

## TableView์ ๊ณ์ธต 
UITableViewController -> UITableView -> UITableViewCell -> Content View


## Reference
[Apple Developer: UITableView](https://developer.apple.com/documentation/uikit/uitableview)
[Apple Developer: UITableViewController](https://developer.apple.com/documentation/uikit/uitableviewcontroller)
[Apple Developer: UITableViewDataSource](https://developer.apple.com/documentation/uikit/uitableviewdatasource)
[Apple Developer: UITableViewDelegate](https://developer.apple.com/documentation/uikit/uitableviewdelegate)



## ๊ธฐ๋ณธ์ ์ธ TableView ์์ฑํด๋ณด๊ธฐ
**์ ์ฒด์ฝ๋**
![](https://i.imgur.com/H5p9HIm.png)

<br />
<br />

### TableView์ View๋ฅผ ๊ทธ๋ ค์ฃผ๊ธฐ ์ํด UITableViewDataSource ํ๋กํ ์ฝ ์ฑํ
```swift
class ViewController: UIViewController, UITableViewDataSource
```
<br />

### TableView ๊ฐ์ฒด ์์ฑ
```swift
private let mainTableView: UITableView = {
    let tableView = UITableView()
    return tableView
}()
```

<br />

### TableView์ cell ์์ฑ ๋ฐ ์ค์ 
```swift
func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
    cell.backgroundColor = .red
    return cell
}

func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return 5
}
```

<br />

### cell ๋ฑ๋ก
```swift
self.mainTableView.dataSource = self
mainTableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
```

<br />

### TableView ๊ฐ์ฒด AutoLayout ์ค์ 
```swift
view.addSubview(mainTableView)
mainTableView.translatesAutoresizingMaskIntoConstraints = false

NSLayoutConstraint.activate([
mainTableView.topAnchor.constraint(equalTo: view.topAnchor),
mainTableView.leadingAnchor.constraint(equalTo: view.leadingAnchor),
mainTableView.trailingAnchor.constraint(equalTo: view.trailingAnchor),
mainTableView.bottomAnchor.constraint(equalTo: view.bottomAnchor)
])
```

<br />

**๊ฒฐ๊ณผํ๋ฉด**
<img src="https://i.imgur.com/NNtpGGW.png" style = "zoom:30%" />
