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
type	foo() {
	if (true)
		int bar = 1;
}\n
```

``` c
// good
type	foo() {
	if (true)
		int bar = 1;
}
```

#### 모든 라인의 끝엔 White Space가 없어야 한다.

#### 비어있는 라인은 2라인 이상 있으면 안된다.


## Comment
#### 모든 주석은 주석 문자('//') 뒤에 한 칸 띄어 써야 한다.
``` c
// bad
//
//bad
//
```

``` c
// good
//
// good
//
```

#### 모든 주석은 한가지 주석 문자('//')만 사용해야 한다.
``` c
// bad
/*
** Multiple Comments
*/
```

``` c
// good
//
// Multiple Comments
//
```


## File-and-Directory


## Header
### 모든 소스 파일에는 연관된 헤더 파일이 있어야 한다.

### 모든 헤더 파일에는 중복 참조를 방지하기 위해 다음과 같은 헤더 가드가 있어야 한다.
``` c
// <Project>_<Path)_<File>_H
// foo/src/bar/baz.h
#ifndef FOO_BAR_BAZ_H
#definzse FOO_BAR_BAZ_H
...
#endif
```

### 모든 인클루드는 파일의 시작에 작성한다.

### 사용하지 않은 헤더는 포함하지 않는다.


## Naming
### (General) 변수, 타입, 함수 이름은 제3자가 즉시 이해할 수 있는 약어로 작성한다. 단, 파일 이름은 가능한 상세하게 서술형으로 작성한다.

### (General) 변수, 타입, 함수 이름은 CamelCase 규칙을 사용한다.
```c
// bad
int dosomething();
```

```c
// good
int doSomething();
```

### (General) 이미 정의되어 있는 변수, 타입, 함수 이름은 사용하지 않는다. 단, 필요한 경우 앞에 'my_'를 붙인다.

### (File Name) 이미 존재하는 파일 이름은 사용하지 않는다.
> errorno.h  

### (File Naming) 파일 이름은 상세하게 적되, 전부 소문자로 작성한다. 필요한 경우 언더바('_')를 사용할 수 있다.


### (Directory) 디렉터리 이름은 모두 소문자로 작성한다. 필요한 경우 언더바('_')를 사용할 수 있다.

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


## Function


## Class
