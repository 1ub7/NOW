# Section03. 변수
## 09. 변수 시작
**패키지(package)란?** 디렉토리를 구분하는 폴더  
- 자바 파일이 위치하는 패키지와 선언 위치가 같아야 함
- 패키지 만들고, 해당 패키지에 들어가는 자바 파일 첫줄에 패키지 선언해줘야함  
  (ex - package variable;)

**변수란?**  
이름 그대로 변할 수 있는 값

```
package bbb;

public class Var {
    static void main(String[] args) {
        int a;
        a=20;
        System.out.println(a);
        System.out.println(a);
        System.out.println(a);
    }
}
```
실행 결과
```
20
20
20
```
<hr>

**변수 선언**   
```
int a
```
- 숫자 정수를 보관할 수 있는 이름이 a라는 데이터 저장소를 만듦
- a에 숫자 정수 보관 가능

**변수에 값 대입** 
```
a=10
```
- 자바에서 ' = '은 오른쪽에 있는 값을 왼쪽에 저장한다는 뜻  
  (수학에서 얘기하는 equals하고는 다름)
- 선언한 변수에 처음으로 값을 대입해서 저장하는 것을 초기화라고 함

**변수 값 읽기**
```
System.out.println(a)
```
- 변수 이름 적음 -> 변수에 저장되어 있는 값을 사용
- 반복해서 읽을 수 있음 / 변수의 값을 읽는다고 값이 없어지는 것은 아님
## 10. 변수 값 변경
```
package bbb;

public class Var1 {
    static void main(String[] args) {
        int a;
        a=10;
        System.out.println(a);
        a=50;
        System.out.println(a);

    }
}
```
실행 결과
```
10
50
```
<hr>

```
a=10;
System.out.println(a);
a=50;
System.out.printls(a);
```
- 변수의 값을 변경하면 변수에 들어있던 기존 값은 삭제
## 11. 변수 선언과 초기화
**변수 선언**
변수 선언 시, 컴퓨터의 메모리 공간을 확보해서 그곳에 데이터를 저장할 수 있음  
-> 변수의 이름을 통해서 해당 메모리 공간 접근 가능
  (하나 혹은 여러개씩 선언 가능)

**변수 초기화**  
변수 선언하고 선언한 변수에 처음으로 값을 저장하는 것
```
package bbb;

public class Var4 {
    static void main(String[] args) {
        int a;
        a=1;
        System.out.println(a);

        int b=2;
        System.out.println(b);
        
        int c=3, d=4;
        System.out.println(c);
        System.out.println(d);
    }
}
```
실행 결과
```
1
2
3
4
```
- 변수의 선언과 초기화를 각각 따로 할 수 있음
- 변수를 선언하면서 동시에 초기화 할 수 있음
- 여러 변수를 선언하면서 초기화도 동시에 진행할 수 있음

**초기화 안하면 어떻게 됨?**
```
java: variable a might not have been initialized
```
컴파일 에러 발생!!!!!!  

**오류 왜 발생 함?**  
컴퓨터에서 메모리는 여러 시스템이 함께 사용하는 공간임(어떠한 값들이 계속 저장됨)  
초기화 하지 않으면 이상한 값이 출력될 수 있음. 이런 문제를 예방하기 위해 자바는 변수를 초기화 하도록 강제함
## 12. 변수 타입1
변수는 데이터를 다루는 종류에 따라 다양한 형식이 존재함
```
package bbb;

public class Var7 {
    static void main(String[] args) {
        int a=100; //정수
        double b=10.5; //실수
        boolean c=true; // true, false 입력 가능
        char d='A'; //문자 하나
        String e="Hello Java"; //문자열, 문자열을 다루기 위한 특별한 타잉ㅂ

        System.out.println(a);
        System.out.println(b);
        System.out.println(c);
        System.out.println(d);
        System.out.println(e);
    }
}
```
실행 결과
```
100
10.5
true
A
Hello Java
```
<hr>
변수는 데이터를 다루는 종류에 따라 다양한 형식 존재 = type(형)  

**변수 타입의 예시**  
int : 정수  
double : 실수  
boolean : true, false  
char : 문자 하나  
string : 문자열  
  (첫 글자가 대문자로 시작하는 특별한 타입)

**자신의 타입에 맞는 데이터 사용**
각 변수는 지정한 타입에 맞는 값을 사용해야 함  
- int a="백원" : 정수 타입에 문자열(X)
- int a="100" : 정수 타입에 문자열(X)
- int a= 100 : 정수 타입에 정수(O)

**리터럴**  
코드에서 개발자가 직접 적은 고정된 값을 프로그래밍 용어
(리터럴 자체 안 변함)

## 13. 변수 타입2
```
package bbb;

public class Var8 {
    static void main(String[] args) {
        //정수
        byte b= 127; //-128 ~ 127
        short s= 32767; // -32,768 ~ 32,767
        int i= 2147483647; //-2,147,483,648 ~ 2,147,483,647

        // -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807
        long l= 9223372036854775807L;

        //실수
        float f= 10.0f;
        double d= 10.0;
    }
}
```
실행 결과
```
127
32767
2147483647
9223372036854775807L
10.0
10.0
```

**변수와 메모리 공간 크기**  
- 정수형
  - byte : -127 ~ 127 (1byte)
  - short : -32,768 ~ 32,767 (2byte)
  - int : -2,147,483,648 ~ 2,147,483,647 (4byte)
  - long : -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807 (8byte)
