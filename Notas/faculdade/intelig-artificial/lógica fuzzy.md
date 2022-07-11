### Exercício

$(x, T(x), U, G, M)$

Onde:
-   X = nome da variável linguística. Exemplo: X = Idade;
-   T(x) = conjunto de termos de X, ou seja, o conjunto de nomes dos valores linguísticos de X, definido para cada valor em U. Exemplo: T(x) = {Jovem, Maduro, Idoso};
-   U = é o universo de discurso. Exemplo: U = (0:90);
-   G = regra sintática (geralmente um gramática) para gerar os valores de X como uma composição de termos de T(x);
-   Conectivos lógicos (negação, interseção e união), modificadores e delimitadores:
	-   Interpretação de Jovem como uma idade inferior a cerca de 20 anos;
	-   Maduro como a idade de 40 a 50;
	-   Idoso como uma idade superior a 70.
-   M = regra semântica pra associar a cada valor gerado por G (regra sintática), um conjunto fuzzy em U
	- Jovem = {1/10; 1/20; 0.5/30; 0.1/40; 0/50}
	- Maduro = {0/10; 0.1/20; 0.5/30; 1/40; 1/50; 0.5/60; 0.1/70; 0/80}
	- Idoso = {0/40; 0.1}


**
- 
- [x] Fuzificação
- [ ] Base de conhecimento
- [ ] Máquina de Inferência
- [ ] Defuzificação

---

**Etapas**
- [ ] Todas as possibilidades de entrada no sistema fuzzy tem que estar na máquina de inferencia.
- [ ] $A_i, \ B_i \ e \ C_i$ são conjuntos fuzzy, onde $A_i$ e $B_i$ são conjuntos de entrada de possibilidades das variáveis de $T(x)$ e $C_i$ é o conjunto de saída das regras fuzzy. Assim $R = A_i \ * \ B_i \ * \ C_i$. Essa operação é feita por um produto cartesiano.
- [ ] A utilização da base de regras para a obtenção da relação de inferência, pode resultar em mais de uma relação. Para ter uma **única saída**, é necessário fazer a **UNIÃO entre as relações dos conjunto M e G**.
- [ ] Calcular a matriz de possibilidades. Princípio da Completura, base de regras bater com a matriz de possibilidades, ou seja, na matriz dá SP/SP, então na base de regras deve ter SP/SP, para retornar a saída.
- [ ] 

---
 
Fórmula Fuzzy $(x,\ T(x),\ U,\ G,\ M)$
$x = Conhecimento$
$T(x) = {Não\ Satisfaz\ (NS),\ Satisfaz\ Parcialmente\ (SP),\ Satisfaz\ (S)}$
$U =\ (0:10)$
$G =\ [NS <(+-)\ 4] \ [SP\ próximo\ de\ 5\ e\ 7]\ [S >(+-)\ 8]$

$$\begin{array} \
M = [\\ NS = [0.0/1,\ 1.0/1,\ 1.0/2,\ 1.0/3,\ 0.8/4,\ 0.2/5,\ 0.0/6,\ 0.0/7,\ 0.0/8,\ 0.0/9,\ 0.0/10] \\
	SP = [0.0/0,\ 0.0/1,\ 0.0/2,\ 0.0/3,\ 0.2/4,\ 0.8/5,\ 1.0/6,\ 0.8/7,\ 0.2/8,\ 0.0/9,\ 0.0/10] \\
	S = [0.0/0,\ 0.0/1,\ 0.0/2,\ 0.0/3,\ 0.0/4,\ 0.0/5,\ 0.0/6,\ 0.2/7,\ 0.8/8,\ 1.0/9,\ 1.0/10]\\
	]
\end{array}
$$

---
### Prova
- [ ] Diferença entre lógica fuzzy e lógica tradicional
- [ ] Conjuntos fuzzy
- [ ] Operações entre conj. Fuzzy
- [ ] Variável linguística
- [ ] Modificadores


{0 = 0.8, 80 = 0.0, 20 = 0.8, 100 = 0.0, 40 = 0.8, 60 = 0.0},
{0 = 0.0, 80 = 0.2, 20 = 0.0, 100 = 0.0, 40 = 0.2, 60 = 0.2}
{0 = 0.8, 80 = 0.2, 20 = 0.8, 100 = 0.0, 40 = 0.8, 60 = 0.2}

- [ ] Pegar a pertinência das possibilidades: Q1: 1.0 | Q2: 0.8 | Q2: 0.2
$$\begin{array}\
	A_i\ |\ B_i\ /\ C_i \\
	------ \\
    NS \ | \  SP \ 	/ \   B\\
    NS \ | \ S	\ / \ I
\end{array}
$$

Arthur: {0=0.2, 80=0.2, 20=0.2, 100=0.0, 40=0.2, 60=0.8}
Meu: {0=0.2, 80=0.2, 20=0.2, 100=0.0, 40=0.2, 60=0.8}

uniao: {0=0.2, 80=0.2, 20=0.2, 100=0.0, 40=0.2, 60=0.8}
uniao: {0=0.2, 80=0.2, 20=0.2, 100=0.0, 40=0.2, 60=0.8}