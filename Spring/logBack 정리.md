------

# *About Logback**

## ***\*💡\** 자바 로깅시스템

```
각 프로그래밍 언어마다 고유의 로깅 프레임워크을 지원하지만, 특히 자바의 경우에는 그 프레임웍 수가 많고 발전된 모델이 많아서 자바 프레임워크를 살펴보고 넘어가고자 합니다.

자바는 역사가 오래된 만큼 많은 로깅 프레임웍을 가지고 있습니다. log4j, logback, log4j2,apache common logging, SLF4J 등 다양한 프레임워크 들이 있는데, 그 개념과 장단점을 알아보고 사용해야합니다.

```




## ***\*💡\** Logback 알아보기


●  기존에는 로그를 관리하기 위해 구현체로써 log4j가 사용되었습니다.<br>

● 기존의 구현체 보다 안정성이 높고 편리하게 로그를 관리하기 위해 Slf4j와 그 구현체로써 Logback이 고안되었습니다.<br>

●  slf4j  API를 구현하므로 다른 logging framework와 logback 간에 쉽게 전환이 가능합니다. <br>


<h5> Logback의 사용 이유 및 장점 </h5>

1.   log4j보다 약 10배 정도 빠르게 수행되도록 내부가 변경되었으며, 메모리 효율성도 좋아졌다. <br>

2. 문서화가 잘 되어 있다. <br>

3.  설정 파일을 변경 하였을 경우, 서버 재가동 없이 변경 내용이 자동으로 갱신된다.  <br>

4. 서버 중지 없이 I/O Failure에 대한 복구를 지원한다. <br>

```
참고) XML 표준사이트 <br>
-https://www.w3.org/TR/xml/
```

------

