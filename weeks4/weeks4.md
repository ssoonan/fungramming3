# 4주차 - Flask와 RESTful, DB, PostgreSQL

## 공부한 것

### Flask & RESTful API

- ch 13 사용자 코멘트 - 일대다 관계를 이용한 db 만들기, form 구현, 권한 설정 등 특별한 건 X 
- ch 14 API - RESTful 방식으로 API 설계하는 방법. RESTful과 API가 헷갈려서 다른 책을 참고함. 그 결과 API란 어플리케이션 프로그래밍 인터페이스란 굉장히 큰 틀을 의미함. 그 API를 설계하고, 웹을 통해 주고 받는 방식이 엄청 많이 있고(XML, JSON ..), 회사마다도 그 방식이 다 다르기에(같은 JSON이어도 어떤 형식으로 넣느냐 따라 다 달라짐), 그걸 통일하려는 노력(=RESTful). 그 방법이 HTTP 주요 메서드를 통해, URL에 리소스를 표현하여, 규약이 정해진 JSON 파일로 주고 받는다는 것. Flask를 통해서도 그걸 구현할 수 있고 flask-restful, flask-restless 등을 통해 쉽게 구현할 수 있다. 
- cookie와 session 다시 공부


### DB & PostgreSQL

#### 6장 : 데이터 조작 - 데이터를 조작하는 측면 (각 행과 그 행 마다의 열 값)

6.1 데이터 삽입 : 테이블이 있으면, 데이터를 넣어야 관리를 한다. INSERT를 이용함. INSERT INTO 테이블이름 VALUES(~~~); but 이런 방식 보다는 INSERT INTO 테이블이름 (컬럼 이름~) VALUES( ~~~ ) 인 식으로 넣기. 값이 없으면 생략하거나, DEFAULT로 넣기


6.2 데이터 업데이트 : 이미 삽입된 데이터를 수정할 때

- 업데이트 할 테이블의 이름 & 컬럼의 이름
- 컬럼의 새 값 (수정할 값) / 여러 개일 수도 있고~
- 바꿀, 업데이트 할 행 / 여러 행 동시에도 되고~ / WHERE로 골라주기 아니면 다 고름

UPDATE 테이블이름 SET WHERE..


6.3 데이터 삭제 : DROP은 테이블 전체를, DELETE는 데이터 각 행을.. 역시 WHERE로 조건 줘서 행 고르기


#### 7장 : 쿼리 - 테이블을 조작, 데이터를 테이블에 넣었으니 이젠 꺼내야한다. 검색도 가능하다고 한다.

##### 7.2 : 테이블 표현식 - 테이블을 계산함. WHERE, GROUP BY, HAVING, FROM

###### 7.2.1 - FROM : 어디서 가져올 것인가?? ,있으면 다른 테이블도 가져옴, 이 땐 CROSS JOIN으로 가져옴. 물론 조건 주기는 가능하겠다만.. 부모를 선택하면 기본은 자식까지 다 가져온다고 했었다.

7.2.1.1 JOIN 종류 : CROSS JOIN, INNER JOIN, LEFT JOIN, RIGHT JOIN, FULL OUTER JOIN 등 ..

ON은 조건 주는 방법. USING은 공통 값 지정해줌. ex SELECT * FROM t1 INNER JOIN t2 USING(num), NATURAL JOIN이 USING을 단축한 것. but USING이 외부조인에도 쓸 수 있고 더 안전하다.

7.2.1.2 alias 별칭 주기. 서브쿼리나 조인을 쓸 때 필요하다.

7.2.1.3 서브쿼리 : 서브쿼리는 FROM, 어디서 가져올 것인가라는 조건을 줄 때 또 쿼리를 씀으로써 줄일 수 있는 것

7.2.1.4 테이블 함수 : ~인 방법으로 쓴다.

7.2.1.5 LATERAL 서브쿼리 : FROM 절에 테이블 2개 (서브쿼리나 등등..)일 때 선행, 앞에 있는 테이블에서 참조할 수 있게 해줌. 

###### 7.2.2 WHERE : boolean 식으로 조건을 준다. <>=, IN / 여기에도 서브쿼리를 쓸 수 있다. SELECT ... FROM fdt WHERE c1 in (SELECT c1 FROM t2)

###### 7.2.3 GROUP BY, HAVING : WHERE로 조건을 준 이후에 다시 조건을 주어 그룹화 등을 하기.



## 계획

### flask 
- 직접 고른 부트스트랩 theme으로 jinja templates 연결 
- posting, 로그인 등 블로그 백단 만들기
- DB는 PostgreSQL로 연결하기
- 배포까지 해보기 > 확실히 익히기

### DB & PostgreSQL
- PostgreSQL 서버에 등록하는 여러 개념들 익히기 
- ch 7 쿼리 입력해보기 
- ch 8 데이터 타입 간단히 익히기
- DB 설계, 최적화 공부
