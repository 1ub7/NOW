# Section04. 연산자
## 17. 산술 연산자
**연산자란?** 계산을 수행하는 기호    

**연산자와 피연산자**  
```
3 + 4
a + b
```
- **연산자** : 연산 기호 ex) +, -  
- **피연산자** : 연산 대상 ex) 3, 4, a, b

**산술 연산자란?** 주로 숫자를 계산하는 데 사용  
ex) +, -, *, /, &

```
package bbb;

public class operator {
    static void main(String[] args) {
        int a = 5;
        int b = 2;

        int sum = a + b;
        System.out.println("a+b="+sum);

        int diff = a-b;
        System.out.println("a-b="+diff);

        int multi = a*b;
        System.out.println("a*b="+multi);

        int div=a/b;
        System.out.println("a/b="+div);

        int mod=a%b;
        System.out.println("a%b="+mod);
    }
}
```
실행 결과
```
a + b = 7
a - b = 3
a * b = 10
a / b = 2
a % b = 1
```
- 5 / 2의 결과는 소수점이 제거된 2로 계산
  - 자바에서 같은 int형끼리 계산하면 계산 결과도 같은 int형 사용
  - int -> 정수형이기 때문에 소수점 이하로 포함 할 수 없음
 
**0으로 나누기**  
10 / 0과 같은 숫자는 0으로 나눌 수 없음(수학적 허용 안됨)
```
Excption in thread "main" java.lang.ArithmeticException: /by zero
```
실행하면 예외 발생 (결과 출력 안되고 프로그램 종료됨)
## 18. 문자열 더하기
문자열에 + 연산자 사용하면 두 문자를 연결할 수 있음
```
package bbb;

public class p {
    static void main(String[] args) {
        String result1 = "hello " + "world";
        System.out.println(result1);

        String s1 = "string1";
        String s2 = "string2";
        String result2 = s1 + s2;
        System.out.println(result2);

        String result3 = "a + b = " + 10;
        System.out.println(result3);

        int num = 20;
        String str = "a + b = ";
        String result4 = str + num;
        System.out.println(result4);

    }
}
```
실행 결과
```
hello world
string1string2
a + b = 10
a + b = 20
```
<hr>

계산 과정
```
"a + b = "(String) + 10(int) //문자열과 숫자 더하기
"a + b = "(String) + "10"(int -> String) //숫자를 문자열로 변경
"a + b = " + "10" //문자열과 문자열 더하기
"a + b = 10" //결과
```

- 문자와 숫자를 더하면 숫자를 문자열로 변경한 다음 서로 더함
- 변수에 담겨 있어도 문자와 숫자를 더하면 문자가 됨

## 19. 연산자 우선순위
```
package bbb;

public class n {
    static void main(String[] args) {
        int sum1 = 1 + 2 * 3;
        int sum2 = (1+2) * 3;
        System.out.println("sum1 = " + sum1);
        System.out.println("sum2 = " + sum2);
    }
}
```
실행 결과
```
sum1 = 7
sum2 = 9
```
- 연산자 우선순위에 의해 곱셈이 먼저 계산된 것
- 우선순위 변경하려면 수학과 똑같이 괄호 사용 -> 먼저 계산됨
<hr>


```
package bbb;

public class n {
    static void main(String[] args) {
        int sum3 = 2 * 2 + 3 * 3;
        int sum4 = (2 * 2) + (3 * 3);
        System.out.println("sum3 = " + sum3);
        System.out.println("sum4 = " + sum4);
    }
}
```
실행 결과
```
sum3 = 13
sum4 = 13
```
 
코드 몇자 줄여서 모호하거나 복잡해 지는 것보다는 코드가 더 많더라도 명확하고 단순한 것이 더 유지보수 하기 좋음  
(연산자 우선순위가 애매하거나 조금이라도 복잡하다면 언제나 괄호 고려)
<hr> 

**연산자 우선순위 암기법**  
1. 괄호 ()
2. 단항 연산자 (++, --, !, ~ 등)
3. 산술 연산자 (*, /, % 등)
4. Shift 연산자 (<<, >>, >>>)
5. 비교 연산자 (<. <=, >, => 등)
6. 등식 연산자 (==, !=)
7. 비트 연산자 (&, ^, |)
8. 논리 연산자 (&&, ||)
9. 삼항 연산자 (? :)
10. 대입 연산자 (=, +=, -=, *= 등)
- 연산자 우선순위는 상식선에서 생각하고, 애매하면 괄호 사용
- 누구나 코드를 보고 쉽고 명확하게 이해할 수 있어야 함
- 개발에서 가장 중요한 것은 단순함과 명확함

## 20. 증감 연산자
```
package bbb;

public class n {
    static void main(String[] args) {
        int a = 0;
        a = a + 1;
        System.out.println("a = " + a);

        a = 1 + 1;
        System.out.println("a = " + a);

        ++a;
        System.out.println("a = " + a);
        ++a;
        System.out.println("a = " + a);
    }
}
```
실행 결과
```
a = 1
a = 2
a = 3
a = 4
```
<hr>

