### PONTA DE PROVA DE ALTA IMPEDÂNCIA

![[Pasted image 20261027062436.png]]

Primeiramente, notam-se três coisas fundamentais sobre este circuito:
1.  Sua impedância de entrada será $100M\Omega$. 
2. A amplificação do primeiro estágio será de -0.1
3. A amplificação do segundo estágio poderá ser chaveada entre 1 ou 10.

A primeira regra é importante devido ao fato que, ao conectarmos a ponta de prova em um circuito, forma-se um divisor de tensão, tal que, se representarmos o circuito dado como uma fonte $\large V_c$ e uma resistência interna $\large R_s$, vamos ter que:
$$
\huge V_M = \frac{V_c}{R_s+Z_{in}}
$$
Onde $\large Z_{in}$ consiste na impedância de entrada da nossa ponta de prova, e sendo  $\large V_M$ a tensão lida pelo multímetro que usa a nossa ponta de prova. Concluímos, pois, que quando maior a impedância de entrada, mais precisa será a medição.

Porém, isso nos leva a  outro problema: como modelar o primeiro estágio de nossa ponta de prova ? Precisamos ter uma impedância de entrada alta, mas também não queremos usar resistores de valores de resistência muito altos como $\large R_f$. Para mitigar isso, fazemos a amplificação ser 0.1, pois aí podemos economizar neste resistor. 

Para mitigar essa amplificação, e fazer o sinal voltar a ser o sinal original da tensão, adicionamos mais um estágio de amplificação. Desse modo, podemos escolher uma amplificação de 10 de modo a garantir que o valor original da tensão apareça no multímetro (0.1 * 10 = 1) ou podemos chavear em uma amplificação de 1, para sinais de tensão muito altos.

### AMPLIFICADOR DE ACOPLAMENTO CA

![[Pasted image 20261027063600.png]]

Aqui, vamos ter os capacitores de acoplamento de modo a evitar a presença de sinais CC em nosso amplificador, que passará a amplificar apenas o sinal CA, com alguns erros localizados.
f_2  No caso das equações constitui a frequência de largura de banda.
f_c1 e f_c2 consistem em frequências de corte dos capacitores.
Ademais, tem um erro nas fórmulas dadas. Vamos ter que, na verdade, a frequência de corte para dado capacitor é:
$$
\huge f_C=\frac{1}{2\pi RC}
$$
Ps. dado certo ganho, a frequência de corte é a frequência onde a amplificação do sinal passa a ser:
$$
\huge |A_{CL2}|=\frac{|A_v|}{\sqrt{2}}
$$

No caso do amplificador dado, isso consiste em uma queda de aproximadamente 3 decibeis na amplificação.

Para deduzir essas fórmulas é meio dedo no cu e gritaria, mas resumindo: Cada capacitor vai causar uma queda de tensão, o que vai gerar, em cada sistema resistência-capacitor, um ganho menor que 1, que se multiplicará ao ganho gerado pelo amplificador operacional em uso. 

Se temos ganho, vamos ter também queda de frequência e, portanto, podemos gerar frequências de corte, ou seja,  níveis de frequência em que vamos observar quedas significativas na amplificação do circuito.

Primeiramente, a fórmula da amplificação é bem trivial. Consiste simplesmente em um AOP conectado por realimentação negativa.

F_2 também é bastante trivial, é só a fórmula da largura de banda para um circuito qualquer de realimentação negativa.

Agora, as fórmulas para os capacitores são meio complicadas de deduzir. Para deduzir elas, precisamos lembrar que o ganho para qualquer sistema baseado em divisor de tensão é:
$$
\huge \frac{R_2}{R_1+R_2}
$$
Considerando a resistência depois do capacitor como R_2, e considerando Z a impedância total entre o resistor e o capacitor, chegamos em:
$$
\huge A_v=\frac{R}{|Z|}
$$
Sabemos, da análise CA, que:
$$
\huge Z = R-jX_C
$$
Portanto:
$$
\huge |Z| = \sqrt{R²+X_c²}
$$
Ou seja:
$$
\huge A_v=\frac{R}{\sqrt{R²+X_c²}}
$$
Queremos que a amplificação caia para $\large \frac{1}{\sqrt{2}}$ de seu valor original, logo que a amplificação original é simplesmente 1:
$$
\huge \frac{1}{\sqrt{2}} = \frac{R}{\sqrt{R^2+X_c^2}}
$$
Ou seja:
$$
\huge R\sqrt{2}=\sqrt{R^2+X_c^2}
$$
elevando tudo ao quadrado:
$$
\huge 2R^2= R^2+X_c^2
$$
De onde trivialmente chegamos em:
$$
\huge X_c=R
$$
Sabemos, também de análise CA, que $\large X_c=\frac{1}{2\pi fC}$. portanto:
$$
\huge \frac{1}{2\pi fC} = R \to f = \frac{1}{2\pi RC}
$$
QED.

