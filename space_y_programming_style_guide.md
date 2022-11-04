# SPACE Y C/C++ 코딩 스타일 가이드

SPACE Y의 구성원들을 위한 C/C++에 대한 코딩 스타일 가이드 입니다.
C/C++ 코드 작성 규칙(서식, 네이밍 규칙, 주석 등)과 Git 커밋 메세지 규칙을 포함하고 있습니다.(2022.10)

## 스타일 가이드의 목적

- 읽기 쉬운 코드
- 사람이 추가되어도 문제없이 진행할 수 있어야 함


## 목차
- [General] (#general)
- [Comment] 
- [File-and-Directory]
- [Header]
- [Naming]
- [Format]
- [Function]
- [Class]


## General
### Non-ASCII Character is Forbidden
#### 아스키 문자가 아닌 문자를 사용하지 않는다.

### No Empty File
#### 내용이 없는 빈 파일은 존재하면 안된다.

#### 파일의 마지막엔 아무것도 없어야 한다.
```c
// bad
type	foo(){
	if(true){
		int bar = 1;
	}
}\n
```
```c
// good
type	foo(){
	if(true){
		int bar = 1;
	}
}
```

#### 모든 라인의 끝엔 White Space가 없어야 한다.

#### 비어있는 라인은 2라인 이상 있으면 안된다.


## Comment
#### 모든 주석은 한가지 주석 문자('//')만 사용해야 한다.
```c
// bad
/*
** Multiple Comments
*/
```
```c
// good
//
// Multiple Comments
//
```

#### 모든 주석은 주석 문자('//') 뒤에 한 칸 띄어 써야 한다.
```c
// bad
//
//bad
//
```
```c
// good
//
// good
//
```

### 모든 주석은 영어로 작성해야 한다.

### 모든 파일의 시작 부분에는 파일 이름, 작성자, 파일 최초 작성일, 파일 수정 일자, 파일에 대한 간략한 설명이 있어야 한다.
```c
// ************************************************************************  //
//  FileName: example.c                                                      //
//  brief: list file header examples                                         //
//                                                                           //
//  Author: Lee-Sung-Ho                                                      //
//  Created: 2022/10/30                                                      //
//  Updated: 2022/11/05                                                      //
//  ***********************************************************************  //
```

### 모든 클래스는 그것이 무엇이고 어떻게 사용하는지 설명하는 주석을 가져야 한다.

### 모든 함수는 그것이 무엇이고 어떻게 동작하는지 설명하는 주석을 가져야 한다.

### 아직 완벽하지 않은 코드, 혹은 임시 해결책에는 TODO: 주석을 사용한다.
```c
...
notPerfectFunc(); // TODO: Implement function
... 
```


## File-and-Directory
### 파일 이름은 가능한 상세하게 서술형으로 작성한다.
### (File Name) 이미 존재하는 파일 이름은 사용하지 않는다.
> errorno.h  //bad

### (File Naming) 파일 이름은 상세하게 적되, 전부 소문자로 작성한다. 필요한 경우 대쉬('-')를 사용할 수 있다.

### (Directory) 디렉터리 이름은 모두 소문자로 작성한다. 필요한 경우 대쉬('-')를 사용할 수 있다.


## Header
### 모든 헤더 파일은 독립적이어야 한다.

### 모든 소스 파일에는 연관된 헤더 파일이 있어야 한다.

### 모든 헤더 파일에는 중복 참조를 방지하기 위해 다음과 같은 헤더 가드가 있어야 한다.
```c
// Header Guard Format: <Project>_<Path)_<File>_H
// example: foo/src/bar/baz.h
#ifndef FOO_BAR_BAZ_H
#define FOO_BAR_BAZ_H
...
#endif
```

### 모든 인클루드는 파일의 시작에 작성한다.

### 인클루드 헤더의 순서는 다음과 같고, 각 그룹은 하나의 빈 라인으로 구분한다. 단, 조건부 포함인 인클루드는 순서에 예외를 둔다.
> 1. 관련 헤더
> 2. 시스템 헤더
> 3. 표준 헤더
> 4. 기타 라이브러리 헤더
> 5. 프로젝트 헤더

### 사용하지 않은 헤더는 포함하지 않는다.

### 전방 선언은 사용하지 않는다.
```c
// bad
class A;

class B{
	A *a;	// Forward Declaration
}
```
```c
// bad
#include "a.h"

class B{
	A a;
}
```

### 10줄 이하의 함수만 인라인으로 정의한다.


## Naming
### (General) 변수, 타입, 함수 이름은 제3자가 즉시 이해할 수 있는 약어로 작성한다. 

### (General) 변수, 타입, 함수 이름은 lowerCamelCase 규칙을 사용한다.
```c
// bad
int Dosomething();
```
```c
// good
int doSomething();
```

### (General) 이미 정의되어 있는 변수, 타입, 함수 이름은 사용하지 않는다. 단, 필요한 경우 앞에 'my_'를 붙인다.

### (Type Name) 타입 이름은 대문자로 시작한다. 구조체, typedef, 열거형을 포함한 모든 타입에 대해 동일한 규칙이 적용된다.

### (Type Name) typedef의 경우 t_로 시작한다.

### (Variable Name) 변수 이름은 모두 소문자로 시작한다.

### (Variable Name) 전역변수의 이름은 g_로 시작한다.

### (Constant Name) 상수의 이름은 k_로 시작한다.

### (Function Name) 함수의 이름은 모두 소문자로 시작한다.

### (Function Name) 함수 실행 중 크래시가 발생할 수 있다면 함수의 이름 뒤에 'OrDie'를 붙인다.

### (Enum Name) 열거형의 이름은 e_로 시작한다.

### (Macro Naming) 매크로는 전부 대문자로 작성한다. 필요한 경우 언더바('_')를 사용할 수 있다.

### (Exception) 표준 함수를 구현하는 경우 해당 표준 문서 성의 표현과 통일성을 갖기 위해 문서 상에 정의된 이름/형태를 그대로 사용할 수 있다.

## Format
### 코드의 각 줄은 주석을 포함해 80자를 넘지 않아야 한다.

### 들여쓰기는 Tab만 사용하되, 그 크기는 2이다.

### 모든 연산자, 피연산자는 하나의 공백으로 구분해야 한다.
```c
// bad
int exampleVar=0;
```
```c
// good
int exampleVar = 0;
```

### 두개의 연속된 공백은 있으면 안된다.

### 함수, 선언문, 제어 구조 다음에 오는 중괄호의 뒤쪽에만 줄바꿈이 있어야 한다.
```c
// bad
if(true)
{
	doSomething();
}
```
```c
// good
if(true){
	doSomething();
}
```

### 조건문(if, while...)에는 한줄이어도 중괄호가 존재해야 한다.
```c
// bad
if(true)
	doSomething();
```
```c
// good
if(true){
	doSomething();
}
```

### 괄호 안에서는 space를 사용하지 않을 것을 권장한다.

### else if, else 키워드는 같은 라인에서 사용하되, 한칸 띄워쓴다.
```c
// bad
if(0 < condition < 1){
	doSomething();
}
else if(condition < 0){
	doSomethingElse1();
}
else{
	doSomethingElse2();
}
```
```c
// good
if(0 < condition < 1){
	doSomething();
} else if(condition < 0){
	doSomethingElse1();
} else{
	doSomethingElse2();
}
```

### 크기를 비교하는 조건문은 보기에 자연스러워야한다.
```c
// bad
if(1 > condition > 0){
	doSomething();
}
```
```c
// good
if(0 < condition < 1){
	doSomething();
}
```

### 포인터와 함께 쓰이는 별표('*')는 변수 이름에 붙어있어야한다.
```c
//bad
int* examplePointer;
```
```c
// good
int *examplePointer;
```

### 한 줄에 한개의 변수 선언만 가능하다.
```c
// bad
int currentValue, nextValue;
```
```c
// good
int	currentValue;
int	nextValue;
```

### 2줄 이상에 연달아 변수를 선언할 경우 같은 레벨로 들여쓰기 되어야 한다.
```c
// bad
int digit;
char *cvtDigit2Char;
```
```c
// good
int		digit;
char	*cvtDigit2Char;
```

### returrn값을 항상 표시하되, return 표현식을 괄호로 묶지 않아야 한다.
```c
// bad
void func(){
	doSomething();
	return ();
}

char func2(){
	char ret;
	ret = doSomethingElse();
	return (ret);
}
```
```c
// good
void func(){
	doSomething();
	return void;
}

char func2(){
	char ret;
	ret = doSomethingElse();
	return ret;
}
```

### 포인터의 접근자('.', '->') 좌우에는 스페이스를 사용하지 않는다.
```c
///bad
int temp = classA . memberElement;
```
```c
int temp = classA.memberElement;
```
## Function


## Class
