> 반응형 웹을 개발하면서 height를 100vh로 설정하는 경우 일부 화면이 모바일 브라우저 내 상단바 혹은 하단바에 의해 가려지는 문제가 있었다. `vh(viewport)`는 상하단바를 제외한 영역을 기준으로 한다. 따라서 다음과 같은 viewport 단위를 적절하게 사용해주어야 한다.
> 

![이미지 출처 : https://blanche-toile.com/web/large-small-and-dynamic-viewport-units](https://velog.velcdn.com/images/7im2108/post/b171543d-ddbc-402c-9aa0-8ae55be5eb1c/image.png)

# 📌vh (Viewport Height)

`vh`는 스크린의 height를 기준으로 하여 백분위로 높이를 나타낸다. 예를들어 스크린 height가 800px인 경우 1vh는 8px이 되는 것이다. 모바일에서는 상하단바 유무와 상관없이 일정한 크기로 동작하는 정적 viewport 단위이다.

# 📌dvh (Dynamic Viewport Height)

`dvh`는 동적 viewport height를 기준으로 하여 백분위로 높이를 나타낸다. 동적 viewport를 기준으로 하기 때문에 상하단바 등의 UI요소에 따라 높이가 유동적으로 변동된다. 반응형 웹을 고려할 때 유용하게 사용된다.

# 📌svh (Small Viewport Height)

`svh`는 최소 viewport 높이를 기준으로 하여 백분위로 높이를 나타낸다. 모바일에서 상하단바가 노출되지 않는 경우에도 상하단바가 있는 경우를 고려하여 최소 viewport를 기준으로 하는 것이다. 예외적인 상황을 고려하여 어떤 경우에서도 콘텐츠가 적절하게 표시되도록 하고싶을 때 유용하다.

# 📌lvh (Large Viewport Height)

`lvh`는 최대 viewport 높이를 기준으로 하여 백분위로 높이를 나타낸다. fullscreen에 가까운 상태를 가정한다. `vh`와의 차이점은 `vh`는 초기 viewport를 기준으로 한 정적 단위이지만, `lvh`는 계속해서 최대 viewport를 반영하는 동적 단위라는 점이다.

| 단위 | 기준 | 뷰포트 변화 반영 |
| --- | --- | --- |
| `vh` | 고정 뷰포트 높이 | ❌ |
| `dvh` | 동적 뷰포트 높이 | ✅ |
| `svh` | 최소 뷰포트 높이 | ✅  |
| `lvh` | 최대 뷰포트 높이 | ✅  |