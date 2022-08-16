> 교재: 자바의 정석 기초편 - 남궁성 

# 조건문과 반복문

- 조건문
  - if문, if-else문, if-else if문, switch문

<br>

- 반복문 
  - for문, while문
    - 항상 그렇지는 않지만 주로 for문은 반복횟수를 알 때, while문은 반복횟수를 모를 때 사용
    - for문과 while문은 서로 변환 가능

# if문

## if-else문
- 둘 중의 하나

## if-else if문
- 여러 개 중의 하나
- 마지막 else블럭은 생략가능!
```java

if (조건식1) {

} else if (조건식2) {

} else if (조건식3) {

} else { 
  // 위의 어느 조건식도 만족하지 않을 때 수행될 문장들을 적는다.
}

```

# switch문

- 처리해야 하는 경우의 수가 많을 때 유용한 조건문

      1. 조건식을 계산한다.
      2. 조건식의 결과와 일치하는 case문으로 이동한다.
      3. 이후의 문장들을 수행한다.
      4. break문이나 switch문의 끝을 만나면 switch문 전체를 빠져나간다. (break문이 없으면 조건문 끝까지 내려가기 때문에 실수로 빼먹지 않도록 조심!)
      5. default문은 if문의 else블럭처럼 생략 가능

```java
switch (조건식) {
      case 값1 :

          break;

      case 값1 :

          break;

      case 값1 :

          break;

      default:
            // 조건식의 결과와 일치하는 case문이 없을때 수행될 문장들
}

```

- 단, 제약조건이 존재함
  - switch문의 조건식 결과는 정수 또는 문자열이어야 한다.
  - case문의 값은 정수 상수(문자 포함), 문자열만 가능하며, 중복되지 않아야 한다. (변수는 사용 불가)

```java

int num, result;
final int ONE = 1;

...

switch(result) {

      case '1':       // OK. 문자 리터럴 (정수 49와 동일)
      case ONE:       // OK. 정수 상수
      case "YES":     // OK. 문자열 리터럴. JDK 1.7부터 허용
      case num:       // 에러. 변수는 불가
      case 1.0:       // 에러. 실수도 불가

}

```

# for문

- 조건식을 생략하면, true로 간주되어서 무한반복문이 됨

```java
public static void main(){
    int i=1 // scope(범위) - 선언위치부터 선언된 블럭의 끝까지
    
    for(;;){
      
    }  
}

```
# do-while문
- 블럭{}을 최소한 한 번 이상 반복 - 사용자 입력받을 때 유용

```java
do {

    // 조건식의 연산결과가 참일 때 수행될 문장들을 적는다. (처음 한 번은 무조건 실행)

} while(조건식);  // <- 끝에 ';' 잊지 않도록 주의!
```

## do-while문을 쓰는게 좋은 경우
- 밑의 코드를 보면 do-while문 대신 while문을 쓰게 되면 코드 중복이 발생하게 된다!

```java

int input  = 0, answer = 0;

answer = (int)(Math.random() * 100) + 1; // 1~100 사이의 임의의 수를 저장
Scanner scanner = new Scanner(System.in);
System.out.println("answer :" + answer);

do {
  System.out.print("1과 100사이의 정수를 입력하세요.>");
  input = scanner.nextInt();

  if(input > answer) {
    System.out.println("더 작은 수로 다시 시도해보세요.");	
  } else if(input < answer) {
    System.out.println("더 큰 수로 다시 시도해보세요.");			
  }
} while(input!=answer);

System.out.println("정답입니다.");

```

