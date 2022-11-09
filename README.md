<!-- 객체 -->
#객체와 프로퍼티
-객체(Object) '자바스크립트의 모든것이 다 객체다!'
-{
    brandName: '코드잇',
    bornYear: 2017,
    isVeryNice: true,
    worstCourse: null
}   key(값 이름): value(값)
-key(값 이름): value(값) 한쌍 = 속성(Property)
-Property Name : Property Value 라고도 부른다.
-Property Name = 문자열(string) 따옴표를 생략하고 작성한다.
-Property Name 주의사항
1. 첫번째 글자는 반드시 문자, 밑줄(_), 달러기호($) 중 하나로 시작!
2. 띄어쓰기 금지!
3. 하이픈(-) 금지! 
이 조건을 벗어나는 경우엔 반드시 따옴표로 감싸주어야한다.
ex) 객체안에 프로퍼티를 만들 때 : 'born Year': 2017,
    새로운 프로퍼티를 추가할 때 : object['default value'] = "기본값";
-Property Value = 모든 자료형을 사용할 수 있다.
-객체안에 객체를 넣는것도 가능하다.

#객체에서 데이터 접근하기
-객체를 다루기 위해서는 변수에 할당해주면서 이름을 만들어주어야한다.
*객체의 프로퍼티에 접근하기 위한 방법.
-점 표기법 (objectName.propertyName)
ex) console.log(codeit.bornYear);
-대괄호 표기법 (objectName['property name'])
-객체안의 객체에 접근하는 방법
ex) console.log(codeit.bestCourse.title);

#객체 다루기
-객체의 프로퍼티 수정하기
let codeit = {
    name: '코드잇',
    bornYear: 2017,
    isVeryNice: true,
    worstCourse: null,
    bestCourse: {
        title: '자바스크립트 프로그래밍 기초',
        language: 'JavaScript'
    }
};
codeit.name = 'codeit';

-객체의 프로퍼티 추가하기
codeit.ceo = '강영훈';
-객체의 프로퍼티 삭제하기
delete codeit.worstCourse;
-객체의 프로퍼티 존재여부 확인하기
1. console.log(codeit.name !== undefined);
2. 'propertyName' in object
console.log('name' in codeit);

#객체와 메소드
-객체의 프로퍼티에는 어떤 자료형이든 저장할 수 있기 때문에 프로퍼티 값으로 함수를 넣어줄 있고, 이런 함수를 객체의 메소드(Method)라고 한다.
-파라미터가 필요한 경우라면 소괄호 안에 파라미터를 적고, 메소드를 호출할때 파라미터로 값을 전달해주면된다.
-메소드 : 어떤 객체의 고유한 동작으로서, 함수의 의미를 부여할 수 있다.
메소드를 활용하면 다른 함수와의 중복을 피할수도 있고, 좀 더 객체에 집중해서 함수의 동작부분을 작성할 수 있다.

#for...in 반복문
-객체안에 있는 프로퍼티들을 가지고 반복적인 동작을 수행할 떄 사용한다.
-객체의 프로퍼티 네임을 가져오는 반복문이기 때문에 일반적인 for문으로는 대체할 수 없는 특별한 반복문이다.
for (변수 in 객체) {
    동작부분
}
-객체의 프로퍼티 네임이 변수에 할당되고, 객체의 프로퍼티 갯수만큼 반복 동작을 하게된다.
for (let k in codeit) {
    console.log(k);
}
-for...in문의 변수는 말그대로 임의의 변수이다. (아무렇게나 정해도됨.)

-숫자형(양수) 프로퍼티 네임 
let myObject = {
    300: '정수',
    1.2: '소수',
};
프로퍼티 네임에는 숫자형(양수)을 작성해서 사용할 수도 있다. 
실제로 사용될 때는 문자열로 형 변환이 되어 사용된다.
이렇게 예외적인 파라티머 네임은 접근할 때도 대괄효 표기법으로만 접근이 가능하다.
console.log(myObject['300']);
console.log(myObject['1.2']);
console.log(myObject.300); // Error!
console.log(myObject.1.2); // Error!

