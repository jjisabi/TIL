# `Array`

<br>

### 1. JavaScript Array 객체
<hr>

- JavaScript에서 배열은 크기 조정이 가능하고, 서로 다른 다양한 데이터 형식을 혼합해서 저장 가능하다.

- 배열의 크기는 동적으로 변경될 수 있다. (이미 할당된 값은 사라지지 않음)

- 변수 외에 객체와 함수도 저장 가능하다.

- JavaScript에서 배열은 `1) 배열 리터럴` `2) Array 생성자 함수` `3) Array.of()` `4) Array.from()` 를 통해 생성할 수 있다.

<br>

### 2. 배열 생성 
<hr>

#### 1. 배열 리터럴
가장 단순하고 직관적인 배열 생성
```
const a = [];
a[0] = 1;
a[1] = 2;
a[2] = 3;

const b = [,,,] //배열 크기 지정

const c = [1, 2, 3];
```
<br>

배열 리터럴 내부에서 Spread Syntax(스프레드 문법)을 사용하여 기존의 배열을 활용하여 새로운 배열 생성 가능
```
const a = [1, 2, 3];
const b = [4, 5, 6];
const c = [...a, ...b]; //[1, 2, 3, 4, 5, 6]
```
<br>

#### 2. Array() 생성자 함수
length 값을 인수로 전달받아 해당 길이의 배열 생성
```
const arr = new Array();
arr[0] = 1;
arr[1] = 2;
arr[2] = 3;

const a = new Array(10);
const b = Array(1, 2, 3); //new 연산자를 사용하지 않고 호출 가능
const c = new Array(0); //빈 배열 리터럴과 동일 ([])
```
<br>

#### 3. Array.of( )
전달된 인수를 요소로 갖는 배열 생성
```
const a = Array.of(1, 2, 'abc', {});  //[1, 2, 'abc' {}]
const b = Array.of(10); // [10]
const c = new Array(10) // [], c.length = 10
```
<br>

#### 4. Array.from( )
유사 배열 객체 또는 이터러블을 인수로 전달받아 배열 생성
```
const a = {length: 3, 0:1, 1:2, 2:3}; //유사 배열 객체
const b = Array.from(a); // [1, 2, 3]
const c = Array.from('abc') //['a', 'b', 'c']
```
<br>

### 3. 배열 메소드
<hr>

#### 1. forEach()
각 배열 요소에 대해 제공 된 함수를 오름차순 인덱스 순서로 한 번씩 실행하는 `순회 메소드`이다. 항상 undefined를 반환하므로 체이닝 할 수 없다.예외를 발생시키는 것 외에는 forEach()루프를 중단할 수 없다.
- 매개변수(parameter)<br>
    1) element : 배열에서 처리 중인 현재 요소<br>
    2) index : 배열에서 처리 중인 현재 요소의 인덱스<br>
    3) array : forEach()를 호출한 배열

- 구문
    ```
    forEach(callbackFn)
    forEach(callbackFn, thisArg)
    ```
- 예시
    ```
    const arr = ['a', 'b', 'c'];

    arr.forEach(element => console.log(element));

    const newArr = arr.forEach((currentElement, index, array) => {
        console.log("currentElement: " + currentElement);
        console.log("index: " + index);
        console.log("array: " + array);
    })
    ```
- 실행결과
  <img src="https://github.com/jjisabi/TIL/assets/158115388/98ce5a88-a2ea-4c96-bfa4-363961786d90">

<br>

#### 2. map()
배열 내의 모든 요소 각각에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 `반환`하는 `순회 메소드`이다. callback 함수를 **각각의 요소에 대해 한 번씩** 순서대로 불러 그 함수의 반환값으로 새로운 배열을 만든다. *값이 삭제되거나 아직 값이 할당/정의되지 않은 인덱스에 대해서는 호출되지 않는다.*

- 새로운 배열 반환 => 원하는 방식으로 변환 및 활용하고 싶을 때 사용할 수 있다.

- 매개변수(parameter)
    1) element: 처리할 현재 요소<br>
    2) index: 처리할 현재 요소의 인덱스<br>
    3) array: map()을 호출한 배열
    
- 반환 값: 배열의 각 요소에 대해 실행한 callback의 결과를 모은 새로운 배열

- 구문
    ```
    arr.map(callback(currentValue[, index[, array]])[, thisArg])
    ```

- 예시

    ```
    const arr = [1, 4, 9, 16];

    const map = arr.map(x => x * 2);
    console.log(map) // [2, 8, 18, 32]

    const newArr = arr.map((currentElement, index, array) => {
    console.log("currentElement: " + currentElement);
    console.log("index: " + index);
    console.log("array: " + array);

    return currentElement * 2;
    })

    console.log(newArr);
    ```

- 결과
  <img src="https://github.com/jjisabi/TIL/assets/158115388/72e4f784-3bf6-469d-9655-beae2a4bc2ce"> 

**마지막 줄에서 확인한 것처럼 map 메서드가 실행된 자리에 리턴되는 새로운 배열이 있다. (콜백 함수의 return 값을 통해 새로운 배열들의 각 요소를 변형 가능)**

<br>

#### 3. find()
제공된 배열에서 제공된 테스트 함수를 만족하는 첫 번째 요소(값)를 반환하는 순회 메서드이다. 만족하는 값이 없으면 `undefined`를 반환한다.

- 구문
    ```
    forEach(callbackFn)
    forEach(callbackFn, thisArg)
    ```

