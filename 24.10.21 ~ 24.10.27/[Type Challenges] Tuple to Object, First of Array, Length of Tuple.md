# **📌Tuple to Object**


> 배열(튜플)을 받아, 각 원소의 값을 key/value로 갖는 오브젝트 타입을 반환하는 타입을 구현하세요.
>
>```tsx
>const tuple = ['tesla', 'model 3', 'model X', 'model Y'] as const
>
>type result = TupleToObject<typeof tuple> // expected { 'tesla': 'tesla', 'model 3': 'model 3', 'model X': 'model X', 'model Y': 'model Y'}
>```


반복문이므로 Mapped type을 사용해야 한다. 

`T` 배열의 n번째 요소를 `K`라고 하고, `K`가 key일 때 value도 `K`로 정의할 수 있다.

참고로 튜플을 순회할 때에는 `number`를 사용하면 된다.

```tsx
type TupleToObject<T extends readonly any[]> = {
  [K in T[number]]: K;
}
```

---

# 📌First of Array


>배열(튜플) `T`를 받아 첫 원소의 타입을 반환하는 제네릭 `First<T>`를 구현하세요.
>
>```tsx
>type arr1 = ['a', 'b', 'c']
>type arr2 = [3, 2, 1]
>
>type head1 = First<arr1> // expected to be 'a'
>type head2 = First<arr2> // expected to be 3
>```

</aside>

위 문제의 경우 단순하게 `type First<T extends any[]> = T[0]`으로 정의해주었다. 더불어 빈 배열의 경우 `never` 타입을 가지도록 다음과 같이 `First<T>`를 정의한다.

```tsx
type First<T extends any[]> = T extends [] ? never : T[0];
```

그 외의 답안으로는 아래와 같은 것들이 있었다.

먼저 `T['length']`로 배열의 길이를 먼저 판단하고 타입을 지정해주는 방식이다. 

```tsx
type First<T extends any[]> = T['length'] extends 0 ? never : T[0]
```

다음 방법은 `infer`를 사용하는 방법이다. `infer`는 타입을 추론할 때 사용된다. 정확한 타입을 정의하지 않고 어떤 타입을 추론하고 싶을 때 사용한다. 

아래 정의한 `type First`를 보면 `T extends [infer R, …infer _]` → 이 부분은 배열의 첫번째 요소인 `R`을 추론하는 것이며, 이 경우 `T`는 빈배열일 수 없다. 첫번째 요소인 `R`이 존재하기 때문! `…infer _` 는 그 뒤에 오는 배열의 요소들을 나타낸다. 따라서 `T`의 배열 첫번째 요소가 존재할 때에는 `R`, 빈 배열일 때에는 `never` 타입을 가지게 되는 것이다.

```tsx
type First<T extends any[]> = T extends [infer R, ...infer _] ? R : never
```

---

# 📌**Length of Tuple**


>배열(튜플)을 받아 길이를 반환하는 제네릭 `Length<T>`를 구현하세요.
>
>```tsx
>type tesla = ['tesla', 'model 3', 'model X', 'model Y']
>type spaceX = ['FALCON 9', 'FALCON HEAVY', 'DRAGON', 'STARSHIP', 'HUMAN SPACEFLIGHT']
>
>type teslaLength = Length<tesla>  // expected 4
>type spaceXLength = Length<spaceX> // expected 5
>```


앞선 문제의 답안에서 힌트를 얻어서 `type Length<T extends any[]> = T['length']` 라고 작성하였으나,

The type `readonly […]' is 'readonly' and cannot be assigned to the mutable type 'any[]'.` 라는 에러가 나서 배열 타입 앞에 `readonly`를 붙여주어 해결하였다.

```tsx
type Length<T extends readonly any[]> = T['length']
```
  
> **💡 왜 arr.length는 안되고 arr['length']는 될까?**
>
>앞선 문제들을 풀어나가며 궁금했던 점은 배열의 길이를 참조할 때 `arr.length` 형태는 사용 불가능하고 `arr['length']` 형태는 사용 가능한 점이었다.
>
>그 이유는 TypeScript의 타입 시스템은 정적 타입 검사기로 런타임 속성을 다루지 않기 때문이라고 한다. `.length`는 런타임에 배열의 길이를 참조하기 떄문에 사용할 수 없으나 `['length']`의 경우 객체의 속성에 접근하는 방법이기 때문에 타입 레벨에서 사용할 수 있다.