-정수형 프로퍼티 네임
객체는 정수형 프로퍼티 네임을 오름차순으로 먼저 정렬하고, 나머지 프로퍼티들은 추가한 순서대로 정렬하는 특징이 있다.
let myObject = {
  '3': '정수3',
  name: 'codeit',
  '1': '정수1',
  birthDay: '2017.5.17',
  '2': '정수2',
};

for (let key in myObject) {
  console.log(key);
}

1
2
3
name
birthDay

#Date 객체
-내장 객체 (Standard built-in objects) = 자바스크립트가 미리 가지고 있는 객체.
-자바스크립트는 특별한 기능별로 다양한 내장 객체들이 존재한다.
-자바스크립트에서 날짜는 모두 Date 객체로 다룬다.
let myDate = new Date();
console.log(myDate);
이 객체를 생성한 순간의 시간이 출력된다.
-Thu May 18 2017 00:00:00 GMT+0900 (대한민국 표준시)
 요일 월 일 년도   시간        시간대
-new Date(특정한 값);
우리가 원하는 날짜를 생성할 수도 있다.
-// new Date(milliseconds)
let myDate = new Date(1000);
1970년 1월 1일 00:00:00 UTC + 1000밀리초!(1초)
-만약 2017년 5월 18일 객체를 만들고 싶다면
// new Date('YYYY-MM-DD')
let myDate = new Date('2017-05-18');
-좀 더 자세하게 시간까지 다루고 싶다면
// new Date('YYYY-MM-DDThh:mm:ss')
let myDate = new Date('2017-05-18T19:11:16');
-소괄호안에 여러개의 값을 전달해주는 방식 
new Date(값, 값, 값 ...);
new Date(YYYY, MM, DD, hh, mm, ss, ms);
년도와 월까지는 필수, 나머지는 생략이 가능하다.
생략할 경우에는 new Date(YYYY, MM, 1, 0, 0, 0, 0); 로 처리된다.
-한가지 주의할점 = month 값은 0부터 시작한다.
-// Date.getTime()
let myDate = new Date(2017, 5, 18, 19, 11, 16);
console.log(myDate.getTime());
myDate 객체가 1970년 1월 1일 00:00:00 UTC부터 몇 밀리초 지났는지를 계산해준다. = 이 정수 값을 타임스탬프(time stamp)라고 부른다.
-요일은 일요일부터 0~6까지 값이 있다.

-Date 객체 정보 수정하기
set으로 시작하는 다양한 메서드를 활용하면, 생성된 Date객체의 정보를 수정할 수도 있다.
*setFullYear(year, [month], [date])
*setMonth(month, [date])
*setDate(date)
*setHours(hour, [min], [sec], [ms])
*setMinutes(min, [sec], [ms])
*setSeconds(sec, [ms])
*setMilliseconds(ms)
*setTime(milliseconds)(1970년 1월 1일 00:00:00 UTC부터 밀리초 이후를 나타내는 날짜를 설정)
ex) let myDate = new Date(2017, 4, 18, 19, 11, 16);

    myDate.setFullYear(2002);
    myDate.setMonth(6);
    myDate.setDate(20);

-간단하게 시간 정보 알아내기
let myDate = new Date();

console.log(myDate.toLocaleDateString()); // myDate가 가진 날짜에 대한 정보 (년. 월. 일)
console.log(myDate.toLocaleTimeString()); // myDate가 가진 시간에 대한 정보 (시:분:초)
console.log(myDate.toLocaleString()); // myDate가 가진 날짜와 시간에 대한 정보 (년. 월. 일 시:분:초)
toLocaleDateString(), toLocaleTimeString(), toLocaleString() 메소드는 사용자의 브라우저에 설정된 국가의 표기에 맞춰 날짜와 시간을 보여준다. 

-똑똑한 Date
Date 객체엔 자동으로 날짜를 수정해주는 유용한 기능이 있다. 
범위를 벗어나는 값을 설정하려고 하면 자동으로 날짜를 수정해준다.
let myDate = new Date(1988, 0, 32); // 1988년 1월 32일은 없다.

// 2월 1일로 자동고침 되는걸 확인할 수 있다.
console.log(myDate) // Mon Feb 01 1988 00:00:00

-지금 이 순간..!?
Date.now() 메소드는 이 메소드가 호출된 시점의 타임스탬프를 반환한다. 이렇게 하면 새로운 객체를 만들지 않아도 바로 현 시점의 날짜 값을 얻어낼 수 있는 것!
let myDate = new Date();

