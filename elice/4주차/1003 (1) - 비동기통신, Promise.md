## 1. 비동기1
### 1) 자바스크립트 제어 흐름
### (1) 자바스크립트 비동기
* 코드의 진행 흐름

   * 다른 멀티스레드 프로그래밍 언어(JAVA, C++)와 다른 방식으로 비동기 동작을 처리한다

* 자바스크립트 내부의 비동기 동작을 이해하기 위해서는 __이벤트 루프 등의 개념__ 을 알아야만 한다

<br>

### (2) 자바스크립트 엔진
* __스레드__

   * 프로그램에서 순차적인 처리 흐름을 나타내는 것

   * 자바스크립트는 __싱글 스레드 프로그래밍 언어__ => 한 번에 하나의 일만 처리할 수 있다는 뜻

<br>

* __하나의 메인 스레드__ 로 JS가 돌아간다

   * 메인 스레드는 코드를 읽어 한 줄씩 실행한다

   * 브라우저 환경에서는 유저 이벤트를 처리하고 화면을 그린다

<br>

### (2-1) 자바스크립트 vs 멀티 스레드 언어
#### (1) 자바스크립트
* 함수 setTimeout의 API, 즉 비동기 API가 작동해서 이 함수를 어떤 큐(queue)에 저장한다

   * 이 큐(queue)는 자바스크립트의 엔진이 아닌, 별도의 환경에서 동작한다

   * 10초 뒤에 함수가 종료하고, 이 함수의 callback을 Task Queue에 넣고 실행해야 한다고 알린다

   * 그러면 자바스크립트 메인 스레드는 (하는 일이 아무것도 없을 때) Task Queue의 코드를 가져와서 실행한다

* 이처럼 자바스크립트는 __하나의 메인 스레드로 비동기 처리를 할 수 있다__

```
setTimeout((c) => {
    console.log('Hi')
}, 10000)
```

<br>

#### (2) 멀티 스레드 언어 (JAVA)
* setTimeout이라는 새로운 함수를 만나면, 새로운 다른 스레드(멀티 스레드)를 만들고, 10초가 지날 때까지 그 스레드는 아무 동작도 하지 않고 기다린다

   * __비동기 처리를 약간 동기적으로 처리한다__ = 실행 중인 코드가 종료될 때까지 다음 코드를 실행하지 않는다

```
setTimeout((c) => { ... }, 10000)
```

<br>
<hr>

### (3-1) 동기적 제어 흐름
* __현재 실행 중인 코드가 종료되기 전까지 다음 줄의 코드를 실행하지 않는 것__

   * 분기문, 반복문, 함수 호출 등이 동기적으로 실행된다

   * __코드의 흐름과 실제 제어 흐름이 동일__

   * 싱글 스레드 환경(JS)에서 메인 스레드를 긴 시간 점유하면, 프로그램을 멈추게 한다

      * Ex> for 무한루프 → 자바스크립트 프로그램을 멈추게 한다

      * 자바스크립트 엔진이 작동할 수 없기에, 시간이 오래 걸리는 일은 비동기적으로 처리하도록 코드를 짜야 한다

* 단점

   * 한 사용자가 요청한 것이 처리될 때까지 기다려야 한다 = 사용자의 요청을 실시간으로 처리할 수 없다

* 장점

   * 코드를 읽을 때는 수월할 수 있다

__Ex>__
```
let a = 10                        // 선언문
console.log("a : ", a)            // console.log 같은 동기적 실행

function foo(num) {
    for (let i=0; i < 10; ++i) {  // 반복문
        console.log(num)
    }
}

foo(num)         // 함수 호출
```

<img src="https://user-images.githubusercontent.com/108077414/193472458-f452e867-c3ce-4236-8c29-001a0d499df3.png" alt="동기적 제어 흐름" width="800px" />

<br>
<hr>

### (3-2) 비동기적 제어 흐름
* __현재 실행 중인 코드가 종료되기 전에 다음 라인의 코드를 실행하는 것__

   * 코드 흐름과 실제 제어 흐름은 다르다

   * 비동기 작업을 기다리는 동안 메인 스레드는 다른 작업을 처리할 수 있다

   * Ex> 프로미스(Promise), 콜백 함수를 호출 하는 함수