## *\*💡\** Logback의 Configuration 파일  
![Chapter 3: Configuration](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASkAAACPCAMAAACRdd33AAAAMFBMVEX///8AAADAwMCnp6fp6enQ0NBoaGjh4eGMjIxNTU2ampqysrJ8fHzHx8fZ2dnw8PBcrf+NAAAE0UlEQVR4nO2b6YKCIBCAmbK0c9//bRcRFDl0uMpgvh+6Eee3gkcOYwRBEATxdQDEJs+2aqofIPHDNDAB81C9phwDhIUMtR2VwLE5XYDjr/rIZmranE7JPTo83RVuF27iAddO7dgZ4M7EJ/4dz/EYTanE51MWbczU6OfGx9/3MKjdGbpOfHp3/LthTIQlsVdFKzXlu7L+ezz5pzFB34lV2puoqlRrel2mDObxXqF3SJny+BL1Ouo7pgzm8QJ0QsOr56uQ3N3hNU00IeYO77fYzYl6HfWZAs/HC5yFqQcMndqNi/cwH1Paij60cEzZp3n9itGeWkFVVm6KJZtaqMmUTZ67kLGK06liU+IMn+MupAlTmSqqzZTv3Jej6qpNsYxP0es3laumykzZRE9Aq2Dtpli2CdiAKTHGCJi2VUnV4J5rkaaEJFinVENeU1wVGAnVkNmUKaoiUwRxNOr++VMncZyQXsWvkNPU9EtNYocOS0ZTIB+xp3apTkxTjEx5oGMKC61T+PIgZVVrSFH9ALNBpgiCODq0TmEhU1jIFEEQR4fWKSxkCguZ+jGgKEEt4nscvU0ylVg+uHJ/g4Vn2a+Z2mrP812mLv6Yqe3m3N/m6mLiBCxrynyVZK8198KGyIPsT3zRcqacK/V+Y4gFPqLH4aeN0HYvNxi2Ku/XEU7uesNM7efVf5FCgqg1pBLXlzsVb3xfzhSmdVet6gV0bCFnJSN/g4p4PjMZ8SyO1jFMbpCRdPKXxedzipZW368KmfWmm/KVWlqWHZS7QgHaczfu0MGVN3K58LZlxPMcetm/dVP9Ei0tUtaFNgaq/zmVVRs7B8qUbFl2UO4KBWgbs94O4HWH+rqjpbUZocVEG+vp5jX6uticW6k1YyA9HZwPdrszHzfli5bWTFktZDqmEKa0AS1FSs0+vWl+VL/47gadmoRMRUuvZ1+Aqb3u4Ewts++19LNQgPZcXbde0XVTMvCZXzM8lKkpWpqnvPQVvYwpb95lRZ86WDZAG3Omvb3YHz/eIustYMq8hJQd9PZTq7WsqfeVn3G7wHqLXaPLbI4Oevup1VrWVDTh932uoAN7nYq9LUkK5/usqb1nCc7wDMuUON3n6U9I4diCqMrtnm0uP+5AFoepqM6wtHC+T5vaeuZZNuQn2VRRXD3bzIwaCqwv2rHbRFOMpQSAYQhtDtFh5ESwsiUHaH/Y1HZ7iAGjMUv+nKmtBhHjFWm4SQdGys+Z8rfoyuw+ppCNa9uNJqoG+3861RugjQRpquYAbSRYUy0FaBe9OK4KMoUl0BTE3Ra2h7pxIfZYmYKqAx8T0U3JB/vNqAobqGkquIIfJs0UHVNbuWmdQjE/tyNDBJEKzSIsZAoLmSII4ujQOoWFTGEhUwRBHB1ap7BY7/ZEvWjWAq2M8wg06jpi2GQKXaTyd1wUdoxDSOGFjF06KAFDHEPIfYXJ1Cqr/WL1etMmU0j2FOE37RxzrGVT2g/EPVNRo1rYqiN3K6bsd8xVutxYIch64SVY+4NdPgahplg7x5QPoYVmH4JJi76iixByI9N60xoB15FNXU8ZhD1Iaeoa3QCCjqmpSCP3fQYxEdttmnLds+zRqqlwGjUV8Ry9UVMsLsr1233+DmQKC5nCQqYIgiAIgvgy/2bkGUK8DmD6AAAAAElFTkSuQmCC)
```
logback의 configuration 파일은 매우 유연한 문법을 갖고있습니다.
configuration 태그는 내부에 최대 1개의 root태그를 갖고,
0개 이상의 appender와 logger태그를 가질수 있습니다.
```  
 <h5>  < logger > ,  로거 구성</h5>

 ```
- <logger> 는 필수 name 속성, 선택적으로  level 속성과 additivity 속성을 가집니다. 

- level 속성은 대소문자를 구분하지 않으면  TRACE, DEBUG, INFO, ERROR, ALL, OFF중 하나의 값으로 지정할 수 있습니다. 

- <appender-ref>태그로 포함된 appender는 명명된 로거에 추가됩니다. 
 ```

 <h5>  < root > ,  루트 로거 구성</h5>
 
```
- 루트 로거의 속성으로는 오직 단 하나의 level 속성만 허용됩니다.

- 가장 최상단의 로거이기 때문에 INHERITED 혹은 NULL 값은 레벨로 가질수 없습니다.

 ```


## *\*💡\**log4j2는 뭔가요?

![](https://blog.kakaocdn.net/dn/pz7AV/btqRL4pzCe1/A03Kx6hCy1KdzMgxHpNOf0/img.png)
 
 <h6> Multi Thread 환경에서 로깅 프레임워크 성능 비교 </h6>
  
<h5> ● 가장 최신에 나온 프레임 워크로써 Apache log4j의 다음 버전입니다.</h5>

 
<h5> ● logback과의 가장 큰 차이는 Multi Thread 환경에서 비동기 로거의 경우 다른 로깅 프레임워크보다 처리량이 훨씬 많고 대기 시간이 훨씬 짧습니다. </h5>
  

## ***\*💡\**logback 적용 예제

<h5> logback.xml </h5>

```xml

<?xml version="1.0" encoding="UTF-8"?>

<!-- [Layout] %m : 로그내용이 출력 %p : trace > debug > info > warn > error 등의 priority 
	출력 %r : 어플리케이션이 시작되어 로깅이벤트가 발생하는 시점까지의 경과시간을 밀리세컨드로 출력 %c : 예) 카테고리가 a.b.c 
	처럼 되어있다면 %c{2}는 b.c가 출력됩니다. %n : 플랫폼 종속적인 개행문자가 출력된다. \r\n 또는 \n 일것이다 %d 
	: 로깅이벤트가 일어나 날짜 출력 ( 프로그램의 실행속도를 느리게 한다.) 예) %d{HH:mm:ss} 또는 %d{dd MMMM yyyy 
	HH:mm:ss} %C : 호출자의 클래스명 출력 예) 클래스구조가 org.apache.xyz.SomeClass 처럼 되어있다면 %C{2}는 
	xyz.SomeClass 가 출력됩니다 %M : 로깅이 발생한 method 이름을 나타냅니다. %F : 로깅이 발생한 프로그램 파일명을 
	나타냅니다. %l : 로깅이 발생한 caller의 정보를 나타냅니다 %L : 로깅이 발생한 caller의 라인수를 나타냅니다 %x 
	: 로깅이 발생한 thread와 관련된 NDC(nested diagnostic context)를 출력합니다. %X : 로깅이 발생한 
	thread와 관련된 MDC(mapped diagnostic context)를 출력합니다. %% : % 표시를 출력하기 위해 사용한다. 
	%t : 로그이벤트가 발생된 쓰레드의 이름을 출력합니다 -->

<configuration scan="true" scanPriod="30 seconds">

	<appender name="SAMPLE"
		class="ch.qos.logback.core.ConsoleAppender">
		<encoder
			class="ch.qos.logback.core.encoder.LayoutWrappingEncoder">
			<layout class="ch.qos.logback.classic.PatternLayout">
				<Pattern>%d{HH:mm:ss.SSS} [%-5p] [%t] [%c{36}] - %m%n</Pattern>
			</layout>
			<charset>UTF-8</charset>
		</encoder>
	</appender>

	<!-- RULES for logging : TRACE < DEBUG < INFO < WARN < ERROR < FATAL -->
	<logger name="org.springframework" level="INFO"
		additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>
	<logger name="egovframework" level="DEBUG" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>
	<logger name="java.sql" level="ERROR" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>

	<!-- SQL문만을 로그로 남기며, PreparedStatement일 경우 관련된 argument 값으로 대체된 SQL문이 보여진다. -->
	<logger name="jdbc.sqlonly" level="WARN" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>

	<!-- SQL문과 해당 SQL을 실행시키는데 수행된 시간 정보(milliseconds)를 포함한다. -->
	<logger name="jdbc.sqltiming" level="DEBUG" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>

	<!-- ResultSet을 제외한 모든 JDBC 호출 정보를 로그로 남긴다. 많은 양의 로그가 생성되므로 특별히 JDBC 문제를 
		추적해야 할 필요가 있는 경우를 제외하고는 사용을 권장하지 않는다. -->
	<logger name="jdbc.audit" level="ERROR" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>

	<!-- ResultSet을 포함한 모든 JDBC 호출 정보를 로그로 남기므로 매우 방대한 양의 로그가 생성된다. -->
	<logger name="jdbc.resultset" level="ERROR" additivity="false">
		<appender-ref ref="SAMPLE" />
	</logger>

	<root level="INFO">
		<appender-ref ref="SAMPLE" /> <!-- Console에 로그를 출력하고자 할 때 사용 -->
	</root>
</configuration>

```

<H6> log4j2 의 성능이 좋고 간편해 보여서 log4j2도 적용해봤습니다~</H6>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration>
    <Appenders>
        <Console name="console" target="SYSTEM_OUT">
            <PatternLayout pattern="%d %5p [%c] [%t] %m%n" />
        </Console>
    </Appenders>
    <Loggers>
        <Logger name="java.sql" level="INFO" additivity="false">
            <AppenderRef ref="console" />
        </Logger>
        <Logger name="egovframework" level="DEBUG" additivity="false">
            <AppenderRef ref="console" />
        </Logger>
		  <!-- log SQL with timing information, post execution -->
	    <Logger name="jdbc.sqltiming" level="INFO" additivity="false">
	        <AppenderRef ref="console" />
	    </Logger>
	    <Logger name="org.springframework" level="INFO" additivity="false">
	        <AppenderRef ref="console" />
	    </Logger>
        <Root level="ERROR">
            <AppenderRef ref="console" />
        </Root>
    </Loggers>
</Configuration>
```

- 로그 적용 
![aaaaa](https://user-images.githubusercontent.com/52389219/120127323-10a27880-c1fa-11eb-859d-bb9ca2c56385.PNG)

시간 /  로그레벨 / 실행 / 실행하는 패키지 위치 (몇글자로 표현할지 설정가능)  /  로그내용


# Referece

● http://tcpschool.com/xml/xml_intro_basic

● https://developer.mozilla.org/ko/docs/Web/API/DOMParser

● https://humble.tistory.com/23

● [https://bcho.tistory.com/1312?category=431297](https://bcho.tistory.com/1312?category=431297) 
