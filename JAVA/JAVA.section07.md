# Section07. 스코프, 형변환
## 45. 스코프1 - 지역 변수와 스코프
**지역 변수란?** 특정 코드 블록(여기선 {}를 뜻함)   
자신이 선언된 코드 블록 안에서만 생존하고, 자신이 선언된 코드 블록을 벗어나면 제거됨    

```
package Scope;

public class Scope1 {
    static void main(String[] args) {
        int m=10; // m 생존 시작
        if (true) { // x 생존 시작
            int x = 20;
            System.out.println("if m = "+m);
            System.out.println("if m = "+x);
        } // x 생존 종료
        System.out.println("main m = " + m);
    } // m 생존 종료
}
```
- int m은 if{} 블록 내부에서도 외부 블록에서 선언된 m에 접근할 수 있음
- int x은 if{} 블록 안에서만 선언되었기 때문에 외부 블록에서 선언되어도 접근 못 함

---
```
package Scope;

public class Scope2 {
    static void main(String[] args) {
        int m = 10;
        for (int i = 0; i<2; i++) {
            System.out.println("for m = " + m);
            System.out.println("for i = " + i);
        }
        System.out.println("main m = " + m);
    }
}
```
for문의 경우 for문 안에서 초기식에 직접 변수를 선언할 수 있음. 그리고 이렇게 선언한 변수는 for 문 코드 블록 안에서만 사용할 수 있음

---
결론     
- 지역 변수는 본인의 코드 블록 안에서만 생존      
- 자신의 코드 블록 안에서는 얼마든지 접근할 수 있음   
- 하지만 자신의 코드 블록을 벗어나면 제거되기 때문에 접근할 수 없음

## 46. 스코프2 - 스코프 존재 이유
```
package Scope;

public class Scope3_1 {
    static void main(String[] args) {
        int m = 10;
        int temp = 0;
        if (m>0) {
            temp = m * 2;
            System.out.println("temp = " + temp);
        }
        System.out.println("m = " + m);
    }
}
```
위와 같은 코드 방식을 쓰면 아래와 같은 문제점들이 발생함    
- 비효율적인 메모리 사용 : temp는 if코드 블록에서만 필요하지만, main()코드 블록이 종료될 때 까지 메모리에 유지되기 때문
- 코드 복잡성 증가 : 스코프가 불필요하게 넓기 때문

```
package Scope;

public class Scope3_2 {
    static void main(String[] args) {
        int m = 10;
        if (m>0) {
            int temp = m * 2;
            System.out.println("temp = " + temp);
        }
        System.out.println("m = " + m);
    }
}
```
int temp 줄을 if문 안으로 넣는 방법이 있음  

---
정리
- 변수는 꼭 필요한 범위로 한정해서 사용하는 것이 좋음. 변수의 스코프는 꼭 필요한 곳으로 한정해서 사용.
- 좋은 프로그램은 무한한 자유가 있는 프로그램이 아니라 적절한 제약이 있는 프로그램임

## 47. 형변환1 - 자동 형변환
**형변환**      
- 작은 범위에서 큰 범위로는 당연히 값을 넣을 수 있음
- 큰 범위에서 작은 범위는 다음과 같은 문제가 발생할 수 있음

**작은 범위에서 큰 범위로 대입은 허용**     
자바에서 숫자를 표현할 수 있는 범위?    
int < long < double     

```
package Casting1;

public class Casting1 {
    static void main(String[] args) {
        int intValue = 10;
        long longValue;
        double doubleValue;

        longValue = intValue;
        System.out.println("longValue = " + longValue);

        doubleValue = intValue;
        System.out.println("doubleValue = " + doubleValue);

        doubleValue = 20L;
        System.out.println("doubleValue2 = " + doubleValue);
    }
}
```
실행 결과
```
longValue = 10
doubleValue = 10.0
doubleValue2 = 20.0
```
작은 범위에서 큰 범위로의 대입은 자바 언어에서 허용함. 그 반대는 안됨   

