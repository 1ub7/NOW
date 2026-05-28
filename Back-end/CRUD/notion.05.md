# 1. @(Annotation)
자바에서 클래스, 메서드, 변수 등에 추가적인 정보를 제공하기 위해 사용하는 문법      
주로 프로그램의 동작 방식이나 객체의 역할, 설정 정보를 표시하기 위해 사용되며 @ 기호를 사용하여 작성
## 1-1. 컴포넌트 등록
스프링이 객체를 자동 생성하고 관리하도록 등록   

**@Controller** : 클라이언트의 웹 요청을 처리하는 클래스에 사용     
URL 요청을 받아 적절한 페이지나 데이터를 반환하는 역할      
**@Service** : 비즈니스 로직을 처리하는 클래스에 사용   
게시글 작성, 회원가입, 로그인 처리 등 실제 기능 구현 담당 역할      
**@Repository** : DB 접근을 담당하는 클래스에 사용        
주로 JPA Repository와 함께 사용되며 데이터 저장, 조회, 수정, 삭제 기능을 처리   
**@Component** : 스프링이 관리하는 일반 객체를 등록할 때 사용       

## 1-2. 요청 매핑
클라이언트의 URL 요청과 메서드를 연결할 때 사용  

**@GetMapping** : GET 요청 처리     
**@PostMapping** : POST 요청 처리   
**@PutMapping** : PUT 요청 처리     
**@DeleteMapping** : DELETE 요청 처리   
**@RequestMapping** : 여러 요청 방식을 모두 설정할 수 있는 기본 매핑

## 1-3. 요청 데이터 처리
클라이언트가 보낸 데이터를 받아올 때 사용   

**@RequestParam** : 클라이언트가 URL이나 form으로 전달한 값을 받음    
**@PathVariable** : URL 경로에 있는 값을 변수로 받음      
**@RequestBody** :  클라이언트가 보낸 JSON 데이터를 객체로 변환하여 받음
**@ModelAttribute** : 폼(Form) 데이터를 객체에 자동으로 바인딩함

## 1-4. 응답 관련
클라이언트에게 데이터를 어떤 형태로 반환할지 지정   

**@ResponseBody** : 메서드 반환값을 view가 아닌 그대로 데이터를 반환  
**@RestController** : REST API 전용 컨트롤러를 만들 때 사용     
**@ResponseStatus** : HTTP 응답 상태 코드를 지정    

## 1-5. 의존성 주입 
객체를 직접 생성하지 않고 스프링이 자동으로 연결하도록 사용         

**@Autowired** : 스프링이 자동으로 객체를 주입      
**@Qualifier** : 같은 타입의 객체가 여러 개 존재할 때 특정 객체를 지정하여 주입     
**@Inject** : 의존 객체를 자동으로 주입      

## 1-6. JPA 관련
DB 테이블과 객체를 연결할 때 사용   

**@Entity** : 해당 클래스를 DB 테이블로 사용    
**@Id** : 기본 키(Primary Key)를 지정   
**@GeneratedValue** : 기본 키 생성 전략을 설정           
**@Column** : 컬럼 설정을 지정   

# 2. Package
자바 클래스들을 기능이나 역할별로 그룹화하여 관리하기 위한 논리적 구조
## 2-1. controller
클라이언트의 요청(URL 요청)을 받아 처리하고, 적절한 응답을 반환하는 계층    

브라우저에서 전달된 요청을 받아 Service 계층에 필요한 작업을 요청하며, 처리 결과에 따라 HTML 페이지나 데이터를 사용자에게 반환  
(주로 @Controller, @GetMapping, @PostMapping 사용)

## 2-2. entity
DB 테이블 구조를 자바 클래스로 표현하는 계층    
클래스의 필드가 DB의 컬럼과 연결되며, 객체와 DB 테이블 간의 매핑을 담당     
(주로 @Entity 사용)

## 2-3. repository
DB에 접근하여 데이터를 저장, 조회, 수정, 삭제하는 기능을 담당하는 계층  
(주로 JpaRepository를 상속받음)

## 2-4. service
애플리케이션의 핵심 비즈니스 로직을 처리하는 계층   

Controller로부터 전달받은 요청을 기반으로 필요한 기능을 수행하며, Repository를 호출하여 데이터베이스 작업을 처리

# 3. SQL table
SQL에서 테이블은 데이터를 행과 열 형태로 저장하는 DB의 기본 구조

## 3-1. 생성 시 확인 요소
**Column Name** : 이름 지정     
**Datatype** : 저장할 데이터의 자료형   

## 3-2. 컬럼 속성    
**PK(Primary Key)** : 각 데이터를 구별하는 고유 값  
**NN(Not Null)** : NULL 값 허용 안 함   
**UQ(Unique)** : 중복 허용 안 함    
**B(Binary)** : 문자 데이터를 바이너리 방식으로 저장/비교   
(대소문자 구분 영향)    
**UN(Unsigned)** : 부호 없는 숫자   
**ZF(Zerofill)** : 빈 자리를 0으로 채움     
**AI(Auto Increment)** : 자동 증가  
**G(Generated)** : 자동 계산 컬럼

# 4. 접근 제어자
클래스, 변수, 메서드 등에 대한 접근 범위를 제한하는 키워드

**public** : 모든 클래스에서 접근 가능  
**private** : 해당 클래스 내부에서만 접근 가능  
**protected** : 같은 패키지 내부와 상속 관계의 클래스에서 접근 가능     
**default** : 접근 제어자를 작성하지 않은 상태를 의미, 같은 패키지 내부에서만 접근 가능 

| 접근 제어자 | 같은 클래스 | 같은 패키지 | 다른 패키지 | 상속 관계 |
| ----- | ----- | ----- | ----- | ----- |
| public | O | O | O | O |
| private | O | X | X | X |
| protected | O | O | X | O |
| default | O | O | X | X |

# 5. return
스프링에서 return은 메서드의 처리 결과를 반환하는 역할    

아래는 예시들   
(1) HTML 페이지 반환
```
@GetMapping("/")
public String home() {

    return "home";
}
```
이면? home 페이지를 반환. 즉, 사용자를 해당 화면으로 이동시킴       

(2) redirect 반환
```
return "redirect:/board/list";
```
이면? 특정 URL로 다시 요청을 보내고 게시글 작성 후 목록 페이지 이동 같은 데 사용    

(3) 데이터 반환     
```
@ResponseBody
@GetMapping("/test")
public String test() {

    return "hello";
}
```
이면? 브라우저에 hello 자체 출력    

(4) 객체 반환 (REST API)
```
@RestController
public class BoardController {

    @GetMapping("/board")
    public Board board() {

        return new Board();
    }
}
```
JSON 형태로 반환

# 6. JSON
(**J**avaScript **O**bject **N**otation)    
서버와 클라이언트 사이에서 데이터를 주고받기 위해 사용하는 텍스트 기반의 데이터 형식

# 7. xmlns
(**XML** **N**ame**s**pace)     
XML 문서에서 태그 이름이 서로 충돌하지 않도록 구분하기 위해 사용하는 namespace 선언

# 8. Integer
자바에서 기본 자료형 int를 객체 형태로 다루기 위한 Wrapper 클래스     

(1) null 사용 가능      
```
Integer num = null;
```
가능
```
int num = null;
```
불가능

(2) 메서드 사용 가능    
```
Integer.parseInt("10");
```
**parseInt?** 문자열을 정수형 데이터로 변환함  