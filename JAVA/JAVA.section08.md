# Section08. 훈련
## 51. Scanner 학습
```
package Scanner;
 
import java.util.Scanner;

public class Scanner1 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("문자열을 입력하세요: ");
        String str = scanner.nextLine();
        System.out.println("입력한 문자열: "+str);

        System.out.print("정수를 입력하세요: ");
        int intValue = scanner.nextInt();
        System.out.println("입력한 정수: "+intValue);

        System.out.print("실수를 입력하세요: ");
        double doubleValue = scanner.nextDouble();
        System.out.println("입력한 실수: "+doubleValue);
    }
}
```
Scanner scanner = new Scanner(System.in)   
- Scanner는 System.in을 사용해서 사용자의 입력을 편리하게 받도록 도와줌     
- Scanner scanner 코드는 scanner 변수를 선언하는 것

scanner.nextLine()  
- 엔터(\n)를 입력할 때까지 문자를 가져옴    

---
**주의할 점** - 타입이 다르면 오류가 발생함   

**print() VS println()**    
print()는 출력하고 다음 라인으로 넘어가지 않음      
println()은 출력하고 다음 라인으로 바로 넘어감

## 52. Scanner - 기본 예제
```
package Scanner;

import java.util.Scanner;

public class Scanner2 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("첫 번째 숫자를 입력하세요: ");
        int num1 = scanner.nextInt();
        System.out.print("두 번째 숫자를 입력하세요: ");
        int num2 = scanner.nextInt();
        int sum = num1 + num2;
        System.out.println("두 숫자의 합: "+sum);
    }
}
```
실행 결과 예시
```
첫 번째 숫자를 입력하세요: 10
두 번째 숫자를 입력하세요: 20
두 숫자의 합: 30
```
---
```
package Scanner;

import java.util.Scanner;

public class Scanner3 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("첫 번째 숫자를 입력하세요: ");
        int num1 = scanner.nextInt();
        System.out.print("두 번째 숫자를 입력하세요: ");
        int num2 = scanner.nextInt();

        if (num1 > num2) {
            System.out.println("더 큰 숫자: "+num1);
        } else if (num1 < num2) {
            System.out.println("더 큰 숫자: "+num2);
        } else {
            System.out.println("두 숫자가 같습니다.");
        }
    }
}
```
실행 결과 예시
```
첫 번째 숫자를 입력하세요: 10
두 번째 숫자를 입력하세요: 20
더 큰 숫자: 20
```

## 53. Scanner - 반복 예제
```
package Scanner;

import java.util.Scanner;

public class ScannerWhile1 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.print("문자열 입력: ");
            String str = scanner.nextLine();
            if (str.equals("exit")) {
                System.out.println("프로그램을 종료합니다.");
                break;
            }
            System.out.println("입력한 문자열: "+str);
        }
    }
}
```
실행 결과 예시
```
문자열 입력: now
입력한 문자열: now
문자열 입력: exit
프로그램을 종료합니다.
```
---
```
package Scanner;

import java.util.Scanner;

public class ScannerWhile2 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true){
            System.out.print("첫 번째 숫자 입력: ");
            int num1 = scanner.nextInt();
            System.out.print("두 번째 숫자 입력: ");
            int num2 = scanner.nextInt();
            if (num1==0 & num2==0) {
                System.out.println("모두 0을 입력하셔서 종료합니다.");
                break;
            }
            System.out.println("더한거: "+(num1+num2));
        }
    }
}
```
실행 결과 예시
```
첫 번째 숫자 입력: 10
두 번째 숫자 입력: 29
더한거: 39
첫 번째 숫자 입력: 0
두 번째 숫자 입력: 0
모두 0을 입력하셔서 종료합니다.
```
---
```
package Scanner;

import java.util.Scanner;

public class ScannerWhile3 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        int sum = 0;
        while (true) {
            int num = input.nextInt();
            if (num == 0) {
                System.out.println("프로그램 종료");
                System.out.println("모든 정수의 합:"+sum);
                break;
            }
            sum += num;
        }
        System.out.println("입력한 모든 정수의 합: "+sum);
    }
}

```
실행 결과 예시
```
10
30
20
40
0
프로그램 종료
모든 정수의 합:100
입력한 모든 정수의 합: 100
```

## 54. 문제와 풀이1
**Q1**
```
package Scanner.scanner;

import java.util.Scanner;

public class ex1 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("당신의 이름을 입력하세요: ");
        String name = scanner.nextLine();

        System.out.print("당신의 나이를 입력하세요: ");
        int age = scanner.nextInt();

        System.out.println("당신의 이름은 "+name+"이고, 나이는 "+age+"살입니다.");
    }
}
```
실행 예시
```
당신의 이름을 입력하세요: 박종수
당신의 나이를 입력하세요: 27
당신의 이름은 박종수이고, 나이는 27살입니다.
```
---
**Q2**
```
package Scanner.scanner;

import java.util.Scanner;

public class ex2 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("정수 한개 입력: ");
        int num = scanner.nextInt();
        if (num%2==0) {
            System.out.println("짝수");
        } else {
            System.out.println("홀수");
        }
    }
}
```
실행 예시
```
정수 한개 입력: 5
홀수
```
---
**Q3**
```
package Scanner.scanner;

import java.util.Scanner;

public class ex3 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("음식 이름: ");
        String name = input.nextLine();
        System.out.print("음식 가격: ");
        int price = input.nextInt();
        System.out.print("음식 수량: ");
        int count = input.nextInt();

        System.out.println(name +count+"개 주문");
        System.out.println("총 가격: "+(price*count));
    }
}
```
실행 예시
```
음식 이름: 젤리
음식 가격: 1000
음식 수량: 5
젤리5개 주문
총 가격: 5000
```
---
**Q4**
```
package Scanner.scanner;

import java.util.Scanner;

public class ex4 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        System.out.print("구구단의 단 수: ");
        int num = input.nextInt();

        System.out.println(num+"단의 구구단: ");
        for (int i=1; i<=9; i++) {
            System.out.println(num+" x "+i+" = "+ num* i);
        }
    }
}
```
실행 예시
```
구구단의 단 수: 6
6단의 구구단: 
6 x 1 = 6
6 x 2 = 12
6 x 3 = 18
6 x 4 = 24
6 x 5 = 30
6 x 6 = 36
6 x 7 = 42
6 x 8 = 48
6 x 9 = 54
```

