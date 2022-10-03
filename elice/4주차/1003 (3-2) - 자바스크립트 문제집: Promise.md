## 1. Promise 개념
### (1) Promise 생성 문법
```
var myPromise1 = new Promise(function(resolve, reject) {
    resolve(1);
});
```
### (2) Promise 이행(resolve)과 거부(reject)
```
myPromise1.then();  //이행
var myPromise2 = new Promise(function(resolve, reject) {
    reject(1);
});
myPromise2.then(); 
```
<br>

__promise.js >__
```
//1. new Promise() 메소드를 호출해서 Promise를 생성하세요.
new Promise(function(resolve, reject) {
    resolve();
});

//2. new Promise()를 호출할 때 콜백 함수의 인자를 resolve, reject로 선언하세요.
function getData() {
    return new Promise(function (resolve, reject) {

    // 3. resolve를 실행해서 아래 선언된 메시지(data)를 resolve 인자 값으로 넘기세요.
    var data = "javascript promise";
    resolve(data);
    });
}

// 4. then을 이용해서 resolve()의 결과 값 data를 resolvedData로 받습니다.
getData().then(function (resolvedData) {
    document.write(resolvedData);
});
```

<br>
<hr>

## 2. Promise로 타이틀 바꾸기