console.log(Date.now() === myDate.getTime()); // true

새로운 객체를 만들어서 getTime 메소드를 호출한 값과 일치한다는 사실을 확인할 수 있는데,
새로운 객체를 만들지 않는다는 점은 일단 우리 눈에 코드 한 줄을 줄일 수 있다는 이점도 있고, 눈에는 드러나지 않지만 코드가 실행될 때 메모리의 부담을 줄여주기도 한다.
그래서 특정한 시점이 아니라 단순히 순간순간 그 때 당시 시간 값이 필요한 경우에는 Date.now() 메소드를 활용하는 것이 코드의 가독성 뿐만아니라 성능적인 측면에서도 좀 더 유리하다.

-Date객체의 형변환
let myDate = new Date(2017, 4, 18);

console.log(typeof myDate); // object
console.log(String(myDate)); // Thu May 18 2017 00:00:00 GMT+0900 (Korean Standard Time)
console.log(Number(myDate)); // 1495033200000
console.log(Boolean(myDate)); // true

Date 객체를 number 타입으로 반환할 경우 이 값은 getTime() 메소드를 활용한 것과 똑같은 수치의 타임스탬프 값이다. Date 객체끼리 사칙 연산도 충분히 가능하다는 뜻.
let myDate1 = new Date(2017, 4, 18);
let myDate2 = new Date(2017, 4, 19);

let timeDiff = myDate2 - myDate1;
console.log(timeDiff); // 86400000 (ms)
console.log(timeDiff / 1000); // 86400 (sec)
console.log(timeDiff / 1000 / 60) // 1440 (min)
console.log(timeDiff / 1000 / 60 / 60) // 24 (hour)
console.log(timeDiff / 1000 / 60 / 60 / 24) // 1 (date)

-날짜를 표현하는 문자열
YYYY-MM-DDThh:mm:ss형식 말고도 날짜를 표현하는 다양한 방식의 문자열이 있다.
let date1 = new Date('12/15/1999 05:25:30');
let date2 = new Date('December 15, 1999 05:25:30');
let date3 = new Date('Dec 15 1999 05:25:30');
하지만 이런 방식을 사용하다보면 브라우저나, 컴퓨터를 사용하는 위치의 시간대에 따라 서로 다른 결과 값이 나올 수도 있기 때문에 적어도 IETF 호환 RFC 2822 타임스탬프와 ISO8601의 한 버전의 형식을 준수하는 문자열로 Date 객체를 생성하는 것을 권장한다.

<!-- 배열 -->
#배열
-배열 안에 있는 값들은 요소(Element)라고 부른다.
-대괄호안의 각 요소들로 순서를 알려주는 숫자가 매겨진다. 숫자 -> index == propertyName
-배열의 요소를 가져오는 방법 console.log(배열이름[index]); -> indexing (0~...)
-순서가 있는 여러값들의 묶음, 여러 값의 묶음 등등

#배열 다루기
-배열도 객체이다. type = object
-length = 배열이 가지고 있는 요소의 총 갯수를 표시해준다. 
 console.log(배열.length); console.log(배열.['length']); -> 대괄호 표시법도 사용가능하다.
length - 1을 해서 배열의 마지막 요소에 접근할 수 있다. console.log(배열[배열.length - 1]);
-배열 수정하기 -> 존재하지 않는 요소에 접근해서 새로운 값을 할당해주게 되면 배열의 요소가 추가되고, 이미 존재하는 요소에 접근해서 값을 할당하면 요소의 값이 수정된다.
배열[5] = '수정하기';
-배열이 5개인데 7번째 값을 추가하면 6번째 값은 empty라는 하나의 요소로 추가되고 배열의 length도 7로 늘어난다.

