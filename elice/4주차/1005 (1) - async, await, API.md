## 1. 비동기2
### 1) async/await
* Promise를 활용한 비동기 코드를 __간결하게(직관적으로, synatic sugar) 작성하는 문법__  

* async/await 문법으로 비동기 코드를 __동기코드 처럼__ 간결하게 작성할 수 있다

   * async 함수와 await 키워드를 이용한다

   * async로 선언된 함수는 반드시 __Promise를 리턴한다__   

* 단, __async 함수 내부의 코드는 비동기적으로 실행된다__

<br>

### (1-1) async 함수
* function 키워드 앞에 async를 붙인다

   * async 함수 내부에서 await 키워드를 사용한다

   * fetchData, fetchUser는 Promise를 리턴하는 함수이다

__Ex >__
```
async function asyncFunc() {
    let data = await fetchData()
    let user = await
fetchUser(data)
    return user
}
```

<br>

### (1-2) await 키워드 실행 순서
* await 키워드는 then 메서드 체인을 연결한 것처럼 순서대로 동작한다

* (Promise then체인을 넣은 것처럼) 비동기 코드에 순서를 부여할 수 있다

   * fetchData2가 promise를 리턴한다면, 성공/실패 여부가 결정될 때까지 다음 then체인이 멈춘다

   * 이것처럼 await도 fetchData2가 리턴한 promise가 resolve될 때까지 다음 then체인을 멈춘다

```
async function asyncFunc() {
    let data1 = await fetchData1()
    let data2 = await fetchData2(data1)
    let data3 = await fetchData3(data2)
    return data3
}
function promiseFunc() {
    return fetchData1()
        .then(fetchData2)
        .then(fetchData3)
}
```

<br>

### (1-3) 에러 처리
* Promise를 리턴하는 함수의 경우, 에러가 발생하면 catch 메서드를 이용하여 에러를 처리한다
   
__Ex >__
```
function fetchData1() {
    return request()
        .then((response) => response.requestData)
        .catch(error => {
           // 에러 발생
        })
}
```

<br>

* catch 메서드를 사용하지 않는다면, async 함수에서 try-catch 구문을 이용하여 에러를 처리한다

   * __catch절의 ```e```__ 는 Promise의 catch 메서드가 받는 반환값과 동일하다

__Ex >__
```
async function asyncFunc() {
    try {                               // 여기서는 fetchData1()과 fetchData2()에 대한 에러 처리가 catch에 묶여 있지만
        let data1 = await fetchData1()  // try-catch 구문을 나눠서 다분화할 수 있다
        return fetchData2(data1)
    } catch (e) {
        console.log("실패: ", e)
    }
}
```

<br>
<hr>

### 2) 실습: wait 함수 구현하기
__문제 >__
* wait 함수는 ms 단위로 기다리는 시간을 입력받습니다.

   * ex) ```wait(500)``` - 500ms를 기다립니다.

* wait 함수는 내부에 ```setTimeout```을 사용합니다.

* ```setTimeout``` 이후 wait 함수가 리턴하는 Promise는 resolve 됩니다.

<br>

__Wait.js >__
```
const wait = (ms) => {
    return new Promise((resolve, reject) => {

        setTimeout(() => {
            resolve()       // callback
        }, ms)
    });
};


/* 축약 가능
   const wait = ms => new Promise(resolve => setTimeout(resolve, ms))
*/

export default wait
```

<br>
<hr>

### 3) HTTP, REST API
### (1) HTTP (Hypertext Transfer Protocol)
* Web에서 서버와 클라이언트 간의 통신하는 방법을 정한 규칙

   * __클라이언트__ 는 웹 브라우저, 모바일 app 등 서버로 요청을 보내는 대상

   * __서버__ 는 클라이언트가 요청을 보내기 전까지 대응하지 않음

* 서버와 클라이언트 사이에는 무수히 많은 요소가 존재

   * DNS, Proxy, Tunnel Core Network

   * HTTP는 이런 존재들 사이의 통신 방법을 규정

<img src="https://user-images.githubusercontent.com/108077414/193994310-0dbd840a-98fa-4847-80fd-224f45c947f2.png" alt="HTTP" width="600px" />

<br>

### (2) HTTP Message
* 서버 주소(Host), 요청 메서드(POST), 상태 코드(403, 404), target path(슬래쉬, /), 헤더 정보, 바디 정보 등이 포함

* 요청 메시지, 응답 메시지의 모양이 다름

* HTTP/1.1 메시지는 사람이 읽을 수 있음

   * 통신 상태를 보고 어떤게 문제가 있는지 파악 가능

<img src="https://user-images.githubusercontent.com/108077414/193994850-ed8026e8-ce51-4da6-b20b-f9bbb2407a16.png" alt="HTTP Message" width="800px" />

<br>

### (2-1) HTTP Header
* 헤더에는 콘텐츠 관련 정보, 인증 관련 정보, 쿠키 정보(사용자 검색, 창을 열고 닫기), 캐시 관련 정보 등 서버와 클라이언트 간 통신 시 필요한 정보를 담고 있다

* 클라이언트 요청 시, 서버 응답 시 모두 헤더에 정보를 담을 수 있다

<br>

### (2-2) HTTP Status
* HTTP 요청 시, 클라이언트는 요청의 결과에 대한 상태 정보를 얻는다

   * 200, 400, 500 등 숫자 코드와, OK, NOT FOUND 등의 텍스트로 이루어짐

   * 코드를 이용해 각 결과에 해당하는 행위를 할 수 있음

