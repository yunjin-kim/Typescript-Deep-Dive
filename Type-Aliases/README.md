# Type Aliases

타입 별칭은 특정 타입이나 인터페이스를 참조할 수 있는 타입 변수를 의미한다
```js
// string 타입을 사용할 때
const name: string = 'string'

// 타입 별칭을 사용할 때
type MyName = string;
const name: MyName = 'string';
```

**interface**레벨의 복잡한 타입에도 별칭을 부여할 수 있다
```js
type Develop = {
  name: string;
  skill: string;
}
```

타입 별칭은 제네릭도 사용할 수 있다
```js
type User<T> = {
  name: T
}
```


## 타입 별칭의 특징

타입 별칭은 새로운 타입 값을 하나 생성하는 것이 아니라 정의한 타입에 대해
나중에 쉽게 참고할 수 있게 이름을 부여하는 것과 같다

인터페이스로 선언한 타입을 VSCode 프리뷰 확인 결과
```js
interface Devolop {
  name: string;
  skill: string
}

//        interface Devolop
let hong: Devolop;
```

타입 별칭으로 선언한 티입을 VSCode 프리뷰 확인 결과
```js
type Devolop = {
  name: string;
  skill: string
}

//        type Devolop = {
//            name: string;
//            skill: string;
//        }
let hong: Devolop;
```

인터페이스는 확장이 가능한 반면
타입 별칭은 확장이 불가능하다

**좋은 소프트웨어는 언제나 확장이 용이해야 한다는 원칙**에 따라
가급적이면 인터페이스로 선언하는 것이 좋다