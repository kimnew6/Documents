# SPA 장단점
#### SPA(Single Page Application)는 한 개(Single)의 Page로 구성된 Application
SPA는 웹 에플리케이션에 필요한 모든 정적 리소스(HTML, CSS, JavaScript)를 최초 한 번에 다운로드 <br>
그 이후 새로운 페이지 요청이 있을 때, 페이지 갱신에 필요한 데이터만 전달 받아서 페이지를 갱신 <br>
<b>SPA를 CSR(Client Side Rendering)</b> 방식으로 렌더링한다고 말한다.<br>
<b>MPA를 SSR(Server Side Rendering)</b> 방식으로 렌더링한다고 말한다.<br>
즉, 첫 요청시 딱 한 페이지만 불러오고 페이지 이동 시 기존 페이지의 내부를 수정해서 보여주는 방식이다.<br>
이를 클라이언트 관점에서 말하자면 최초 페이지를 로딩한 시점부터는 페이지 리로딩 없이 필요한 부분만 서버로 부터 받아서 화면을 갱신하는 것이다.<br>필요한 부분만 갱신하기 때문에 네이티브 앱에 가까운 자연스러운 페이지 이동과 사용자 경험(UX)을 제공할 수 있다.<br>
Angular, React, Vue 등 프론트엔드 기술들이 나오면서 크게 유행하고 있다.
### SPA 장점
1. 자연스러운 사용자 경험 (UX)
- 전체 페이지를 업데이트 할 필요가 없기 때문에 빠르고 '깜빡' 거림이 없다.
2. 필요한 리소스만 부분적으로 로딩 (성능)
- SPA의 Application은 서버에게 정적리소스를 한 번만 요청한다.그리고 받은 데이터는 전부 저장해놓는다.
3. 서버의 템플릿 연산을 클라이언트로 분산 (성능)
4. 컴포넌트별 개발 용이 (생산성)
5. 모바일 앱 개발을 염두에 둔다면 동일한 API를 사용하도록 설계 가능 (생산성)
### SPA 단점
1. JavaScript 파일을 번들링해서 한 번에 받기 때문에 초기 구동 속도가 느리다. (Webpack의 code splitting으로 해결 가능)
2. 검색엔진최적화(SEO)가 어려움 (SSR로 해결 가능)
3. 보안 이슈 (프론트엔드에 비즈니스 로직 최소화)
- SSR에서는 사용자에 대한 정보를 서버측에서 세션으로 관리를 하지만 CSR 방식에서는 클라이언트측의 쿠키말고는 사용자에 대한 정보를 저장할 공간이 마땅치 않다.
#### SPA 방식이 모두 CSR인 것은 아니다.

# SPA 단점을 보완할 수 있는 방법은?
### SSR (Server Side Rendering)
SEO 구축이 필요한 상황이라면 SPA를 SSR (서버사이드렌더링) 방식으로 구축하여야합니다.<br>
SPA이지만 크롤링에 더 친화적인 SSR 방식으로 사이트를 구축하는 것이 SEO의 관점에서 적합합니다<br>
대표적인 SSR 프레임워크로는 React의 Next.js, Vue의 Nuxt, Angular의 Angular Universal이 있습니다.<br>
 ### Pre-rendering (사전 렌더링)
 만약 우리 사이트가 이미 SPA의 CSR 방식으로 구현되어있거나, SSR방식으로 개발이 불가한 경우 Pre-rendering (사전랜더링)을 통해 SEO할 수 있습니다.<br>
 Pre-rendering은 서버에서 요청하는 자가 사람인지 크롤러인지 판단하여 사람에게는 HTML과 js 등을 제공하고 크롤러에게는 사전에 렌더링된 HTML 버전의 페이지를 보여주는 방식입니다. 즉, 크롤러는 서버에서 이미 렌더링된 HTML 버전의 소스를 손쉽게 읽을 수 있게 됩니다.<Br>
 Pre-rendering 라이브러리로는 react-helmet, prerender-spa-plugin, prerender.io, puppeteer, rendertron 등이 있습니다.
 ### History API
  History API는 SPA방식의 웹사이트에서 주소가 바뀌지 않는 문제를 해결하기 위해 싱글페이지이지만 주소를 부여하는 기능의 API입니다.<Br>
  과거 SPA환경에서 #또는 #!을 통해 주소를 구분하였지만 현재는 History API와 pushState() 방법을 통해 특수문자로 된 주소가 아닌 정적인 URL과 같은 주소를 설정할 수 있게 되었습니다. SEO의 관점에서 이는 크롤링뿐만 아니라 백링크를 얻기 용이하게 되었다고 볼 수 있습니다.
