# JIT Compiler: compilação em tempo de execução

> A arquitetura Java é baseada na interpretação de Bytecodes pela JVM.<br>
> Mas esta Máquina Virtual é muito mais complexa do que um mero interpretador.<br>

> Texto retirado do livro: "Arquitetura e Design de Software, dos irmãos Silveira"

---
Quando o Java foi lançado, a JVM era ordens de magnitude mais lenta que hoje.
Hoje, o Java é bastante rápido, mas ainda carrega este estigma originado no passado.
As primeiras JVMs eram simplesmente interpretadores de bytecodes. Liam arquivos .class
e traduziam cada bytecode na sequência de execução para as instruções
de máquina equivalentes.

> Nota: ou seja, inicialmente, Java tinha uma compilação completo, seguida de uma interpretação.

A partir do Java 1.1, a Sun incluiu seu primeiro JIT Compiler, adquirido da Symantec, e,
no Java 1.2, incluiu o HotSpot. A evolução dessas duas tecnologias ao longo das versões do Java
é o que faz a JVM ser equiparável a aplicações nativas em C e C++.

Os grandes ganhos de performance do Java devem-se à otimização adaptativa,
isto é, a capacidade de fazer otimizações de acordo com o uso do programa e as
condições do momento. 

Tanto Java quanto C possuem uma etapa de compilação
estática, que gera um arquivo binário a ser executado, e, durante essa compilação,
várias otimizações são realizadas. A diferença é que o binário nativo C gerado é executado
diretamente na máquina, e o binário Java é ainda executado através da JVM,
onde outras otimizações acontecem. No caso do C, toda otimização possível é feita
estaticamente pelo compilador, enquanto que o Java consegue executar uma segunda
etapa de otimizações dentro da VM no momento da compilação dos bytecodes para
código nativo, na chamada compilação dinâmica. É isto o que faz o Java executar tão
rapidamente.

> Nota: Java compila o código-fonte para bytecodes. Enquanto C, para código nativo.

Durante a execução do programa, a JVM a analisa e detecta os pontos mais importantes
e executados da aplicação. Esses métodos são então compilados dinamicamente
pelo JIT para código nativo otimizado, e toda execução subsequente é feita
com ele, atingindo performance comparável a C.

As VMs mais modernas conseguem até recompilar determinado método com otimização
mais agressiva caso percebam que a performance melhorará.
Elas também percebem que determinado código já não é mais importante, e descartam suas compilações,
ou que determinada heurística aplicada não foi boa, e aplicam um novo tipo de otimização.

> Para evitar uma compilação completa, seguida de interpretação, surge o JIT Compiler.<br>
> Este compilador Just-in-time encontra os pontos mais executados do código (hotspot) e os compila para código nativo.

A evolução constante da JVM e do JIT faz com que o Java seja cada vez mais
rápido. Mesmo um programa antigo melhora significativamente sua performance
se o usuário simplesmente atualizar a versão da JVM. 

Em um programa nativo tradicional, para o usuário ter um ganho de performance,
por exemplo, por causa de uma versão nova do compilador C, ele terá que esperar do fabricante uma versão
nova recompilada. Mais do que isso, muitos programas comerciais em C exigem
um mínimo de portabilidade, como, por exemplo, rodar desde o Windows XP até
o Windows 7, ou suportar qualquer processador Intel e AMD.

Para tanto, frequentemente a compilação do programa C é feita usando recursos comuns a todas as
plataformas visadas. Ou seja, um denominador comum em relação a otimizações,
instruções de máquina e chamadas do sistema. Já o Java, por não fazer a compilação
para código nativo apenas estaticamente, consegue usar estratégias focadas no sistema operacional
e no hardware usados no momento de sua execução, chegando a
invocar instruções específicas do processador em uso.

---
# Otimizações para clientes e servidores

Diferentes aplicações têm diferentes necessidades de performance e responsividade.
Pensando nisso, a JVM oferece perfis diferentes que adaptam o funcionamento
do JIT e outras características da JVM.

> Um JIT mais agressivo, que compila muitos métodos para código nativo, aumenta o tempo de inicialização, mas melhora a perfomance.

Aplicações voltadas ao usuário final, geralmente clientes Desktop, têm uma
grande demanda por inicialização rápida, embora não precisem tanto de performance;
em geral, o gargalo nessas aplicações é o input do usuário. Se habilitarmos
a opção -client na JVM, ela perde menos tempo no startup para o usuário ver o
resultado mais rapidamente, mas ao custo de ter um JIT fazendo otimizações 
menos agressivas a longo prazo. Um dos focos desta configuração é, por exemplo, não
consumir muita memória, até deixando de fazer certas otimizações no JIT que 
acabariam aumentando o uso de memória, como inline de métodos.

Já a opção -server prevê cenários nos quais o tempo inicial não é um grande
problema, mas existe uma preocupação maior com a performance a longo prazo.
O startup demora mais algum tempo, e o JIT roda em uma de suas versões mais
agressivas para o desempenho da aplicação.

O uso de memória é mais intenso, mas a performance de execução é maior a longo prazo.
A VM server abusa, por exemplo, de recursos como inline de métodos, em que o código compilado pelo JIT
já junta na memória o código dos métodos envolvidos para evitar jumps ao máximo.
Nas versões mais recentes da HotSpot, caso não passemos a opção explicitamente,
a própria máquina virtual escolhe entre client e server, tamanho do heap,
algoritmo de GC e outros pontos com base no tipo de hardware no qual o software
está sendo executado – este recurso é chamado de VM ergonomics. Há ainda
opções experimentais, como a -XX:+AgressiveOpts que habilita mais otimizações.

Dado este monitoramento que a JVM faz para decidir o momento certo de otimizar
seu código pelo JIT, fica a pergunta: o que é melhor, escrever pequenos métodos
reaproveitáveis entre si com muitas invocações, ou métodos gigantes que são
invocados umas poucas vezes? Quebrar nosso código em pequenos métodos, que
concentram uma única responsabilidade, é a melhor prática. E, por questões de performance,
para o JIT, quanto mais reaproveitáveis forem seus métodos, mais invocações serão feitas e mais focadas serão as otimizações.

### Programe baseado em boas práticas, e deixe o JIT cuidar da execução otimizada.
