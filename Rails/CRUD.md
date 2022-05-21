# CRUD in Rails!
Create와 Read는 **[[MVC.md]](https://github.com/binary-ho/Ruby-on-Rails/blob/main/Rails/MVC.md)** 파일에 적혀 있다.    
여기서는 나머지 Update와 Delete를 만들어 보겠다.

## Update
Controller 부분 제외하면 Create와 절차가 같습니다. Create 과정은 자동으로 만들어진 데이터의 id를 생성해 주기 때문에 id를 지정해줄 필요가 없지만, Update나 delete는 데이터를 특정해야 하므로, id를 알 필요가 있습니다. 

```ruby
# Controlloer
def modify  # 글 수정 form 입니다.
    @post = Post.find(params[:post_id])
end

  def update    # 글 수정 action
    post = Post.find(params[:post_id])
    post.item = params[:item]
    post.price = params[:price]
    post.save
    redirect_to '/read'
  end

# routes.rb 수정
get '/modify/:post_id' => 'home#modify' # 글 수정 form
post '/update/:post_id' => 'home#update'  # 글 수정 action
```
```html
<!--게시글을 읽는 페이지에서 수정 페이지로 데이터를 전달하는 방법입니다.-->
<!-- post.id는 만든 적 없지만 자동으로 생성되는 점에 유의합니다.-->
<h1>게시글 읽기</h1> <br>
<% @posts.each do |p| %>
  <% if p.item != nil %>
  물건: <%= p.item %> <a  href="/modify/<%=p.id%>>"> 수정 </a><br>  <!--포인트-->
  가격: <%= p.price %> <br> <hr>
  <% end %>
<% end %>
<br>
<a href="/">돌아가기 </a>

<!--modify.html.erb 파일 입니.-->
<form action="/update/<%=@post.id%>" method="post" >
  상품: <input type="text" name="item" value="<%=@post.item %>"/> <br>
  가격: <input type="number" name="price" value="<%=@post.price %>"/>
  <input type="submit">
</form>
<br>
<a href="/">메인으로</a>

```
<br/>

1. form page `modify`와 action page `update`를 만듭니다. 
2. 두 번째 블록 첫 문단! modify url에 post.id를 전달하는 것이 중요
    ```html
    물건: <%= p.item %> <a  href="/modify/<%=p.id%>>"> 수정 </a><br> 
    ``` 
<br/>

3. controller에서 받은 id를 이용해서 Post에서 해당 post를 불러옵니다.
    ```ruby
    def modify 
        @post = Post.find(params[:post_id])
    end
    ```
<br/>

4. 이후 modify view파일에 전달합니다 (이미 적혀있는 글 내용을 불러오기 위해)<br/>
   
5. modify view에서 수정한 뒤 폼을 보내는 url에 id를 실어 보냅니다.
    ```html
    <form action="/update/<%=@post.id%>" method="post" >
    ```
<br/>

6. update controller에서 url을 통해 post_id를 전달 받은 다음 update를 실행
    ```ruby
    def update    # 글 수정 action
        post = Post.find(params[:post_id])
        post.item = params[:item]
        post.price = params[:price]
        post.save
        redirect_to '/read'
    end
    ```


## Delete

```ruby
# Controller
def delete
    post = Post.destroy(params[:post_id])
    redirect_back(fallback_location: '/')
  end

# a 태그로 링크를 누르기 위해 get으로 가져옴 
get '/delete/:post_id' => 'home#delete'
```
rails 버젼이 업데이트 되면서, `redirect_to :back`이 삭제되고, `redirect_back`을 사용하도록 바뀌었습니다. 사용은 위 같이 무조건 fallback_location을 지정해줘야 합니다. 아니면 오류가 뜹니다. (뒤로 못 돌아갈 때를 대비하는 것 같습니다.)


### 참조
Youtube Channel 코딩전도사 - **[[바로가기]](https://www.youtube.com/user/shj5508)**
stackoverflow 게시글 - **[[rails redirect_to :back not working]](https://stackoverflow.com/questions/44098584/rails-redirect-to-back-not-working)**


