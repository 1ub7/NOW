# Section10. 메서드
## 71. 메서드 시작
**함수(function)**      
ex) add(a, b)=a+b이면   
이름 : add / 받는 값 : a,b   / 연산 : a+b

- 함수에 값을 입력하면, 함수가 가진 연산을 처리한 다음 결과를 출력
- 같은 함수를 다른 입력 값으로 여러번 호출할 수 있음 (재사용 가능)

## 72. 메서드 사용
자바에선 함수가 메서드(Method)임

아래는 메서드 정의 예시
```
public static int add(int a, int b) {
        System.out.println(a+"+"+b+" 연산 수행");
        int sum = a + b;
        return sum;
    }
```
**메서드 선언**     
```
public static int add(int a, int b)
```
메서드 이름, 반환 타입, 파라미터 목록을 포함    
메서드 선언 정보를 통해 다른 곳에서 해당 메서드를 호출할 수 있음

- public static
    - public : 다른 클래스에서 호출할 수 있는 메서드라는 뜻
    - static : 객체를 생성하지 않고 호출할 수 있는 정적 메서드라는 뜻
- int add(int a, int b)
    - int : 반환 타입 정의
    - add : 메서드의 이름을 부여
    - (int a, int b) : 메서드를 호출할 때 전달하는 입력 값을 정의

**메서드 본문**     
```
{
        System.out.println(a+"+"+b+" 연산 수행");
        int sum = a + b;
        return sum;
}
```
- 메서드가 수행해야 하는 코드 블록
- 메서드의 실행 결과를 반환하려면 return문을 사용
    - return sum : sum 변수에 들어있는 값을 반환

**메서드 호출**     
메서드는 계산을 끝내고 결과(return 값)를 반환   
메서드 호출이 끝나면 해당 메서드가 반환한 결과 값으로 치환됨

---
**인수** : 메서드 내부로 들어가는 값    
**매개변수** : 메서드를 정의할 때 선언한 변수   
메서드를 호출할 때 인수를 넘기면, 그 인수가 매개변수에 대입됨

## 73. 메서드 정의
- 매개변수가 없는 경우
    - 선언 : 매개변수를 비워두고 정의
    - 호출 : 인수를 비워두고 호출
- 반환 타입이 없는 경우
    - 선언 : 반환 타입을 void로 정의
    - 호출 : 메서드만 호출하고 반환 값을 받지 않으면 됨

**void와 return 생략**      
모든 메서드는 항상 return을 호출해야함      
**그런데** 반환 타입이 void인 경우에는 생략 가능    
자바 컴파일러가 반환 타입이 없는 경우에는 return을 마지막줄에 넣음

## 74. 반환 타입
반환 타입이 있는 메서드는 반드시 return을 사용해서 값을 반환해야 함 

**반환 값 무시**    
반환 타입이 있는 메서드를 호출했는데 만약 반환 값이 필요없다면 사용하지 않아도 됨   

## 75. 메서드 호출과 값 전달1
**자바는 항상 변수의 값을 복사해서 대입한다**      

```
package method;

public class MethodValue1 {
    public static void main(String[] args) {
        int num1 = 5;
        System.out.println("1. changeNumber 호출 전, num1: "+num1);
        changeNumber(num1);
        System.out.println("4. changeNumber 호출 후, num2: "+num1);
    }
    public static void changeNumber(int num2) {
        System.out.println("2. changeNumber 변경 전, num2: "+num2);
        num2 = num2 * 2;
        System.out.println("3. changeNumber 변경 후, num2: "+num2);
    }
}
```

## 76. 메서드 호출과 값 전달2
**호출자의 변수 이름과 매개변수의 이름을 같게 하면?**       

