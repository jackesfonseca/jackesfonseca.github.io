---
title: Portifolio 5 - IA
date: 2023-12-11 13:30:00 -0400
categories: [portfolio - inteligencia artificial, portifolio 5]
tags: [ai, portfolios, algoritmos de busca]
---

## Introdução

Neste portfólio, exploraremos profundamente o intrigante universo das Redes Bayesianas e o gerenciamento de incertezas. Imaginem-se em um labirinto escuro, com apenas um farol para iluminar o caminho à frente. Cada passo pode aproximá-los da saída ou levá-los a um beco sem saída. Essa situação de incerteza é semelhante ao que enfrentamos ao aplicar a teoria da probabilidade em diversos campos, desde a inteligência artificial até a economia e medicina.

A incerteza, embora muitas vezes indesejada, é uma parte intrínseca de nossa existência. Como lidamos com isso? É aí que entram a utilidade e a teoria de decisão, auxiliando na tomada de decisões informadas em face da incerteza. Neste portfólio, mergulharemos profundamente na notação básica de probabilidade e discutiremos conceitos chave, como independência e independência condicional.

Sabiam que o Reverendo Thomas Bayes, que deu origem à famosa Regra de Bayes, nunca publicou sua descoberta em vida? Um amigo encontrou seu trabalho e o publicou postumamente. Agora, essa regra é a pedra angular de muitos sistemas de inferência, incluindo as redes Bayesianas (Bellhouse, 2004).

Redes Bayesianas são uma ferramenta poderosa que nos permite lidar com a incerteza de maneira estruturada e gráfica. Se você já usou um filtro de spam de email, já se beneficiou das redes Bayesianas!

Da mesma forma, se já usou um GPS para navegar, provavelmente já se beneficiou do Filtro de Kalman, uma aplicação específica de raciocínio probabilístico ao longo do tempo. Esses filtros estimam a localização e a velocidade de um objeto a partir de medições ao longo do tempo, que são inerentemente incertas.

Esses são apenas alguns dos tópicos fascinantes que exploraremos neste portfólio. Além disso, discutiremos diversos temas relacionados e compartilharemos reflexões, análises e exemplos práticos. Espero que desfrutem desta jornada pelo mundo da probabilidade, incerteza e decisões racionais!

## Incerteza

Agentes inteligentes, como robôs ou algoritmos de IA, frequentemente se encontram em situações de incerteza, seja devido à observação parcial, ao não determinismo ou a eventos imprevisíveis. Para lidar com isso, esses agentes podem empregar a teoria da probabilidade como ferramenta para quantificar a incerteza.

Vamos analisar o exemplo de um “Smart Taxi” que precisa calcular o melhor momento para sair, considerando várias variáveis incertas, para garantir que o passageiro chegue ao aeroporto a tempo para o voo.

A viagem ao aeroporto pode variar com base no trânsito, condições climáticas e possibilidade de acidentes na rota.
Trânsito	Tempo médio de viagem
Médio	30 min
Pesado	45 min
Leve	20 min

Probabilidade de chuva:

    Trânsito pesado: 50%

Probabilidade de acidente:

    Acréscimo no tempo de viagem: 5%, 10 min

Por exemplo, entre as 19h e as 21h, o trânsito é médio. Se chover (50% de chance), o trânsito ficará pesado. Existe uma probabilidade de 5% de ocorrer um acidente, o que aumentaria o tempo de viagem em 10 minutos.

Temos também o exemplo de diagnóstico médico. Uma dor de dente, por exemplo, pode estar relacionada a cáries, gengivite, abcessos, entre outros problemas. Cada diagnóstico é uma possibilidade e cada um deles tem sua probabilidade associada. Em vez de tentar todos os diagnósticos possíveis, um médico pode fazer uma avaliação probabilística para identificar o problema mais provável.

A teoria da probabilidade nos fornece uma maneira eficaz de lidar com a incerteza. Por meio de compromissos epistemológicos, um agente inteligente é capaz de lidar com situações onde a verdade de uma sentença é desconhecida, atribuindo um grau de crença numérico variando entre 0 (certamente falso) e 1 (certamente verdadeiro). Esta abordagem é fundamental para resolver problemas de qualificação e tomar decisões informadas.

## Utilidade

