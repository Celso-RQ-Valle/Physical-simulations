# Physical-simulations
This project consists of storing codes simulating physical experiments.

## <a href = 'https://github.com/celso05/Physical-simulations/blob/main/Campo_eletrico.ipynb'> 1 - Campo Elétrico </a>
### Descrição Teórica do Código

Este código Python visa a visualização do campo elétrico gerado por duas cargas pontuais em um plano bidimensional. Ele utiliza a biblioteca `numpy` para cálculos numéricos e `matplotlib` para a visualização gráfica.

#### 1. Fundamentos Teóricos

O campo elétrico $\( \mathbf{E} \)$ devido a uma carga pontual $\( Q \)$ em um ponto no espaço é dado pela equação:

$$
\mathbf{E} = \frac{k \cdot Q}{r^2} \hat{\mathbf{r}}
$$

onde:
- $\( k \)$ é a constante de Coulomb $\( k = \frac{1}{4 \pi \epsilon_0} \)$, com $\( \epsilon_0 \)$ sendo a permissividade elétrica do vácuo.
- $\( Q \)$ é a magnitude da carga.
- $\( r \)$ é a distância entre a carga e o ponto de observação.
- $\( \hat{\mathbf{r}} \)$ é o vetor unitário na direção do vetor deslocamento da carga ao ponto de observação.

Neste código, duas cargas \( Q_1 \) e \( Q_2 \) são posicionadas em coordenadas especificadas no plano, e o campo elétrico resultante em cada ponto do plano é calculado como a soma vetorial dos campos elétricos de ambas as cargas.

#### 2. Geração do Grid

Primeiro, um grid bidimensional de pontos é criado utilizando as funções `numpy.linspace` e `numpy.meshgrid`. Este grid abrange uma área de $\([-5, 5]\)$ em ambas as direções $\( x \)$ e $\( y \)$, permitindo a avaliação do campo elétrico em uma ampla região ao redor das cargas.

#### 3. Cálculo do Campo Elétrico

Para cada ponto do grid:
- Calcula-se a distância $\( d_1 \)$ e $\( d_2 \)$ de cada carga para o ponto.
- Os vetores deslocamento $\( \mathbf{v}_1 \)$ e $\( \mathbf{v}_2 \)$ são determinados.
- Os vetores unitários $\( \hat{\mathbf{v}}_1 \)$ e $\( \hat{\mathbf{v}}_2 \)$ são obtidos dividindo os vetores deslocamento pela respectiva distância.
- O campo elétrico resultante é então calculado somando-se os vetores campo elétrico individuais de cada carga, conforme a equação acima.

Para evitar divisões por zero, um pequeno valor chamado `Erro` é adicionado às distâncias $\( d_1 \)$ e $\( d_2 \)$.

#### 4. Visualização

A visualização do campo elétrico é realizada usando as seguintes técnicas:
- **Plotagem das Cargas**: As cargas são representadas como pontos coloridos no plano.
- **Vetores do Campo Elétrico**: O campo elétrico em cada ponto do grid é representado por vetores usando `plt.quiver`.
- **Linhas de Fluxo**: As linhas de fluxo do campo elétrico são desenhadas utilizando `plt.streamplot`, mostrando a direção do campo.
- **Curvas de Nível**: As intensidades do campo elétrico são mostradas através de curvas de nível preenchidas `plt.contourf`, e uma barra de cores é incluída para indicar a magnitude do campo.

#### 5. Parâmetros Ajustáveis

O código permite ajustar as magnitudes das cargas $\( Q_1 \)$ e $\( Q_2 \)$, possibilitando a análise de diferentes configurações de campo elétrico. O usuário pode modificar os valores das cargas diretamente antes de chamar a função de plotagem.

#### Referências

- A equação do campo elétrico é baseada na Lei de Coulomb.
- A visualização gráfica é inspirada em métodos comuns de representação de campos vetoriais em física.

Este código é uma ferramenta didática útil para compreender a interação entre campos elétricos gerados por duas cargas.

Exemplo:

