## dequeueReusableCell
### Declaration
```swift
func dequeueReusableCell(
    withIdentifier identifier: String,
    for indexPath: IndexPath
) -> UITableViewCell
```
- identifier(식별자)로 찾은 후 Reusable(재사용) 가능한 Cell 개체를 반환
- Parameter의 identifier는 Cell을 식별하는 String. nil이 아니어야 함.
- Parameter의 IndexPath는 Cell의 위치를 지정하는 index 경로.
- 많은 Cell을 가진 TableView를 표현해야 할 때 Memory가 Cell의 전부를 할당하고 있다가 표현할 필요 없이 화면에 보이는 Cell만 할당하고 있으면 되기 때문에 Memory를 절약 할 수 있다.

### dequeueReusableCell의 문제점
- Cell을 재활용함으로써 생기는 문제
- Cell의 UI(Label, button)나 Attribute(속성)들이 중첩되는 문제점이 있다.

### 예제
- 30개의 Cell을 가지고 3번째 Cell만 red 색을 가지는 TableView 생성.
```swift
import UIKit

class ViewController: UIViewController {
    
    private let cell = "cell"
    
    private let tableView = {
        let tableView = UITableView()
        return tableView
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.dataSource = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: cell)
        configureUI()
    }
    
    private func configureUI() {
        view.backgroundColor = .white
        view.addSubview(tableView)
        tableView.translatesAutoresizingMaskIntoConstraints = false
        tableView.topAnchor.constraint(equalTo: view.topAnchor).isActive = true
        tableView.leftAnchor.constraint(equalTo: view.safeAreaLayoutGuide.leftAnchor).isActive = true
        tableView.rightAnchor.constraint(equalTo: view.safeAreaLayoutGuide.rightAnchor).isActive = true
        tableView.bottomAnchor.constraint(equalTo: view.safeAreaLayoutGuide.bottomAnchor).isActive = true
    }

}

extension ViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 30
    }
    
    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: cell, for: indexPath)
        cell.textLabel?.text = "\(indexPath)"
        if indexPath.row == 3 {
            cell.backgroundColor = .red
        }
        return cell
    }
    
}
```
### 결과화면
![](https://i.imgur.com/icLTBL4.gif)

### 해결방안
- index 별로 설정을 해주는 방법으로 문제를 해결할 수 있다.
```swift
if indexPath.row == 3 {
    cell.backgroundColor = .red
} else {
    cell.backgroundColor = .white
}
```

### 결과화면
![](https://i.imgur.com/IzBIbLX.gif)


## Reference
[Apple Developer: dequeueReusableCell(withIdentifier:for:)](https://developer.apple.com/documentation/uikit/uitableview/1614878-dequeuereusablecell)