```
package method;

public class MethodValue2 {
    public static void main(String[] args) {
        int number = 5;
        System.out.println("1. changeNumber 호출 전, number: "+number);
        changeNumber(number);
        System.out.println("4. changeNumber 호출 후, number: "+number);
    }
    public static void changeNumber(int number) {
        System.out.println("2. changeNumber 변경 전, number: "+number);
        number = number * 2;
        System.out.println("3. changeNumber 변경 후, number: "+number);
    }
}
```
main()도 사실은 메서드임. 각각의 메서드 안에서 사용하는 변수는 서로 완전히 분리된 다른 변수

---
```
package method;

public class MethodValue3 {
    public static void main(String[] args) {
        int num1 = 5;
        System.out.println("changeNumber 호출 전, number: "+num1);
        num1 = changeNumber(num1);
        System.out.println("changeNumber 호출 후, number: "+num1);
    }
    public static int changeNumber(int num2) {
        num2 = num2 * 2;
        return num2;
    }
}
```
**자바는 항상 변수의 값을 복사해서 대입함**

## 77. 메서드와 형변환
**명시적 형변환**
```
package method;

public class MethodCasting1 {
    public static void main(String[] args) {
        double number = 1.5;
        printNumber((int)number);
    }
    public static void printNumber(int n) {
        System.out.println("숫자: "+n);
    }
}
```

**자동 형변환**     
int < long < double     
메서드를 호출할 때 매개변수에 값을 전달하는 것도 결국 변수에 값을 대입하는 것   
```
package method;

public class MethodCasting2 {
    public static void main(String[] args) {
        int number = 100;
        printNumber(number);
    }
    public static void printNumber(double n) {
        System.out.println("숫자: "+n);
    }
}
```

메서드를 호출할 때는 전달하는 인수의 타입과 매개변수의 타입이 맞아야 함.    
근데 타입이 달라도 자동 형변환이 가능한 경우에는 호출할 수 있음.

## 78. 메서드 오버로딩
**오버로딩**    
이름이 같고 매개변수가 다른 메서드를 여러개 정의하는 것     

**오버로딩 규칙**       
메서드의 이름이 같아도 매개변수의 타입 및 순서가 다르면 오버로딩을 할 수 있음. (반환 타입은 인정하지 않음)

**메서드 시그니처**     
메서드 시그니처 = 메서드 이름 + 매개변수 타입(순서)     
(자바에서 메서드를 구분할 수 있는 고유한 식별자나 서명)     

---
예제1
```
package method;

public class Overloading1 {
    public static void main(String[] args) {
        System.out.println("1: "+add(1,2));
        System.out.println("2: "+add(1,2,3));

    }
    public static int add(int a, int b) {
        System.out.println("1번 호출");
        return a + b;
    }
    public static int add(int a, int b, int c) {
        System.out.println("2번 호출");
        return a + b + c;
    }
}
```
실행 결과
```
1번 호출
1: 3
2번 호출
2: 6
```

예제2
```
package method;

public class Overloading2 {
    public static void main(String[] args) {
        myMethod(1, 1.2);
        myMethod(1.2,1);
    }
    public static void myMethod(int a, double b) {
        System.out.println("int a, double b");
    }
    public static void myMethod(double a, int b) {
        System.out.println("double a, int b");
    }
}
```
실행 결과
```
int a, double b
double a, int b
```

예제3
```
package method;

public class Overloading3 {
    public static void main(String[] args) {
        System.out.println("1: "+add(1,2));
        System.out.println("2: "+add(1.2,1.5));
    }
    public static int add(int a, int b) {
        System.out.println("1번 호출");
        return a + b;
    }
    public static double add(double a, double b) {
        System.out.println("2번 호출");
        return a + b;
    }
}
```
실행 결과
```
1번 호출
1: 3
2번 호출
2: 2.7
```

## 79. 문제와 풀이1
**Q1**      
리펙토링
```
package method.ex;

public class MethodEx1Ref {
    public static void main(String[] args) {
        System.out.println("평균값: "+average(1,2,3));
        System.out.println("평균값: "+average(15,25,35));
    }
    public static double average(int a, int b, int c) {
        int sum = a+b+c;
        return sum/3.0;
    }
}
```