---
**자동 형변환 (혹은 묵시적 형변환)**     
작은 범위 숫자 타입에서 큰 범위 숫자 타입으로의 대입은 개발자가 직접 형변환을 하지 않아도 됨.

## 48. 형변환2 - 명시적 형변환
```
package Casting1;

public class Casting2 {
    static void main(String[] args) {
        double doubleValue = 1.5;
        int intValue = 0;
        intValue = (int) doubleValue; // 이게 명시적 형변환
        System.out.println(intValue);
    }
}
```
int형은 double형보다 숫자의 표현 범위가 작음. 그리고 실수를 표현할 수도 없음.   

---
**캐스팅 용어**     
cast는 금속이나 다른 물질을 녹여서 특정한 형태나 모양으로 만드는 과정을 의미    

**명시적 형변환 과정**      
```
intValue = (int) doubleValue;
intValue = (int) 1.5;
intValue = 1;
```
참고 : 변수의 값은 대입연산자(=)를 사용해서 직접 대입할 때만 변경됨  

```
package Casting1;

public class Casting3 {
    static void main(String[] args) {
        long maxIntValue = 214748647; // int 최고값
        long maxIntOver = 2147483648L; // int 최고값 + 1(초과)
        int intValue = 0;

        intValue = (int) maxIntValue; // 형변환
        System.out.println("maxIntValue casting= " + intValue);

        intValue = (int) maxIntOver;
        System.out.println("maxIntOver casting= " + intValue);
    }
}
```
출력 결과   
```
maxIntValue casting=2147483647
maxIntOver casting=-2147483648
```

---
**정상 범위**   
int로 표현할 수 있는 범위에 포함되기 때문에 long에서 int로 형변환을 해도 아무런 문제가 없음     

**초과 범위**   
예시를 들자면? int로 표현할 수 있는 가장 큰 숫자인 2147483647보다 1큰 숫자를 입력했다 치자. 이 숫자는 리터럴은 int 범위를 넘어가기 때문에 마지막에 L을 붙여서 long형을 사용해야 함.     
이 경우 int로 표현할 수 있는 범위를 넘기 때문에 다음과 같이 long에서 int로 형변환 하면 문제가 발생함    

## 49. 계산과 형변환
```
package Casting;

public class Casting4 {
    static void main(String[] args) {
        int div1 = 3/2;
        System.out.println("div1 = " + div1);
        
        double div2 = 3/2;
        System.out.println("div2 = " + div2);
        
        double div3 = 3.0/2;
        System.out.println("div3 = " + div3);
        
        double div4 = (double) 3/2;
        System.out.println("div4 = " + div4);
        
        int a=3;
        int b=2;
        double result = (double) a/b;
        System.out.println("result = " + result);
    }
}
```
출력 결과
```
div1 = 1
div2 = 1.0
div3 = 1.5
div4 = 1.5
result = 1.5
```
자바에서 계산은 다음 2가지가 있음   
- 같은 타입끼리의 게산은 같은 타입의 결과를 냄  
    - int+int는 int, double+double은 double의 결과가 나옴
- 서로 다른 타입의 계산은 큰 범위로 자동 형변환이 일어남
    - int+long은 long+long
    - int+double은 double+double

## 50. 정리
**형변환**      
int < long < double     
- 작은 범위에서 큰 범위로는 대입할 수 있음  
    - 이것을 묵시적 형변환 또는 자동 형변환이라 함
- 큰 범위에서 작은 범위의 대입은 다음과 같은 문제가 발생할 수 있음. 이때는 명시적 형변환을 사용해야 함.
    - 소수점 버림
    - 오버플로우
- 연산과 형변환
    - 같은 타입은 같은 결과를 냄
    - 서로 다른 타입의 계산은 큰 범위로 자동 형변환이 일어남