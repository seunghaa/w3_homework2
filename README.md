##CRUD 자기소개서에 적용해보기
처음 민우선생님이 올려주신 영상을 보고 수업시간에 배운 CRUD를 따라해보았는데 이해가 정말 되지 않고 중간에 막혀서 진도가 나아가지 못했다. 좀 더 설명이 듣고 싶어서 CRUD를 찾아보다가 
https://www.flearning.net/courses/2 이 사이트에서 루비온레일즈 강좌가 있길래 그 중에서 CRUD부분만 다시 찾아서 천천히 보았다. 
이것을 보고 다시 민우선생님의 영상을 보았는데 다르게 한 부분들이 좀 있어서 이를 계속 찾아보면서 공부를 했다. 

CRUD를 자기소개페이지에 어떻게 적용하라는 것인지 고민을 해보다가 위에 NAV바에 탭페 Q&A게시판을 따로 만들어 새로운 탭을 형성하기로 하고 거기에 CRUD를 구현해 보려고 하였다.
민우 선생님의 영상은 처음 메인페이지에 CRUD를 바로 적용시켰는데 나는 새로운 tab에 CRUD로 된 게시판을 새로 만드려다 보니 경로설정이 처음에 너무 어려워서 계속 여러가지로 시도하다가 연결을 성공했다.
민우선생님의 영상을 토대로 다혜선생님이 올린 수업자료와 찾아본 인터넷 강의를 모두 참고해가며 자기소개 페이지에 "궁금한 점을 질문할 수 있는" CRUD로 구현된 게시판을 만들었다.
####공부한 것 정리
==****하나의 페이지를 만들기 위해서는****==
1. controller 생성을 한다. 
2. routes 파일에서 경로를 생성한다.
ex) get '/' => 'blog#index'
도메인을 쳐서 등러오면 blog라는 컨트롤러 안에 index라는 액션을 생성한다는 의미이다.
3. controller에서 위의 경로에서 설정한 액션을 정의해준다. 
4. 해당 액션의 view폴더를 설정해준다.

==****rails console 사용하려면 ****==

1. 블로그에 글을 쓰려면 date base를 만들 모델을 생성해야 한다.
(t) rails g model post
--post라는 모델을 만드는 것
2. db-migrate 안에 있는 20170423... 라고 써있는 파일을 열어 
데이터 베이스를 설계할 설계도에 해당하는 migration 파일을 다음과 같이 수정을 한다.
```erb```
class CreatePosts < ActiveRecord::Migration
  def change
    create_table :posts do |t|
      t.string :writer
      t.text   :content

      t.timestamps null: false
    end
  end
end
```
설계도가 완성된 것을 토대로 데이터 베이스를 만들어 주려면 
(t) rake db:migrate

==*여기까지, posts라는 테이블이 만들어 진 것이고 db의 migrate폴더의 migration파일에서 만들어준 writer와 content를 가진 것으로 작성이 된다. *==


==****경로 ****==
DELETE)post_path    : 하나의 글 삭제
POST)posts_path     : 새글쓰기
GET)posts_path:전체글보기
GET)new_post_path:글쓰기 창으로 가기
PATCH)post_path:하나의 글 수정
GET)post_path:하나의 글 보기
GET)edit_post_path:수정창으로 가기

#### 더 해봐야 할 것&어려운 것
--CRUD로 만든 게시판 HTML과 CSS수정하는 것이 내 생각처럼 잘 되지 않았다.
--경로 설정하는 것이 아직 익숙하지 않다. 
--영상을 겨우 따라하면서 과제를 했는데 아직까지 어려워서 많이 해봐야 할 것 같다. 

https://lastlast-seungha.c9users.io/