___

<div style="display: inline_block"><br>
<img align="left" height="40" width="40" src="https://raw.githubusercontent.com/devicons/devicon/master/icons/csharp/csharp-original.svg"> 
</div>

# Estudos CSharp

___


### Sumario

1. [Classe](#1) 
2. [Metodo](#2)
3. [Funcoes](#3)
4. [Escopo e Object](#4)
5. [NameSpace](#5)
6. [Modificadores](#6)
7. [Herança](#7)
8. [Encapsulamento](#8)
9. [Construtor](#9)
10. [Membros Estaticos](#10)
11. [Polimorfismo](#11)
12. [Sobrecarga](#12)
13. [Getters e Setters](#13)
14. [Sobrecarga de Construtores](#14)
15. [Abstraçao](#15)
16. [Herança Derivada](#16)
17. [Interface](#17)
18. [Try e Catch](#18)
19. [Erros de Exceçao Geral](#19)
20. [throw](#20)
21. [ParaName e nameof()](#21)
22. [Propriedade Somente Leitura](#22)
23. [criando exceçoes](#23)
24. [StackTrace](#24)
25. [InnerException](#25)
26. [OIException](#26)
27. [finally](#27)
28. [using](#28)
29. [FileSystem](#29)

<div  id ='1'/>

 * **Classe**  - Utilizamos normalmente para desenvolver um ou mais metodos e atribui��es que visam dividir o codigo de foma a deixa-lo otimizado para sua utilizaçao, respeitando os conceitos e convençoes de forma a deixar-lo intelegivel.
~~~c#
class Program 
{
    static void Main(string[] args)
    {....}
}
~~~

<div  id ='2'/>

 * **Metodo** - Aplicaçao realizada para execuçao de uma tafera, normalmente atribu�ndo valores a variaveis e utilizando processamento computacional para isso (contas).
 
<div  id ='3'/>

 * **Funcoes** - Bloco de codigo criado para realizar determinadas tarefas necessarias a uma implementaçao.
 fazem parte da logica de uma classe ou escopo maior.
  
<div  id ='4'/>

 * **Escopo** - Bloco logico definido entre chaves que pode conter uma ou varias logicas/classes/metodos/campos e funçoes.
 *  **Class Object** - A classe object é uma classe genérica que todas as classes já herdam por default. Em resumo, Object é a super classe de toda a classe, e automaticamente qualquer instancia possue seus métodos (`ToString()`, `GetHashCode()`, `etc`)
 *   

<div  id ='5'/>

 * **NameSpace** - Bloco onde que contem uma soluçao (conjunto de codigos que formam um programa), funcionando como uma classe maior dentro do C# e que torna especifico todas as classes que a contam

<div  id ='6'/>

 * **Modificadores** - palavras reservadas no C# que especificam o que o quao acessivel para mudança esta aquele campo.
   * **_private_** - torna o campo privado, acessado apelas pelo escopo pertencente.
   * **_protected_** - torna o campo protegido, acessado apelas pelo escopo pertencente e suas classes filhas.
   * **_public_** - torna o campo publico, acessado de qualquer classe dentro do NameSpace da solucao. 

<div  id ='7'/>

 * **Herança** - Conceito aplicado a classes que podem acessar par�metros e estruturas de outras classes, numa rela��o de classe base e classe filha. Os atributos da classe base podem ser acessados pela classe filha.

~~~c#
//repare nessa linha onde temos a rela��o filha : base
public class Diretor : Funcionario  
{
   Console.WriteLine("A var�avel {0} tem valor", x);
}
~~~

```c#
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

~~~c#
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

~~~c#
public class Auxiliar : Funcionario
{
    Auxiliar carlos = new Auxiliar( 1000 , 337 189 888 82);
}
~~~

<div  id ='10'/>

 * **Membros Est�ticos** - Uma propriedade da Classe a que abriga, sendo acessado apenas por ela.
~~~c#
//exemplo de membro estatico com getter/setter
public static int TotalDeFuncionarios { get ; private set}  
~~~

<div  id ='11'/>

 * **Polimorfismo** - Utilizado para escrever m�todos/fun��es de uma classe que contem aquela mesma fun��o, mas com atribui��es dentro do escopo diferentes
~~~c#
//Construtor abstrato que indica que temos esse metodo
public abstract class Funcionario 
{
    ...
    public abstract double GetBonificacao();
}
~~~

~~~c#
public class Diretor : Funcionario
{
    public override double GetBonificacao() 
    {
       return Salario*0.5; 
    }
}
~~~

~~~c#
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
~~~c#
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

~~~c#
public class Diretor : Funcionario 
{
    public Diretor( double salario, string cpf) : base(salario , cpf) 
    {
        Console.WriteLine("CRIANDO DIRETOR");
    }
}
~~~


```c#
public Funcionario(double salario , string cpf)
{
    CPF = cpf;
    TotalDeFuncionarios++;
    Salario = salario;
}
```
Repare que a `Class Diretor` � filha da `Class Funcion�rio` e isso deve ser evidenciado para o C# com os `: Nome_Classe_base`.
Pomdemos ainda ter uma situa��o em que devemos usar palavras reservadas para acessar de forma correta esses construtores:

```c#
public class Diretor: Funcionario
{
    public override GetBonificacao()
    {   
        return Salario + base.GetBonificacao();
    }
}
```
~~~c#
public class Funcionario
{
    public virtual GetBonificacao()
    {   
        return Salario*0.1 ;
    }
}
~~~

<div  id ='15'/>

 * **Abstracaoo** - Ainda com respeito a metodos de construtores, temos um recurso da abstracao, onde os membros dessa classe nao sao objetos do programa, mas balizadores de como esses objetos devem ser instanciados. Assim sendo, um metodo de construtor abstrato nao pode ser instanciado. É similar um processo de assinatura. onde há o comprometimento da classe que herda uma abstração, de implementar seus métodos dentro do seu próprio escopo.

~~~c#
public abstract class Funcionario 
{
    public Funcionario(double salario , string cpf)
    {
        public abstract double GetBonificacao();
    }
}
~~~

```c#
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

 * **Herança Derivada** - Quando uma classe filha herda os parametros de outra classe filha, que por sua vez herda da classe pai. A Classe filha intermediaria pode nesse processo possuir propriedades exclusivas para aqueles membros daquela classe, e ainda sim
herdar as outras caracteristicas da classe base. Nesse exemplo podemos dizer que ela funciona como um filtro, onde podemos selecionar quem herda quais caracteristicas segundo as necessidades do negocio.
    * `Membros separados ---> Classe Exclusiva ---> Classe geral`
    * `Membros comuns ---> ---> ---> ---> ---> ---> Classe geral`


Um exemplo de classe exclusiva, fazemos os membros herdarem a partir dessa classe:
```c#
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
~~~c#
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
de `Funcionario`. As classes que herdaram de `Autenticavel` tem outros parametros, como `Senha`.

~~~c#
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

 * **Interface** - como nao temos herança multipla no C#, quando uma classe tenta herdar diretamente de outras 2 classes temos o recurso de `interface`, ela parece uma classe abstrata e tem apenas metodos abstratos (apesar de nao precisar escrever `abstract`).
Ela e como um contrato, que diz que tal metodo apontado por ela sera usado por quem chama a interface, mas que sera implementado por esta classe, ja que ela nao pode faze-lo. A convençao diz que ela deve ser escrita por `I+Nome`

```c#
//arquivo IAutenticavel.cs
public interface IAutenticavel
{ 
    bool Autenticar(string senha);              
}
```

```c#
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

```c#
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

* **try e catch** - Utilizado para tratamento de erros de diversas origens. Ele testa o codigo/metodo dentro do seu escopo e retorna uma mensagem de erro caso seja detectada a falha, sendo que esta foi espeficicada dentro do codigo (nao trata falhas nao especificadas). Vale dizer que num mesmo bloco podemos ter mais de um bloco `catch` para tratamento de erros.

```c# 
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

* **Erros de Excecao Geral** - podemos tratar os erros com o bloco Try/Catch referenciando um erro especifico como `NullReferenceException` e `DividedByZero`. Contudo, ha uma forma mais generalista de trata-los, onde podemos espeficicar apenas os erros que quisermos, e deixar os demais para um tratamento geral, segundo o codigo:

```c# 
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
por convencao, chamamos as variaveis que tratam erro de `e`.

<div  id ='20'/>

* **throw** - passa a frente uma excecao sem encerrar o codigo, saindo dele e passando para
o proximo metodo abaixo no CallStack (pilha de chamada).

```csharp
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
que ajudara na depuracao de um possivel erro. Vejamos a seguinte situacao: O erro foi pego pelo `throw new ArgumenttException ("mensagem", ParaName);` num metodo acima da CallStack. 
Ele retorna lanca o erro pra pilha abaixo, que por sua vez tem um `try/catch`. Entao, esse erro pode ser melhor depurado, analisando o `ParaName` da `ArgumentException` e sua `Message`

```c#
//metodo acima da pilha
if(agencia < 0)
{
    throw new ArgumentException("agencia n�o pode ser 0", nameof(agencia));
}
```

```c#
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

* **Propriedade somente leitura** - Quando temos campos que nao queremos mudar os numeros em praticamente nenhum lugar do codigo usamos o modificador `private readonly int Nome` na variavel. Assim temos a construcao:

```c#
private readonly int _numero;
public int Numero
{
    get
    {
        return _numero;_
    }
}
```
Contudo, o C# tem o mesmo recurso do getter e setter, onde podemos omitir toda essa construcao
por um 
```c# 
public int Numero {get;}
```
 sem prejuizo de codigo, pois e a mesma coisa por "debaixo dos panos".

<div  id ='23'/>

**Criando Excecoes** - a Classe do tipo `Exception`, como toda classe em C#, aceita que facamos alteracoes, incrementando algo que o .NET noo preve, como nossa regra de negocios. Vamos entender como isso e realizado. Primeiramente temos que criar uma classe com o erro que queremos tratar, bem como colocar os construtores que ela deve conter para nos auxiliar:

```c#
//arquivo SaldoInsuficienteException
public double Saldo{get;};
public double ValorSaque {get;}
class SaldoInsuficienteException : Exception {
    public SaldoInsuficienteException()
    { }
    public SaldoInsuficienteException ( string message) : base(message)
    { }
    public SaldoInsuficienteException ( double valor , double valorsaque) : 
    this ("Valor insuficiente para saque! faltam = " + (valorsaque - saldo))
    {
        Saldo = saldo;
        ValorSaque = valorsaque;
    }
}
```

Agora que temos nosso construtor, vamos chamado na base do erro, ou seja, no metodo a ser testado.

```c#
if(_saldo_ < valor)
{
//podemos chamar qualquer uma das sobrecargas desse metodo, optei por esta.  
    throw SaldoInsuficienteException(_saldo, valor);
}
```
O `throw` reporta a pilha inferior...

```c#
try
{
...Operacao testada...
}
catch (SaldoInsuficienteException ex)
{
    Console.WriteLine(ex.Message)
    Console.WriteLine("Exce��o do tipo Saldo InsuficienteException");
}
```

Em resumo: o Bloco do meio testa o `valor` que e superior ao saldo, e reporta o erro e seu argumento para para a pilha inferior, o bloco try/catch pega
o erro e trata mostrando no console o `ex.Message` ("Valor insuficiente para saque! faltam! XXX ), e o Console escreve "Excecao do tipo Saldo InsuficienteException").

caminho `--> Main -> try -> Sacar(valor) -> throw SaldoInsuficienteException( saldo, saque) -> reporta ao SaldoInsuficienteException (messagem) a mensagem 
--> repassa ao Exception a mensagem --> retorna a pilha abaixo e e pego pelo catch --> mostra a mensagem e encerra a operacao ` .


<div  id ='24'/>


24. **StackTrace obs** - Algo interessante de se salientar � que o StackTrace mostra o caminho que ocorreu a excecao, a partir do `throw` que o lancou, entretando, caso ele tenha um novo throw new preenchido pelo caminho, ele reescreve em cima do StackTrace anterior. Para evitarmos isso lancamos o `throw` sem nenhum argumento de excecoo a frente.

<div  id ='25'/>

26. **InnerException** - Essa excecao e interna de uma outra excecao, e pode ser usada, por exemplo, para omitir informacoes sensiveis a um grupo espefaco.
Vamos construir um construtor para nossa nova Excecao a ser utilizada.
```c#
class OperacaoFinanceiraException : Exception
{
    public OperacaoFinanceiraException()
    { }
    public OperacaoFinanceiraException(string mensagem) : base(mensagem)
    { }
    public OperacaoFinanceiraException(string mensagem, Exception excecaoInterna) : base(mensagem, excecaoInterna)
    { }
}
```
E agora o bloco que reportaria uma exce��o do .Net ir� reportar uma exce��o interna, criada por n�s.
```c#
 public void Transferir(float valor, ContaCorrente destino)
{
  try
  {
      Sacar(valor);
  }
  catch (SaldoInsuficienteException ex)
  {
      throw new OperacaoFinanceiraException("Opera��o Inv�lida!", ex );
  }
}
```
Repare que agora temos um argumento que � nossa InnerException, que preserva o StackTrace da exce��o original.
Caso queiramos saber ele, � s� ver sua propriedade `Message` no c�digo.

```c#
try
   {
        conta.Saldo = 100;
        conta2.Saldo = 1000;
        conta.Transferir(1000, conta2);
    }
catch (OperacaoFinanceiraException e )
    {                
         Console.WriteLine(e.StackTrace);
         Console.WriteLine(e.Message);
         Console.WriteLine("Exce��o do tipo Opera��o FinanceiraException!");
         Console.WriteLine("\n\n\n INFORMA��ES DA INNER EXCEPTION = ");
         Console.WriteLine(e.InnerException.Message);
         Console.WriteLine(e.InnerException.StackTrace);
    }
```

<div  id ='26'/>


26. **IOException** - � a classe de exce��o do .Net que trata de erros proveninentes de entrada e sa�da de dados da aplica��o.
� utitilizado da mesma forma que os anteriores at� aqui citados. Contudo, h� alguns casos que ela deve prever, como o de uma
parada repentina do sistema, pois os arquivos que foram lidos precisariam ser fechados antes do final da aplica��o, para disponibilizar
o recursos novamente. Para isso temos um outro recursos, o `finally`. Que ser� discutido abaixo.

<div  id ='27'/>

27. **Finally** - � uma diretira do bloco try/catch que sempre � executado caso tenha sido implementado. Ent�o, em resumo, caso tenha sido ou n�o
pego pelo try/catch ele ser� executado ao final. 

```c#
try
{}
catch
{}
finally
{}
```
ent�o, nele poderemos fechar, a priori, os recursos que poderiam ter sido interrompidos por algum problema de leitura durante o acesso externo.
Contudo, apesar dessa possibilidade, n�o � assim que tratamos tipos de erro como `FileNotFoundException()` (arquivo n�o encontrado). Para tal,
podemos usar um recurso que funciona como o bloco try/catch/finally que verifica se o arquivo � nulo que substitui a l�gica `try/catch/finally`...


<div  id ='28'/>

28. **using** - Essa classe utiliza a mesma logica, sem as implementa��es necess�rias para se pegar um erro do tipo arquivo nulo por exemplo,
est� tudo implicito em seu uso. Veja o exemplo:

```c#
RecursoDoSistema recurso = null;
try
{
    recurso = new RecursoDoSistema();
    recurso.Usar();
}
finally
{
    if(recurso != null)
    {
        recurso.Dispose();
    }
}
```
Tudo isso acima podemos trocar pela sintaxe `using`. Contudo, ao usar ela, o objeto que  instanciamos com ela deve conter uma `interface` espec�fica para libera��o de 
recursos do sistema, a `IDispose`. Essa interface tem apenas 1 m�todo, o `Dispose`, que far� nossa fun��o de `Leitor.Fechar()`. 
Veja o exemplo.

```c#
//cogido no Program.cs // verifica se os arquivos existem e aponta implicitamente o m�todo Dispose
//obrigatorio no construtor que o recebe, no caso o LeitorDeArquivos)
using (LeitorDeArquivos leitor = new LeitorDeArquivos("teste.txt")) 
  {
      leitor.LerProximaLinha();
  }
```

```c#
//arquivo LeitorDeArquivos.cs
// o construtor deve assinar o contrato com o Idisposable do .Net para liberar os recursos
class LeitorDeArquivos : IDisposable 
{
   public string Arquivo { get; }
   public LeitorDeArquivos(string arquivo)
   {
       Arquivo = arquivo;
       Console.WriteLine("Abrindo Arquivo");
       //throw new FileNotFoundException();
   }
   public string LerProximaLinha()
   {
       Console.WriteLine("lendo proxima linha...");
       //throw new IOException();
       return "linha do arquivo";
   }
   public void Dispose() // � chamado para fechar os recursos de leitura de arquivos, obritatorio
   {
       Console.WriteLine("Fechando os arquivos");
   }
}
```
No caso acima pordemos testar as seguintes situa��es: 
 * Falta de arquivo (null) //n�o chama o Dispose pq n�o precisa.
 * Erro na leitura do arquivo por alguma interrup��o //chama o Dispose e fecha a aplica��o de leitura.
 * Sem erros //chama o Dispose para fechar o arquivo

Em todas as situa��es acima, o using utiliza ou n�o o Dispose de maneira correta.

<div  id ='29'/>

29. **FileSystem** - O sistema de arquivos normalmente não armazena todo o dado num unico arquivo, ja que nao é prático e consumiria muita memória. A estratégia agora é falar sobre fluxo de dados, que picota o arquivo em partes, e vai entregando ao navegador, programa, etc.
Vamos colocar o arquivo contas.txt dentro de `/bin/Debug/net5.0/`, que é a pasta raiz do nosso projeto.

```c#
    var enderecoDoArquivo = "contas.txt";
    var numeroDeBytesLidos = -1;
    var fluxoDoArquivo = new FileStream(enderecoDoArquivo, FileMode.Open);
    var buffer = new by[1024]; //caso não seja preenchido retorna após a leitura o número 0 {20, 45, 50, 251,0,0,0,0,0,0 ...}
    While(fluxoDeBytesLidos !=0){
        numeroDeBytesLidos = fluxoDoArquivo.Read(buffer, 0, 1024);
    }
    //public override int Read(byte[] array, int offset, int count) ... traduzindo
    //public override int Read(bytes lidos, do inicio da leitura , qnts posições quer ler)
    fluxoDoArquivo.Read(buffer, 0, 1024);
```
O File.Open é um enum que tem como opções (`CreateNew, Create, Open, OpenOrCreate, Truncate, Append`).

Para visualizar o que estamos fazendo, vamos analisar o armezamento pelo laço ...

```c#
Metodo(buffer){
    var utf8 = new UTF8Encoding();
    var texto = utf8.GetString(buffer);
    Console.Write(texto);
    //Foreach(var meuByte in buffer){
    //    Console.Write(meuByte)
    //}
}
```
Da forma como está podemos ler o arquivo, inclusive os espaços e tabulações, que tem seu código na table Unicode. Para liberar os recursos do arquivo, inserimos o `fluxoDoArquivo.Close();`

A tratativa das possíveis exceções que podem ocorrer em uma abertura de arquivo são grandes. Para fugir desse tipo de tratamento, vamos utilizar o `using`

```c#
   using(var fluxoDoArquivo = new FileStream(enderecoDoArquivo, FileMode.Open)){
    //código
   }
```


