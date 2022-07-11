- A Programação Orientada a Objetos (OOP) é um paradigma no qual objetos do mundo real são vistos como entidades separadas que têm seu próprio estado, que é modificado apenas por procedimentos incorporados, chamados métodos.
- Como os objetos operam de forma independente, eles são encapsulados em módulos que contêm ambientes e métodos locais. A comunicação com um objeto é feita por mensagem. Os objetos são organizados em classes, das quais herdam métodos e variáveis equivalentes. O paradigma orientado a objetos fornece benefícios fundamentais da extensibilidade de código e código reutilizável.

---

Características e Benefícios:

- Uma nova classe (chamada de classe derivada ou subclasse) pode ser derivada de outra classe (chamada de classe base ou superclasse) por um mecanismo chamado **herança**. A classe derivada **herda** todas as características da classe base: sua estrutura e comportamento (resposta às mensagens). Além disso, a classe derivada pode conter estado adicional (variáveis de instância) e pode apresentar comportamento adicional (novos métodos para responder para novas mensagens). Significativamente, a classe derivada também pode **substituir o comportamento** correspondente a alguns dos métodos da classe base: haveria um método diferente para r**esponder à mesma mensagem**. Além disso, o mecanismo de herança é permitido mesmo sem acesso ao código fonte da classe base.
- A capacidade de usar a herança é a característica mais distintiva do paradigma OOP. A herança dá ao OOP seu principal benefício sobre outros paradigmas de programação - reaproveitamento e extensão de código relativamente fáceis sem a necessidade de alterar o código-fonte existente.
- O mecanismo de modelagem de um programa como uma coleção de objetos de várias classes, e além disso descrevendo muitas classes como extensões ou modificações de outras classes, proporciona um alto grau de modularidade.
- Idealmente, o estado de um objeto é manipulado e acessado apenas pelos métodos desse objeto. (A maioria das línguas OO permitem manipulação direta do Estado, mas esse acesso é estilisticamente desencorajado). Desta forma, a interface de uma classe (como objetos dessa classe são acessados) é separada da implementação da classe (o código real dos métodos da classe). Assim, o encapsulamento e a ocultação de informações são benefícios inerentes ao OOP.

---

## Pilares do OOP

- Abstraction
- Encapsulation
- Inheritance
- Polymorphism

### Abstraction

- Classes *abstract* só servem como superclasse geradora, ela não pode estanciar um objeto.

```java
public abstract class main(){
 private int x;
 public abstract void returnX();
}
```


- Métodos abstratos não possuem lógica, são métodos vazios:

```java
public abstract void teste();
```

---

### Inheritance

> Search to herança versus composição

- Mesmo depois de reescrever um método da classe mãe, a classe filha ainda pode acessar o método antigo. Isto é feito através da palavra chave super.metodo(). Algo parecido ocorre entre os construtores das classes.

- Herança permite basear uma nova classe na definição de uma outra classe previamente existente.
- A classe filha herda os métodos da classe mãe.
- A herança será aplicada tanto para as características quanto para os comportamentos.

- *As subclasses possuem todos os próprios atributos e métodos e possuem todos os atributos e métodos da superclasse*

**Abstrato e final (!important)**

- Classe abstrata: ela não pode ser instanciada. Só pode servir como superclasse, ou seja, não pode gerar objetos.
- Método abstrato: é um método declarado, mas não implementado na superclasse. O método abstrato só pode ser colocado dentro de uma classe abstrata ou de uma interface.
- Classe final: não pode ser herdada por outra classe. Ou seja, é obrigatpriamente uma classe folha. É uma classe ESTÉRIL.
- Método final: não pode ser sobrescrito pelas suas subclasses. Obrigatoriamente tem que ser herdado. O método final não pode ser sobreposto.

**Tipos**

Especialização:
- Percorre da raíz para as folhas, isto é, da super-classe para as sub-classes

Generalização:
- Percorre a árvore de herança das sub-classes para a super-classe

**@Override**
- Após estender uma classe, se eu quiser usar os mesmos setters e guetters e o mesmo método preciso usar o @Override para sobrescrever aqueles métodos

---

### Encapsulation