__Ex>__
```
let a = 10                          // 1. 변수 선언

setTimeout(function callback() {
    console.log('a : ', a)          // 3. 3초 뒤에 a의 값을 출력
}, 3000)

console.log('Finished')             // 2. Finished 출력
```

<img src="https://user-images.githubusercontent.com/108077414/193473329-20e66afc-d010-40eb-aca2-f46007d19d45.png" alt="비동기적 제어 흐름" width="800px" />


<br>
<hr>

### (4) 퀴즈
<img src="" alt="비동기통신 퀴즈" />

### 2) 이벤트 루프
### (1-1) 자바스크립트의 비동기
* 자바스크립트 엔진

   * 비동기 처리를 제공하지 않는다

   * 대신, 비동기 코드는 정해진 함수를 제공하여 활용할 수 있다 → __이 함수들을 API라 한다__   

* 비동기 API의 예시

   * ```setTimeout```, ```XMLHttpRequest```, ```fetch``` 등의 Web API가 있다

* Node.js의 경우 파일처리 API, 암호화 API 등을 제공한다

<br>

### (1-2) 비동기 코드 예시
* 타이머 비동기 처리
```
setTimeout(() => console.log('타이머 끝'), 1000)       // 특정 시간이 되었을 때 1번 실행
setInterval(() => console.log('인터벌 타이머'), 1000)  // 특정 시간마다 실행
```

* 네트워크 처리
```
fetch('https://google.com')                            // 구글로 요청을 보내서 응답을 받을 수 있음
    .then(() => console.log('네트워크 요청 성공.'))
    .catch(() => console.log('네트워크 요청 실패.'))
```

<br>
<hr>

### (2) 비동기 처리 모델
* __자바스크립트 엔진__

   * 메인 스레드로 구성되어 있다

   * 메인 스레드는 __Call stack__ 를 이용해 코드를 읽고 실행함

      * 함수 안에 함수가 있는 경우, 실행 컨텍스트에 func1(), func2()가 쌓이게 됨 (execution context stack)
<br>

* __비동기 환경__

   * API 모듈은 비동기 요청을 처리한 후, __Taskque__ 에 callback 함수를 넣는다

      * setTimeout()의 경우, Web API 모듈에 등록되었을 때, 특정 시간 후 Task queue에 들어간다

   * __Job queue__ 는 Promise API나 animation frame에서 사용된다
<br>

* __이벤트 루프(Event Loop)__

   * 자바스크립트 엔진 외부에 존재한다

      * node.js 환경의 경우, libuv라는 모듈에서 비동기 처리를 담당한다

   * 비동기 코드가 끝나고 call stack이 다 비워졌을 때, Task queue의 첫번째 callback 함수를 Call stack에 집어넣고 코드를 실행한다

      * Task queue에 callback 함수가 들어온 순서대로 함수를 Call stack으로 내보낸다

      * 단, queue는 여러 개가 존재하며, 그 중 우선순위가 높은 큐(잡 큐 등)에서 나중에 들어온 콜백 함수가 실행될 수 있다

<br>

<img src="https://user-images.githubusercontent.com/108077414/193474517-97bf6001-bfd4-445d-8261-28c4b800036a.png" alt="비동기 처리 모델" width="800px" />

<br>

### (2-1) 비동기 처리 예시
* console.log를 만난다

* request 함수는 userData에 콜백 함수를 받는다

   * request 함수는 비동기 처리를 끝냈을 때, 콜백 함수를 Task queue에 넣어준다

   * Task queue에서 request가 끝나면 Call stack에 request callback 함수를 넣어주고, console.log가 찍히고 끝난다

__Ex>__
```
request("user-data", (userData) => {
    console.log("userData 로드")
    saveUsers(userData)
});

console.log("DOM 변경")
console.log("유저 입력")
```

<br>
<hr>

### 3) Promise
### (1-1) Promise API
* 비동기 API 주 하나

* 테스크 큐(Task queue)가 아닌 잡큐(Job queue, 혹은 microtask queue)를 사용한다

   * 잡큐는 테스크 큐보다 우선순위가 높다

__Ex >__
```
③ 3번째 실행
setTimeout(() => {
    console.log("타임아웃 1");
}, 0);

① 1번째 실행
Promise.resolve().then(() => console.log("프로미스 1"));

④ 4번째 실행
setTimeout(() => {
    console.log("타임아웃 2");
}, 0);

② 2번째 실행
Promise.resolve().then(() => console.log("프로미스 2"));
```
<br>

