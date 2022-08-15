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

#### (6) Object (객체)
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
