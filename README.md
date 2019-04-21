### @ERROR_FIX

---

### @Jquery Not Working

- jquery.js import 확인

---

### @Ajax Encoding

- java -> jsp 로 한글 보낼때 깨짐 현상
- java 에서는 URLEncoder.encode(foo); 
- jsp 에서는 decodeURIComponent(bar);

---

### @Tomcat Server failed to start

- 프로젝트 복사, 변경 오류 : Servers - server.xml - &lt; Context docBase=" ... &gt; 에서 중복 삭제
- 서블릿 매핑 설정 오류 : 서블릿 매핑 확인
 
---

### @Unknown Tag (c:...), @Jstl Not Working

- jstl-api.jar, standard.jar import 확인
- &lt;%@taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %&gt; 작성 확인
- 오타 확인 (예 : c:forEach (O), c:foreach(X))

---

### @Json Not Working

- WEB-INF - lib 에 json.jar, json-api.jar import 확인

---

### @Check Json Type

- Javascript에서 Json 여부 확인 할 수 있는 External Method 발견하지 못함
- Json을 stringify 했을때 길이가 일정하게 2만큼 길어짐
```javascript

	function isJson(data) {
		var oldData = data;
		var newData = JSON.stringify(data);
		if (Object.keys(oldData).length == (Object.keys(newData).length - 2)) {
			return false;
		} else {
			return true;
		}
	}
 ```
 
 ---
 
 ### @Dismantle Json Layers
 
 - 두가지 방법 존재
 ```javascript
 	function firstMethod(foo){
 		$.each(foo, function() {
		...
		}); 
 	}
```
```javascript
	function secondMethod(foo){
		for(var bar in foo){
		foo[bar]...
		}
	}
```