```java
int input  = 0, answer = 0;

answer = (int)(Math.random() * 100) + 1; // 1~100 사이의 임의의 수를 저장
Scanner scanner = new Scanner(System.in);
System.out.println("answer :" + answer);

System.out.print("1과 100사이의 정수를 입력하세요.>");  // 입력 코드
input = scanner.nextInt();

while(input!=answer) {
  
  if(input > answer) {
    System.out.println("더 작은 수로 다시 시도해보세요.");	
  } else if(input < answer) {
    System.out.println("더 큰 수로 다시 시도해보세요.");			
  }
  System.out.print("1과 100사이의 정수를 입력하세요.>"); // 입력코드가 여기서 한 번 더 입력되어야 한다.
  input = scanner.nextInt(); // 즉, 코드 중복이 발생한다. 이때는 do-while문을 쓰는 것이 좋다.
}

System.out.println("정답입니다.");
```

# Math.random()의 기본 범위

- Math 클래스의 random 함수 기본범위: 0보다 크거나 같고 1보다 작다
- 0 <= Math.random() < 1 
- 실제 값: 0, 0.1355, 0.00486, 0.000153,....


# break문

```java

		int sum = 0;
		int i   = 0;

		while(true) {  // 무한 반복문 for(;true(생략가능);){}, while문은 true 생략 불가!
			if(sum > 100)
				break; // 조건식이 true여서 무한반복문이지만 이를 통해 자신이 속한 하나의 반복문을 벗어난다.
			++i;
			sum += i;
		} // end of while

		System.out.println("i=" + i);
		System.out.println("sum=" + sum);

```

# continue문

- 자신이 포함된 반복문의 끝으로 이동 - 다음 반복으로 넘어감
- 반복을 계속하지만 특정 조건을 만족하면 반복문 안의 continue문 이후의 모든 코드를 건너띄고 다음 반복으로 넘어가서 조건식을 검토함


# 이름붙은 반복문

- 반복문에 이름을 붙여서 하나 이상의 반복문을 벗어날 수 있다.

```java

      // for문에 Loop1이라는 이름을 붙였다.
		Loop1 : for(int i=2;i <=9;i++) {	
				for(int j=1;j <=9;j++) {
					if(j==5)
						break Loop1;	// Loop1이라는 가장 바깥의 반복문을 빠져나감
//						break;  		// 한 개의 반복문만 빠져나감
//						continue Loop1;
//						continue;
					System.out.println(i+"*"+ j +"="+ i*j);
				} // end of for i
				System.out.println();
		} // end of Loop1

```

```java
int menu = 0, num  = 0;
Scanner scanner = new Scanner(System.in);

outer:   // while문에 outer라는 이름을 붙인다. 
while(true) {
  System.out.println("(1) square");
  System.out.println("(2) square root");
  System.out.println("(3) log");
  System.out.print("원하는 메뉴(1~3)를 선택하세요.(종료:0)>");

  String tmp = scanner.nextLine(); // 화면에서 입력받은 내용을 tmp에 저장
  menu = Integer.parseInt(tmp);    // 입력받은 문자열(tmp)을 숫자로 변환

  if(menu==0) {  
//				System.out.println("프로그램을 종료합니다.");
    break;
  } else if (!(1<= menu && menu <= 3)) {
    System.out.println("메뉴를 잘못 선택하셨습니다.(종료는 0)");
    continue;		
  }

  for(;;) { // 무한 반복문, while(true)도 사용 가능
      System.out.print("계산할 값을 입력하세요.(계산 종료:0, 전체 종료:99)>");
    tmp = scanner.nextLine();    // 화면에서 입력받은 내용을 tmp에 저장
    num = Integer.parseInt(tmp); // 입력받은 문자열(tmp)을 숫자로 변환

    if(num==0)  
      break;        // 계산 종료. for문을 벗어난다.

    if(num==99) 
      break outer;  // 전체 종료. break outer를 통해 for문과 while문을 모두 벗어난다.

    switch(menu) {
      case 1: 
        System.out.println("result="+ num*num);		
        break;
      case 2: 
        System.out.println("result="+ Math.sqrt(num)); 
        break;
      case 3: 
        System.out.println("result="+ Math.log(num));  
        break;
    } 
  } // for(;;)
} // while의 끝
System.out.println("프로그램이 종료되었습니다.");

```