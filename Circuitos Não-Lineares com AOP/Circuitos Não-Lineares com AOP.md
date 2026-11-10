### CIRCUITOS COMPARADORES
às vezes, queremos comparar duas tensões para saber qual é a maior. Podemos fazer isso por intermédio de comparadores.

### COMPARADOR NÃO-INVERSOR

![[Pasted image 20261105111025.png]]

Aqui, simplesmente conectamos as duas entradas de um amplificador diretamente nas tensões que queremos comparar. Aqui, quando $\large v_{in}$ é positiva, isso produz a saturação positiva, caso contrário, saturação negativa.

Vale destacar que este tipo de comportamento ocorre unicamente quando consideramos o ganho em malha aberta do amplificador como sendo infinito. Para qualquer outra situação, vamos ter que:
$$
\huge v_{in, min}=\frac{\pm V_{SAT}}{A_{VOL}}
$$
É a mínima tensão que precisamos para produzir saturação.

Devido a este efeito, podemos dar zoom em uma ferramenta como um osciloscópio, onde vamos observar que existe uma região de transição linear entre as duas saturações. como mostra a figura abaixo.

![[Pasted image 20261105111348.png]]

### COMPARADOR INVERSOR

![[Pasted image 20261105111407.png]]

A única diferença é que iremos conectar a tensão de entrada na saída inversora, de modo que ele vai apresentar o comportamento inverso ao amplificador visto anteriormente.

No caso deste circuito, existe ainda mais uma diferença: A presença de diodos limitadores. Estes diodos irão evitar que seja alimentado o amplificador com uma tensão maior que 0.7 ou menor que -0.7.

Isto tem muitas aplicações, dentre estas, podemos citar a conversão de sinais senoidais para sinais quadrados, além é claro da comparação de dois sinais.

### SAÍDA LIMITADA

![[Pasted image 20261105112245.png]]

Podemos limitar a sáida de um amplificador por intermédio de diodos zener. Aqui, vamos ter, independentemente do sinal da onda, sempre um diodo zener atuando na região ativa, e outro atuando na região de ruptura, forçando uma determinada tensão.

ps. algo que me confundiu inicialmente era quem causava a região de ruptura no zener. Quem faz isso não é a fonte, e sim a saída do amplificador, que faz com que, sempre, um dos zeners atue em ruptura, causando uma saída de 5 volts constante (até invertermos a orientação)

Consideremos um outro exemplo de saída limitada:

![[Pasted image 20261105112735.png]]

Aqui, no semiciclo positivo, o diodo não faz nada, permitindo que toda a tensão de saturação passe para $\large v_{out}$. Porém, no semiciclo negativo, vamos ter que o diodo zener vai começar a conduzir corrente, deixando antes dele uma tensão de 0.7 que passará para $\large v_{out}$, produzindo o sinal mostrado à direita.

### COMPARADORES DE REFERÊNCIA DIFERENTE DE 0

![[Pasted image 20261105113623.png]]

É trivial perceber que a entrada inversora passa a receber voltagem de um divisor de tensão, que modifica o valor mínimo que $\large v_{in}$

Neste caso, o ponto de comutação é justamente o ponto de inversão da saturação negativa para a saturação positiva.

Podemos calcular ele por intermédio de:
$$
\huge V_{com}=\frac{R_2}{R_1+R_2}V_{CC}
$$
Ele é descrito no slide como o ponto de referência.
# COMPARADORES COM HISTERESE

Vamos dizer que temos uma entrada com bastante ruído. Se a tensão de entrada estiver perto do ponto de comutação do amplificador, pode acontecer de termos uma saída muicho loka. Para evitar isso, podemos utilizar de um circuito de realimentação positiva, algo que vai fazer com que ele tenha dois pontos de comutação / histerese distintos.

### SCHMITT TRIGGER

![[Pasted image 20261105174439.png]]

O schmitt trigger é um circuito absolutamente lindo. O seu funcionamento é semelhante a alguns circuitos digitais com memória.

