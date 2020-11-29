

# [JAVA] 자바의 메모리 구조 

하나의 JAVA 파일은 크게 필드, 생성자, 메소드로 구성된다.<br>

● 자바(JVM)의 메모리 사용방식 <BR>

● static 메모리  <BR>

● stack 메모리 <BR>

● heap 메모리 <BR>

------

## JVM의 메모리 사용방식

**프로그램을 실행시킬때 CPU와의 작업을 위해서 저장장치에 있던 내용들이 메모리에 올라가기 시작한다.<br>**

![img](https://t1.daumcdn.net/cfile/tistory/9951443D5C6E85BE02)

메모리는 크게 4가지 영역으로 나눌수 있다. <br>

자세한 내용은 GC 에 대한 내용을 다룰때 [여기](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/%EA%B0%80%EB%B9%84%EC%A7%80%EC%BB%AC%EB%A0%89%EC%85%98(GC).md)에서 정리 하겠다. <BR>

## Static memory area

**필드, 생성자, 메소드로 구성된 JAVA파일 중 필드 부분에서 선언된 변수 (전역변수) 와 정적 멤버 변수(static이 붙은 자료형 ) 는 Static 영역에 데이터를 저장한다.<br>**

**static 영역의 데이터는 프로그램의 시작부터 종료가 될 때까지 메모리에 남아있게 된다. 즉, 프로그램이 종료될 때까지 어디서든 사용이 가능한 이유이기도 하다.<br>**

**전역변수를 무분별하게 많이 사용하면 메모리가 부족할 우려가 있어 필요한 변수만 사용할 필요가있다. <br>** 

## Stack memory area

**현재까지 작성하던 메소드 내에서 정의하는 기본 자료형 (int, double, byte, long, boolean)에 해당되는 지역변수의 데이터의 값이 저장되는 공간이 Stack 영역이다.<br>**

**해당 메소드가 호출될 때 메모리에 할당되고 종료되면 메모리가 해제 된다.**

![image-20201129175018381](C:\Users\DoHyun\Desktop\스크린샷샤샷\캡처2.JPG)

![img](http://postfiles1.naver.net/MjAxNzAzMTBfMjYy/MDAxNDg5MDcyMTUyOTM4.cRNCdoeIEEOG2ml0qNbOy9uCUm0Z7-vKvmQMPzYm6uQg.NQJdJCKtm9E-4R1vKQz2nUhMeUs92rw25YFJdeSwzSAg.PNG.heartflow89/image.png?type=w773)

위의 소스 코드처럼 a라는 변수는 main 메소드가 호출될 때 Stack 영역에 할당되고 종료시 해제된다.<br>

즉, Stack영역은  LIFO(Last In First Out)의 구조를 갖고 변수에 새로운 데이터가 할당되면 이전 데이터는 지워진다는 것을 알 수 있다.<Br>

또한 for문 내에 int i를 정의하였는데 for문이 종료된 다음 i를 출력하지 못하는 이유는 **지역변수이므로 for문의 종료와 함께 Stack 영역에서 해제**되었기 때문이다.<Br>

## Heap memory area

**클래스 변수  = new 클래스();<br>**

참조형의 데이터 타입을 갖는 객체(인스턴스), 배열 등은 Heap영역에 데이터가 저장된다. <br>

이때, 변수(객체, 객체변수, 참조변수)는 Stack영역의 공간에서 실제 데이터가 저장된 Heap영역의 참조값을 new 연산자를 통해 리턴받는다.<br>

**실제 데이터를 갖고있는 Heap 영역의 참조 값을 Stack 영역의 객체가 갖고있는 것이다 **

이렇게 리턴 받은 참조값을 갖고있는 객체를 통해서만 해당 인스턴드를 핸들링 할수 있다.

![](C:\Users\DoHyun\Desktop\스크린샷샤샷\캡처.JPG)



**a 변수는 데이터가 저장된 Heap 영역의 참조값을 리턴받아 갖고있다는 것을 확인 할 수 있다.<br>**

**문자열을 저장하는 String도 참조형이다. new 연산자를 이용해서 생성하면 데이터는 Heap 영역에 저장되고 str1과 str2는 참조 값을 리턴 받는다. 저장된 주소가 다르기 때문에 "=="으로 비교 시 "다른 주소값 입니다."가 출력되는 것이다. <br>**

![img](http://postfiles3.naver.net/MjAxNzAzMTBfODAg/MDAxNDg5MDc1ODI4NDMw.621h7wW2hby6d_AiV7K7qRhbK18Nk4HtoN1A-2nTbmMg.MmFAzdr9cMJGsI6KpyhqxV6kcdotO8lViClzBmEbND0g.PNG.heartflow89/image.png?type=w773)

<h6> **Heap에 저장된 데이터가 더 이상 사용이 불필요하다면 메모리 관리를 위해 JVM(자바 가상머신)에 의해 알아서 해제된다.** </h6>

**이러한 기능을 가비지컬렉션(GC, 쓰레기 수집) 이라고 한다. **

가비지컬렉션에 대한 내용은 [여기](https://github.com/JeonDoHyun/TIL/blob/main/JAVA/%EA%B0%80%EB%B9%84%EC%A7%80%EC%BB%AC%EB%A0%89%EC%85%98(GC).md) 정리 



<br>

# Referece

● https://siyoon210.tistory.com/124<br>

●http://blog.naver.com/PostView.nhn?blogId=heartflow89&logNo=220954420688 <br>

● 자바의 정석 ( 남궁성 지음 )<br>

