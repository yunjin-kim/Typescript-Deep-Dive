# properties

## 읽기 전용 프로퍼티 (Readonly properties)

일부 프로퍼티들은 객체가 처음 생성될 때만 수정 가능해야 한다
프로퍼티 이름 앞에 **readonly**를 넣어서 이를 저장할 수 있다
```js
interfae Point {
  readonly x: number;
  readonly y: number;
}
```
객체 리터럴을 할당하여 **Point**를 생성한다
할당 후에는 **x**, **y**를 수정할 수 없다
```js
let p1: Point = { x: 10, y: 20 };
p1.x = 5; // Error
```

typescript에서는 모든 변경 메서드가 제거된 **Array<T>**와 동일한
**ReadonlyArray<T>** 타입을 제공한다
그래서 생성 후에 배열을 변경하지 않음을 보장할 수 있다
```js
let a: number[] = [1, 2, 3, 4];
let b: ReadonlyArray<number> = a;
ro[0] = 12; // Error
ro.push(1); // Error
```

#### **readonly** vs **const**

프로퍼티는 **readonly**를 사용하고 변수는**const**를 사용한다


## 초과 프로퍼티 검사 (Excess Property Checks)

// Todo