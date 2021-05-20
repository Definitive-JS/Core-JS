## 2021-05-20 함수

### 함수(function) 란?
함수(function)란 하나의 특별한 목적의 작업을 수행하도록 설계된 독립적인 블록을 의미합니다.
이러한 함수는 필요할 때마다 호출하여 해당 작업을 반복해서 수행할 수 있습니다.

```예제
function addNum(x, y) {
    return x + y;
}
document.write(addNum(2, 3));
```
<br/>

### 자바스크립트 함수
- 자바스크립트에서는 함수도 하나의 타입(datatype)입니다.
- 따라서 함수를 변수에 대입하거나, 함수에 프로퍼티를 지정하는 것도 가능합니다.
- 또한, 자바스크립트 함수는 다른 함수 내에 중첩되어 정의될 수도 있습니다.
<br/>

### 반환(return)문
- 자바스크립트에서 함수는 반환(return)문을 포함할 수 있습니다.
- 이러한 반환문을 통해 호출자는 함수에서 실행된 결과를 전달받을 수 있습니다.
- 반환문은 함수의 실행을 중단하고, return 키워드 다음에 명시된 표현식의 값을 호출자에게 반환합니다.
- 반환문은 배열이나 객체를 포함한 모든 타입의 값을 반환할 수 있습니다.
```
function multiNum(x, y) {
    return x * y;         // x와 y를 곱한 결과를 반환함.
}
var num = multiNum(3, 4); // multiNum() 함수가 호출된 후, 그 반환값이 변수 num에 저장됨.
document.write(num);
```
<br/>

### 변수의 유효 범위(variable scope)
자바스크립트에서 객체나 함수는 모두 변수(variable)입니다.
변수의 유효 범위(scope)란 해당 변수가 접근할 수 있는 변수, 객체 그리고 함수의 집합을 의미합니다.
자바스크립트에서 변수는 유효 범위에 따라 다음과 같이 구분됩니다.
1. 지역 변수(local variable)
2. 전역 변수(global variable)
<br/>

### 지역 변수(local variable)
- 지역 변수(local variable)란 함수 내에서 선언된 변수를 가리킵니다.
- 이러한 지역 변수는 변수가 선언된 함수 내에서만 유효하며, 함수가 종료되면 메모리에서 사라집니다.
- 함수의 매개변수 또한 함수 내에서 정의되는 지역 변수처럼 동작합니다.
```
function localNum() {
    var num = 10; // 지역 변수 num에 숫자 10을 대입함.
    document.write("함수 내부에서 변수 num의 타입은 " + typeof num + "입니다.<br>"); // number
}
localNum();       // 함수 localNum()을 호출함.
document.write("함수의 호출이 끝난 뒤 변수 num의 타입은 " + typeof num + "입니다."); // undefined
```
<br/>

### 전역 변수(global variable)
- 전역 변수(global variable)란 함수의 외부에서 선언된 변수를 가리킵니다.
- 이러한 전역 변수는 프로그램의 어느 영역에서나 접근할 수 있으며, 웹 페이지가 닫혀야만 메모리에서 사라집니다.
```
var num = 10; // 전역 변수 num을 선언함.
function globalNum() {
    document.write("함수 내부에서 변수 num의 값은 " + num + "입니다.<br>"); // 10
    num = 20; // 전역 변수 num의 값을 함수 내부에서 변경함.
}
globalNum();  // 함수 globalNum()을 호출함.
document.write("함수의 호출이 끝난 뒤 변수 num의 값은 " + num + "입니다."); // 20
```
<br>

### 함수의 유효 범위
대부분의 프로그래밍 언어에서는 블록 내에서 정의된 변수를 블록 외부에서는 접근할 수 없습니다.
블록(block)이란 코드 내에서 중괄호({})로 둘러싸인 부분을 가리킵니다.
이러한 블록을 기준으로 하는 유효 범위를 블록 단위의 유효 범위라고 합니다.
하지만 자바스크립트는 다른 언어와는 달리 함수를 블록 대신 사용합니다.
자바스크립트에서 함수는 자신이 정의된 범위 안에서 정의된 모든 변수 및 함수에 접근할 수 있습니다.
'전역 함수'는 모든 전역 변수와 전역 함수에 접근할 수 있습니다.
반면, 다른 함수 내에 정의된 '내부 함수'는 그 함수의 부모 함수(parent function)에서 정의된 모든 변수 및 부모 함수가 접근할 수 있는 모든 다른 변수까지도 접근할 수 있습니다.
```
// x, y, name을 전역 변수로 선언함.
var x = 10, y = 20;
// sub()를 전역 함수로 선언함.
function sub() {
    return x - y;     // 전역 변수인 x, y에 접근함.
}
document.write(sub() + "<br>");
// parentFunc()을 전역 함수로 선언함.
function parentFunc() {
    var x = 1, y = 2; // 전역 변수와 같은 이름으로 선언하여 전역 변수의 범위를 제한함.
    function add() {  // add() 함수는 내부 함수로 선언됨.
        return x + y; // 전역 변수가 아닌 지역 변수 x, y에 접근함.
    }
    return add();
}
document.write(parentFunc());
```
<br/>

