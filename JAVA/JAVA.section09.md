# Section09. 배열
## 59. 배열 시작
~
## 60. 배열의 선언과 생성
**배열**   
같은 타입의 변수를 사용하기 편하게 하나로 묶어둔 것     

```
package Array;

public class Array1Ref1 {
    static void main(String[] args) {
        int[] student;
        student = new int[5];

        student[0] = 90;
        student[1] = 80;
        student[2] = 70;
        student[3] = 60;
        student[4] = 50;

        System.out.println("학생1 점수: "+student[0]);
        System.out.println("학생2 점수: "+student[1]);
        System.out.println("학생3 점수: "+student[2]);
        System.out.println("학생4 점수: "+student[3]);
        System.out.println("학생5 점수: "+student[4]);
    }
}
```
**배열 변수 선언**      
- int[]처럼 타입 다음에 대괄호([])가 들어감   
- 근데 배열 변수를 선언한다고해서 아직 사용할 수 있는 배열이 만들어진 것은 아님   
    - int a에는 정수를, double b에는 실수를 담을 수 있음
    - int[] student와 같은 배열 변수에는 배열을 담을 수 있음

**배열 생성**       
- 배열을 사용하려면 배열을 생성해야 함
- new는 새로 생성한다는 뜻, int[5]는 int형 변수 5개라는 뜻.     
(int형 변수 5개를 다룰 수 있는 배열을 새로 만든다는 뜻)

**배열과 초기화**   
- new int[5]라고 하면 총 5개의 int형 변수가 만들어짐,   
(자바는 배열을 생성할 때 그 내부값을 자동으로 초기화)
- 숫자는 0, boolean은 false, String은 null로 초기화

**배열 참조값 보관**    
- new int[5]로 배열을 생성하면 배열의 크기만큼 메모리를 확보    
    - int형을 5개 사용하면 4byte * 5 -> 20byte 확보     
- 배열을 생성하고 나면 자바는 메모리 어딘가에 있는 이 배열에 접근할 수 있는 참조값(주소)(x001)을 반환
    - x001이라고 표현한 것이 참조값

```
int[] student = new int[5];
int[] student = x001;
student = x0001;
```

참조값을 확인하고 싶다면 다음과 같이 배열의 변수를 출력  
```   
System.out.println(student);
```

## 61. 배열 사용
**인덱스**      
배열의 위치를 나타내는 숫자     

**배열은 0부터 시작**   
사용 가능한 인덱스의 범위는 0 ~ (n-1)이 됨      
(student가 5개의 요소를 가진다면 student[4]가 배열의 마지막 요소인것)

**배열에 값 대입**      
배열에 값을 대입하든 배열의 값을 사용하든 간에 일반적인 변수와 사용법은 같음.   
추가로 []를 통해 인덱스만 넣어주면 됨.

```
student[0] = 90;
x00l[0] = 90; //변수에 있는 참조값을 통해 실제 배열에 접근
```
```
student[1] = 80;
x001[1] = 80; // 변수에 있는 참조값을 통해 실제 배열에 접근
```
---
**기본형 VS 참조형**    
기본형(Primitive Type) : int, long, double, boolean처럼 변수에 사용할 값을 직접 넣을 수 있는 데이터 타입    
참조형(Reference Type) : int[] student와 같이 데이터에 접근하기 위한 참조(주소)를 저장하는 데이터 타입

## 62. 배열 리펙토링
**리펙토링(Refactoring)**        
기존의 코드 기능은 유지하면서 내부 구조를 개선하여 가독성을 높이고, 유지보수를 용이하게 하는 과정   
(이는 중복을 제거하고, 복잡성을 줄이며 이해하기 쉬운 코드로 만들기 위함)

