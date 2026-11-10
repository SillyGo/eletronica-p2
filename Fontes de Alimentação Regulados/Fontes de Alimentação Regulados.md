### INTRODUÇÃO
A qualidade de determinada fonte depende:
1. da regulação de carga
2. da regulação de linha
3. da resistência de saída.

O que isso significa? 
Primeiramente, regulação de carga: Quando temos uma carga que consome quantidades diferentes de corrente, geralmente a tensão de saída vai variar consideravelmente. Uma fonte é considerada de boa regulação de tensão quando essa variação é a mínima possível. Idealmente sendo 0.
Segundo: Regulação de Linha: vamos dizer que a tensão de entrada da fonte mude um pouco. É esperado que a tensão de saida fique aproximadamente constante para todos esses valores de tensão de entrada.
Terceiro: Resistência de Saída: queremos que a resistência equivalente de determinada fonte de tensão sempre se aproxime de 0, sendo esta, idealmente, igual a 0

### QUANTIFICANDO:
Podemos quantificar a regulação de carga por meio da seguinte equação:
$$
\huge Reg_{Q}=\frac{V_{0}-V_{max}}{V_{max}}100\%
$$ 
Aqui, vamos ter que $\large V_0$ é a tensão de saída quando a corrente consumida pela carga é igual a 0. Ao passo que $\large V_{max}$ é a tensão de carga quando a corrente de carga é máxima.
Um regulador será bom quando este valor for mínimo.

Podemos quantificar a regulação de linha da seguinte maneira:
$$
\huge Reg_L=\frac{V_{HL}-V_{LL}}{V_{LL}}100\%
$$
Onde $\large V_{HL}, V_{LL}$ são, respectivamente, as tensões de saída de  altas e baixa de linha.
Por "tensão de linha", refere-se à tensão de entrada. 

Quanto à resistência equivalente, podemos simplesmente usar a resistência de thévenin, e a seguinte expressão:
$$
\huge R_{th} = \frac{V_0-V_{max}}{I_{max}}100\%
$$
Onde estas tensões são, respectivamente, a tensão de carga para corrente de carga  nula e corrente de carga máxima, e $\large I_{max}$ é justamente a corrente máxima que a carga pode assumir.
Como mencionado, sempre vamos querer  a menor resistência possível.

ps. também podemos definir a regulação de carga por intermédio da Resistência de thévenin. Pode facilmente ser encontrado que:
$$
\huge Reg_Q=\frac{R_{th}}{R_{Lmin}}100\%
$$
Onde $\large $\large R_{Lmin}$ consiste na menor possível resistência de carga.
### REGULADORES

Vamos dizer que você tem uma fonte de tensão arbitrária. As regulações de carga e de linha dela vão sempre ser muito altas. Para tentar mitigar esse problema, geralmente se coloca um regulador de tensão entre a fonte e a carga.

Esses reguladores podem ser classificados como Shunt ou Série.
# REGULADORES SHUNT

![[Pasted image 20261108114604.png]]

O melhor exemplo é o regulador zener. Um dos circuitos reguladores mais simples, e ainda bem efetivos para determinadas aplicações.
Aqui, o diodo zener $\large V_z$ vai operar na região de ruptura, produzindo sua tensão de ruptura na tensão da carga. 
A tendência neste circuito é igual para todos os reguladores shunt: Um aumento na corrente de carga é respondido com uma diminuição na corrente shunt, e uma diminuição na corrente de carga é respondida com um aumento da tensão shunt, de modo que a tensão de ruptura do diodo seja sempre aplicada.

Para finalizar reguladores zener, precisamos apenas lembrar que:
$$
\huge I_S=\frac{V_{in}-V_{out}}{R_s}
$$
Será a corrente no resistor-série, que fica aproximadamente constante, contanto que a tensão de entrada também o seja, sendo pouco afetada por variações na corrente de carga.

### REGULADOR DE TENSÃO ZENER COM DIODO

![[Pasted image 20261108115129.png]]

Para grandes correntes de carga, vamos ter piora considerável de performance no regulador-zener.  Para evitar isso, podemos adicionar um transistor.
Devido ao transistor: quando aumentarmos a corrente de carga, isso vai ser respondido com um input maior dentro da base do transistor, o que vai gerar uma corrente de coletor que, junto com a corrente shunt já providenciada pelo zener, irá contribuir ainda mais para regular a tensão para grandes correntes de carga.

As equações deste circuito são bastante intuitivas.

### REGULADOR ZENER COM REGULAÇÃO

![[Pasted image 20261108115659.png]]

Aqui, a técnica empregada vai ser a de realimentação no transistor: aumentos na corrente de carga também vão gerar um aumento da corrente de retroalimentação, o que, por sua vez, irá causar uma maior corrente coletora-opositora, contribuindo, portanto, para a regulação de carga.

As fórmulas também são bastante intuitivas. Pelo divisor de tensão, vamos ter que a tensão de base vai ser:
$$
\huge V_B=\frac{R_1}{R_1+R_2}V_{out}
$$
Vamos também ter que, das leis do transistor:
$$
\huge V_B=V_{BE}+V_Z
$$
Rearranjando, encontramos o v out determinado 

Para projetar bem um circuito desses, é fortemente recomendado que R1 e R2 sejam muito maiores que a resistência de carga. Isso irá aumentar consideravelmente a eficiência total deste circuito.
### EFICIÊNCIA
Podemos definir a eficiência de qualquer regulador como sendo:
$$
\huge E_f=\frac{P_{out}}{P_{in}}100\%
$$
Onde $\large P_{out}=V_{out}I_L$, e $\large P_{in}=V_{in}I_S$.
Podemos ainda definir a potência do regulador como sendo:
$$
\huge P_{reg}=P_{in}-P_{out}
$$
Algo interessante de se notar é que, nos reguladores shunt, geralmente a potência dissipada em R_S é a maior potência dissipada de todo o circuito regulador.
# REGULADORES SÉRIE
Uma desvantagem dos reguladores shunt é seu consumo, e acima de tudo sua baixa eficiência.
Quando a eficiência é um critério que importa muito (de modo que se pode desprezar a complexidade crescente do circuito) vamos ter que usar reguladores série.

### SEGUIDOR ZENER

![[Pasted image 20261108122831.png]]

Aqui, vamos simplesmente ter um transistor em configuração de seguidor de emissor.
A corrente que vai passar por RS vai ser aproximadamente ignorável, de modo que podemos simplesmente aproximar e dizer que, aproximadamente, toda a corrente que entra no coletor vai ser a corrente que vai sair no $\large V_{out}$
Devido ao detalhe acima, dizemos que estes reguladores são "reguladores série".
Ademais, o transistor é chamado de transistor de passagem, devido ao fato que quase toda a corrente passa por ele.
Devido à substituição do resistor série por um transistor série, e devido ao fato que grande parte da potência dissipada é nesse resistor série, vamos ter que a eficiência vai ser maior pois a dissipação de potência no transistor de passagem vai ser consideravelmente menor.

### REGULADOR DE DOIS TRANSISTORES

![[Pasted image 20261108125415.png]]

Aqui, vamos ter a mesma coisa mas com dois transistores. Isso ajuda ainda mais a regular a tensão para grandes correntes de carga.
Aqui, devido ao fato da corrente de entrada ser aproximadamente igual à corrente de saída, vamos ter simplesmente uma eficiência de 
$$
\huge E_f=\frac{V_{out}}{V_{in}}100\%
$$
E vamos ter uma potência dissipada no circuito regulador de:
$$
\huge P=(V_{out}-V_{in})I_L
$$