**Q2**      
특정 숫자만큼 같은 메시지를 반복 출력하는 리펙토링
```
package method.ex;

public class MethodEx2Ref {
    public static void main(String[] args) {
        printMessage("Hello world!", 3);
        printMessage("java", 5);
        printMessage("hi", 7);
    }
    public static void printMessage(String message, int times) {
        for (int i = 0; i < times; i++) {
            System.out.println(message);
        }
    }
}
```

**Q3**      
입금, 출금을 나타내는 코드
```
package method.ex;

public class MethodEx3 {
    public static void main(String[] args) {
        int balance = 10000;

        // 입금 1000
        balance = deposit(balance, 1000);
        // 출금 2000
        balance = withdraw(balance, 2000);
        System.out.println("최종 잔액: "+balance+"원");
    }
    public static int deposit(int balance, int amount) {
        balance += amount;
        System.out.println(amount+"원을 입금하였습니다. 현재 잔액: "+balance+"원");
        return balance;
    }
    public static int withdraw(int balance, int amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println(amount+"원을 출금하였습니다. 현재 잔액: "+balance+"원");
        } else {
            System.out.println(amount+"원을 출금하려 했으나 잔액이 부족합니다.");
        }
        return balance;
    }
}
```

## 80. 문제와 풀이2
**Q1**      
은행 계좌 입출금
```
package method.ex;

import java.util.Scanner;

public class MethodEx4 {
    public static void main(String[] args) {
        int balance = 0;
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("-----------------------------------");
            System.out.println("1.입금 | 2.출금 | 3.잔액 학인 | 4.종료");
            System.out.println("-----------------------------------");
            System.out.print("선택: ");

            int choice = scanner.nextInt();
            int amount;

            switch (choice) {
                case 1:
                    System.out.print("입금액을 입력하세요: ");
                    amount = scanner.nextInt();
                    deposit(balance, amount);
                    break;
                case 2:
                    System.out.print("출금액을 입력하세요: ");
                    amount = scanner.nextInt();
                    balance = withdraw(balance, amount);
                case 3:
                    System.out.println("현재 잔액: " + balance + "원");
                    break;
                case 4:
                    System.out.println("시스템을 종료합니다.");
                    return;
                default:
                    System.out.println("올바른 선택이 아닙니다. 다시 선택해주세요.");
            }
        }
    }
        public static int deposit(int balance, int amount) {
            balance += amount;
            System.out.println(amount+"원을 입금하였습니다. 현재 잔액: "+balance+"원");
            return balance;
    }
        public static int withdraw(int balance, int amount) {
            if (balance >= amount) {
                balance -= amount;
                System.out.println(amount+"원을 출금하였습니다. 현재 잔액: "+balance+"원");
            } else {
                System.out.println(amount+"원을 출금하려 했으나 잔액이 부족합니다.");
            }
            return balance;
    }
}

```

## 81. 정리
**변수명 VS 메서드명**      
변수명 : 일반적으로 명사 사용   
메서드명 : 무언가 동작하는데 사용하기 때문에 일반적으로 동사 사용

**메서드 사용의 장점**      
- 필요할 때마다 그 기능을 다시 작성할 필요 없이 해당 메서드를 호출함으로써(캡슐화) 코드 재사용할 수 있음
- 코드의 가독성이 좋음
- 모듈성 있음
- 오류 발생 시 해당 메서드만 수정하면 전체 코드 베이스에 영향을 주지 않고 변경 사항을 적용할 수 있음 (코드 유지 관리 쉬움)
- 재사용성과 확장성이 좋음
- 프로그램의 다른 부분에서는 복잡한 내부 작업에 대해 알 필요 없이 메서드를 사용할 수 있음(추상적)
