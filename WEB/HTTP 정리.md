------

# HTTP 정리

● HTTP란 무엇인가?  <BR>

● http/1.0 & http/1.1 & http/2.0 정리  <BR>

● http  vs https <br>

------

## ***\*💡\** HTTP란 무엇인가요?

● HTTP란 HyperText Transport Protocol의 약자로 웹서버와 클라이언트간의 문서를 교환하기 위한 통신규약이다. <br>

●  WWW의 분산되어 있는 Server와 Client 간에 Hypertext를 이용한 정보교환이 가능하도록 하는 통신 규약이다.<br>

●  HTTP는 웹에서만 사용하는 Protocol로 TCP/IP 기반으로 한 지점에서 다른 지점(보통 클라이언트와 서버)으로 요청과 응답을 전송한다.<br>

- HTTP Message 종류
  - Request : 요청 Message ( Client → Server )
  - Response : 응답 Message ( Server → Client )



![img](http://wiki.gurubee.net/download/attachments/26739929/3_HTTPRequestResponse.jpg)

<h5> HTTP의 특징 </h5>

● HTTP 메세지는 HTTP Server와 HTTP Client에 의해서 해석  <br>

● TCP/IP 프로토콜의 Application 계층에 위치  <br>

● TCP Protocol을 이용한다. (디폴트 포트 : 80 )  <br>

● 현재 Version 1.1  (RFC 2616) <br>

```
RPC란 무엇인가?<br>
- Remote Procedure Call, 분산 네트워크 시스템에서 다른 서버에 있는 프로그램의 코드를 사용해서 값을 받아옴.
```

------

## ***\*💡\** HTTP/1.0 , HTTP/1.1 , HTTP/2.0

<h5> HTTP/1.0 - 확장성 만들기</h5>

- HTTP/0.9 는 매우 제헌적이었고 브라우저와 서버 모두 좀 더 융통성을 가지도록 빠르게 확장되었다.

  ● 버전 정보가 각 요청 사이트내로 전송되기 시작했습니다.  (HTTP/1.0이 GET 라인에 붙은 형태로 )<br>

  ● 상태 코드 라인 또한 응답의 시작 부분에 붙어 전송되어, 브라우저가 요청에 대한 성공과 실패를 알 수 있고 그 결과에 대한 동작을 할 수 있게되었다. <br>

  ● HTTP 헤더 개념은 요청과 응답 모두를 위해 도입되어, 메타데이터 전송을 허용하고 프로토콜을 극도로 유연하고 확장 가능하도록 만들어줬다.<BR>

  ● 새로운 HTTP 헤더의 도움으로, 평이한 HTML 파일들 외에 다른 문서들을 전송하는 기능이 추가되었다.<BR

  

  <H6>● HTTP/1.0의 문제점 <br></H6>

  ​	● 매번 필요할 때마다 연결( 비 지속성 연결 방식) -> 성능의 저하 <br>

  ​	● GET/HEAD/POST 메소드만 허용한다. <br>

  ​	● 한번에 얻어서 가져올수 있는 데이터의 양이 제한적이다. <br>

  ​	● URI의 크기도 작으며, 캐시 기능이 미흡하다. <br>

  

<h5> HTTP/1.1 - 표준 프로토콜</h5>

- HTTP/1.0의 성능 개선에 중점을 두었다. <br>

  ● 지속적인 연결을 가능하게 하는 persistent connection 지원한다. <br>

  ● http/1.0 에선 keep-alive 옵션을 줬어야했는데 이것이 default, 파이프라이닝을 추가해  여러 요청에 빠르게 응답할수 있다.<br>

  ● multiple request 처리가 가능해졌다. <br>

  ● GET,HEAD,POST,OPTIONS,DELELTE,TRACE,CONNET 메소드를 허용한다. <br>

  ● proxy server와 캐시 기능 향상 (Cashe-Control) <br>

  ● request/response가 pipeline 방식으로 진행 <br>

  -  파이프라인 방식

  ​	● 응답 메세지가 도착하지 않은 상태에서 연속적인 요구 메세지를 서버에 전달한다. <br>

  ​	● 이때, 서버는 요구 메세지를 수신한 순서대로 응답메세지를 클라이언트에 전달한다.<br>

  ​	● 연결과 종료횟수를 줄임으로서 네트워크 자원이 절약된다. <br>

  ​	● 발생하는 패킷의 숫자를 감소시키고, 네트워크 트래픽도 감소시킨다. <br>

  ![img](http://wiki.gurubee.net/download/attachments/26739929/3_HTTPConnectionHandling.png)

<h5> HTTP/2.0 - 더 나은 성능을 위한 프로토콜</h5>

<h6>● HTTP/2.0의 특징 </h6>

● Server Push - 필요한 리소스를 클라이언트 요청없이 보내준다. <br>

●  Multiplexed Streams - 한 커넥션에서 여러 메세지를 동시에 주고받는다.<br>

●  HPACK 압축 -  헤더 중복 검사를 한다.<br>

●  다양한 라이브러리 및 프레임워크 연동을 지원한다.<br>

●  접속 로그를 Kafka에 전송해서 서버에 접근하지 않고도 확인이 가능하다.<br>

●  클라이언트 측 로드밸런싱으로 부하를 분산한다.<br>



# Referece

● https://www.w3.org/Protocols/rfc2616/rfc2616.html

● http://wiki.gurubee.net/pages/viewpage.action?pageId=26739929

● https://developer.mozilla.org/ko/docs/Web/HTTP/Basics_of_HTTP/Evolution_of_HTTP