```
package Array;

public class Array1Ref2 {
    static void main(String[] args) {
        int[] student;
        student = new int[5];

        student[0] = 90;
        student[1] = 80;
        student[2] = 70;
        student[3] = 60;
        student[4] = 50;

        for (int i=0; i<student.length; i++) {
            System.out.println("학생"+(i+1)+" 점수: "+student[i]);
        }
    }
}
```
실행 예시
```
학생1 점수: 90
학생2 점수: 80
학생3 점수: 70
학생4 점수: 60
학생5 점수: 50
```
- 배열의 인덱스는 0부터 시작하기 때문에 i=0을 초기값으로 사용
- student.length
    - 배열의 길이를 제공하는 기능
    - 조회만 가능, 대입 불가능
    - 현재 배열의 크기가 5이기 때문에 여기서는 5가 출력
---
위에 코드를 더 간편화 시킨 거
```
package Array;

public class Array1Ref3 {
    static void main(String[] args) {
        int[] student = {90, 80, 70, 60, 50};

        for (int i=0; i<student.length; i++) {
            System.out.println("학생"+(i+1)+" 점수: "+student[i]);
        }
    }
}
```

**간단한 배열 생성**    
배열은 {}만 사용해서 생성과 동시에 편리하게 초기화하는 기능 제공    
(이때는 예제와 같이 배열 변수의 선언을 한 줄에 함께 사용할 때만 가능)

## 63. 2차원 배열 - 시작
**2차원 배열**      
행과 열로 구성된 배열   
사용법은 []가 하나 추가되는 것을 제외하고는 1차원 배열과 같음   
**arr[행][열], arr[row][column]**   

```
package Array;

public class ArrayDi0 {
    static void main(String[] args) {
        int[][] arr = new int[2][3];
        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[0][2] = 3;
        arr[1][0] = 4;
        arr[1][1] = 5;
        arr[1][2] = 6;

        System.out.print(arr[0][0] + " ");
        System.out.print(arr[0][1] + " ");
        System.out.print(arr[0][2] + " ");
        System.out.println(); //한 행이 끝나면 라인 변경

        System.out.print(arr[1][0] + " ");
        System.out.print(arr[1][1] + " ");
        System.out.print(arr[1][2] + " ");
        System.out.println(); //한 행이 끝나면 라인 변경
    }
}
```
실행 예시
```
1 2 3 
4 5 6
```

## 64. 2차원 배열 - 리팩토링1
위에 코드를 중첩 for문 써서 간편화한 거
```
package Array;

public class ArrayDi2 {
    static void main(String[] args) {
        int[][] arr = new int[2][3];
        arr[0][0] = 1;
        arr[0][1] = 2;
        arr[0][2] = 3;
        arr[1][0] = 4;
        arr[1][1] = 5;
        arr[1][2] = 6;

        for (int row=0; row<2; row++) {
            for (int column = 0; column<3; column++) {
                System.out.print(arr[row][column]+" ");
            }
            System.out.println();
        }
    }
}
```

## 65. 2차원 배열 - 리팩토링2
위에 코드를 배열 적는 방식을 간편화한 거
```
package Array;

public class ArrayDi2 {
    static void main(String[] args) {
        int[][] arr = {
            {1,2,3},
            {4,5,6}
        };

        for (int row=0; row< arr.length; row++) {
            for (int column = 0; column<arr[row].length; column++) {
                System.out.print(arr[row][column]+" ");
            }
            System.out.println();
        }
    }
}
```
---
**구조 개선 - 값 입력**     
배열의 크기 상관없이 배열에 순서대로 1씩 증가하는 값을 입력하도록 변경      
```
package Array;

public class ArrayDi3 {
    static void main(String[] args) {
        int[][] arr = new int[3][3];

        int i=1;
        for (int row=0; row<arr.length; row++) {
            for (int column=0; column<arr[row].length; column++) {
                arr[row][column] = i++;
            }
        }

        for (int row=0; row< arr.length; row++) {
            for (int column = 0; column<arr[row].length; column++) {
                System.out.print(arr[row][column]+" ");
            }
            System.out.println();
        }
    }
}
```