### CIRCUITO COM LARGURA DE BANDA AJUSTÁVEL

![[Pasted image 20261104173532.png]]

Vamos deduzir suas fórmulas.

Primeiramente, podemos calcular o ganho da mesma forma como sempre calculamos, usando o terra virtual e a tensão da fonte e, posteriormente, os valores da tensão de entrada e saída do amplificador, de onde chegamos na fórmula comum dos amplificadores diferenciais que, neste caso, depende unicamente de $\large R_1$ e $\large R_f$.

Finalmente, precisamos formalizar B. Este é também chamado de fator de realimentação e surge devido ao divisor de tensão formado entre o R (variável) e $\large R_1$ (fixo). Da fórmula do divisor de tensão, vamos ter que o valor da tensão no divisor será de:
$$
\huge V = \frac{R || R_1}{R_f+(R||R_1)}V_{out}
$$
Chamamos este termo feioso de 'B', de modo que:
$$
\huge V = BV_{out}
$$
Portanto, encontramos que:
$$
\huge B = \frac{V}{V_{out}}=\frac{1}{A_v}
$$
Ademais, podemos usar a aproximação comum que dita que:
$$
\huge f_2=\frac{f_{unitario}}{A_v}=Bf_{unitario}
$$
Como queríamos demonstrar.

# CIRCUITOS COM AOP NÃO-INVERSOR
Até agora, vimos somente circuitos com AOP inversor. Vamos agora ver circuiots que usam amplificadores não-inversores.

### AMPLIFICADOR COM ACOPLAMENTO CA

![[Pasted image 20261104174943.png]]

Não tem muito mais a adicionar aqui, só um amplificador com acoplamento CA que nem o visto anteriormente, porém com um tipo de amplificador diferente, o que muda na amplificação do sinal.

ps. tem algo que eu não entendi exatamente o motivo pelo o qual foi mencionado, mas que foi, então irei mencionar aqui.

Da mesma forma como definimos B para o circuito anterior, podemos definir B para este circuito da seguinte forma:
$$
\huge B = \frac{R_1}{R_1+R_f}
$$
Que vai tender a 1 conforme a frequência tende a 0. Isso acontece pois quando a frequência tende a 0, o capacitor C3 vai tender a um circuito fechado, o que vai dar a impressão de que a resistência $\large R_1$ está indo para o infinito.

Tirando isso, vale destacar algo extremamente importante, a frequência de corte global consiste na frequência máxima de corte dos capacitores, de modo que a queda de 3 dB acontece unicamente em
$$
\huge f_{corte} = \max(f_{c1},f_{c2},f_{c3})
$$

### AMPLIFICADOR PARA DISTRIBUIÇÃO DE ÁUDIO

![[Pasted image 20261104175839.png]]

Aqui, temos simplesmente um amplificador que distribui uma saída por meio de 3 seguidores de tensão. Aqui, as fórmulas são bastante simples, e seguem exatamente as mesmas fórmulas que foram vistas anteriormente.

A única coisa que faltou explicar (ambos o livro e os slides) foi o papel de $\large R_2$. O papel deste consiste em regular a frequência de corte. Observa a posição dele dentro do circuito. Assumindo que o capacitor de entrada possua um valor de capacitância $\large C$, vamos ter que a frequência de corte de todo o sistema será igual a:
$$
\huge f_c=\frac{1}{2\pi R_2C}
$$
Portanto, $\large R_2$ tem o papel de controlar a frequência de corte de todo o circuito.

### GANHO DE TENSÃO CHAVEADO COM JFET

![[Pasted image 20261104180345.png]]

Mais um circuito extremamente simples, graças a Deus.

Primeiramente, o que é um JFET ? Este consiste simplesmente em uma chave eletrônica: sempre que ele  operado com uma tensão em nível baixo (abaixo da tensão de abertura), ele atua como um circuito aberto. Porém, no momento que esta tensão cruza este limiar, ele fecha o circuito, completando o terra. Quando isso acontece, para calcular a amplificação, fica necessário associar $\large R_2$ em paralelo com $\large R_1$ antes de computar a divisão do divisor de tensão não-inversor. Caso contrário, vamos ter que esta é simplesmente $\large \frac{R_f}{R_1}+1$.