#배열 메소드
-배열을 안전하고 효과적으로 사용하기 위해서는 배열의 메소드를 사용해야한다.
-splice -> 배열을 삭제하는 메소드 ex) 배열.splice(1);
-splice 메소드의 파라미터로 값을 하나만 전달하게되면 전달된 인덱스로부터 그 이후의 모든 요소를 삭제하게된다.
-splice 메소드의 두번째 파라미터로 숫자값을 하나 더 전달해주면 삭제할 갯수를 정할 수 있다. 
ex) 배열.splice(startIndex, deleteCount);
-splice 메소드의 세번째 파라미터는 값을 전달하게 되면 삭제한 요소 자리에 그 값이 추가된다.
ex) 배열.splice(startIndex, deleteCount, item);
-삭제할 갯수를 0으로 만들어주면 아무것도 삭제하지 않고 새로운 값을 추가할 수 있다.
ex) 배열.splice(1, 0, 'item', 'item2');
-삭제할 갯수를 하나만 정해서 요소를 수정할 수 있다. 여러개로 정하면 여러개의 요소를 수정하는것도 가능하다.
ex) 배열.splice(2, 1, 'item');

#배열 메소드2
// 배열의 첫 요소를 삭제 : shift()
배열.shift();
// 배열의 마지막 요소를 삭제 : pop()
배열.pop();
// 배열의 첫 요소로 값 추가 : unshift(value)
배열.unshift('value');
// 배열의 마지막 요소로 값 추가 : push(value)
배열.push('value');
 
#배열에서 특정 값 찾기 (indexOf / lastIndexOf)
-배열에서 특정 값을 찾으려면 indexOf 메소드를 사용하면 된다. array.indexOf(item)을 하면 array 배열에 item이 포함되어 있는지 확인할 수 있다.

1.만약 포함되어 있다면, item이 있는 인덱스가 리턴된다.
2.포함되어 있지 않다면, -1이 리턴된다.
3.여러 번 포함되어 있으면, 처음 발견된 인덱스가 리턴된다.

-lastIndexOf -> indexOf와는 반대로 탐색을 뒤에서 부터 하게 된다.

#배열에서 특정 값이 있는지 확인하기(includes)
-includes -> 그 값이 배열안에 있는지, 그 여부만 확인하고 싶을 때 사용한다.
array.includes(item)을 하게되면 array배열에 item이 있을 경우 true를, 없을 경우 false를 리턴한다.

#배열 뒤집기 (reverse)
-reverse라는 메소드를 활용하면, 배열의 순서를 뒤집을 수도 있다.

#for...of 반복문
-for...in 문은 변수에 배열의 프로퍼티 네임이 할당됐었는데, for...of문은 변수에 배열의 요소가 할당된다.
for (let 변수 of 배열) {
    동작부분;
}

#다차원 배열 (multidimesional array)
-다차원 배열 -> 배열안에 배열이 들어가는 형태
-배열안의 배열의 요소 접근하기 console.log(배열[0][1]);
-여러가지 값들의 순서나 위치에 중점을 둔 정보가 필요하다면 다차원 배열을 활용할 수 있다.

<!-- 자료형 심화 -->
#다양한 숫자 표기법
-let millionaire = 1000000000; === let myNumber = 1e9; // 지수 표기법
-지수 표기법은 컴퓨터 뿐만 아니라 과학, 공학, 수학처럼 숫자를 다루는 다양한 분야에서 아주 큰 수나 작은 수를 표기하는 방법 중 하나이다.
-알파벳 e 오른쪽 값이 음수가 되면 이 숫자만큼 10의 거듭제곱으로 나누라는 의미이다. -> (-9.1e-5 === -0.000091);
// 숫자 표기법
// 16진법 (Hexadecimal)
let hex1 = 0xff; // 255
let hex2 = 0xFF; // 255
// 8진법 (Octal)
let octal = 0o377; // 255
// 2진법 (binary numeral system)
let binary = 0b11111111; // 255

#숫자형 메소드
// Number
let myNumber = 0.3591;

// toFixed(0 ~ 100)
-소수를 다룰 때 사용하는 메소드. 파라미터로 숫자값을 전달해주면 그만큼 소숫점 아래의 자릿수를 고정해주는 메소드이다.
console.log(myNumber.toFixed(3));
-파라미터로 전달하는 값이 숫자값의 자릿수를 초과하게되면 0으로 대체된다.
-주의해야할점 -> toFixed 메소드를 사용해 계산된 값은 문자열이다. 
-이 메소드로 수정된 값을 숫자로 사용하고 싶을때는 number 함수를 이용해서 숫자로 형변환을 해줘야한다.
console.log(typeof Number(myNumber.toFixed(3)));
-자바스크립트에서는 어떤 값 앞에 +기호를 붙여주면 number 함수와 똑같은 결과를 얻을수 있다.
console.log(+myNumber.toFixed(3));

