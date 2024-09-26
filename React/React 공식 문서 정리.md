# Describing the UI
## Your First Component
#### 목표
- What a component is
- React에서 component가 수행하는 역할
- component 작성 방법

#### component 정의 및 역할
component는 마크업을 뿌릴 수 있는 JavaScript함수이다. CSS, JavaScript를 사용자 정의 component로 결합하여 재사용 가능한 UI 요소를 반환하는 함수
프로젝트 크기가 커지면서 컴포넌트 재사용하여 개발 속도 높인다.

#### component 사용
import 한 후 component 태그를 작성하여 사용한다.
속성이 포함 된 태그 반환 (JSX 마크업 반환)  
HTML + JavaScript = JSX 구문 (JavaScript와 마크업을 함께 사용할 수 있다.)

1. Export the component
```
export default
```
2. Define the function (function 명은 항상 대문자)
```
function Profile() { … }
```
3. Add markup
```
return <> <img src="" /> </>
```

## Importing and Exporting Components
#### 목표
- Root Component 는 무엇인가
- component를 import/export 하는 방법
- 하나의 파일에서 여러 component를 가져오고 내보내는 방법
- component를 여러 파일로 분할하는 방법

#### The Root Component
Root Component는 애플리케이션의 최상위 컴포넌트. 
일반적으로 이 컴포넌트는 전체 애플리케이션의 구조와 상태를 관리하고, 다른 모든 컴포넌트를 포함한다.
React DOM의 render 메서드를 통해 HTML DOM에 렌더링된다. 
Root Component file은 Default로 App.js로 설정 

#### Exporting and importing a component
1. component를 넣을 새 JS 파일을 생성한다.
2. export: 해당 파일에서 component를 내보낸다.
3. import: component를 사용할 파일로 가져온다. 

#### Exporting and importing multiple components from the same file
- 1개 export
```
export default Button
import Button from ‘./….js/;
```

- 2개 이상 export
 ```
export: export Button1 , export Button2
import { Button1, Button2 } from ‘Button.js’;
```


## Writing Markup with JSX
#### 목표
- React가 마크업과 렌더링 로직을 혼합하는 이유
- JSX와 HTML 다른점
- JSX로 정보를 표시하는 방법

#### JSX: JavaScript에 마크업 추가
JSX는 JavaScript 파일 내에 HTML과 유사한 마크업 작성하는 구문
이전에는 콘텐츠(HTML), 디자인(CSS), 로직(JavaScript)으로 모두 별도로 작성하였으나 웹이 interactive해지면서 로직이 점점 컨텐츠에 영향을 미치게 됨  
-> 로직과 마크업이 함께 존재하는 JSX 구문으로 바뀜
이에 따라 **JavaScript 파일 내에 HTML과 같은 마크업을 작성하여 logic과 contents를 한 위치에 유지할 수 있다.**

#### HTML을 JSX로 변환
아래 3번항목 내용을 참고하여 변환

#### JSX 규칙
- 단일 루트 요소 반환
여러 요소를 반환하려면 단일 상위 태그로 (`<></>` 또는 `<div></div>`) 요소 래핑
(<></> : 해당 빈 태그를 fragment라고 한다. HTML 트리에 흔적 남기지 않는다.)
- 모든 태그를 닫는다. 
JSX에서 태그를 명시적으로 닫아야 한다. <img />
- CamelCase
속성명은 (-)나 예약어를 사용할 수 없다.(class가 예약어이므로 className으로 쓴다.)

## JavaScript in JSX with Curly Braces { }
#### 목표
- 따옴표로 문자열을 전달하는 방법
- 중괄호를 사용하여 JSX내에서 JavaScript 변수 참조/함수 호출/객체 사용 하는 방법

#### 따옴표로 문자열 전달하기
: 따옴표 안의 JSX 속성은 문자열로 전달 된다.
```
const description = 'Gregorio Y. Zara';
return <img alt = "description" />;
```

#### 중괄호 사용하기
: 중괄호를 사용하면 JavaScript logic과 변수를 마크업으로 가져올 수 있다.
1. 중괄호 사용 위치
- JSX 태그 내부의 텍스트로<br>
```
<h1>{name}'s To Do List</h1>
```
- (=) 기호 다음의 속성으로<br>
```
src={avatar}
```

2. JSX 태그 내부의 텍스트로
- 변수 참조<br>
```
const name = 'Gregorio Y. Zara';
<h1>{name}'s To Do List</h1>
```
- 함수 호출<br>
```
function formatDate(date) {...}
<h1>To Do List for {formatDate(today)}</h1>
```


3. 이중 중괄호 사용
객체 전달 시 이중 중괄호 사용<br>
```
person={{ name: "Hedy Lamarr", inventions: 5 }}
```

## Passing Props to a Component
#### 목표
- component에 props를 전달하는 방법
- component에서 props를 읽는 방법
- props의 기본값을 지정하는 방법
- 일부 JSX를 component에 전달하는 방법
- 시간이 지남에 따라 props 변경

React component는 props를 사용하여 서로 통신한다. 모든 상위 component는 props를 제공하여 하위 component에 정보를 전달할 수 있다. (객체, 배열, 함수 등)

#### Familiar props
props: JSX 태그에 전달하는 정보들로서 className, src, alt, width, height 등등

#### Passing props to a component
1. props를 component JSX에 전달
```
<Avatar
  person={{ name: 'Lin Lanying', imageId: '1bX5QH6' }}
  size={100}
/>
```

2. component에서 props 읽기
- 구조분해<br>
```
function Avatar ({ person, size }){...}
```

- 스프레드
```
function Avatar(props) {
 let person = props.person;
 let size = props.size ...
}
```

#### props 기본 값 설정
값이 지정되지 않았을 때 prop에 기본 값을 지정하려면 = 매개변수 바로 뒤에 기본 값을 넣어 구조 분해 수행할 수 있다.
```
function Avatar ({ person, size = 100 }) {...}
```


#### JSX 스프레드 구문을 사용하여 prop 전달
전달하는 props가 너무 많을 때 간략히 하기 위해 props로 전달하여 각 이름을 나열하지 않고 모든 props 전달 ( …props)
```	
function Profile(props) {
 return (
   <div className="card">
     <Avatar {...props} />
   </div>
 );
}
```

#### JSX 자식으로 전달
component가 nested 되었을 때, 상위 component는 하위 component의 children prop에서 content를 받는다. 
```
<Card><Avatar/></Card>

function Card({ children }){
  return (<div className="card">{children}</div>);
}
```

#### 시간이 지남에 따라 props 변경
**props는 불변성, 읽기 전용이므로 props 값 변경하지 말 것.**
component가 props를 변경해야 하는 경우 상위 component에 다른 props를 요청해야 한다.

## Conditional Rendering
#### 목표
- 조건에 따라 다른 JSX 반환 방법
- JSX를 조건부로 포함하거나 제외하는 방법
- 조건부 구문 단축키

#### 조건부로 JSX 반환
- if 조건절, 아무것도 반환 하지 않을 때 : null

#### 조건부로 JSX 포함
- 삼항 연산자(?:):  `{isPacked ? name + ' ✔' : name} `
- 논리 AND 연산자 (&&):  `{name} {isPacked && '✔'}`
조건에 맞으면 렌더링, 그렇지 않으면 아무것도 렌더링 하지 않음

