# Formação - Java e Orientação a Objetos

## 01 - Histórico e Conceitos

A plataforma Java proporciona um ambiente completo para o desenvolvimento de programas, sendo composta por:

- Linguagem de Programação de alto nível e orientada a objetos
- Máquina Virtual (JVM - Java Virtual Machine), que garante independência de plataforma, pois o código executa na máquina virtual
- Java Runtime Environment (JRE), que agrega a máquina virtual e garante recursos para executar um programa
- Java Development Kit (JDK), conjunto de utilitários

Em Java, os programas são escritos em um arquivo com a extensão .java, que posteriormente será compilado para um arquivo .class. O .class contém os bytecodes, interpretados pela máquina virtual (JVM).

Exemplo em Java:

```java
// Arquivo: MyProgram.java
public class MyProgram {
    public static void main(String[] args) {
        // Código do programa aqui
    }
}
```

A JVM está disponível para a maioria dos sistemas operacionais, permitindo a execução do mesmo programa Java em diferentes plataformas.

"Escreva uma vez e execute em qualquer lugar."

JavaSE -> Standard Edition:
Componente padrão do Java que fornece um ambiente de desenvolvimento para aplicações de pequeno e médio porte e a JVM padrão.

JavaEE -> Enterprise Edition:
Componente baseado no JavaSE, focado no desenvolvimento de aplicações empresariais, provendo serviços adicionais.

Java é lento?

- `javac`: compilador que transforma o programa .java em .class
- Bytecodes interpretados pela JVM
- `jit`: compilador just in time, otimiza bytecodes em tempo de execução, melhorando o desempenho
- Os trechos de código mais executados são otimizados pelo `jit`
- `hotspot`: trecho de código frequentemente executado, traduzido para linguagem de máquina pelo compilador `jit`

Java é gratuito?

O Java é gratuito para estudos e testes. Para uso comercial, é necessário desembolsar um valor para licenciamentos.

---

## 02 - Características da Linguagem

- Independência de plataforma - Write once and run anywhere
- Orientação a objetos
- Não usa ponteiros - Não permite o acesso direto à memória e possui um coletor de lixo para limpar objetos não referenciáveis
- Multithread - Permite execução concorrente

---

## 03 - Sintaxe Básica e Programação Estruturada/Procedural/Imperativa

### Formatação de Texto

```java
String nome = "Maria";
int idade = 30;
double valor = 55.9999;
System.out.println(String.format("Meu nome é %s, eu tenho %d anos e hoje gastei %.2f reais", nome, idade, valor));
```

### Switch Case

```java
switch (expressao) {
    case valor1:
        // código a ser executado se a expressão for igual a valor1
        break;
    case valor2:
        // código a ser executado se a expressão for igual a valor2
        break;
    case valor3:
        // código a ser executado se a expressão for igual a valor3
        break;
    default:
        // código a ser executado se a expressão não for igual a nenhum valor
        break;
}
```

### Leitura de Dados

```java
import java.util.Scanner;

public class ExemploScanner {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Digite seu nome: ");
        String nome = scanner.nextLine();
        System.out.print("Digite sua idade: ");
        int idade = scanner.nextInt();
        System.out.print("Digite o valor que pretende investir esse mês: ");
        double valor = scanner.nextDouble();

        System.out.println(nome + " que tem " + idade + " anos, irá investir R$ " + valor + " esse mês.");

        scanner.close();
    }
}
```

---

## 04 - Orientação a Objetos

Com a programação estruturada, o reúso de código fica extremamente dificultado. Entretanto, ao encapsular trechos de código em classes e métodos, podemos reutilizar as regras do negócio em diferentes partes do código.

### Pilares da Orientação a Objetos

- Polimorfismo
- Herança
- Abstração
- Encapsulamento

### Classes e Objetos

Classes definem novos tipos (tipos referenciáveis). Uma classe encapsula trechos de código, e objetos são instâncias de uma classe, sendo uma abstração de entidades do mundo real.

Exemplo em Java:

```java
public class Gato {
    // Atributos e métodos da classe Gato aqui
}

// Instância da classe Gato
Gato garfield = new Gato();
```

Outro exemplo:

```java
public class Filme {
    // Atributos e métodos da classe Filme aqui
}

// Instância da classe Filme
Filme oppenheimer = new Filme();
```

### Métodos e Atributos

Métodos definem comportamentos, enquanto atributos definem características.

### Modificadores de Acesso

Atributos devem ser definidos como private.

- `public`: métodos públicos podem ser acessados por qualquer objeto
- `private`: métodos privados só podem ser acessados pelo próprio objeto
- `protected`: métodos protegidos só podem ser acessados pelo próprio objeto e por objetos que sejam subclasse deste objeto

Métodos abstratos (`abstract`) devem ser implementados pela subclasse.

### Métodos Acessadores

Getters e setters são usados para acessar e modificar dados, respectivamente.

```java
public class ExemploClasse {
    private int idade;

    public int getIdade() {
        return idade;
    }

    public void setIdade(int novaIdade) {
        idade = novaIdade;
    }
}
```

### Palavra Reservada `this`

Faz referência a um dado da própria classe.

```java
public class ExemploThis {
    private int valor;

    public void setValor(int valor) {
        this.valor = valor;
    }
}
```

### Herança e Polimorfismo

Herança é uma forma de reusar código, envolvendo superclasses e subclasses. Polimorfismo permite que objetos possam ser atribuídos a variáveis do tipo de qualquer uma de suas abstrações.

### Sobrecarga de Métodos

Métodos em Java (incluindo construtores) podem ter o mesmo nome, mas parâmetros diferentes.

### Interfaces

Definem o que uma abstração deve fazer, sem especificar como deve fazer.
