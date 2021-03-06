## Chapter 2 - Study Feedback  (20.01.11)



##### 1. 지난 스터디에서 깨달은 점을 응용

- 지난 스터디에서, Mong은 And와 Or의 성질을 이용해서 문제에 접근하였다.

- 나도 이번에는 비슷한 시각으로 Chapter 2 의 핵심 문제인 '2진법 산수'에 접근해보기로 했다.

- 우선 2진법 덧셈에서 고려해야 할 사항은 다음 두 가지다.

  1) 두 수(a,b)를 더할 때(sum) 자리 올림이 되면 그 수는 0으로 바뀐다 

  ​	=> (0+0), (1+1) 은 0이 되고, (1+0), (0+1)은 1이 된다.

  ​	=> 더하는 두 수가 다르면 1, 같으면 0이 된다. 

  ​	=> 이는 **Xor**의 속성과 같다.

  2) (1+1)의 경우를 제외하고는, 자리 올림 수(carry)는 항상 0이다.

  ​	=> 이는 **And**의 속성과 같다.

- 반가산기(HalfAdder)의 구현에서 이러한 And와 Xor의 속성에 집중했다.

  ```
  CHIP HalfAdder {
      IN a, b;    // 1-bit inputs
      OUT sum,    // Right bit of a + b 
          carry;  // Left bit of a + b
  
      PARTS:
      // Put you code here:
      Xor(a=a, b=b, out=sum);
      And(a=a, b=b, out=carry);
  }
  ```

- 반가산기의 구현은 위와 같은데, 속성에 집중하니 쉽게 풀렸다. 이를 이용하여 FullAdder, Add16 등 다른 것들도 구현하였다.



**2. Epiphany of this week**

- 역시 중요한 것은 본질의 파악이라는 것을 느꼈다. 수학적 '개념 이해'가 가장 중요하고, 그로부터 문제 해결 능력이 파생된다.
- 이 능력을 기르려면, 어떤 문제에 당면했을 때 큰 그림과 어떤 기능의 본질을 파악하려는 자세가 중요하다는 것을 새삼 새기게 되었다.

- 아울러, 비록 아직 chapter2 까지 밖에 진도가 나가지 않았지만, 단순히 불 논리로 이루어진 Nand 게이트가 발전하여 이렇게 '2진법의 덧셈과 뺄셈'으로 구현될 수 있다는 점이 정말 신기하기만 하다.
- 아주 단순한 기능을 다듬고 발전시켜 정밀하고 복잡한 컴퓨터가 탄생하는 과정을 스터디를 통해 목도하는 중이다.