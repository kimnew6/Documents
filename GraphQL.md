## GraphQL
### Apollo Client
**Apollo Client는 GraphQL 기반의 라이브러리로, 클라이언트 애플리케이션의 GraphQL과 데이터 교환을 돕는다. React에서 사용하는 Apollo Client를 특별히 React Apollo라고 부른다.**   

리액트에는 ContextAPI, Redux, MobX 등 전역으로 상태관리를 하기 위한 많은 선택지가 있다. Apollo Client도 그 중 하나의 선택지로 로컬에서 전역 상태관리를 하기위해 사용할 수 있다.

원래 Apollo Client는 GraphQL을 사용해 서버와 통신을 하며 반환 값을 캐시로 보관하는 상태 관리 라이브러리이다. 하지만 일부 서비스는 서버 없이 완전히 독립적으로 작동할 수 있고, Apollo Client는 그런 경우에도 로컬 상태를 관리할 수 있다. 즉, Apollo Client만 사용해 전역 상태관리를 할 수 있다.

물론 서버가 있는 경우에도 GraphQL 통신으로 가져온 상태와 로컬 상태 모두 함께 관리할 수 있다. 그렇기 때문에 이미 클라이언트에서 Apollo Client를 사용하고 있다면 굳이 Redux나 MobX같은 추가적인 상태관리 라이브러리를 사용하지 않고도 충분히 전역 상태관리를 적용할 수 있다. 😀

### GraphQL
Graph QL(이하 gql)은 Structed Query Language(이하 sql)와 마찬가지로 쿼리 언어. 페이스북이 개발.   
GraphQL은 웹 클라이언트가 데이터를 서버로 부터 효율적으로 가져오는 것이 목적. 서버측 런타임으로 클라이언트에게 요청한 만큼의 데이터를 제공하는 데 우선 순위를 둠.   
GraphQL의 문장은 주로 클라이언트 시스템에서 작성하고 호출한다.   
GraphQL은 서버 API를 통해 정보를 주고받기 위해 사용하는 질의 언어(query language)이다. GraphQL API는 보통 하나의 엔드포인트를 사용하며, 요청 시 사용하는 질의문에 따라 응답의 구조가 달라진다.  
#### REST API와 비교
**REST API**
- URL, METHOD등을 조합하기 때문에 다양한 Endpoint가 존재
- 특정 기능을 위해 `여러번` API가 호출 됨
- 특정 요청에 fit한 응답을 돌려주기 위해서는 API를 `새로` 만들어야함
- API `유지보수`의 어려움


**GraphQL**
- 단 하나의 Endpoint가 존재
- API에서는 불러오는 데이터의 종류를 쿼리 조합을 통해서 결정
- gql API를 사용하면 여러번 네트워크 호출을 할 필요 없이, 한번의 네트워크 호출로 처리 할 수 있습니다.
- 
예를 들면, REST API에서는 각 Endpoint마다 데이터베이스 SQL 쿼리가 달라지는 반면, gql API는 gql 스키마의 타입마다 데이터베이스 SQL 쿼리가 달라집니다.

![image](https://user-images.githubusercontent.com/84711115/159873939-33846880-61c6-458b-905e-193b6f163a8f.png)

#### GraphQL의 장점
- 하나의 Endpoint를 지님으로써, API나 View를 따로 구성할 필요가 없어진다. 요청을 보낼때는 정해진 한 군데로만 요청을 보내면 되고, 그 외의 API를 신경쓸 필요가 없어져, 유지보수가 용이해진다.
- 한번의 요청으로 원하는 모든 데이터를 서버로부터 요청하여 가져온다. `Overfetching`이나 `Underfetching`등의 문제가 발생하지 않는다.   
`Overfetching` : 원하는 data 이상의 정보를 요청받는 것, data의 정제에 리소스가 낭비  
`Underfetching` : 원하는 data의 정보를 요청받기 위해 여러번 요청을 보내는 것, 네트워크를 통해 여러번 접근을 하여 리소스 낭비  
- 기종에 상관없는 API
- Redux를 대체할 Apollo : Redux와 Universal Router를 사용할 때보다 프로세스가 `간결`해졌다.

#### GraphQL의 단점
- HTTP 캐싱 :  GraphQL은 `하나`의 URL로 처리하기에, HTTP에서 제공하는 캐싱 전략을 그대로 사용하는 것은 `불가능`하다.
- 파일 업로드 : GraphQL은 지속적으로 성장하는 생태계로써, 완성된 명세가 `존재하지 않는다`. 따라서 이 외의 것들은 `직접` 개발할 수 밖에 없게 된다. 다른 대안을 이용하여 파일 업로드 구현.
- 요청 필터링의 어려움 : GraphQL은 클라이언트가 필요한 데이터를 스스로 결정하여 요청. 따라서 GraphQL의 다양한 요청형태에서 잘못된 요청을 필터링하기가 `까다롭다`.

#### 질의문으로 실행할 수 있는 작업 유형(operation type)에는 다음과 같이 query, mutation, subscription이 있다. 각 유형을 용도에 맞게 사용해야 한다.
![image](https://user-images.githubusercontent.com/84711115/159867534-cb81e87a-07c7-4b83-b18a-d34a84d35f5a.png)

- query: 데이터를 받아올 때 사용한다.
- mutation: 데이터를 생성, 수정, 삭제할 때 사용한다.
- subscription: 웹소켓을 사용해 실시간 양방향 통신을 구현할 때 사용한다.

개발 환경 설정
GraphQL을 사용하려면 다음과 같은 순서로 기본적인 서버 환경을 설정해야 한다.

1. GraphQL 스키마를 작성한다.
2. resolve 함수를 작성한다.
3. GraphQL 스키마와 resolver 함수를 병합한다.
4. 서버 환경을 설정한다.

![image](https://user-images.githubusercontent.com/84711115/159867483-161da63a-3cb4-43c7-b228-c69ffeb9cd58.png)

Redux와 Apollo Client의 차이점을 알아보고 기본 환경을 설정하는 방법을 살펴봤다.

Redux는 REST API를 사용하기 때문에 리소스의 크기가 서버에서 결정된다. 데이터 교환이 복잡하게 이루어지고, 엔드포인트 증가 및 overfetching과 underfetching 등의 문제점을 가지고 있다. 반면에 Apollo Client는 GraphQL을 기반으로 한다. 서버에서는 어떠한 자원을 사용할 수 있는지 정의하고, 클라이언트에서 렌더링에 필요한 데이터를 요청하는 방식이다. 꼭 필요한 데이터 교환이 이루어지기 때문에 매우 깔끔하며 효과적이다.

하지만 두 방법 중 어느 것이 더 좋다고 단정 지어 말하기는 어렵다. 최신 기술을 적용하기 전에 서비스의 방향성 및 개발 환경에 따라 어느 한쪽 또는 양쪽 모두를 사용할 수 있기 때문이다.
