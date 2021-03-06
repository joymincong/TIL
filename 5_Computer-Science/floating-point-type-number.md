# 부동 소수점

## 정의

아주 큰 수와 아주 작은 수를 효율적으로 표현하기 위한 방법 중 하나로 주로 실수를 표현방법 (floating-point type number)을 사용한다.



표현 방법은

> 유효숫자 x 소수점의 위치(지수의 곱)

이며 예를 들어,

> 123.456 = 123456 x 10^-3

으로 표현된다.



(32bit 기준)

보통은 부호(1bit), 유효숫자(24bit), 지수(8bit)를 각각 저장한다. 이는 적은 메모리로 실수를 저장할 수 있다.

> 부호(1bit) + 지수(8bit) + 유효숫자(24bit)

```
부호 : 0(+) or 1(-)
지수 : 127 기준으로 더하고 뺀 값
가수 : 왼쪽부터 차례대로
```





파이썬에서는 `유효숫자e지수` 로 표현할 수 있다.

> 123.456 = 123456e-3, 123400 = 1234e2



## 이진 부동소수점

실제 컴퓨터에서는 이진수 부동소수점 방식을 사용한다.



```
0.5 = 0.1 = 1x2^-1
0.75 = 0.11 = 11x2^-2
```



## 실수 표현 오차

이진수 부동 소수점를 사용하다보니 0.1과 같이 십진수로 쉽게 표현할 수 있는 수도 이진수를 사용하게 되면 무한개의 유효숫자가 나오게 된다.



하지만 컴퓨터에서 메모리 크기, 유효숫자에 할당된 비트 수가 제한되어 있기 때문에 0.1를 표현할 시 가장 비슷한 숫자를 표현한다.



하지만 실제 0.1를 입력하면 0.1로 보이게 된다. 이는 REPL 방식에서 값이 일정 소수점 이하 값을 생략하기 때문이다.

* REPL(Read-Eval-Print Loop) 방식 ? 주피터 노트북이나 파이썬 콘솔을 실행해 명령어를 한줄씩 입력해 상황을 지켜보는 방식 



그렇기 때문에

> 0.1 + 0.2 == 0.3 

> False

로 출력 된다.



이 문제를 해결하기 위해서는 round()함수를 이용해 반올림을 시켜준다.

> round(0.1 +0.2, 5) == round(0.3,5)

> True