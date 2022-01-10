# localStorage, sessionStorage, cookie
#### 쿠키의 단점을 보완해 HTML5에서 '웹스토리지'라는 기술 탄생
1-1) 웹스토리지 : 로컬스토리지, 세션스토리지.

1-2) 웹스토리지는 Key와 Value 형태로 이루어짐.

1-3) 웹스토리지는 클라이언트에 대한 정보를 저장.

1-4) 웹스토리지는 로컬에만 정보를 저장, 쿠키는 서버와 로컬에 정보를 저장.

#### 로컬스토리지는 클라이언트에 대한 정보를 영구적으로 저장
ex) 자동 로그인 저장

#### 세션스토리지는 세션 종료 시(브라우저 닫을 경우) 클라이언트에 대한 정보 삭제
ex) 입력 폼 정보 저장

3-1) 로컬&세션스토리지 장점1 : 서버에 불필요하게 데이터를 저장하지 않는다.

3-2) 로컬&세션스토리지 장점2 : 용량이 크다. (약 5Mb, 브라우저마다 차이 존재)

3-3) 로컬&세션스토리지 단점 : HTML5를 지원하지 않는 브라우저의 경우 사용 불가

#### 쿠키는 만료 기한이 있는 Key, Value 형태의 저장소
4-1) 쿠키 장점 : 대부분의 브라우저가 지원

4-2) 쿠키 단점1 : 매 HTTP요청마다 포함되어 api호출로 서버에 부담.

4-3) 쿠키 단점2 : 쿠키의 용량이 작음 (약 4Kb)

4-4) 쿠키 단점3 : 암호화 존재 x -> 사용자 정보 도난 위험

#### 예시
- 자동 로그인 -> 로컬스토리지

- 입력 폼 정보 -> 세션스토리지

- 비로그인 장바구니 -> 세션스토리지

- 다시 보지 않음 팝업 창 -> 쿠키

### 값 가져오는 법

1. 로컬 스토리지
```
localStorage.setItem('name', 'Luluzoe');
localStorage.setItem('birth', 2017);
localStorage.getItem('name'); // Luluzoe
localStorage.getItem('birth'); // 2017 (문자열)
localStorage.removeItem('birth');
localStorage.getItem('birth'); // null (삭제됨)
localStorage.clear(); // 전체 삭제
```

```
let object = {

"A" : 1,

"B" : 2,

"name" : "wecode",

"Key" : "Value"
}
```

```
localStorage.A (Key == A)
localStorage.getItem("A")
```
2. 세션 스토리지
```
sessionStorage.A (Key == A)
sessionStorage.getItem("A")
```
3. 쿠키
```
getCookie("A") (Key == A)
```
### 세팅하는 법
1. 로컬 스토리지
```
localStorage.A = 1 (Key == A, Value = 1)
localStorage.setItem("A", 1)
```
2. 세션 스토리지
```
sessionStorage.A = 1 (Key == A, Value = 1)
sessionStorage.setItem("A", 1)
```
3. 쿠키
```
setCookie("A", 1, 7) (Key == A, Value == 1, 유효기간 == 7초)
```


# 그외에 브라우저에 저장하는 방법을 아시나요?
### IndexedDB
IndexedDB는 파일이나 블롭 등 많은 양의 구조화된 데이터를 클라이언트에 저장하기 위한 로우 레벨 API   
IndexedDB API는 인덱스를 사용해 데이터를 고성능으로 탐색   
   
IndexedDB는 SQL을 사용하는 관계형 데이터베이스(RDBMS)와 같이 트랜잭션을 사용하는 데이터베이스 시스템   
JavaScript 기반의 객체지향 데이터베이스   
IndexedDB의 데이터는 인덱스 키를 사용해 저장하고 회수할 수 있으며, 구조화된 복사 알고리즘을 지원하는 객체라면 모두 저장할 수 있음   
사용하려면 데이터베이스 스키마를 지정하고, 데이터베이스와 통신을 연 후에, 일련의 트랜잭션을 통해 데이터를 가져오거나 업데이트해야함
