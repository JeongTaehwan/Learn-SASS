## Sass 컴파일방법
```
npm init -y //package.json 생성
npm i -D parcel-bundler // parcel-bundler 설치
npx parcel "실행할 파일" // 실행
```

## Sass의 데이터 종류

Number: 숫자
Strings: 문자
Colors: 색상 표현
Booleans: 논리
Nulls: 아무것도 없음
Lists: 공백이나 , 로 구분된 값의 목록 | ex) (apple, orange, banana)
Maps: Lists와 유사하나 값이 Key: Value 형태 | ex) (apple: a, orange: o, banana: b)

## 데이터 종류의 특이사항
Number: 숫자에 단위가 있거나 없습니다.
Strings: 문자에 따옴표가 있거나 없습니다.
Nulls: 속성값으로 null이 사용되면 컴파일하지 않습니다.
Lists: ()를 붙이거나 붙이지 않습니다.
Map: ()를 꼭 붙여야 합니다.

## 상위 선택자 참조 (Ampersand)

&를 사용함
&는 바로 윗단계의 선택자를 참조함

## @at-root (중첩 벗어나기)

@at-root를 사용
ex) 변수를 선언하고 중괄호 밖에선 사용을 못하니 안쪽에서 사용을 해야하는데 중첩은 되면 안될때

## 중첩된 속성
ex) css에선 margin-... 등으로 사용헀다면 Scss에선  margin 안에 top, bottom 등등을 사용할 수 있음

## 변수

$로 시작함
$변수이름: 속성값; <- 이런식으로 작성함

## 변수 - 2
### 변수의 유효범위는 선언된 블록 {} 안에서만 사용 가능하다
### 변수 재 할당

변수를 선언하고 또 다른 변수에 변수를 넣을 수 있다.
