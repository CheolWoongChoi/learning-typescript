## 8. 함수 조합의 원리와 응용

### 8-1 함수형 프로그래밍이란?
- 함수형 프로그래밍
  - 순수 함수와 선언형 프로그래밍 토대 위에 함수 조합과 모나드 조합으로 코드를 설계하고 구현하는 기법
  - Q. 리액트에는 어떻게 적용할 수 있을까?
  

### 8-3 고차 함수와 커리
  - 애리티(arity)
    - 함수에서 매개변수의 개수
  - 부분 적용함수
    - 부분 적용함수 (partially applied function) 또는 부분 함수(partial function)이라고 함
    
  - 이전의 고차 함수 예제 (98p)
    - ver1의 코드를 보면 이해하기가 쉽지 않다.
  ```typescript
    // ver1
    const add = (a: number): (number) => number => (b: number): number => a + b
  
    // ver2
    type NumberToNumberFunc = (number) => number;
    
    const add = (a: number): NumberToNumberFunc => {
      const _add: NumberToNumberFunc = (b: number): number => {
        return a + b; // 클로저
      }
    
      return _add;
    }
  ```
  
 ### 8-4 함수 조합
  - Array.prototype.reduce()
  ```typescript
    arr.reduce(callback, [initialValue]);
    
    // callback form
    function(acc, curValue, curIdx, array) {
      // logic
    }
    
    
  ```
  
  - compose.ts 코드 에러? (189p)
  
  - 함수 매개변수에 매개변수명이 없고, 타입만 있어서 에러가 난다. 책에 전반적으로 오류가 있는 듯.
  
  - compose 함수와 pipe 함수의 차이 (193p)
    - compose는 인자의 오른쪽부터 왼쪽으로, 전달된 함수들이 차례로 실행
    - pipe는 인자의 왼쪽부터 오른쪽으로, 전달된 함수들이 차례로 실행
    - pipe와 달리 compose는 순수함수 조건을 만족해서, 
    내부에서 함수들을 담은 배열을 새로운 배열에 담는데 굳이 이렇게 처리해야 하나? 
    그리고 pipe 함수는 함수형 프로그래밍에서 쓰이는 방식이 아닌가? 
    맞다면 compose처럼 새로운 배열에 담지 않는 지? 
 
 
  
## 9. 람다 라이브러리

### 9-3
  - 209p의 R.pipe 인자에 3개의 인수가 들어가면 오류 발생
  
  - 포인트가 있는 함수와 포인트가 없는 함수
  ```typescript
    // point O
    const inc = (b: number): number => R.add(1)(b)
    
    // point X
    const inc = R.add(1)
  
  ```
  
  - 214p ~ 215p가 전형적인 함수형 프로그래밍 예제인듯

### 9-4
  - currying을 쓰는 이유가 직관적으로 보이기 위해서? (선언적 프로그래밍 의미)
  - 
  


