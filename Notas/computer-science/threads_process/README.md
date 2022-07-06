## Threads and Process

- Tarefas podem ser implementadas de várias formas, como processos, threads, transações e jobs.
- O estado de uma tarefa em um determinado instante é denominado contexto.
- Troca de contexto: o ato de suspender uma tarefa e reativar outra é denominado uma troca de contexto.

### Processos

Quase todos os sistemas operacionais atuais suportam e existência de mais de uma tarefa em cada processo, como é o caso do Linux, Windows, iOS e os sistemas UNIX mais recentes.

Hoje em dia o processo deve ser visto como uma unidade de contexto, ou seja, um container de recursos utilizados por uma ou mais tarefas para sua execução: áreas de memória (código, dados, pilha), informações de contexto e descritores de recursos do núcleo (arquivos abertos, conexões de rede, etc). Um processo pode então conter várias tarefas, que compartilham esses recursos. Os processos são isolados entre si pelos mecanismos de proteção providos pelo hardware (isolamento de áreas de memória, níveis de operação e chamadas de sistema), impedindo que uma tarefa do processo P(a) acesse um recurso atribuído ao processo P(b).

Os sistemas operacionais atuais geralmente associam por default uma única tarefa a cada processo, o que corresponde à execução de um programa sequencial. Caso se deseje associar mais tarefas ao mesmo processo cabe ao desenvolvedor escrever o código necessário para solicitar ao núcleo a criação dessas tarefas adicionais, usualmente sob a forma de threads.

O núcleo do sistema operacional mantém descritores de processos, denominados PCBs (Process Control Blocks), para armazenar as informações referentes aos processos ativos. Um PCB contém informações como o identificador do processo (PID – Process IDentifier), seu usuário, prioridade, data de início, caminho do arquivo contendo o código executado pelo processo, áreas de memória em uso, arquivos abertos.

Associando-se tarefas a processos, o descritor (TCB) de cada tarefa pode ser bastante simplificado: para cada tarefa, basta armazenar seu identificador, os registradores do processador e uma referência ao processo onde a tarefa executa.

#### Gestão de processos

Durante a vida do sistema, processos são criados e destruídos, a criação de novos processos é feita em duas etapas. No primeiro `Fork()`, todo o espaço de memória do processo inicial (pai) é copiado para o novo processo (filho), incluindo o código da(s) tarefa(s) associada(s) e os descritores dos arquivos e demais recursos associados ao mesmo. A chamada de sistema `fork()` é invocada por um processo, mas dois processos recebem seu retorno: o processo pai, que a invocou, e o processo filho. Ambos os processos acessam os mesmos recursos do núcleo, embora executem em áreas de memória distintas.

Na segunda etapa, o processo filho usa a chamada de sistema `execve()` para carregar um novo código binário em sua memória. Essa chamada substitui o código do processo que a invoca pelo código executável contido em um arquivo informado como parâmetro.

A chamada de sistema `exit()` usada no exemplo acima serve para informar ao núcleo do sistema operacional que o processo em questão não é mais necessário e pode ser destruído, liberando todos os recursos a ele associados. Tarefas associadas ao mesmo processo podem trocar informações facilmente, pois compartilham as mesmas áreas de memória. Todavia, isso não é possível entre tarefas associadas a processos distintos. Para resolver esse problema, o núcleo deve prover às aplicações chamadas de sistema que permitam a comunicação interprocessos (IPC – Inter-Process Communication).


### Threads

Uma thread é definida como sendo um fluxo de execução independente. Um processo pode conter uma ou mais threads, cada uma executando seu próprio código e compartilhando recursos com as demais threads localizadas no mesmo processo. Cada thread é caracterizada por um código em execução e um pequeno contexto local, o chamado Thread Local Storage (TLS), composto pelos registradores do processador e uma área de pilha em memória, para que a thread possa armazenar variáveis locais e efetuar chamadas de funções. Threads são também utilizadas para implementar fluxos de execução dentro do núcleo do SO, neste caso recebendo o nome de threads de núcleo (em oposição às threads dos processos, denominadas user threads).

#### Modelos de Threads

As threads contidas nos processos, definidas no espaço de usuário, devem ser gerenciadas pelo núcleo do sistema operacional.

##### O modelo N:1

Os sistemas operacionais mais antigos suportavam apenas processos sequenciais, com um único fluxo de execução em cada um. No modelo de threads N:1, pois N threads dentro de um processo são mapeadas em uma única thread no núcleo. Esse modelo também é denominado fibers ou ainda green threads.

O modelo de threads N:1 é muito utilizado, por ser leve e de fácil implementação. Como o núcleo somente vê uma thread, a carga de gerência imposta ao núcleo é pequena e não depende do número de threads dentro da aplicação.

#### O modelo 1:1

A necessidade de suportar aplicações multithread levou os desenvolvedores de sistemas operacionais a incorporar a gerência dos threads dos processo no núcleo do sistema. Para cada thread de usuário foi então associado um thread correspondente dentro do núcleo, suprimindo com isso a necessidade de bibliotecas de threads. Este é o modelo mais frequente nos sistemas operacionais atuais.

O modelo 1:1 resolve vários problemas: caso uma thread de usuário solicite uma operação bloqueante, somente sua thread de núcleo correspondente será suspensa. Além disso, a distribuição de processamento entre as threads é mais justa e, caso o hardware tenha mais de um processador, mais threads do mesmo processo podem executar ao mesmo tempo, o que não era possível no modelo N:1.

O modelo de threads 1:1 é adequado para a maioria das situações usuais. No entanto, é pouco escalável: a criação de um número muito grande de threads impõe uma carga elevada ao núcleo do sistema, inviabilizando aplicações com muitas tarefas

#### O modelo N:M

O conjunto de threads de núcleo associadas a um processo, denominado thread pool, geralmente contém uma thread para cada thread de usuário bloqueada, mais uma thread para cada processador disponível; esse conjunto pode ser ajustado dinamicamente, conforme a necessidade da aplicação.

Ele alia as vantagens de maior interatividade do modelo 1:1 à maior escalabilidade do modelo N:1. Como desvantagens desta abordagem podem ser citadas sua complexidade de implementação e maior custo de gerência dos threads de núcleo, quando comparados ao modelo 1:1.

#### Thread safety

Thread safety é um conceito de programação de computadores aplicável no contexto de programas multi-thread. Um código é dito thread-safe se ele apenas manipula estruturas de dados compartilhadas de uma forma que garanta uma execução segura através de várias threads ao mesmo tempo. A segurança de thread é uma propriedade que permite que o código rode em ambientes multi-thread através do restabelecimento de algumas das correspondências entre o fluxo de controle real e o texto do programa, por meio de sincronização.