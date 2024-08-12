# Physical-simulations
This project consists of storing codes simulating physical experiments.

## 1 <a href = 'https://github.com/celso05/Physical-simulations/blob/main/Campo_eletrico.ipynb'> Campo Elétrico </a>
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
