## Ⅱ. 자바스크립트 2강 (Javascript)   
## 1. 강의 자료
* 자료: https://www.notion.so/JS-22-6-8723b46e0cde4d90b020b689e5cb9f0a#6d71826efcd24cbfbecd00ea8092f8ee
* 영상: https://youtu.be/U34GhHn3oAs

<br>

### 6) 변수   
#### (3-1) String (문자열)
◆ 형태: __``` '문자열', "문자열", `문자열`, `문자열${변수명}`  ```__   

   * 탬플릿 리터럴(template literals): __``` ${} ```__   

__ex>__   
```
let name = 'hojun'

- 예전 방법
console.log('제 이름은 ' + name + '입니다.)

- 탬플릿 리터럴
console.log('제 이름은 ${name}입니다.)

- 결과
제 이름은 hojun입니다.
```
<br>

◆ 호출: __변수명, 변수명[index]__   

   * 호출은 할 수 있지만, 개별 값 변경 X   

__ex>__   
```
let name = 'hojun'
name[0]            // h
```
<br>

#### (3-2) 메소드   
* __str.length__  

__ex>__
```
let name = 'hojun'
name.length        // 5
```
<br>

* __str.slice( , )__  

__ex>__
```
let name = 'hojun'
name.slice(2,)        // 'jun'

'hello world'.slice(6, )  // 'world'
```
<br>

* __str.replace( , )__   

__ex>__

```
'hello world'.replace('hello, 'hi')  // 'hi world'
```

__ex>__: 정규 표현식 사용 가능   
```
'hello world hello'.replace('hello, 'hi')  // 'hi world hello'

- 정규 표현식
'hello world hello'.replace(/hello/g, 'hi')  // 'hi world hi'
```
<br>

* __str.repeat()__

   * 권장하는 방법 X, 알고리즘 문제 풀 때 사용   

__ex>__   
```
'0'.repeat(3)  //  '000'

'0'.repeat(3).split('')   //  (3) ['0', '0', '0']
```

<br>
<hr>

#### (4) Boolean (논리값), undefined, null   
__ex>__   
```
!![]   // true
!!{}   // true

!!''       // false
!!'hello'  // true, 문자가 하나라도 있으면 true

!!0    // false
!!10   // true
!!-10  // true

let x  // undefined, 값이 할당되지 X

let x = null  // 값이 없음을 명시
```

<br>
<hr>

#### (5-1) Array (배열): object   
* 형태   
```
['a', 'b', 'c']
[100, 200, 300]

[{'one':1, 'two':2}, {'one':10, 'two':20}]

// 3차원
let x = [[[1, 2], [10, 20], [100, 200]], [[3, 4], [30, 40], [300, 400]]]

```

__ex>__   
```
let x = ['a', 'b', 'c']
x[0]                     // 'a'

let x = [{'one':1, 'two':2}, {'one':10, 'two':20}]
x[0]                                                // {'one':1, 'two':2}
x[0]['one']                                         // 1

let x = [[[1, 2], [10, 20], [100, 200]], [[3, 4], [30, 40], [300, 400]]]
x[1][2][1]                                          // 400
```
<br>

#### (5-2) 메소드
* __변수명.length__  

__ex>__
```
let x = [10, 20, 30, 40]
x.length        // 4
```

<br>

* __변수명.forEach__   

__ex>__
```
let x = [10, 20, 30, 40]
x.forEach(x => console.log(x ** 2))   //  100  400  900  1600
```

<br>

* __map__: 어떤 데이터를 pick할 때 (데이터를 뽑아낼 때)   

__ex>__   
```
let x = [10, 20, 30, 40]
x.map(x => x+100)        // (4) [110, 120, 130, 140]
```

<br>

* __filer__: 어떤 값을 가져올 때   

__ex>__   
```
let x = [1, 2, 3, 4, 5, 6, 7]
x.filter(x => x > 4)        // (3) [5, 6, 7]
```

<br>

* __find__: 어떤 값을 찾을 때   

   * ID처럼 고유한 값을 찾을 때 사용   

__ex>__   
```
let x = [1, 2, 3, 4, 5, 6, 7]
x.filter(x => x > 4)        // 5
```

<br>

* __fill__: 어떤 값을 채울 때   

