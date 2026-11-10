
### INTRODUÇÃO
Geralmente, amplificadores diferenciais são os mais usados em circuitos integrados de AMP-OP. Isto é devido à sua capacidade de usar capacitores de capacitância muito pequena (ou seja, quie são capacitores difíceis de montar capacitores de desvio com), algo compatível com uma limitação bem conhecida dos CIs - a de capacitores de alta capacitância (ex. $\large 1\mu F$) serem muito grandes.

### ENTRADAS 
![[Pasted image 20261015135340.png]]

Neste diagrama, a primeira coisa a se notar é o $\large v_{out}$, expresso trivialmente como:
$$
\huge v_{out}=v_{c1}-v_{c2}
$$
Esta é a primeira equação importante do amplificador diferencial.
Nesta, nota-se que aumentos em $\large v_{c1}$ e diminuições em $\large v_{c2}$ ocasionam aumentos em $\large v_{out}$. Estas tensões são tensões no coletor, ou seja, são inversamente proporcionais às tensões na base. Desse modo, podemos dizer que:
1. $\large v_{out}$ é diretamente proporcional a $\large v_1$
2. $\large v_{out}$ é inversamente proporcional a $\large v_2$
Desse modo, dizemos que $v_{out}$ e $\large v_1$ estão em fase, ao passo que $v_{out}$ e $\large v_2$ estão com uma defasagem de 180 graus (inversão). Por isso, chamamos:

-  $\large v_1$ é a entrada não-inversora
- $\large v_2$ é  a entrada inversora.

Uma terminologia bastante importante, que iremos utilizar pelo resto deste estudo.

Às vezes, podemos ter uma das entradas aterradas. Isto vai ser um caso de estudo importante. 
Quando nenhuma das duas entradas está aterrada, chamamos o amplificador de Amplificador Diferencial, e sua tensão de saída é dada, em função de $\large v_1$ e $\large v_2$ por:
$$
\huge v_{out} = A_v(v_1-v_2)
$$
Para um determinado ganho $\large A_v$ inerente ao amplificador.

### SAÍDA COM TERMINAÇÃO SIMPLES
![[Pasted image 20261015203505.png]]

Na imagem acima, temos um exemplo de uma configuração de terminação simples.
Aqui, ainda vamos ter:
$$
\huge v_{out}=A_v(v_1-v_2)
$$
Porém, existe uma diferença fundamental entre estes e os amplificadores diferenciais. No caso dos amplificadores de terminal simples, vamos ter que o ganho de tensão é metade do ganho de tensão que normalmente teríamos em um amplificador diferencial. Isto é porque vamos ter a saída em apenas um coletor, invés dos dois.

### CONFIGURAÇÕES DA ENTRADA NÃO-INVERSORA

![[Pasted image 20261015204255.png]]

Aqui, vamos ter que a entrada inversora está aterrada, de modo que vamos ter que, para ambos:
$$
\huge v_{out}=A_vv_1
$$
Mas vamos ter que, para o amplificador simples, o seu ganho vai ser metade do ganho do amplificador diferencial, como discutido.

### CONFIGURAÇÕES DA SAÍDA INVERSORA

![[Pasted image 20261015204832.png]]

Ocorre quando aterramos a entrada não-inversora.
Aqui, vamos ter que:
$$
\huge v_{out}=-A_vv_2
$$
E o ganho segue a mesma lógica descrita anteriormente.

### ANÁLISE CC DE UM AMPLIFICADOR DIFERENCIAL

![[Pasted image 20261015205042.png]]

Na imagem acima, temos a análise CC de um amplificador diferencial.
Trivialmente, conforme vimos anteriormente, vamos ter que, sendo $\large I_T$ a corrente de cauda, que passa pelo resistor $\large R_E$, e assumindo a primeira aproximação, ou seja, o diodo completamente ideal:
$$
\huge I_T=\frac{V_{EE}}{R_E}
$$
Além disso, sendo $\large I_E$ a corrente no emissor de cada um dos transistores, é trivial concluir que:
$$
\huge I_E=\frac{I_T}{2}
$$

Estas regras também seguem no caso de um amplificador de terminação simples.
Ademais, assumindo a segunda aproximação, a única coisa que muda é o caso da corrente de cauda, para calcular esta, basta fazer:
$$
\huge I_T=\frac{V_{EE}-V_{BE}}{R_E}
$$
trivialmente.

### ANÁLISE CA DE UM AMPLIFICADOR DIFERENCIAL:
Para um amplificador diferencial, independentemente dele ser de entrada simples ou de entrada diferencial, vamos sempre ter que:
$$
\huge z_{in}=2\beta r_e'
$$
Um resultado muito importante. Isto é devido ao fato da base "ver duas entradas".
Ademais, como mencionado, o ganho para amplificadores de entrada diferencial é dado por:
$$
\huge A_V=\frac{R_C}{r_e'}
$$
Onde $\large R_C$ é simplesmente a resistência em um dos coletores, ou nos dois (quando é nos dois, ou seja, quando tivermos um diferencial, elas vão ser iguais)

Ademais, para amplificadores de saída simples, vamos sempre ter que:
$$
\huge A_V=\frac{R_C}{2r_e'}
$$
Como mencionado, o ganho vai ser duas vezes menor.
