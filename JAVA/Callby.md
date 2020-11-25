<h1> Call By Reference VS Call By Value
  <h3>Today I Learned </h3>

​    ● call by refernce & call by value의 개념

​    ●  call by refernce & call by value 차이점

​    ● call by refernce & call by value 예제 설명 


----------------------------------------------------------------------------------

## call by refernce & call by value의 차이점

● <h5>Call by reference VS Call by value<h5>

**Call by value** <Br>

**Call by value는 메서드 호출 시에 사용되는 인자의 메모리에 저장되어 있는 값(value)을 복사하여 보낸다.**<br>

**Call by reference**<br>

**Call by reference는 메서드 호출 시 사용되는 인자 값의 메모리에 저장되어있는 주소(Address)를 복사하여 보낸다.**



##  call by refernce 예시

● Call by reference는 메서드 호출 시에 사용되는 인자가, 값이 아닌 주소(Address)를 넘겨줌으로써, 주소를 참조(Reference)하여 데이터를 변경할 수 있습니다.

![image-20201124202229059](C:\Users\DoHyun\AppData\Roaming\Typora\typora-user-images\image-20201124202229059.png)

![img](https://t1.daumcdn.net/cfile/tistory/2463F137592FBADE0A)

● swap() 메서드 호출 시에 인자 a와 b는 메모리에 저장 된 주소 값을 복사하여 매개변수 x와 y의 메모리에 저장합니다. 결국 swap() 메서드는 10과 20이 저장 된 0x0001번지와 0x0005번지의 주소를 참조하여 연산하기 때문에, 연산 결과에 따라 원본 데이터가 변하게 됩니다.

## call by value 예시

![image-20201124202209606](C:\Users\DoHyun\AppData\Roaming\Typora\typora-user-images\image-20201124202209606.png)

● 이유 : swap() 메서드 호출 시에 사용한 인자 a,b와 swap() 메서드내의 매개변수 x,y는 서로 다르기 때문입니다.



![img](https://t1.daumcdn.net/cfile/tistory/26190835592FBA1032)

● swap() 메서드 호출 시에 사용한 인자 a와 b는 할당 된 메모리 주소가 아닌 메모리에 담겨져 있던 값만이 복사되어 swap() 메서드 내부의 매개변수 x와 y의 메모리 주소에 담겨지게 됩니다.

## Reference

●  https://re-build.tistory.com/3

● 자바의 정석 PART 1 ( 남궁성님)

● https://sleepyeyes.tistory.com/11

