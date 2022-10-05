## 1. 비동기2
### 1) async/await
* Promise를 활용한 비동기 코드를 __간결하게(직관적으로, synatic sugar) 작성하는 문법__  

* async/await 문법으로 비동기 코드를 __동기코드 처럼__ 간결하게 작성할 수 있다

   * async 함수와 await 키워드를 이용한다

   * await 키워드는 반드시 async 함수 안에서만 사용해야 한다

   * async로 선언된 함수는 반드시 __Promise를 리턴한다__   
<br>

### (1) async 함수
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
