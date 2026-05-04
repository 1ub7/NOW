# Section05. 조건문
## 26. if문1 - if, else
**조건문이란?** 특정 조건에 따라서 다른 코드를 실행하는 것      
**if문**과 **Switch문**이 있음  
둘다 특정 조건에 따라서 다른 코드를 실행

**if문**    
특정 조건이 참인지 확인하고, 그 조건이 참(True)일 경우 특정 코드 블록을 실행함
```
if (조건) {
    // 조건이 참일 때 실행되는 코드
}
```

---

```
package COND;

public class If1 {
    static void main(String[] args) {
        int age = 20;

        if (age>=18) {
            System.out.println("성인입니다.");
        }

        if (age < 18) {
            System.out.println("미성년자입니다.");
        }
    }
}
```
실행 결과
```
성인입니다.
```
age의 값이 20이니까 첫번째 if문에 대입하면 20>=18 (True)임

---

**else문**      
else문은 if문에서 만족하는 조건이 없을 때 실행하는 코드를 제공함
```
if (조건) {
    // 조건이 참일 때 실행되는 코드
} else {
    // 만족하는 조건이 없을 때 실행되는 코드
}
```

else문을 사용하면 위에서 if문 예시로 진행했던 코드를 아래와 같이 더 간략하게 바꿀 수 있음   

```
package COND;

public class if2 {
    static void main(String[] args) {
        int age = 20;
        if (age >= 18) {
            System.out.println("성인입니다.");
        } else {
            System.out.println("미성년자입니다.");
        }
    }
}
```
실행 결과
```
성인입니다.
```

## 27. if문2 - else if
**문제**    
(if문만 사용해서 코드 작성)     
나의 답
```
package COND;

public class if3 {
    static void main(String[] args) {
        int age = 17;// 나이 적기

        if (age <= 7) {
            System.out.println("미취학");
        }
        if (age >= 8 && age <= 13) {
            System.out.println("초등학생");
        }
        if (age >=14 && age <=16) {
            System.out.println("중학생");
        }
        if (age >= 17 && age <= 19) {
            System.out.println("고등학생");
        }
        if (age >=20) {
            System.out.println("성인");
        }
    }
}
```
정답 여부 : O   

하지만 위에 코드는 단점이 있음  
- 이미 조건을 만족해도 불필요한 다음 조건을 계속 검사함 
- 조건을 중복 체크하면서 코드의 효율성도 떨어짐

저런 코드에 쓰이는 게 **else if문**     

**else if문**       
if문의 조건이 거짓일 때 조건을 검사함   
(앞에 있던 if문이 참이면 실행 안함)
```
if (조건1) {
    // 조건1이 참일 때 실행되는 코드
} else if (조건2) {
    // 조건1이 거짓이고, 조건2가 참일 때 실행되는 코드
} else if (조건3) {
    // 조건2이 거짓이고, 조건3이 참일 때 실행되는 코드
} else {
    // 모든 조건이 거짓일 때 실행되는 코드
}
```
if문을 하나로 묶는다는 개념     
(else는 생략 할 수 있음)

## 28. if문3 - if문과 else if문
if문에 else if문을 같이 사용하는 것은 서로 연관된 조건일 때 사용함      
그치만 서로 연관 없는 독립 조건이면 else if 안쓰고 if문을 각각 사용함

예시1
```
if (조건1) {
    // 작업1 수행
} else if (조건2) {
    // 작업2 수행
}
```
예시2
```
if (조건1) {
    // 작업1 수행
}
if (조건2) {
    // 작업2 수행
}
```
예시1은 둘 중 하나만 수행됨 / 예시2는 조건만 맞으면 둘다 수행될 수도 있음       
(if문에 여러 조건이 있다고 항상 if-else로 묶어서 사용할 수 있는 것은 아님  )

---

**문제**    
나의 답
```
package COND;

public class if5 {
    static void main(String[] args) {
        int price=10000;
        int age=10;
        int dis=0;

        if (price>=10000) {
            dis+=1000;
            System.out.println("10000원 이상 구매, 1000원 할인함");
        }
        if (age<=10) {
            dis+=1000;
            System.out.println("10살 이하, 1000원 할인함");
        }
        System.out.println((price-dis)+"원 할인");
    }
}
```
정답 여부 : O