__ex>__   
```
Array(3)           // (3) [empty × 3],  빈 배열
Array(3).fill(0)   // (3) [0, 0, 0]

Array(3).fill(0).map((value, index) => value + index)     // (3) [0, 1, 2]
Array(3).fill(0).map((value, index) => value + index +1)  // (3) [1, 2, 3]
```

<br>
<hr>

#### (6-1) Object (객체)
* 형태: __```{ key : value }```__   

__ex>__   
```
{
    "지역이름": "전국",     // key : value(2개의 집합을 가리켜 객체 프로퍼티)
    "확진자수": 24889,
    "격리해제수": 23030,
    "사망자수": 438,
    "십만명당발생율": 48.0
}
```

<br>

* 새로운 문법: 변수명과 값을 key와 value로 쓰고 싶을 때

__ex>__   
```
let x=1, y=2, z=3
let object = {x, y, z}    // {x: 1, y: 2, z: 3}

```

<br>

* 호출 방법: __변수명, 변수명.지역이름, 변수명['지역 이름']__   

__ex>__   
```
let x=1, y=2, z=3
let object = {x, y, z}

object       // {x: 1, y: 2, z: 3}
object.x     // 1
object['x']  // 1
```

<br>

* 수정: value['hello'] = 'world', value['hello' = null   
   
* 삭제: dele value['hello'] 는 추천하지 않음
   * 메모리 상에 'world'가 남아 있음   
   
   * value['hello'] = null   

__ex>__: 수정   
```
let x=1, y=2, z=3
let object = {x, y, z}

object['hello'] = 'world'
object                   // {x: 1, y: 2, z: 3, hello: 'world'}
```

<br>

#### (6-2) Object 메소드   
* Object.keys(변수명)   

__ex>__   
```
Object.keys(object)  //  ['x', 'y', 'z', 'hello']
```

* Object.values(변수명)

__ex>__   
```
Object.values(object)  // [1, 2, 3, 'world']
```

* Object.entries(변수명)   

__ex>__   
```
Object.entries(object)

0: (2) ['x', 1]
1: (2) ['y', 2]
2: (2) ['z', 3]
3: (2) ['hello', 'world']
length: 4
```

<br>
<hr>

#### (7-1) Map
* 메소드:

   * set() : 데이터를 넣어줌   
   * get() : value를 가져오는 것
   * keys() : key값만 불러오기
   * values() : value값만 불러오기

```
let map = new Map()
map.set('one', 100)
map.set('two', 200)
map.set('three', 300)   // Map(4) {'one' => 100, 'two' => 200, 'three' => 300, 'four' => Array(2)}

map.get('one')   // 100

map.keys()       // MapIterator {'one', 'two', 'three', 'four'}

map.values()     // MapIterator {100, 200, 300, Array(2)}

map.entries()
//
0: {"one" => 100}
1: {"two" => 200}
2: {"three" => 300}
3: {"four" => Array(2)}
```

<br>

#### (7-2) object를 map 자료형으로 변환   
__ex>__   
```
let x=1, y=2, z=3
let object = {x, y, z}    // {x: 1, y: 2, z: 3}

let test = new Map(Object.entries(object))
test                      // Map(3) {'x' => 1, 'y' => 2, 'z' => 3}
```

<br>
<hr>

#### (8) Set (object)   
* 중복을 허용하지 X

* 메소드: ``` add, delete, has, size ```   

__ex>__   
```
let x = new Set('11111222223333')
set     // Set(3) {'1', '2', '3'}
```

__ex>__: ``` add, size ```   
```
x.add(4);    // Set(4) {'1', '2', '3', 4}
x.size       // 4
```

<br>
<hr>

### 7) 조건문   
* __``` if, else if, else ```__   
<br>

#### (1) 삼항 연산자   
* 기본 구성: (참 또는 거짓) ? 참일때 연산결과 : 거짓일때 연산결과   

__ex>__
```
let result = true ? 1 : 100;
result                       // 1

false ? console.log('one') : console.log('two');  // two
```

<br>

#### (2) switch문   
```
let day

switch (new Date().getDay()) {
  case 0:
    day = "일";
    break;
  case 1:
    day = "월";
    break;
  case 2:
    day = "화";
    break;
  case 3:
    day = "수";
    break;
  case 4:
    day = "목";
    break;
  case 5:
    day = "금";
    break;
  case 6:
    day = "토";
}

console.log(day)  // 일
```

<br>
<hr>

### 8) 반복문   
#### (1) for문   
```
for (let i = 0; i < 10; i++) {
    console.log(i)
}
```

<br>

#### (2) for of문   
__ex1>__   
```
let a = [10, 20, 30];   // let a = 'hello',  let a = '19821'도 가능

for (let i of a) {
    console.log(i);
}

// 출력
10
20
30
```

__ex2>__   
```
let sum = 0
let a = '19821'
for (let i of a) {
    sum += parseInt(i)  // 21
}
```

__ex3>__
```
let a = {'one':1, 'two':2};
for (let i in a) {
    console.log(i);        // one two, key값 출력
    console.log(a[i]);     // 1 2, value값 출력
}
```
<br>

#### (3-1) while문   
```
let x = 0;
while (x < 10) {
    console.log(x);  // 0부터 9까지 출력
    x++;
}
```

#### (3-2) 무한 반복
* ``` for (;;) {} ```   

* ``` while (true) {} ```   

<br>

#### (3-3) do-while문
* while문은 조건이 false면 실행되지 않지만, do-while문은 false라도 최소 1번은 실행된다

* 기본형: __```do { 반복할 것 } while (조건)```__   

__ex>__
```
let x = 10;
do {
    console.log(x);
    x++;
} while (x < 10)    // 10
```

<br>

#### (4) break / continue   
* ```break``` : 반복문이 만족했을 때, 반복문을 탈출   

* ```continue``` : 반복문이 만족했을 때, 다음 루프로 넘어감   

__ex>__   
```
for (let i = 0; i < 10; i++) {
    if (i == 5) continue;      // 1~4, 6~9 출력
    console.log(i);
}
```

<br>
<hr>

### 9) 함수
#### (1-1) 함수 표현식과 함수 선언식   
```
let 함수표현식 = function(){}   // 호이스팅 X
                               // 정확히는 호이스팅은 일어나지만, "일시적 사각지대(TDZ, Temporal Dead Zone)"에 빠져 error가 난다


function 함수선언식(){}        // 호이스팅 O, 함수 선언 되기 앞에도 출력하고자 하는 argument식을 넣을 수 있음
```

<br>

#### (1-2) parameter(파라미터), argument(인자)   
* 매개변수 (파라미터, parameter): x, y   
* 전달인자 (argument): 3, 5

__ex>__: 함수 선언식   
```
function add(x, y){  // parameter (파라미터)
    return x + y;
}

add(3, 5)            // argument (인자)
```

<br>

__ex>__: 함수 표현식   
```
add(3, 5)                   // argument (인자), 호이스팅 O

let add = function(x, y){   // parameter (파라미터)
    return x + y;
}

add(3, 5)                   // argument (인자)
```

<br>

__ex>__: 파라미터 디폴트값   
```
function add(a = 100, b = 200) {  // 디폴트 값
    console.log(a, b);
    return a + b;
}

add();                // add에 인자를 넣어주지 않으면, 300이 출력됨
add(10);              // 10만 넣어주면 210 출력
add(b=300)            // 500,  a에 입력
add(undefined, 300);  // 400

add(10, 20);  // 30 출력
```

<br>

#### (2-1) 콜백함수   
* 함수를 선언하고, 나중에 실행   

__ex>__   
```
function add(x, y) {   // add 함수
    return x + y;
}

function mul(x, y) {   // mul 함수
    return x * y;
}

function cal(a, b){
    return a(10, 10) + b(10, 10);
}

cal(add, mul);         // 함수를 변수처럼 사용
```

<br>

#### (2-2) 화살표 함수로 콜백함수 선언   
* 장점: argument에 들어갈 따로 함수 naming을 안해줘도 됨   
* 단점: 콜백지옥에 빠질 수 있음 → 들여쓰기 많아짐   

__ex>__
```
function cal(a, b){
    return a(10, 10) + b(10, 10);
}

cal((a, b) => a + b, (a, b) => a * b);  // cal함수 안의 argument 자리에 화살표 함수 넣어줌
```

<br>

#### (2-3) 화살표 함수
```
function A(x) {
    return x**2
}

// 함수표현식, 호이스팅 X
let A = x => { x**2 };
```

__ex>__
```
function f(a, b) {
    let z = 10
    let result = z + a + b
    return result
}

// 함수표현식, 호이스팅 X
let f = (a, b) => {         // 값이 여러개일 때, 파라미터에 ()를, 리턴값이 {}로 감싸줌
    let z = 10
    let result = z + a + b
    return result
};
```