// toString(2 ~ 36)
let myNumber = 0.3591;

console.log(myNumber.toString(2)); -> 11111111
console.log(myNumber.toString(8)); -> 377
console.log(myNumber.toString(16)); -> ff
-결과값은 문자열이다.

-숫자형 메소드를 사용할 때 주의해야할 점 : 숫자에 바로 메소드를 사용할 수도 있는데, 숫자를 그냥 적으면 에러가 발생한다.
정수에 바로 점을 찍게되면 소숫점으로 인식하기 때문. 
-> 정수 형태의 숫자 값에는 메소드를 사용할 때  
1.반드시 점 두개를 사용하거나, 255..
2.양 옆을 괄호()로 감싸준다.

#Math 객체
-절댓값 (Absolute Number) : 어떤 값의 '양수(positive number)' 버전.
console.log(Math.abs(-10)); -> 10
console.log(Math.abs(10)); -> 10

-최댓값 (Maximum) : Math.max 함수에 파라미터로 여러 수를 넘겨주면, 그중 가장 큰 값이 리턴된다.
console.log(Math.max(2, -1, 4, 5, 0)); -> 5

-최솟값 (Minimum) : Math.min 함수에 파라미터로 여러 수를 넘겨주면, 그중 가장 작은 값이 리턴된다.
console.log(Math.min(2, -1, 4, 5, 0)); -> -1

-거듭제곱 (Exponentiation) : 자바스크립트에서 Math.pow(x, y)를 하면 x의 y승의 결괏값이 리턴된다.
console.log(Math.pow(2, 3)); -> 8
console.log(Math.pow(5, 2)); -> 25

-제곱근 (Square Root) : Math.sqrt(x)를 하면 x의 제곱근이 리턴된다.
console.log(Math.sqrt(25)); -> 5
console.log(Math.sqrt(49)); -> 7

-반올림 (Round) : Math.round(x)를 하면 x의 반올림된 값이 리턴된다. 소수점 부분이 0.5 이상이면 가장 가까운 정숫값으로 올라가고, 소수점 부분이 0.5 미만이면 가장 가까운 정숫값으로 내려간다.
console.log(Math.round(2.3)); -> 2
console.log(Math.round(2.4)); -> 2
console.log(Math.round(2.49)); -> 2
console.log(Math.round(2.5)); -> 3
console.log(Math.round(2.6)); -> 3

-버림과 올림 (Floor and Ceil) : Math.floor(x)을 하면 x의 버림 값이, Math.ceil(x)을 하면 x의 올림 값이 리턴됩니다. 이 경우, 소수 부분이 얼마 인지와는 상관이 없다.
console.log(Math.floor(2.4)); -> 2
console.log(Math.floor(2.49)); -> 2
console.log(Math.floor(2.8)); -> 2
console.log('-'); -> -
console.log(Math.ceil(2.4)); -> 3
console.log(Math.ceil(2.49)); -> 3
console.log(Math.ceil(2.8)); -> 3

-난수 (Random) : Math.random을 하면 0 이상 1 미만의 값이 랜덤으로 리턴된다.
console.log(Math.random()); -> 0.21458369059793236
console.log(Math.random()); -> 0.6622040803059857
console.log(Math.random()); -> 0.785172717569619
console.log(Math.random()); -> 0.9056556038884926

#바보 자바스크립트?
let sum = 0.1 + 0.2;
console.log(sum); -> 0.30000000000004 ?!
-사람과 컴퓨터가 숫자를 다루는 방식이 다르기 때문에 숫자를 계산할 때 오차가 발생한다.
-오차를 해결하는 방법
1.toFixed() 메소드 사용하기 
toFixed 값은 문자열이기 때문에 숫자로 형변환을 해주어야한다.
-> console.log(Number(sum.toFixed(1))); Number 메소드 사용하기
-> console.log(+sum.toFixed(1)); + 붙여주기
2.Math.round() 메소드 사용하기
=console.log(Math.round(sum * 10) / 10);

