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