O conceito de “utilidade” desempenha um papel fundamental na tomada de decisões em cenários de incerteza. Na teoria da utilidade, cada resultado ou estado potencial é associado a um valor de utilidade, representando a preferência de um agente. O agente então busca maximizar a utilidade total, tomando decisões que levam aos estados com maior utilidade.

Retornando ao nosso exemplo do Smart Taxi, há diversas opções de rotas e tempos de partida que poderiam ser escolhidos. Cada um desses caminhos possui um nível de utilidade para o cliente, baseado em suas preferências pessoais. Talvez o cliente prefira chegar mais cedo ao aeroporto para evitar estresse, ou talvez prefira maximizar o tempo de trabalho e chegar mais próximo do voo. Essas preferências influenciam a utilidade de cada opção.
Caminho	Chegada no Aeroporto	Utilidade
Caminho 1	19:30	80
Caminho 2	20:00	95
Caminho 3	20:30	70

No exemplo acima, o Caminho 2 tem a maior utilidade para o cliente, sendo a melhor opção de acordo com a teoria da utilidade.

É importante ressaltar que a utilidade é subjetiva e pode variar consideravelmente entre diferentes agentes, dependendo de suas preferências individuais. A função de utilidade pode levar em consideração qualquer conjunto de preferências, desde as mais comuns até as mais peculiares. Ao compreender e aplicar a teoria da utilidade, os agentes inteligentes podem tomar decisões mais informadas e alinhadas com suas preferências ou as preferências de seus usuários.

## Teoria de Decisão

A teoria de decisão é uma ferramenta essencial para a tomada de decisões racionais em contextos de incerteza. Ela é, em sua essência, a interseção da teoria da probabilidade, que lida com a incerteza, e a teoria da utilidade, que expressa preferências. Esta combinação pode ser representada pela seguinte fórmula:

Decision theory=Probability theory+Utility theoryDecision theory=Probability theory+Utility theory

O princípio básico da teoria de decisão é que um agente é racional se e somente se escolhe a ação que gera a maior utilidade esperada, calculada a partir da média de todos os resultados possíveis da ação. Este conceito é conhecido como o Princípio da Utilidade Máxima Esperada (MEU, do inglês maximum expected utility).

Um agente operando sob a teoria de decisão se comporta da seguinte maneira:

python

```
function dt-agent(percept) returns an action
  persistent: belief_state, probabilistic beliefs about the current state of the world
  action, the agent's action

  update belief_state based on action and percept
  calculate outcome probabilities for actions,
    given action descriptions and current belief_state
  select action with highest expected utility
    given probabilities of outcomes and utility information
  return action
```

Nesta função, o agente primeiramente atualiza seu estado de crença com base na ação e percepção. Em seguida, calcula as probabilidades dos resultados para as ações possíveis, considerando as descrições das ações e o estado atual de crença. Finalmente, seleciona a ação que apresenta a maior utilidade esperada, levando em conta as probabilidades dos resultados e as informações de utilidade.

Se voltarmos ao exemplo do Smart Taxi, o agente decisional calcularia a utilidade esperada de cada rota e horário de partida possíveis, considerando as probabilidades de ocorrências como trânsito, chuva e acidentes. Então, o agente escolheria a ação - isto é, a rota e o horário de partida - que maximiza essa utilidade esperada. Dessa forma, a teoria de decisão auxilia na tomada de decisões racionais e bem informadas em situações complexas e incertas.

## Notação Básica de Probabilidade

A teoria da probabilidade proporciona um arcabouço formal para lidar com a incerteza, oferecendo uma base sólida para modelar raciocínio e inferência sob condições incertas. Antes de aprofundarmos em suas aplicações, é essencial compreender alguns conceitos fundamentais e notações básicas de probabilidade.

O conjunto que engloba todos os estados de mundos possíveis é denominado espaço amostral. Esses estados são mutuamente exclusivos e exaustivos. Para representação, utilizamos a letra grega Ω para denotar o espaço amostral, enquanto a letra ω é empregada para representar um elemento específico desse espaço.

Um princípio básico da probabilidade estipula que todo estado de mundo possível possui uma probabilidade situada entre 0 e 1, e a probabilidade do conjunto total de estados de mundo é 1. Este é um axioma fundamental da teoria da probabilidade.

