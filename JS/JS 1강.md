## Ⅰ. 자바스크립트 (Javascript)   
## 1. 강의 자료
https://www.notion.so/JS-22-6-8723b46e0cde4d90b020b689e5cb9f0a#6d71826efcd24cbfbecd00ea8092f8ee

<br>

### 0) 개발자 도구
* __ctrl + shit + i__   
<br>

### 1) 삽입 위치
* 기본 태그: __```<script> </script>```__   

* 보통 body의 맨 끝   

__ex>__
```
<body>
    <h1>hellow world</h1>
    <p id="one">hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    <p>hello world</p>
    
    <script> // body 맨 끝에 넣어줌
        document.getElementById('one').innerHTML =
        'hi world'
    </script>
</body>
```
<br>
<hr>

### 2)  JavaScript를 출력하는 4가지 방법
* ```ctrl+shift+i```를 누르고 Console에서 테스트 가능   
<br>

#### (1) 문서 내 요소를 선택하여 출력
* innerHTML   
```
document.getElementById('one').innerHTML =
        'hi world'            // 화면에 hi world 출력
```
<br>

#### (2) 문서 내 직접 출력
* write   
```
document.write('js hello!!')  // 화면에 js hello!! 출력
```
<br>

#### (3) 사용자 인터렉션 
* alert   
```
alert('hello')    // hello라는 알람창이 뜸
```

* confirm   
```
confirm('hello')  // 알람에서 확인 누르면 true, 취소 누르면 false 반환
```
<br>

#### (4) 콘솔에 찍는 방법
* 웹 화면이 아니라, 콘솔 화면에 출력   

* conole.log
```
console.log('hello')  // 콘솔에 hello 출력
```

<br>
<hr>

### 3) 코드 구조   
#### (1) ~문
* 문(statement)은 세미콜론으로 구분   

* 문 → 값, 연산자, 키워드, 명령어, 표현식 등
<br>

#### (2) 주석
```
//    1줄 주석
/**/  여러 줄 주석
```
<br>

#### (3) 엄격모드   
* 엄격모드를 실행한 곳에서만 최신 문법 사용 가능

   * 기본의 문법도 작동해야 하므로

* 코드 최상단에 사용
   * __```"use strict";```__   
<br>
<hr>

### 4) 변수
* 변수 선언: __```var```, ```let```, ```const```__   
   * 주로 __```const```__ 사용, 상수에 자주 사용      

* 숫자로 시작 X
* 띄어쓰기 X
* 예약어 사용 X
* 달러($)나 언더스코어(_) 제외한 특수문자 X
* 소문자로 시작
   * class는 대문자로 시작
<br>

#### (1) __```var```__: 함수 레벨 스코프, 사용 권장 X  
__ex>__   
* __★ 다른 언어에서는 재선언 X ★__   
* var을 사용할 땐 에러가 안 떠서 에러를 찾기 힘듦   

```
var x = 10;  // 변수 선언
var y = 20;

console.log(x + y)

var x = 10;  // 재선언
var y = 20;

console.log(x + y)
```
<br>

__ex>__   
* 중괄호 안에서 선언된 변수는 밖으로 꺼낼 수 없음 → is not defined   

```
if (true) {
   const testName = 'hojun'
   let testAge = 10
}
```
<br>

#### (2) __```let```__: 블록 레블 스코프   
* 값을 재선언할 때 사용   

__ex>__   
```
const xx = 100
xx = 100        // 에러 뜸

let yy = 100
yy = 10         // 10으로 바뀜
```

<br>
<hr>

### 5) 연산자   
#### (1) 논리 연산자   
* 참 (true) = 1 / 거짓 (false) = 0   

* 그리고(and) = && / 또는(or) = ||

* ! : 부정

__ex>__   
```
true && false  // false
```

__ex>__   
```
for (let x = 0; x < 100; x++ {
    if (x % 3 == 0 && x % 5 == 0) {
        console.log(x)
    }
}
```

__ex>__
```
!false     // true
!!false    // false
!!1        // true
!!'hello'  // true
```
<br>

#### (2) 비트 단위 연산자   
* ```&``` : and
* ```|``` : or

* 실무에서 보기 어렵다

__ex>__   
* 9 & 5
```
9 = 1 0 0 1   // 2진수
5 =   1 0 1
  = 0 0 0 1   // 1이 된다
```

__ex>__   
* 9 | 5
```
9 = 1 0 0 1
5 =   1 0 1
  = 1 1 0 1  // 13이 된다
```
<br>

◇ 참고 자료
: https://jam-ws.tistory.com/19

<br>

#### (3) 단락 회로 평가   
* 앞의 값이 null인지 확인하고 싶은 경우
```
result1 = 10 || 100;   // 앞에 값(10)이 있으므로, 뒤의 값을 볼 필요도 없이 항상 true
result2 = 0 && 100;    // 앞의 값이 0이므로, 뒤의 값을 볼 필요도 없이 항상 false


username = 'hojun';
result5 = username || '유저 이름이 없습니다';   // 변수에 값 hojun이 있으므로 true

username = undefined;
result5 = username || '유저 이름이 없습니다';   // 변수 값이 없어 false이므로 뒤의 값을 본다
                                               // result5  →  <유저 이름이 없습니다>라고 출력
```
<br>

