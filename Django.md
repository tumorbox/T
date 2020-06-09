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

   

   

   