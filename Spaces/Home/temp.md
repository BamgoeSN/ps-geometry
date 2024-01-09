$$ B = 64 $$
$2^B$ 미만의 정수에 대해선 더하고 빼고 곱하고 나누고 다 overflow 없이 가능함.
$$u, v, m \in [0, 2^{2B}) \qquad uv \in [0, 2^{4B}) $$
이때 $uv \bmod m$을 u128만 가지고 구하고자 함.
$$ u = u_h 2^B + u_l \qquad v = v_h 2^B + v_l $$
라고 두자.
$$ u_h, u_l, v_h, v_l \in [0, 2^B) $$
의 범위가 성립함. 그러면 $uv$는
$$ uv = u_h v_h 2^{2B} + (u_h v_l + u_l v_h) 2^B + u_l v_l = P 2^{2B} + Q 2^B + R $$
로 정리됨. 여기서 $P, Q, R$은
$$ P, Q, R \in [0, 2^{2B}) $$
의 범위를 만족함.
$$ s = R_l \quad r = (R_h + Q_l)_l \quad q = ((R_h + Q_l)_h + Q_h)_l \quad p = ((R_h + Q_l)_h + Q_h)_h + P $$
의 네 가지 상수를 정의하면
$$ uv = p 2^{3B} + q 2^{2B} + r 2^B + s $$
이고 이들은
$$ p,q,r,s \in [0, 2^B) $$
의 조건을 만족함. $uv < 2^{4B}$이기 때문. 이걸 이제 $m$으로 나눈 나머지 구하면 되는 것.

Naive 나눗셈을 적용해도 되지 않을까?

1. 위에 기술한 대로 $p, q, r, s$를 구하고, naive 나눗셈을 시뮬레이션할 것.
2. 답은 $n \leftarrow 0$에 저장된다.
3. $c \leftarrow 0$, $x \leftarrow p2^B + q$. $c2^{2B} + x$가 naive 나눗셈에서 볼 피제수이다.
4. $c2^{2B} + x = fm + g$인 정수 $f, g$를 구함. 
5. 망했는데