#### (4) 비교 연산자   
* __```===```__: 타입까지 같다

* __```!==```__: 타입까지 다르다

__ex>__   
```
let x = 3
let y = '3'

console.log(x == y)   // true → ★ 다른 언어에선 false 출력 ★

console.log(x === y)  // false → 타입이 다르다
console.log(x !== y)  // true
```

<br>

#### (5) 단항 산술 연산자   
* ```++x, x++, --x, x--```   

   * ```x++```: 일단 x를 출력한 뒤에 플러스가 됨

__ex>__
```
let x = 3
++x             // 4

x++             // 4
console.log(x)  // 5
```
<br>

#### (6) nullish 병합 연산자   
* (3)번 단락 회로 평가처럼 앞에 값이 __null__ 이거나 __undefined__ 면 뒤의 값을 넣어줌   

__ex>__   
```
let result1;
let result2 = result1 ?? 100;   // result1은 undefinded,  100을 넣어줌

let result3 = 10;
let result4 = result3 ?? 100;   // 앞의 값 10 출력
```
<br>

#### (7) typeof 연산자   
* 타입을 알려줌   

__ex>__   
```
typeof 10    // 'number' 출력
typeof '10'  // 'string' 출력
```
<br>

#### (8) 프로퍼티 접근 연산자   
* 여러가지 값들에 접근할 때

① 마침표 프로퍼티 접근 연산자   
② 대괄호 프로퍼티 접근 연산자   

__ex>__
```
let x = {'one':1, 'two':2}
x.one                      // 1   마침표 프로퍼티 접근 연산자
x['one']                   // 1   대괄호 프로퍼티 접근 연산자
```
<br>

#### (9) 관계 연산자
* 키(key)만 가지고 판단, 값(value)은 보지 X   

__ex>__
```
10 in [10, 20, 30]   // false  /   10, 20, 30의 키(key)는 인덱스 0, 1, 2

1 in 'hello'         // error
'h' in 'hello'       // error

'name' in {'name' : 'hojun', 'age' : 10}   // true → 키(key)에 name이 있기에
```

__ex>__
```
'length' in [10, 20, 30];    // true

let x = [10, 20, 30]
console.dir(x)

// Array(3)
0: 10
1: 20
2: 30
length: 3  → 배열에 length도 포함
```

__ex>__
```
let x = {'one' : 1, 'two' : 2}
console.dir(x)

// object
one: 1
two: 2  → length가 없으므로 length in {'one' : 1, 'two' : 2}는 false   
```

<br>
<hr>

### 6) 변수   
#### (1-1) 원시타입 (primitve)
* 하나의 값만 가지고 있음
   * number, string, boolean, null(아무것도 없음), undefined(아무 값도 넣지 않았을 때), symbol
   
   * symbol (문서 내 변경 불가능한 유일한 값)
   
* 고유의 값 변경 불가

__ex>__
```
let x = 'hello'
x[0]   // h → 호출 가능

x[0] = 100
x            // hello → 값이 바뀌지 X
```
<br>

#### (1-2) 참조타입  (reference types)
* object (object, array, map, set), function

__ex>__: 전부 타입이 같음   
```
let x = [10, 20, 30]
typeof x              // 'object'

let x {'one' : 1, 'two' : 2}
typeof x              // 'object'
```
<br>

* 값 변경 가능

__ex>__
```
let x = [10, 20, 30]
x[1]                  // 20

x[1] = 100
x                     // [10, 100, 30]  →  값이 변함
```
<br>

#### (1-3) Number (숫자)   
* 호출: 변수명

* 메서드   
   * 10.toString은 안 됨 → 소수점이 있을 수 있기 때문에
   
   * (10).toString()는 가능
   
```
let x = 10
x.toString()   // 문자열 '10'
```
<br>

* __변수명.toFixed()__   
```
let x = 10.3
x.toFixed()    // '10'
```
<br>

* __Number()__ : 문자열을 숫자로 변경

   * 사용 권장하지 X
```
Number('10')    // 10
```
<br>

* __parseInt()__: <안전하게> 문자열을 숫자로 변경   
```
parseInt('10') + parseInt('10')   // 20
```
<br>

__ex>__
```
parseInt('10asdfsdfae')    // 10
Number('10asdfsdfae')      // NaN
```
<br>

* __NaN__   

   * Not a Number: 표현할 수 없는 값
   
* __Infinity, -Infinity__   

__ex>__   
```
typeof NaN       // 'number'
typeof Infinity  // 'number'
```

* __Math__   

   * Math.PI : 3.14...출력
   
   * Math.max() : 최댓값 출력
   
   * Math.min() : 최솟값 출력
   
__ex>__
```
Math.max(10, 20, 30)           // 최댓값, 30
Math.min(10, 20, 30, 1, 2, 3)  // 최솟값, 1
```
