------

# String 생성 방식의 차이점 new VS " " (리터럴)

● new VS " "  <BR>

● String 은 변하지 않는다. <BR>

● String 객체들의 연산이 이루어지면, 새로운 객체를 계속 만들어내기 때문에 메모리 관리 측면에서 상당히 비효율적이다.<br>

------

## ***\*💡\** 아래의 코드에서 몇개의 객체가 생성이 될까?**

```java
public class StringExample { 
  public static void main(String [] args) {
    String name1 = new String("nroo");
    String name2 = "nroo";
    String name3 = "nroo";
  } 
}
```

● String은 클래스니깐 참조타입이고 그러면 객체 3개 만들어져서 각각 참조하겠네 라는 생각이 가능하다<br>

● 결론부터 말하자면 2개의 객체가 만들어진다. 밑의 내용을 보면 이해가 될듯 

● 하지만 Java에서 String은 특별한 참조 자료형이다.<br>

![img](https://t1.daumcdn.net/cfile/tistory/2536E64F58B9640E06)

● 결론적으로 두 가지 방식 모두 String 객체를 생성한다는 사실은 같다. <br>

● new 생성자를 이용해서 인스턴스를 생성한 뒤, heap에서 메모리 관리가 이루어진다는 사실은 다른 참조형과 같다.  <br>

<h4>●  하지만 다른 참조형과는 다르게 변하지 않는다는 특징을 갖고있다.<br></h4>

● 위 그림에서 s3  = s3+ s3; 을 실행한다면 CatCat값을 가지는 String 객체를 생성하고 s3는 생성된 인스턴스를 참조하게 된다.<br>

<h5>● 새로운 객체를 계속 만들어 내기 때문에 메모리 관리 측면에서 상당히 비효율적이다.</br></h5>

```
● 이러한 이유로 만들어진 메모리 영역이 Heap 안에 있는 String Constant Pool이다. 
● 여기에는 기존에 만들어진 문자열 값이 저장되어 있다.
● s1과 s2 처럼 리터럴로 생성된 같은 값을 가지는 객체는 같은 레퍼런스를 가지게된다....!!!
```

● String은 클래스니깐 참조타입이고 그러면 객체 



<br>

# Referece

● https://ict-nroo.tistory.com/18

● http://www.journaldev.com/797/what-is-java-string-pool