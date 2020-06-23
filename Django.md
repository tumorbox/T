



파이썬 설치

https://www.python.org/downloads/release/python-376/

 vs코드

https://code.visualstudio.com/docs/?dv=win\

api 키

AIzaSyDmM8To4UYKBMEvfnmhY-EK8Yxpwoa3DWQ





# Django intro 

## Start Django

1. 장고 설치

   ```bash
   pip install django==2.1.15
   pip list 
   ```

2. 프로젝트 생성

   ```bash
   django-admin startproject <프로젝트명>
   ```

   ```bash
   python manage.py runserver
   	http://127.0.0.1:8000/	
   ```

3. 프로젝트 생성시 제공하는 파일

   - manage.py
     - 전체 django와 관련된 모든 명령어를 manage.py를 통해 실행 합니다.

   - `__init__.py`
     - 현재 `__init__.py`파일이 존재하는 폴더를 하나의 프로젝트 혹은 패키지를 인식하게 해주는 파일
   - settings.py
     - 현재 프로젝트의 전체적인 설정 및 관리를 위해 존재하는 파일

   - urls.py
     - 내 프로젝트에 접근 할 수 있는 경로를 설정하기 위한 파일

   - wegi.py
     - 배포를 위해 사용

   

   

   

   ## Start app

   

   ```bash
   $ python manage.py startapp pages
   
   ```

   - app 설치 후 settings.py에 설정 변경

   ```py
    Application definition
   
   INSTALLED_APPS = [
       'pages',       
       
       'django.contrib.admin',
       'django.contrib.auth',
       'django.contrib.contenttypes',
       'django.contrib.sessions',
       'django.contrib.messages',
       'django.contrib.staticfiles',
   ]
   
   
   LANGUAGE_CODE = 'ko-kr'
   TIME_ZONE = 'Asia/Seoul'
   ```

   - 서버 실행해서 변경 사항 확인











# Django_form
### 0612	



throw.html 상대경로 사용







가져오는 방식이 2가지

- []  ---> 값이 없을 때 오류 발생

- .get --->  값이 없어도 오류 발생 안함. 값이 없으면 none 출력

  -  request.GET == 딕셔너리와 유사하다.

     request.GET != dict()

```bas
print(request.GET['message'])
print(request.GET.get('message'))
```



data는 주소창에서 받아 오는게 아님

Query String parameter에..









# Django_relation

06/22

cascade만 사용





django 확장 툴 설치

```bash
$ pip install django-extensions
```

settings에 등록해줘야 한다.

'django_extensions' 으로 등록



쉘창을 켠다  -> mysite 위치로 가서 켜야한다.

```bash
$ python manage.py shell_plus
```



ipython 설치

```bash
$ pip install ipython
```



0623

# 로그인/로그아웃

## Admin 관리자 계정 생성

```python
# musicians/admin.py -admin 정의
from.models import Musician, Album
admin.site.register(Musician, Alubm)
```

```bash
# bash 관리자계정 생성
python manage.py createsuperuser
```



http -> 일반적으로 상태를 저장하지 않는다.



### AuthenticationForm

- AuthenticationForm은 ModelForm이 아닌 Form 상속

- 로그인 함수 이용해서 로그인시 import 필요

```python
from django.contrib.auth import login as auth_login

```

```python
def login(request):
    if request.method == "POST":
        form = AuthenticationForm(request, request.POST)
        # AuthenticationForm은 ModelForm이 아닌 Form 상속
        # 별도로 정의된 Model이 없다는 뜻 
        # 그래서 넘겨주는 인자가 달라진다.
        if form.is_valid():
            # 로그인 DB에 뭔가 작성하는 것은 동일하지만, 연결된 모델이 있는건 아니다.
            # 그럼 무엇을 확인해야 하는가?
            # -> 세션과 유저 정보를 확인해야한다.
            # 그래서 request도 같이 넘겨줘야 한다.
            
            auth_login(request, form.get_user())
            return redirect('articles:index')
    else:
        form = AuthenticationForm()        
    context = {
        'form': form
    }
    return render(request, 'accounts/login.html', context)
```



- user.is_authenticated 를 이용해서 로그인상태 저장

``` html
<body>
  {% if user.is_authenticated %}
    <h3>{{ user.username }}님 환영합니다.</h3>
    <a href = "{% url 'accounts:logout' %}" >로그아웃</a>
  {% else %}
    <h3>로그인 or 회원가입 </h3>
    <a href = "{% url 'accounts:login' %}" >로그인</a>
    <a href = "{% url 'accounts:signup' %}" >회원가입</a>
  {% endif %}
  <hr>
```

```python
from django.contrib.auth.decorators import login_required
```