#### 조건부로 JSX를 변수에 할당
```
<li className="item">
 {itemContent}
</li>
```

## Rendering Lists
목표
- map()을 이용하여 배열에서 component 렌더링 하는 방법
- filter()를 사용하여 특정 component만 렌더링 하는 방법
- key 사용하는 이유

#### 배열 데이터 렌더링
1. 데이터를 배열로 만든다.
2. 배열 데이터를 가져와 새 배열을 만든다. 
```
const listItems = people.map(person => <li>{person}</li>);
```
3. 해당 component를 반환한다.
```
return <ul>{listItems}</ul>;
```

#### 항목 배열 필터링
1. filter()함수 호출하여 조건에 맞는 새 배열 생성
```
const chemists = people.filter(person =>
person.profession === 'chemist');
```

2. map()함수로 JSX 구문에 돌린다.
```
const listItems = chemists.map(person =><p>known for {person.accomplishment}</p>);
```

3. component 반환한다.
```
return <ul>{listItems}</ul>;
```

#### key로 list 항목을 순서대로 유지
사용 이유: component가 어떤 배열 항목에 해당하는 지 알려주어 배열 항목이 삽입되거나 삭제 될 때 올바르게 업데이트 할 수 있다. Warning: Each child in a list should have a unique “key” prop. 오류 발생<br>
key는 
- database의 고유한 key/id 값 사용
- local에서 생성된 데이터 사용 (UUID 등)
- 고유한 값이어야 하며 변경되어서는 안된다.

## Keeping Components Pure
#### 목표
- 순수함수란 무엇이고, 버그를 방지하는데 어떻게 도움이 되는지
- 렌더링 단계에서 변경사항을 유지하여 component를 순수하게 유지하는 방법
- strict 모드를 사용하여 component의 실수를 찾는 방법

#### 순수성: 동일한 입력 시 동일한 출력 반환한다. 호출되기 전에 존재했던 객체나 변수는 변경되지 않는다. 
React는 모든 component가 순수 함수라고 가정한다. (component의 순수 함수: component가 동일한 입력이 주어지면 항상 동일한 JSX를 반환해야 한다.)

#### Side Effects
Component는 JSX만 반환해야 한다. 렌더링 전에 존재했던 객체나 변수를 변경하면 안된다.(지역변수 x)  -> Props로 전달 가능
```
let guest = 0;
function Cup(){ guest = guest + 1; return <h1>{guest}</h1> }
```

-> Props로 전달 가능
```
function Cup({ guest }) {  return <h1>{guest}</h1> }
export default function TeaSet() {  return <Cup guest={1} />  }
```

렌더링은 언제나 발생할 수 있으므로 component는 렌더링 순서에 의존하면 안된다. 

#### Side Effects를 일으키는 곳
렌더링 도중에 발생 X, 보통 event handler에서 발생한다. -> useEffect 사용

#### StrictMode로 순수하지않은 계산 감지
React에는 렌더링 하는 동안 세 가지 입력을 읽을 수 있다. (1.props 2.state 3.context)
component가 렌더링되는 동안 기존 변수나 객체를 변경하면 안된다. 
Strict 모드는 component를 두 번 호출하여 위의 규칙을 위반하는 component를 찾는다. `<React.StrictMode>`

-> componet는 렌더링에 사용하는 입력(props, state, context)를 변경해서는 안되고(순수 함수로 유지), 화면을 업데이트 하려면 기존 객체나 변수를 변경하는 대신 상태를 set한다. 

## Your UI as a Tree
#### 목표
- React가 component 구조를 보는 방법
- 렌더 트리는 무엇인 지
- 모듈 종속성 트리란 무엇인 지

#### UI를 트리로 표현
UI is often represented using tree structures. (Trees are a relationship model between items)
React tree는 데이터가 흐르는 방식과 렌더링 및 앱 크기를 최적화 하는 방법)

#### 렌더 트리
component 중첩하여 상위/하위 component가 생성 됨. 해당 관계를 모델링
트리는 노드로 구성되며 각 노드는 component를 나타낸다. 최상위 component는 루트 component이며 React가 첫 번째로 렌더링 하는 component이다. 조건부 렌더링을 사용하면 path가 달라 여러 렌더링에 걸쳐 다양하게 렌더링 할 수 있다. 

#### 모듈 종속성 트리
- React 앱의 모듈 종속성을 나타낸다: component와 로직을 별도의 파일로 분할하여 JS modules를 만들 수 있다. (component, function, constants를 export 할 수 있음)
- 트리를 구성하는 노드는 component가 아닌 모듈이다.
- 종속성 트리는 빌드 시 필요한 코드를 묶는데 사용된다.
- 종속성 트리는 페인팅 시간을 늦추고 번들로 묶인 코드를 최적화할 수 있으므로 대규모 번들 크기를 디버깅 하는데 유리하다.

# Adding Interactivity
## Responding to Events
#### 목표
- 이벤트 핸들러 작성하는 방법
- 상위 component에서 이벤트 전달하는 방법
- 이벤트 전파 및 중지 방법

#### 이벤트 핸들러 추가
1. component 내 버튼에서 handleClick() 함수를 선언한다.
2. 해당 함수 내부에 로직을 구현한다.
```
function handleClick() {  alert('You clicked me!');  }
```
3. 구현한 함수를 JSX에 추가한다.
```
onClick={handleClick}
```
(호출되지 않고 전달 되어야 한다. onClick={handleClick}  O /  onClick={handleClick()} X )

이벤트 핸들러에서 props 읽기
이벤트 핸들러는 component 내부에 선언되므로 component props에 액세스 할 수 있다. 
```
function AlertButton ({props1}){return (<button onClick={() => alert(props1}}/> )}
```

#### 이벤트 핸들러를 props로 전달하기
```
function Button({onClick}){return (<button onClick={onClick}></button>)}
```

```
function PlayButton(){
  function handlePlayClick() {  alert(`Playing !`); }
  return (<Button onClick={handlePlayClick}>Play Button</Button>);
}
```

#### 이벤트 핸들러 props 이름 지정
on+대문자로 시작 `onUploadImg`

#### 이벤트 전파
이벤트 핸들러는 모든 하위 항목에서도 이벤트를 포착하고, 발생한 곳에서 시작하여 트리 위로 올라간다. (bubbles)
- 전파 중지
		: 이벤트 핸들러는 이벤트 객체를 인수로 받고 이를 이용하여 중지한다. 
		`e.stopPropagation()`

- 핸들러 전달(전파의 대안)
전파로 관리하기 어려울 때 핸들러 전달로 대체

- 기본 동작 방지<br>
e.preventDefault(): `<form>`태그의 onSubmit 이벤트 시 전체 페이지 로드함<br>
e.stopPropagation() : 연결된 상위 이벤트 핸들러 실행 중지 (버블링 방지)<br>
e.preventDefault(): 브라우저의 기본 동작 방지<br>

#### 이벤트 핸들러 side Effect
이벤트 핸들러는 순수할 필요가 없으므로 side Effect가 발생하기 쉽다. 데이터 변경을 위해 state를 사용한다. 

## State: A Component’s Memory
#### 목표
- useState Hook을 사용하여 상태 변수를 추가하는 방법
- useState Hook이 반환하는 값 쌍
- 두 개 이상의  state 변수를 추가하는 방법
- state를 local로 부르는 이유

