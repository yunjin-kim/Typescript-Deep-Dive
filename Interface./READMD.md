# Interface

oject 타입은 인터페이스와 클래스의 상위 타입이다
object 타입은 속성이 다른 객체를 모두 자유롭게 담을 수 있다
```js
let obj: object = { name: 'Hong', age: 22 }
```
이 코드에서 object 타입은 마치 객체를 대상으로 하는 any 타입처럼 동작한다
타입스크립트의 인터페이스 구문은 이렇게 동작하지 않게 하려는 목적으로 고안되었다
변수 obj에는 항상 name과 age 속성으로 구성된 객체만 가질 수 있게 한다

## 인터페이스 선언문

타입스크립트는 객체 타입을 정의할 수 있게 하는 interface라는 키워드를 제공한다
```js
interface 인스페이스이름 {
  속성이름: 속성타입
}
```

```js
interface Person {
  name: string;
  age: number;
}
```
Person 인터페이스의 목적은 name과 age라는 이름의 속성이 둘 다 있는 객체만 유효하도록
객체의 타입 범위를 좁히는데 있다


## 선택 속성 구문

인터페이스를 설계할 때 어떤 속성은 반드시 있어야 하지만 어떤 속성을 없어도 상관없는 형태로 만들고 싶을 땐
선택 속성 구문을 사용하면 된다
속성 이름뒤에 물음표 기호를 붙여서 만든다
```js
interface Person {
  name: string;
  age: number;
  etc?: boolean; 
}

let person1: Person = { name: 'Hong', age: 22 };
let person2: Person = { name: 'Hong', age: 22, etc: false};
```


## 익명 인터페이스

타입스크립트는 interface 키워드도 사용하지 않고 인터페이스의 이름도 없는 인터페이스를 만들 수 있다
이를 **익명 인터페이스**라고 한다
```js
let person: {
  name: string;
  age: number;
  etc?: booleaen;
} = { name: 'Hong', age: 22 }
```

익명 인터페이스 사용 예
```js
function printMe(me: { name: string, age: number, etc?: boolean }) {
  console.log(
    me.etc 
    ? `${me.name} ${me.age} ${me.etc}`
    : `${me.name} ${me.age}`
  )
}
printMe(person) // Hong 22
```