---
title: "2016 year (coding practice)"
date: 2018-10-23
categories: coding-practice
---
### Explain problems: 
Jan First 2016 is a Friday. What is a day of month of A and day of B of 2016?<br>
Complete the solution, which accepts two numbers a and b and returns the day of the month in 2016.<br>
The namd of the day is SUN,MON,TUE,WED,THU,FRI,SAT.<br>
For example, if a=5, b=24, then May 24 is Tuesday, so return the string TUE.<br>

### Restrictions: 
2016 is a leap year.<br>
The month a and the day b of 2016 is real day. (The dates of 26th 13Month or 45th Feb will not be given)<br>

### Input and output examples: 
|  a |  b  |result|
|:---:|:---:|:---:|
|  5 |  24 |  TUE |

### 문제 설명:
2016년 1월 1일은 금요일입니다. 2016년 a월 b일은 무슨 요일일까요? <br>
두 수 a ,b를 입력받아 2016년 a월 b일이 무슨 요일인지 리턴하는 함수, solution을 완성하세요. <br>
요일의 이름은 일요일부터 토요일까지 각각 SUN,MON,TUE,WED,THU,FRI,SAT 입니다. <br>
예를 들어 a=5, b=24라면 5월 24일은 화요일이므로 문자열 TUE를 반환하세요. <br>

### 제한 조건:
2016년은 윤년입니다. <br>
2016년 a월 b일은 실제로 있는 날입니다. (13월 26일이나 2월 45일같은 날짜는 주어지지 않습니다) <br>

### 입출력 예:
|  a |  b  |result|
|:---:|:---:|:---:|
|  5 |  24 |  TUE |

```javascript
function solution(a, b) {
    var answer = '';
    var month = parseInt(a);
    var days = parseInt(b);
    var calendar = [];
    var date = '';
    var counter = 1;
    for(var i = 1; i < 13; i++)
    {
        calendar[i] = [];
        for(var j = 1; j < 32; j++)
        {
            switch(counter%7) {
                case 0: date = 'THU'; break;
                case 1: date = 'FRI'; break;
                case 2: date = 'SAT'; break;
                case 3: date = 'SUN'; break;
                case 4: date = 'MON'; break;
                case 5: date = 'TUE'; break;
                case 6: date = 'WED'; break;
            }
            calendar[i][j] = date;
            if(i === 2 && j > 29)
            {
                calendar[i][j] = null;
                counter--;
            }
            if(i < 8 && i !== 2)
            {
                if(i%2 === 0 && j > 30 )
                {
                    calendar[i][j] = null;
                    counter--;
                }    
            }
            else if(i > 7)
            {
                if(i%2 !== 0 && j > 30)
                {
                    calendar[i][j] = null;
                    counter--;
                }
            }
            counter++;
        }
    }
    answer = calendar[month][days];
    return answer;
}
```
### P.S:
It was given a baseline date, but I considered that baseline date and actual calendar date are different. <br>
So, I had to consider it and the code had been extended. <br>
If the baseline date is same actual calendar date, then using the date function. <br>


기준 날이 주어졌지만 실제 달력의 날짜와 주어진 기준 날의 요일이 다를 수 있다는 걸 감안하고 코드를 짜느라 길어졌다.
실제 달력을 기준으로 한다면 Date 함수를 써서 간단히 짤 수 있다. 

like this,
이런 식으로


```javascript
function getDayName(a,b){
    var arr = ['SUN','MON','TUE','WED','THU','FRI','SAT'];
    var date = new Date(`2016-${a}-${b}`);
    var day = date.getDay();
    return arr[day];
}

console.log(getDayName(5,24));
```

Problems from [Programmers](https://programmers.co.kr/) <br>
문제 출처 [프로그래머스](https://programmers.co.kr/)
