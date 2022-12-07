# Happy Number
Example 1:
```Javascript
Input: n = 19
Output: true

Explanation:
1² + 9² = 82
8² + 2² = 68
6² + 8² = 100
1² + 0² + 0² = 1
```
Example 2:
```Javascript
Input: n = 2
Output: false
```

Constraints:
```Javascript
1 <= n <= 2³¹ - 1
```
```Javascript
/**
 * 숫자로 입력한 입력값 n을 문자열로 변환해 split 함수로 1글자씩 배열에 저장한다.
 * 배열에서 reduce를 활용해 제곱합을 구해 calculate 변수에 저장한다.
 * - Math.pow() 함수는 base^exponent처럼 base 에 exponent를 제곱한 값을 반환합니다.
 * - reduce() 는 배열.reduce((누적값, 현잿값, 인덱스, 요소) => { return 결과 }, 초깃값); - map과 비슷합니다.
 * stack 이라는 배열에 이미 calculate 값이 있다면 무한반복되니 방지를 위해 있는 값이면 false를 반환합니다.
 * - includes 는 배열에 값이 있는지 true, false 를 반환합니다.
 * stack 에 없는 수이면 stack 배열에 추가합니다.
 * 반환값에 함수를 넣어 다시 호출(재귀)합니다.
 * @param {number} n
 * @param {Array} stack
 */
const isHappy = (n, stack = []) => {
  if (n === 1) return true;
  let nums = n.toString().split('');
  let calculate = nums.reduce((sum, num) => sum += Math.pow(Number(num), 2), 0);
  if (stack.includes(calculate)) return false;
  stack.push(calculate);
  return isHappy(calculate, stack);
};

console.log(isHappy(2));  // output: false
console.log(isHappy(19)); // output: true
 
```
