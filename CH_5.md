> 교재: 자바의 정석 기초편 - 남궁성 

# 배열
- 배열은 **같은 타입**의 여러 변수를 하나의 묶음으로 다루는 것
- 변수를 하나 하나 선언하면 저장공간이 연속적이지 않다.
- 배열을 구성하는 변수들은 저장공간이 연속적으로 배치되어 있다.

```java
int score1, score2, score3,...;  // 많은 수의 변수를 선언하기가 불편함


int[] score = new int[5]; // 5개의 int값을 저장할 수 있는 배열을 생성

여기서 score라는 변수는 참조변수라고 하며 값을 저장하는 공간이 아니라 배열의 주소값이 저장된다.

```

# 배열의 선언과 생성

- 배열의 선언: 배열을 다루기 위한 참조변수의 선언

```java
선언 방법
- 타입[] 변수이름;            // 배열을 선언 (배열을 다루기 위한 참조변수 선언) 
- 변수이름 = new 타입[길이];  // 배열을 생성 (실제 저장공간을 생성)

int[] score;          // int타입의 배열을 다루기 위한 참조변수 score 선언
score = new int[5];   // int타입의 값 5개를 저장할 수 있는 배열을 생성한 후 score라는 참조변수안에 배열의 주소값을 저장

int[] score = new int[5]  // 이렇게 한 문장으로 선언 가능, 배열의 선언과 생성을 동시에

```

# 배열의 길이

- 배열이름.length : 배열의 길이 (int형 **상수**)
- 배열은 한 번 생성하면 실행 동안 그 길이를 바꿀 수 없다.

```java
int[] arr = new int[5];
int   tmp = arr.length;
```

- 배열이름.length를 사용하는 사례

```java
int[] arr = new int[5];
for(int i=0;i < score.length; i++) // score.length를 사용하면 조건식을 변경하지 않아도 자동으로 바뀜
```

# 배열의 초기화
- 배열의 각 요소에 처음으로 값을 저장하는 것
- 배열은 기본적으로 생성과 동시에 자동초기화 된다.

```java
int[] score = new int[5]; // 길이가 5인 int형 배열을 생성한다.
score[0] = 50;            // 각 요소에 직접 값을 저장한다. (초기화)
score[1] = 60;
score[2] = 70;
score[3] = 80;
score[4] = 90;
```

- 배열을 초기화하는 간단한 방법

```java
// 방법 1
int[] score = new int[]{50, 60, 70, 80, 90};

// 방법2 <- 이 방법을 더 많이 사용함
int[] score = {50, 60, 70, 80, 90}; // new int[]를 생략할 수 있음
```

## 주의사항

**방법2를 두 줄로 나누는 것은 불가능!**

```java
int[] score;
score = {50, 60, 70, 80, 90}; // 에러 발생! new int[]를 생략할 수 없음
```

# 배열의 출력

- 배열이름을 통해서는 배열의 값이 출력되지 않는다.

```java
int[] iArr = {100, 95, 80, 70, 60};
System.out.println(iArr); // [I@53bd815b와 같은 형식의 문자열이 출력된다.
```

- 단,char형의 경우 println의 기능으로 인해 char형 배열은 배열이름으로 값이 출력된다.

```java
char[] chArr = {'a', 'b', 'c', 'd'}
System.out.println(chArr):  // 출력-> abcd
```

## 배열을 출력하는 방법
### 1. for문을 이용하는 방법
```java
for(int i=0; i< iArr.length; i++){ // 배열의 요소를 순서대로 하나씩 출력
    System.out.println(iArr[i]);
}
```
### 2. Arrays클래스를 이용하는 방법
  - Arrays.toString(배열명)
  - toString이 iArr배열 값을 문자열 "[100, 95, 80, 70, 60]"로 변환하고 println이 이 문자열을 출력시킨다.
  - 단, Arrays클래스를 사용하기 위해서는 java.util.Arrays를 import해야한다.(이클립스 단축키: ctrl+shift+o(알파벳))
```java
// 배열 iArr의 모든 요소를 출력한다. [100, 95, 80, 70, 60]
System.out.println(Arrays.toString(iArr)); 
```

# String배열의 선언과 생성

- n개의 문자열을 담을 수 있는 배열을 생성한다.
- String배열은 참조형이기 때문에 null값이 기본값이다.

```java
String[] name = new String[n]; 
```

|자료형|기본값|
|---|---|
|char|'\u0000'|
|byte, short, int|0|
|long|0L|
|float|0.0f|
|**참조형**|**null**|

<br>

- 실제로 배열의 공간 하나에 문자열이 그대로 저장되는 것이 아니라 참조형이기 때문에 문자열은 각각 다른 공간에 저장되고 그 공간의 주소값이 배열의 공간 하나에 저장된다. 그렇게 주소값이 저장된 여러개의 공간으로 구성된 하나의 배열의 전체 주소값은 다시 name이라는 참조형 변수 안에 저장된다.

```java
String[] name = new String[3]; // String[]은 참조형 배열이기 때문에 name은 참조형 변수이다.

String[] name = {"Kim", "Park", "Yi" };

```

# String클래스

- 문자열은 여러 개의 문자가 나열되어 있는 것
- String클래스는 문자 배열인 char[]에 메서드(기능)을 결합한 것, 왜냐하면 서로 관련이 있기 때문

## String클래스는 내용을 변경할 수 없다.(read only)

