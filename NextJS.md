# NextJS
### Library vs Framework
library는 개발자로서 자기가 사용하는 것(개발자가 주인). library를 불러와서 자기가 library를 사용해서 무언가를 한다. library를 사용할 때는, 원하는 대로 코드를 작성할 수 있고, 사용하고 싶을 때 사용할 수 있다. 리액트를 사용 할 때 Coomponents폴더를 만들거나 Routes폴더를 만든다든다지 할 수 있다. 언제 react를 부를지, 어떤 폴더 구조로 만들지 원하는대로 만들 수 있다. react 앱을 만드는데 많은 자유도가 있다.     

framework는 코드를 불러오는 것(개발자가 게스트). framework에서는, 코드를 적절한 위치에 잘 적기만 한다면 framework는 코드를 불러와서 동작하게 한다. nextJS같은 framework에서는, 특정한 규칙을 따라서 특정한 걸 해야한다. 우리가 그것들을 따랐을 때 모든 게 정상적으로 잘 동작한다. 예를 들어 ReactDOM.render 같은 부분에 직접 접근하지 못한다. 추상화 시킨 것. pages 폴더 안에 index파일을 만들면 자동적으로 어떤 설정이나 router 설치 없이 자동적으로 서버의 home부분에서 작동한다. page폴더안에 파일을 만들면 nextjs가 알아서 url을 만든다.    

함수의 이름은 중요하지 않고, 함수가 default export되는 것과 파일명이 중요하다. 파일명이 URL이 된다. 예외) index파일은 '/' 이것과 같음.

<img width="651" alt="스크린샷 2022-04-06 오후 9 29 10" src="https://user-images.githubusercontent.com/84711115/161974646-055309af-19f8-472d-89f0-d091616959f8.png">
<img width="416" alt="스크린샷 2022-04-06 오후 9 28 29" src="https://user-images.githubusercontent.com/84711115/161974557-2ee1937c-28d5-4057-ae09-c2ed98edeaf9.png">

### next.js의 가장 좋은 기능 중 하나는, 앱에 있는 페이지들이 미리 렌더링 된다는 것! 정적(static)으로
- create react app은 CSR(client side render)를 하는 앱을 만든다. 앱의 소스코드를 살펴보면, 하나의 div만 있다. ```<div id="root"></div>```를 제외하고는 모두 다 자바스크립트다. 브라우저가 자바스크립트, react 등 모든 것을 fetch한 후에야 UI가 보인다.
<img width="890" alt="스크린샷 2022-04-06 오후 9 55 32" src="https://user-images.githubusercontent.com/84711115/161979418-91d3246d-035e-487e-938c-688f114954b1.png">
        
              
- nextjs로 작성된 페이지의 소스코드를 보면, 실제 HTML이 있는 것을 볼 수 있다. 페이지가 미리 렌더링 된다는 것. 렌더링이 늦게 되더라도, 자바스크립트가 비활성화 되어 있어도, HTML 코드는 렌더링되어 볼 수 있다.
          
<img width="597" alt="스크린샷 2022-04-06 오후 9 53 57" src="https://user-images.githubusercontent.com/84711115/161979268-53f4bac5-3649-4388-b08b-d5fc554268c1.png">

#### 페이지를 열면 보게 되는 것이 HTML, 그리고나서 react.js가 전송됐을 때, react.js 앱이 된다. react.js를 프론트엔드 안에서 실행하는 것을 hydration이라고 부른다.
1. next.js는 react.js를 백엔드에서 동작시켜서 페이지를 미리 만드는데, component들은 render시키고, rendering이 끝났을 때는 HTML이 된다.
2. next.js는 그 HTML을 페이지의 소스코드에 넣어준다(SEO에 정말 좋음).
3. 유저는 자바스크립트와 react.js가 로딩되지 않았더라도 콘텐츠를 볼 수 있게 된다.
4. react.js가 로딩 되었을 때 기본적으로 존재하는 것들과 연결이 되어서 일반적인 react.js 앱이 된다.

css style은 ```<style jsx>{``}</style>``` 을 사용한다. global style은 ```<style jsx global>{``}</style>```   
모든 페이지에 적용할 수 있게 하려면, `pages/_app.js` 파일을 만들어서 `<NavBar />` 를 가져오고, `<style jsx global>{``}</style>` 도 적용해 준다. 이때 `_app.js` 파일 이름은 고정되어 있다.