#### 일반 변수로는 충분하지 않은 경우
- 지역 변수는 렌더링 간에 유지 되지 않는다. 
react는 컴포넌트를 렌더링 할 때마다 초기 상태로 렌더링 됨
( -> 지역 변수 값이 변경되어도 저장되지 않고 초기값으로 돌아간다.)

- 지역 변수를 변경해도 렌더링이 트리거 되지 않는다. 
(react는 지역 변수 데이터가 바뀌어도 렌더링 되지 않는다.렌더링 대상이 아님)

- 새 데이터로 component를 업데이트하려면
렌더링 간 데이터 유지되어야 하고, React를 트리거하여 변경된 데이터로 component 렌더링해야 한다.

- useState Hook이 제공 하는 것
렌더링 간에 데이터를 유지하는 state 변수
변수를 업데이트하고 React를 트리거하여 component를 다시 렌더링 하는 state 설정 함수

#### state 변수 추가
1. 파일 상단에 useState 가져오기
```
import { useState } from ‘react’;
```
2. 상태 변수 선언
```
const [data, setData] = useState();
```
3. 이벤트 핸들러 연결
```
function handleClick() { setData(‘Hello’) };
```

- Hook: "use"로 시작하는 함수이며 렌더링되는 동안에만 사용할 수 있는 함수
- useState: component가 어떤 것을 기억하도록 알림
```
const [data, setData] = useState(초기값);
```
- data: 저장한 값이 포함된 state 변수
- setData: state 변수를 업데이트하고 React를 트리거하여 component를 다시 렌더링 할 수 있는 state를 설정하는 함수()

- state 동작 순서
1) component가 처음으로 렌더링 된다. (초기 값 기억)
2) state 업데이트 (setData(변경된 데이터 값))
3) component가 두 번째 렌더링 된다.

#### component에 여러 state 변수 제공 가능
#### state는 isolated, private 이다.
동일한 component를 두 번 렌더링 하면 각 복사본은 isolated 된 상태이다. 
(둘 중 하나를 변경해도 다른 하나에 영향을 미치지 않고 state가 별도로 저장된다.)

## Render and Commit
#### 목표
- 렌더링의 의미 이해
- component를 렌더링하는 시기와 이유
- 화면에 component를 표시하는 단계
- 렌더링이 항상 DOM 업데이트를 생성하지 않는 이유

#### 1단계: 렌더링 트리거
component가 렌더링 되는 경우
- component의 초기 렌더링
: 앱이 시작되면 초기 렌더링을 트리거 해야한다. root.render();
- component의 state가 업데이트 됨
: setState() 함수로 state값을 변경하여 추가 렌더링을 트리거 한다. 

#### 2단계: component 렌더링
렌더링을 트리거 한 후 React는 component를 호출하여 화면에 표시할 내용을 파악한다. 렌더링은 React가 component를 호출하는 것이다.
- 초기 렌더링 시 React는 루트 component를 호출/ DOM노드 생성
- 후속 렌더링 시 state가 업데이트 된 component 호출/ 초기 렌더링 이후 변경된 속성이 있는 지 계산

#### 3단계: DOM에 변경사항 commit
component를 호출(렌더링)한 후 React는 DOM 을 수정한다.
초기 렌더링의 경우 appendChild() DOM API를 사용하여 생성된 모든 DOM 노드를 화면에 배치한다.
재렌더링의 경우 필요한 필수 작업만 DOM에 적용
	(React는 렌더링 간에 차이가 있는 경우에만 DOM 노드 변경)

#### 브라우저 페인트
렌더링이 완료되고 React가 DOM을 업데이트 한 후 브라우저가 화면을 다시 칠한다. 

## State as a snapshot
#### 목표
- set state가 다시 렌더링을 트리거하는 방법
- state 업데이트 시기 및 방법
- state를 설정한 후 즉시 업데이트 되지 않는 이유
- 이벤트 핸들러가 state의 snapshot에 액세스 하는 방법

State는 snapshot처럼 동작/ 기존의 state가 변경되는 것이 아니라 대신 다시 렌더링이 트리거 된다.

#### state를 설정하면 렌더링이 트리거 된다.
이벤트 핸들러 실행 -> setData()가 설정됨 -> 새로운 state값에 따라 component 렌더링

#### 렌더링은 시간에 맞춰 snapshot을 찍는다.
렌더링은 React가 component 함수를 호출하는 것 의미하고 해당 component에서 반환하는 JSX는 시간에 따른 UI의 snapshot과 같다. (props, 이벤트 핸들러 등은 렌더링 당시의 state를 사용하여 계산된다.)

- React가 component를 다시 렌더링 할 때
1) React가 component 함수를 다시 호출
2) component 함수는 새로운 JSX 스냅샷을 반환한다.
3) React는 component함수가 반환한 스냅샷과 일치하도록 화면을 업데이트 한다.

#### 시간 경과에 따른 state
이벤트 핸들러가 비동기적이더라도 state의 값은 렌더링 내에서 절대 변경되지 않는다. 각 렌더의 상태 값은 고정되어 있다.

## Queueing a Series of State Updates
#### 목표
- batching이 무엇인지, React가 이를 사용하여 여러 state를 업데이트 처리 하는 방법
- 동일한 state변수에 여러 업데이트를 연속으로 적용하는 방법

#### React 배치 상태 업데이트
React는 state 업데이트를 처리하기 전에 이벤트 핸들러의 모든 코드가 실행될 때 까지 기다린다. 
-> component안의 코드가 완료될 때까지 UI가 업데이트 되지 않는다. (일괄 처리하여 너무 많은 재렌더링 방지)

#### 다음 렌더링 전에 동일한 state 변수를 여러 번 업데이트
다음 렌더링 전에 동일한 state 변수를 여러 번 업데이트 하고 싶을때 이전 queue에 기반한 다음의 함수를 전달할 수 있다. state 값을 바꾸는 대신 state로 무언가를 하도록 지시하는 방법이다.
```
setNumber(n => n + 1)
```

명명규칙
해당 state 변수의 첫 글자로 함수 인수 이름 지정
```
setEnabled(e => !e);
setLastName(ln => ln.reverse());
```

## Updating Objects in State
#### 목표
- React state에서 객체를 업데이트 하는 방법
- 중첩된 객체를 변경하지 않고 업데이트 하는 방법
- 불변성을 유지하는 방법
- Immer을 사용하여 객체 복사의 반복성을 줄이는 방법

State는 모든 JavaScript 값을 보유할 수 있으나 객체나 배열의 값을 직접 변경해서는 안된다. 
대신 새 객체를 생성하거나 기존 객체의 복사본을 만들어 사용해야 한다.

#### 가변

JavaScript에서 숫자, 문자열, boolean은 불변 값 -> state가 변경되나 원래 값 자체는 	변경되지 않는다. 객체는 가변값으로 원래 값 자체가 변경될 수 있다. (가변)
	-> 불변 데이터처럼 처리 해야 한다. 

#### state를 읽기 전용으로 처리
state에 넣은 모든 JavaScript 객체를 읽기 전용으로 처리해야 한다.
```
onPointerMove={e => {
 position.x = e.clientX;
 position.y = e.clientY;
}}
```