---
**참고**    
if문을 각각 사용할지, if와 else if를 같이 묶어서 사용할지는 요구사항에 따라 다름    

if문 안에 명령이 한개만 있으면 {}중괄호를 생략 할 수 있음   
그치만 중괄호를 쓰는게 훨 나음
- 중괄호를 사용할 시 가독성이 훨씬 좋아짐
- 중괄호를 사용할 시 나중에 코드 수정할 때 오류를 덜 발생 시킴

## 29. switch문
**문제**    
(if문 사용해서 코드 출력)   
나의 답
```
package COND;

public class if6 {
    static void main(String[] args) {
        int grade = 2;
        int coupon;

        if (grade==1){
            coupon = 1000;
        }
        else if (grade==2) {
            coupon = 2000;
        }
        else if (grade==3) {
            coupon = 3000;
        }
        else {
            coupon = 500;
        }
        System.out.println("발급받은 쿠폰"+coupon);
    }
}
```
정답 여부 : O

**Switch문**    
if문을 조금 더 편리하게 사용할 수 있는 기능     
if문은 비교 연산자 사용 가능이지만,   
  switch문은 단순히 값이 같은지만 비교할 수 있음    

```
switch (조건식) {
    case value1:
        // 조건식의 결과 값이 value1일 때 실행되는 코드
        break;
    case value2:
        // 조건식의 결과 값이 value2일 때 실행되는 코드
        break;
    default :
        // 조건식의 결과 값이 위에 어떤 값에도 해당하지 않을 때 실행되는 코드
}
```
- 조건식의 결과 값이 어떤 case의 값과 일치하면 해당 case의 코드를 실행
- break문은 현재 실행 중인 코드를 끝내고 switch문을 빠져나가게 하는 역할
- 만약 break문이 없으면 일치하는 case 이후의 모든 case 코드들이 순서대로 실행됨
- default는 조건식의 결과값이 모든 case의 값과 일치하지 않을 때 실행됨 (선택)

```
package COND;

public class S2 {

    public static void main(String[] args) {
        int grade = 1;

        int coupon;
        switch (grade) {
            case 1:
                coupon = 1000;
                break;
            case 2:
                coupon = 2000;
                break;
            case 3:
                coupon = 3000;
                break;
            default:
                coupon = 500;
        }
        System.out.println("발급받은 쿠폰 " + coupon);
    }
}
```
실행 결과
```
발급받은 쿠폰 2000
```
---

**만약 break문이 없다면?**   
다음 case로 계속 실행이 됨

**if문 VS switch문**    
특정 값에 따라 코드를 실행할 때는 switch문을 사용하면 좋음      
(if문만 사용해도 되긴 함)

**JAVA14 새로운 switch문**      
switch문은 if문 보다 조금 덜 복잡한 것 같지만, 그래도 코드가 깔끔하게는 나오지 않음     
위에 문제를 해결하고자 새로운 switch문이 정식 도입됨

```
package COND;

public class S4 {
    static void main(String[] args) {
        int grade=2;

        int coupon = switch (grade) {
            case 1 -> 1000;
            case 2 -> 2000;
            case 3 -> 3000;
            default -> 500;
        } ;
        System.out.println("발급받은 쿠폰" + coupon);
    }
}
```
- ->를 사용함
- 선택된 데이터를 반환할 수 있음

## 30. 삼항 연산자
참과 거짓에 따라서 특정 값을 구하는 경우 ?: 연산자를 사용할 수 있음     
이 연산자를 사용하면 if문과 비교해서 코드를 단순화 할 수 있음
```
package COND;

public class Op1 {
    static void main(String[] args) {
        int age = 18;
        String status;
        if (age >= 18) {
            status = "성인";
        } else {
            status = "미성년자";
        }
        System.out.println("age = " + age + " status = " + status);
    }
}
```
이랬던 코드를
```
package COND;

public class Op2 {
    static void main(String[] args) {
        int age = 18;
        String status = (age >= 18) ? "성인" : "미성년자";
        System.out.println("age = " + age + " status = " + status);
    }
}
```
이렇게 간결하게 만들 수 있음