### (1-2) Promise
* 비동기 작업을 표현하는 자바스크립트 객체   

   * 비동기 작업의 진행, 성공, 실패 상태를 표현한다   

      * ```new Promise()```나 ```fetch()``` 비동기 API를 통해 ```Pending(진행)``` 상태에 접어들게 되고, 성공/실패 상태(```settled```)를 알 수 있다

         * 비동기 처리 중에 pending 상태를 표현할 수 있다

      * 성공은 ```fullfilled```나 ```resolved```, 실패는 ```rejected```로 표현된다

         * 성공의 경우에는 ```.then()``` 메소드가 실행되고, 실패의 경우에는 ```.catch()``` 메소드가 실행된다

         * ```.then(성공시)``` + ```.catch()``` / ```.then(성공시, 실패시)```   

   * 비동기 처리의 순서를 표현할 수 있다   
<br>
<hr>

### (2) Promise 생성자
* 기본형: __```new Promise(콜백 함수)```__

   * callback 함수는 executor 함수라고 하며, ```(resolve, reject)``` 두 인자를 받는다

__Ex >__
```
let promise = new Promise((resolve, reject) => {
    if (Math.random() < 0.5) {
        return reject("실패");
    }
    resolve(10);
});
```
<br>

### (3-1) Promise 메서드
* __```.then()```__ 메서드

   * 성공했을 때 실행할 콜백 함수를 인자로 넘긴다

   * ```.then(성공 콜백1, 실패 콜백2)```로 성공/실패 콜백 함수를 함께 인자로 넘길 수 있다

* __```.catch()```__ 메서드

   * 실패했을 때 실행할 콜백 함수를 인자로 넘긴다

* __```.finally```__ 메서드

   * 성공/실패 여부와 상관없이 모두 실행할 콜백 함수를 인자로 넘긴다

__Ex >__
```
promise
    .then(data => {
        console.log("성공: ", data)
    })
    .catch(e => {
        console.log("실패: ", e)
    })
    .finally(() => {
        console.log("promise 종료")
    })
```
<br>

### (3-2) Promise 메서드 체인
* ```then/catch``` 메서드가 또 다른 promise를 리턴하여, 비동기 코드에 순서를 부여한다

* 동일한 객체에 메서드를 연결할 수 있는 것을 __체이닝(chaining)__ 이라 한다

* 함수를 호출한 주체가 함수를 끝낸 뒤 자기자신을 리턴하도록 하여 구현한다

__Ex >__
```
promise
    .then(data => {
        return fetchUser(data)        // fetchUser() 함수가 promise를 리턴하는 함수라면, 이게 끝나야 다음 then이 실행된다
    })                                   → 비동기 코드의 순서를 부여할 수 있다
    .then(user => {
        console.log('User : ', user)
    })
    .catch(e => {
        console.log("실패: ", e)
    })
```
<br>
<hr>

### (4) Promise 정적 함수
* __```Promise.resolve```__

   * 성공한 Promise 객체를 바로 반환한다

* __```Promise.reject```__

   * 실패한 Promise 객체를 바로 반환한다

* 인위적으로 Primise 메서드 체인을 만들 수 있다

   * Promise를 리턴하는 함수를 만들어 호출할 필요가 없다

   * 비동기 코드로 진행해야 하는 상황 등에서 유용하게 사용할 수 있다

__Ex >__
```
Promise
    .resolve(10)
    .then(console.log)
    
Promise
    .reject("Error")
    .catch(console.log)
```
<br>

### (5) Promise.all 메서드
* 정적인 메서드

* Promise 배열을 받아 모두 성공시 각 Promise의 resolved값을 배열로 반환한다

   * 다 성공할 때까지 or 하나라도 실패할 때까지 기다린다

   * 하나의 Promise라도 실패시, 가장 먼저 실패한 Promise의 실패 이유를 반환한다

__Ex >__
```
Promise.all([
    promise1,
    promise2,
    promise3
])
    .then(values => {
        console.log("모두성공: ", values)
    })
    .catch(e =>
        console.log("하나라도 실패: ", e)
    })
```
