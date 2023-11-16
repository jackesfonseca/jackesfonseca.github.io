---
title: Portifolio 4 - IA
date: 2023-10-16 13:30:00 -0400
categories: [portfolio - inteligencia artificial, portifolio 4]
tags: [ai, portfolios, algoritmos de busca]
---
## Agente Baseado em Conhecimento; 
Os Agentes Baseados em Conhecimento são sistemas inteligentes que utilizam representações simbólicas do conhecimento para realizar suas tarefas. Eles armazenam informações sobre o ambiente e utilizam essas informações para tomar decisões inteligentes.

Existem diferentes tipos de abordagens para implementar Agentes Baseados em Conhecimento, podendo variar de sistemas especialistas a sistemas mais avançados de inteligência artificial, como por exemplo:

1. Sistema Especialista:
        Um sistema especialista é um tipo específico de ABC que se concentra em resolver o problema dentro de um domínio particular. Ele utiliza um conjunto de regras de conhecimento especializado para tomar decisões ou fazer recomendações.

2. Representação de Conhecimento:
        Diz respeito a maneira como o conhecimento fica armazenado no sistema. Podendo incluir estruturas como redes semânticas, árvores de decisão, lógica de primeira ordem, ontologias, entre outras.

3. Raciocínio Baseado em Conhecimento:
        Nessa categoria, o agente usa seu conhecimento para raciocinar a fim de chegar a conclusões. Pode envolver inferência lógica, indução, dedução, entre outros métodos.

4. Aprendizado de Máquina Baseado em Conhecimento:
        Em alguns casos, os agentes baseados em conhecimento podem incorporar técnicas de aprendizado de máquina para melhorar seu conhecimento com base em dados e experiências prévias.

5. Ontologia:
        Uma ontologia é uma estrutura que define os conceitos relevantes em um domínio específico e as relações entre esses conceitos. Pode ser usada para representar o conhecimento de forma mais formal e semântica.

6. Tomada de Decisão:
        Os agentes baseados em conhecimento são frequentemente utilizados para tomar decisões em situações extremamente complexas, utilizando o conhecimento acumulado para avaliar opções e escolher a melhor ação.

## Lógica e Processo de inferência; 
A lógica é um sistema formal para expressar e analisar argumentos, enquanto o processo de inferência é o ato de tirar conclusões a partir de uma base de conhecimento.

**Tipos de Lógica e Processo de Inferência:** Existem diversos tipos de lógica, como lógica proposicional, lógica de primeira ordem, lógica difusa e lógica temporal. O processo de inferência varia desde a dedução simples até técnicas mais complexas, como a inferência bayesiana.

**Exemplos de Lógica e Processo de Inferência:** Um exemplo de lógica proposicional seria "Se faz sol, então não irei sair". Podemos inferir que, se eu não saí, então deve ter feito sol.

**Importância da Lógica e do Processo de Inferência:** A lógica é importante para identificar os componentes do conhecimento. Na lógica proposicional, a afirmação "Se está chovendo, então a rua está molhada" ajuda a compreender a relação entre chuva e a condição da rua. A inferência, por sua vez, é essencial para derivar novas conclusões desse conhecimento.

Essas ferramentas são de extrema importância para agentes baseados em conhecimento, permitindo aprendizado e tomada de decisões mais eficientes. Por exemplo, um agente de inteligência artificial pode usar a lógica para entender as regras do xadrez e, em seguida, empregar a inferência para prever os movimentos do adversário com base nessas regras.

Portanto, enquanto a lógica estabelece relações de causa e efeito ou condições, a inferência é utilizada para fazer previsões ou chegar a novas conclusões com base nessas relações ou condições estabelecidas. Essas abordagens formam a base para a inteligência e a tomada de decisões em sistemas baseados em conhecimento.

## Agente baseado em lógica proposicional 

São agentes que utilizam a lógica proposicional para representar e manipular seu conhecimento. Esses agentes são restritos a declarações que podem ser classificadas como verdadeiras ou falsas, incapazes de expressar relações mais complexas.