#문자열 심화
-자바스크립트에서는 문자열도 객체처럼 다룰 수 있다. 문자열은 배열과 비슷한 부분이 많다.
// String 
myString = 'Hi codeit';

// 부분 문자열 접근 slice(start, end)
console.log(myString.slice(0, 2)); // 0번 인덱스부터 1번 인덱스까지 가져옴.
console.log(myString.slice(3)); // 3번 인덱스부터 끝까지 가져옴.
console.log(myString.slice()); // 문자열 전체를 가져옴.

// 양끝 공백 제거
console.log(myString.trim()); // trim 메소드

// 대소문자 변환
console.log(myString.toUpperCase()); // 대문자
console.log(myString.toLowerCase()); // 소문자

// 요소 탐색
console.log(myString.indexOf('i')); // 앞 부터
console.log(myString.lastIndexOf('i')); // 뒤 부터
-없는 문자열을 찾으려고 하면 -1이 출력된다.

// 요소 접근
console.log(myString.[3]); // 대괄호 표현법
console.log(myString.charAt(3)); // charAt 메소드

// 문자열 길이
console.log(myString.length); // length 프로퍼티

#문자열과 배열의 비슷한 점
-배열과 문자열 모두 length프로퍼티를 가지고 있고, 대괄호 표기법으로 각 요소에 접근할 수 있다.
꽤 많은 메소드들이 배열과 문자열 모두 동일하게 사용된다. 배열을 다룰 때 유용한 for..of문을 문자열에 활용할 수도 있다.

let myString = 'Codeit';

for (let str of myString) {
  console.log(str);
}
->  C
    o
    d
    e
    i
    t

#문자열과 배열의 다른 점
-비슷하다고 해서 완전히 같다고는 할 수 없다.

let myString = 'Codeit';
let myArray = ['C', 'o', 'd', 'e', 'i', 't'];

console.log(typeof myString); -> string (문자열은 string(문자))
console.log(typeof myArray); -> object (배열은 object(객체))
-typeof 연산자를 사용해서 두 값의 자료형을 비교해보면, string과 object, 확실히 서로 다른 자료형인걸 확인할 수 있고,

console.log(myString === myArray); -> false
console.log(myString == myArray); -> false
-일치 비교뿐만 아니라, 느슨하게 비교하는 동등비교에서도 false가 출력되는걸 확인할 수 있다.

-mutable vs immutable
-가장 중요한 차이는 배열은 'mutable(바뀔 수 있는)' 자료형인 반면 문자열은 'immutable(바뀔 수 없는)' 자료형이라는 것이다.
-베열은 요소에 접근해서 할당연산자를 통해 요소를 수정할 수 있지만, 문자열은 한 번 할당된 값을 수정할 수 없다.
다르게 표현해서, 변수에 할당된 문자열을 바꾸고 싶다면, 일부를 바꾸는 게 아니라 새로운 문자열을 지정해주어야 한다.

// 배열은 mutable
let myArray = ['C', 'o', 'd', 'e', 'i', 't'];
myArray[0] = 'B';
console.log(myArray); -> (6) ["B", "o", "d", "e", "i", "t"]

// 문자열은 immutable
let myString = 'Codeit';
myString[0] = 'B';
console.log(myString); -> Codeit

#기본형과 참조형
-자료형 (Date Type) : 기본형, 참조형
-Number String Null Bollean undefined : 기본형 (Primitive Type)
: 변수에 기본형 값을 다루는 방식은 모두 똑같다. ex) let x = 3;
-Object : 참조형 (Reference Type)
: 변수에 객체를 할당하면 변수에 객체가 담기는 것이 아니라 그 객체를 가지고 있는 주소값이 담기는 것이다. ex) let x = {name: "codeit"};
-> 기본형 값을 변수에 담아 사용할 때는 값이 그대로 할당되고, 참조형 값을 변수에 담아 사용할 때는 해당 객체를 가리키는 주소값이 할당된다.

#참조형 복사하기
-참조형 값은 변수에 할당될 때 값 자체가 아니라 '주소값'이 할당된다.

