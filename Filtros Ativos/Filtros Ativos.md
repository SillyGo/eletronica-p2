# INTRODUÇÃO
Filtros são sistemas eletrônicos fascinantes. Sua função núcleo é permitir a passagem de sinais com determinadas frequências, e bloquear outras frequências indesejadas de passarem.
Existem dois tipos de filtros:

FILTROS PASSIVOS: estes são geralmente construídos com elementos básicos, como resistores, capacitores, e indutores. Este tipo de filtro é difícil de sintonizar, e  é mais usado para frequências que excedem 1MHz. Eles são chamados de filtros "passivos" pois não apresentam ganho de potência.
FILTROS ATIVOS: estes são filtros que são construídos com resistores, capacitores, e amplificadores operacionais (devido aos quais estes tipos de filtros vão passar a apresentar ganho de potência, motivo pelo qual eles são ditos filtros "ativos")
Estes filtros são mais usados para frequências abaixo de 1MHz, e são bem fáceis de serem sintonizados.

ps. "Sintonizar" um filtro consiste em ajustar os valores de seus componentes de modo que o filtro passe a filtrar a faixa de frequências desejada.

# RESPOSTAS IDEAIS
Primeiro, uma questão de notação: a "Resposta em Frequência" de um filtro consiste no gráfico ganho de tensão x frequência. Semelhante àqueles que vimos quando estávamos falando sobre largura de banda.

Existem 5 tipos de filtros:
1. Passa-Baixa
2. Passa-Alta
3. Passa-Faixa
4. Rejeita-Faixa
5. Passa-Todas (deslocador de fase)

### PASSA-BAIXA
um filtro passa-baixa é um filtro que permite a passagem de todas as frequências ABAIXO de determinado limiar.
Vamos, portanto, ter uma frequência de corte, que é o momento a partir do qual o filtro começa a filtrar.
A região entre a frequência 0 e a frequência de corte denomina-se banda de passagem, ao passo que as frequências acima da frequência de corte denominam-se "banda de corte".
Temos ainda a região de decaimento entre a banda de passagem e a banda de corte, que em circuitos reais não é vertical, e denomina-se de região de transição.

PASSA BAIXA IDEAL: tem transição vertical, atenuação (perda de sinal) nula na banda de passagem e infinita na banda de corte.

Idealmente, o ganho de fase para este tipo de circuito é nulo, de modo a preservar o formato da onda de entrada sempre.

### PASSA-ALTA
Vey, é literalmente igual ao passa-baixa mas com todas as frequências acima de corte sendo chamadas agora de "banda de passagem", e todas as frequências entre 0 e o corte sendo denominadas "banda de corte".
Ele segue os mesmos princípios de atenuação que o passa-baixa, porém invertido.

### PASSA-FAIXA
Vamos ter aqui duas frequências de corte: uma frequência de corte inferior, e outra superior. Este filtro permite a passagem de frequências que estejam dentro do intervalo entre a frequência de corte inferior e a superior. Não estudei o resto destes slides, mas imagino que este tipo de filtro possa ser construído associando um filtro passa-baixa com um filtro passa-alta.

Definimos sua largura de banda como sendo:
$$
\huge BW = f_2-f_1
$$
Também temos uma nova medida chamada "frequência central", definida como a média geométrica das duas frequências de corte:
$$
\huge f_c=\sqrt{f_1f_2}
$$
Podemos ainda definir o "fator Q", que vai ser bem importante no futuro, mas por enquanto só será usado para classificar filtros. O fator Q define-se como:
$$
\huge Q =\frac{f_c}{ BW}
$$
Se Q for maior que 1, o filtro é chamado de banda estreita. Caso contrário, é chamado de "Banda larga".

### REJEITA-FAIXA
É o inverso do filtro passa faixa. O filtro rejeita faixa rejeita a faixa que, no passa faixa, seria aceita como a banda de passagem.

### PASSA-TODAS
Permite a passagem de todas as frequências.
Sua utilidade como filtro consiste no modo como ele afeta a fase de determinado sinal. Com ele, podemos alterar a fase de um sinal sem alterar sua amplitude.
Caso contrário, ele não filtra nenhuma frequência.

# RESPOSTAS APROXIMADAS
Nunca vamos conseguir chegar nas respostas ideais mencionadas acima, porque a vida não é um morango. Podemos, porém, construir respostas aproximadas às respostas ideais. 
Primeiro, devemos definir alguns conceitos:
$$
\huge A_t=\frac{V_{out}}{V_{out(med)}}
$$
Aqui, temos a fórmula clássica da atenuação. Como se pode muito bem ver, é quase impossível aqui termos atenuação 0 ou infinito. 
Define-se $\large V_{out(med)}$ como a tensão de saída da região de banda média. A região de banda média é aquela localizada dentro da banda de passagem para a qual a tensão de saída vai ser aproximadamente constante.
PS. logo que a atenuação é geralmente escrita em decibéis, é importante lembrar que :
$$
\huge A_{t(dB)}=-20\log(A_t)
$$
![[Pasted image 20261109125643.png]]