Vamos reiterar esses conceitos utilizando um exemplo concreto abordado em sala de aula.

Definimos as seguintes variáveis aleatórias:

    Cárie (Cavity) = {verdadeiro, falso}
    Dor de dente (Toothache) = {verdadeiro, falso}
    Problema com a sonda dental (Catch) = {verdadeiro, falso}

A tabela abaixo apresenta a distribuição de probabilidade conjunta para essas variáveis:
Toothache-ToothacheCatch-CatchCavity0.1080.0120.0720.008-Cavity0.0160.0640.1440.576
Cavity-Cavity​ToothacheCatch0.1080.016​-Toothache-Catch0.0120.064​0.0720.144​0.0080.576​

Note que a soma de todas as probabilidades é 1, como requerido em qualquer distribuição de probabilidade.

A probabilidade de uma proposição é a soma das probabilidades dos mundos onde a proposição é verdadeira. Por exemplo, para calcular a probabilidade de Cavity ∨ Toothache (cárie ou dor de dente):

P(Cavity∨Toothache)=0.108+0.012+0.072+0.008+0.016+0.064=0.28P(Cavity∨Toothache)=0.108+0.012+0.072+0.008+0.016+0.064=0.28

Podemos também calcular a probabilidade marginal de Cavity, que é a soma das probabilidades para Cavity em todos os possíveis estados das outras variáveis:

P(Cavity)=0.108+0.012+0.072+0.008=0.2P(Cavity)=0.108+0.012+0.072+0.008=0.2

Esse procedimento é conhecido como marginalização, pois "marginaliza" (remove) as outras variáveis.

Formalmente, a marginalização para qualquer conjunto de variáveis Y e Z é dada por:

P(Y)=∑P(Y,Z=z), para todo zP(Y)=∑P(Y,Z=z), para todo z

Aplicando à nossa situação, temos:

P(Cavity)=P(Cavity,Toothache,Catch)+P(Cavity,Toothache,−Catch)+P(Cavity,−Toothache,Catch)+P(Cavity,−Toothache,−Catch)P(Cavity)=P(Cavity,Toothache,Catch)+P(Cavity,Toothache,−Catch)+P(Cavity,−Toothache,Catch)+P(Cavity,−Toothache,−Catch)
=(0.108,0.016)+(0.012,0.064)+(0.072,0.144)+(0.008,0.576)=(0.2,0.8)=(0.108,0.016)+(0.012,0.064)+(0.072,0.144)+(0.008,0.576)=(0.2,0.8)

O gráfico de barras acima representa as probabilidades calculadas. Podemos observar que a probabilidade de ter cárie ou dor de dente (Cavity ∨ Toothache) é maior do que a probabilidade de apenas ter cárie (Cavity). Isso faz sentido, pois o evento "Cavity ∨ Toothache" inclui mais possibilidades do que apenas o evento "Cavity".

Isso ilustra como a teoria da probabilidade pode ser aplicada para quantificar a incerteza em situações do mundo real, como em diagnósticos médicos. Ao compreender esses conceitos e utilizar ferramentas de cálculo e visualização, podemos fazer previsões mais informadas e tomar decisões mais acertadas.

## Independência e Independência Condicional

Independência é um conceito fundamental na teoria das probabilidades. Se dois eventos são independentes, a ocorrência de um não afeta a probabilidade do outro. Formalmente, dizemos que dois eventos A e B são independentes se a probabilidade do evento A ocorrer dado que o evento B ocorreu é igual à probabilidade original de A.

Por exemplo, se estivermos jogando uma moeda e um dado simultaneamente, os resultados são independentes. O resultado do lançamento da moeda não afeta o resultado do lançamento do dado.

Independência Condicional é uma forma de independência que é válida quando temos alguma informação adicional. Dois eventos A e B são condicionalmente independentes dado um terceiro evento C se a probabilidade de A ocorrer dado que B e C ocorreram é igual à probabilidade de A ocorrer dado que C ocorreu.

Por exemplo, se temos três cartas, uma vermelha, uma azul e uma verde, a probabilidade de retirar a carta vermelha não é afetada pela retirada da carta azul. Mas se sabemos que a carta verde já foi retirada, a retirada da carta azul afeta a probabilidade de retirar a carta vermelha.

