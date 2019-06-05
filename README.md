### @ERROR Dictionary

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
 
 - 두가지 방법 존재(2nd better - key 조회 가능)
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

---

### @Repeat String Without Loop

 - <http://commons.apache.org/proper/commons-lang/download_lang.cgi>
 ```java
 void repeat(str,num){
 	StringUtils.repeat(str, num);
 }
 ```

---

### @Connection Timed Out : Connect

- 방화벽 인바운드 규칙 확인
- Ip, Port 다시 한번 확인
- 사설 IP 아닌지 

---

### @git push not working

* 메시지

```git
- 'origin' doesn't appear to be a git repository.
- Could not read from repository.
```

* 로컬과 remote repository 연결 안되어 있는 상태
- git remote add origin remote URL 로 연결시켜줘야 함

---

### @git pull not working

* 메시지

```git
- There is no tracking information for the current branch.
- Please specify which branch you want to merge with.
```

* 로컬과 remote repository 연결 설정 문제
- git branch --set-upstream-to=origin/master master

---

### @modify git commit

* push 하기 전 상태에 사용 

* git commit --amend

* vi 처럼 내용 수정하고 저장하면 수정됨

---

### @ajax spring not working

* request는 정상적으로 가능하지만 response에 문제가 생겨서 error가 실행됨

```java
@RequestMapping(value = "/foo")
public void foo(HttpServletResponse response ...)
{
	response.getWriter().write("bar");
}
```

* response의 writer를 통해 response 처리를 할 수 있음

* 컨트롤러 메소드에 리턴값 매핑설정이 되어있는 경우 void 처리하면 해결 가능

* writer에 string 값이 아닌 int를 넣으면 전달되지 않기도 

---

### @mysql ssl error

* db url에 verifyServerCertificate=false&useSSL=false 추가해주면됨

* 그래도 오류날 경우 "&" -> "&amp;" 로  

---

### @json printing object object

* javascript 에서 foo로 출력하면 안되고 foo.value로 해야함

* 올바른 예시

```javascript
success: function(data){
	if(data=="") return;
	var parsed = JSON.parse(data);
	var result = parsed.result;
	for(var i = 0; i < result.length; i++){
		addBbsContent(result[i][0].value, result[i][1].value, result[i][2].value, result[i][3].value);
	}
	var pageNumber = Number(parsed.last);
}
```

* 틀린 예시

```javascript
success: function(data){
	if(data=="") return;
	var parsed = JSON.parse(data);
	var result = parsed.result;
	for(var i = 0; i < result.length; i++){
		addBbsContent(result[i][0], result[i][1], result[i][2], result[i][3]);
	}
	var pageNumber = Number(parsed.last);
}
```
