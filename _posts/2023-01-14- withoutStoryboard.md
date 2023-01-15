# iOS Programmatically

1. Storyboard 파일 삭제
- 굳이 Storyboard파일을 삭제하지 않아도 programmatically 하는데 문제 없지만 사용하지 않는 파일은 삭제하는게 좋기에 Storyboard를 삭제해준다.
![](https://i.imgur.com/4ddZGEQ.png)

<br/>

2. info.plist 수정 
- info.plist에 가서 StoryboardName key 항목을 -를 눌러 삭제한다.
![](https://i.imgur.com/tNWTG0h.png)

- 💡 Project의 Metadata가 담긴 info.plist는 이미지와 같이 Project 초기에는 key가 적지만 Project가 진행되면서 점점 기능이 추가되면 key값을 찾는데 어려울 수 있다. 이럴 때는 Xcode의 [Find Navigator] 기능을 사용하면 쉽게 찾을 수 있다.
![](https://i.imgur.com/eFIw7Wi.png)

<br/>

3. Main Interface 삭제
![](https://i.imgur.com/Mk2xqKh.png)

- Xcode directory 최상단에 있는 Project를 클릭해서 TARGETS -> Info로 이동한다음 Main storyboard file base name Key값을 지워준다.

<br/>

4. 여기까지 하고 실행을 하면 Simulator가 검은화면을 보여준다면 정상적으로 설정을 잘 한것이다. 아직 initial ViewController를 설정해주지 않았기 때문에 검은화면이 나오는것.

![](https://i.imgur.com/r9XY1Qf.png)

- ❗️Simulator를 실행하자마자 Runtime error가 발생한다면 Storyboard와 연결된것들을 다 지우지 못했기 때문. 
![](https://i.imgur.com/HGFgxf7.png)

<br/>

5. SceneDelegate 설정 
- iOS 13 이후로는 AppDelegate의 LifeCycle의 역할을 SceneDelegate가 담당하게 되어 SceneDelegate에서 Scene을 지정해주어야 한다.
![](https://i.imgur.com/7fvahes.png)


```swift
window = UIWindow(windowScene: windowScene)
```
- Storyboard를 사용할 경우 window 속성은 자동으로 Initialization되어 연결된다. 하지만 지금은 Stroyboard가 없으므로 사용자가 직접 연결해준다. 

```swift
window?.rootViewController = ViewController()
```
- App을 켰을 때 시작점이 될 initial ViewController를 뜻한다
- initial ViewController를 바꾸고 싶으면 바꾸고 싶은 ViewController의 이름으로 변경한다.

```swift
window?.makeKeyAndVisible()
```
- makeKeyAndVisible() 메소드는 window를 보여주고 이 window를 key window로 만들어 준다


<br/>

6. 확인해보기
- 내가 지정한 initial ViewController 파일로 가서 viewDidLoad에 view.backgroundColor = .white를 설정해 흰색 배경화면이 나오는지 확인한다.

![](https://i.imgur.com/Qtp9ec9.png)