# CIRCUITOS INVERSORES / NÃO INVERSORES

Aqui, vamos ter circuitos cujo amplificador pode funcionar simultaneamente como um amplificador inversor e não-inversor.
Ao mesmo tempo, podemos também ter simplesmente circuitos que acionam, simultaneamente, as entradas inversora e não-inversora. Isso pode gerar comportamentos interessantes pois o resultado consistirá na superposição do sinal resultante de apenas uma saída inversora acionada, com o sinal resultante de uma saída não-inversora acionada.

### INVERSOR - NÃO INVERSOR COMUTÁVEL

![[Pasted image 20261104181245.png]]

Aqui, podemos acionar a entrada não inversora por intermédio de uma chave. Caso a entrada não-inversora não seja acionada, vamos ter simplesmente um amplificador inversor, de onde tiramos que:
$$
\huge A_v=-\frac{R_f}{R_1}=-\frac{R}{R}=-1
$$
Esta configuração é a posição inferior, na qual a entrada não-inversora está aterrada.
Na configuração superior, vamos ter simultaneamente um amplificador inversor e não-inversor. Quando isso acontece, devemos antes calcular a amplificação não-inversora:
$$
\huge A_v=\frac{R_f}{R_1}+1=\frac{R}{R}+1=1+1=2
$$
já calculamos que a amplificação inversora é -1. Somando as duas, encontramos 1, que é o resultado da amplificação total na configuração superior.

### INVERSOR COMUTÁVEL CONTROLADO POR JFET

![[Pasted image 20261104182300.png]]

Mesma lógica de anteriormente. A única diferença é o JFET, que já foi explicado anteriormente. Ademais, o resistor antes da entrada não-inversora está lá simplesmente para ajudar o JFET a regular a tensão, ele não muda o comportamento não-inversor do amplificador.

### INVERSOR COM GANHO AJUSTÁVEL

![[Pasted image 20261105091248.png]]

Para verdadeiramente modelar este circuito, vamos precisar modelar os ganhos puramente inversores e puramente não-inversores deste circuito.

O ganho inversor, como mostra o circuito, é bem simples. Vamos ter que
$$
\huge A_-=-\frac{R_2}{R_1}
$$
Ao passo que, para calcular o ganho da etapa não-inversora, vamos ter um acúmulo de quedas de tensão: Primeiramente, vamos ter a queda de tensão por causa do divisor de tensão entre R_1 e a resistência variável (que chamarei a partir de agora de R_x) e a amplificação do amp-op. Associando as duas, encontramos que:
$$
\huge A_+=(\frac{R_2}{R_1}+1)(\frac{R_x}{R_1+R_x})
$$
Ademais, por superposição, vamos ter que o ganho total do sistema equivale a:
$$
\huge A_v=A_++A_-=(\frac{R_2}{R_1}+1)(\frac{R_x}{R_1+R_x})-\frac{R_2}{R_1}
$$

Disso, podemos deduzir os dois casos mostrados acima. Primeiro, quando R_x=0, vamos observar que todo o termo da esquerda vai cair para zero, apenas sobrando $\large -\frac{R_2}{R_1}$. Como queríamos demonstrar.
Ademais, quando fazemos $\large R_x=R_2$:
$$
\huge (\frac{R_2+R_1}{R_1})(\frac{R_2}{R_2+R_1})-\frac{R_2}{R_1}
$$
cortanto:
$$
\huge = \frac{R_2}{R_1}-\frac{R_2}{R_1}=0
$$
Como queríamos demonstrar.

### TROCADOR DE SINAL
![[Pasted image 20261105093202.png]]

Essa fórmula pode ser demonstrada da mesma forma que o inversor com ganho ajustável, e será deixada como exercício ao leitor.

### GANHO AJUSTÁVEL E REVERSÍVEL

![[Pasted image 20261105093621.png]]