## 66. 향상된 for문
**향상된 for문**    
```
for (변수 : 배열 또는 컬렉션) {
    // 배열 또는 컬렉션의 요소를 순화하면서 수행할 작업
}
```
---
예시
```
package Array;

public class EnhancedFor1 {
    static void main(String[] args) {
        int[] numbers = {1,2,3,4,5};

        //일반 for문
        for (int i=0; i<numbers.length; i++) {
            int number = numbers[i];
            System.out.println(number);
        }
        //형성된 for문, for-each문
        for (int number : numbers) {
            System.out.println(number);
        }
        //for-each문을 사용할 수 없는 경우, 증가하는 index 값 필요
        for (int i=0; i<numbers.length; ++i) {
            System.out.println("number"+i+"번의 결과는: "+numbers[i]);
        }
    }
}
```
향상된 for문 예시
```
for (int number : numbers) {
        System.out.println(number);
}
```
- 배열의 인덱스를 사용하지 않고, 종료 조건을 주지 않아도 됨
- :의 오른쪽에 numbers와 같이 탐색할 배열을 선택하고, :의 왼쪽에 int number와 같이 반복할 때 마다 찾은 값을 저장할 변수를 선언
- 인덱스 사용 안해도 배열의 요소를 순화할 수 있음   
(코드가 간결하고 가독성이 좋음)
---
**향상된 for문을 사용하지 못하는 경우**     
int i와 같은 증가하는 인덱스 값을 직접 사용해야할 때    

## 67. 문제와 풀이1
**Q1**      
배열을 사용하도록 변경
```
package Array.ex;

public class ArraryEx1 {
    static void main(String[] args) {
        int[] student = {90, 80, 70, 60, 50};

        int total = 0;
        for (int i = 0; i <student.length; i++) {
            total += student[i];
        }
        double avg = (double) total/5;

        System.out.println("점수 총합: "+total);
        System.out.println("점수 평균: "+avg);
    }
}
```
**Q2**      
배열의 입력과 출력
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx2 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        int[] nums = new int[5];
        System.out.println("5개의 정수를 입력하세요: ");
        for (int i = 0; i<nums.length; i++) {
            nums[i] = scanner.nextInt();
        }
        System.out.println("출력");
        for (int i=0; i<nums.length; i++) {
            System.out.print(nums[i]);
            if (i<nums.length-1) {
                System.out.print(", ");
            }
        }
    }
}
```
**Q3**      
배열과 역순 출력    
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx3 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] nums = new int[5];

        System.out.println("5개의 정수를 입력하세요: ");
        for (int i = 0; i<nums.length; i++) {
            nums[i] = scanner.nextInt();
        }
        System.out.println("출력");
        for (int i=4; i>=0; i--) {
            System.out.print(nums[i]);
            if (i>0) {
                System.out.print(", ");
            }
        }
    }
}
```
**Q4**      
합계와 평균
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx4 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] nums = new int[5];
        int sum=0;
        double avg;

        System.out.println("5개의 정수를 입력하세요:");
        for (int i=0; i<nums.length; i++) {
            nums[i] = scanner.nextInt();
            sum += nums[i];
        }
        avg = (double) sum / 5;
        System.out.println("입력한 정수의 합계: "+sum);
        System.out.println("입력한 정수의 평균: "+avg);
    }
}
```
**Q5**  
합계와 평균2
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx5 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[] nums = new int[3];
        int sum=0;
        double avg;

        System.out.println("입력받을 숫자의 개수를 입력하세요: ");
        System.out.println("3개의 정수를 입력하세요: ");
        for (int i=0; i<nums.length; i++) {
            nums[i] = scanner.nextInt();
            sum += nums[i];
        }
        avg = (double) sum / 3;
        System.out.println("입력한 정수의 함계: "+sum);
        System.out.println("입력한 정수의 평균: "+avg);
    }
}
```

