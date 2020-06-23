## Django ORM

### 프로젝트 생성

- Project Name : mysite

- App name : articles

  

###  페이지 생성

 	1. Index page
     - /index/ : 전체 게시글 목록을 보여 줄 페이지
 	2. create pages
     - /new/ : 글 작성을 위한 form(제목, 내용) 입력 페이지
     - /create/ : 글 작성 결과(제목, 내용)을 출력하는 페이지



## 추가

 	1. base template
     - 모든 템플릿들이 상속 받을 base.html



## 주의 사항

1. urls.py 설정 분리

   - app.name 함께 설정

     

2.  template 폴더 구조





$ python manage.py makemigrations



$ python manage.py migrate articles

