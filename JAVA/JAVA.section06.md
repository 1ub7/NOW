# Section06. 반복문
## 34. 반복문 시작
**반복문이란?** 특정 코드를 반복해서 실행할 때 사용됨   
**종류** : while / do-while / for

## 35. while문1
**while문**
조건에 따라 코드를 반복해서 실행할 때 사용됨
```
while (조건식) {
    // 코드
}
```
- 조건식이 참이면 코드 블럭 실행, 거짓이면 while문을 탈주함
- 코드 블럭 실행한 후 끝나면 다시 조건식 검사로 돌아가서 조건식을 검사함 (무한 반복)

--- 
```
package loop;

public class while1_1 {
    static void main(String[] args) {
        int count =0;
        while (count < 3) {
            count = count + 1;
            System.out.println("현재 숫자는" + count);
        }
    }
}
```
실행 결과
```
현재 숫자는: 1
현재 숫자는: 2
현재 숫자는: 3
```

## 36. while문2
**문제: 1부터 하나씩 증가하는 수를 3번 더해라(1~3 더하기)** 
(while 사용해서)
나의 답
```
package loop;

public class Q {
    static void main(String[] args) {
        int sum = 0;
        int i = 1;

        sum += i;
        System.out.println("i="+i+" sum="+sum);
        i++;

        sum += i;
        System.out.println("i="+i+" sum="+sum);
        i++;

        sum += i;
        System.out.println("i="+i+" sum="+sum);
    }
}
```
정답 여부 : O

**문제2: i부터 하나씩 증가하는 수를 마지막 수까지 더해라**  
나의 답
```
package loop;

public class QQ {
    static void main(String[] args) {
        int sum = 0;
        int i = 1;
        int endNum = 3;

        while (i<=endNum) {
            sum += i;
            System.out.println("i="+i+" sum="+sum);
            i++;
        }
    }
}
```
정답 여부 : O

## 37. do-while문
while문과 비슷하지만, 조건에 상관없이 무조건 한 번은 코드를 실행함
```
do {
    // 코드
} while (조건식);
```

---
```
package loop;

public class DoWhile1 {
    static void main(String[] args) {
        int i = 10;
        while (i < 3) {
            System.out.println("현재 숫자는: "+i);
            i++;
        }
    }
}
```
위에 코드는 무조건 거짓임   
-> 아무것도 출력 안됨

```
package loop;

public class DoWhile2 {
    static void main(String[] args) {
        int i = 10;

        do {
            System.out.println("현재 숫자는: "+i);
            i++;
        } while (i<3);
    }
}
```
위와 같이 do-while을 쓰면   
실행 결과
```
현재 숫자는: 10
```

## 38. break, continue
둘다 반복문에서 사용할 수 있는 키워드임     
**break** : 반복문을 즉시 종료하고 나감     
**continue** : 반복문의 나머지 부분을 건너뛰고 다음 반복으로 진행하는데 사용됨  
(모든 반복문에서 사용 가능)

**break**   
```
while (조건식) {
    코드1;
    break; // 즉시 while문 종료
    코드2;
}
```
코드2 실행도 못하고 바로 while문 끝냄

**continue**    
```
while (조건식) {
    코드1;
    continue; // 즉시 조건식으로 이동함
    코드2;
}
```
코드2 실행도 못하고 바로 다음 while문으로 다시 올라감

---
**문제1: 1부터 시작해서 숫자를 계속 누적해서 더하다가 합계가 10보다 처음으로 큰 값은 얼마인가?**    
나의 답
```
package loop;

public class break1 {
    static void main(String[] args) {
        int sum = 0;
        int i = 1;

        while (true) {
            sum += i;
            if (sum > 10) {
                System.out.println("i= "+i);
                break;
            }
            i++;
        }
    }
}
```
정답 여부 : O

**문제2: 1부터 5까지 숫자를 출력하는데, 숫자가 3일 때는 출력을 건너뛰어야 한다.**   
나의 답
```
package loop;

public class continue1 {
    static void main(String[] args) {
        int i = 1;

        while (i<=5) {
            if (i==3) {
                i++;
                continue;
            }
            System.out.println(i);
            i++;
        }
    }
}
```
정답 여부 : O

## 39. for문1
주로 반복 횟수가 정해져 있을 때 사용함
```
for (1.초기식; 2.조건식; 4.증감식) {
    // 3. 코드
}
```

**for문의 실행 순서**   
1. 초기식 실행 (주로 반복 횟수와 관련된 변수 선언 / 초기화할 때 사용)   
2. 조건식 검증 (참이면 코드 실행 / 거짓이면 for문 탈주)
3. 코드 실행
4. 코드 종료 시 증감식 실행 (주로 초기식에 넣은 반복 횟수와 관련된 변수의 값을 증가할 때 사용)
5. 다시 2.조건식 부터 시작함 (무한 반복)

for문은 while문을 조금 더 편하게 다룰 수 있도록 구조화 한 것임

**문제: i부터 하나씩 증가하는 수를 마지막 수까지 더해라**  
나의 답
```
package loop;

public class for1 {
    static void main(String[] args) {
        int sum = 0;
        int endNum = 3;

        for (int i = 1; i<=endNum; i++) {
            sum += i;
            System.out.println("i="+i+"sum="+sum);
        }
    }
}
```
정답 여부 : O