- 실수형
  - float : 대략 -3.4E38 ~ -3.4E38 (7자리 정밀도 / 4byte)
  - double : 대략 -1.7E308 ~ -1.7E308 (15자리 정밀도 / 8byte)
- 기타
  - boolean : ture, false(1byte)
  - char : 문자 하나(1byte)
  - String : 문자열 표현 / 메모리 사용량은 문자 길이에 따라 동적으로 달라짐

**리터럴 타입 지정**  
-  정수 리터럴
  - int 기본 사용
  - 만약 숫자 20억이 넘어가면 L을 붙어서 long 사용  
    (대문자 소문자 모두 가능)
- 실수 리터럴
  - double 기본 사용
  - 만약 float 사용 시 f 붙여서 형식 지정

**변수 타입 정리**  
아래 타입들은 실무에서 거의 사용하지 않음  
- byte : 표현 길이 작음
  - 타입을 직접 선언하고 여기에 숫자 값을 대입해서 계산하는 일은 거의 없음
  - 대신 파일을 바이트 단위로 다루기 때문에 파일 전송, 파일 복사 등에 주로 사용됨
- short : 표현 길이가 너무 작음
- float : 표현 길이와 정밀도가 낮음
- char : 문자 하나를 표현하는 일은 거의 없음

**자주 사용하는 타입**  
실무에서 자주 사용하는 타입
- 정수 - int, long : 기본은 int / 만약 20억이 넘을 것 같으면 long
  - 파일을 다룰 때는 byte 사용
- 실수 - double : 실수는 무조건 double
- 불린형 - boolean : ture, false 참 거짓 표현 (조건문에서 자주 사용)
- 문자열 - String : 문자를 다룰 때는 문자 하나든 문자열이든 모두 String 사용하는 것이 편리

**참고**  
메모리 용량은 매우 저렴  
메모리 용량을 약간 절약 < 개발 속도나 효율에 초점 맞추는 것이 더 효과적

## 14. 변수 명명 규칙
변수의 이름을 짓는데는 규칙과 관례가 있음  
**규칙 필수!!!!!!!** / 규칙 안 지키면 컴파일 오류 발생  
관례는 필수 아니지만 전세계 개발자가 해당 관례를 따르기 때문에 **사실상 규칙**

**규칙**
- 변수 이름은 숫자로 시작할 수 없음
  - 숫자를 이름에 포함하는 것은 가능
- 이름에는 공백 들어갈 수 없음
- 자바의 예약어를 변수 이름으로  사용할 수 없음
- 변수 이름에는 영문자, 숫자, 달러 기호 또는 밑줄만 사용 가능
  
**관례**
-  소문자로 시작하는 낙타 표기법
  - 변수 이름은 소문자로 시작하는 게 일반적
    -> 여러 단어로 이루어진 변수 이름의 경우 각 단어를 대문자로 시작

**낙타표기법**  
프로그래밍에서 변수, 함수, 클래스 등의 이름을 지을 때 많이 사용하는 표기법 중 하나  
(각 단어의 첫 글자가 대문자로 시작하고 이 대문자들이 낙타의 동봉처럼 보이는 것에서 유래됨)

**자바 언어의 관례 한번에 정리**  
클래스는 대문자로 시작, 나머지는 소문자로 시작  
- 자바에서 클래스 이름의 첫 글자는 대문자로 시작 / 나머지는 모두 첫 글자를 소문자로 시작
- ex) 클래스는 첫 글자 대문자, 나머지는 모두 첫 글자 소문자로 시작
  - 클래스 : Person, OrderDetail
  - 변수를 포함한 나머지 : firstName, userAccount
- 여기에 예외는 딱 2개
  - 상수는 모두 대문자를 사용 / 언더바로 구분 : USER_LIMIT
  - 패키지는 모두 소문자를 사용 : org.spring.boot

변수 이름은 의미있고 그 용도를 명확하게 설명해야함  
- a, b: 이런 변수는 용도를 설명하지 않음
- studentCount, maxScore : 용도를 명확하게 설명

## 15. 문제와 풀이
**문제1**
다음 코드에 반복해서 나오는 숫자 4,3을 다른 숫자로 한번에 변경할 수 있도록  
다음을 변수 num1,num2를 사용하도록 변경해보세요

```
package bbb;

public class Var9 {
    static void main(String[] args) {
        int num1=4;
        int num2=3;
        System.out.println(num1 + num2);
        System.out.println(num1 - num2);
        System.out.println(num1 * num2);
    }
}
```
실행 결과
```
7
1
12
```
**문제2**  
- 클래스 이름 : VarEx2
- 변수 num1을 선언, 이에 10 할당
- 변수 num2을 선언, 이에 20 할당
- 두 변수의 합을 구하고 그 결과를 새로운 변수 sum 저장
- sum 변수의 값을 출력

```
package bbb;

public class VarEx2 {
    static void main(String[] args) {
        int num1=10;
        int num2=20;
        int sum=num1+num2;
        System.out.println(sum);
    }
}
```
실행 결과
```
30
```
**문제3**  
- 클래스 이름 : VarEx3
- long 타입 변수 선언하고 그 변수를 백억으로 초기화한 후 출력
- boolean 타입의 변수를 선언하고 true로 초기화한 후 출력
```
package bbb;

public class VarEx3 {
    static void main(String[] args) {
        long longVer = 10000000000L;
        System.out.println(longVer);

        boolean booleanVar = true;
        System.out.println(booleanVar);
    }
}
```
실행 결과
```
100000000000
true
```
## 16. 정리
정리!!!!!!!
