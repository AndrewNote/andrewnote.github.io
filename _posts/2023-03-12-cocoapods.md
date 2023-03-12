- Specs에 모든 라이브러리를 저장해놓고 제공함 (중앙화)
- 거의 대부분의 라이브러리가 Cocoapods을 지원함
- gem (Ruby로 이루어진 Package Manager)
- Ruby로 개발되어 있어서 Ruby로 설치해주어야 함
- macOS에서 Ruby가 기본적으로 설치되어 있기 때문에 바로 설치 가능
- 프로젝트를 빌드 할 때마다 모든 라이브러리가 같이 빌드되서 빌드 시간이 느림
- 종속성관리가 쉬움
<!-- -- ex) A라이브러리 설치하고 사용하다가 B라이브러리가 필요해서 설치하려고 보니 B라이브러리에 A기능이 포함되어 있다면 즉 여러개가 종속이 되어있다면 중복설치할 필요없이 한번만 설치하면 된다  -->

```
sudo gem install cocoapods // cocoapods 설치하기
pod init // 의존성 관리를하는 Podfile 생성
vi Podfile    // podfile을 연다
pod install
```
- .xcodeproj가 아닌 .xcworkspace 프로젝트 파일을 열어 작업을 해야함
- 기존 프로젝트와 의존성을 맺어주기 위해 workspace를 생성
- workspace에 여러개의 Project가 포함되어 있다면 podfile을 통해 개별적으로 라이브러리를 추가할 수 있음
- 라이브러리를 항상 최신버전으로 사용하려면 Pod 버전을 명시하지 않으면 됨

Podfile.lock
pod install : pod을 추가, 수정, 삭제할 때에 사용 pod 마다 설치된 버전을 Podfile.lock에 기록
pod update
pod outdated
pod repo update
pod repo update {팟이름} -> 개별적인 pod에 대한 업데이트도 가능
### Reference
[cocoapods 라이브러리 검색](https://cocoapods.org/)
