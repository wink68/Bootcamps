### 1. 동기 & 비동기 처리 개념
__문제 >__
* ```setTimeout```을 이용해서 비동기 처리 함수를 완성한다

   * `printWithDelay()`를 실행해서 3초 늦게 "async callback" 문장을 띄우는 코드를 작성

__index.js >__
```
// 2. 비동기 처리 Asynchronous callback
function printWithDelay(print, timeout) {
  setTimeout(print, timeout);
}
printWithDelay(() => {
    console.log("async callback")
    }, 3000);


//1. 동기처리 함수를 그대로 수행하는 `printImmediately()` 함수
function printImmediately(print) {
  print();
}

//동기처리
printImmediately(() => console.log("hello"));

module.exports = { printWithDelay };
```

<br>
<hr>

### 2. setTimeout 사용하는 함수 만들기
__문제 >__
* 함수명: ```countDownThree```

* 함수 실행 시, 3 -> 2-> 1-> “끝” 이 차례대로 출력

   * 3은 함수 실행 시 딜레이 없이 바로 출력되어야 한다

__countDownThree.js >__
```
function countDownThree () {
    console.log(3);                             // 바로 실행
    setTimeout(() => console.log(2), 1000);     // 1초 뒤 실행
    setTimeout(() => console.log(1), 2000);     // 2초 뒤 실행
    setTimeout(() => console.log("끝"), 3000);  // 3초 뒤 실행
}

module.exports = { inputs: [], func: countDownThree }
```

<br>
<hr>

### 3. setTimeout 사용하는 함수 만들기 2
__문제 >__
* 함수명: ```printAfterNSeconds```

* 함수 실행 n초 후에 “n초가 경과되었습니다.” 문구가 출력

   * 출력될 문구는 template literal(백틱)을 사용하여 만드시오

__printAfterNSeconds.js >__
```
function printAfterNSeconds(n) {
    setTimeout(() => {
        console.log(`${n}초가 경과되었습니다.`)
    }, 1000*n)
}

const inputA = 2

module.exports = { inputs: [inputA], func: printAfterNSeconds }
```

<br>
<hr>

### 4. setTimeout 사용하여 웹 구현하기
* 입력 칸에 이름을 입력한 후 버튼을 클릭하면, 입력된 이름이 담긴 “alert 창” 이 2초 후에 나타나도록 코드를 작성해 보세요
<br>

__index.js >__
```
function TwoSeconds (e) {
    e.preventDefault();

    const nameValue = Name.value;   // 입력된 이름 value 가져오기
    setTimeout(() => {
        alert(`입력된 이름: ${nameValue}`)
    }, 2000)
}

const Name = document.getElementById("inputName");

const button = document.getElementById("buttonSubmit");
button.addEventListener("click", TwoSeconds);
```
<br>

__HTML >__
```
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>2초 뒤에 alert</title>
  <link rel="stylesheet" href="index.css">
  <! --- 여기서 index.js를 가져옵니다. --->
  <script src="index.js" type="module" defer></script>
</head>
<body>
  <div class="container">
    <div class="item">
      <h3>2초 뒤에 alert</h3>
      <form>
        <label class="label" >이름
          <input type="text" id="inputName" placeholder="박태환" />
        </label>
        <br />
        <button id="buttonSubmit">클릭</button>
      </form>
    </div>
  </div>
</body>
</html>
```
