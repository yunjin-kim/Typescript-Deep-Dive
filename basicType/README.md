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


## Enum (열거)

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


## Any

사용자로부터 받은 데이터나 서드 파티 라이브러리 같은 동적인 컨텐츠에서 알지 못하는 타입을 표현해야 할 수도 있다
이 경우 타입 검사를 하지 않고, 그 값들이 컴파일 시간에 검사를 통과하길 원한다
이 경우 **any** 타입을 사용할 수 있다
```js
let notSure: any = 4;
notSure = "can instead string";
```
**any**타입은 기존에 자바스크립트로 작업할 수 있는 강력한 방법으로,
컴파일 중에 점진적으로 타입 검사를 하거나 하지 않을 수 있다
**Object**가 비슷한 역할을 할 수 있을 것 같다고 생각할 수 있다
그런데 **Object**로 선언한 변수들은 오직 어떤 값이든 그 변수에 할당할 수 있게 해주지만
실제로 메서드가 존재하더라도 임의로 호출할 수 없다
```js
let notSure: any = 4;
notSure.ifItExists();
notSure.toFixed();

let prettySure: Object = 4;
prettySure.toFixed(); // Error
```

**any**타입은 타입의 일부만 알고 전체는 알지 못할 때 유용하다
여러 다른 타입이 섞인 배열을 다룰 수 있다
```js
let list: any[] = [1, true, 'apple'];
list[0] = 1;
```


## void

**void**는 어떤 타입도 존재할 수 없음을 나타내기 때문에 **any**의 반대 타입 같다
**void**는 보통 함수에서 반환 값이 없을 때 반환 타입을 표현하기 위해 쓰인다
```js
function warnUser(): void {
  console.log("Hola")
}
```
**void**를 타입 변수으로 선언하는 것은 유용하지 않다
왜냐하면 그 변수에는 **null**또는 **undefined**만 할당할 수 있기 때문이다
```js
let unusable: void = undefined;
unusable = null; 
```


## Null and Undefined

typescript는 **undefined**와 **null** 둘 다 각각 자신으 타입 이름으로 
**undefined**, **null**로 사용한다
```js
// 이 밖에 이 변수에 할당할 수 있는 값이 없다
let u: undefined = undefined;
let n: null = null;
```
기본적으로 **null**과 **undefined**는 다른 모든 타입의 하위 타입이다
이건 **null**과 **undefined**를 **number**와 같은 타입에 할당할 수 있다는 것을 의미한다

히지만 **--strictNullChecks**를 사용하면 **null**과 **undefined**는 
오직 **any**와 각자 자신들 타입에만 할당 가능하다(예외적으로 undefined는 void에 할당 가능
)
이건 많은 일반적인 에러를 방지하는데 도움을 준다
이경우 **string** 또는 **null** 또는 **undefined**를 허용하고 싶은 경우 
유니온 타입인 **string | null | undefined**를 사용할 수 있다


## Never

**never**타입은 절대 발생할 수 없는 타입을 나타낸다
예를 들어 **never**는 함수 표현식이나 화살표 함수 표현식에서 항상 오류를 발생시키거나
절대 반환하지 않는 반환 타입으로 쓰인다
변수 또한 타입 가드에 의해 아무 타입도 얻지 못한다면 **never**타입을 얻을 수 있다
**never**타입은 모든 타입에 할당 가능한 하위 타입이다
하지만 어떤 타입도 **never**타입에 할당할 수 있거나 하위 타입이 아니다(자신은 제외)
```js
function 
// never를 반환하는 함수는 함수의 마지막에 도달할 수 없다
function error(message: string): never {
  throw new Error(message);
}

// 반환 타입이 never로 추론된다
function fail() {
  return error("something failed")
}

// never를 반환하는 함수는 함수의 마지막에 도달할 수 없다
function infiniteLoop(): never {
  while (true) {

  }
}
```


## Object

**object**는 원시타입이 아닌 타입을 나타낸다
예를 들어 **number**, **string**, **boolean**, **bigint**, **symbol**, **null**, **undefined**가 아닌 나머지를 의미한다

```js
declare function create(o: object | null): void;

create({ prop: 0 });
create(null);

create(43); // Error
create('string'); // Error
```
- declare 키워드는 변수, 상수, 함수, 클래스가 어딘가에 이미 선언되어 있음을 알린다  
  즉, js 코드로를 컴파일되지 않고 typescript 컴파일러에게 타입 정보를 알리기만 한다


## Type assertions (타입 단언)
가끔 typescript보다 개발자가 값에 대해 더 잘 알고 있을 때가 있다
이런 경우는 어떤 언티티의 실제 타입이 현재 타입보다 더 구체적일 때 발생한다

타입 단언은 컴파일러에게 '날 믿어, 내가 뭘 하고 있는지 알아'라고 말해주는 방법이다
타입 단언은 다른 특별한 검사를 하거나 데이터를 재구성하지는 않는다
이느 런타입에 영향을 미치지 않으며 온전히 컴파일러만 이를 사용한다
타입스크립트는 개발자가 필요한 어떤 특정한 검사를 수행했다고 인지한다
```js
// angle-braket
let someValue: any = 'string';
let stringLength: number = (<string>someValue).length;
```
```js
// as 문법
let someValue: any = 'string';
let stringLength: number = (someValue as string).length;
```
**타입스크립트와 JSX를 함께 사용할 때는 as 스타일의 단언만 허용된다**