- 매개변수(parameter)<br>
    1) element: 현재 처리되고 있는 요소<br>
    2) index: 배열에서 현재 처리되고 있는 요소의 인덱스<br>
    3) array : find()가 호출된 배열

- 반환 값: 제공된 테스트 함수를 만족하는 배열의 첫 번째 요소(없다면 'undefined' 반환)
    ```
    const inventory = [
        { name: "apples", quantity: 2 },
        { name: "bananas", quantity: 0 },
        { name: "cherries", quantity: 5 },
      ];

    // 1) 함수 사용
    function isCherries(fruit){
        return fruit.name === "cherries"
    }
    console.log(inventory.find(isCherries));

    //2. 화살표 함수 및 구조 분해 사용
    const result = inventory.find(({ name }) => name === "cherries");
    console.log(result);
    ```
- 결과
  <img src="https://github.com/jjisabi/TIL/assets/158115388/049aee5a-c99d-443d-9e44-a52bc09a4752">

<br>

#### 4. findIndex()
- 배열에서 찾은 요소의 인덱스가 필요한 경우
- 구문
    ```
    forEach(callbackFn)
    forEach(callbackFn, thisArg)
    ```

- 매개변수(parameter) <br>
    1) element: 현재 처리되고 있는 요소<br>
    2) index: 배열에서 현재 처리되고 있는 요소의 인덱스<br>
    3) array: findIndex()가 호출된 배열

- 반환 값: 테스트를 통과하는 첫 번째 요소의 인덱스 (일치하는 요소가 없으면 `-1 반환`) 

- 예시
    ```
    const arr = [4, 6, 8, 8, 12]

    console.log(arr.findIndex((item) => item === 8))
    console.log(arr.findIndex((item) => item === 3))
    ```    
- 결과
  <img src="https://github.com/jjisabi/TIL/assets/158115388/c332f4c1-6111-4b97-91bf-c6aa5e675ed0">
<br>

#### 5. indexOf()
값의 인덱스를 찾아야 하는 경우 -> findIndex()와 유사하지만 테스트 함수를 사용하는 것 대신 각 요소가 값과 동일한 지 확인

- 구문
    ```
    forEach(callbackFn)
    forEach(callbackFn, thisArg)
    ```

- 매개변수(parameter)<br>
    1) searchElement: 배열에서 위치를 찾을 요소<br>
    2) fromIndex: 검색을 시작할 0 기반 인덱스(정수)<br>
    

- 반환 값: 테스트를 통과하는 첫 번째 요소의 인덱스 (일치하는 요소가 없으면 `-1 반환`) 

- 요소
    ```
    const array = [2, 9, 9];
    array.indexOf(2); // 0
    ```
<br>    

#### 6. includes()
배열의 항목에 특정 값이 포함되어 있는 지 판단하여 true, false 반환
- 배열에 값이 존재하는 지 찾아야 하는 경우 사용

- 구문
    ```
    includes(searchElement)
    includes(searchElement, fromIndex)
    ```

- 매개변수(parameter)<br>
    1) searchElement: 찾을 값<br>
    2) fromIndex: 검색을 시작할 0 기반 인덱스(정수)<br>

- 반환 값
배열 내에서 searchElement 값이 발견되면 true 불리언 값 반환

- 예시
    ```
    [1, 2, 3].includes(2); // true
    [1, 2, 3].includes(4); // false
    [1, 2, 3].includes(3, 3); // false - 검색 시작할 기반 인덱스가 더 큼
    [1, 2, 3].includes(3, -1); // true
    [1, 2, NaN].includes(NaN); // true -NaN 올바르게 검색
    ["1", "2", "3"].includes(3); // false - type 일치하지 않음
    ```
<br>    

#### 7. pop()
배열에서 마지막 요소를 제거하고 그 요소를 반환하는 메소드이다.

- 구문
    ```
    arr.pop();
    ```

- 매개변수(parameter)<br>
    elementN: 배열의 끝에 추가할 요소

- 반환 값: 호출한 배열의 새로운 length 속성 반환

- 예시
    ```
    var arr = ["가", "나", "다", "라"];

    var popped = arr.pop();

    console.log(arr); // ['가', '나', '다' ]

    console.log(popped); // '라'
    ```
<br>    

#### 8. push()
배열의 끝에 요소를 추가하고 새로운 배열의 길이를 반환한다.

- 구문
    ```
    arr.push(element1[, ...[, elementN]])
    ```

- 반환 값: 배열에서 제거한 요소. (빈 배열의 경우 undefined 를 반환.)

- 예시
    ```
    var sports = ["축구", "야구"];
    var total = sports.push("미식축구", "수영");

    console.log(sports); // ['축구', '야구', '미식축구', '수영']
    console.log(total); // 4
    ```    
<br>

#### 9. sort()
배열의 요소를 적절한 위치에 정렬한 후 해당 배열을 반환
- compareFunction 이 제공되지 않으면 요소를 문자열로 변환하여 비교 정렬한다. 숫자도 문자열로 변환되기 때문에 `1, 2, 11` -> `1, 11, 2` 으로 정렬 된다.
문자열 대신 숫자를 비교하기 위한 compare함수는 a에서 b를 뺄 수 있다.
   ```
    function compareNumbers(a,b){
        return a-b;
    }
    ```

- 구문
    ```
    arr.sort([compareFunction]);
    ```

- 반환 값: 정렬한 배열 (원 배열이 정렬 됨, 복사본 x)

- 예시
    ```
    const arr = [2, 11, 7, 1, 10];

    arr.sort(function (a, b) {
        return a - b;
    });

    console.log(arr) // [1, 2, 7, 10, 11]
    ```
<br>        



