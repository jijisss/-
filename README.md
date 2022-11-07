<!-- 1.객체 -->
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
-Property Value = 모든 자료형을 사용할 수 있다.
-객체안에 객체를 넣는것도 가능하다.

#객체에서 데이터 접근하기
-객체를 다루기 위해서는 변수에 할당해주면서 이름을 만들어주어야한다.
*객체의 프로퍼티에 접근하기 위한 방법.
-점 표기법 (objectName.propertyName)
ex) console.log(codeit.bornYear);
-대괄호 표기법 (objectName.['propertyName'])
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

#배열 다루기

#배열 메소드

#배열 메소드2

#for...of 반복문

#다차원 배열

<!-- 자료형 심화 -->

<!-- 과제로 복습하기 -->