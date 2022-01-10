# 제네릭

제네릭이란 타입을 마치 함수의 파라미터처럼 사용하는 것을 의미한다
```js
function getText(text) {
  return text;
}

getText("hi"); // 'hi'
getText(10); // 10
getText(true); // true
```
제네릭으로
```js
function getText<T>(text: T): T {
  return text;
}

getText<string>('hi');
getText<number>(10);
getText<boolean>(true);
```

먼저 위 함수에서 제네릭 타입이 **<string>**이 되는 이유는 **getText()** 함수를 호출할 때 
제네릭(함수에서 사용할 타입) 값으로 **string**을 넘겼기 때문이다
인자로 문자열을 넘기면 getText함수를 아래와 같이 정의한 것과 같다
```js
function getText<string>(text: string): string {
  return text;
}
```

## 제네릭 사용하는 이유

```js
function logText<T>(text: T): T {
  return text;
}
```
함수의 인자와 반환 값을 모두 **T** 라는 타입을 추가한다
이렇게 되면 함수를 호출할 때 넘긴 타입에 대해 타입스크립트가 추정할 수 있게 된다
따라서 함수의 입력 값에 대한 타입과 출력 값에 대한 타입이 동일한지 검증할 수 있게 된다

이렇게 선언한 함수는 2가지 방법으로 호출할 수 있다
```js
// 1
const text = logText<string>("Hola world");
// 2
const text = logText("Hola world");
```
두번째 방법이 코드가 짧고 가독성도 좋아 흔하게 사용되지만
복잡한 코드에서는 타입 추정이 되지 않을 수 있다


## 제네릭 타입 변수

```js
function logText<T>(text: T): T {
  console.log(text.length); // Error T doesn't have .length
  return text;
}
```
위 코드를 변환하려고 하면 컴파일러에서 에러가 발생한다
**text**에 **.length**가 있다는 단서가 없기 때문이다
위 제네릭 코드는 함수의 인자와 반환 값에 대한 타입을 정하진 않았지만
입력 값으로 어떤 타입이 들어왔고 반환 값으로 어떤 타입이 나가는지 알 수 있다

이러한 경우 제네릭에 타입을 줄 수 있다
```js
function logText<T>(text: <Array>T): <Array>T {
  console.log(text.lenght);
  return text;
}
```


## 제네릭 타입

제네릭 인터페이스
```js
function logText<T>(text: T): T {
  return text;
}
// 1
let str: <T>(text: T) => T = logText;
// 2
let str: {<T>(text: T): T} = logText;
```

위와 같은 변형 방식으로 제네릭 인터페이스 코드를 작성할 수 있다
```js
interface GenericLogTextFn {
  <T>(text: T): T;
}

function logText<T>(text: T): T {
  return text;
}

let meyString: GenericLogTextFn = logText; // true
```
```js
interface GenericLogTextFn<T> {
  (text: T): T;
}

function logText<T>(text: T): T {
  return text;
}

let myString: GenericLogTextFn<string> = logText;
```


## 제네릭 클래스

```js
class GenericMath<T> {
  pi: T;
  sum: (x: T, y: T) => T;
}

let math = new GenericMath<number>();
```
제네릭 클래스를 선언할 떄 클래스 이름 오른쪽에 **<T>**를 붙여준다
그리고 해당 클래스로 인터페이스를 생성할 때 타입에 어떤 값이 들어갈 지 지정하면 된다


## 제네릭 제약 조건

```js
function logText<T>(text: T): T {
  console.log(text.length); // Error: T doesn't have .length
  return text;
}
```
인자와 타입에 선언한 **T**는 아직 어떤 타입인지 구체적으로 정의하지 않았기 때문에 **length**코드에서 오류가 난다
이럴 때 만약 해당 타입을 정의하지 않고도 **length** 속성 정도는 허용하려면 아래와 같이 작성한다
```js
interface LengthWise {
  length: number;
}

function logText<T extends LengthWise>(text: T): T {
  console.lo(text.length);
  return text;
}
```