// 참조형 복사하기 (Reference Type Copy)
// 배열일 때
let numbers1 = [1, 2, 3];
let numbers2 = numbers1.silce(); -> silce() : 괄호 안에 아무 숫자도 넣지 않으면 배열의 처음부터 끝까지 리턴 값으로 받아온다.

numbers2.push(4);

conosle.log(numbers1); -> (3) [1, 2, 3]
conosle.log(numbers2); -> (4) [1, 2, 3, 4]

-> slice 메소드를 활용하면 배열을 복사하는 것과 같은 효과를 얻을 수 있다.

// 객체일 때
1. Object.assign(객체를 복사할 수 있는 메소드)를 활용하여 복사하기

let course1 = {
    title: '파이썬 프로그래밍 기초',
    language: 'Python'
};

let course2 = Object.assign({}, course1); -> Object.assign 객체를 복사할 수 있는 메소드

course2.title = '알고리즘의 정석';

console.log(course1); -> {title: "파이썬 프로그래밍 기초",
    language: "Python"}
console.log(course2); -> {title: "알고리즘의 정석",
    language: "Python"}

2. for...in문을 함수로 만들어 사용하여 복사하기

function cloneObject(object) {
    let temp = {};

    for (let key in object) {
    temp[key] = object[key]; 
    }

    return temp;
};

let course1 = {
    title: '파이썬 프로그래밍 기초',
    language: 'Python'
};

let course2 = cloneObject(course1);
let course3 = cloneObject(course1);

course2.title = '자료 구조';
course3.title = '객체 지향 프로그래밍';

console.log(course1); -> {title: "파이썬 프로그래밍 기초",
    language: "Python"}
console.log(course2); -> {title: "자료 구조",
    language: "Python"}


#const, 변수와 상수 사이
-let으로 선언한 변수 : 재할당이 가능하다.
-const로 선언한 변수 : 재할당이 불가능하다.
-const 변수 (variable) vs const 상수 (constant)
    myName                   MY_NAME


let team1 = ['Drum', 'Bass', 'Saxophone'];
const team2 = ['Drum', 'Bass', 'Saxophone'];

team1.splice(2, 1, 'Trumpet');
team1 = ['Drum', 'Bass', 'Trumpet'];

team2.splice(2, 1, 'Piano');
team2 = ['Drum', 'Bass', 'Piano'];

console.log(team1);
console.log(team2);


#변수 선언
var 변수 : var 변수는 let 이나 const 처럼 똑같이 키워드 다음에 변수이름을 써서 선언할 수 있고,
var myVariable;

myVariable = 'codeit';

혹은 키워드와 변수이름, 그리고 할당연산자와 값으로 선언과 동시에 값을 할당해 줄 수도 있다.
var myVariable = 'codeit';

#중복 선언 허용
var 키워드로 선언한 변수의 첫 번째 문제는, let과 const와는 다르게 중복 선언이 가능하다는 것이다.
똑같은 이름으로 변수를 한 번 더 선언하게 되면, 에러가 발생하는 것이 아니라 그냥 기존의 변수를 덮어써 버리는 것. let키워드로 선언한 변수에 값을 재할당하는 것과는 엄연히 다르다.
var myVariable = 'codeit';
console.log(myVariable); -> codeit
var myVariable = 'Codeit!';
console.log(myVariable); -> Codeit!
이렇게 변수가 중복선언이 되면, 길고 복잡한 코드를 작성할 때 실수를 할 가능성이 커지고, 상황에 따라서는 치명적인 오류가 발생할 수 있다.

#함수 스코프
var 키워드 변수가 사라진 두 번째 문제는 Scope의 문제이다. 
let과 const 키워드로 선언한 변수는 if, for, function 등등 어떤 키워드와 관계없이 코드 블록, 즉 {} 중괄호로 감싸진 부분을 기준으로 scope를 갖게 되지만, var 키워드로 선언한 변수는 scope가 function에서만 구분되어 있다.
// let, const
{
  let x = 3;
}

function myFunction() {
  let y = 4;
}

console.log(x);
console.log(y);

-> Uncaught ReferenceError: x is not defined 
: let이나 const 키워드의 경우에는 중괄호로 감싸진 경우라면 모두 중괄호 밖에서는 지역 변수에 접근할 수 없다.

// var
{
  var x = 3;
}

function myFunction() {
  var y = 4;
}

