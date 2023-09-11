## 라이브러리 설정
상단에 해당 라이브러리를 설정해줘야 사용할수 있음
```java
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
```

### 1. c:if
```html
<c:set var="user" value="admin" />
<!-- 조건에 맞을 경우 -->
<c:if test="${user eq 'admin'}">
	<p> <c:out value="${user}" /> </p>
</c:if>
```

### 2. c:when
```html
<c:set var="user" value="admin" />
<c:choose>
	<!-- 조건에 맞을 경우 -->
	<c:when test="${user eq 'admin'}">
	<p> <c:out value="${user}" /> </p>
	</c:when>
	<c:when test="${user eq 'normal'}">
	<p> <c:out value="${user}" /> </p>
	</c:when>
	<!-- 그외일 경우 -->
	<c:otherwise>
		<p>none</p>
	</c:otherwise>
</c:choose>
```

### 3. c:forEach
```html
<!-- ${list}를 item으로 선언, ${item.키}로 출력 -->
<c:forEach var="item" items="${list}" varStatus="status">
	<div>${item.name}</div>
</c:forEach>
```

### 4. c:set
- model에 vo나 map을 담았을경우
	```java
	model.addAttribute("user", new User());
	model.addAttribute("user", new HashMap<String, String>());
	```
	```html
	<!-- jstl에서 해당 model ${board}에 담은값을 변경할수 있음-->
	<c:set target="${user}" property="title" value="제목값 변경" />
	<c:out value="${user.title}" />
	```
- 일반적인 변수를 설정하는 경우
	```html
	<c:set var="user" value="admin" />
	<p> <c:out value="${user}" /> </p>
	```
 

### 5. c:remove
```html
<!-- 선언된 키값 user 삭제 -->
<c:remove var="user"/>
```

### 6. c:out
<c:out>문을 사용하는 이유는 xss 공격을 방어하기 위해서 사용함
또한 HTML 문자를 탈락(escape)시키는 기능도 가지고 있음
```html
>  - &lt;
<  - &gt;
&  - &amp;
'  - &#039;
'' - &#034;
```

```html
<!-- board 값이 없으면 default로 foo를 출력함 -->
<c:out value="${board}" default="foo" />
```