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