- O encapsulamento é deixar um atributo como privado para as classes;
- Para acessar o atríbuto precisamos criar métodos e criar a lógica de validação ali dentro;
- O objetivo do encapsulamento é proteger você dos atríbutos e os atríbutos de você;
- Serve para padronizar objetos também;
- Encapsular é ocultar partes independentes da implementação, permitindo construir partes invisíveis ao mundo exterior.
- A interface é responsável por fazer a comunicação do encapsulamento;
- Feito isso, o acesso aos dados do atributo é feito por meio da chamada do método;
- Encapsulamento esconde a maneira como os objetos guardam seus dados. É uma prática muito importante.

```java
class Conta {
  String titular;
  int numero;
  String agencia;
  // double saldo;
  private double saldo; // Marcando um atributo como privado, fechamos o acesso ao mesmo em relação a todas as outras classes,
  DataConta dataAbertura;

  boolean sacarValor(double valorASerSacado) {
    if (valorASerSacado > this.saldo) {
      return false;
    } else {
      this.saldo -= valorASerSacado;
      return true;
    }
  }

  /* Para permitir o acesso aos atributos (já que eles são private ) de uma
  maneira controlada, a prática mais comum é criar dois métodos, um que retorna
  o valor e outro que muda o valor. */
  public double getSaldo() {
    return this.saldo;
  }
  
  public double depositaValor(double valorASerDepositado) {
    return this.saldo += valorASerDepositado;
  }

  boolean retiraValor(double valorASerRetirado) {
    if (valorASerRetirado > this.saldo) {
      return false;
    } else {
      this.saldo -= valorASerRetirado;
      return true;
    }
  }

  boolean calculaRendimento() {
    return true;
  }

  String systemOutPrint() {
    String dados = "Titular: " + this.titular;
    dados += "\nNúmero: " + this.numero;
    dados += "\nSaldo: R$ " + this.saldo;
    dados += "\nAgência: " + this.agencia;
    dados += "\nData Abertua: " + this.dataAbertura.dataFormatada();
    return dados;
  }
}

class Cliente {
  String nome;
  String sobrenome;
  String cpf;
}

class DataConta {
  int dia;
  int mes;
  int ano;

  public String dataFormatada() {
    String dia = Integer.toString(this.dia);
    String mes = Integer.toString(this.mes);
    String ano = Integer.toString(this.ano);
    String data = dia + "/" + mes + "/" + ano;
    return data;
  }
}

class GuettersSetters {
  public static void main(String[] args) {

    Conta minhaConta = new Conta(); 

    DataConta data = new DataConta();
    minhaConta.dataAbertura = data;

    minhaConta.titular = "Carlos";
    minhaConta.numero = 123;
    minhaConta.agencia = "45656-8";
    minhaConta.depositaValor(500);
    data.dia = 23;
    data.mes = 04;
    data.ano = 2016;

    minhaConta.sacarValor(200); 
    
    System.out.println(minhaConta.getSaldo());

    boolean consegui = minhaConta.sacarValor(500);
    if (consegui) {
      System.out.println("Consegui sacar");
    } else {
      System.out.println("Não consegui sacar");
    }

    double novoSaldo = -200;
    if (novoSaldo < 0) {
      System.out.println("Não é possível realizar essa operação");
    } else {
      minhaConta.depositaValor(novoSaldo);
    }
    System.out.println(minhaConta.systemOutPrint());
    System.out.println("Rendimento atual: R$ " + minhaConta.calculaRendimento());
  }
} 
```

**Public**

- A classe atual e todas as outras classes podem ver

**Private**

- Somente a classe atual pode ver

**Protected**

- A classe atual e suas sub-classes filhas podem ver.
- Outras classes podem acessar atributos e métodos protected se, e somente se, a classe for instânciada ou se a classe for uma sub-classe da classes que está acessando seus métodos e atributos.

**Boas práticas**

- Devemos deixar sempre os atríbutos como private ou protected
- Assim devemos acessá-los a partir dos métodos public ou protected

---

### Polymorphism

- Polimorfismo é a capacidade de um objeto poder ser referenciado de várias formas. (cuidado, polimorfismo não quer dizer que o objeto fica se transformando, muito pelo contrário, um objeto nasce de um tipo e morre daquele tipo, o que pode mudar é a maneira como nos referimos a ele).

- O poder do polimorfismo, juntamente com a reescrita de método: diminuir o acoplamento entre as classes, para evitar que novos códigos resultem em modificações em inúmeros lugares.

