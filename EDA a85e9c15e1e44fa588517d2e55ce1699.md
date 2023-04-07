# EDA

### Análise de Algoritmos (introdução)

O que significa analisar algoritmos?

Ao analisar um algoritmo, tenta-se prever, ou, pelo menos, ter uma ideia da quantidade de recursos que será utilizada ao executá-lo. Isso pode ser feito em função de várias coisas e dentre elas está o tempo de execução, uma variável muito utilizada.

Assim, dependendo do algoritmo utilizado, a quantidade de entradas pode aumentar significativamente o tempo de execução, enquanto em outros o tempo de execução não é tão drasticamente afetado mesmo que a quantidade de entradas seja muito maior. 

No gráfico abaixo, o Selection sorte fica bem mais lento quando as entradas aumentam, diferente do que acontece com os outros algoritmos listados.

![https://joaoarthurbm.github.io/eda/posts/introducao-a-analise/comparacao-ordenacao.jpeg](https://joaoarthurbm.github.io/eda/posts/introducao-a-analise/comparacao-ordenacao.jpeg)

Hipótese base da análise de algoritmos e operações primitivas

> Hipótese: O custo de operações primitivas é constante.
> 

Em tese, todas as operações primitivas apresentadas abaixo possuem o mesmo tempo de execução. Entretanto, na vida real, esse custo pode variar de acordo com a máquina, a linguagem etc, mas a variação é insignificante.

**Operações Primitivas**

- Avaliação de expressões booleanas (i >= 2; i == 2, etc);
- Operações matemáticas (*, -, +, %, etc);
- Retorno de métodos (return x;);
- Atribuição (i = 2);
- Acesso à variáveis e posições arbitrárias de um array (v[i]).

Num algoritmo simples, o custo é totalizado com 3 passos simples:

1. Identificar primitivas 
2. Identificar seu número de execuções                               
3. Somar o custo total.

> Dizer que um algoritmo tem custo constante significa dizer que o seu tempo de execução independe do tamanho da entrada.
> 

Com base nisso, o custo de operação será a soma das primitivas, PORÉM, a medida que os algoritmos ficam mais refinados, esse custo começa a levar em consideração outras coisas.

Condicionais e o pior caso 

O pior caso é o mais comum de acontecer. Fato. Quando pensamos nessa possibilidade, já eliminamos soluções ruins. Num algoritmo que calcula a aprovação de um aluno, por exemplo, o pior caso será a reprovação. Se isso acontece, uma parte do código menos signficativa deixa de ser executada. Como há uma condicional, isso muda o passo 2, pois primitivas podem ser excluidas, somadas, duplicadas, etc no processo.

Iteração

A iteração afeta o número de vezes que uma primitiva é executada. Ela pode ser n vezes, ou n + 1 vezes, talvez.

Com isso o valor final não é mais apenas a soma das primitivas e agora leva em consideração o numero de vezes que elas são executadas.

Loops aninhados

Devemos analisar com CALMA quantas vezes cada primitiva vai ser executada e levar em consideração os loops internos e sua relação de dependência com os mais externos.

### Análise Assintótica

Ordem de crescimento

Ao analisar uma função, pode-se abstrair algumas informações e ainda assim ser possível identificar sua ordem de crescimento, o que é bastante útil quando trata-se de algoritmos com valores altos de entrada. 

Como isso é feito?

- Ignorando constantes
- Ignorando expoentes de menor magnitude

Mas por que esses valores podem ser ignorados? Simplesmente pelo fato deles serem insignificantes quando comparados com um n² ou n³, por exemplos. Ou seja: não fazem diferença real numa função que trabalha com valores altos.

Exemplo

$f(n)=3c + 2c n+3∗n2/2+c∗(n2+n)/2$

Realizando os processos de abstração, podemos dizer que a função acima possui uma ordem de crescimento de n², ou seja, é uma função quadrática.

> Quando observamos tamanhos de entrada grande o suficiente para tornar relevante apenas a ordem de crescimento do tempo de execução, estamos estudando a eficiência assintótica.
> 

**Notação Theta  $Θ$**

De acordo com o material utilizado com base neste resumo, aka material do prof João Arthur: 

> Para duas funções $f(n$) e $g(n)$, dizemos que $f(n)$ é $Θ(g(n))$ se $0≤c1∗g(n)≤f(n)≤c2∗g(n),∀n≥n0$
> 

Mas o que isso quer dizer? Basicamente, que o crescimento da nossa função f(n) é igual ao da função g(n). Vou demonstrar isso usando uma função bem simples: $f(n) = 3n + 3.$

**Passo 1:** Vamos abstrair a função 3n + 3.

3n + 3 passa a ser apenas n, ou seja, uma função linear e agora assumirá o valor de g(n). O valor de f(n) permanecerá o mesmo.

0 ≤ c1 * n ≤ 3n + 3 ≤ c2 * n (p/ todo e qualquer valor de n maior ou igual a zero).

**Passo 2:** Estabelecer um valor p/ n respeitando o que foi dito acima. Dessa forma, diremos que n = 1.

**Passo 3:** Resolver f(n) com o valor de n estabelecido.

0 ≤ c1 * n ≤ 3n + n ≤ c2 * n  $→$ 0 ≤ c1 * 1 ≤ 3 * 1 + 3  ≤ c2 * 1

$→$ 0 ≤ c1 ≤ 6 ≤ c2. 

**Passo 4:** Definir valores para c1 e c2. c1 deve ser maior que zero e menor ou igual a 6 e c2 deve ser maior ou igual a 6 no exemplo acima.

Se c1 = 1 e c2 = 6, ou, sei lá, c1 = 2 e c2 = 7, o valor de f(n) continua sendo maior que c1 e menor que c2.

Assim: 0 ≤ 2 ≤ 6 ≤ 7. Sendo 2 o limite inferior e 7 e o limite superior da função.

**Notação O (Big O notation)**

Define um limite superior para uma função f(n). Segundo o material do prof João Arthur:

> Para duas funções $f(n)$ e $g(n)$, dizemos que $f(n)$ é $O(g(n))$ se: $0≤f(n)≤c∗g(n),∀n≥n0$
> 

Acho que você percebeu que essa inequação é bem parecida com a da notação Theta, certo? A diferença entre elas é que o limite inferior da Big O é zero, além de trabalharmos apenas com um c (limite superior) a ser definido.

Os passos para definir o limite superior da Big O são os mesmos da notação Theta. Assim, dizemos que o limite superior da função f(n) = n² + 1 é 2.

Toda função Theta é uma Big O, mas nem toda Big O é uma Theta, visto que Thetas possuem limite inferior e Big Os não.

<aside>
💡 “[...] basta escolhermos uma função com **n** elevado a um expoente maior do que o da função sob análise que conseguimos definir um limite superior para ele. Por exemplo, a função f(n)=n² é O(n²), O(n³), O(n4) […]”  Um exemplo é a função f(n) = 7n. Seu limite superior pode ser n, n², n³, etc…

</aside>

> “Em termos simplistas, f(n)∈O(g(n)) significa dizer que o crescimento de f(n) é menor ou igual ao crescimento de g(n).”
> 

**Notação Omega (Ω)**

Define o limite inferior para uma função f(n). Assim:

> Para duas funções $f(n)$ e $g(n)$, dizemos que $f(n)$ é $Ω(g(n))$ se: $0≤c∗g(n)≤f(n),∀n≥n0$
> 

O processo para achar seu limite inferior é o mesmo da notação Theta. 

Toda função Theta é Omega, mas nem toda Omega é Theta, pois a Omega não possui limite superior.

<aside>
💡 Todo limite inferior de Omega pode ser 1, basta usar o expoente 0. Além disso, dado um expoente, para limitá-lo inferiormente basta escolher um expoente menor. Por exemplo, f(n³) é Ω(n²).

</aside>

> Em termos simplistas, f(n)∈Ω(g(n)) significa dizer que o crescimento de f(n) é maior ou igual ao crescimento de g(n).
>