**전위, 후위 증감연산자**    
연산자의 위치에 따라 연산이 수행되는 시점이 달라짐

**전위 증감 연산자**    
증감 연산자가 변수 앞에 오는 경우    
(증감 연산이 먼저 수행된 후 나머지 연산 수행)

**후위 증감 연산자**    
증감연산자가 변수 뒤에 오는 경우    
(다른 연산이 먼저 수행된 후 증감 연산 수행)

참고 : 증감 연산자 단독 사용할 경우는 다른 연산이 없기 때문 -> 본인의 값만 증가          
(전위든 후위든 둘다 결과 같음)
## 21. 비교 연산자
두 값을 비교하는 데 사용(조건문과 함께 사용)

**비교 연산자 종류**    
- == : 동등성(equal to0
- != : 불일치(not equal to)
- ' > ': 크다(greater than)
- < : 작다(less than)
- ' >= ' : 크거나 같다(greater than or equal to)
- <= : 작거나 같다(less than or equal to)
참(True) 또는 거짓(False)이라는 결과 나옴
(참 또는 거짓은 boolean형)

**주의할 점** =와 ==는 다르다!!!!    
- = : 대입연산자, 변수에 값 대입
- == : 동등한지 확인하는 비교 연산자
불일치 연산자는 != 사용 (!는 반대라는 뜻)

**문자열 비교**    
문자 비교할 때는 .equals() 메서드 사용    
(==는 성공 여부 불확실)

## 22. 논리 연산자
boolean형인 true / false 를 비교하는데 사용

**논리 연산자 종류**    
- &&(그리고) : 두 피연산자가 모두 참이면 '참' 반환. 둘중 하나라도 거짓이면 '거짓' 반환
- ||(또는) : 두 피연산자 중 하나라도 참이면 '참' 반환, 둘다 거짓이면 '거짓' 반환
- !(부정) : 피연산자의 논리적 부정을 반환, 즉, 참이면 '거짓', 거짓이면 '참' 반환

```
package bbb;

public class Logical1 {
    static void main(String[] args) {
        System.out.println("&&: AND 연산");
        System.out.println(true && true);
        System.out.println(true && false);
        System.out.println(false && false);

        System.out.println("||: OR 연산");
        System.out.println(true || true);
        System.out.println(true || false);
        System.out.println(false || false);

        System.out.println("! 연산");
        System.out.println(!true);
        System.out.println(!false);

        System.out.println("변수 활용");
        boolean a = true;
        boolean b = false;
        System.out.println(a && b);
        System.out.println(a || b);
        System.out.println(!a);
        System.out.println(!b);
    }
}
```
- a && b는 false 반환 -> b가 거짓이여서
- a || b는 true 반환 -> a가 참
- !a와 !b는 각각의 논리적 부정 반환
<hr>

```
package bbb;

public class Logical2 {
    static void main(String[] args) {
        int a = 15;
        boolean result = a > 10 && a < 20;
        System.out.println("result = " + result);
    }
}
```
실행 결과
```
result = true
```
범위를 나타내는 경우 아래와 작성하면 코드 읽기 좀 좋음
boolean result = 10 < a && a < 20;

## 23. 대입 연산자
값을 변수에 할당하는 연산자

**축약(복합) 대입 연산자**    
산술 연산자와 대입 연산자를 한버에 축약해서 사용할 수 있음    
연산자 종류 : +=, -=, *=, /=, %=

## 24. 문제와 풀이
**문제 1 - int와 평균**    
나의 답
```
package bbb;

public class OperationEx1 {
    static void main(String[] args) {
        int num1=10;
        int num2=20;
        int num3=30;
        int sum=num1+num2+num3;
        int average=sum/3;
        System.out.println(sum);
        System.out.println(average);
    }
}
```
정답 여부 : O

**문제2 - double과 평균**    
나의 답
```
package bbb;

public class OperationEx2 {
    static void main(String[] args) {
        double val1 = 1.5;
        double val2 = 2.5;
        double val3 = 3.5;
        double sum = val1+val2+val3;
        double average = sum / 3;

        System.out.println(sum);
        System.out.println(average);
    }
}
```
정답 여부 : O

**문제3 - 합격 범위**    
나의 답
```
package bbb;

public class OperationEx3 {
    static void main(String[] args) {
        int score=88;
        boolean result =  score >= 80 && score <= 100;
        System.out.println(result);
    }
}
```
정답 여부 : O

## 25. 정리
**자주 사용하는 연산자**    
- 산술 연산자 : +, -, *, /, %
- 증가 및 감소 연산자 : ++, --
- 비교 연산자 : ==, !=, >, <, >=, <=
- 논리 연산자 : &&, ||, !
- 대입 연산자 : =, +=, -=, *=, /=, %=

**추가적인 연산자**    
- 삼항 연산자 : ? :
- instanceof 연산자 : 객체 타입 확인
- 그외 : new, [](배열 인덱스), .(객체 멤버 접근), ()(메소드 호출)

**비트 연산자는 실무에서 거의 사용할 일이 없음**    
- 비트 연산자 : &, |, ^, ~, <<, >>, >>> 
