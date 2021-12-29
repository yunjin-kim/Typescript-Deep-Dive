## Boolean

**boolean**값은 참 / 거짓 값이다
```js
let isTrue: boolearn = true;
```

## Number

typescript의 모든 숫자는 부동 소수 값이다
부동 소수에는 **number**라는 타입이 붙혀진다
16진수, 10진수, 2진수, 8진수 리터럴도 지원한다
```js
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

## String

typescript는 텍스트 데이터 타입을 **string**으로 표현하고
큰따음표(")나 작은따음표(')를 문자열 데이터를 감싸는데 사용한다

```js
let color: string = "blue";
color = 'red';
```
또한 템플릿 문자열을 사용하면 여러 줄에 걸쳐 문자열을 작성할 수 있고 표현식을 포함시킬 수 있다
이 문자열은 백틱(`) 문자로 감싸지며 **${ expr }**과 같은 형태로 표현식을 포함시킬 수 있다
```js
let fullName: string = `Hong Siyoung`;
let intro: string = `Hola my name is ${fullName}`;
```

## Array

typescript는 배열 타입을 두가지 방법으로 쓸 수 있다

- 배열 요소들을 나타내는 타입 뒤에 **[]**를 쓰는 것이다
```js
let list: number[] = [1, 2, 3];
```

- 제네릭 배열 타입을 쓰는 것이다**Array<elemType>**
```js
let list: Array<number> = [1, 2, 3];
```


## Tuple

튜플 타입을 사용하면 요소의 타입과 개수가 고정된 배열을 표현할 수 있다
단 요소들의 타입이 모두 같을 필요는 없다
```js
// 튜플 타입으로 선언
let x: [string, number];
// 초기화
x = ["hola", 11]; 

// 잘못된 초기화
x = [10, "hola"];
```

정해진 인덱스에 위치한 요소에 접근하려면 해당 타입이 나타난다
```js
console.log(x[0].substring(1)); // ola
console.log(x[0].substring(1)); // Error
```

정해진 인덱스 외에 다른 인덱스에 있는 요소에 접근하면 오류가 발생한다
```js
x[3] = 'world'; // Error
```


## Enum

javascript의 표준 자료형 집합과 사용하면 도움이 될만한 데이터형은 **enum**이다
**enum**은 값의 집합에 더 나은 이름을 붙여줄 수 있다
```js
enum Color { Red, Green, Blue }
let c: Color = Color.Green;
```

기본적으로 **enum**은 0부터 시작하여 멤버들의 번호를 매긴다
멤버 중 하나의 값을 수동으로 설정하여 번호를 바꿀 수 있다
```js
// 0 대신 1 부터 시작해 번호를 매긴다
enum Color { Red = 1, Green, Blue }
let c: Color = Color.Green;
```

```js
// 모든 값을 수동으로 설정할 수 있다
enum Color { Red = 1, Grren = 2, Blue = 4 }
let c: Color = Color.Grren;
```

**enum**의 유용한 기능 중 하나는 매겨진 값을 사용해 enum 멤버의 이름을 알아낼 수 있다는 것이다
위 예제에서 2라는 값이 위의 어떤 **Color** enum 멤버와 매칭되는지 알 수 없을 때
이에 일치하는 이름을 알아낼 수 있다
```js
enum Color { Red = 1, Green, Blue }
let colorName: string = Color[2];

console.log(colorName); // Green
```