Para entender seu funcionamento, devemos antes calcular a tensão na entrada não-inversora. Logo que esta recebe a retroalimentação de $\large v_{out}$, vamos ter que ela vai ser igual a:
$$
\huge V_+=\frac{R_1}{R_1+R_2}V_{out}
$$
Devido ao divisor de tensão. Chamamos essa fração do divisor de tensão de $\large \beta$, que é a fração de realimentação que havíamos visto enquanto estudávamos circuitos lineares com amplificadores operacionais.
Podemos dizer, portanto, que:
$$
\huge V_+=\beta V_{out}
$$
Onde a fração de realimentação vai ser algum valor constante para nosso circuito.
Examinemos o que acontece quando $\large V_{out}$ se encontra inicialmente em estado de saturação positiva: A realimentação vai continuar jogando uma tensão de $\large \beta V_{out}$ para a entrada não-inversora, de modo que, para ocorrer comutação, vamos precisar de uma tensão inversora superior ou igual a esta. O que nos dá nosso primeiro ponto de comutação (chamado de UTP, ou "Upper Trigger Point"):
$$
\huge UTP = \beta V_{out}=\beta V_{sat}
$$
Logo que neste caso, a tensão de saída será a tensão de saturação do próprio amplificador operacional.

Agora, vamos dizer que o circuito está saturado negativamente. A realimentação vai continuamente ficar alimentando uma tensão negativa de $\large -\beta V_{sat}$ para a entrada não-inversora. Portanto, para comutar, vamos precisar de uma tensão igual ou superior (em módulo) a esta na entrada inversora. Definimos este ponto como LTP, ou "Lower Trigger Point":
$$
\huge LTP = -\beta V_{sat}
$$
QED.

Podemos ainda definir mais um valor: O valor de histerese. Definimos "histerese" como sendo o valor da distância entre o UTP e LTP. Trivialmente, isto nos dá:
$$
\huge Histerese=H=2\beta V_{sat}
$$Podemos ainda projetar um schmitt trigger com saída negativa aterrada e positiva retroalimentada e alimentada direto na fonte: 

![[Pasted image 20261105180145 1.png]]

Neste caso, vamos ter que, da lei dos nós em $\large V_+$ e do terra virtual formado:
$$
\huge \frac{V_{in}}{R_1}=-\frac{V_{out}}{R_2}
$$
Caso a saturação seja positiva, $\large V_{out}=V_{sat}$, e:
$$
\huge V_{in}=LTP=-\frac{R_1}{R_2}V_{sat}
$$
Caso a saturação seja negativa, $\large V_{out}=-V_{sat}$ e, portanto:
$$
\huge V_{in}=UTP=\frac{R_1}{R_2}V_{sat}
$$
QED.
# COMPARADORES DE JANELA

Um comparador simples simplesmente detecta quando a tensão excede certo limiar. Comparadores de janela são únicos no sentido que eles apenas detectam quando a tensão está dentro de determinado limiar chamado de janela.

Podemos considerar um comparador de janela inversor, 

![[Pasted image 20261105180756.png|593]]

Como ilustrado na imagem acima, o comparador por janela inversor funciona de modo a produzir 0 para quando o valor de $\large V_{in}$ está entre LTP e UTP, e $\large V_{sat}$ caso contrário.

Abaixo temos um diagrama deste tipo de circuito:

![[Pasted image 20261105180933.png|607]]

No caso deste circuito, podemos manualmente selecionar valores de HTP e LTP de modo a produzir a histerese.

Isto também é um circuito bem elegante: Se $\large 3 < V_{in} < 4$, o amplificador A1 vai produzir saída negativa, e o A2 também, fazendo com que ambos diodos operem em corte e, portanto, produza saída baixa (0). Caso contrário, vamos ter no mínimo um dos amplificadores produzindo saída positiva, que vai fazer o diodo começar a conduzir, gerando saturação, pois cada um dos amplificadores mostrados opera como comparadores simples.
# INTEGRADORES

Integradores são circuitos que fazem uma operação de integração.
Às vezes chamamos o integrador de "O integrador Miller", em homenagem ao bro que pensou nele pela primeira vez

![[Pasted image 20261105185241.png]]

Acima temos o circuito base de um integrador. É muito semelhante à estrutura de amplificadores inversores, com a diferença de que temos, agora, um capacitor na realimentação.