## Regra de Bayes, Aplicações e Modelo Ingênuo

A Regra de Bayes é um princípio crucial na inferência estatística, permitindo a atualização de crenças a priori com base em novos dados. Formalmente expressa como:

P(A∣B)=P(B∣A)⋅P(A)P(B)P(A∣B)=P(B)P(B∣A)⋅P(A)​

Isso é aplicável em diversos contextos, como na medicina, onde a probabilidade de uma doença pode ser atualizada com base em resultados de testes. O Modelo Ingênuo de Bayes, uma extensão da Regra de Bayes, assume independência entre características de um evento, sendo usado, por exemplo, em filtros de spam de e-mail.

Um cenário de aplicação é o Wumpus World, um jogo de inteligência artificial. A Regra de Bayes atualiza a probabilidade de um Wumpus em sala adjacente ao perceber um "fedor", enquanto o Modelo Ingênuo é útil para calcular a probabilidade de diferentes estados do mundo e guiar as ações do jogador com base em percepções independentes.

## Redes Bayesianas

As Redes Bayesianas são modelos gráficos probabilísticos que representam variáveis e suas dependências condicionais por meio de um grafo direcionado acíclico (DAG). Essas redes são valiosas para modelar relações complexas de causalidade e correlação, como a relação entre "Chuva", "Engarrafamento" e "Chegar tarde no trabalho".

## Inferência

Inferência é o processo de dedução de propriedades de uma população ou distribuição de probabilidade com base em uma amostra. Utilizando a Regra de Bayes, é possível inferir a probabilidade de uma pessoa ter uma doença dado um teste positivo.

## Tempo e Incerteza

Tempo e incerteza na modelagem de incertezas envolvem a dimensão temporal. Modelos estocásticos como cadeias de Markov lidam com essa incerteza no tempo. Em previsão do tempo, por exemplo, a incerteza é introduzida ao relacionar as condições atuais às previsões futuras.

## Estados e Observações

Problemas práticos frequentemente envolvem estados (condições do sistema) e observações (dados coletados sobre esses estados). Em robótica, por exemplo, os estados podem ser a posição do robô, enquanto as observações são dados dos sensores.

## Modelo de Transição e Modelos de Sensores

O modelo de transição representa a probabilidade de transição entre estados em um sistema estocástico, crucial em cadeias de Markov. Modelos de sensores descrevem a probabilidade de uma observação dada um estado, essenciais em problemas de filtro de partículas e localização de robôs. Em um robô de navegação, o modelo de transição pode indicar a probabilidade de o robô mover-se entre posições, enquanto o modelo do sensor expressa a probabilidade das leituras dos sensores dadas as posições do robô.

### Filtragem

A filtragem é a tarefa de calcular a distribuição posterior do estado atual dado o histórico de observações, útil para estimar o estado presente de um sistema. No exemplo em Python, um filtro de partículas simples é utilizado. Um conjunto de partículas representa possíveis estados, e seus pesos são atualizados com base no modelo do sensor. Os pesos são normalizados para refletir a probabilidade.

### Predição

A predição envolve o cálculo da distribuição posterior do estado futuro dado o histórico de observações, permitindo prever o estado subsequente do sistema. No exemplo Python, um modelo de transição é aplicado a um conjunto de partículas para projetar o estado futuro.

### Suavização

Suavização consiste em calcular a distribuição posterior de um estado passado dado o histórico de observações, sendo útil para estimar estados anteriores de um sistema. Geralmente, requer algoritmos mais complexos. No exemplo fornecido, não é exemplificado devido à sua complexidade.

### Explicação Mais Provável

A explicação mais provável é a tarefa de encontrar a sequência de estados mais provável dada a sequência de observações. O exemplo em Python utiliza o algoritmo de Viterbi, amplamente usado em Modelos Ocultos de Markov.

### Aprendizado

Aprendizado envolve ajustar os parâmetros de um modelo para melhor se adequar aos dados. Em modelos probabilísticos, a verossimilhança máxima ou métodos bayesianos geralmente são usados para aprender parâmetros. O exemplo em Python ilustra o aprendizado da média em um modelo gaussiano.

Embora o exemplo seja simples, a aprendizagem em modelos probabilísticos e aprendizado de máquina pode ser complexa, envolvendo desafios como overfitting, underfitting, regularização e validação cruzada, não abordados neste portfólio.

