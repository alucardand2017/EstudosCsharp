___

<div style="display: inline_block"><br>
<img align="left" height="40" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg"> 
</div>

# Estudos CSharp

___


### Sum�rio

1. [Classe](#1) 
2. [Metodo](#2)
3. [Func�es](#3)
4. [Escopo](#4)
5. [NameSpace](#5)
6. [Modificadores](#6)
7. [Heran�a](#7)
8. [Encapsulamento](#8)
9. [Construtor](#9)
10. [Membros Est�ticos](#10)
11. [Polimorfismo](#11)
12. [Sobrecarga](#12)
13. [Getters e Setters](#13)
14. [Sobrecarga de Construtores](#14)
15. [Abstra��o](#15)
16. [Heran�a Derivada](#16)
17. [Interface](#17)
18. [Try e Catch](#18)
19. [Erros de Exce��o Geral](#19)
20. [throw](#20)
21. [ParaName e nameof()](#21)
22. [Propriedade Somente Leitura](#22)


<div  id ='1'/>

 * **Classe**  - Utilizamos normalmente para desenvolver um ou mais m�todos e atribui��es que visam dividir o c�digo de foma a deixa-lo otimizado para sua utiliza��o, respeitando os conceitos e conven��es de forma a deixar-lo inteleg�vel.
~~~JavaScript
class Program 
{
    static void Main(string[] args)
    {....}
}
~~~

<div  id ='2'/>

 * **M�todo** - Aplica��o realizada para execu��o de uma tafera, normalmente atribu�ndo valores a vari�veis e utilizando processamento computacional para isso (contas).
 
<div  id ='3'/>

 * **Fun��es** - Bloco de c�digo criado para realizar determinadas tarefas necess�rias a uma implementa��o.
 fazem parte da logica de uma classe ou escopo maior.
  
<div  id ='4'/>

 * **Escopo** - Bloco l�gico definido entre chaves que pode conter uma ou v�rias l�gicas/classes/m�todos/campos e fun��es.

<div  id ='5'/>

 * **NameSpace** - Bloco onde que contem uma solu��o (conjunto de codigos que formam um programa), funcionando como uma classe maior dentro do C# e que torna especifico todas as classes que a cont�m

<div  id ='6'/>

 * **Modificadores** - palavras reservadas no C# que especificam o que o qu�o acess�vel para mudan�a est� aquele campo.
   * **_private_** - torna o campo privado, acessado apelas pelo escopo pertencente.
   * **_protected_** - torna o campo protegido, acessado apelas pelo escopo pertencente e suas classes filhas.
   * **_public_** - torna o campo p�blico, acessado de qualquer classe dentro do NameSpace da solu��o. 

<div  id ='7'/>

 * **Heran�a** - Conceito aplicado a classes que podem acessar par�metros e estruturas de outras classes, numa rela��o de classe base e classe filha. Os atributos da classe base podem ser acessados pela classe filha.

~~~JavaScript
//repare nessa linha onde temos a rela��o filha : base
public class Diretor : Funcionario  
{
   Console.WriteLine("A var�avel {0} tem valor", x);
}
~~~

```JavaScript
public class Funcionario // classe base
{
    protected int x = 10;
}
```

<div  id ='8'/>

 * **Encapsulamento** - Conceito aplicado a vari�veis e campos que necessitam de um regramento espec�fico para seu acesso, dando ou n�o permiss�o para escritas e leituras de campos/vari�veis.

<div  id ='9'/>

 * **Construtor** - Metodo que especifica como sua classe deve "ser", especificando quais entradas e sa�das s�o obrigat�rias
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

 * **Membros Est�ticos** - Uma propriedade da Classe a que abriga, sendo acessado apenas por ela.
~~~JavaScript
//exemplo de membro estatico com getter/setter
public static int TotalDeFuncionarios { get ; private set}  
~~~

<div  id ='11'/>

 * **Polimorfismo** - Utilizado para escrever m�todos/fun��es de uma classe que contem aquela mesma fun��o, mas com atribui��es dentro do escopo diferentes
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
 

* **Sobrecarga** - � a forma que nos permite ter m�todos chamados da mesma referencia (nome) entre as diferentes classes, onde cada m�todo pode ter escopo diferente.
O exemplo acima � um tipo de sobrecarga de m�todo.

<div  id ='13'/>

 * **Getters e Setters** - Express�o que representa uma l�gica de acesso a vari�veis e campos que tem restri��o de acesso por parte do c�digo. Sua forma de representa��o por der um `public double Salario {get; set;}`, que representa ao c�digo o seguinte m�todo:
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

 * **Sobrecarga de Construtores** - Utiliza o mesmo princ�pio da Sobrecarga, mas aplicado a Construtores de Classes.  

Sendo os campo CPF e Sal�rio Getters e Setters, podemos ter:

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
Repare que a `Class Diretor` � filha da `Class Funcion�rio` e isso deve ser evidenciado para o C# com os `: Nome_Classe_base`.
Pomdemos ainda ter uma situa��o em que devemos usar palavras reservadas para acessar de forma correta esses construtores:

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

 * **Abstra��o** - Ainda com respeito a m�todos de construtores, temos um recurso de abstra��o onde os membros 
  dessa classe n�o s�o objetos do programa, mas balizadores de como esses objetos devem ser instanciados. Assim sendo, um m�todo de construtor abstrato n�o pode ser instanciado, servindo como
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

 * **Heran�a Derivada** - Quando uma classe filha herda os parametros de outra classe filha, que por sua vez herda da classe pai. 
A Classe filha intermedi�ria pode nesse processo possuir propriedades exclusivas para aqueles membros daquela classe, e ainda sim
herdar as outras caracteristicas da classe base. Nesse exemplo podemos dizer que ela funciona como um filtro, onde podemos
selecionar quem herda quais caracteristicas segundo as necessidades do neg�cio.
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
de `Funcionario`. As classes que herdaram de `Autenticavel` tem outros par�metros, como `Senha`.

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

 * **Interface** - como n�o temos heran�a multipla no C#, quando uma classe tenta herdar diretamente de outras 2 classes
temos o recurso de `interface`, ela parece uma classe abstrata e tem apenas metodos abstratos (apesar de n�o precisar escrever `abstract`).
Ela � como um contrato, que diz que tal m�todo apontado por ela ser� usado por quem chama a interface, mas que ser� implementado
por esta classe, j� que ela n�o pode faze-lo. A conven��o diz que ela deve ser escrita por `I+Nome`

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

* **try e catch** - Utilizado para tratamento de erros de diversas origens. Ele testa o c�digo/m�todo
dentro do seu escopo e retorna uma mensagem de erro caso seja detectada a falha, sendo que est� foi espeficicada
dentro do codigo (n�o trata falhas n�o especificadas). Vale dizer que num mesmo bloco podemos ter mais de um bloco
`catch` para tratamento de erros.

```JavaScript 
try
{
    Metodo();
}
//trata a divis�o por zero no m�todo Metodo()
catch (DivideByZeroException excecao)
{
Console.WriteLine(excecao.Message);
Console.WriteLine(excecao.StackTrace);
}
```

<div  id ='19'/>

* **Erros de Exce��o Geral** - podemos tratar os erros com o bloco Try/Catch referenciando um erro espec�fico
como `NullReferenceException` e `DividedByZero`. Contudo, h� uma forma mais generalista de trata-los, onde 
podemos espeficicar apenas os erros que quisermos, e deixar os demais para um tratamento geral, segundo o c�digo:


```JavaScript 
try
{
    Metodo();
}
//trata a divis�o por zero dentro de Exception
catch (DivideByZeroException e)
{
    Console.WriteLine(e.Message);
    Console.WriteLine(e.StackTrace);
    Console.WriteLine("Erro de referencia vazia!");
}
//trata as demais exce�oes 
catch (Exception e)
{
    Console.WriteLine(e.Message);
    Console.WriteLine(e.StackTrace);
    Console.WriteLine("Aconteceu um outro erro!");
}
```
por conven��o, chamamos as variaveis que tratam erro de `e`.

<div  id ='20'/>

* **throw** - passa a frente uma exce��o sem encerrar o c�digo, saindo dele e passando para
o pr�ximo m�todo abaixo no CallStack (pilha de chamada).

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
que ajudar� na depura��o de um poss�vel erro. Vejamos a seguinte situa��o: 
O erro foi pego pelo `throw new ArgumenttException ("mensagem", ParaName);` num metodo acima da CallStack. 
Ele retorna lan�a o erro pra pilha abaixo, que por sua vez tem um `try/catch`. Ent�o, esse erro pode ser
melhor depurado, analisando o `ParaName` da `ArgumentException` e sua `Message`

```js
//metodo acima da pilha
if(agencia < 0)
{
    throw new ArgumentException("agencia n�o pode ser 0", nameof(agencia));
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

* **Propriedade somente leitura** - Quando temos campos que n�o queremos mudar os n�meros em praticamente nenhum lugar do c�digo
usamos o modificador `private readonly int Nome` na vari�vel. Assim temos a constru��o:

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
Contudo, o C# tem o mesmo recurso do getter e setter, onde podemos omitir toda essa constru��o
por um 
```js 
public int Numero {get;}
```
 sem prejuizo de c�digo, pois � a mesma coisa por
"debaixo dos panos".