### 매개변수와 인수
- 자바스크립트에서는 함수를 정의할 때는 매개변수의 타입을 따로 명시하지 않습니다.
- 함수를 호출할 때에도 인수(argument)로 전달된 값에 대해 어떠한 타입 검사도 하지 않습니다.
- 함수를 호출할 때 함수의 정의보다 적은 수의 인수가 전달되더라도, 다른 언어와는 달리 오류를 발생시키지 않습니다.
- 이 같은 경우 자바스크립트는 전달되지 않은 나머지 매개변수에 자동으로 undefined 값을 설정합니다.
- 매개변수(parameter)란 함수의 정의에서 전달받은 인수를 함수 내부로 전달하기 위해 사용하는 변수를 의미합니다.

인수(argument)란 함수가 호출될 때 함수로 값을 전달해주는 값을 말합니다.
```
function addNum(x, y, z) { // x, y, z라는 3개의 매개변수를 가지는 함수 addNum()을 정의함.
    return x + y + z;
}
addNum(1, 2, 3); // 인수로 1, 2, 3을 전달하여 함수를 호출함. -> 6
addNum(1, 2);    // 인수로 1, 2을 전달하여 함수를 호출함. -> NaN
addNum(1);       // 인수로 1을 전달하여 함수를 호출함. -> NaN
addNum();        // 인수로 아무것도 전달하지 않고 함수를 호출함. -> NaN
```
<br/>

### 미리 정의된 전역 함수
- 자바스크립트는 사용자의 편의를 위해 다양한 기능의 여러 전역 함수를 미리 정의하여 제공합니다.
- 이러한 전역 함수는 자바스크립트의 어떤 타입의 객체에서도 바로 사용할 수 있습니다.
- 자바스크립트에서 미리 정의되어 있는 전역 함수는 다음과 같습니다.
1. eval()
2. isFinite()
3. isNaN()
4. parseFloat()
5. parseInt()
6. decodeURI()
7. decodeURIComponent()
8. encodeURI()
9. encodeURIComponent()
10. escape()
11. unescape()
12. Number()
13. String()
<br/>

### eval()
eval() 함수는 문자열로 표현된 자바스크립트 코드를 실행하는 함수입니다.
```
문법
eval("문자열");
```
```
var x = 10, y = 20;
var a = eval("x + y"); // 30
var b = eval("y * 3"); // 60
document.write(a + "<br>" + b);
```
<br/>

### isFinite()
isFinite() 함수는 전달된 값이 유한한 수인지를 검사하여 그 결과를 반환합니다.
만약 인수로 전달된 값이 숫자가 아니라면, 숫자로 변환하여 검사합니다.
```
문법
isFinite(검사할값);
```
```
예제
isFinite(123);       // true
isFinite(123e100);   // true
isFinite(0);         // true
isFinite(true);      // true
isFinite(false);     // true
isFinite(null);      // true
isFinite("123");     // true
isFinite("");        // true
isFinite("문자열");  // false
isFinite(undefined); // false
isFinite(NaN);       // false
```
<br/>

### isNaN()
isNaN() 함수는 전달된 값이 NaN인지를 검사하여 그 결과를 반환합니다.
만약 인수로 전달된 값이 숫자가 아니라면, 숫자로 강제 변환하여 검사합니다.
전달된 값이 숫자인지 아닌지를 확인하기 위하여 typeof 연산자를 대신 사용할 수도 있습니다.
```
문법
isNaN(검사할값);
```
```
예제
isNaN(123);       // false
isNaN(123e100);   // false
isNaN(0);         // false
isNaN(true);      // false
isNaN(false);     // false
isNaN(null);      // false
isNaN("123");     // false
isNaN("");        // false
isNaN("문자열");  // true
isNaN(undefined); // true
isNaN(NaN);       // true
```
<br/>

