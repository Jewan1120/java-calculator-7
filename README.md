# 문자열 덧셈 계산기

## 기능 요구 사항
- 쉼표(,) 또는 콜론(:)을 구분자로 가지는 문자열을 전달하는 경우 구분자를 기준으로 분리한 각 숫자의 합을 반환한다.
    - 예: "" => 0, "1,2" => 3, "1,2,3" => 6, "1,2:3" => 6
- 앞의 기본 구분자(쉼표, 콜론) 외에 커스텀 구분자를 지정할 수 있다. 커스텀 구분자는 문자열 앞부분의 "//"와 "\n" 사이에 위치하는 문자를 커스텀 구분자로 사용한다.
    - 예를 들어 "//;\n1;2;3"과 같이 값을 입력할 경우 커스텀 구분자는 세미콜론(;)이며, 결과 값은 6이 반환되어야 한다.
- 사용자가 잘못된 값을 입력할 경우 `IllegalArgumentException`을 발생시킨 후 애플리케이션은 종료되어야 한다.

## 고려 사항
- 커스텀 기본자가 있을 경우 커스텀 구분자와 기본 구분자를 함께 사용하여 문자열 분리
  - ~~기존 구분자는 무효?~~ &rarr; `기존 구분자 + 커스텀 구분자`로 문자열을 분리
- 비어 있는 문자열은 "0"으로 연산
- 터무니 없이 큰 숫자를 더해야 할 경우가 있을 수 있으므로 연산은 `BigInteger`로 처리
- 잘못된 입력 &rarr; 예외 처리
  - 기본 구분자 + 커스텀 구분자 외에 다른 특수문자가 들어올 경우
  - 커스텀 구분자 구분 형식이 "//"로 시작하지만 "\n"로 끝나지 않을 경우
  - 커스텀 구분자에 문자가 아니라 문자열이 올 경우

## 기능 구현 목록
- [x] 문자열 덧셈 계산기 View 구성
- [x] 계산할 문자열 입력 받기
- [x] 커스텀 구분자 검출 및 유효성 확인
- [x] 커스텀 구분자를 기존 구분자에 추가
- [x] 기본 구분자와 커스텀 기본자를 이용해 문자열 분리
- [x] 분리된 문자열이 숫자로 이루어졌는지 유효성 확인
- [x] 분리된 숫자들의 합을 계산하고 반환
  - [x] 분리된 문자열이 비어있는 경우 0으로 계산