## arguments
- 함수에 여러가지 정보를 담고있는 객체로 특히, 인자와 관련된 정보를 담고있음
- 함수안에서 사용할 수 있도록 그 이름이나 특성이 약속되어 있는 일종의 배열이나 배열은 아님
- 함수에는 arguments라는 변수에 담긴 숨겨진 유사 배열이 있고, 이 배열에는 함수를 호출할 때 입력한 인자가 담겨있음

#### 매개변수와 인자
```
function a(org){
  코드	
}
a(1);
```
> org : 매개변수(parameter) - 값이 들어가는 변수<br/>1 : 인자(arguments) - 그 변수의 들어가는 값

```
function sum(){
  var _sum = 0;    
  for(var i = 0; i < arguments.length; i++){
    document.write(i+' : '+arguments[i]+'<br />');
    _sum += arguments[i];
  }   
  return _sum;
}
document.write('result : ' + sum(1,2,3,4));
```
- 결과
```
0 : 1
1 : 2
2 : 3
3 : 4
result : 10
```
> 함수 sum은 인자로 전달된 값을 모두 더해서 리턴하는 함수이고, 인자에 대한 정의가 없다. 하지만 sum(1,2,3,4)로 4개의 인자를 sum으로 전달하고 있다.<br/>함수를 정의할때 인자가 몇개가 들어올지 몰라 인자에 대한 구현을 하지않았음에도 즉, __매개변수가 없어도 인자를 전달 할 수 있는 것은 arguments라는 특수한 배열이 있기 때문__ 이다.<br/>결국 arguments는 사용자가 전달한 인자들에 접근할수있으므로 인자(1,2,3,4)를 갖고있게되는 것이다. 그래서 입력값으로 전달한 값을 \_sum에 하나씩 더해서 리턴한 값으로 10을 리턴한다.

- `+= : a = 0 일때 a += 1은  a = a + 1 과 같다 (a에 1을 더한 후 다시 a에 넣음)`

- 과정
```
_sum += arguments[i]
_sum = _sum + arguments[0]
_sum = 0 + 1
_sum = 1

_sum = _sum + arguments[1]
_sum = 1 + 2
_sum = 3

_sum = _sum + arguments[2]
_sum = 3 + 3
_sum = 6

_sum = _sum + arguments[3]
_sum = 6 + 4
_sum = 10
```

## funtion.length
- 매개변수와 관련 된 두가지 수가 있음
  - arguments.length : 함수로 전달된 실제 인자의 수를 의미 (함수를 호출할때의 인자의 갯수)
  - 함수이름.length : 함수에 정의된 인자의 수를 의미 (함수의 매개변수 갯수)

```
function zero(){
  console.log(
    'zero.length', zero.length,
    'arguments', arguments.length
  );
}
zero();  // zero.length 0 arguments 0 
```
```
function one(arg1){
  console.log(
    'one.length', one.length,
    'arguments', arguments.length
  );
}
one('val1', 'val2');  // one.length 1 arguments 2 
```
```
function two(arg1, arg2){
  console.log(
    'two.length', two.length,
    'arguments', arguments.length
  );
}
two('val1');  // two.length 2 arguments 1
```
- 매개변수와 인자의 수가 같아야하는 작업을 할때 사용됨