Mesma coisa. O inversor é trivial:
$$
\huge A_-=-\frac{nR}{R}=-n
$$
Para calcular o não inversor, devemos associar as duas resistências em paralelo:
$$
\huge R = R || \frac{nR}{n-1}=\frac{nR}{2n-1}
$$
Agora, devemos apenas lembrar que existirá um divisor de tensão na entrada não-inversora devido à resistência variável. Para calcular esta não é dificil. Cálculos nos levam a chegar que o valor de sua amplificação será 'x', onde x é o valor que varia de 0 a 1 e enuncia a porcentagem do resistor que sobra depois do cursor. Vamos encontar:
$$
\huge A_+=x(\frac{nR}{\frac{nR}{2n-1}}+1)=x(2n-1+1)=2nx
$$
Logo:
$$
\huge A_v=2nx-n=n(2x-1)
$$
Quando x = 0, vamos ter que o ganho vai ser, trivialmente, -n. Quando x = 1, o ganho será +n, como queríamos demonstrar.

### INVERSOR DE FASE

![[Pasted image 20261105094725.png]]

O inversor de fase é verdadeiramente um circuito fascinante. Seu funcionamento é  o seguinte: para diferentes frequências, o capacitor vai operando em estágios diferentes, o que afeta a amplificação do estágio não-inversor e pode, portanto, causar mudanças na fase de saída. Um exemplo é considerarmos a frequência muito abaixo da frequência de corte. Quando isso acontece, o capacitor é um circuito fechado e, portanto, a amplificação não-inversora será 2, e a total será 1, totalizando uma inversão de fase de 0 graus. Porém, em uma frequência muito maior que a frequência de corte, o capacitor vai atuar como circuito fechado, fazendo com que o ganho não-inversor seja igual a 0, e o ganho total, portanto, seja igual a -1.
Tendo isso em mente, vale destacar que nem o livro nem o professor explicaram como calcular o deslocamento de fase para valores entre estes dois extremos, mas digo que a fórmula é bem bonita:
$$
\huge \phi = -2\arctan(\frac{f}{f_c})
$$
onde f é a frequência atual, e f_c é a frequência de corte do capacitor.

# CIRCUITOS AMPLIFICADORES SOMADORES
Para concuirmos (finalmente!) seguem algumas aplicações de amplificadores somadores:

### SUBTRATOR

![[Pasted image 20261105100015.png]]

O primeiro estágio é um inversor, de modo que sua saída vai ser -v1, e o segundo estágio é somador, de modo que sua saída vai ser
$$
\huge v_{out}=-R(\frac{-v_1}{R}+\frac{v_2}{R})=v_1-v_2
$$
QED.
### SOMA DAS DUAS ENTRADAS

![[Pasted image 20261105101435.png]]

Isso parece bem feio (e é) mas quando você olha fundo, você percebe que na verdade é apenas aplicação direta de amplificadores inversores com não-inversores, e que a soma total lá em cima vem do princípio da superposição.

### GERADOR DE MÉDIA

![[Pasted image 20261105101632 1.png]]

Apenas aplicação direta de amplificadores somadores. Basta lembrar que, para um amplificador somador:
$$
\huge v_{out}=-R_f(\frac{v_1}{R_1}+\frac{v_2}{R_2}+\frac{v_3}{R_3})
$$

Que a prova da equação principal deste circuito fica trivial.

### CONVERSOR D / A BINÁRIO PONDERADO

![[Pasted image 20261105102010.png]]

Consiste em uma das aplicações de um gerador de média, Vamos ter que aqui você vai receber os bits em cada uma das entradas de voltagem, e você vai 'cuspir' um valor analógico para eles.
Ps. Algo importante de se lembrar é que, neste caso, o resistor de 8R recebe o primeiro bit, e assim descendo até chegar no resistor de R, que recebe o último bit.

Usaríamos este tipo de conversor caso nós tivéssemos poucos bits, e precisão não fosse algo muito importante.

Isso se dá devido ao fato que este conversor é bastante dependente dos valores que cada resistor possui, algo que pode ser bastante problemático por geralmente estes variarem bastante em função do calor, carga, e outros fatores.

### CONVERSOR D / A DE ESCADA

![[Pasted image 20261105102321.png]]

Isso funciona da seguinte maneira: cada estágio que avançamos para a esquerda, adicionamos mais um '2R', de modo que a contribuição da corrente cai por dois a cada ciclo à esquerda. Podemos portanto construir a tabela:

| Bit | Resistor vertical | Contribuição para a saída |
| --- | ----------------- | ------------------------- |
| D3  | R4                | $(-V_{ref}/2)$            |
| D2  | R3                | $(-V_{ref}/4)$            |
| D1  | R2                | $(-V_{ref}/8)$            |
| D0  | R1                | $(-V_{ref}/16)$           |
Que ilustra o comportamento da contribuição de saída para cada um dos bits.