### parseFloat()
parseFloat() 함수는 문자열을 파싱하여 부동 소수점 수(floating point number)로 반환합니다.
```
문법
parseFloat("문자열");
```
```
예제
parseFloat("123");        // 123
parseFloat("123.000");    // 123
parseFloat("123.456");    // 123.456
parseFloat("12 34 56");   // 12
parseFloat(" 123 ");      // 123
parseFloat("123 초콜릿"); // 123
parseFloat("초콜릿 123"); // NaN
```
<br/>

### parseInt()
parseInt() 함수는 문자열을 파싱하여 정수로 반환합니다.
```
문법
parseInt("문자열");
```
``` 
예제
parseInt("123");        // 123
parseInt("123.000");    // 123
parseInt("123.456");    // 123
parseInt("12 34 56");   // 12
parseInt(" 123 ");      // 123
parseInt("123 초콜릿"); // 123
parseInt("초콜릿 123"); // NaN
parseInt("10", 10);     // 10
parseInt("10", 8);      // 8
parseInt("10", 16);     // 16
parseInt("0x10");       // 16
```
<br/>

### Number()
Number() 함수는 전달받은 객체의 값을 숫자로 반환합니다.
```
문법
Number(객체);
```
```
예제
Number("123");        // 123
Number("123.000");    // 123
Number("123.456");    // 123.456
Number("12 34 56");   // NaN
Number("123 초콜릿"); // NaN
Number(true);         // 1
Number(false);        // 0
Number(new Date());   // 현재 날짜에 해당하는 숫자를 반환함.
Number(null);         // 0
```
<br/>

### String()
String() 함수는 전달받은 객체의 값을 문자열로 반환합니다.
```
문법
String(객체);
```
```
예제
String(123);        // 123
String(123.456);    // 123.456
String("123");      // 123
String(new Date()); // 현재 날짜에 해당하는 문자열을 반환함.
String(null);       // null
String(true);       // true
String(false);      // false
String(Boolean(1)); // true
String(Boolean(0)); // false
```
<br/>

### encodeURI()와 encodeURIComponent()
encodeURI() 함수는 URI에서 주소를 표시하는 특수문자를 제외하고, 모든 문자를 이스케이프 시퀀스(escape sequences) 처리하여 부호화합니다.
하지만 encodeURIComponent() 함수는 URI에서 encodeURI() 함수에서 부호화하지 않은 모든 문자까지 포함하여 이스케이프 시퀀스 처리합니다.
```
문법
encodeURI(부호화할URI);
encodeURIComponent(부호화할URI);
```
```
예제
var uri = "http://google.com/search.php?name=홍길동&city=서울";
var enc1 = encodeURI(uri);
var enc2 = encodeURIComponent(uri);
document.write(enc1 + "<br>" + enc2);
```
<br/>

### decodeURI()와 decodeURIComponent()
decodeURI() 함수는 encodeURI() 함수나 다른 방법으로 만들어진 URI(Uniform Resource Identifier)를 해독합니다.
decodeURIComponent() 함수는 encodeURIComponent() 함수나 다른 방법으로 만들어진 URI 컴포넌트를 해독합니다.
```
문법
decodeURI(해독할URI);
decodeURIComponent(해독할URI);
```
```
예제
var uri = "http://google.com/search.php?name=홍길동&city=서울";
var enc1 = encodeURI(uri);
var enc2 = encodeURIComponent(uri);
document.write(enc1 + "<br>" + enc2 + "<br><br>");
```
<br/>

### escape()와 unescape()
escape() 함수는 전달받은 문자열에서 특정 문자들을 16진법 이스케이프 시퀀스 문자로 변환합니다.
unescape() 함수는 전달받은 문자열에서 escape() 함수나 다른 방법으로 만들어진 16진법 이스케이프 시퀀스 문자를 원래의 문자로 변환합니다.
```
문법
escape("변환할문자열");
unescape("원래대로변환할문자열");
```
```
예제
var str = "Hello! World ?#$";
var esc = escape(str);
var une = unescape(esc);
document.write(esc + "<br>" + une);
var dec1 = decodeURI(enc1);
var dec2 = decodeURIComponent(enc2);
document.write(dec1 + "<br>" + dec2);
```
