컴포넌트를 개발하면서 보통 `<div>`, `<span>` 등의 태그를 많이 사용했는데, 코드만 보고 어떤 콘텐츠인지 이해하기 힘들었다. 개발자도구로 Dom의 요소를 확인할 때도 `<div>` 태그가 많아서 파악하는데 시간이 오래 걸렸다. 의미를 담고 있는 태그를 사용하면 명시적이고 직관적인 컴포넌트 설계가 가능할 것 같았다. 그래서 시맨틱 태그를 사용해보기로 했다.

### Semantics

시맨틱은 코드 조각의 ‘의미’를 나타낸다. 즉 시맨틱 태그는 의미가 있는 태그이다. 시맨틱 태그의 요소로는 header, nav, form, article 등이 있으며 태그를 통해 이름만 보고도 어떤 내용인지 유추할 수 있다.

![이미지 출처 : https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYvHzj%2FbtsKm4jLBvi%2FsDKap0zZ1YLV4qsRauIWC1%2Fimg.png](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYvHzj%2FbtsKm4jLBvi%2FsDKap0zZ1YLV4qsRauIWC1%2Fimg.png)

### 시맨틱 태그 요소

header : 로고나 제목 등이 포함된 페이지 상단
footer : 저작권, 연락처, 작성자 정보 등이 포함된 페이지 하단
main : 페이지의 주요 콘텐츠를 감싸는 요소
section : 페이지에서 여러 항목들을 감싸는 요소
article : 독립적인 글(컨텐츠)을 다루는데 사용하는 태그
aside : 사이드바와 같이 옆에 위치하는 컨텐츠를 담는 태그
details : 사용자가 보거나 숨길 수 있는 추가 세부 정보를 정의하는 태그. 사용자와 상호 작용이 가능하며 버튼을 통해 열고 닫을 수 있다.
nav : 웹사이트의 메뉴, 탭, 탐색경로 등 탐색 링크가 포함된 태그
summary : 상세 요소의 요약 등을 포함하는 태그
이 외에도 설명 목록을 나타내는 `dl`, 목록의 항목을 나타내는 `li`, 하나의 문단을 정의하는 `p` 태그 등의 텍스트 콘텐츠뿐만 아니라 이미지 태그인 `img`, 비디오와 오디오 태그인 `video`, `audio` 등 멀티미디어 컨텐츠 태그 등이 있다.

✅ 더 많은 태그 보러가기 https://developer.mozilla.org/ko/docs/Web/HTML/Element#inline_text_semantics

### 시맨틱 태그 특징

#### 1. 검색 엔진 최적화 (SEO)

검색 엔진 최적화란 웹 페이지 검색 엔진이 자료를 수집하고 순위를 부여하는 방식에 맞게 웹 페이지를 구성해서 검색 결과의 상위에 나올 수 있게 하는 것이다. 검색 엔진이 인덱스를 생성하는데 사용하는 정보는 HTML 코드인데, 의미를 명확하게 나타내는 시맨틱 태그는 이러한 인덱스 생성에 영향을 준다. 그래서 시맨틱 태그를 사용한 웹페이지는 검색 엔진 결과 페이지에서 상위에 노출될 확률이 높다.

#### 2. 스크린 리더

스크린 리더는 시각 장애가 있는 사용자에게 화면을 읽어주는 역할을 한다. `<div>` 태그나 `<span>` 태그 등 의미를 알 수 없는 태그보다는 `<header>`, `<section>` 등 의미가 포함된 태그를 전달하면 사용자가 쉽게 이해하는데 도움이 된다.

#### 3. 접근성 및 가독성 향상

시맨틱 태그는 코드 블록을 찾기 쉽고, HTML의 구조를 파악하기 수월하다. 태그가 거의 `<div>` 이면 Dom의 레이아웃을 확인할 때, 어떤 div가 어떤 컨텐츠인지 구분하기 힘들 것이다. 또한 콘텐츠의 명확하고 구조화된 설계가 가능하다는 장점이 있다. 다른 사람이 코드를 파악할 때도 태그만 보고 코드의 의미를 파악할 수 있어서 유지보수와 협업을 할 때도 편리하다.