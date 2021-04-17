## Scss 컴파일방법

```
npm init -y //package.json 생성
npm i -D parcel-bundler // parcel-bundler 설치
npx parcel "실행할 파일" // 실행
```

## Scss의 데이터 종류

- `Number`: 숫자
- `Strings`: 문자
- `Colors`: 색상 표현
- `Booleans`: 논리
- `Nulls`: 아무것도 없음
- `Lists`: 공백이나 , 로 구분된 값의 목록 | ex) `(apple, orange, banana)`
- `Maps`: `Lists`와 유사하나 값이 `Key: Value` 형태 | `ex) (apple: a, orange: o, banana: b)`

## 데이터 종류의 특이사항

- `Number`: 숫자에 단위가 있거나 없습니다.
- `Strings`: 문자에 따옴표가 있거나 없습니다.
- `Nulls`: 속성값으로 `null`이 사용되면 컴파일하지 않습니다.
- `Lists`: `()`를 붙이거나 붙이지 않습니다.
- `Map`: `()`를 꼭 붙여야 합니다.

## 상위 선택자 참조 (Ampersand)

- `&`를 사용함
- `&`는 바로 윗단계의 선택자를 참조함

## @at-root (중첩 벗어나기)

- `@at-root`를 사용
- ex) 변수를 선언하고 중괄호 밖에선 사용을 못하니 안쪽에서 사용을 해야하는데 중첩은 되면 안될때

## 중첩된 속성

- ex) `css`에선 `margin-...` 등으로 사용헀다면 `Scss`에선 `margin` 안에 `top, bottom` 등등을 사용할 수 있음

## 변수

- `$`로 시작함
- `$변수이름: 속성값;` <- 이런식으로 작성함

## 변수 - 2

- 변수의 유효범위는 선언된 블록 `{}` 안에서만 사용 가능하다
- 변수의 유효범위는 선언된 블록 `{}` 안에서만 사용 가능하다

## 변수 재 할당

- 변수를 선언하고 또 다른 변수에 변수를 넣을 수 있다.

## 전역설정 (!global)

- `!global` 키워드를 사용함
- 박스 안에서 선언한 변수를 바깥에서도 사용할 수 있음

## 기본값 설정

- `!default` 키워드를 사용함
- 변수와 값을 선언하되 기본 변수값이 있으면 현재 설정한 값은 사용하지 않음

## 문자보간

- `#{}`를 사용함
- `#{}`를 이용하여 코드 어디서든 변수 값을 넣을 수 있음

## 가져오기

- `@import` 키워드를 사용함
- 외부에서 가져온 Sass파일들은 모두 CSS 출력 파일로 병합됨
- `@import "경로";`로 사용함
- Sass `@import`는 기본적으로 Sass 파일을 가져오는데, CSS `@import`규칙으로 컴파일되는 몇 가지 상황이 있음.

```
1. 파일 확장자가 .css일때
2. 파일 이름이 http://로 시작하는 경우
3. url()이 붙었을 경우
4. 미디어쿼리가 있는 경우
```

## 연산

- 산술 연산자
  - `+` 더하기
  - `-` 빼기
  - `*` 곱하기 (하나 이상의 값이 반드시 숫자(Number))
  - `/` 나누기 (오른쪽의 값이 반드시 숫자(Number))
  - `&` 나머지
- 비교 연산자
  - `==` 동등
  - `!=` 부등
  - `<` 대소 / 보다 작은
  - `>` 대소 / 보다 큰
  - `<=` 대소 및 동등 / 보다 작거나 같은
  - `>=` 대소 및 동등 / 보다 크거나 같은
- 논리(불린, Boolean) 연산자
  - `and` 그리고
  ```scss
  $width: 90px;
  div {
    @if ($width < 100px and $width = 90px) {
      height: 300px;
    }
  }
  ```
  - `or` 또는
  ```scss
  $width: 90px;
  div {
    @if ($width > 100px or $width > 30px) {
      height: 300px;
    }
  }
  ```
  - `not` 부정
  ```scss
  $width: 90px;
  div {
    @if not($width > 100px) {
      height: 300px;
    }
  }
  ```
- 문자 연산
  - 기본적으로 `+`를 사용함
  - 첫번째 피연산자에 따옴표가 붙어있으면 연산결과도 따옴표가 붙어있고, 그렇지 않으면 그대로 나옴
- 색상 연산
  - 색상 또한 연산할 수 있음
  - 그러나 `rgba` 의 `a` 값은 두 연산하는 값이 일치해야함
  - `rgba` 의 `a`값을 연산하기 위해 `opacify()`와 `transparentize()`함수를 사용하여 연산할 수 있음

```scss
div {
  color: #123456 + #345678;
  // R: 12 + 34 = 46
  // G: 34 + 56 = 8a
  // B: 56 + 78 = ce
  background: rgba(50, 100, 150, 0.5) + rgba(10, 20, 30, 0.5);
  // R: 50 + 10 = 60
  // G: 100 + 20 = 120
  // B: 150 + 30 = 180
  // A: Alpha channels must be equal
}
```

```scss
$color: rgba(10, 20, 30, 0.5);
div {
  color: opacify($color, 0.3); // 30% 더 불투명하게 / 0.5 + 0.3
  background-color: transparentize($color, 0.2); // 20% 더 투명하게 / 0.5 - 0.2
}
```