## 55. 문제와 풀이2
**Q1**      
변수 값 교환
```
package Scanner.scanner2;

public class ex1 {
    static void main(String[] args) {
        int a = 10;
        int b = 20;
        int temp;

        temp = a;
        a = b;
        b = temp;
        System.out.println("a = "+ a);
        System.out.println("b = "+ b);
    }
}
```
a의 값을 어딘가에 보관해두기 위해 temp를 생성함

---
**Q2**
```
package Scanner.scanner2;

import java.util.Scanner;

public class ex2 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("첫 번째 숫자: ");
        int num1 = scanner.nextInt();
        System.out.print("두 번째 숫자: ");
        int num2 = scanner.nextInt();
        int temp;

        if (num1 > num2) {
            temp = num1;
            num1 = num2;
            num2 = temp;
        }
        System.out.println("두 숫자 사이의 모든 정수: ");
        for (int i = num1; i <= num2; i++) {
            System.out.print(i);
            System.out.print(",");
        }
    }
}
```
실행 예시
```
첫 번째 숫자: 8
두 번째 숫자: 3
두 숫자 사이의 모든 정수: 
3,4,5,6,7,8,
Process finished with exit code 0
```

## 56. 문제와 풀이3
**Q1**
```
package Scanner.scanner2;

import java.util.Scanner;

public class ex3 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        while (true) {
            System.out.print("이름 입력: ");
            String name = input.nextLine();
            if (name.equals("종료")) {
                System.out.print("프로그램을 종료합니다.");
                break;
            }
            System.out.print("나이 입력: ");
            int age = input.nextInt();
            input.nextLine();

            System.out.println("입력한 이름: "+name+", 나이: "+age);
        }
    }
}
```
실행 예시
```
이름 입력: now
나이 입력: 27
입력한 이름: now, 나이: 27
이름 입력: 종료
프로그램을 종료합니다.
```
---
**Q2**
```
package Scanner.scanner2;

import java.util.Scanner;

public class ex4 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        while (true) {
            System.out.print("상품 가격: ");
            int price = input.nextInt();
            System.out.print("구매 수량: ");
            int quantity = input.nextInt();

            if (price == -1) {
                System.out.println("프로그램 종료");
                break;
            }
            int result = price * quantity;
            System.out.println("총 비용: "+result);
        }

    }
}

```
실행 예시
```
상품 가격: 3000
구매 수량: 3
총 비용: 9000
```

## 57. 문제와 풀이4
**Q1**
```
package Scanner.scanner2;

import java.util.Scanner;

public class ex5 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int sum = 0;
        int count = 0;
        int input = 0;

        System.out.println("숫자 입력: ");
        while (true) {
            input = scanner.nextInt();
            if (input == -1) {
                break;
            }
            sum += input;
            count++;
        }
        double avg = (double) sum / count;
        System.out.println("입력한 숫자들의 합계: "+sum);
        System.out.println("입력한 숫자들의 평균: "+avg);
    }
}

```
실행 예시
```
숫자 입력: 
1
2
-1
입력한 숫자들의 합계: 3
입력한 숫자들의 평균: 1.5
```

**여기 while문 축약이 가능함!!**
```
while ((input=scanner.nextInt()) != -1) {
            sum += input;
            count++;
        }
```
로 축약할 수 있음

---
**Q2**
```
package Scanner.scanner2;

import java.util.Scanner;

public class ex6 {
    static void main(String[] args) {
        Scanner input = new Scanner(System.in);
        int totalCost = 0;

        while (true) {
            System.out.println("1: 상품 입력, 2: 결제, 3: 프로그램 종료");
            int option = input.nextInt();

            if (option == 1) {
                input.nextLine();
                System.out.print("상품명 입력: ");
                String product = input.nextLine();
                System.out.print("가격 입력: ");
                int price = input.nextInt();
                System.out.print("구매 수량 입력: ");
                int quantity = input.nextInt();

                totalCost += price * quantity;
                System.out.println("상품명:"+product+" 가격:"+price+" 수량:"+quantity+" 합계:"+price * quantity);
            } else if (option == 2) {
                System.out.println("총 비용: "+totalCost);
                totalCost = 0;
            } else if (option == 3) {
                System.out.println("프로그램을 종료합니다.");
                break;
            } else {
                System.out.println("올바른 옵션을 선택하세요.");
            }
        }
    }
}

```
실행 예시
```
1: 상품 입력, 2: 결제, 3: 프로그램 종료
1
상품명 입력: 사과
가격 입력: 1000
구매 수량 입력: 5
상품명:사과 가격:1000 수량:5 합계:5000
1: 상품 입력, 2: 결제, 3: 프로그램 종료
2
총 비용: 5000
1: 상품 입력, 2: 결제, 3: 프로그램 종료
3
프로그램을 종료합니다.
```

## 58. 정리
