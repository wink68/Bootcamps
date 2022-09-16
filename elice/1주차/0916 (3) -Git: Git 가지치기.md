## 3. Git 가지 치기
## 1) Git Branch
* 독립적으로 어떤 작업을 진행하기 위한 개념

* 각각의 Branch는 다른 Branch의 영향을 받지 X

<br>

### (1) Git Branch 종류
* __메인 branch__: 배포할 수 있는 수준의 안정적인 branch

* __토픽 branch__: 기능 추가나 버그 수정과 같은 단위 작업을 위한 branch

<br>

### (2) Git Branch 생성
* 명령어 __```git branch 이름```__

   * HEAD → master: master 브랜치는 첫 git 저장소를 만들 때 자동으로 생성되는 branch

   * HEAD는 현재 가리키고 있는 branch를 의미

<br>

### (3) Git Branch 확인
* 명령어 __```git branch```__

```
  $ git branch
    like_feature
  * master
```

<br>

### (4) Git Branch 이름 변경
* 명령어 __```git chekckout 변경할 이름```__

```
  $ git checkout like_feature
  Switched to branch 'like_feature'
```

* ```checkout```은 branch를 전환하는데 사용 가능

   * ```git log```로 확인한 __snapshot__ 을 넘나들 때도 사용 가능

   * snapshot의 hash값을 이용하여 __과거의 파일 내용__  을 확인할 수 있음

```
   git checkout <snapshot hash>  // 16진수로 이루어진 hash
```

__ex>__
```
  $ git log --pretty=oneline
  e4abb6f... (HEAD -> master) this is master
  d97d387... another snapshot
  
  $ git checkout d97d38
  ...
  HEAD is now at d97d38 another snapshot
  
  $ git log --pretty=oneline
  e4abb6f... (master) this is master
  d97d387... (HEAD) another snapshot     // HEAD가 바뀜
```

<br>
<hr>

## 2) fast forward

<br>
<hr>

## 3) Merge

<br>
<hr>

## 4) conflict 해결
