0. UITableView나 UICollectionView로 App의 대부분의 View를 만들지만 `만국박람회`의 첫 화면 처럼 UIViewController에서 UI를 설정할 경우도 있으므로 Custom으로 만드는 방법을 공부해본다.
또는 앱의 여러 View에서 사용할 UITextField나 UIButton도 예시와 같이 설정할 수 있으므로 앱의 통일성을 위해서도 사용해도 좋다.
ex) 회원가입 View와 로그인 View와 쿠폰입력하는 View의 TextField를 같은 옵션을 주고 싶을 때

<br />

1. textColor는 blue이고 backgroundColor는 red이며 
text는 Label변수 이름이고 굵은 font에 사이즈는 20이고
자동줄바꿈을 위해 lineBreakMode와 numberOfLines를 설정한 Label을 만든다고 가정했을 때 이렇게 만들 수 있다.
**(여러 기능이 필요하기 때문에 많은 옵션이 들어간다)**

```swift!
private let label1 = {
        let label = UILabel()
        label.textColor = .blue
        label.text = "UILabel 1"
        label.backgroundColor = .red
        label.font = .boldSystemFont(ofSize: 16)
        label.lineBreakMode = .byWordWrapping
        label.numberOfLines = 0
        return label
}()
```

<br />

2. 그런데 만약 이미지와 같이 거의 비슷한 옵션을 가진 UILabel을 여러개를 만든다고 한다면 오토레이아웃은 StackView로 간결하게 잡을 수 있지만 label 객체를 똑같이 복붙해서 여러개를 만들어야 할것이다.

![](https://i.imgur.com/JBzGovS.png)

```swift!
private let label2 = {
        let label = UILabel()
        label.textColor = .blue
        label.text = "UILabel 2"
        label.backgroundColor = .red
        label.font = .boldSystemFont(ofSize: 16)
        label.lineBreakMode = .byWordWrapping
        label.numberOfLines = 0
        return label
}()
private let label3 = {
        let label = UILabel()
        label.textColor = .blue
        label.text = "UILabel 3"
        label.backgroundColor = .red
        label.font = .boldSystemFont(ofSize: 16)
        label.lineBreakMode = .byWordWrapping
        label.numberOfLines = 0
        return label
}()

.......
```

<br />

3. 파일을 따로 만들어서 (CustomLabel) 프로젝트에서 사용할 나만의 UILabel을 만들어 본다.

```swift
// CustomLabel.swift
class CustomLabel: UILabel {
    init(labelText: String) {
        super.init(frame: .zero)
        textColor = .blue
        text = labelText            // 매개변수 설정한 값
        backgroundColor = .red
        font = .boldSystemFont(ofSize: 16)
        lineBreakMode = .byWordWrapping
        self.numberOfLines = 0      // self는 생략가능
    }
        
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}
```
- UILabel을 상속받고 init()으로 생성. 다른 옵션값은 같고 text값만 다르니 각각의 UILabel의 text의 값을 받기 위해 매개변수로 labelText를 설정한다.

<br />

4. UILabel을 만들었던 CustomLabel로 생성한다.

```swift
// ViewController.swift
private let label1 = CustomLabel(labelText: "label 1")
private let label2 = CustomLabel(labelText: "label 2")
private let label3 = CustomLabel(labelText: "label 3")
private let label4 = CustomLabel(labelText: "label 4")
private let label5 = {
        let label = CustomLabel(labelText: "label 5")
        label.backgroundColor = .yellow
        return label
}()
```
- 훨씬 간결해진것을 확인할 수 있으며 파라미터값 외에 변경사항이 없을 때는 {}를 생략할 수 있다.
- 따로 변경사항을 주고 싶으면 {}를 표기하고 안에 변경하고자 하는 옵션값을 넣어주면 된다.


![](https://i.imgur.com/hxVwXNp.png)


**전체 코드**
```swift!

// CustomLabel.swift
class CustomLabel: UILabel {
    init(labelText: String) {
        super.init(frame: .zero)
        textColor = .blue
        text = labelText            
        backgroundColor = .red
        font = .boldSystemFont(ofSize: 16)
        lineBreakMode = .byWordWrapping
        self.numberOfLines = 0     
    }
        
    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}

// ViewController.swift
class ViewController: UIViewController {
    
    private let label1 = CustomLabel(labelText: "label 1")
    private let label2 = CustomLabel(labelText: "label 2")
    private let label3 = CustomLabel(labelText: "label 3")
    private let label4 = CustomLabel(labelText: "label 4")
    private let label5 = {
        let label = CustomLabel(labelText: "label 5")
        label.backgroundColor = .yellow
        return label
    }()
    
    private lazy var stackView = {
        let stackView = UIStackView(arrangedSubviews: [label1,label2,label3,label4,label5])
        stackView.translatesAutoresizingMaskIntoConstraints = false
        stackView.axis = .vertical
        stackView.spacing = 30
        return stackView
    }()
    
    override func viewDidLoad() {
        super.viewDidLoad()
        view.addSubview(stackView)
        
        NSLayoutConstraint.activate([
            stackView.topAnchor.constraint(equalTo: view.topAnchor, constant: 100),
            stackView.centerXAnchor.constraint(equalTo: view.centerXAnchor),
        ])
    }
}
```