```
onPointerMove={e => {
 setPosition({
   x: e.clientX,
   y: e.clientY
 });
}}
```
-> 새 객체를 만들어 state 설정 함수에 전달한다. 
-> position이 새 객체로 변경, 해당 component를 다시 렌더링 함

#### 스프레드 구문(...)을 사용하여 객체 복사
객체의 하나의 필드만 업데이트 하고 다른 필드는 이전 값을 유지하려고 할 때 사용
-> 스프레드 구문은 얕은 복사! (한 수준 깊이의 항목만 복사, 중첩 객체에서 사용 X)
```
setPerson({
… person,
firstName: e.target.value
})
```


중첩객체 업데이트
새 객체 생성하여 업데이트
```
const [person, setPerson] = useState({
 name: 'Niki de Saint Phalle',
 artwork: {
   title: 'Blue Nana',
   city: 'Hamburg',
   image: 'https://i.imgur.com/Sd1AgUOm.jpg',
 }
});

setPerson({
…person,
name: ‘name1’,
artwork: {
…person.artwork,
city: ‘Seoul’
}
})
```

Immer 라이브러리를 사용하여 간결한 업데이트 로직 작성
```
updatePerson(draft => {
 draft.artwork.city = 'Lagos';
});
```

## Updating Arrays in State
#### 목표
- state에서 배열의 항목 추가, 제거, 변경하는 방법
- 배열 내부의 객체를 업데이트 하는 방법
- Immer를 사용하여 배열 복사의 반복성을 줄이는 방법

#### 가변성 없이 배열 업데이트
배열 업데이트 할 때마다 setState()함수에 새 배열을 생성하여 전달해야 한다. 
-> map(), filter()함수 사용 O / pop, push, shift 사용 X

1) 배열에 추가
```
setArtists( [ … artists, {id: nextId ++, name: name}] )  //spread(...) 구문 사용
```

2) 배열에서 제거
filter() 사용
```
setArtists ( artists.filter(a => a.id !== artist.id));  //원래 배열은 수정되지 않음
``` 

3) 배열 변환
```
const nextShapes = shapes.map(shape => {  //배열의 일부, 전체 항목 변경을 위해 map()으로 새 배열 생성
…shape, y: shape.y + 50;
})
```

4) 배열의 항목 바꾸기
```
const nextCounters = counters.map((c, i) => {  //map()함수의 두 번째 인수에서 인덱스를 받아 해당 인덱스의 값 변경
if (i === index) {
return c + 1;
}
```

5) 배열에 삽입
특정 위치에 값 삽입할 때 slice() 함수 사용
```
//1. 새 배열 생성
    const nextArtists = [
      ...artists.slice(0, insertAt),
      { id: nextId++, name: name },
      ...artists.slice(insertAt)
    ];

//2. setArtists에 새 배열 데이터 추가
    setArtists(nextArtists);
```

6) 배열에 대한 기타 변경
배열 복사 한 후 reverse(), sort() 메소드 사용

#### 배열 내부의 객체 업데이트
중첩된 상태 업데이트 시 업데이트 하려는 지점부터 최상위 수준까지 복사본을 만들어야 한다. 

#### Immer 사용하여 간결하게 업데이트
```
updateMyTodos(draft => {
 const artwork = draft.find(a => a.id === artworkId);
 artwork.seen = nextSeen;
});
```

# Managing State
## Reacting to Input with State
#### 목표
- 선언적 UI vs 명령적 UI
- component 가 가질 수 있는 다양한 시각적 state 생성하는 방법
- state 변경을 트리거 하는 방법

#### 선언적 UI vs 명령적 UI
명령적 UI는 구현하는 방법 상세히 지시
(UI를 명령적으로 조작할 시 모든 UI에 명령을 내려야 하므로 복잡한 시스템에서는 관리하기 어려워진다.)
-> 해당 문제를 해결하기 위해 React에서는 선언적 방법을 활용하며 UI를 직접 조작하지 않는다. 대신 보여주고 싶은 것을 State로 선언하여 UI를 업데이트 한다. 

#### 리액트에서 UI를 구현하는 과정 (선언적)
1) 상태 변수로 선언 할 component의 다양한 시각적 state 식별(입력, 비어있음, 제출 중, 성공, 실패 등)

2) state를 변경하는 트리거 결정
인간 입력(버튼 클릭, 필드 입력, 링크 탐색 등)/ 컴퓨터 입력(네트워크 응답 도착, 시간 초과 완료 등)
위와 같은 입력이 발생할 때, UI를 업데이트 하려면 설정한 state 값 변경해야 한다. 

3) useState를 사용하여 메모리의 상태를 표현한다. (상태 변수 선언)
* 꼭 필요한 가능한 적은 수의 state 사용
`const [ data, setData ] = useState(null);`

4) 필요하지 않은 상태 변수 제거
- 역설을 일으키는 state인가?
- 다른 상태 변수에서 동일한 정보를 사용할 수 있는가?
- 다른 상태 변수의 역으로부터 동일한 정보를 얻을 수 있는가?

5) 이벤트 핸들러를 연결하여 state 설정
```
const handleTextareaChange = (e) => { setData(e.target.value)};
onChange={handleTextareaChange}
```

## Choosing the State Structure
#### 목표
- single/multiple state 사용하는 경우
- state 구성할 때 피해야 할 것
- state structure 관련 된 일반적인 문제 해결하는 방법

#### structuring state(상태 구조화)의 원칙
* state를 가능한 단순하게 만들되, 필요한 state까지 단순하게는 X (데이터베이스 정규화 처럼)
1) 관련된 state를 그룹화(두 개 이상의 state 변수를 동시에 업데이트 한다면 단일 state 변수로 병합할 수 있는 지 확인)
2) state 모순 피하기
3) 중복 state 피하기(렌더링 하는 동안 다른 props나 state에서 뽑을 수 있는 값이면 state로 처리 x)
4) nested된 state 피하기(업데이트 하기 어려움)

#### structuring state 상세
1) Group related state
두 개 이상의 상태 변수가 항상 함께 변경되는 경우, 하나로 합쳐 단일 상태 변수로 만드는 것이 좋다.
```
const [x,setX] = useState(0);
const [y, setY] = useState(0);

const [position, setPosition] = useState({x:0, y:0});
```

#### Avoid contradictions in state
isSending, isSent는 동시에 true일 수 없으므로 하나의 state 변수로 처리

#### Avoid redundant state
렌더링 하는 동안 component의 props나 state 변수에서 어떤 데이터를 계산할 수 있다면 state에 포함하지 말아야 한다.
예시) fullName은 lastName + firstName으로 해결할 수 있으므로 state 변수로 작성하지 않음
```
const [lastName, setLastName] = useState('');
const [firstName, setFirstName] = useState('');
const [fullName, setFullName] = useState('');
```

#### Avoid duplication in state

#### Avoid deeply nested state
중첩된 객체와 배열을 사용하여 state 구조화 하는 방법 ("flat")
: 하위 객체/배열의 ID 배열을 저장하여 해당 ID로 매핑 한다. 객체 추가/삭제 시 ID배열에서 해당 ID만 제거하면 된다. (아니면 변경된 부분부터 객체의 복사본을 만들어야 하기 때문에 복잡)
```
export const initialTravelPlan = {
id: 0,
  title: '(Root)',
  childPlaces: [{
    id: 1,
    title: 'Earth',
    childPlaces: [{
      id: 2,
      title: 'Africa',
      childPlaces: [{
        id: 3,
        title: 'Botswana' …},
      id: 4,
      title: 'Europe',
      childPlaces: [{
        id: 5,
        title: 'Croatia',
        childPlaces: [],
      }....

// -> 데이터 조정:
export const initialTravelPlan = {
  0: {
    id: 0,
    title: '(Root)',
    childIds: [1, 42, 46],
  },
  1: {
    id: 1,
    title: 'Earth',
    childIds: [2, 10, 19, 26, 34]
  },
  2: {
    id: 2,
    title: 'Africa',
    childIds: [3, 4, 5, 6 , 7, 8, 9]
  }, 
```

