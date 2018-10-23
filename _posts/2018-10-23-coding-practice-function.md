---
title: "function development (coding practice)"
date: 2018-10-23
categories: coding practice programmers LV2
---

### Explain Problems:
Our team is working on a functional improvement. Each function can be reflected in the service at 100% advance. <br>
In addition, the development speed of each function is different. So, the function behind it can be developed before the function in front, and the function in the back is distributed together when the function in front is distributed.<br>
Complete the solution to return how many functions are deployed for each distribution that will be given an integer array 'speeds' and 'progresses' which they should be distributed first. <br>

### 문제 설명:
프로그래머스 팀에서는 기능 개선 작업을 수행 중입니다. 각 기능은 진도가 100%일 때 서비스에 반영할 수 있습니다. <br>
또, 각 기능의 개발속도는 모두 다르기 때문에 뒤에 있는 기능이 앞에 있는 기능보다 먼저 개발될 수 있고, 이때 뒤에 있는 기능은 앞에 있는 기능이 배포될 때 함께 배포됩니다. <br>
먼저 배포되어야 하는 순서대로 작업의 진도가 적힌 정수 배열 progresses와 각 작업의 개발 속도가 적힌 정수 배열 speeds가 주어질 각 배포마다 몇 개의 기능이 배포되는지를 return 하도록 solution 함수를 완성하세요. <br>

### Restrictions: 
- The number of works(the length of array of speeds and progresses) is below 100 works.
- The progress of works is a natural number under 100.
- The speed of works is a natural number below 100.
- You can deploy only once a day, and at the end of the day.
- For example, if a job with a 95% progress rate develops at 4% per day, the deployment takes place two days later.

### 제한 사항:
- 작업의 개수(progresses, speeds배열의 길이)는 100개 이하입니다.
- 작업 진도는 100 미만의 자연수입니다.
- 작업 속도는 100 이하의 자연수입니다.
- 배포는 하루에 한 번만 할 수 있으며, 하루의 끝에 이루어진다고 가정합니다.
- 예를 들어 진도율이 95%인 작업의 개발 속도가 하루에 4%라면 배포는 2일 뒤에 이루어집니다.

### Input and output example:
progresses  speeds  return <br>
[93,30,55]  [1,30,5]  [2,1] <br>

### 입출력 예:
progresses	speeds	return <br>
[93,30,55]	[1,30,5]	[2,1] <br>

### Explain about input and output example:
- You can deploy the first function after 7 days. First function is completed 93% and progressing 1% per day.
- You can deploy the second function after 3 days. Second function is completed 30% and progressing 30% per day.
- However, the first function didn't be completed yet, second function can be deployed after 7 days when the first function will be deployed.
- You can deploy the third function after 9 days. Third function is completed 55% and progressing 5% per day.
- So, you can deploy 2 functions at 7 days, and 1 function at 9 days.

### 입출력 예 설명: 
- 첫 번째 기능은 93% 완료되어 있고 하루에 1%씩 작업이 가능하므로 7일간 작업 후 배포가 가능합니다.
- 두 번째 기능은 30%가 완료되어 있고 하루에 30%씩 작업이 가능하므로 3일간 작업 후 배포가 가능합니다.
- 하지만 이전 첫 번째 기능이 아직 완성된 상태가 아니기 때문에 첫 번째 기능이 배포되는 7일째 배포됩니다.
- 세 번째 기능은 55%가 완료되어 있고 하루에 5%씩 작업이 가능하므로 9일간 작업 후 배포가 가능합니다.
- 따라서 7일째에 2개의 기능, 9일째에 1개의 기능이 배포됩니다.

### Solved:
```javascript
function solution(progresses, speeds) {
    var answer = [];
    var proc = [];
    var proLength = progresses.length;
    for(var i=0; i<proLength; i++)
    {
        proc.push(completePeriod(progresses[i], speeds[i]));
    }
    var procLength = proc.length;
    var total = 0;
    for(var stand=0; stand<procLength; stand++)
    {
        var count = 1;
        for(var j=stand+1; j<procLength; j++)
        {
            if(proc[stand] > proc[j]) count++;
            else if(proc[stand] === proc[j]) count++;
            else if(proc[stand] < proc[j]) {stand = j-1; break;}
        }
        total += count;
        if(total <= procLength) answer.push(count);
    }
    
    return answer;
}

function completePeriod(start, pace) {
    var days;
    var total = 0;
    var count = 1;
    for (;;)
    {
        if(total >= 100) break;
        total = start + (pace*count);
        count++;
    }
    return count-1;
}
```
Problems from [Programmers](https://programmers.co.kr/) <br>
문제 출처 [프로그래머스](https://programmers.co.kr/)