A intuição aqui é realmente muito simples. Primeiramente, devemos lembrar de algumas fórmulas importantes. A mais importante de todas é a fórmula da corrente do capacitor. Vamos deduzir ela:

Sabemos que $\large C = \frac{q}{V_C}$. E sabemos também que $\large q=\int i dt$. Portanto, rearranjando:
$$
\huge \int i dt=CV_C \to i_C=C\frac{dV_C}{dt}
$$
Ademais, sabemos também que toda a corrente que sai de $\large v_{in}$ passa pela realimentação ao invés de entrar no amplificador. Por causa disso, vamos ter que a corrente do capacitor é igual à corrente que sai de $\large V_{in}$, que por sua vez é igual a:
$$
\huge I=I_C=\frac{V_{in}}{R}
$$
devido ao terra virtual. Ademais, como a tensão do lado esquerdo do capacitor é 0, e a tensão do lado direito é $\large V_{out}$, vamos ter que:
$$
\huge V_C=0-V_{out} \to V_C=-V_{out}
$$
Substituindo todos nossos achados:
$$
\huge \frac{V_{in}}{R}=-C\frac{dV_{out}}{dt}
$$
Rearranjando, encontramos:
$$
\huge \frac{dV_{out}}{dt}=-\frac{1}{RC}V_{in}
$$
Portanto:
$$
\huge V_{out}=-\frac{1}{RC}\int V_{in}dt
$$
Como queríamos demonstrar, o circuito faz uma operação de integração.
# DIFERENCIADORES

Derivadores são, simplesmente, circuitos que realizam a operação de derivação. Curiosamente, a única diferença estrutural destes pros integradores está na posição do capacitor, como ilustra o circuito abaixo:

![[Pasted image 20261105190623.png]]

Aqui, vamos ter que a tensão no capacitor é igual a:
$$
\huge V_C=V_{in}
$$
Trivialmente. Ademais, vamos ter que a corrente de realimentação vai ser igual a:
$$
\huge \frac{0-V_{out}}{R}=I=I_C
$$
Logo que:
$$
\huge I_C=C\frac{dV_C}{dt}
$$
Podemos substituir nossos achados e concluir que:
$$
\huge -\frac{V_{out}}{R}=C\frac{dV_{in}}{dt}
$$
Rearranjando, encontramos que:
$$
\huge V_{out}=-RC\frac{dV_{in}}{dt}
$$
Que tira a derivada da tensão de entrada. Portanto, temos um circuito que faz uma diferenciação, QED.
# CONVERSÃO DE FORMA DE ONDA

### DE SENOIDE PARA RETANGULAR:
Podemos simplesmente empregar um schmitt trigger, nada muito complexo.

### DE RETANGULAR PARA TRIANGULAR
O leitor ávido já deve ter percebido que aqui vamos precisar usar um integrador. Mas para esse leitor eu faço uma pergunta: E se tivermos uma componente DC somada à componente AC ? Caso isso aconteça, o integrador vai continuamente magnificar essa componente CC linearmente, progressivamente deslocando o sinal gerado na saída! Para evitar isso, podemos colocar um resistor em paralelo com o capacitor do integrador, de modo a aproveitar da mesma lógica que os capacitores de desvio, quando estávamos estudando análise CC / CA. Isso nos leva ao seguinte circuito:

![[Pasted image 20261105191521.png]]

Dito isso, infelizmente (caro leitor,) nem o livro nem os slides de Adrien mostram como chega nessa bela fórmula descrita ao lado. Porém, não acho que ela deva ser complicada de se demonstrar,  acho que é aplicação simples de cálculo. Eh, fica como exercício para o leitor.

### DE TRIANGULAR PARA PULSO
Para isso, podemos simplesmente fazer uso de um comparador com ponto de referência desviado por divisor de tensão.

![[Pasted image 20261105191842.png]]

Por causa disso, vamos ter que o comparador só vai produzir pulso quando o triângulo passar de determinado threshold definido. Podemos aumentar esse threshold (até certo nível, ou seja, o máximo possibilitado pelo amplificador) até chegarmos em um pulso bem fino.
Especificamente para este caso, não poderíamos usar um shmitt trigger. Por que ? (importante, eu acho)