객체 추가 삭제 시, childIds 배열에서 id 추가/삭제로 해결 가능



## Sharing State Between Components
#### 목표
- component 간에 state를 공유하는 방법(lifting up)
- controlled, uncontrolled component

두 개 이상의 component의 state가 같이 변경되기를 원할 때, 공통 상위 coponent로 옮기고 props로 state를 전달한다.(lifting state up)

#### lifting state up by example
1) 하위 component에서 state 변수 제거
```
const [isActive, setIsActive] = useState(false);

//제거 후, 인자에 상위 부모로부터 받을 props 추가
function Panel({ isActive }) {...
```

2) 공통 부모로부터 하드코딩 된 데이터 전달
```
<Panel isActive={true} />
```

3) 공통 부모에 state 추가, 이벤트 핸들러로 하위 component에 전달
```
const [activeIndex, setActiveIndex] = useState(0); (하위 component를 control 할 state 변수)
<Panel isActive={activeIndex === 0} onShow{() => setActiveIndex(0)} />
```

#### 각 state에 대한 single source
React에서 component는 자체 state를 가진다.

## Reserving and Resetting State
#### 목표
- React가 언제 상태를 유지하거나 재설정 하는지
- component의 state를 reset하는 방법
- key와 type이 state 유지에 영향을 미치는 방법

#### state는 렌더 트리 위치에 연결되어 있다. (React는 UI component 렌더링 트리 구축)
: state는 component가 아니라 react 내부에서 유지된다. React가 각 state를 가지고 있다가 각 state를 해당 렌더 트리 위치에 있는 component와 연결한다. 

#### React가 state 유지/재설정 할 때
동일한 위치에 동일한 component를 렌더링 하는 것은 state 유지(* 위치: JSX 마크업 위치가 아닌 UI 트리의 위치)
component를 제거하면 state도 삭제
동일한 위치에 component간 전환 (동일한 위치에서 component 변경 시 react 렌더 트리에서 기존 component state 제거/재설정)
재렌더링 사이에 state를 유지하려면 트리 구조가 일지해야 한다.

#### 동일한 위치에서 state reset 하는 방법
기본적으로 동일한 렌더트리 위치라면 state유지/ reset하려면
1) 다양한 위치에서 component 렌더링
   ```
      {isPlayerA &&
        <Counter person="Taylor" />
      }
      {!isPlayerA &&
        <Counter person="Sarah" />
      }
   ```

2) 위치가 같은 곳에서 reset 하려면 -> key 사용하여 component에 id 부여
   ```
      {isPlayerA ? (
        <Counter key="Taylor" person="Taylor" />
      ) : (
        <Counter key="Sarah" person="Sarah" />
      )}
   ```

3) 키를 사용하여 state reset ***

#### Summary
React는 동일한 컴포넌트가 동일한 렌더트리에 위치한다면 state유지
동일한 위치란 JSX태그가 아니라, JSX를 배치한 트리 위치와 연결
key를 제공하여 state를 강제로 reset 할수 있다.
component를 중첩하면 의도하지 않은 state reset이 발생할 수 있으므로 중첩X

## Extracting State Logic into a Reducer
#### 목표
- What a reducer function is
- reducer(useReducer)로 useState 리팩토링 하는 방법
- reducer가 필요한 경우
- reducer 잘 작성하는 방법

#### useState를 useReducer로 통합
- useReducer 사용 이유: useState로 상태 변수를 선언하고 이벤트 발생 시 state를 변경하는데 state를 변경하는 이벤트 핸들러가 많아질 수록 복잡해지기 때문
-> useReducer라고 하는 단일함수에서 처리

1) state를 set하는 것에서 action 전달로 변경
: 이벤트핸들러에서 변경 내용을 나열하는 것(setData)이 아니라, dispatch 객체로 action을 전달하여 방금 action을 지정한다. 
`dispatch({type: ‘added’})`

2) reducer 함수 작성
: reducer 함수 작성하여 action에 따른 state 로직 작성, 반환
2개의 인수 사용 (현재 state,action)
```
function reducer(state, action) {
  if(action.type === ‘added’) {
    return { …state, count:action.count + 1;}
  }
}
```
* 보통은 if/else문 보다 switch 문을 사용함
* state를 직접 바꾸면 안됨/  새 객체를 만들어서 바뀐 값만 바꿔야 함 (기존 state 얕은 복사)

3) component에서 reducer 사용
Reducer를 component에서 연결하기 위해 useReducer Hook 사용
useReducer 인수: 1) reducer function 명, 2) 초기 state 값
import { useReducer } from ‘react’;
const [state, dispatch] = useReducer(reducer, initialstate);

#### useState vs useReducer
일반적으로 useReducer를 구성하는 데에 필요한 코드가 useState보다 더 길기 때문에 이벤트 핸들러가 많거나 복잡할 때 사용, useState보다 가독성이 좋고 순수함수이므로 테스트 시에 유리하다.

#### reducer 잘 작성하기
- reducer는 순수함수로 작성
- 각 작업은 데이터에 여러 변경 사항이 발생하더라도 단일 사용자의 상호 작용을 나타낸다. 

#### Immer 라이브러리r로 reducer 간결하게 작성하기
state에서 객체나 배열처럼 Immer 라이브러리를 사용하여 argument를 변경하여 state를 변경 할 수 있다.

## Passing Data Deeply with context
#### 목표
- What prop drilling is
- 중복 prop들을 context로 대체하는 방법
- context 사용 사례
- context에 대한 대안

일반적으로 props를 통해서 상위 component에서 하위component로 전달한다. context를 사용하면 명시적으로 전달하지 않고도 하위 트리의 모든 component에서 props를 사용할 수 있다.

**Prop Drilling**: component 트리에서 데이터를 하위 컴포넌트로 전달하기 위해 중간 컴포넌트를 통해 prop을 전달하는 것

props를 전달하는 것에 대한 문제점: 트리 전체에 걸쳐 prop을 전달하거나 많은 component에 동일한 prop이 필요한 경우(중복 시) 코드가 복잡해짐, 공통 부모를 찾기 어려울 수 있음.

#### context: props의 대안
context 사용 시 하위 전체 트리에 props 데이터 제공 가능, 하위 component가 가장 가까운 상위 component를 찾을 수 있다.
1) context를 만든다.
```
import { createContext } from 'react';
export const LevelContext = createContext(1);
```

2) context 사용
- useContext Hook을 가져온다. 생성한 context를 import한다.
```
import { useContext } from ‘react’;
import { LevelContext } from ‘./LevelContext.js’;
```

- 기존 prop을 제거하고 방금 가져온 context에서 값을 읽는다.
```
const level = useContext(LevelContext);
```

