# 6주차 - Flask 확장들, Elasticsearch

## 공부한 것

### Flask

기존에는 햇갈렸던 config 파일을 만들어서 설정들을 넣는 것의 의의를 알겠음. 굳이 dict파일로 구분하지 않더라도, 
> app.config.from_pyfile('config.py') 이런 식으로 파일안에 변수만 넣고 불러오기도 가능, 파일이 아니어도 된다.  

### Flask 확장

flask-security : 기존 flask-login보다 강화된 보안을 제공. 비밀번호 해싱을 두 번 및 여러 config를 제공함으로써 보안 강화가 가능.
flask-admin : 각 사이트의 관리자 역할을 할 수 있는 웹앱 만들기를 쉽게 하는 인터페이스를 제공. DB만 확장에 넣어주면 DB를 GUI 환경으로 제어가능하다.
을 활용하고, 기존 flask-admin의 ModelView가 아닌, 새로운 front 단을 만들어 넣으려 함. 그러기 위해선, 밑바탕인 BaseView를 상속받아 필요한 기능들을 넣어주면 된다. 말로는 되게 쉬워보이지만, css, html 하나를 바꾸면, 기존 admin의 jinja문법을 다 바꿔야하고, 필요한 기능들을 가져와야 하는데, 그러려면 flask-admin의 jinja 코드를 다 공부해야하고, 지나치게 많은 노력이 필요하다. 기존 앞단 하나 붙이는데도 며칠의 시간이 걸렸고, 5주 안의 시간에는 절대 못 할 거 같아, 방향을 잘못 잡았음을 깨달았다. 또한 flask-admin, flask-security 각각 그 모듈만의 블루프린트를 가지는데, 그걸 그냥 flask에 @로 route를 주면 블루프린트 충돌이 일어나고, 신경쓸 점이 한 두가지가 아니었다. 이번에 그렇게 자율적으로 처음 합쳐봐서 어려웠을 수도 있지만, flask 책에서처럼 쉽게 확장들을 다루는 건 어렵다는 걸 깨달았다. 

### ElasticSearch

RDBMS와는 다르고, NoSQL처럼 json 형식으로 자료를 저장한다. RESTful API를 이용, http 메소드로 접근이 가능하다. PUT으로 index를 설정, POST로 document를 등록하고, GET으로 자료를 조회할 수 있다. yml 파일에 여러 설정들을 넣어준다(이름, 포트, 마스터 노드, 클러스터 등등). 검색 방법도 must, should, term, match 등으로 일치여부를 판단해, json으로 response를 보낸다. 이 받은 json 데이터를 프레젠테이션 로직에서 꾸며, 앞단에서 보여준다. 현재 findbig5 사이트는 elastic cloud 서버를 활용해 데이터를 모으고, client가 검색을 하거나, GET요청을 보내면 그에 맞는 데이터를 elastic cloud에 요청해 json으로 가져오고, 그 json을 flask에 주면, flask view, template단에서 꾸며서 보여주는 식이다. 굳이 이렇게 클라우드를 돌리지 않고, flask랑 Elasticsearch를 같이 돌리는 방법도 있을 거 같지만, 자료가 많이 나오지는 않는다. 



## 계획

### flask 
- restful api 다시 봐보고, flask로 restful api구현하는 확장들 공부하기 (flask-restful, flask-restless)

### ES?
- 원래 계획은 elasticsearch를 더 공부해보는 것이었지만, 현재 상태에서는 공부해도 쓸 곳이 없고, 한동안도 쓸 데가 없을 거 같다.

### AWS or ?
- FB5를 어디다가 업로드 할 것인가? ..