No caso da imagem acima, teríamos como a banda média o espaço entre 0 e  $\large f_c$. Entre $\large f_c,f_s$ teríamos uma região de transição entre a passagem e o corte.

### ORDEM DE UM FILTRO
Para todos filtros, temos uma ordem. A ordem é determinada pelo número de circuitos RC (ou polos) que um determinado circuito contêm. Logo, porém, que isso é uma coisa muito difícil de se contar, podemos determinar a ordem de um determinado circuito contando o número de capacitores e indutores que ele contêm.

# APROXIMAÇÕES (R.A PARTE 2)
Isso vai ser basicamente "respostas aproximadas" parte 2. Aqui vamos ter várias aproximações para a resposta de filtros.

### APROXIMAÇÃO BUTTERWORTH

![[Pasted image 20261109130019 1.png]]

O decaimento deste filtro, porém, é consideravelmente lento: ele fica em apenas 20dB por década (ou seja, da frequência 100Hz para 1kHz, ele vai decair apenas 20dB). Mas pode ser um filtro bastante utilizado devido à resposta plana na banda de passagem

### APROXIMAÇÃO CHEBYSHEV

![[Pasted image 20261110134831.png]]

O filtro chebyshev contêm uma vantagem: o fato de seu decaimento ser mais rápido que o filtro buttersworth.
Tem um porém:  o ripple que ocorre antes do decaimento.
Em casos como estes, vamos ter que o número de ripples irá depender da ordem do  filtro. Teremos que:
$$
\huge n_{ondas}=\frac{n}{2}
$$
Onde 'n' consiste na ordem do filtro.
### APROXIMAÇÃO CHEBYSHEV INVERSA

![[Pasted image 20261110135039.png]]

Decaimento igual à de chebyshev. A diferença é que, dessa vez, a região plana é a banda de passagem, ao passo que todo o resto possui uma ondulação considerável, que pode ser bem ruim para determinadas aplicações.
### APROXIMAÇÃO ELÍPTICA

![[Pasted image 20261110135134.png]]

Este é o filtro que possui o decaimento mais rápido de todos. Não é especificado a velocidade deste decaimento, mas ele é bastante rápido. O sacrifício é o fato de agora existirem oscilações na região de corte e de passagem.
### APROXIMAÇÃO BESSEL

![[Pasted image 20261110135243.png]]

Ele possui também uma .característica monotônica (assim como butterworth) mas o decaimento para filtros de bessel são ainda mais lentos que butterworth, assumindo que os dois operam na mesma ordem
Existe, porém, um motivo para a existência deste filtro: ele desloca as fases linearmente com relação à frequência. Isso significa que, para sinais não-senoidais, eles vão ter suas fases deslocadas linearmente com relação à frequência. 
Por causa disso, a forma do sinal de saída vai ser aproximadamente a mesma que a do sinal de entrada, algo bastante vantajoso quando não se quer que haja distorção em sinais não-senoidais.
# RESPOSTAS AO DEGRAU PARA AS APROXs.

Estuda a resposta ao degrau dessas aproximações.

### BUTTERWORTH & CHEBYSHEV INVERSO

![[Pasted image 20261110135756.png]]

Resposta inicia com overshoot, depois apresenta certo wobble até estabilizar em 1 volt.
Isso acontece devido ao fato que, como vimos, essas duas respostas possuem um certo decaimento, mas possuem ganho ideal na banda de passagem.
### CHEBYSHEV E ELÍPTICO

![[Pasted image 20261110140112.png]]

Como dá para ver, acontece um wobble ainda maior. Isso se dá em razão do wobble que estas duas aproximações possuem na banda de passagem.
### APROXIMAÇÃO DE BESSEL

![[Pasted image 20261110140318.png]]

Consiste em uma resposta quase perfeita. Devido a este fato, geralmente utilizamos muito este tipo de filtro em aplicações como filtragem de sinais digitais, onde possuímos vários degraus em série.
E eu pensando inicialmente que o filtro de bessel não havia aplicações reais.

# ESTÁGIOS DE PRIMEIRA ORDEM

Estágios de filtros ativos de 1ra ordem ou 1 polo são aqueles que possuem ordem 1, ou seja, possuem apenas 1 capacitor. 
Podemos, pois, usar eles apenas como filtros passa-baixa, logo que passa-faixa e rejeita-faixa só podem ser implementados para estágios de ordem superior.

### FORMA 1

![[Pasted image 20261110140748.png]]