## 68. 문제와 풀이2
**Q1**      
가장 작은 수, 큰 수 찾기    
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx6 {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("입력 받을 숫자의 개수를 입력하세요: ");
        int n = scanner.nextInt();

        int[] nums = new int[n];
        int minNumber, maxNumber;

        System.out.println(n+"개의 정수를 입력하세요:");
        for (int i = 0; i<n; i++) {
            nums[i] = scanner.nextInt();
        }
        minNumber = maxNumber = nums[0];
        for (int i = 1; i<n; i++) {
            if (nums[i] < minNumber) {
                minNumber = nums[i];
            }
            if (nums[i] > maxNumber) {
                maxNumber = nums[i];
            }
        }
        System.out.println("가장 작은 정수: "+minNumber);
        System.out.println("가장 큰 정수: "+maxNumber);
    }
}
```
**Q2**  
2차원 배열1 - 3명의 학생
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx7 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int[][] scores = new int[4][3];
        String[] subjects = {"국어", "영어", "수학"};

        for (int i =0; i<4; i++) {
            System.out.println((i+1)+"번 학생의 성적을 입력하세요:");
            for (int j=0; j<3; j++) {
                System.out.println(subjects[j]+"점수:");
                scores[i][j] = scanner.nextInt();
            }
        }
        for (int i =0; i<4; i++) {
            int total = 0;
            for (int j=0; j<3; j++) {
                total += scores[i][j];
            }
            double avg = total / 3.0;
            System.out.println((i+1)+"번 학생의 총점: "+total+", 평균: "+avg);
        }
    }
}
```
**Q3**  
2차원 배열2 - 학생수 입력 받아서 하기
```
package Array.ex;

import java.util.Scanner;

public class ArrayEx8 {
    static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("학생수를 입력하세요: ");
        int student = scanner.nextInt();

        int[][] scores = new int[student][3];
        String[] subjects = {"국어", "영어", "수학"};

        for (int i =0; i<student; i++) {
            System.out.println((i+1)+"번 학생의 성적을 입력하세요:");
            for (int j=0; j<3; j++) {
                System.out.print(subjects[j]+"점수:");
                scores[i][j] = scanner.nextInt();
            }
        }
        for (int i =0; i<student; i++) {
            int total = 0;
            for (int j=0; j<3; j++) {
                total += scores[i][j];
            }
            double avg = total / 3.0;
            System.out.println((i+1)+"번 학생의 총점: "+total+", 평균: "+avg);
        }
    }
}
```

## 69. 문제와 풀이3
**Q1**      
상품 관리 프로그램 만들기
```
package Array.ex;

import java.util.Scanner;

public class ProductAdminEx {
    static void main(String[] args) {
        int maxProducts = 10;
        String[] name = new String[maxProducts];
        int[] price = new int[maxProducts];
        int count = 0;

        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("1. 상품 등록 | 2. 상품 목록 | 3. 종료");
            System.out.print("메뉴를 선택하세요: ");
            int num = scanner.nextInt();
            scanner.nextLine();

            if (num == 1) {
                if (count >= maxProducts) {
                    System.out.println("더 이상 상품을 등록할 수 없습니다.");
                    continue;
                }
                System.out.print("상품 이름을 입력하세요: ");
                name[count] = scanner.nextLine();
                System.out.print("상품 가격을 입력하세요: ");
                price[count] = scanner.nextInt();

                count++;
            } else if (num == 2) {
                if (count == 0) {
                    System.out.println("등록된 상품이 없습니다.");
                    continue;
                }
                for (int i = 0; i < count; i++) {
                    System.out.println(name[i] + ":" + price[i] + "원");
                }
            } else if (num == 3) {
                System.out.println("프로그램을 종료합니다.");
                break;
            } else {
                System.out.println("잘못된 메뉴를 선택하셨습니다.");
            }
        }
    }
}

```
## 70. 정리