## 40. for문2
```
for (;;) {
    // 코드
}
```
위 처럼 초기식, 조건식, 증감식은 선택이므로 생략도 가능함

**문제: 1부터 시작하여 숫자를 계속 누적해서 더하다가 합계가 10보다 큰 처음 값은 얼마인가?**     
나의 답
```
package loop;

public class forQ1 {
    static void main(String[] args) {
        int i = 1;
        int sum = 0;

        for (; ; ) {
            sum += i;
            if (sum>10){
                System.out.println("i="+i+" sum="+sum);
                break;
            }
            i++;
        }
    }
}
```
정답 여부 : O

---
for문 없이 while문으로 모든 반복을 다를 수 있음     
하지만 카운터 변수가 명확하거나, 반복 횟수가 정해진 경우에는 for문을 사용하는 것이 구조적으로 더 깔끔하고 유지보수 하기 좋음

## 41. 중첩 반복문
내부에 또 반복문을 만들 수 있음     
(for, while 모두 가능)

```
package loop;

public class Nested1 {
    static void main(String[] args) {
        for (int i = 0; i < 2; i++) {
            System.out.println("외부 for 시작 i:"+i);
            for (int j = 0; j < 3; j++) {
                System.out.println("-> 내부 for "+i+"-"+j);
            }
            System.out.println("외부 for 종료 i: "+i);
            System.out.println();
        }
    }
}
```
실행 결과
```
외부 for 시작 i:0
-> 내부 for 0-0
-> 내부 for 0-1
-> 내부 for 0-2
외부 for 종료 i: 0

외부 for 시작 i:1
-> 내부 for 1-0
-> 내부 for 1-1
-> 내부 for 1-2
외부 for 종료 i: 1
```

## 42. 문제와 풀이1
**문제1: 자연수 출력**      
나의 답
```
package loop;

public class Q1 {
    static void main(String[] args) {
        int count = 1;
        while (count <= 10) {
            System.out.println(count);
            count++;
        }
    }
}
```
다른 답 (for문)
```
package loop;

public class Q1 {
    static void main(String[] args) {
        for (int count = 1; count <= 10; count++) {
            System.out.println(count);
        }
    }
}
```
정답 여부 : O

**문제2: 짝수 출력**    
나의 답
```
package loop;

public class Q2 {
    static void main(String[] args) {
        int num = 2;
        int count = 1;
        while (count <= 10) {
            System.out.println(num);
            num += 2;
            count++;
        }
    }
}
```
다른 답
```
package loop;

public class Q2_1 {
    static void main(String[] args) {
        for (int num = 2, count = 1; count<=10; num += 2, count++ ) {
            System.out.println(num);
        }
    }
}
```
정답 여부 : O

**문제3: 누적 합 계산**     
나의 답
```
package loop;

public class Q3 {
    static void main(String[] args) {
        int max = 10;
        int sum = 0;
        int i = 1;

        while (i<=max) {
            sum += i;
            i++;
        }
        System.out.println(sum);
    }
}
```
다른 답
```
package loop;

public class Q3 {
    static void main(String[] args) {
        int max = 10;
        int sum = 0;
        for (int i = 1; i <= max; i++) {
            sum += i;
        }
        System.out.println(sum);
    }
}
```
정답 여부 : O

## 43. 문제와 풀이2
**문제4: 구구단 출력**  
나의 답
```
package loop;

public class Q4 {
    static void main(String[] args) {
        for (int i = 1; i <= 9; i++) {
            for (int j = 1; j <= 9; j++) {
                System.out.println(i+"*"+j+"="+i*j);
            }
        }
    }
}
```
정답 여부 : O

**문제5: 피라미드 출력**    
나의 답
```
package loop;

public class Q5 {
    static void main(String[] args) {
        int rows = 5; // 정수 적기
        for (int i = 1; i <= rows; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```
정답 여부 : O   
print / println 구분하기

## 44. 정리
**for문**   
장점
- 초기화, 조건 체크, 반복 후의 작업을 한 줄에서 처리할 수 있어 편리함
- 정해진 횟수만큼의 반복을 수행하는 경웨 사용하기 적합함
- 다른 곳에서 이 변수를 실수로 변경할 가능성이 적음

단점
- 루프의 조건이 루프 내부에서 변경되는 경우, for 루프는 관리하기 어려움
- 복잡한 조건을 가진 반복문을 작성하기에는 while문이 더 적합할 수 있음

**while문**     
장점
- 루프의 조건이 루프 내부에서 변경되는 경우, 관리하기 쉬움
- for 루프보다 더 복잡한 조건과 시나리오에 적합함
- 조건이 충족되는 동안 계속해서 루프를 실행하며, 종료 시점을 명확하게 알 수 없는 경우 유용함

단점
- 초기화, 조건 체크, 반복 후의 작업이 분산되어 있어 코드를 이해하거나 작성하기 어려울 수 있음
- 루프 변수가 while 블록 바깥에서도 접근 가능하므로, 이 변수를 실수로 변경하는 상황이 발생할 수 있음

**결론**    
정해진 횟수만큼 반복 수행해야하면 for문     
아니면 while문 사용해라