3) context 제공
- 상위 컴포넌트를 context 제공자로 wrapping 한다.
* component는 <LevelContext.Provider>에서 가장 가까운 부모 값을 사용한다.

```
import { LevelContext } from './LevelContext.js';
export default function Section({ level, children }) {
 return (
   <section className="section">
     <LevelContext.Provider value={level}> 
       {children}
     </LevelContext.Provider>
   </section>
 );
}
```

#### context는 중간 component를 통과한다.
context를 제공하는 copmonet와 이를 사용하는 component 사이에 원하는 만큼 component를 추가 삽입할 수 있다. 

#### context 사용 전 고려해야 할 사항
- 기본적으로 props로 전달하는 것으로 사용하되 props가 너무 많거나 상위 component를 찾기 어려운 경우에 context 사용

- component를 추출하고 자식 요소로 JSX에 전달한다.

# context 사용 사례
- 테마 지정: dark, light mode에 따라 component 조정

- 로그인 된 현재 계정: 많은 component가 현재 로그인 된 사용자를 알아야 할 때 context에 넣으면 트리 어느곳에서나 편리하게 읽을 수 있다.

- 라우팅, 상태 관리 등

## Scaling Up with Reducer and Context
#### 목표
- reducer와 context 결합하는 방법
- state 전달을 피하고 props로 전달하는 방법
- context 및 state 로직을 별도의 파일로 추출하는 방법

reducer: 이벤트 핸들러로 state 변경하는 로직 통합하여 간결하게 유지
context: props를 다른 component에 전달 가능

#### reducer와 context 결합
reducer의 state와 dispatch 함수는 최상위 component에서만 사용할 수 있으므로 다른 component는 이벤트 핸들러를 props으로 전달해야 한다. 이때 context를 통해 모든 하위 component에서 반복적인 prop drilling없이 읽을 수 있다.

1) context 생성
```
const [state, dispatch] = useReducer(reducer, initialState);
```
2) context에 state와 dispatch 추가
```
 <TasksContext.Provider value={state}>
 <TasksDispatchContext.Provider value={dispatch}>
```
3) 하위 트리에서 context 사용

# Escape Hatches
## Referencing Values with Refs
목표
- component에 ref를 추가하는 방법
- ref 값을 업데이트 하는 방법
- ref가 state와 어떻게 다른지
- ref를 안전하게 사용하는 방법

Refs: 렌더링에 사용되지 않는 값을 보관하는데 사용, 렌더링 하는 동안 정보 유지

#### component에 ref 추가
- useRef Hook import한 후 component에서 호출한다. 초기 값을 인수로 전달한다.
```
import { useRef } from ‘react’;
const ref = useRef(0)
```

- useRef는 객체를 반환한다.
`{ current: 0 }`

- ref.current 속성
: 해당 속성을 통해 현재 값에 접근할 수 있다. React가 추적하지 않는다.
```
function MyComponent() { 
  const inputRef = useRef(null); 
  useEffect(() => { 
    inputRef.current.focus(); // inputRef의 current 속성을 사용하여 DOM 노드에 접근할 수 있음
  }, []); 
  return <input ref={inputRef} type="text" />; 
}
```

- state처럼 문자열, 객체, 함수 등을 가리킬 수 있다. state와 다르게 ref는 읽고 수정할 수 있는 current 속성을 가진 JavaScript 객체이다.

- state를 설정하면 component가 다시 렌더링 되는 반면 ref를 변경 시 렌더링 되지않는다. 다시 렌더링하여 화면에 표시할 필요 없는 경우 ref를 사용하는 것이 효율적


#### refs와 state 차이점
- Ref
```
useRef(initialValue) returns { current: initialValue }
```
변경할 때 재렌더링 X
current 값 변경 가능 (렌더링 없이)
렌더링 하는 동안 current 값을 읽거나 쓰면 안됨. 렌더링 하는 동안 값이 필요하다면 state를 사용해야 한다. 

- State
```
useState(initialValue) returns ([value, setValue])
```
변경 시 재렌더링 O
변경 불가능(값을 변경하려면 setValue() 함수 사용해야 함)
언제든지 state를 읽을 수 있다. 

#### refs 사용하는 경우
- 변경 값을 component에 출력하지 않아도 되는 경우
- JSX를 계산하는 데 필요하지 않은 다른 객체
- DOM 요소에 접근하여 저장 및 조작

## Manipulating the DOM with Refs
#### 목표
- ref 속성을 사용하여 React가 관리하는 DOM 노드에 접근하는 방법
- ref JSX 속성이 HOOK useRef 와 어떻게 연관이 있는지
- 다른 component의 DOM 노드에 접근하는 방법
- DOM을 수정하는 것이 안전한 경우

React에서 관리하는 DOM 요소에 접근해야 할 때 refs 사용(노드에 초점, 스크롤, 크기/위치 측정 등)

#### 노드에 대한 참조 얻기(React가 관리하는 DOM 노드에 접근하기 위해)
- useRef Hook을 가져와 component 내부에 ref를 선언한다.
```
import { useRef } from ‘react’;
const myRef = useRef(null);
```

- DOM 노드를 가져오려는 JSX 태그에 ref속성으로 참조를 전달한다.
`<div ref={myRef}>`  (myRef를 전달하여 myRef.current에 DOM을 넣는다)

- useRef는 current 객체를 반환한다. (React가 DOM 노드를 만들면 current 객체에 reference를 전달하므로 이벤트 핸들러에서 이 노드에 접근할 수 있다.)
```
myRef.current.scrollIntoView();
myRef.current.focus()
```

#### 다른 component의 DOM 노드에 접근
- forwardRef 속성을 사용하여 DOM 노드에 접근한다. forwardRef를 사용하여 선언된 컴포넌트는 부모로부터 ref를 전달받을 수 있다.
```
const MyInput = forwardRef((props, ref) => {
  return <input {...props} ref={ref} />;
});
```
- React의 업데이트
1) 렌더링 하는 동안 component 호출하여 화면에 표시할 것 파악 
2) 커밋 하는 동안 DOM에 변경사항 적용
Refs는 일반적으로 이벤트 핸들러에서 접근 (렌더링 중에 접근 x)

3. refs를 사용한 DOM 조작의 모범 사례
일반적으로 focus(), 스크롤 위치 관리, 브라우저 API 호출 등 React에서 관리하는 DOM 노드를 변경하지 않아야 한다. 

## Synchronizing with Effects
#### 목표
- Effects는 무엇인가? Effect가 event와 다른 점
- component에서 Effect를 선언하는 방법
- Effect 재실행을 건너뛰는 방법
- Effect가 두 번 실행되는 이유와 이를 수정하는 방법

React state를 기반으로 React가 아닌 component를 제어, 서버 연결 설정 등의 외부 시스템과 동기화해야 할 때 Effect 사용

#### What Effects are
렌더링 코드는 순수, 이벤트 핸들러는 side effect 포함
Effects는 component 안에서 데이터 가져오기, 외부 라이브러리 연동, 수동으로 DOM 조작 등의 작업 시 사용된다. 
useEffect 훅은 Side Effect를 지정할 수 있는 훅.
interaction으로 발생하는 event와 달리 Effect는 렌더링 자체로 발생한다. 
Effect를 사용하면 component를 외부 API, 네트워크 등과 동기화 할 수 있다. 