Aqui, temos a representação mais simples de todas. Quando a frequência passa da frequência de corte, vai começar a ser introduzida reatância que lentamente vai transformando o capacitor em um curto circuito, até este realmente virar um e a tensão na entrada não-inversora virar 0. Quando isso acontece, vamos ter que a tensão de saída vai ser 0 devido ao terra virtual. Quando isso acontece, vamos ter que a frequência chegou na banda de corte.
Ademais, este amplificador está na configuração "seguidor de tensão", o que implica que o ganho total neste caso, assumindo uma frequência suficientemente baixa, vai ser unitário.

### FORMA 2

![[Pasted image 20261110141205.png]]

Aqui, vamos ter um estágio de retroalimentação na entrada inversora que transforma este amplificador para um amplificador não-inversor, de modo que seu ganho vai ser expresso como:
$$
\huge A_v = \frac{R_2}{R_1}+1
$$
Ademais, nosso circuito RC agora vai ser entre $\large R_3$ e $\large C_1$, de modo que a nossa frequência de corte passa a ser
$$
\huge f_c=\frac{1}{2\pi R_3C_1}
$$
Como já vimos muitas vezes.
Aqui, vamos ter a implementação de um filtro de Butterworth, logo que a queda deste filtro, além da frequência de corte vai ser exatamente igual a 20dB por década.

### FORMA 3

![[Pasted image 20261110141525.png]]

Aqui, se for desconsiderado o capacitor de retroalimentação, vamos simplesmente ter um ganho igual ao ganho de um amplificador inversor, que já está escrito.
Mesma coisa para a frequência de corte, que vai ser bem fácil de ser deduzida sozinha.
Este caso que eu descrevi, onde deprezamos o capacitor, só pode ser considerado para baixas frequências, onde este pode ser considerado uma malha aberta ao invés de uma malha fechada, como ocorre em frequências mais altas. Neste caso, onde a frequência atinge a banda de corte, vamos ter que o capacitor irá se comportar que nem uma malha fechada, algo que, por sua vez, transforma o amplificador em um simples seguidor de tensão, onde o ganho total será igual a 0, conforme desejávamos.

### E AS OUTRAS APROXIMAÇÕES ?
Todas as aproximações que possuem wobble não podem ser implementadas com n = 1, elas requerem um circuito com mais polos,  justamente por possuírem a oscilação descrita. Portanto, podemos ao máximo representar filtros de butterworth com 1 polo só.

# ESTÁGIOS PASSA-ALTA DE PRIMEIRA ORDEM

Estes serão circuitos extremamente parecidos com os circuitos que vimos anteriormente para passa-baixa.
### 1 FORMA

![[Pasted image 20261110142037.png]]

Inicialmente, o ganho vai obviamente ser 0, pois o capacitor vai se comportar como malha aberta até a frequência de corte. Quando chegamos nela, vamos ter a região de transição, até o capacitor começar a se comportar como malha fechada, momento a partir do qual toda a tensão de $\large v_{in}$ é passada para o amplificador. Quando isso acontece, vamos ter simplesmente um amplificador seguidor de tensão e, portanto, um ganho unitário.

### FORMA 2

![[Pasted image 20261110142237.png]]

Aqui, vamos ter um circuito novamente quase igual à representação passa-baixa, e que vai seguir a mesma lógica que anteriormente.

Assim como o seu antecessor em passa-baixa, vamos ter uma saída com decaimento de 20dB por década.

### FORMA 3

![[Pasted image 20261110142341.png]]

Este vai ser o único das formas vistas até agora que vai ser mais diferentão.
Quanto a diminuir a tensão de entrada para frequências mais baixas, creio que isso segue como algo bem fácil de ser observado para $\large C_1$.
O único ponto de dúvidas aqui talvez seja a questão do ganho. Vamos decompor isso:
É conhecido que a reatância X_c de um capacitor qualquer é dada por:
$$
\huge X_c=\frac{1}{2\pi fC}
$$Vamos ter, portanto, que em CA cada um desses capacitores vai se comportar como um resistor. Quando isso acontece, vamos ter um simples amplificador inversor, cujas resistências são as capacitâncias dos capacitores. Portanto, vamos ter que, em CA, o ganho deste amplificador será igual a:
$$
\huge A_v=\frac{X_{c2}}{X_{c1}}
$$
Portanto:
$$
\huge A_v=-\frac{\frac{1}{2\pi fC_2}}{\frac{1}{2\pi fC_1}}=-\frac{C_1}{C_2}
$$
Como queríamos demonstrar (QED).
# FILTROS PASSA-BAIXA VCVS DE SEGUNDA ORDEM E GANHO UNITÁRIO

Os estágios de segunda ordem são consideravelmente mais comuns por serem mais fáceis de serem estudados e implementados. Geralmente construiremos estágios de ordem maior por intermédio da associação em cascata de estágios de segunda ordem.