![1723759966270190](https://github.com/user-attachments/assets/98d2362c-a591-4ce0-ac0a-11e923ed5c52)

## <a href = 'https://github.com/Celso-RQ-Valle/Physical-simulations/blob/main/Git%20Monte%20Carlo.ipynb'> 2 - Simulação por Monte Carlo </a>
### Descrição Teórica do Código

Este código Python utiliza o método de Monte Carlo para realizar três simulações distintas: a integral de \( \sin(x) \), a estimativa de \( \pi \), e a simulação de tendenciosidade de um estimador de média. Ele faz uso da biblioteca `numpy` para os cálculos numéricos e `matplotlib` para a visualização gráfica.

#### 1. Fundamentos Teóricos

O método de Monte Carlo baseia-se na geração de números aleatórios para estimar valores de interesse. Em vez de usar uma abordagem determinística, ele simula processos aleatórios e faz inferências a partir das médias de resultados obtidos em diversas iterações.

#### 2. Cálculo da Integral de $\sin(x)$

A primeira parte do código realiza a integração de $\sin(x)$ no intervalo $[0, \pi]$ usando o método de Monte Carlo. A integral é estimada pela seguinte fórmula:

$$
\int_0^{\pi} \sin(x) dx = 2
$$

Aqui, um grande número de pontos aleatórios é gerado dentro do intervalo $[0, \pi]$ e a função $\sin(x)$ é avaliada nesses pontos. A estimativa da integral é obtida ao calcular a média das avaliações multiplicada pelo comprimento do intervalo.

#### 3. Estimativa de $\pi$

Na segunda parte, o código utiliza Monte Carlo para estimar o valor de $\pi$. Um círculo de raio 1 é inscrito em um quadrado, e pontos aleatórios são gerados dentro do quadrado. A razão entre o número de pontos que caem dentro do círculo e o número total de pontos gerados é usada para estimar $\pi$, com base na fórmula:

$$
\pi \approx 4 \times \frac{\text{número de pontos no círculo}}{\text{número total de pontos}}
$$

#### 4. Simulação de Tendenciosidade de Estimador

Na terceira parte, o código simula a tendenciosidade de um estimador de média. A cada iteração, 10 valores são gerados a partir de uma distribuição normal com valor médio real $x = 20$. Em seguida, é calculada a média dos valores após a remoção de possíveis valores extremos (via a função `removeMm`). A simulação é repetida 50.000 vezes para calcular a tendenciosidade, ou seja, a diferença entre a média estimada e o valor real $x$ .

As seguintes estatísticas são obtidas:
- **sx**: Desvio padrão das médias estimadas.
- **tend**: Tendenciosidade, ou a diferença entre a média estimada e o valor verdadeiro.
- **stend**: O erro padrão da tendenciosidade.

#### 5. Visualização

O código também oferece uma visualização gráfica dos resultados da integral de $\sin(x)$ e da estimativa de $\pi$, plotando gráficos que mostram a evolução das estimativas à medida que o número de iterações aumenta.

#### Referências

O método de Monte Carlo é amplamente utilizado em física, estatística e finanças para resolver problemas de integração e estimativa que seriam difíceis de calcular de forma determinística.

Exemplo:

![int sen](https://github.com/user-attachments/assets/0afc59dc-7b77-438c-a785-42c996281da8)
![pi mon](https://github.com/user-attachments/assets/932d13ad-fb84-4eba-b234-c9bde80d3801)

## <a href='https://github.com/Celso-RQ-Valle/Physical-simulations/blob/main/Simula%C3%A7%C3%A3o_de_Pendulo_Duplo.ipynb'> 3 - Simulação de Pêndulo Duplo </a>
### Descrição Teórica do Código

Este código Python simula o movimento de um pêndulo duplo, um sistema clássico de dinâmica não-linear que demonstra comportamento caótico em certas condições. A simulação é feita utilizando o método de Runge-Kutta de segunda ordem (RK2) para a integração numérica das equações diferenciais do sistema. As bibliotecas `numpy` e `matplotlib` são utilizadas para os cálculos numéricos e para a visualização gráfica, respectivamente, permitindo uma análise detalhada do comportamento do sistema ao longo do tempo.

#### 1. Fundamentos Teóricos

O pêndulo duplo consiste em dois pêndulos acoplados de maneira sequencial, com o segundo pêndulo suspenso na extremidade do primeiro. Cada movimento individual afeta diretamente o outro, resultando em um sistema altamente sensível às condições iniciais. Tal sensibilidade é uma característica típica de sistemas caóticos.

![images](https://github.com/user-attachments/assets/1174474a-f7cc-4844-b2cc-018542c9d0ba)


As equações do movimento são derivadas a partir das leis de conservação de energia e do momento angular, mas devido à sua natureza não-linear, sua solução analítica é inviável. Por isso, opta-se por uma abordagem numérica para a solução, utilizando o método de Runge-Kutta para resolver as equações diferenciais ordinárias.

#### 2. Simulação do Pêndulo Duplo

Inicialmente, o código define os parâmetros físicos do sistema: as massas dos corpos ($m_1$, $m_2$), os comprimentos dos fios ($l_1$, $l_2$), e as condições iniciais para os ângulos ($\theta_1$, $\theta_2$) e os momentos conjugados ($p_1$, $p_2$). O método de Runge-Kutta é utilizado para integrar as equações do movimento no tempo e determinar a evolução tanto dos ângulos quanto das energias cinética e potencial do sistema.

No início da simulação, é feita a suposição de que a massa do primeiro corpo ($m_1$) é significativamente maior que a do segundo ($m_2$), ou seja, $m_1 \gg m_2$. Essa consideração inicial simplifica o comportamento do sistema e resulta em um movimento mais previsível para o corpo menor, uma vez que as forças geradas pelo segundo corpo têm pouca influência no movimento do primeiro.

As equações diferenciais que descrevem o sistema, com base na energia e no momento angular, são expressas da seguinte forma:

$$
\dot{\theta}_1 = \frac{l_2 p_1 - l_1 p_2 \cos(\theta_1 - \theta_2)}{(l_2 l_1^2) (m_1 + m_2 \sin^2(\theta_1 - \theta_2))}
$$

$$
\dot{p}_1 = -(m_1 + m_2) g l_1 \sin(\theta_1) - A + B
$$

Os termos $A$ e $B$ representam contribuições das interações entre os momentos conjugados e os ângulos, sendo recalculados a cada iteração do processo de integração.

#### 3. Comparação de Casos: $m_1 \gg m_2$ e $m_1 \sim m_2$

Após as simulações iniciais com a consideração de que $m_1$ é muito maior que $m_2$, o código também explora o cenário onde as massas dos corpos são comparáveis ($m_1 \sim m_2$). Essa transição ilustra como a dinâmica do sistema se altera à medida que as influências mútuas entre os dois corpos se tornam mais pronunciadas.

Quando $m_1 \gg m_2$, o movimento do primeiro pêndulo domina o sistema, e o segundo pêndulo se move essencialmente como uma extensão passiva, com perturbações muito pequenas no comportamento global do sistema. Nesse cenário, o movimento é menos caótico e mais previsível, pois o corpo menor não exerce uma força significativa sobre o corpo maior.

No entanto, quando $m_1$ é comparável a $m_2$, o sistema exibe um comportamento muito mais caótico e complexo. Nessa configuração, ambos os corpos influenciam fortemente o movimento um do outro, e pequenas variações nas condições iniciais podem resultar em grandes divergências nos resultados da simulação. O movimento passa a ser extremamente sensível a perturbações, e o sistema evolui para um regime caótico muito mais evidente.

#### 4. Visualização

A simulação gera diversos gráficos que ajudam a entender o comportamento do sistema. Inicialmente, são gerados gráficos com a suposição de que $m_1 \gg m_2$, permitindo observar o movimento mais suave e previsível. Em seguida, gráficos adicionais são produzidos para o caso em que $m_1 \sim m_2$, ilustrando o aumento na complexidade do sistema e o comportamento caótico emergente.

Esses gráficos incluem:

- A trajetória dos ângulos $\theta_1$ e $\theta_2$ ao longo do tempo;
- O espaço de fase do sistema (representação gráfica da relação entre ângulos e velocidades angulares);
- A evolução das energias cinética e potencial dos dois corpos, demonstrando como a energia é trocada entre os pêndulos.

Esses gráficos são gerados usando a biblioteca `matplotlib`, que permite uma visualização clara e detalhada do comportamento do sistema em diferentes condições.

#### 5. Comportamento Caótico

Uma característica marcante do pêndulo duplo, especialmente no caso em que $m_1 \sim m_2$, é o comportamento caótico. Pequenas diferenças nas condições iniciais podem resultar em trajetórias radicalmente diferentes para os ângulos e velocidades angulares. O código ilustra esse comportamento, permitindo simular o sistema em diferentes configurações iniciais e observar como o comportamento se altera de forma imprevisível.

#### Referências

O estudo de sistemas dinâmicos não-lineares, como o pêndulo duplo, é fundamental para a compreensão de fenômenos caóticos em várias áreas da física e matemática. Este exemplo destaca como sistemas aparentemente simples podem gerar dinâmicas extremamente complexas e imprevisíveis.

Exemplo:

![pos2](https://github.com/user-attachments/assets/c359cb7a-a72b-4149-bc43-d0b08a4fa5bd)