#### Effect를 사용하는 방법
1) Effect 선언: useEffect Hook을 가져온다.
```
import { useEffect } from ‘react’;
```
2) component 최상위 수준에서 useEffect hook을 호출하고 내부에 코드를 넣는다.
```
function MyComponent() {
	useEffect(() => {...}) return <div/>
}
```
컴포넌트가 렌더링 될 때마다 화면을 업데이트 한 다음 useEffect내부 코드를 실행한다. (useEffect는 렌더링이 화면에 반영될 때까지 지연된다.)

3) Effect dependencies를 지정한다. 
기본적으로 Effect는 모든 렌더링 후에 실행된다. 모든 렌더링마다 호출하고 싶지 않을 때 Effect의 두 번째 인수인 의존성배열을 빈 배열로 추가한다. 
```
useEffect(() => {
 // 모든 렌더링 후에 실행된다. 
});


useEffect(() => {
 // 처음 mount 될때만 실행된다. (component가 나타날 때)
}, []);


useEffect(() => {
 // mount 될때와 a,b 의 값이 변했을 때 실행된다. 
}, [a, b]);
```

모든 의존성 배열 값이 마지막 렌더링 시와 같은 값이면 (변하지 않았다면) Effect를 건너뛴다.

4) cleanup 함수 사용하여 정리 추가
connect-> disconnect/ subscribe -> unsubscribe/ fetch -> cancle,ignore

cleanup 함수: useEffect의 콜백 함수가 반환하는 함수, 다음 useEffect 호출 전에 실행되어 타이머나 인터벌 등의 리소스의 정리(clean-up)나 이벤트 핸들러의 제거 등을 할 수 있다. component가 마운트 해제 될때 코드가 Effect가 다시 실행되기 전에 정리하는 함수를 호출한다. 

#### Effect가 두 번 실행되는 이유와 처리 방법
- Strict Mode에서 React가 개발 버전에서는 버그를 찾기위해 의도적으로 component를 두 번 마운트한다. 

- 해결방법: Effect를 다시 마운트한 후 작동하도록 수정하는 방법 o 
Effect를 한 번 실행하는 방법 x

-> cleanup 함수 구현
UI 위젯: 두 번 호출해도 일이 일어나지 않는 UI 위젯은 clean up 함수 불필요
일부 API는 두 번 연속 호출 허용하지 않으므로 clean up 함수 필요
이벤트: removeEventlistener()로 정리 필요
애니메이션: 애니메이션을 초기값으로 재설정 필요
데이터 fetch: fetch 중단 필요
```
useEffect(() => {
let ignore = false;
const json = await fetchTodos();
if(!ignore) {setTodos(json)}
 return () => {  ignore = true; };
})
```

## You Might Not Need an Effect
#### 목표
- component에서 불필요한 Effects 제거하는 이유, 방법
- Effects 없이 비용이 많이 드는 계산을 캐시하는 방법
- Effects 없이 component state를 재설정하고 조정하는 방법
- 이벤트 핸들러 간에 logic 공유하는 방법
- 어떤 logic을 이벤트 핸들러로 옮겨야하는 지
- 부모 component에 변경 사항을 알리는 방법

#### 불필요한 Effects를 제거하는 방법
Effects가 필요하지 않는 경우
- 외부 API, 네트워크 등과 관련되지 않은 경우(state를 업데이트 하려는 경우)
- 렌더링 중에 계산할 수 있는 경우(state나 props로 처리)
- 사용자 이벤트를 처리하는 경우
(사용자 이벤트는 주로 사용자의 인터랙션에 반응하여 동작하고 이는 React의 상태 업데이트를 직접적으로 발생시키므로 Effects 필요 없음)

#### 비용이 많이 드는 계산 캐싱
- 비용이 많이 드는 코드 예시
 ```
 const [visibleTodos, setVisibleTodos] = useState([]);
 useEffect(() => {
   setVisibleTodos(getFilteredTodos(todos, filter));
 }, [todos, filter]);
```

- state, effect 제거/ 비용이 많이 드는 계산에 useMemo Hook wrapping

useMemo: 주로 계산 비용이 큰 연산의 결과를 캐싱하고, 의존성이 변경될 때만 다시 계산하여 리렌더링을 방지하는 데 사용된다. (성능 최적화)
useMemo의 첫 번째 인자로는 계산을 수행하는 함수를 전달, 두 번째 인자로는 의존성 배열을 전달

```
const visibleTodos = getFilteredTodos(todos, filter);

const visibleTodos = useMemo(() => {
   return getFilteredTodos(todos, filter);
 }, [todos, filter]);
```

####  Effects 없이 component state를 재설정하고 조정하는 방법
props가 변경 될 때 모든 state 재설정
key prop을 사용하여 component의 인스턴스를 관리한다. 같은 key가 유지되면 React는 기존 component를 재사용하지만, key가 변경되면 React는 새로운 component 인스턴스를 생성한다. 이를 활용하여 prop이 변경될 때 component를 새로운 것으로 처리하여 모든 state를 재설정할 수 있다.

```
function ExampleComponent({ keyProp }) { 
  const [state1, setState1] = useState(null); 
  const [state2, setState2] = useState('');

  return ( <div key={keyProp}>

  <p>State 1: {state1}</p> 
  <p>State 2: {state2}</p> </div> );
}
```

props가 변경 될 때 일부 state 재설정

#### 이벤트 핸들러 간에 logic 공유하는 방법
렌더링이 필요한 코드는 Effect에서 사용, 여러 component의 state를 업데이트 해야 하는 경우 단일 이벤트 중에 처리

## Lifecycle of Reactive Effects
#### 목표
- Effects의 수명 주기가 component의 Lifecycle과 다른 점
- 각 개별 Effects를 고립적으로 생각하는 방법
- Effects가 재동기화되어야 하는 경우와 그 이유
- Effects의 의존성이 결정되는 방식
- 값이 반응적이라는 것은 무엇을 의미하는 지
- 빈 의존성 배열이 의미하는 것
  
component는 mount, unmount, update의 수명주기
Effects는 동기화, 동기화 중지

#### Effects의 Lifecycle
Effect는 주변 component와 별도의 Lifecycle을 갖는다. component가 mount 될 때 실행(반응형 값에 따라 여러 번 동기화 시작 및 중지 가능성)
Effects는 외부 시스템을 동기화하는 방법이며 의존성 값이 변경되고 코드가 변경됨에 따라 동기화가 더/덜 발생할 수 있다.
동기/비동기 처리: useEffect 내에서 비동기 작업을 수행
의존성 배열: 의존성 배열을 사용하여 특정 상태나 프로퍼티의 변경에 반응하여 동기화 발생
클린업: useEffect 훅이 반환하는 함수를 통해 클린업 작업을 정의할 수 있으며, 컴포넌트가 사라질 때 실행된다.

#### Effects가 재동기화되어야 하는 경우와 방법
재동기화: 특정 의존성이 변경될 때 해당 useEffect 훅이 다시 실행되는 것
이유: 의존성 배열의 변경, if 조건부 로직 존재, 비동기적 state 변경(state 변경 시 재렌더링 되기 때문)
방법: 의존성 배열 명시, 배열 변경 시 재동기화/ clean up 함수 호출, 다시 connection/ component 언마운트 후 다시 mount