**Características dos Agentes Baseados em Lógica Proposicional:** Embora limitados, esses agentes são muito bons para lidar com problemas expressos em termos de proposições simples. Sua eficiência computacional os torna adequados para aplicação em sistemas que requerem respostas em tempo real.

**Exemplos de Agentes Baseados em Lógica Proposicional:** Um exemplo prático seria um agente que monitora as condições meteorológicas e decide se deve ou não sair de casa com um guarda-chuva. Este agente pode ter regras simples como "Se está chovendo, então eu preciso de um guarda-chuva" e "Se o céu está nublado, então vai chover". Utilizando essas regras, o agente pode tomar decisões sobre a necessidade de carregar um guarda-chuva com base nas condições meteorológicas observadas.

Esses agentes são eficientes em contextos nos quais as relações de causa e efeito são diretas e podem ser expressas de maneira simples. Embora suas capacidades sejam limitadas em comparação com abordagens mais complexas, sua simplicidade e rapidez tornam-nos valiosos em situações em que a tomada de decisões precisa ser ágil e direta.

```
# representação de conhecimento em lógica proposicional
conhecimento = {'P': True, 'Q': False}

# Exemplo de regra lógica
def regra_e(p, q):
    return p and q

# Exemplo de inferência
inferencia = regra_e(conhecimento['P'], not conhecimento['Q'])

# Saída da inferência
print(f'O resultado da inferência é: {inferencia}')

```
Neste exemplo, as variáveis 'P' e 'Q' representam proposições, e a função regra_e implementa uma regra lógica (AND). A inferência é realizada com base no conhecimento fornecido

## Contribuições
Para ilustrar a aplicação da lógica proposicional em sistemas de inteligência artificial, onsidere o seguinte problema.

Exemplo: Sistema de Recomendação de Filmes em Python

```
# Base de Conhecimento (preferências do usuário)
preferencias_usuario = {'Terror': True, 'Animação': False, 'Drama': True, 'Ficcao': False}

# Filmes disponíveis com suas características
filmes = {
    'Filme1': {'Terror': True, 'Animação': True, 'Drama': False, 'Ficcao': True},
    'Filme2': {'Terror': True, 'Animação': False, 'Drama': True, 'Ficcao': False},
    'Filme3': {'Terror': False, 'Animação': True, 'Drama': True, 'Ficcao': False},
    'Filme4': {'Terror': False, 'Animação': False, 'Drama': True, 'Ficcao': True},
}

# Função de Recomendação usando Lógica Proposicional
def recomendar_filmes(usuario, filmes):
    filmes_recomendados = []

    for filme, caracteristicas in filmes.items():
        # Aplicação da lógica proposicional para a recomendação
        if all(caracteristicas[genero] == usuario[genero] for genero in usuario):
            filmes_recomendados.append(filme)

    return filmes_recomendados

# Obtendo a lista de filmes recomendados para o usuário
filmes_recomendados = recomendar_filmes(preferencias_usuario, filmes)

# Exibir os filmes recomendados
print("Filmes Recomendados:")
for filme in filmes_recomendados:
    print(f"- {filme}")


```
No exemplo acima, temos as preferências do usuário definidas por valores booleanos para diferentes gêneros de filmes. A base do conhecimento do sistema inclui características de cada um filme. A função recomendar_filmes utiliza lógica proposicional para fazer a recomendação dos filmes que se alinham com as preferências do usuário. A recomendação é baseada na correspondência entre as preferências do usuário e as características dos filmes.

Este é um exemplo básico em python, mas na prática, sistemas mais complexos podem utilizar lógica proposicional de maneiras mais sofisticadas, incorporando mais variáveis e regras para fazer recomendações mais precisas e personalizadas.

## Referencia Bibliográfica
* Russell, S., & Norvig, P. (2014). "Inteligência Artificial: Uma Abordagem Moderna." Pearson.
* Nilsson, N. J. (1998). "Artificial Intelligence: A New Synthesis." Morgan Kaufmann.