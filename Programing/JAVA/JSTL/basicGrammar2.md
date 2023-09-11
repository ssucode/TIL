## 비교연산자
### 1. eq(==)
#### 문자열 또는 숫자가 같으면 참입니다. null 또는 빈 문자열 인지도 확인할 수 있습니다.
```html
<c:if test="${name == '홍길동'}">
<c:if test="${name eq '홍길동'}">
<c:if test="${name == null}">
<c:if test="${name eq null}">
<c:if test="${num == 5}">
<c:if test="${num eq 5}">
```

### 2. ne(!=)
#### 문자열 또는 숫자가 다르면 참입니다.
```html
<c:if test="${name != '홍길동'}">
<c:if test="${name ne '홍길동'}">
<c:if test="${num != 5}">
<c:if test="${num ne 5}">
```

### 3. empty
#### List 또는 배열이 비어있거나, 문자열이 null 또는 빈 문자열이면 참을 반환합니다. 숫자 0은 eq(==) 로 비교해야 합니다.
```html
<c:if test="${empty name}">
```

### 4. not empty
#### List 또는 배열이 비어 있지 않을 경우, 문자열이 값이 있을 경우 참을 반환합니다.
```html
<c:if test="${not empty name}">
```

## 논리연산자
### and (&&)
#### 모두 참일때 참이 됩니다.
```html
<c:if test="${a > b and c < d}">
<c:if test="${a > b && c < d}">
```

### or (||)
#### 둘중 하나라도 참이면 참이 됩니다.
```html
<c:if test="${a > b or c < d}">
<c:if test="${a > b || c < d}">
```

### not (!)
#### 논리를 반전합니다.
```html
<c:if test="${not a == ''}">
<c:if test="${! a == ''}">
```