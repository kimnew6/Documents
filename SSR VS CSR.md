# SSR vs CSR?
## SSR
#### Server Side Rendering의 약자
#### 서버 쪽에서 렌더링 준비를 끝마친 상태로 클라이언트에 전달하는 방식
<BR>![image](https://user-images.githubusercontent.com/84711115/148543773-6e5f8fb3-3025-4a6c-86f4-0ca342ac2bb1.png)
#### SSR의 단계
  1. User가 Website 요청을 보냄
  2. Server는 'Ready to Render'. 즉시 렌더링 가능한 HTML 파일을 만든다.(리소스 체크, 컴파일 후 완성된 HTML 컨텐츠로 만든다.)
  3. 클라이언트에 전달되는 순간, 이미 렌더링 준비가 되어있기 때문에 HTML은 즉시 렌더링 된다. 사이트 자체는 조작 불가능.(JavaScript 읽히기 전)
  4. 클라이언트가 자바스크립트를 다운받는다.
  5. 다운 받아지고 있는 사이에 유저는 컨텐츠는 볼 수 있지만 사이트를 조작 할 수는 없다. 이때의 사용자 조작을 기억하고 있는다.
  6. 브라우저가 JavaScript 프레임워크를 실행한다.
  7. JavaScript까지 성공적으로 컴파일 되었기 때문에 기억하고 있던 사용자 조작이 실행되고 이제 웹 페이지는 상호작용 가능해진다.
  ![image](https://user-images.githubusercontent.com/84711115/148545668-dfbf2a36-dedb-4257-9366-291a4ed7ed21.png)
  #### 서버에서 이미 '렌더 가능한' 상태로 클라이언트에 전달되기 때문에, JavaScript가 다운로드 되는동안 사용자는 무언가를 보고 있을 수 있다.
## CSR
  #### Client Side Rendering의 약자
  #### SSR과 달리 렌더링이 클라이언트 쪽에서 일어난다.
  서버는 요청을 받으면 클라이언트에 HTML과 JavaScript를 보내준다. 클라이언트는 그것을 받아 렌더링을 시작한다.
![image](https://user-images.githubusercontent.com/84711115/148545094-882d6502-2751-4945-90c4-fa45a6e6979e.png)
#### CSR의 단계
  1. User가 Website 요청을 보냄
  2. CDN(엔드 유저의 요청에 '물리적'으로 가까운 서버에서 요청에 응답하는 방식)이 HTML 파일과 JS로 접근할 수 있는 링크를 클라이언트로 보낸다.
  3~4. 클라이언트는 HTML과 JS를 다운로드 받는다. (이때 SSR과 달리 유저는 아무것도 볼 수 없다.)
  5. 다운이 완료된 JS가 실행된다. 데이터를 위한 API가 호출된다. (이 때 유저들은 placeholder를 보게된다.)
  6. 서버가 API로부터의 요청에 응답한다.
  7. API로부터 받아온 data를 placeholder 자리에 넣어준다. 이제 페이지는 상호작용이 가능해진다.
![image](https://user-images.githubusercontent.com/84711115/148545755-8009b602-a083-42f8-a8fc-185bcd0fffd8.png)
#### 서버에서 처리 없이 클라이언트로 보내주기 때문에 JS가 모두 다운로드 되고 실행이 끝나기 전까지 사용자는 볼 수 있는게 없다.
## SSR vs CSR
  ### 웹페이지를 로딩하는 시간
  - 첫 페이지 로딩시간 <BR>
  CSR은 HTML, CSS와 모든 스크립트들을 한 번에 불러옴 <BR>
  SSR은 필요한 부분의 HTML과 스크립트만 불러옴 <BR>
  #### 평균적으로 SSR이 더 빠르다.
  - 나머지 로딩 시간<BR>
  CSR은 이미 첫 페이지 로딩할 때 나머지 부부을 구성하는 코드를 받아왔기 때문에 빠르다.<BR>
  반면, SSR은 첫 페이지를 로딩한 과정을 정확하게 다시 실행한다. 그래서 더 느림.
  ### SEO(Search Engine Optimization)
  대부분의 웹 크롤러, 봇들은 JS를 실행시키지 못하고 HTML에서만 컨텐츠를 수집하기 때문에 CSR 방식으로 개발된 페이지를 빈 페이지로 인식하게 된다. <br>
  SSR 방식은 View를 서버에서 렌더링하기 때문에 HTML에 컨텐츠가 저장되어 있어 SEO를 사용하는데 문제가 없다.<br>
  (최근 구글이 트렌드를 바꾸고 있음. 구글의 경우 크롤러 내부에 JS 엔진이 있음. 구글은 CSR방식으로도 SEO 측면에서 문제없음.)
  ### 서버 자원 사용
  SSR이 서버 자원을 더 많이 사용한다. 매번 서버에 요청을 하기 때문이다.<br>
  반면 CSR은 서버 부하가 적다.
  
  
  ![img1 daumcdn](https://user-images.githubusercontent.com/84711115/148548651-f44562ea-9431-4210-a135-332027e2e416.jpg)

# CSR과 SSR이 next js 기반에서 어떻게 다른지(왜 ssr이 필요한지/ CRA와 다른 게 뭔지)
  ### NextJS
  SSR개념을 React에 입힌 프레임워크를 제공한다. 리액트는 CSR.<br>
  둘의 장점만을 조합해 처음엔 SSR로 렌더링을 하고 이후 다른 페이지에선 CSR을 활용하는 방식이다. 이를 활용해 좋은 사용자 경험과 SEO등 최적화 문제를 해결할 수 있다.
  
