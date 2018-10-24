---
title: "the largest number"
date: 2018-10-23
categories: coding-practice
---

### Explain Problems:
When given a zero or positive integer, identify the largest number you can make by attaching an integer. <br>
For example, if the given integer is [6, 10, 2], then [6102, 6210, 1062, 1026, 2610, 210], the largest of which is 6210.<br>
When an array of 0 or positive integers is given as a parameter, create a solution function so that the largest number that can be created by rearranging the order into a string. <br>

### 문제 설명:
0 또는 양의 정수가 주어졌을 때, 정수를 이어 붙여 만들 수 있는 가장 큰 수를 알아내 주세요. <br>
예를 들어, 주어진 정수가 [6, 10, 2]라면 [6102, 6210, 1062, 1026, 2610, 2106]를 만들 수 있고, 이중 가장 큰 수는 6210입니다. <br>
0 또는 양의 정수가 담긴 배열 numbers가 매개변수로 주어질 때, 순서를 재배치하여 만들 수 있는 가장 큰 수를 문자열로 바꾸어 return 하도록 solution 함수를 작성해주세요. <br>

### Restrictions: 
- The numbers are at least 1 and not more than 100,000.
- The numbers element is not less than 0 and not more than 1,000.
- The correct answer may be too large, so replace it with a string to return it.

### 제한 사항:
- numbers의 길이는 1 이상 100,000 이하입니다.
- numbers의 원소는 0 이상 1,000 이하입니다.
- 정답이 너무 클 수 있으니 문자열로 바꾸어 return 합니다.

### Input and output example:
<table>
   <tbody>
     <tr>
       <th>numbers</th>
       <th>return</th>
     </tr>
     <tr>
       <td>[6,10,2]</td>
       <td>"6210"</td>
     </tr>
     <tr>
       <td>[3,30,34,5,9]</td>
       <td>"9534330"</td>
     </tr>
  </tbody>
</table>

### 입출력 예:
<table>
   <tbody>
     <tr>
       <th>numbers</th>
       <th>return</th>
     </tr>
     <tr>
       <td>[6,10,2]</td>
       <td>"6210"</td>
     </tr>
     <tr>
       <td>[3,30,34,5,9]</td>
       <td>"9534330"</td>
     </tr>
  </tbody>
</table>

### Solved:
```javascript
function solution(numbers) {
    var answer = [];
    var result = permutation(numbers);
    for(var i=0; i<result.length; i++)
    {
        answer.push(Number(result[i].join('')));
    }

    var max = answer.reduce( function (previous, current) { 
        return previous > current ? previous:current;
    });
    console.log(max);
    return String(max);
}

function permutation(array) { 
 
    function p(array, temp) { 
      var i, x; 
      array.length || result.push(temp); 
      for (i = 0; i < array.length; i++) { 
        x = array.splice(i, 1)[0]; 
        p(array, temp.concat(x)); 
        array.splice(i, 0, x); 
      } 
    } 
 
    var result = []; 
    p(array, []); 
    return result; 
} 
```
Problems from [Programmers](https://programmers.co.kr/) <br>
문제 출처 [프로그래머스](https://programmers.co.kr/)