## Modelo Oculto de Markov

O Modelo Oculto de Markov (HMM) é um modelo estatístico onde o sistema é um processo de Markov com parâmetros desconhecidos. Determinar os parâmetros ocultos a partir dos observáveis é o desafio. A implementação em Python seria extensa, mas bibliotecas como hmmlearn oferecem soluções prontas.

## Filtros de Kalman

Os Filtros de Kalman são ótimos em teoria de controle e processamento de sinais, usados para estimar o estado interno de um sistema dinâmico linear a partir de medições observáveis. Implementações em Python estão disponíveis em bibliotecas como pykalman.

## Quantificando Incertezas e Redes Bayesianas

Em face de um novo problema, considerar como as incertezas podem ser representadas é crucial. As Redes Bayesianas são ferramentas poderosas para modelar incertezas e relações complexas entre variáveis. Amostragem de Monte Carlo, usando algoritmos como Gibbs Sampling e Metropolis-Hastings, é comum para inferências em Redes Bayesianas. Estes métodos são fundamentais para avaliar a probabilidade de eventos complexos, como diagnósticos médicos baseados em vários sintomas.

## Raciocínio Probabilístico ao Longo do Tempo e Filtros de Kalman

O raciocínio probabilístico é uma ferramenta poderosa que pode ser estendida para lidar com problemas temporais e incertezas. Modelos como o Modelo Oculto de Markov (HMM) e Filtros de Kalman são eficazes em lidar com a dinâmica temporal e incertezas em diferentes contextos.

O Filtro de Kalman é particularmente útil em combinar previsões de um modelo físico com observações ruidosas para estimar o verdadeiro estado de um sistema. É amplamente utilizado em aplicações como rastreamento de localização em GPS, análise de séries temporais financeiras e controle de sistemas robóticos. Os modelos de transição e sensores desempenham papéis essenciais nos Filtros de Kalman, onde o primeiro descreve as mudanças no estado ao longo do tempo, e o segundo modela a probabilidade de diferentes observações dadas diferentes estados.

## Discussões:

    - Análise de Novos Problemas com Redes Bayesianas:
    Redes Bayesianas são amplamente aplicadas em diversos domínios para modelar a incerteza. Na medicina, podem ser usadas para diagnosticar com base em sintomas e histórico do paciente, enquanto em engenharia, modelam a confiabilidade de sistemas complexos.

    - Algoritmos Gibbs Sampling e Metropolis-Hastings:
    Estes são algoritmos de amostragem Monte Carlo usados em inferência estatística, especialmente úteis para distribuições de alta dimensão. São comuns em amostragem de Redes Bayesianas para obter a distribuição posterior.

    - Sistemas Práticos/Comerciais Baseados em Incerteza:
    Sistemas de recomendação, como os da Amazon e Netflix, lidam com incertezas sobre as preferências do usuário, utilizando métodos como filtragem colaborativa, uma forma de inferência probabilística.

    - Exemplos Práticos:
    Exemplos apresentados, como a avaliação da qualidade das bananas com Redes Bayesianas e o rastreamento da altura de um macaco com o Filtro de Kalman, demonstram aplicações práticas de raciocínio probabilístico.

    - Análise de Novos Problemas Temporais Baseados em Incertezas:
    Problemas temporais, como previsão do tempo e análise econômica, envolvem incertezas inerentes. Lidar com essas incertezas é crucial para fazer previsões precisas.

    - Discussão Mais Detalhada sobre Modelos de Transição e de Sensores:
    Modelos de transição e sensores são fundamentais em sistemas que lidam com incertezas, fornecendo maneiras de modelar a evolução do estado do sistema ao longo do tempo e como observamos esse estado.

    - Descrição de Algoritmos:
    A descrição detalhada e a implementação de algoritmos, como o Filtro de Kalman e a Rede Bayesiana, são cruciais para entender essas técnicas. O estudo desses algoritmos é parte fundamental do aprendizado de máquina e inferência estatística.

O entendimento desses conceitos e técnicas proporciona uma base sólida para abordar problemas complexos que envolvem incertezas e mudanças ao longo do tempo. Recomenda-se a exploração adicional por meio de estudos aprofundados e aplicação prática em contextos específicos.