console.log(x); -> 2
console.log(y); -> Uncaught ReferenceError: y is not defined
: 하지만 var 변수는 지역변수의 구분이 함수에만 있기 때문에 if, for, while, switch 등 다양한 상황에서 선언한 변수가 자칫, 전역변수의 역할을 하게 될 수도 있는 것.

*참고 : 이렇게 함수를 기준으로만 적용되는 스코프는 함수 스코프, 코드 블록을 기준으로 적용되는 스코프는 블록 스코프라는 용어를 사용한다.


#끌어올림 (Hoisting)
// let, const
console.log(myVariable); -> Uncaught ReferenceError: Cannot access 'myVariable' before initialization
let myVariable;
 
: let과 const로 선언한 변수는 선언되기 이전에 사용될 수 없다. 하지만, var 변수는 함수 스코프를 기준으로 선언되기 이전에도 변수에 접근이 가능하다.

// var
console.log(myVariable); -> undefined
var myVariable; 

: 변수의 선언이 끌려 올라가서 마치, 2번째 줄과 첫 번째 줄이 바뀐 것처럼 동작한다.
var myVariable;
console.log(myVariable);

이렇게 변수가 끌어올려 지는 현상을 '호이스팅(hoisting)'이라고 부른다. 다행히 호이스팅은 선언과 동시에 값을 할당하더라도, 선언문만 올려지기 때문에 값은 그대로 두 번째 줄에 남아있다.
console.log(myVariable); -> undefined
var myVariable = 2;
console.log(myVariable); -> 2

-한 가지 주의해야 될 부분은, 함수를 선언할 때도 이 호이스팅이 적용된다.

sayHi();

function sayHi() {
  console.log('hi');
}

-> hi
당연한 듯 함수가 잘 실행되는 모습을 확인할 수 있다.
이런 현상은 함수를 한 번 선언하고 나면 어디서든 유연하게 사용할 수 있다는 장점이 있지만, 코드의 흐름에는 부정적인 영향을 끼칠 수 있다. 그래서 함수를 선언할 때는 가급적 코드 윗부분에 선언하거나, 호출을 항상 아래쪽에서 한다거나 나름대로 규칙을 세워서 코드를 작성하는것이 좋다.

(자, 지금까지 오래된 자바스크립트에서 변수를 만들 때 사용했던 var 키워드에 대해서 살펴봤는데요.
요즘은 잘 사용되지 않지만, 그래도 자바스크립트의 상식적인 측면에서 가볍게 이해하고 계시면 좋을 것 같습니다!)

<!-- 과제로 복습하기 -->
#팩토리얼 
-계승(팩토리얼) : 1부터 어떤 양의 정수 n까지의 정수를 모두 곱한 것을 말하며 n!로 나타낸다.
팩토리얼은 아래와 같이 계산한다. 0!은 1이라는 점도 기억해야한다.
0! = 1
1! = 1
2! = 1 * 2 = 2
3! = 1 * 2 * 3 = 6
4! = 1 * 2 * 3 * 4 = 24
5! = 1 * 2 * 3 * 4 * 5 = 120
6! = 1 * 2 * 3 * 4 * 5 * 6 = 720

-팩토리얼의 정의를 다시 한번 살펴보면, 1부터 어떤 양의 정수 n까지의 정수를 모두 곱한 것을 말하며 n!로 나타낸다. 인데, 곱셈이기 때문에 교환법칙에 의해서 어떤 양의 정수 n부터 1까지의 정수를 모두 곱한 것을 말하며 n!로 나타낸다라고 표현해도 결과는 같다. 
그래서 0!부터 6!을 구하는 공식을 다시 작성하면 아래와 같이 작성할 수 있다.
0! = 1
1! = 1
2! = 2 * 1 = 2
3! = 3 * 2 * 1 = 6
4! = 4 * 3 * 2 * 1 = 24
5! = 5 * 4 * 3 * 2 * 1 = 120
6! = 6 * 5 * 4 * 3 * 2 * 1 = 720

#거스름돈 구하기
-복습하기!


#팰린드롬
-"토마토"와 "기러기"처럼 거꾸로 읽어도 똑같은 단어를 "팰린드롬(palindrome)"이라고 부른다.
-복습하기!

