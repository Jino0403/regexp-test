#정규표현식(RegExp)

정규식, Regular Expression

## 역할

- 문자 검색(search)
- 문자 대체(replace)
- 문자 추출(extract)

## 테스트 사이트
https://regexr.com/

## 정규식 생성
```js 
// 생성자
new RegExp('표현', '옵션')
new RegExp('[a-z]', 'gi' )
// 정규표현식의 모든 내용을 검색하겠다는 뜻의 g옵션과 대소문자 구별 안하겠다는 I 옵션사용

// 리터럴
/표현/옵션
/[a-z]/gi
```
## 예제문자

``` js
const str = `
010-1234-5678
thesecon@gmail.com
http://www.omdbapi.com/?apikey=7035c60&s=frozen
The quick brown fox jumps over the lazy dog.
abbcccdddd
`

// const regexp = new RegExp('the','gi')
const regexp = /the/gi
console.log(str.match(regexp))
```

## 메소드

메소드 | 문법 | 설명
--|--|--
test | `정규식.test(문자열)` | 일치 여부 (boolean) 반환
match | `문자열.match(정규식)` | 일치하는 문자의 배열 (Array) 반환
replace | `문자열.replace(정규식,대체문자)` | 일치하는 문자를 대체

## 예제문자

```js
let str = `
010-1234-5678
thesecon@gmail.com
http://www.omdbapi.com/?apikey=7035c60&s=frozen
The quick brown fox jumps over the lazy dog.
abbcccdddd
`

const regexp = /fox/gi
// console.log(regexp.test(str))
str = str.replace(regexp,"AAA")
console.log(str)

```

# 플래그(옵션)

플래그 | 설명
--|--
g | 모든 문자 일치(global)
i | 영어 대소문자를 구분 않고 일치(ignore case)
m | 여러 줄 일치(multi line)

## 예제 문자

```js
let str = `
010-1234-5678
thesecon@gmail.com
http://www.omdbapi.com/?apikey=7035c60&s=frozen
The quick brown fox jumps over the lazy dog.
abbcccdddd
`

const regexp = /\.$/gim
// 마침표 기호 하나는 특정한 문자를 검색하는 일종의 패턴
// 명령이 아닌 일반적인 문자로 해석되게 하려면 앞에 \(백슬래시) 기호추가
// => escape 문자 (본래의 기능에서 벗어나 상태가 바뀌는 문자)
// $는 앞에 있는 하나의 단어로 그 해당하는 줄이 끝나는 부분을 찾아서 배열데이터 반환
// m의 의미는 전체줄에서 다 검색(x) 각각의 줄을 하나의 시작과 끝으로 보겠다 선언
console.log(str.match(regexp))
```


## 패턴(표현)

패턴 | 설명
--|--
^ab | 줄(Line) 시작에 있는 ab와 일치
ab$ | 줄(Line) 끝에 있는 ab와 일치
. | 임의의 한 문자와 일치
a&verbar;b | a 또는 b와 일치
ab? | b가 없거나 b와 일치
{3} | 3개 연속 일치
{3,} | 3개 이상 연속 일치
{3,5} | 3개 이상 5개 이하(3~5개) 연속 일치
[abc] | a또는 b 또는 c
[a-z] | a부터 z 사이의 문자 구간에 일치(영어 소문자)
[A-Z] | A부터 Z 사이의 문자 구간에 일치(영어 대문자)
[0-9] | 0부터 9사이의 문자 구간에 일치(숫자)
[가-힣] | 가부터 힣 사이의 문자 구간에 일치(한글)
\w | 63개 문자(Word, 대소영문52개 + 숫자10개 + _)에 일치
\b | 63개 문자에 일치하지 않는 문자 경계(Boundary)
\d | 숫자(Digit)에 일치
\s | 공백(Space, Tab 등)에 일치
(?=) | 앞쪽 일치(Lookahead)
(?<=) | 뒤쪽 일치(Lookbehind)