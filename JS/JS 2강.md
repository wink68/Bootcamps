## Ⅱ. 자바스크립트 2강 (Javascript)   
## 1. 강의 자료
* 자료: https://www.notion.so/JS-22-6-8723b46e0cde4d90b020b689e5cb9f0a#6d71826efcd24cbfbecd00ea8092f8ee
* 영상: https://youtu.be/U34GhHn3oAs

<br>

### 6) 변수   
#### (1-4) String (문자열)
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
