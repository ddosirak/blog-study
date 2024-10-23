package.json을 보다가 dependencies와 devDependencies를 보고 무슨 차이가 있는지 궁금했다. 한번 정리를 해봐야 할 것 같아서 알아보았다!

### dependencies

애플리케이션 동작에 필요한 라이브러리를 dependencies에 설치한다. dependencies에 설치된 라이브러리는 배포에 포함된다. 주로 react, react-router-dom, react-query 등이 dependencies에 들어간다.

</br>

### dependencies 설치 방법

```typescript
npm i
```

</br>

### devDependencies

애플리케이션 동작과 직접적인 연관은 없지만, 개발할 때 필요한 라이브러리를 설치한다. devDependencies에 설치된 라이브러리는 배포에 포함되지 않는다. 주로 어플의 로직과 필요하지 않은 라이브러리를 설치할 때 사용한다.

</br>

### devDependencies 설치 방법

```typescript
npm i -D
```

```typescript
npm i -dev
```

</br>

### devDependencies 사용하는 이유

devDependencies에 설치된 라이브러리는 배포에 포함되지 않기 때문에 build 시 시간 소요와 의존성을 줄일 수 있고, 최종 결과물의 크기도 줄일 수 있다.

```typescript
"devDependencies": {
    "@types/howler": "^2.2.8",
    "gh-pages": "^5.0.0",
    "tailwindcss": "^3.3.3",
    "typescript": "^5.0.2",
    "vite": "^4.4.5"
},
"dependencies": {
    "howler": "^2.2.3"
}
```

</br>

### devDependencies에 설치할 수 있는 라이브러리

-   typescript
-   vite
-   tailwindcss
-   webpack
-   esLint
-   sass 등