- O uso de herança aumenta o acoplamento entre as classes, isto é, o quanto uma classe depende de outra. A relação entre classe mãe e filha é muito forte e isso acaba fazendo com que o programador das classes filhas tenha que conhecer a implementação da classe mãe e vice-versa fica difícil fazer uma mudança pontual no sistema. Esse é um problema da herança, e não do polimorfismo, que resolveremos mais tarde com a ajuda de Interfaces.

---

```java  
public class EmpregadoDaFaculdade {
 private String nome;
 private double salario;
    public double getGastos() {
    return this.salario;
    }
    public String getInfo() { 
    return "nome: " + this.nome + " com salário " + this.salario;
    }
}

public class ProfessorDaFaculdade extends EmpregadoDaFaculdade {
    private int horasDeAula;
    public double getGastos() {
        return this.getSalario() + this.horasDeAula * 10;
    } public String getInfo() {
        String informacaoBasica = super.getInfo();
        String informacao = informacaoBasica + " horas de aula: " + this.horasDeAula;
        return informacao;
    }
} 
// o super invoca o método da classe mãe
```

```java
public class GeradorDeRelatorio {
 public void adiciona(EmpregadoDaFaculdade f) {
     System.out.println(f.getInfo());
        System.out.println(f.getGastos());
        }
}
// Ou seja, podemos usar essa classe para informar as informações e gastos do professor e funcionário
```

- Um certo dia, muito depois de terminar essa classe de relatório, resolvemos aumentar nosso sistema, e colocar uma classe nova, que representa o Reitor . Como ele também é um EmpregadoDaFaculdade , será que vamos precisar alterar algo na nossa classe de Relatorio ? Não. Essa é a ideia! Quem programou a classe GeradorDeRelatorio nunca imaginou que existiria uma classe Reitor e, mesmo assim, o sistema funciona.


```java
public class Reitor extends EmpregadoDaFaculdade { 
    // informações extras
    public String getInfo() {
        return super.getInfo() + " e ele é um reitor";
    }
    // não sobrescrevemos o getGastos!!!
}
```

#### Polimorismo
- Bem, o polimorfismo é o mecanismo pelo qual podemos "relaxar o sistema de tipos", para que também - aceitemos objetos das classes filha ou derivadas.

- Polimorfismo permite que o mesmo nome represente vários comportamentos diferentes.

- Todo método tem uma assinatura, consiste em:
> Quantidade e tipos de parâmetros


```java
public float test(int x, float y) {
 return x / y;
}

// ===
 
public int test(int x, float z) {
 return x * z;
}

// !=

public int test(int x, float y, String z){
 return x / z; 
}
```

---

- Digamos que temos uma classe pai e algumas classes filho que herdam dela. Às vezes, queremos usar uma coleção - por exemplo, uma lista - que contém uma mistura de todas essas classes. Ou temos um método implementado para a classe pai - mas gostaríamos de usá-lo também para as crianças.

- Simplificando, o polimorfismo oferece uma maneira de usar uma classe exatamente como seu pai, para que não haja confusão com os tipos de mistura. Mas cada classe filho mantém seus próprios métodos como eles são.

- Isso normalmente acontece definindo uma interface (pai) a ser reutilizada. Ele descreve vários métodos comuns. Em seguida, cada classe filho implementa sua própria versão desses métodos.

- Sempre que uma coleção (como uma lista) ou um método espera uma instância do pai (onde métodos comuns são descritos), o idioma cuida de avaliar a implementação correta do método comum - independentemente de qual filho é passado.


---

#### Tipos de polimorfismo
**Sobreposição**:
- A sobreposição de @Overide é uma forma de sobrepor um método abstrato ou não de uma super-classe ou sub-classe. Para isso, o método deve ter a mesma assinatura, isto é, deve ser igual ao do qual herdou e conter os mesmos tipos e quantidades de parametros.

- A sub-classe que extends uma super-classe obrigatoriamente precisa de sobreposição em todos os seus métodos do qual herdou. No entanto, sub-classes que herdam de uma sub-classe que herdou de uma super-classe, não precisam obrigatoriamente de uma sobreposição de métodos.

- A mesma assinatura em classes diferentes.

**Sobrecarga**:
- É uma forma de reagir a alguma coisa.

- Assinaturas diferentes em uma mesma classe, isto é, mesmo nome do método mas com atríbutos diferentes