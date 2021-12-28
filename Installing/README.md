## 타입스크립트 설치

#### 타입스크립트 패키지 설치
```js
npm install -g typescript
tsc --version
```

#### 타입스크립트 파일 만들기

hola.ts
```js
function hola(person: string) {
    return "Hola, " + person;
}

let user = "Hong";

document.body.textContent = hola(user);
```

#### 코드 컴파일하기

커맨드 라인에서 typescript 컴파일러를 실행시킨다
```js
tsc hola.ts
```
결과는 동일한 자바스크립트 코드를 포함하고 있는 hola.js파일이 된다


#### ts-node 설치
tsc는 타입스크립트 코드를 ES5 형식의 자바스크립트 코드로 변환만 할 뿐 실행하지는 않는다.
타입스크립트 코들를 ES5로 변환하고 실행까지 동시에 하려면 ts-node라는 프로그램을 설치해야 한다
```js
npm i -g ts-node
```

커맨드 라인에서 컴파일과 실행을 동시 진행할 수 있다
```js
ts-node hola.ts
```


## 타입스크립트 프로젝트 생성

타입스크립트 개발은 node.js 프로젝트를 만든 다음 개발 언어를 타입스크립트로 설정하는 방식으로 진행한다

```js
// package.json 생성
npm init
```
package.json은 node.js가 관리하는 패키지 관리 파일로서 프로젝트 정보와 관련 패키지가 기록된다

- 패키지 설치 명령 옵션

| npm i 옵션 | 의미              | 단축 명령 | 
| ---- | --------------------- | ------- | 
| --save | 프로젝트를 실행할 때 필요한 패키지로 설치한다. 패키지 정보가 package.json 파일의 'dependencies' 항목에 등록된다 | -S | 
| --save-dev | 프로젝트를 개발할 때만 필요한 패키지로 설치한다. 패키지 정보가 package.json 파일의 'devDependencies'항목에 등록된다 | -D | 

```js
npm i -D typescript ts-node
```

타입스크립트는 기본적으로 ESNext 자바스크립트 문법을 포함하고 있지만 자바스크립트와 완전히 다른 언어이다
자바스크립트 컴파일러는 **a => a + 1**과 같은 코드를 동작시킬 수 있지만
타입스크립트 컴파일러는 **(a: number): number => a + 1** 처럼 타입이 명시적으로 설정되어 있어야만 코드가 문법에 맞게 작성되었는지를 검증해 코드를 동작시킨다

이 때문에 자바스크립트로 개발된 라이브러리나 웹 브라우저나 node.js가 기본적으로제공하는 타입들의 존재도 알지 못한다
예를 들어 ramda 라이브러리는 @types/ramda, Promise 같은 타입을 사용하려면 @types/node라는 패키지를 설치해야 한다
```js
npm i -D @types/node
```