----
**삼항 연산자**     
```
(조건) ? 참_표현식 : 거짓_표현식
```
- 삼항 연산자 = 항이 3개
- 특정 조건에 따라 결과가 나오기 때문에 조건 연산자라고도 함
- 조건 만족 시 참_표현식 / 아닐 시 거짓_표현식 실행됨 (if, else문과 유사)
- if문처럼 코드 블럭을 넣을 수 있는 게 아니라 단순한 표현식만 넣을 수 있음

## 31. 문제와 풀이1
**문제1 : 학점 계산하기**    
나의 답
```
package COND;

public class Q1 {
    static void main(String[] args) {
        int score = 87; // 점수 적기
        if (score>=90) {
            System.out.println("A");
        }
        else if (score>=80 && score<90) {
            System.out.println("B");
        }
        else if (score>=70 && score<80) {
            System.out.println("C");
        }
        else if (score>=60 && score<70) {
            System.out.println("D");
        } else {
            System.out.println("F");
        }
    }
}
```
정답 여부 : O

**문제2 : 거리에 따른 운송 수단 선택하기**      
나의 답
```
package COND;

public class Q2 {
    static void main(String[] args) {
        int distance = 100; // 거리 적기
        if (distance <= 1) {
            System.out.println("도보");
        }
        else if (distance<=10) {
            System.out.println("자전거");
        }
        else if (distance <= 100) {
            System.out.println("자동차");
        }
        else {
            System.out.println("비행기");
        }
    }
}
```
정답 여부 : O

**문제3 : 환율 계산하기**       
나의 답
```
package COND;

public class Q3 {
    static void main(String[] args) {
        int dollar = 10;
        if (dollar < 0) {
            System.out.println("잘못된 금액입니다.");
        } else if (dollar == 0) {
            System.out.println("환전할 금액이 없습니다.");
        } else if (dollar > 0) {
            System.out.println("환전 금액은 " + dollar*1300 + "원입니다.");
        }
    }
}
```
정답 여부 : O

## 32. 문제와 풀이2
**문제4 : 평점에 따른 영화 추천하기**   
나의 답
```
package COND;

public class Q4 {
    static void main(String[] args) {
        double rating = 8;// 평점 적기
        if (rating <= 9) {
            System.out.println("어바웃타임 추천");
        } if (rating <= 8) {
            System.out.println("토이스토리 추천");
        } if (rating <= 7) {
            System.out.println("고질라 추천");
        }
    }
}
```
정답 여부 : O

**문제5 : 학점에 따른 성취도 출력하기**     
나의 답
```
package COND;

public class Q5 {
    static void main(String[] args) {
        String grade = "C"; // 학점 적기
        String coment = switch (grade) {
            case "A" -> "탁월한 성과입니다!";
            case "B" -> "좋은 성과입니다!";
            case "C" -> "준수한 성과입니다!";
            case "D" -> "향상이 필요합니다.";
            case "F" -> "불합격입니다.";
            default -> "잘못된 학점입니다.";
        };
        System.out.println(coment);
    }
}
```
정답 여부 : O

**문제6 : 더 큰 숫자 찾기**     
나의 답
```
package COND;

public class Q6 {
    static void main(String[] args) {
        int a = 10; //정수 적기
        int b = 20; //정수 적기
        int max = (a>b) ? a : b;
        System.out.println("더 큰 숫자는 " + max + "입니다.");
    }
}
```
정답 여부 : O

**문제7 : 홀수 짝수 찾기**      
나의 답
```
package COND;

public class Q7 {
    static void main(String[] args) {
        int x = 5;
        String result = (x%2==0) ? "짝수" : "홀수";
        System.out.println("x = " + x + "," + result);
    }
}
```
정답 여부 : O

## 33. 정리
**if문** : 특정 조건이 참인지 거짓인지 확인하고, 그 조건이 참일 경우 특정 코드 블록을 실행함    
**else문** : if문이 거짓인 경우 실행    
**else if문** : if문의 조건이 거짓일 때 다음 조건을 검사함  
(if문이 참이면 else if문은 실행 안함)   
**switch문** : 조건식에 해당하는 특정 값으로 실행할 코드를 선택함