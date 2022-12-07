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
 * 숫자로 입력한 입력값 n을 문자열로 변환해 1글자씩 끊어 배열에 저장한다.
 * 배열에서 reduce를 활용해 제곱합을 구해 calculate 변수에 저장한다.
 * dp 라는 배열에 이미 calculate 값이 이미 있다면 무한 반복하게 될테니 그것을 방지하기 위해 이미 있는 값이면 멈추고 false를 반환한다.
 * dp 에 없는 수이면 dp 배열에 추가한다.
 * 반환값에 함수를 넣어 주면서 재귀적으로 실행될 수 있도록 한다.
 */
 const isHappy = (n, dp = []) => {
    if (n === 1) return true;

    let nArray = String(n).split('');
    let calculate = nArray.reduce((sum, element) => sum += Math.pow((element), 2), 0);

    if (dp.includes(calculate)) return false;
    dp.push(calculate)
    return isHappy(calculate, dp);
};
 
```
