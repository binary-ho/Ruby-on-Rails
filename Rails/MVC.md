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

# Model 만들기!
모델을 만들어서 게시글을 작성해본다. [[post 오류 사전처리]]()
#### 1. 모델 생성 명령어 입력
```
rails generate model post
```
model, 모델이름이름's migration, fixtures, 테스트 파일이 생성됨. **단수로 적자!!**
- migration: 데이터 형식 결정 파일, 저장될 데이터들의 양식을 정해줌

#### 2. get방식으로 form을 보여줄 페이지와 post방식으로 실제 form을 처리할 페이지 만들기 (action 만들기) <br/>
![model1](https://user-images.githubusercontent.com/71186266/169622893-207370f2-9df7-49ae-9db7-99e70b0e07ff.PNG)

#### 3. from 작성! get방식 페이지에서 만들어서 post 페이지로 보냅니다. <br/>
![model2](https://user-images.githubusercontent.com/71186266/169622895-95dec1a0-9a9d-4881-8521-65bb0d6f9abb.PNG)
sumit을 누르면 post 페이지 **new 페이지로 폼 전송!** 

#### 4. migration 파일 수정 
파일은 `db/migrate`폴더에 `crate_지어준 이름s.rb`형식으로 있다. <br/>
![model3](https://user-images.githubusercontent.com/71186266/169623280-e5e70d50-5786-4323-b926-e62804eae371.PNG)
- 각 column의 형식과 이름을 정해주고 table을 생성한다!. <br> `:item`은 string 형식, `:price`는 bigint형식!

#### 5. db 생성 - migration 완료
```
rake db:migrate
```

#### 6. post처리 해주기
![model4](https://user-images.githubusercontent.com/71186266/169623632-d5e3c047-f155-4714-9430-77b7b996bbd8.PNG)
- 해당 페이지의 Post 가져와서 대입!
- save이후, redirection!

#### 7. 읽기 처리
**7.1 action 설정** 
**@post라는 맴버 변수에 Post 내용을 가져옵니다.** <br/>
![model5](https://user-images.githubusercontent.com/71186266/169623925-f6debf6b-d3c2-4ee9-82cf-486b8f92b9a0.PNG)

**7.2  설정**
**맴버 변수 호출해서 읽기** <br/>
![model6](https://user-images.githubusercontent.com/71186266/169623929-04bbd8e4-d91b-4271-a3c9-4e1e05f4df3e.PNG)

**7.3 실행** <br/>
![model7](https://user-images.githubusercontent.com/71186266/169623930-e4e18f1a-2264-4dcf-b9ae-bfe7bd816cf3.PNG)
![model8](https://user-images.githubusercontent.com/71186266/169623931-dcf4fa9d-77c1-497f-8575-eab51b4d8106.PNG)


### 참조
Youtube Channel 코딩전도사 - **[[바로가기]](https://www.youtube.com/user/shj5508)**
