# Anotações - Arquitetura Limpa - Robert C. Martin

> "A arquitetura é o conjunto de decisões que você queria ter tomado logo no início de um projeto,
> mas, como todo mundo, não teve a imaginação necessária".
>> Ralph Johnson

---
## Introdução

> Como estruturar sistemas de software?

Uma arquitetura boa vem de compreendê-la mais como uma jornada do que como um destino,
mais como um processo contínuo de investigação do que como um artefato congelado.

> "A única maneira de ir rápido, é ir bem."
>> Robert C. Martin

Todo software é um conjunto de atribuções, laços de iteração e condicionais.
O que muda é como organizamos o código.

Fazer funcionar não é difícil. Fazer direito é outra questão.
Quando você faz um software bem feito, não será preciso hordas de programadores para manutenção.

Sistemas interconectados e muito acoplados custam caro.

Segundo Robert Martin, não há diferença entre Design e Arquitetura de Software.
Costumeiramente, o termo Arquitetura é utilizado para se referir a detalhes de mais alto nível, como a organização das diferentes camadas de software.
Enquanto o termo Design é utilizado para detalhes de mais baixo nível, como a escolha entre um laço de iteração for ou while.

Porém, para Robert, os detalhes de baixo nível servem de base para os de alto nível. Logo, ambos estão conectados.
Não há como pensar em Arquitetura, sem pensar em Design de Software.

Se o esforço necessário para manter um software for alto, então o design está ruim.

Para levar a sério a arquitetura do software, você precisa saber como é uma
boa arquitetura de software. Para construir um sistema com um design e
uma arquitetura que minimizem o esforço e maximizem a produtividade,
você precisa saber quais atributos da arquitetura do sistema podem
concretizar esses objetivos.

> Software: Soft (Suave) + Ware (Produto)<br>
> O software foi inventado para ser uma maneira fácil de mudar o comportamento das máquinas.

> Se você me der um programa que funcione perfeitamente, mas seja
impossível de mudar, então ele não funcionará quando as exigências
mudarem e eu não serei capaz de fazê-lo funcionar. Portanto, o
programa será inútil.

> Se você me der um programa que não funcione, mas seja fácil de
mudar, então eu posso fazê-lo funcionar, e posso mantê-lo
funcionando à medida que as exigências mudarem. Portanto, o
programa permanecerá continuamente útil.

---
## Paradigmas da Programação
> A arquitetura de software começa pelo código.<br>
> Paradigmas de programação são maneiras de se programar.<br>

Há três grandes paradigmas de programação: Paradigma estruturado, funcional e orientado a objetos.<br>
Observe o alinhamento desses três paradigmas com as três grandes preocupações arquiteturais:
- Funções;
- Separação de Componentes;
- Gerenciamento de Dados;

Mas antes, veja um pequeno texto sobre testes.

### Testes
Um programa pode ser provado como incorreto por um teste, mas um teste não pode provar que um programa está correto.
Tudo o que os testes fazem, depois de todos os esforços necessários, é permitir que consideremos um programa como suficientemente correto para os nossos propósitos.

A matemática é a ciência que prova que algo está correto.<br>
A ciência, por sua vez, não tem como provar que algo está correto, mas prova que algo está incorreto.

O desenvolvimento de software é como o desenvolvimento científico. Demonstramos a exatidão, quando falhamos em comprovar a inexatidão.

### Programação Estruturada
Com o uso de funções, laços de iteração e condicionais, a programação estrutura impôs disciplina sobre a transferência de controle.<br>
Estruturas de controle, combinadas com execuções sequenciais, poderiam substituir os comandos "goto". Todos os programas podem ser construídos a partir de três estruturas: sequência, seleção e iteração.<br>
A programação estruturada permite que os módulos de um sistema sejam decompostos em funções de alto nível. A partir dessas funções, podemos realizar testes para tentar provar que estas pequenas funções estão incorretas. Se os testes não conseguirem provar a incorreção das funções, então elas serão suficientemente corretas para o propósito.

### Programação Funcional
Imutabilidade. A programação funcional impõe disciplina sobre a atribuição.<br>
Primeiro paradigma desenvolvido, criado antes mesmo da programação e baseado no cálculo diferencial e integral.<br>
Uso de funções anônimas, ou seja, sem declaração.

### Programação Orientada a Objetos
Abstração de objetos do mundo real em classes, que geram instâncias programáveis.<br>
A base de uma boa arquitetura, é a compreensão e aplicação dos princípios do Design Orientado a Objetos.<br>
Linguagens orientadas a objetos possibilitam o encapsulamento fácil não só de funções, como também de dados.<br>
A grande sacada da programação orientada a objetos, é a construção de sistemas de baixo acoplamento, com o polimorfismo e inversão de dependências, isso é possível.<br>
Para o arquiteto de software, a OO é a habilidade de ter controle absoluto sobre cada dependência de código-fonte do sistema. Módulos de alto nível independentes dos módulos de baixo nível.

### Conclusão sobre os paradigmas
Decompor o programa em funções, facilita o desenvolvimento de testes, que podem comprovar a incorreção dessas funções, mas não a corretude das mesmas.

O software é como a ciência, orientado pela refutabilidade. Testes não provam corretude, mas sim a incorretude.

---
## Design de Sistemas
