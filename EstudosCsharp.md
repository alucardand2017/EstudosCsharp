___

<div style="display: inline_block"><br>
<img align="left" height="40" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg"> 
</div>

# Estudos CSharp

___


### Sumário

1. [Classe](#1) 
2. [Metodo](#2)
3. [Funcões](#3)
4. [Escopo](#4)
5. [NameSpace](#5)
6. [Modificadores](#6)
7. [Herança](#7)
8. [Encapsulamento](#8)
9. [Construtor](#9)
10. [Membros Estáticos](#10)
11. [Polimorfismo](#11)
12. [Sobrecarga](#12)
13. [Getters e Setters](#13)
14. [Sobrecarga de Construtores](#14)
15. [Abstração](#15)
16. [Herança Derivada](#16)
17. [Interface](#17)
18. [Try e Catch](#18)
19. [Erros de Exceção Geral](#19)
20. [throw](#20)
21. [ParaName e nameof()](#21)
22. [Propriedade Somente Leitura](#22)


<div  id ='1'/>

 * **Classe**  - Utilizamos normalmente para desenvolver um ou mais métodos e atribuições que visam dividir o código de foma a deixa-lo otimizado para sua utilização, respeitando os conceitos e convenções de forma a deixar-lo intelegível.
~~~JavaScript
class Program 
{
    static void Main(string[] args)
    {....}
}
~~~

<div  id ='2'/>

 * **Método** - Aplicação realizada para execução de uma tafera, normalmente atribuíndo valores a variáveis e utilizando processamento computacional para isso (contas).
 
<div  id ='3'/>

 * **Funções** - Bloco de código criado para realizar determinadas tarefas necessárias a uma implementação.
 fazem parte da logica de uma classe ou escopo maior.
  
<div  id ='4'/>

 * **Escopo** - Bloco lógico definido entre chaves que pode conter uma ou várias lógicas/classes/métodos/campos e funções.

<div  id ='5'/>

 * **NameSpace** - Bloco onde que contem uma solução (conjunto de codigos que formam um programa), funcionando como uma classe maior dentro do C# e que torna especifico todas as classes que a contém

<div  id ='6'/>

 * **Modificadores** - palavras reservadas no C# que especificam o que o quão acessível para mudança está aquele campo.
   * **_private_** - torna o campo privado, acessado apelas pelo escopo pertencente.
   * **_protected_** - torna o campo protegido, acessado apelas pelo escopo pertencente e suas classes filhas.
   * **_public_** - torna o campo público, acessado de qualquer classe dentro do NameSpace da solução. 

<div  id ='7'/>

 * **Herança** - Conceito aplicado a classes que podem acessar parâmetros e estruturas de outras classes, numa relação de classe base e classe filha. Os atributos da classe base podem ser acessados pela classe filha.

~~~JavaScript
//repare nessa linha onde temos a relação filha : base
public class Diretor : Funcionario  
{
   Console.WriteLine("A varíavel {0} tem valor", x);
}
~~~

```JavaScript
public class Funcionario // classe base
{
    protected int x = 10;
}
```

<div  id ='8'/>

 * **Encapsulamento** - Conceito aplicado a variáveis e campos que necessitam de um regramento específico para seu acesso, dando ou não permissão para escritas e leituras de campos/variáveis.

<div  id ='9'/>

 * **Construtor** - Metodo que especifica como sua classe deve "ser", especificando quais entradas e saídas são obrigatórias
no nomento do seu instanciamento.

~~~JavaScript
//arquivo Funcionario.cs
public class Funcionario // classe base
{
    // construtor deve ter o mesmo nome
    public Funcionario (double salario, string cpf)  
    {
        Salario = salario;
        CPF = cpf;
    }
}
~~~

~~~JavaScript
public class Auxiliar : Funcionario
{
    Auxiliar carlos = new Auxiliar( 1000 , 337 189 888 82);
}
~~~

<div  id ='10'/>

 * **Membros Estáticos** - Uma propriedade da Classe a que abriga, sendo acessado apenas por ela.
~~~JavaScript
//exemplo de membro estatico com getter/setter
public static int TotalDeFuncionarios { get ; private set}  
~~~

<div  id ='11'/>

 * **Polimorfismo** - Utilizado para escrever métodos/funções de uma classe que contem aquela mesma função, mas com atribuições dentro do escopo diferentes
~~~JavaScript
//Construtor abstrato que indica que temos esse metodo
public abstract class Funcionario 
{
    ...
    public abstract double GetBonificacao();
}
~~~

~~~JavaScript
public class Diretor : Funcionario
{
    public override double GetBonificacao() 
    {
       return Salario*0.5; 
    }
}
~~~

~~~JavaScript
//arquivo GerenteDeConta.cs
public class GerenteDeConta : Funcionario 
{
    public override double GetBonificacao() 
    {
        return (Salario*0.25); .
    }
}
~~~

<div  id ='12'/>
 

* **Sobrecarga** - É a forma que nos permite ter métodos chamados da mesma referencia (nome) entre as diferentes classes, onde cada método pode ter escopo diferente.
O exemplo acima é um tipo de sobrecarga de método.

<div  id ='13'/>

 * **Getters e Setters** - Expressão que representa uma lógica de acesso a variáveis e campos que tem restrição de acesso por parte do código. Sua forma de representação por der um `public double Salario {get; set;}`, que representa ao código o seguinte método:
~~~JavaScript
public double Salario
{
    get
    {
        return Salario;
    }
    set
    {
        Salario = value;
    }
}   
~~~
 

<div  id ='14'/>

 * **Sobrecarga de Construtores** - Utiliza o mesmo princípio da Sobrecarga, mas aplicado a Construtores de Classes.  

Sendo os campo CPF e Salário Getters e Setters, podemos ter:

~~~JavaScript
public class Diretor : Funcionario 
{
    public Diretor( double salario, string cpf) : base(salario , cpf) 
    {
        Console.WriteLine("CRIANDO DIRETOR");
    }
}
~~~


```JavaScript
public Funcionario(double salario , string cpf)
{
    CPF = cpf;
    TotalDeFuncionarios++;
    Salario = salario;
}
```
Repare que a `Class Diretor` é filha da `Class Funcionário` e isso deve ser evidenciado para o C# com os `: Nome_Classe_base`.
Pomdemos ainda ter uma situação em que devemos usar palavras reservadas para acessar de forma correta esses construtores:

```JavaScript
public class Diretor: Funcionario
{
    public override GetBonificacao()
    {   
        return Salario + base.GetBonificacao();
    }
}
```
~~~JavaScript
public class Funcionario
{
    public virtual GetBonificacao()
    {   
        return Salario*0.1 ;
    }
}
~~~

<div  id ='15'/>

 * **Abstração** - Ainda com respeito a métodos de construtores, temos um recurso de abstração onde os membros 
  dessa classe não são objetos do programa, mas balizadores de como esses objetos devem ser instanciados. Assim sendo, um método de construtor abstrato não pode ser instanciado, servindo como
uma forma para bolos.

~~~JavaScript
public abstract class Funcionario 
{
    public Funcionario(double salario , string cpf)
    {
        public abstract double GetBonificacao();
    }
}
~~~

```JavaScript
public class Diretor : Funcionario
{
    public Diretor( double salario, string cpf) : base(salario , cpf) 
    {
        Console.WriteLine("CRIANDO DIRETOR");
    }
    public override double GetBonificacao() 
    {
        return Salario*0.5; 
    }
}
```

<div  id ='16'/>

 * **Herança Derivada** - Quando uma classe filha herda os parametros de outra classe filha, que por sua vez herda da classe pai. 
A Classe filha intermediária pode nesse processo possuir propriedades exclusivas para aqueles membros daquela classe, e ainda sim
herdar as outras caracteristicas da classe base. Nesse exemplo podemos dizer que ela funciona como um filtro, onde podemos
selecionar quem herda quais caracteristicas segundo as necessidades do negócio.
    * `Membros separados ---> Classe Exclusiva ---> Classe geral`
    * `Membros comuns ---> ---> ---> ---> ---> ---> Classe geral`


Um exemplo de classe exclusiva, fazemos os membros herdarem a partir dessa classe:
```JavaScript
public abstract class Autenticavel : Funcionario
{
    public string Senha { get; set; }
    public Autenticavel(double salario, string cpf) : base(salario, cpf)
    {
    }
    public bool Autenticar(string senha)
    {
        return Senha == senha;
    }
}
```

A classe base tem a seguinte cara:
~~~JavaScript
public abstract class Funcionario 
{
   public string Nome { get; set; }
   public string CPF { get; set; }
   public double Salario { get; protected set; }
   public static  int TotalDeFuncionarios {get; private set;}  //1    
   public Funcionario(double salario , string cpf)
   {
       CPF = cpf;
       TotalDeFuncionarios++;
       Salario = salario;
   }
}
~~~

Abaixo vemos a classe `Auxiliar` herdar apenas de `Funcionario`, enquanto as demais herdam de `Autenticavel` que por sua vez herda
de `Funcionario`. As classes que herdaram de `Autenticavel` tem outros parâmetros, como `Senha`.

~~~JavaScript
// Arquivo GererenteDeContas.cs
public class GererenteDeContas : Autenticavel
{...}
// Arquivo Diretor.cs
public class Diretor : Autenticavel
{...}
// Arquivo Auxiliar.cs
public class Auxiliar : Funcionario
{...}
~~~

<div  id ='17'/>

 * **Interface** - como não temos herança multipla no C#, quando uma classe tenta herdar diretamente de outras 2 classes
temos o recurso de `interface`, ela parece uma classe abstrata e tem apenas metodos abstratos (apesar de não precisar escrever `abstract`).
Ela é como um contrato, que diz que tal método apontado por ela será usado por quem chama a interface, mas que será implementado
por esta classe, já que ela não pode faze-lo. A convenção diz que ela deve ser escrita por `I+Nome`

```JavaScript
//arquivo IAutenticavel.cs
public interface IAutenticavel
{ 
    bool Autenticar(string senha);              
}
```
```JavaScript
//arquivo Diretor.cs
public class Diretor : Funcionario, IAutenticavel 
{
   ...
   public string Senha { get; set; }
   public bool Autenticar(string senha)
   {
       return Senha == senha;
   }
}
```
```JavaScript
//arquivo GerenteDeConta.cs
public class GerenteDeConta : Funcionario, IAutenticavel
{
    ...
    public string Senha { get; set; }
    public bool Autenticar(string senha)
    {
        return Senha == senha;
    }
}
```
 
<div  id ='18'/>

* **try e catch** - Utilizado para tratamento de erros de diversas origens. Ele testa o código/método
dentro do seu escopo e retorna uma mensagem de erro caso seja detectada a falha, sendo que está foi espeficicada
dentro do codigo (não trata falhas não especificadas). Vale dizer que num mesmo bloco podemos ter mais de um bloco
`catch` para tratamento de erros.

```JavaScript 
try
{
    Metodo();
}
//trata a divisão por zero no método Metodo()
catch (DivideByZeroException excecao)
{
Console.WriteLine(excecao.Message);
Console.WriteLine(excecao.StackTrace);
}
```

<div  id ='19'/>

* **Erros de Exceção Geral** - podemos tratar os erros com o bloco Try/Catch referenciando um erro específico
como `NullReferenceException` e `DividedByZero`. Contudo, há uma forma mais generalista de trata-los, onde 
podemos espeficicar apenas os erros que quisermos, e deixar os demais para um tratamento geral, segundo o código:


```JavaScript 
try
{
    Metodo();
}
//trata a divisão por zero dentro de Exception
catch (DivideByZeroException e)
{
    Console.WriteLine(e.Message);
    Console.WriteLine(e.StackTrace);
    Console.WriteLine("Erro de referencia vazia!");
}
//trata as demais exceçoes 
catch (Exception e)
{
    Console.WriteLine(e.Message);
    Console.WriteLine(e.StackTrace);
    Console.WriteLine("Aconteceu um outro erro!");
}
```
por convenção, chamamos as variaveis que tratam erro de `e`.

<div  id ='20'/>

* **throw** - passa a frente uma exceção sem encerrar o código, saindo dele e passando para
o próximo método abaixo no CallStack (pilha de chamada).

```js
try
{         
    return numero / divisor;
}    
catch (DivideByZeroException)
{
    Console.WriteLine("Divisor com " + divisor como parametro);
    throw;
}
catch (Exception)
{
    Console.WriteLine("Erro de outro tipo");
    throw;
}
```
<div  id ='21'/>

* **ParaName e nameof(variavel)** - A classe `ArgumentExcepetion` pode retornar uma mensagem mais espeficica
que ajudará na depuração de um possível erro. Vejamos a seguinte situação: 
O erro foi pego pelo `throw new ArgumenttException ("mensagem", ParaName);` num metodo acima da CallStack. 
Ele retorna lança o erro pra pilha abaixo, que por sua vez tem um `try/catch`. Então, esse erro pode ser
melhor depurado, analisando o `ParaName` da `ArgumentException` e sua `Message`

```js
//metodo acima da pilha
if(agencia < 0)
{
    throw new ArgumentException("agencia não pode ser 0", nameof(agencia));
}
```

```js
//metodo abaixo na pilha
try
{
    ContaCorrente conta = new ContaCorrente(0 , 456754);
}
catch (ArgumentException e)
{
    Console.WriteLine(e.Message); //vai mostrar a mensagem da pilha acima
    Console.WriteLine(e.ParamName); // vai mostrar o nome do apontado no nameof
}
```

<div  id ='22'/>

* **Propriedade somente leitura** - Quando temos campos que não queremos mudar os números em praticamente nenhum lugar do código
usamos o modificador `private readonly int Nome` na variável. Assim temos a construção:

```js
private readonly int _numero;
public int Numero
{
    get
    {
        return _numero;_
    }
}
```
Contudo, o C# tem o mesmo recurso do getter e setter, onde podemos omitir toda essa construção
por um 
```js 
public int Numero {get;}
```
 sem prejuizo de código, pois é a mesma coisa por
"debaixo dos panos".
