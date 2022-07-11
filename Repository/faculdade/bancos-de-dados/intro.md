### Aula 1 - Introdução a banco de dados

- Bancos de dados permitem armazenar dados em forma de tabelas, onde cada linha representa um registro e cada coluna representa um campo. Os dados são armazenados em arquivos de texto, que podem ser lido e manipulados por uma linguagem de programação.
- Os bancos de dados permitem armazenar dados de tipos como strings, numéricos, timestamps, multimídia, monetários, binários, booleano, geométricos (Ponto, Segmentos de linha, Caixa, Caminho, Polígono, Círculos), endereço de rede, cadeias de bits, tipos compostos e outros.
- O enfoque tradicional de salvar dados em arquivos tem muitas desvantagens, dentre elas, duplicação de dados, redundância, erros de processamento, entre outras.
  
**Banco de Dados (BD)**

- Um banco de dados é uma coleção de dados relacionados, com algum significado inerente. Representa um aspecto do mundo real (possui as características das sua necessidade lógica e prática); Um banco de dados é projetado, construído e populado (preenchido) com dados para uma finalidade específica.
- Para que um banco de dados seja preciso e confiável, ele precisa ser um reflexo verdadeiro do minimundo que representa ou seja, reflexo da sua necessidade. As mudanças precisam ser refletidas o mais breve possível.
- Um banco de dados pode ter qualquer tamanho e complexidade.
- Exemplo de Banco de Dados: Universidade
  - Aluno;
  - Disciplina;
  - Turma;
  - Histórico Escolar;
  - Pré-requisito.

<img src="https://i.ibb.co/9NSmHL1/18-04-22-12-21-53.png" width="720px">

**Sistemas Gerenciados de Banco de Dados (SGBD)**

- É uma coleção de programas que permite aos usuários criar e manter um banco de dado. É um software que facilita o processo de definição, construção, manipulação e compartilhamento de dados entre diversos usuários e aplicações;
- Como definir um banco de dados para minha aplicação ? É necessário um  banco  de  dados que  envolve  especificar  os tipos, estruturas e restrições dos dados que serão armazenados;
- A definição descritiva do banco de dados é armazenada na forma de um catálogo ou dicionário, chamado metadados;
- O compartilhamento de um banco de dados permite que diversos usuários e programas acessem-no simultaneamente. Um programa de aplicação acessa o banco de dados ao enviar consultas ou solicitações ao SGBB;
- Proteção contra acessos indevidos;
- Manutenção;
- Vantagens em utilizar um SGBD
  - Controlar a redundância;
  - Restringir acesso;
  - Armazenamento persistente;
  - Estruturas de armazenamento e técnicas de pesquisa para o processamento de consultas;
  - Backup e recuperação;
  - Múltiplas interfaces do usuário;
  - Relacionamentos complexos entre os dados;
  - Restrições de integridade.

**Ciclo de vida do banco de dados**

- Compreende as seguintes etapas:
  - Análise dos requisitos;
  - Projeto lógico;
  - Projeto Físico.

Análise dos requisitos
- Os requisitos dos bancos de dados são determinados pela fase de levantamento de requisitos e análise de sistemas;
- É gerada uma especificação formal dos requisitos e esta inclui os dados exigidos para o processamento, os relacionamentos de dados e a plataforma de software para a implementação do banco de dados;
- Ex: Clientes, Faturamento, Produtos, Pedidos.

Projeto Lógico
- Diagrama de modelo de dados conceitual que mostra todos os dados e seus relacionamentos ER ou UML. As construções do modelo de dados precisam ser transformadas em tabelas;
- Modelagem conceitual de dados;
- Integração da visão;
- Transformação do modelo de dados conceitual;
- Normalização das tabelas.

<img src="https://i.ibb.co/hxNTcTw/18-04-22-13-59-31.png" width="720px">
<img src="https://i.ibb.co/LQ4zcCR/18-04-22-14-00-23.png" width="720px">

Projeto Físico
- Essa etapa envolve a seleção de índices (métodos de acesso), particionamento,clustering de dados e a implementação do banco de dados;
- O principal objetivo desta etapa é representar de maneira precisa a realidade e otimizar o desempenho da melhor forma possível;
- Nesta etapa, o banco de dados pode ser criado por meio da implementação do esquema formal, usando a linguagem SQL

