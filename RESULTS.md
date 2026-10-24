# K6 lab results
## Part 0
- Step 0.1, http_req_duration: avg=468.98ms min=468.98ms med=468.98ms max=468.98ms p(90)=468.98ms p(95)=468.98ms
- Step 0.2, requests, rate and p(95), and why the rate stays below 5: 72 requests, 3.399 requests per second, p(95)=557.01ms. Each iteration takes 1.42s, that's mean users cannot send five requests every second, because each iteration already takes more than 1 second(1.42s), so they have to wait for each iteration to finish, so total requests that could finish in 1 second is approximately 3.399 requests per second.
- Step 0.6, exit code of the normal run and of the run with P95=300: exit code of the normal run is 0 and exit code of the run with P(95)=300 is 99.
- Step 0.7, rules that passed, p(95), p(99), exit code after your change: 
rules that passed -> 
http_req_duration
    ✓ 'p(95)<1000' p(95)=381.89ms
    ✓ 'p(99)<1500' p(99)=388ms
http_req_failed
    ✓ 'rate<0.01' rate=0.00%
Exit code after change is 99.
- Step 0.8, what was wrong, and how the checks showed it: The request used pepperoni and knife. After run explore.js, I noticed that it uses Pepperoni and Knife, which are uppercase. So, I change both in bug hunt file from lowercase to uppercase.
## Part A results
| Step | Test type | Users | Req/s | p(95) | Max | Failed | Checks |
| ---- | ------------ | ----- | ----- | ----- | --- | ------ | ------ |
| A1 | Smoke | 1 |  0.518/s | 391.14ms | 392.72ms | 0.00% | 100.00% |
| A2 | Average load | 3 | 1.28/s | 482ms | 1s | 0.00% | 100.00% |
| A3 | Stress | 5 | 2.01/s | 696.33ms | 1.17s | 0.00% | 100.00% |
| A4 | Spike | 5 | 1.03/s | 494.46ms | 745.51ms | 0.00% | 100.00% |
| A5 | Soak | 2 | 0.966/s | 559.56ms | 927.30ms | 0.00% | 100.00% |
## Part B
1. | Step | Test type | Users | Req/s | p(95) | Max | Failed | Checks |
| ---- | ------------ | ----- | ----- | ----- | --- | ------ | ------ |
| A1 | Smoke | 1 |  0.518/s | 391.14ms | 392.72ms | 0.00% | 100.00% |
| A2 | Average load | 3 | 1.28/s | 482ms | 1s | 0.00% | 100.00% |
| A3 | Stress | 5 | 2.01/s | 696.33ms | 1.17s | 0.00% | 100.00% |
| A4 | Spike | 5 | 1.03/s | 494.46ms | 745.51ms | 0.00% | 100.00% |
| A5 | Soak | 2 | 0.966/s | 559.56ms | 927.30ms | 0.00% | 100.00% |
2. Each iteration takes 1.42s, that's mean users cannot send five requests every second, because each iteration already takes more than 1 second(1.42s), so they have to wait for each iteration to finish, so total requests that could finish in 1 second is approximately 3.399 requests per second.
3. Yes. p(95) response time increased from 482ms in a2-average test to 696.33 in a3-stress test with 5 users.
4. The p(95) response time increased to approximately 641 ms at 60 seconds, but it later decreased to approximately 327 ms at 90 seconds.
5. 
6.
7.
8.
9.