Cada estágio de segunda ordem será possuidor de uma "Frequência ressonante" e um fator Q, que auxiliará em determinar a amplificação máxima.

### SEGUNDA ORDEM 1:

![[Pasted image 20261110180305.png]]

Um  exemplo de filtro de ordem superior é o acima. 
Aqui, conforme a frequência se aproxima de 0, os capacitores irão atuar como circuitos abertos, o que vai fazer com que o amplificador vire simplesmente um seguidor de tensão. Porém, conforme a frequência passa da frequência de corte e passa a atingir valores mais altos, vamos ter que os capacitores passam a se comportar como circuitos fechados, o que vai causar um aterramento da entrada não-inversora, e uma consequente geração de saída igual a 0.
Por causa disso, observamos que este é um circuito passa-baixa.
Aqui, existem algumas coisas que vão ser diferentes dos de primeira ordem. Por exemplo, vamos ter aqui um fator Q com maior importância.
Para circuitos de segunda ordem como o acima, vamos ter:
$$
\huge Q = 0.5\sqrt{\frac{C_2}{C_1}}
$$
Neste tipo de circuito, aumentar o fator Q corresponde a aumentar o fator de realimentação positiva do circuito, o que vai gerar picos na resposta de frequência, como mostra o gráfico abaixo.

![[Pasted image 20261110180803.png]]

Ademais, devido à existência de vários circuitos RC neste circuito, vamos ter que calcular uma medida chamada frequência de polo, definida como:
$$
\huge f_p=\frac{1}{2\pi \sqrt{R_1R_2C_1C_2}}
$$
O que é parecido às fórmulas de frequência de corte vistas anteriormente, mas usando meio que uma lógica de média geométrica.
Neste caso, a frequência de corte total do circuito pode ser definida como:
$$
\huge f_c=K_cf_p
$$
Onde a constante listada será dependente do Q da seguinte forma:
1. Se Q = 0.707 (resposta de butterworth), $\large K_c$=1
2. Se Q = 0577 (resposta de bessel), $\large K_c$=0.786
Ademais, vamos ter que, para os dois filtros listados, a frequência de corte continua sendo o ponto em que a atenuação é de 3dB.

### FILTROS DE ORDEM MAIOR
Como mencionado anteriormente, estes filtros podem facilmente ser construídos por meio da associação em cascata de circuitos de segunda ordem.
Aqui, intuitivamente, a atenuação total vai ser a soma das atenuações de cada etapa do circuitos
Por causa disso, (por exemplo) dois circuitos em cascata, cada um com respostas de butterworth, não vão produzir uma resposta de butterworth na saída, isso acontece porque, se eles produzirem resposta de butterworth, eles vão causar, cada, uma atenuação de 3dB na frequência de corte, o que por sua vez vai totalizar uma atenuação de 6dB na frequência de corte, o que não é o que queremos, logo que queremos apenas uma atenuação de 3dB.
Por isso, vamos precisar, para produzir uma resposta de butterworth, de circuitos individuais com fatores Q diferentes entre si (um maior e outro menor que 0.707), de modo que suas atenuações em corte somadas totalizem 3dB.

Podemos usar os valores desta tabela para produzir respostas de butterworth para circuitos de ordem maior:

![[Pasted image 20261110182621.png]]

# OUTROS FILTROS DE SEGUNDA ORDEM

### FILTROS PASSA-BAIXA DE COMPONENTES IGUAIS

![[Pasted image 20261110182707.png]]

Aqui, temos simplesmente um passa baixa conectado a um amplificador não-inversor. As componentes iguais permitem que a média geométrica resulte numa forma mais palatável da frequência de polo. Porém, a frequência de corte ainda segue sendo calculada da mesma forma que anteriormente, de modo que precisamos conhecer K_c por meio do valor obtido em Q.

Algo a ser notado, inclusive, é o valor bizarro de  Q ... nem o livro nem os slides mostram como demonstrar ... Eu acho que é algo a ver com a impedância e reatância de cada capacitor ...

### PASSA-ALTA DE 2DA ORDEM E GANHO UNITÁRIO

![[Pasted image 20261110183051 1.png]]

Observa-se que, tal qual anteriormente, para encontrar um circuito de segunda ordem passa-alta apenas pegamos o circuito passa-baixa de ganho unitário (visto anteriormente) e trocamos um resistor de lugar com um capacitor.
Dito isso, me perdoe, mas também não é explicado de onde veio esse Q.

### PASSA-ALTA DE 2NDA ORDEM E GANHO > 1

![[Pasted image 20261110183232.png]]

Mesma coisa que o passa-baixa de ganho maior que 1. Inclusive a mesma fórmula do fator Q. 