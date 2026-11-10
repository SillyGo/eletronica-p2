
### O AMPLIFICADOR IDEAL

![[Pasted image 20261016103437.png]]

Representado pela figura acima, o amplificador ideal possui algumas propriedades importantes.
Primeiramente, sua equação de ganho é definida exatamente da mesma forma como vimos, ou seja:
$$
\huge v_{out}=A_v(v_+-v_-)
$$
Onde $\large v_+$ e $\large v_-$ são, respectivamente, a entrada não-inversora e inversora.
Ademais, para o caso do amp-op ideal, temos algo que parece paradoxal, mas não é: seu ganho de tensão deve ser infinito.
Isso se deve ao fato que, em certos casos (como quando temos retroalimentação), queremos que $\large v_+=v_-$. Uma forma de garantir este comportamento é fazendo o ganho tender ao infinito, logo que:
$$
\huge v_+-v_-=\lim_{A_v \to \infty}  \frac{v_{out}}{A_v}=0
$$
Deste modo, podemos rearranjar a equação, obtendo:
$$
\huge v_+=v_-
$$
Como queríamos.
Ademais, temos outras propriedades, como:
1. A impedância de entrada deve tender ao infinito
2. A impedância de saída deve tender a 0

### AMPLIFICADOR INVERSOR

Consiste em conectar a saída do amplificador de volta na entrada inversora, aterrando a entrada não-inversora

![[Pasted image 20261016170707.png]]

De análise simples, vamos ter que:
$$
\huge V_{in}=i_{in}R_1
$$vamos ter também que:
$$
\huge V_{out}=-i_{in}R_f
$$
Sabemos que o ganho consiste em v_out divido por v_in. Portanto:
$$
\huge A_v=\frac{-R_f}{R_1}
$$
É a equação para o cálculo de um amplificador inversor.
Sua impedância de entrada é facilmente dada por:
$$
\huge Z_{in}=R_1
$$

### LARGURA DE BANDA
todo amplificador tem uma medida de frequência chamada largura de banda.
Caso a frequência de operação do amplificador passe dessa medida, vamos ter que a amplificação vai ficando mais baixa.
Uma forma de medir a amplificação é por meio de decibeis (dB). Podemos converter de amplificação simples para amplificação em dB da seguinte maneira:
$$
\huge A_{vdB}=20\log_{10}(A_v) 
$$
Ademais, é importante definir dois conceitos, o ganho em malha fechada ($\large A_{cl}$) e o ganho em malha  aberta ($\large A_{ol}$)
O  ganho de malha fechada acontece quando temos, por exemplo, retroalimentação. 
Finalmente, acima de determinada frequência, vamos ter uma certa queda de frequência.
Podemos, encontrar a frequência a partir do ganho atual do amplificador por meio da seguinte relação:
$$
\huge f_{2(CL)}=\frac{f_{unitario}}{1+A_{v(CL)}}
$$
Onde 'cl' significa 'closed loop', ou seja, malha fechada.
O $\large f_{unitario}$ corresponde à frequência do amplificador quando o ganho é unitário, ou seja, quando $A_{v(CL)}=0 dB$ .
![[Pasted image 20261025182004.png]]

A curva de ganho / frequência apresenta o comportamento visto acima.

Na grande maioria das vezes, podemos assumir
$$
\huge f_{unitario} = 1MHz
$$

### AMPLIFICADOR NÃO-INVERSOR

![[Pasted image 20261025182558.png]]

Por meio de processos que eu estou com preguiça de enunciar mas que involvem (como sempre) análise nodal, vamos encontrar que:
$$
\huge A_v=\frac{R_f}{R_1}+1
$$
Que é quase exatamente igual à regra de amplificação para amplificadores inversores.

### AMPLIFICADORES SOMADORES

![[Pasted image 20261027060541.png]]

Aqui temos a soma de duas tensões, mas podemos adicionar 'n' diferentes tensões.
Sabemos que a corrente total que entra no amplificador é:
$$
\huge i = i_{v1}+i_{v2}
$$
Ademais, pelo terra virtual, encontramos que:
$$
\huge 0 - R_fi = v_{out}
$$
tal que:
$$
\huge v_{out}=-R_fi =-R_f(i_{v1}+i_{v2})
$$
Ademais, sabemos que:
$$
\huge v_1-0=R_1i_1 \to i_1=\frac{v_1}{R_1}
$$
De forma análoga, encontramos que:
$$
\huge i_2=\frac{v_2}{R_2}
$$
E, portanto, que:
$$
\huge v_{out} = -R_f(\frac{v_1}{R_1}+\frac{v_2}{R_2})
$$
### AMPLIFICADORES SEGUIDORES DE TENSÃO

![[Pasted image 20261027061349.png]]

Aqui, temos um simples buffer. Logo que a tensão em ambos terminais do amplificador é igual, e a entrada inversora está em curto com $\large v_{out}$, vamos ter simplesmente que:
$$
\huge v_{in}=v_{out}
$$
e, como consequência, teremos que o ganho de malha  fechada deste circuito será igual a 1.