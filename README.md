#11. 자바스크립트 서브셋과 확장


## 언어확장 ##
### 상수와 범위 변수 ###
#### 상수 ####
- 상수 선언 const 
- 유효범위는 var와 같고, 함수 최상단으로 끌어올려진다. (hoisted)
- 상수 선언 이후에 별도의 할당은 무시 한다.
- 상수를 재정의 하려하면, 에러를 발생시킨다.
- Javascript 1.5 이상에서 사용가능

```
const pi = 3.14; //상수정의
pi = 4; //무시
const pi = 4; //에러 발생.(상수 재정의)
var pi = 4; //에러 발생.(같은 이름 사용)
```

#### let ####
- 가장 가까운 블록 내에서, 그리고 중첩된 모든 하위 블록에서 유효하다.
- 우리가 평소에 쓰던 언어와 비슷한 유효범위
- 아직 표준은 아님
- Javascript 1.7 이상에서 가능.

```
function oddsums(n)
{
    let total = 0, result=[];
    for(let x = 1; x <= n; x++)
    {
        let odd = 2 * x - 1;
        total += odd;
        result.push(total);
    }
    console.log("total =", total);
    //console.log("add = ", add); //Error
    return result;
}

oddsums(5);
```
```
o = {x:1, y:2};
for(let p in o) console.log(p);
for each(let v in o) console.log(v);
console.log(p); //Error
console.log(v); //Error
```
```
let x = 1;
for(let x = x + 1; x < 5; x++)
    console.log(x);
{
   let x = x + 1; //x는 undefined 이기 때문에, x는 NaN이다.
   console.log(x); //NaN을 출력한다.
}
```
```
let x=1, y=2;
let (x=x+1, y=x+2)
{
    console.log(x+y); //print 5
};
console.log(x+y); //print 3
```
```
let x=1, y=2;
console.log(let (x=x+1, y=x+2) x+y); // print 5
console.log(x+y); // print 3
```

#### 해체할당 ####
- 등호의 오른쪽에서 하나 이상의 값이 추출('해체')되어, 등호의 왼쪽에 지정된 변수로 저장된다.

```
//배열 사용
let [x,y] = [1,2]; // let x=1, y=2
[x,y] = [x+1, y+1]; // x=x+1, y=y+1
[x,y] = [y,x]; // chage value
console.log([x,y]); // print [3,2]
```
```
// [x,y] 좌표를 [r, theta] 극좌표로 변환.
function polar(x,y)
{
    return [Math.sqrt(x*x + y*y), Math.atan2(y,x)];
}

//극좌표를 데카르트 좌표계로 변환.
function cartesian(r, theta)
{
    return [r * Math.cos(theta), r * Math.sin(theta)];
}

let [r,theta] = polar(1.0, 1.0);
let [x,y] = cartesian(r,theta);
```
