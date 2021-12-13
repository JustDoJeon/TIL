# Web Storage

●  Web Storage이란 무엇인가요?   <BR>

● Web Storage의 종류와 설명<BR>

● 실습 <br>


------

## ***\*💡\** Web Storage이란 무엇인가요?

●  웹 스토리지는 서버가 아닌, 클라이언트에 데이터를 저장할 수 있도록 지원하는 HTML5의 새로운 기능입니다. <br>

● 웹 스토리지와 쿠키의 기능 자체는 유사하지만, 쿠키는 약 4KB까지 밖에 저장 공간을 이용하지 못하는 반면에 웹 스토리지는 약 5MB까지 저장 공간을 이용할 수 있습니다.<br>

●  자세한 최신 정보는 https://www.w3.org/TR/webstorage/ 여기서 볼 수 있습니다. <br>

```
참고) XML 표준사이트 <br>
- https://www.w3.org/TR/webstorage/ 
```

------

## ***\*💡\**Web Storage의 종류  

<h5> 1) 로컬 스토리지 (Local Storage)</h5>

  ● 로컬 스토리지는 브라우저에 반영구적으로 데이터를 저장하며, 브라우저를 종료해도 데이터가 유지됩니다.<br>

  ● 도메인이 다른 경우에는 로컬 스토리지에 접근할 수 없습니다. <br>

  ● 위에 말과 같지만 도메인마다 별도로 로컬 스토리지를 생성합니다. <BR>

 ```
 ● 로컬 스토리지 구현과 사용 ( JavaScript)
 
 //로컬스토리지 저장
localStorage.loginId = value;
localStorage.setItem("key", value);

//특정 로컬스토리지 불러오기
localStorage.loginId;

localStorage.getItem("key");

//전체 로컬스토리지 데이터 불러오기
localStorage.getItem(); 

//특정 로컬스토리지 삭제
localStorage.removeItem("key");


//로컬스토리지 전체 삭제
localStorage.clear();
 ```

![로컬스토리지](https://user-images.githubusercontent.com/52389219/126490778-1fc9913a-68ec-4ea9-822a-8282bce49e13.PNG) <H6>로컬 스토리지 실행과 웹 브라우저상 확인 사진<br>


<h5> 2) 세션 스토리지(Session Storage) </h5>

 ● SessionStorage는 데이터의 지속성과 액세스 범위에 특수한 제한이 존재합니다. <br>

 ● SessionStorage는 windows 전역 객체의 sessionStorage라는 컬렉션을 통해 저장/조회가 이루어집니다.<br>

 ● SessionStorage는 데이터가 지속적으로 보관되지 않습니다. 이는 마치 브라우저 기반 세션 쿠키와 그 성질이 비슷한데, 현재 페이지가 브라우징 되고 있는 브라우저 큰텍스트 내에서만 데이터가 유지됩니다. <br>

 ● SessionStorage 역시 Web Storage의 기본 보안 처럼 도메인별로 별도로 생성됩니다. 여기에 더불어 SessionStorage는 같은 사이트의 같은 도메인이라 할지라도 브라우저가 다르면 서로 다른 영역이 됩니다(즉 브라우저 컨텍스트가 다릅니다) <br>


 ```
 ● 세션 스토리지 구현과 사용(JavaScript)
 
//세션 저장
sessionStorage.setItem("key", value);

//특정 세션 값 불러오기
sessionStorage.getItem("key");

//특정세션 삭제
sessionStorage.removeItem("key");

//세션 전체 삭제
sessionStorage.clear();

● 세션 스토리지 구현과 사용(Java) , key와 value에는 각자 세션에 담을것을 정해서 설정
public String intro( HttpServletRequest req, HttpServletResponse res){

	//세션 생성
	req.getSession().setAttribute("key", value);

	//세션 값 반환
	req.getSession().getAttribute("key");

	//세션 값 반환 없으면 세션생성
	req.getSession();
	req.getSession(true); // 위에꺼와 같음
	
	//세션 값 반환 없으면 null 반환
	req.getSession(true); 
}



public void filter(ServletRequest req, SercletResponse res){
	HttpSession session = request.getSession();
}

// 세션종료 모두삭제
session.invalidate(); 

// Key인 세션 제거
session.removeAttribute("key"); 

// 세션 속성의 이름들을 Enumeration 객체 타입으로 리턴
session.getAttributeNames();  

// 1970년 1월 1일 0시 0초를 기준으로 하여 현재 세션이 생성된 시간까지 경과한 시간을 계산하여 1/1000초 값으로 리턴
session.getCreationTime();
 ```

  ![세션스토리지 확인](https://user-images.githubusercontent.com/52389219/126490901-b1fd2f22-1cb4-4cba-8117-924a0857a886.PNG)

 

<H6>세션 스토리지 실행과 웹 브라우저상 확인 사진1<br>

 

![세션스토리지](https://user-images.githubusercontent.com/52389219/126491030-8a2f31ca-176a-4241-8fb6-a52681d8c7e7.PNG)

  

<H6>세션 스토리지 실행과 웹 브라우저상 확인 사진2<br>

 

# Referece

● https://untitledtblog.tistory.com/47

● [www.tutorialrepublic.com/html-tutorial/html5-web-storage.php](https://www.tutorialrepublic.com/html-tutorial/html5-web-storage.php)

● https://eblo.tistory.com/109

● [developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage](https://developer.mozilla.org/en-US/docs/Web/API/Window/sessionStorage)