<br>

### (2-3) 요청 메서드
* 특정 요청에 대해 의미를 부여하는 메서드

   * GET, POST, PUT PATCH, DELETE - 직접 커스텀에서 사용하는 부분

      * GET : 정보를 가져오겠다는 요청

      * POST : 서버에 어떤 내용을 붙인다 (생성)

      * PUT, PATCH : 기존의 정보를 업데이트 한다

      * DELETE : 정보를 삭제한다

   * OPTIONS, CONNECT, TRACE - 브라우저에서 자동으로 처리를 해주는 부분

<br>
<hr>

### (3) REST API (Reperesentational State Transfer API)
* __API__

   * 사용자가 특정 기능을 사용할 수 있도록 제공하는 함수

   * Application Programming Interface
<br>

* __REST API__

   * HTTP의 요청 메서드에 응하는 서버 API와 클라이언트 간 통신의 구조가 지켜야 할 좋은 방법에 대한 내용

      * HTTP는 단순히 통신 규약

      * REST API는 그 통신 규약을 어떻게 하면 잘 사용해서 서버와 클라이언트 간의 통신을 잘 할 수 있는가에 대한 내용

   * 요청 메서드의 의미, URI 설계, 클라이언트의 상태에 대한 동작 등을 정의한다

<br>

### (3-1) REST API 요청 메서드
* GET - 리소스 정보를 얻음

* POST - 리소스를 생성

* PUT - 리소스를 생성하거나 업데이트

* DELETE - 리소스를 제거

<br>
<hr>

### 4) Fetch API
* 기존 XMLHTTPRequest를 대체하는 HTTP 요청 API

   * 차이점: Fetch가 Promise를 리턴할 수 있음

* 네트워크 요청 성공시, Promise는 Response 객체를 resolve한다

* 네트워크 요청 실패시, Promise는 에러를 reject한다

```
let result = fetch(serverURL)

result
    .then(response => {
        if (response.ok) {
            // 요청 성송
        }
    })
    .catch(error => {
        // 요청 실패
    })
```

<br>

### (1) Response
* Response 객체는 결과에 대한 다양한 정보를 담는다

   * response.ok는 HTTP Status code가 200-299 사이면 true, 그 외 false이다

   * response.status는 HTTP status code를 담는다

   * response.statusText는 OK나 NOT FOUND같은 텍스트를 담는다

   * response.url은 요청한 URL 정보를 담는다

```
fetch(serverURL)
    .then(response => {
        response.ok
        response.status
        response.statusText
        response.url
        response.bodyUsed
    })
```

<br>

### (2) Header
* response.headers로 Response 객체의 헤더 정보를 얻을 수 있다

```
fetch(serverURL)
    .then(resp => {
        for (let [k, v] of resp.headers) {
            console.log(k, v)
        }
    })
```

<br>

### (3) Body 메서드
* response.json() 메서드는 얻어온 body 정보를 json으로 만드는 Promise를 반환한다

   * Promise가 resolve되면 얻어온 body 정보를 읽는다

* response.text(), response.blob(), response.formData() 등의 메서드로 다른 형태의 바디를 읽을 수 있다

```
fetch(serverURL)
    .then(response => {
        return response.json()
    })
    .then(json => {
        console.log('body: ', json)
    })
```

<br>

### (4) POST 요청
* fetch(url, options)로 fetch 메서드 옵션을 넣을 수 있다

* method 필드로 여러 요청 메서드를 활용할 수 있다

* headers, body 필드를 활용해 서버에 추가 정보를 보낸다

```
fetch(serverURL, {
    method: 'post',                 // 여러 요청 메서드 활용 가능
    headers: {                      // 헤더 정보
        'Content-Type':'application/json;charset=utf-8',
        Authentication:'mysecret'
    },
    body: JSON.stringify(formData)  // 바디 정보
})
    .then(response => {
        return response.json()
    })
    .then(json => {
        console.log('POST 요청 결과: ', json)
    })
```

<br>
<hr>

### (5) 실습: 유저 정보 요청하여 변환하기
__문제 >__
* 서버에서 데이터를 요청했을 때, 그 데이터를 가공해서 원하는 형식으로 사용할 수 있도록 함

* ```https://randomuser.me``` API를 이용해, 여러 유저의 정보를 받아와 가공하는 함수를 만는다

   * age 가 40세 이상인 유저만을 필터링합니다.

   * 필터링 된 유저 목록을 리턴합니다.

* 유저 정보 변환
```
- user.email -> email
- user.name.first, user.name.last -> name - `${user.name.first} ${user.name.last}`
- user.picture.large -> pictureUrl
- user.login.username -> username
- user.location.country, user.location.state, user.location.city -> location - `${user.location.country}, ${user.location.state}, ${user.location.city}`
- user.dob.age -> age
```

* 변환 결과
```
{
  email: 'sara.petersen@example.com',
  name: 'Sara Petersen',
  pictureUrl: 'https://randomuser.me/api/portraits/women/63.jpg',
  username: 'happybear329',
  location: 'Denmark, Nordjylland, Sommersted',
  age: 27
}
```

<br>

__User.js >__
```

```

<br>
<hr>

### (6) 실습: Posts 정보 조합하기