## Projetos e Problemas

### Rede Bayesiana: Avaliando a Qualidade das Bananas

    Instalação das Dependências:
        Instalação da biblioteca pgmpy para trabalhar com modelos gráficos probabilísticos, incluindo redes bayesianas.

bash

pip install pgmpy

    Importando as Bibliotecas Necessárias:
        Importação das bibliotecas necessárias para o exemplo.

python

from pgmpy.models import BayesianNetwork
from pgmpy.factors.discrete import TabularCPD

    Construindo a Rede Bayesiana:
        Definição da estrutura da rede e das distribuições de probabilidade condicional para cada nó.

python

model = BayesianNetwork([('Qualidade', 'Cor'), ('Qualidade', 'Doçura')])
cpd_qualidade = TabularCPD('Qualidade', 2, [[0.6], [0.4]])
### Definição das CPDs para Cor e Doçura

model.add_cpds(cpd_qualidade, cpd_cor, cpd_doçura)
assert model.check_model()

    Realizando Inferências:
        Uso da rede para inferir a probabilidade de uma banana ser de alta qualidade dada sua cor e doçura.

python

from pgmpy.inference import VariableElimination

infer = VariableElimination(model)
posterior_qualidade = infer.query(['Qualidade'], evidence={'Cor': 1, 'Doçura': 1})
print(posterior_qualidade)

    Resultado Esperado:
        O resultado será a distribuição posterior da qualidade da banana dada a cor e doçura observadas.

plaintext

+--------------+------------------+
| Qualidade    |   phi(Qualidade) |
+==============+==================+
| Qualidade(0) |           0.1385 |
+--------------+------------------+
| Qualidade(1) |           0.8615 |
+--------------+------------------+

    Fontes Recomendadas:
        Redes Bayesianas na Wikipedia
        Documentação da biblioteca pgmpy
        Livro: "Probabilistic Graphical Models: Principles and Techniques"

Filtro de Kalman: Rastreando a Altura de um Macaco Saltador

    Instalação das Dependências:
        Instalação da biblioteca filterpy para processamento de sinais e filtragem.

bash

pip install filterpy

    Importando as Bibliotecas Necessárias:
        Importação das bibliotecas necessárias para o exemplo.

python

from filterpy.kalman import KalmanFilter
import numpy as np

    Inicializando o Filtro de Kalman:
        Inicialização do Filtro de Kalman com um estado unidimensional e uma única observação.

python

kf = KalmanFilter(dim_x=1, dim_z=1)

    Definindo o Modelo do Filtro de Kalman:
        Definição do modelo, incluindo estado inicial, matriz de transição de estado, matriz de observação e matrizes de covariância.

python

kf.x = np.array([0.])  # altura inicial
### Definição das matrizes F, H, P, R e Q

kf.P *= 1000.  # alta incerteza inicial na altura do macaco

    Gerando Dados de Teste:
        Geração de alturas simuladas para o macaco e adição de ruído gaussiano.

python

### Geração de alturas simuladas e adição de ruído

    Aplicando o Filtro de Kalman:
        Aplicação do Filtro de Kalman às medições, prevendo e atualizando a altura estimada.

python

for r_height, height in zip(heights, heights_noised):
    kf.predict()
    kf.update(height)
    print ('Altura real: {:3.2f} | Altura estimada: {:3.2f} | Altura com ruido: {:3.2f}'.format(r_height, kf.x[0], height))

    Resultado Esperado:
        Saída com estimativas da altura do macaco em cada passo de tempo.

plaintext

Altura real: 10.00 | Altura estimada: 10.47 | Altura com ruido: 10.58
Altura real: 15.00 | Altura estimada: 13.93 | Altura com ruido: 17.10
Altura real: 14.00 | Altura estimada: 13.94 | Altura com ruido: 13.97
Altura real: 16.00 | Altura estimada: 18.88 | Altura com ruido: 29.09
Altura real: 15.00 | Altura estimada: 21.31 | Altura com ruido: 27.03

### Fontes Recomendadas:
        Introdução ao Filtro de Kalman
        Documentação da biblioteca filterpy
        Filtro de Kalman na Wikipedia
        Livro: "Kalman and Bayesian Filters in Python"