```java
String a = "a"; // "a"가 저장된 공간의 주소값이 a안에 담긴다.
String b = "b";	// "b"도 마찬가지이다.

// a + b는 "a"와 "b"가 더해지므로 "ab"가 된다.
// 그런데 여기서 a의 내용이 "a"에서 "ab"로 변경되는 것이 아니라 "ab"는 새로운 공간에 저장되고 그 주소값이 a에 담긴다.
a = a + b; // 즉, "a"는 그대로 존재하고 "ab"가 새로운 공간에 저장되어 그 주소값이 a로 담겨서, a안에 담긴 값이 기존의 "a"의 주소값에서 "ab"의 주소값으로 바뀌는 것이다.
```

# String클래스의 주요 메서드
|메서드|설명|
|---|---|
|char charAt(int index)|문자열에서 해당 위치(index)에 있는 문자를 반환한다.|
|int length()|문자열의 길이를 반환한다.|
|String substring(int from, int to)|문자열에서 해당범위(from~to)의 문자열을 반환한다.(**to는 포함 안 됨**, 마지막 범위의 문자는 포함 안 됨)|
|boolean equals(Object obj)|문자열의 내용이 같은지 확인한다. 같으면 결과는 true, 다르면 false|
|char[] toCharArray()|문자열을 문자배열(char[])로 변환해서 반환한다.|

```java
// charAt(int index)
String str = "ABCDE";
char ch = str.charAt(2); // 문자 하나를 받을 때는 char타입 변수에 담는다.
System.out.println(ch);  // C

// substring(int from, int to)
String str2 = str.substring(1, 4); // 만약 마지막 범위는 안쓰고 시작 범위만 쓰면 맨 마지막 순서의 문자가 범위가 된다.(str.substring(1) <- BCDE) 
System.out.println(str2); // BCD

```


# 커맨드 라인을 통해 입력받기
- 커맨드 라인에 입력한 값이 문자열 배열에 담겨서 전달된다.
- run configuration 또는 cmd창에서 입력 가능

```java
class Ex5_7 {
	public static void main(String[] args) {
		System.out.println("매개변수의 개수:"+args.length);
		for(int i=0;i< args.length;i++) {
			System.out.println("args[" + i + "] = \""+ args[i] + "\"");
		}
	}
}
```

# 2차원 배열
- 4행 3열의 2차원 배열 score를 생성
- 인덱스와 배열 형태를 제외하고 값을 저장하거나 출력하는 방식은 1차원 배열과 비슷함

```java
int[][] score = new int[4][3];
```
||||
|---|---|---|
|score[0][0]|score[0][1]|score[0][2]|
|score[1][0]|score[1][1]|score[1][2]|
|score[2][0]|score[2][1]|score[2][2]|
|score[3][0]|score[3][1]|score[3][2]|

# 2차원 배열의 초기화

- 2차원 배열의 생성과 초기화를 한 번에 하는 방식

```java
// 방법 1
int[][] arr = {{1, 2, 3}, {4, 5, 6}};

// 방법 2 <- 더 직관적이어서 추천
int[][] arr = {
									{1, 2, 3},
									{4, 5, 6}
							}
```

- 2차원 배열은 1차원 배열의 배열이다. 
- score안에는 배열의 주소값이 들어 있는데 그 배열은 score[0]~[3]까지의 주소값을 저장하고 있는 하나의 1차원 배열이다. 즉, score는 주소값을 가지고 있고 그 주소값의 1차원 배열은 다시 여러개의 공간을 구성하고 각각의 공간안에는 score[0]~[3]까지의 값들이 각각 들어있는 배열의 주소값이 저장되어 있다.

```java
int[][] score = {
										{100, 100, 100},  // score[0]
										{20, 20, 20},			// score[1]
										{30, 30, 30},			// score[2]
										{40, 40, 40}			// score[3]
								}
```

# Arrays 배열 다루기

## Arrays클래스는 클래스의 한 종류 (Math클래스처럼  관련 메서드를 모아놓은 것)

- 배열의 비교와 출력: toString(), equals() <- 자주 쓰이는 메서드
	- toString(): 괄호안에 배열 이름을 적으면 문자열로 반환한다. 2차원 배열일때는 deepToString()을 사용함.
	- equals(): 두 배열을 비교해서 같거나 다르면 boolean값을 출력한다. 2차원 배열일때는 deepEquals()를 사용함.
```java
		String[][] str2D = {{"aaa", "bbb"},{"AAA", "BBB"}};
		String[][] str2D2 = {{"aaa", "bbb"},{"AAA", "BBB"}};
		
		System.out.println(str2D == str2D2); // false, 참조변수 값 비교
		System.out.println(Arrays.deepEquals(str2D, str2D2)); // true, 실제 문자열 비교
		
```

<br>

- 배열의 복사: copyOf(), copyOfRange()
```java
int[] arr = {0, 1, 2, 3, 4};
int[] arr2 = Arrays.copyOf(arr, arr.length); // copyOf(복사할 배열 이름, 복사할 요소의 개수) [0, 1, 2, 3, 4]
int[] arr3 = Arrays.copyOf(arr, 3); // 앞에서부터 복사할 요소의 개수 만큼 출력 [0, 1, 2]
int[] arr4 = Arrays.copyOf(arr, 7); // 만약 요소의 개수보다 더 큰 수를 넣으면 나머지는 0이 출력 [0, 1, 2, 3, 4, 0, 0]
int[] arr5 = Arrays.copyOfRange(arr, 2, 4); // (arr, from, to) 마지막 to의 범위는 불포함 [2 ,3]
```
<br>

- 배열의 정렬: sort()
```java
int[] arr = {3, 2, 0, 1, 4};
Arrays.sort(arr); // 배열 arr을 오름차순으로 정렬한다.
System.out.println(Arrays.toString(arr)); // [0, 1, 2, 3, 4]
```

