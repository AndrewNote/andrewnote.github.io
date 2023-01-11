# AutoLayout
- 예시와 같이 iPhone14에 맞춰 UI를 설정했을 때 Layout이 잘 잡혔지만 Screen의 크기가 다른 iPhone SE를 실행했을 시 UI가 잘려서 나온것을 확인할 수 있다.

![](https://i.imgur.com/eDRL2dS.png)
![](https://i.imgur.com/IJGQXoq.png)

- iOS에서는 Device별로 대응하지 않고 Screen 크기에 따라 유연하게 대처할 수 있도록 Layout 제어 기능을 지원한다

## Auto-Resizing
- 단순한 Interface에서 적용할 때
- 보다 더 직관적으로 사용할 수 있으므로 사용하기 쉽다.
- 조금의 복잡한 Layout이나 객체의 크기나 간격을 정확하게 맞춰야 할 때는 설정하기 어렵다.

![](https://i.imgur.com/afGTnMr.png)

- 왼쪽에는 사각형이 중첩되어 있고 Toggle 형식으로 활성화와 비활성화를 할 수 있다.
- 바깥쪽 사각형은 내가 선택한 객체의 상위뷰이고 안쪽 사각형은 객체이다.
- 안쪽 사각형은 가로를 활성화하면 넓이를 세로를 활성화하면 높이를 Screen에 따라 선택한 객체를 자동으로 조절할 수 있다.
- 바깥 사각형의 각각의 위치를 활성화 하면 객체와 객체상위뷰 간에 위, 아래, 오른쪽, 왼쪽 간격을 유지할 수 있다.


## Auto-Layout
- Auto-Resizing을 대체하기 위해 도입된 기능
- Auto-Layout은 객체들 사이의 제약 조건을 **빈틈없이 설정이 되면** 이 조건들을 바탕으로 Screen의 크기에 따라 적절한 Layout을 계산하고 유지하는 작업을 한다. 

![](https://i.imgur.com/40M7QpN.png)
- Storyboard 아래쪽에 보면 여러 개의 아이콘이 있는데 각각의 제약조건을 설정 할 수 있다.
- Align(정렬), Constraints(제약조건), Issues(이슈관리), embed(기능추가)