Visão dos dados
- Um SGBD é uma coleção de arquivos e programas inter-relacionados que permitem ao usuário o acesso para consultas e alterações desses dados;
- O maior benefício de um banco de dados é proporcionar ao usuário uma visão abstrata dos dados
- Níveis de abstração do sistema
  - Nível Físico ou Interno;
    - É o nível mais baixo de abstração que descreve como esses dados estão de fato armazenados;
    - Estruturas de dados complexas de baixo nível são descritas em detalhes
  - Nível Lógico ou Conceitual;
    - Descreve quais dados estão armazenados no banco de dados e quais os inter-relacionamentos entre eles;
    - É utilizado pelos administradores de banco de dados (DBA) que precisam decidir quais informações devem pertencer ao banco de dados.
  - Nível de Visão ou Externo
    - Descreve apenas parte do banco de dado;

Exemplo dos três níveis de abstração (Arquitetura de três esquemas):

<img src="https://i.ibb.co/3C3hVLX/18-04-22-14-12-25.png" width="720px">

**Modelo de dados**

- Sob a estrutura do banco de dados está o modelo de dados. Um conjunto de ferramentas conceituais usadas para a descrição dos dados, relacionamentos entre dados, semântica de dados e regras de consistência;
- Os modelos são divididos em três grupos:
  - Modelos Lógicos com Base em Objetos;
    - São usados na descrição de dados no nível lógico (conceitual) e de visões (externo);
    - São divididos em
      - Modelo Entidade - Relacionamento;
      - Modelos Orientado à Objeto;
      - Modelos Semântico de dados;
      - Modelo Funcional de Dados.
  - Modelos Lógicos com Base em Registros;
    - São usados para especificar a estrutura lógica do banco de dados quanto para implementar uma descrição de alto nível;
    - São divididos em
      - Modelo Relacional;
      - Modelo de Rede;
      - Modelo Hierárquico;
  - Modelos Físicos de Dados.
    - São usados para descrever os dados no nível mais baixo;
    - Os dois mais conhecidos são
      - Modelo unificado (unifying model);
      - Modelo de partição de memória (frame-memory model)

**Linguagens de Banco de Dados**

- Um  sistema  de  banco  de  dados,  proporciona  dois tipos de linguagens:
  - Linguagens de Definição de Dados (DataDefinition Language - DDL)
    - Especifica por meio de uma linguagem especial, um esquema de dados;
    - O resultado da compilação dos parâmetros da DDL é armazenado em um conjunto de tabelas que constitui o dicionário de dados;
    - Utilizada pelos DBA’s e pelos projetistas de BD para definir e especificar os esquemas.
  - Linguagens de Manipulação de Dados (Data Manipulation Language - DML)
    - É a linguagem que viabiliza o acesso ou a manipulação dos dados de forma compatível ao modelo de dados;
    - Utilizada para recuperar, inserir, remover e modificar dados no banco de dados. Exemplos: INSERT, UPDATE,DELETE, COMMIT, ROLLBACK,SAVEPOINT e etc.

**Atores dos banco de dados**

- Administradores de banco de dados;
  - Supervisionar e gerenciar os recursos de banco de dados;
  - O DBA é responsável por autorizar acesso ao banco de dados, coordenar e monitorar seu uso e adquirir recursos de software e hardware conforme necessidade. Também é responsável por problemas como falhas na segurança e demora no tempo de resposta do sistema.
- Projetistas de banco de dados;
  - São responsáveis por identificar os dados a serem armazenados e escolher estruturas apropriadas para representar e armazenar esses dados;
  - Eles interagem com um grupo de usuários e desenvolvem visões do banco de dados que cumprem os requisitos de dados e processamento.
- Usuários finais;
  - São pessoas cujas funções exigem acesso ao banco de dados para consultas, atualizações e gerações de relatórios;
  - Usuários finais casuais – gerentes normalmente;
  - Usuários finais iniciantes – maioria dos usuários;
  - Usuários finais sofisticados – cientistas, analistas de negócios;
  - Usuários isolados – usuários que utilizam somente para determinadas aplicações.
- Analistas de sistemas e programadores.