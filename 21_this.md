## this
- 함수 내에서 함수 호출 맥락(context)을 의미
  - 맥락 : 상황에 따라서 달라진다는 의미
- 가변적으로 함수를 어떻게 호출하느냐에 따라 가리키는 대상이 달라짐

## 함수호출
- 함수안에 this는 그 함수가 소속된 객체를 가르킴
```
function func(){
  if(window === this){
    document.write("window === this");
  }
}

func(); 
```
- 결과
```
window === this 출력 즉, window === this는 true
```
> this는 전역객체인 window와 같다.

## 메소드의 호출
- 객체의 소속인 메소드의 this는 그 객체를 가르킴
```
var o = {
  func : function(){
    if(o === this){
      document.write("o === this");
    }
  }
}

o.func();
```
- 결과
```
o === this 출력 즉, o === this는 true
```


## 생성자의 호출
- 생성자를 호출하면 생성자의 this는 생성자의 객체를 가르킴
```
var funcThis = null; 
 
function Func(){
  funcThis = this;
}

var o1 = Func();  // window
if(funcThis === window){
  document.write('window <br />');
}
 
var o2 = new Func();  // o2
if(funcThis === o2){
  document.write('o2 <br />');
}
```
> 일반함수(o1)를 호출했을 때와 new를 이용해서 생성자(o2)를 호출했을 때의 차이<br/>
funcThis = this;는 var가 없기때문에 위에 전역변수 var funcThis = null;를 가르킴 그리고 그 안에 this가 담김 즉, var funcThis = this 가 됨<br/>함수를 호출하면 함수의 this 는 window를 가르키고 생성자는 빈 객체를 생성하게되고 이 객체내에서 this는 만들어진 객체를 가르킴

- 생성자가 실행되기 전까지는 객체는 변수에도 할당될 수 없다. 즉, 생성자에대한 호출이 모두 끝난다음에야 비로소 o2 라는 변수안에 생성된 객체가 할당이 된다. 객체는 만들어져있지만 실제로 할당이 되지않기때문에 그전에 참조할 수 없다.<br/>
그런데 this는 객체의 초기화가 끝나서 어떤 식별자에 담기기전에 우리가 객체를 참고할수있는 레퍼런스이므로 this가 아니면 객체에 대한 어떠한 작업을 할 수 없다.
```
function Func(){
  document.write(o);
}

var o = new Func();  // undefined
```


## apply, call
- 함수의 메소드인 apply, call을 이용하면 this의 값을 제어할 수 있음
```
var o = {}
var p = {}

function func(){
  switch(this){
    case o:
      document.write('o<br />');
  break;
    case p:
      document.write('p<br />');
  break;
    case window:
      document.write('window<br />');
  break;          
  }
}

func();  // window
func.apply(o);  // o
func.apply(p);  // p
```
> 함수를 apply로 호출 시 어플라이 메소드의 첫번째 인자는 해당 객체의 this값이 되어 이를 이용하면 this의 값을 제어할 수 있다.

- `switch() : ()안에 값과 같은 case 안에 구간이 breack가 나올때까지 실행 (if와 대체됨)`

- `리터럴(Literal) : 편리하게 값을 만들 수 있는 문법적인 체계`