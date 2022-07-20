## Redes Blockchain
- [[Bitcoin]]
- [[Polkadot]]
- [[Ethereum]]
- [[Bep20]]
- [[Bep2]]
- [[Tron Network]]
- [[Avalanche]]
- [[Solana]]
- [[Fantom]]

---
### Layer 1
- Uma blockchain de camada 1 ( *chain/root layer* ) é  o nome usado para descrever um protocolo de rede blockchain principal, como Ethereum ou Bitcoin.
- Blockchains de camada 1 são simplesmente a rede principal à qual uma solução de dimensionamento de camada 2 se conecta para melhorar a escalabilidade e a taxa de transferência de transações da cadeia principal, ou camada 1.
- O nome Camada 1 vem de seu relacionamento com soluções de dimensionamento de camada 2 como *state channels*, *rollups* e *plasma side chains*.
```ad-info
- Layer 1: a blockchain padrão de função principal.
- Layer 2: um conjunto de funcionalidades sobre uma blockchain de layer 1.
```

### Layer 2
- A layer 2 refere-se a um protocolo secundário que é construído em cima de uma blockchain existente.
- As principais redes de criptomoedas, como a Ethereum, enfrentam dificuldades de velocidade de transação e dimensionamento. Bitcoin e Ethereum ainda não são capazes de processar milhares de transações por segundo. Além disso, essas soluções de layer 2 geralmente oferecem taxas de transação muito melhores.
- Os protocolos da layer 2 são projetados especificamente para se integrar ao blockchain subjacente para melhorar o rendimento da transação.
- Eles contam com o mecanismo de consenso e a segurança da cadeia principal.
- As operações na layer 2 geralmente podem ser executadas independentemente da layer 1. É por isso que às vezes são chamadas de soluções "off-chain". A layer 1 pode fornecer a segurança inerente a uma blockchain, a layer 2 pode fornecer a velocidade.
- Como as transações na layer 2 estão acontecendo em uma chain diferente, uma conexão é aberta periodicamente para mover essas transações para o blockchain principal. Essa conexão às vezes é chamada de *bridge* ou *channel*. Portanto, uma consideração importante para uma solução de layer 2 é como as transações são validadas e confirmadas antes de serem movidas para a chain principal.

#### Dimenssões da rede
- Execução da transações
	- As estratégias de execução de transações lidam com como as transações são executadas, onde são executadas, quais são os ambientes de confiança, quais são os ambientes de segurança e descentralização, etc.
- Disponibilidade de dados
	- As estratégias de disponibilidade de dados lidam com se a solução da Camada 2 disponibiliza ou não seus dados de transação na cadeia principal da Camada 1.

#### Layer 2 Scaling Solutions
- State Channels
- Side Chains
- Rollups
	- Optimistic Rollups (ORs)
	- Zero-Knowledge Rollups (ZKRs)
	- ZKR vs OR
	- Plasma
- Validiums
- Volitions

**State Channels**


---
### Transações
```ad-warning
💡 Rede de origem tem que ser a mesma do destino
```

Resposta 
1. O que é uma blockchain de camada 1 ? A
R: A principal rede blockchain à qual as camadas 2 se conectam.

2. Por que as camadas 2 são referidas às vezes como "off-chain"? B
R: As operações na layer 2 geralmente podem ser realizadas independentemente da layer 1.

3. O que são blockchains de camada 2 ? A
R: Projetado para ajudar a layer 1 com taxa de transferência e taxas de transação.

4. Quais são as dimensões nas quais as soluções de dimensionamento da Camada 2 têm abordagens diferentes?
R: Transaction Execution and Data Availability