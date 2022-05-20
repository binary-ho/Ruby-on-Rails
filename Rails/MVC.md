# MVC in Rails!
Rails 에서의 MVC

# 정보 전달
1. 브라우저에서 url 요청 form 태그로 request에 담아 전송
2. routes.rb에서 url에 맞는 컨트롤러와 action을 찾기
3. 해당 컨트롤러의 action에 params에 정보 담아서 넘겨줌
4. controller가 @변수(맴버 변수) 이용해서 view 파일에 정보 전달
5. view는 브라우저에 화면 전달
<br/>

### 실제로 전달해서 print 해보기

1. **controller 만들기 + 맴버 변수 선언** <br/>
![print1](https://user-images.githubusercontent.com/71186266/169535812-9d590671-be69-4f43-924b-8ad4a8b1acfd.PNG)

2. **routes.rb에 정보 추가** <br/>
![print3](https://user-images.githubusercontent.com/71186266/169535809-f6028fb4-a9bf-4c50-95c8-7850a5511a21.PNG)

3. **erb파일에 맴버 변수 전달하여 출력하도록 설정** <br/>
![print2](https://user-images.githubusercontent.com/71186266/169535805-e41d2597-e2c6-484e-99d1-51a051ea8d01.PNG)

4. **쨘** <br/>
![print4](https://user-images.githubusercontent.com/71186266/169536353-9c0b1b81-bf07-4951-8735-9add87f9dac1.PNG)

**지역 변수를 전달하지 않도록 주의**


# Controller 만들기!

#### 1. terminal에서 controller를 생성합니다.
```
rails generate controller home
```
위와 같은 커멘드 입력시, 알아서 `home_controller.rb`라는 이름의 Controller <br/>
views에 home이라는 이름의 폴더가 생성되고, 테스트파일, 헬퍼, scss등이 생성됩니다.

#### 2. 컨트롤러에서 **action**을 만들어줍니다.
#### 3. `config/routes.rb`에서 어떤 url에 접근 했을 때, 어떤 컨트롤러의 어떤 action을 실행할지 설정합니다.
#### 4. view의 폴더에 action과 이름이 같은 erb파일을 만들어 보여줄 화면을 만듭니다.



### 참조
Youtube Channel 코딩전도사 - **[[바로가기]](https://www.youtube.com/user/shj5508)**
