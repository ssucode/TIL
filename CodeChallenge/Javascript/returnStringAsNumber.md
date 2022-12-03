# 문자열을 숫자로 변환 - parsint 사용하지 않음

```Javascript
/**
 * parsint 없이 문자열을 숫자로 변환하는 함수 구현
 * Implementing a function to convert a string to a number without parsint
 * 공백은 숫자로 취급하지 않음
 * 첫번째 자리에 +,-가 들어올수 있음
 * 첫번째 이후 문자가 숫자가 아닌 열이 있으면 현재 열부터 이후 모두 무시 
 * 공백도 현재열부터 이후 모두 무시
 * @str 문자열
 */
function customParseInt(str) {
  let nextFlag = true;
  let strNumber = '';
  for (let i = 0; i < str.length; i++) {
    const char = str[i];
    if (!nextFlag) continue;
    if (char == '+' || char == '-'){
      if (i != 0) nextFlag = false;
      if (char == '+' && i != 0) continue;
      if (char == '-') continue;
    }
    if (char == ' ' || !(/[0-9-+]/g).test(char)) {
      nextFlag = false;
      continue;
    }
    strNumber += char;
  }
  return (strNumber) ? strNumber * 1: NaN;
}

const str = '+12 345-+BC'; // Input String
console.log(customParseInt(str)); // Output Number : 12
console.log(parseInt(str)); // Output Number : 12

const str = '-545BC'; // Input String
console.log(customParseInt(str)); // Output Number : -545
console.log(parseInt(str)); // Output Number : -545

const str = '+-12';
console.log(customParseInt(str)); // Output NaN
console.log(parseInt(str)); // Output NaN
```