#### Effects의 의존성이 결정되는 방식
변할 수 있는 값인 props 전달 받음
Effect가 해당 props를 읽는다.
props가 변경 사항이 있을 때 Effect가 동기화된다. 
각 Effects는 별개의 독립적인 동기화 프로세스를 나타내야 한다. (분할)
반응형 값
component 본문에 선언된 모든 변수는 반응형이다.

```
function ChatRoom({ roomId, selectedServerUrl }) { 
  const settings = useContext(SettingsContext); 
  const serverUrl = selectedServerUrl ?? settings.defaultServerUrl;

  useEffect(() => {
    const connection = createConnection(serverUrl, roomId);
    connection.connect();
    return () => {
      connection.disconnect();
    };
  }, [roomId, serverUrl]);
}
```
-> 변수: roomId, selectedServerUrl, settings, serverUrl 
컴포넌트 내부에 선언된 props, state 및 기타 값은 렌더링 중에 계산되고 React 데이터 흐름에 영향을 미치므로 반응형이다. component 본문 내부에 선언된 모든 렌더링 중 값이 변하는 변수(state, props 뿐 만 아니라)는 반응형이다. 
모든 반응형 값은 재렌더링 시 변경될 수 있으므로 의존성에 포함되어야 한다. 렌더링으로 인해 변경되지 않는 props는 의존성 필요 x

#### 빈 의존성 배열이 있는 Effect의 의미
반응형 값을 사용하지 않으며 component가 마운트 될때 한 번만 effect 실행되고 다시 실행되지 않는다.  component가 unmount 될 때 연결이 끊어짐

#### React가 linter를 사용하여 의존성이 올바른지 확인한다.
linter에 동기화하고 싶지 않을 때는
1) component 밖으로 해당 값 이동 2) Effect 내부로 이동

## Separating Events from Effects
#### 목표
- 이벤트 핸들러와 Effect 중에서 선택
- Effect가 반응형이고 이벤트 핸들러가 반응형이 아닌 이유
- Effect 코드의 일부가 반응하지 않게 하려는 경우
- Effect Events 정의, Effect에서 Events를 추출하는 방법
- Effect Events를 사용하여 Effects에서 최신 props 및 state를 읽는 방법
  
#### 이벤트 핸들러와 Effect
- 이벤트 핸들러: 특정 상호작용에 대한 응답(버튼 누를때만 동작), 항상 수동으로 트리거 됨
- Effect: 동기화가 필요할 때 실행 됨 (state, props 등 반응형 값이 변경되었을때), 자동으로 필요할 때 실행 됨

#### Effect가 반응형이고 이벤트 핸들러가 반응형이 아닌 이유
- 이벤트 핸들러 로직은 상호작용을 수행하지 않는 한 다시 실행 x, 변경사항에 반응하지 않음
- Effects는 반응형 값을 읽는 경우 의존성 배열에 지정해야 하고 해당 값이 변경 되면 새 값으로 Effect의 로직을 다시 실행하므로 반응형

#### Effect 코드의 일부를 비반응형으로 사용하려고 할때
반응형 logic과 비반응형 logic을 섞으려면 특수 Hook useEffectEvent을 사용한다.
```
 const onConnected = useEffectEvent(() => {
   showNotification('Connected!', theme);
 });


 useEffect(() => {
   const connection = createConnection(serverUrl, roomId);
   connection.on('connected', () => {
     onConnected();
   });
   connection.connect();
 }, [roomId]);
```

useEffectEvent 는 의존성에서 제외해야 한다.

#### Effect Events를 사용하여 Effects에서 최신 props 및 state를 읽는 방법
Effects 자체는 반응형으로 유지, 내부 코드에서 useEffectEvent() 호출하여 useEffectEvent() 코드를 실행시키고 props와 state를 얻는다. 
Effects 내부에서만 호출해야 함, 다른 component나 Hook에 전달 x

## Removing Effect Dependencies
#### 목표
- 무한 Effect 의존성 loop 수정하는 방법
- 의존성 제거 방법
- 객체 및 함수 의존성을 피하는 방법과 이유
- 의존성 linter를 억제하는 것이 위험한 이유와 해결책

#### Effect가 무한 루프 발생하는 경우와 수정하는 방법
빈 배열로 의존성 배열을 설정한 경우 -> 적절한 의존성 추가, 특정 조건이 충족될 때만 useEffect를 실행하도록 조건문을 추가
useEffect 내부에서 상태를 업데이트하고, 이 업데이트가 useEffect의 의존성으로 설정되어 있어서 자기 자신을 다시 트리거하는 경우
-> useEffect 내에서 상태를 업데이트할 때, 해당 상태가 useEffect의 의존성으로 설정되어 있지 않도록 함

#### 의존성 제거 방법
- 고려해야 할 점
: Effect가 아닌 이벤트 핸들러에서 사용해야 하는 지
: Effect가 서로 관련 없는 여러 가지 작업을 하는 지 -> 두 개의 Effect로 나눔
: Effect 내부에서 set함수 읽고 있는 지 -> updater 함수 사용

의존성 배열에 선언하지 않으려면 반응형 값을 component에서 제외한 후 전역에서 선언한다. Effect가 반응형 값에 의존하지 않으므로 component의 props나 state가 변경될 때 다시 실행할 필요 없다. 

#### 객체 및 함수 의존성을 피하는 방법과 이유
- 의존성 배열에 객체: 객체의 어떤 속성이 변경되었을 때, 객체 전체가 변경된 것으로 인식하여 새 객체가 처음부터 다시 생성된다.
- 의존성 배열에 함수: 함수는 매번 새로운 참조를 가지기 때문에, 함수를 useEffect의 종속성으로 설정하면 매번 useEffect가 실행될 수 있다.
-> 필요이상으로 재동기화 된다.

해결: 
1) 객체, 함수 component외부로 이동하여 반응형 값으로 포함하지 않음
2) prop에 의존하여 외부로 이동할 수 없는 경우 Effect내부로 이동
```
function avg(a, b) {
   const sum = a + b
   return sum / 2;
}
```

                 input1
                           \
		    avg()
                           /
                 input2
                 
3) props에서 객체를 받아서 읽음
   
## Reusing Logic with Custom Hooks
#### 목표
- 사용자 정의 hook 작성 방법
- component 간 logic 재사용 방법
- 사용자 정의 hook 사용하는 시기와 이유

#### 사용자 정의 hook
component 간의 중복 logic이 있을 경우 재사용하여 중복 제거, 선언형으로 구현 됨
(하는 방법보다 무엇을 하려는 지 의도 설명)
한 Hook에서 다른 Hook으로 반응형 값을 전달할 수 있으며 해당 값은 최신 상태로 유지된다.
사용자 정의 Hook은 state 자체가 아니라 state logic만 공유한다.
모든 Hooks는 컴포넌트가 다시 렌더링될 때마다 다시 실행된다.

작성방법
1) hook 명명규칙: ‘use’로 시작, ‘use’ 후 대문자로 시작
`function useOnlineStatus() {...}`
2) hook안에 logic 작성 후 호출

사용자 정의 hook을 사용하는 경우
- 여러 컴포넌트에서 비슷한 상태와 동작을 필요로 할 때
- 특정 상태에 따라 다양한 UI를 표시해야 할 때
- 반복되는 logic이지만, 의존성 배열이 달라 effect를 분리하는 것이 옳을 때
- 마이그레이션, 리팩토링





