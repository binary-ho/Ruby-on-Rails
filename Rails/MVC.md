# MVC in Rails!
Rails 에서의 MVC

#### 1. terminal에서 controller를 생성합니다.
```
rails generate controller home
```
위와 같은 커멘드 입력시, 알아서 **`home_controller.rb`라는 이름의 Controller와** <br/>
**views에 home이라는 이름의 폴더가 생성되고**, 테스트파일, 헬퍼, scss등이 생성됩니다.

#### 2. 컨트롤러에서 **엑션**을 만들어줍니다.
#### 3. `config/routes.rb`에서 어떤 url에 접근 했을 때, 어떤 컨트롤러의 어떤 엑션을 실행할지 설정합니다.
#### 4. view의 폴더에 엑션과 이름이 같은 erb파일을 만들어 보여줄 화면을 만듭니다.

