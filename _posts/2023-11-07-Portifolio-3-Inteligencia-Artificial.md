---
title: Portifolio 3 - Inteligência Artificial
date: 2023-11-07 16:56:00 -0400
categories: [portfolio - inteligencia artificial, portifolio 2]
tags: [ai, portfolios, algoritmos de busca]
---

## Representação Atômica x Fatorada
A representação atômica e a representação fatorada são duas abordagens fundamentais para trabalhar com Problemas de Satisfação de Condições (CSPs), encontrados em áreas da inteligência artificial, otimização e planejamento.

Na **representação atômica**, cada um dos estados é tratado como uma caixa preta indivisível, sem qualquer estrutura interna que seja conhecida. Essa abordagem tem como característica a simplicidade, sendo os estados considerados unidades indivisíveis, fazendo com que o problema seja mais fácil de entender e resolver em vários casos. No entanto, essa simplicidade pode ser uma limitação, uma vez que a representação atômica pode não capturar todas as nuances e complexidades de um estado real. A dificuldade de identificação de soluções eficazes para o CSP pode ser causada pela falta de detalhes internos.

Por outro lado, na **representação fatorada**, os estados existentes são quebrados em variáveis ou "fatores", ou seja, são decompostos em partes menores e mais fácil de serem gerenciados. Cada fator representa uma parte específica do estado e possui seu próprio conjunto de valores possíveis. Isso permite uma visão mais detalhada do estado. Além disso, esse tipo de representação fatorada facilita a resolução do CSP, uma vez que o problema pode ser abordado resolvendo subproblemas menores associados a cada fator. Isso pode levar a uma resolução muito mais eficiente, uma vez que a complexidade é distribuída em partes menores e mais gerenciáveis.

Em resumo, a escolha entre a representação atômica e a representação fatorada depende da natureza do problema CSP e das necessidades específicas da aplicação. A representação atômica é mais simples, mas pode ser limitada em sua capacidade de representar estados complexos. Por outro lado, a representação fatorada oferece uma visão mais detalhada permitindo uma resolução mais eficiente do problema, mas pode ser mais complexa de se trabalhar. A decisão sobre qual abordagem usar depende da análise cuidadosa do problema em questão e dos objetivos que se deseja alcançar.

## Definindo Problemas de Satisfação de Condições (CSPs)

Os Problemas de Satisfação de Restrições (CSPs) fazem parte de uma classe de problemas computacionais que impõem certas propriedades estruturais adicionais à solução buscada. São comumente usados para representar uma grande variação de situações existentes no mundo real, das quais é preciso encontrar um tipo de atribuição adequada de valores para um conjunto de variáveis que estão sujeitas a um conjunto de restrições.

Componentes dos CSPs:

* **Variáveis:** Em um CSP, os elementos do problema são representados por um conjunto de variáveis. Cada variável existente pode assumir valores em um domínio específico. Essas variáveis são importasntes para representar oo problema. Por exemplo, em um problema de escalonamento de tarefas, as variáveis podem representar as diferentes tarefas que podem ser programadas.

* **Domínio:** Para cada variável existe um domínio associado, que é o conjunto de valores possíveis para essa variável. Como no caso de um problema de coloração de mapas, o domínio de cada região do mapa seria um conjunto de cores disponíveis.

* **Restrições:** As restrições são as condições que trazem as propriedades da solução. Elas determinam quais são as combinações de valores das variáveis permitidas e quais são proibidas. Por exemplo, em um problema de horário de aulas, as restrições podem indicar que duas ou mais aulas não podem ser ministradas na mesma sala simultaneamente.

* **Objetivo:** Por fim, o objetivo principal ao resolver um CSP é encontrar uma atribuição de valores para as variáveis que satisfaça todas as restrições impostas. Em muitos casos, o objetivo pode ser encontrar uma solução para otimizar algum critério, como minimizar custos ou maximizar a utilização de recursos.

### Aplicações dos CSPs:

Os CSPs pode ser aplicado em vários tipos de aplicações, incluindo:

* Agendar tarefas para empresas e indústrias.
* Resolver quebra-cabeças lógicos, como Sudoku, palavras cruzadas e puzzles de imagens.
* Problemas de alocação de recursos em telecomunicações e muito mais.
* Roteamento de veículos e logística.
* Planejamento de recursos e atribuição de projetos.
* Layout de chips e design de circuitos eletrônicos.

Em resumo, os Problemas de Satisfação de Restrições são uma abordagem poderosa para modelar e resolver problemas complexos do mundo real, de modo que a estrutura das restrições desempenha um papel de suma importância na busca de soluções viáveis e eficientes.

## Tipos de Condições 
Existem diferentes tipos de condições ou restrições em CSPs:

* **Restrições Unárias:** Envolve uma única variável.
* **Restrições Binárias:** Envolve duas variáveis.
* **Restrições n-árias:** Envolve n variáveis.

Por vezes, para simplificar a resolução do problema, restrições n-árias podem ser transformadas em um conjunto de restrições binárias através do uso de variáveis auxiliares

## Consistência

A consistência pode ser avaliada em diferentes níveis a fim de verificar a avaliação de solução de um CSP:

* **Consistência de Nó:** Verifica se cada variável pode satisfazer suas restrições individualmente. Se um valor no domínio de uma variável não for consistente com todas as restrições existente que envolvem essa variável, ele é removido do domínio.
* **Consistência de Arco:** Verifica se cada par de variáveis pode satisfazer suas restrições conjuntamente. A preocupação aqui é com a consistência entre pares de variáveis. 
* **Consistência de Trajeto:** Estende a consistência de arco para sequências de variáveis. 
* **Consistência k:** Generaliza a consistência de arco para um conjunto de k variáveis. Essa abordagem é útil quando restrições envolvem mais de duas variáveis e precisam ser verificadas em grupos maiores.
* **Consistência Global:** Verifica se o CSP completo pode satisfazer todas as suas restrições.

É importante notar que a consistência de arco é fundamental para a resolução de CSPs, e várias técnicas, como o algoritmo AC-3, são usadas para alcançar essa consistência.

## Algoritmos

Quando existem muitas variáveis e restrições em um CSP pode tornar o problema desafiado. Para enfrentar desafios assim, existem várias técnicas de resolução, incluindo:

* **Consistência de Arco:** Tarta de fazer a verificação da consistência das restrições em relação a um par de variáveis, a fim de reduzir o domínio das variáveis para melhorar a eficiência da busca.

* **Busca em Árvore:** Uma técnica clássica de exploração para diferentes distribuição de valores para as variáveis, visando uma solução que satisfaça todas as restrições.

* **Algoritmos de Busca Local:** Usados quando o objetivo é encontrar uma solução para otimizar algum critério. O espaço de soluções é explorado em busca de soluções melhores.

* **Algoritmos de Propagação de Restrições:** Usados comumente para diminuir os domínios das variáveis com base nas restrições impostas, fazendo a busca muito mais eficiente.

## Estruturas de Problemas
A escolha da estrutura de representação de um problema CSP vai depender da natureza do problema e das restrições que estão envolvidas. Cada uma dessas estruturas tem seus próprios desafios e características associados à resolução. A seleção da abordagem certa para um problema específico é primordial para encontrar uma solução de forma eficiente.

Problemas com estrutura de árvore são geralmente mais simples de resolver comparad as demais. Uma sequência de variáveis se dispõe de tal forma que cada variável, excluindo a primeira, tem exatamente uma restrição a outra variável precedente na sequência. A solução para tais problemas pode ser obtida em tempo linear, relacionando-se diretamente ao número de variáveis. Soluções para problemas com essa estrutura podem ser obtidas em tempo linear em relação ao número de variáveis.

Exemplo:
	
```
    A
   / \
  B   C
 / \ / \
D   E   F
```

6.2. Estrutura de Grafo

Problemas com uma estrutura de grafo mais complexa exigem estratégias de resolução mais elaboradas. A complexidade desses problemas está relacionada à topologia do grafo e à natureza das restrições. As variáveis podem ter múltiplas restrições entre si, o que, por vezes, exige algoritmos de busca como Backtracking ou Local Search.

Exemplo:
	
```
    A - B
   / \ / \
  C - D - E
   \ / \ /
    F - G
```

6.3. Grafo Bipartido

Nessa estrutura, as variáveis podem ser divididas em dois conjuntos com todas as restrições sendo entre variáveis de conjuntos diferentes. Dessa forma é criado uma separação clara entre os conjuntos, podendo simplificar a resolução, uma vez que as restrições ocorrem apenas entre grupos de variáveis distintos.

Exemplo:
	
```
  A - 1
  B - 2
  C - 3
```

6.4. Grafo em Grade

Essa estrutura é comum em muitos problemas práticos. Por exemplo, no problema Sudoku, as células do tabuleiro formam uma grade, e as restrições são entre células que estão na mesma linha, na mesma coluna, ou na mesma região de 3x3.

Exemplo:
	
```
  A - B - C
  |   |   |
  D - E - F
  |   |   |
  G - H - I
```

## Discussões


```
import math
import random

# Função de exemplo: podemos substituí-la pela função que você deseja otimizar.
def goal_function(x):
    return math.sin(x) + 0.1 * x

def simulated_annealing(start_solution, goal_function, max_iterations, initial_temperature, cooling_rate):
    current_solution = start_solution
    current_cost = goal_function(current_solution)

    best_solution = current_solution
    best_cost = current_cost

    for i in range(max_iterations):
        # Gerar uma solução vizinha aleatória.
        neighbor_solution = current_solution + random.uniform(-0.5, 0.5)
        neighbor_cost = goal_function(neighbor_solution)

        # Calcular a diferença nas funções de custo.
        cost_diff = neighbor_cost - current_cost

        # Aceitar a solução vizinha se for melhor ou com uma probabilidade baseada na diferença de custo e temperatura.
        if cost_diff < 0 or random.random() < math.exp(-cost_diff / initial_temperature):
            current_solution = neighbor_solution
            current_cost = neighbor_cost

        # Atualizar a melhor solução encontrada até agora.
        if current_cost < best_cost:
            best_solution = current_solution
            best_cost = current_cost

        # Reduzir a temperatura com a taxa de resfriamento.
        initial_temperature *= cooling_rate

    return best_solution, best_cost

# Parâmetros do Simulated Annealing
initial_temperature = 1.0
max_iterations = 1000
cooling_rate = 0.95
start_solution = 5.0

# Executar o Simulated Annealing
best_solution, best_cost = simulated_annealing(start_solution, goal_function, max_iterations, initial_temperature, cooling_rate)

print("Melhor solução:", best_solution)
print("Melhor custo:", best_cost)

```

Explixando um pouco sobre o código

```
def objective_function(x):
    return math.sin(x) + 0.1 * x
```

Função que representa o objetivo que se deseja otimizar

Função simulated_annealing:
Implementação do algoritmo Simulated Annealing:

* initial_solution: A solução inicial do algoritmo.
* objective_function: A função objetivo a ser otimizada.
* max_iterations: O número máximo de iterações do algoritmo.
* initial_temperature: A temperatura inicial do algoritmo.
* cooling_rate: A taxa de resfriamento, que reduz a temperatura após cada iteração.

O algoritmo inicia com a solução inicial, calcula o custo associado usando a função objetivo e em seguida, tenta encontrar soluções vizinhas aleatórias. Se uma solução vizinha for melhor (com uma probabilidade baseada na diferença de custo e temperatura), ela é aceita como a nova solução atual (melhor). Isso permite que o algoritmo aceite soluções piores inicialmente e, com o tempo, explore mais e encontre o mínimo global.

## Projetos e problemas
Neste exemplo vou aplicar um algoritmo de planejamento de tarefas usando conceitos do CSP.

```
# Definindo as tarefas e recursos
tasks = ["Tarefa1", "Tarefa2", "Tarefa3"]
resources = ["Recurso1", "Recurso2", "Recurso3"]

# Criando um dicionário para armazenar as atribuições de tarefas a recursos
assignments = {}

# Definindo as restrições
def valid_assignment(task, resource):
    # Adicionando suas próprias restrições aqui, se necessário.
    # Por exemplo, você pode verificar se o recurso já foi alocado a outra tarefa.
    return True

# Algoritmo de CSP simples
def csp_solve(tasks, resources, assignments):
    if not tasks:
        # Todas as tarefas foram alocadas com sucesso.
        return True

    task = tasks[0]
    for resource in resources:
        if valid_assignment(task, resource):
            assignments[task] = resource
            if csp_solve(tasks[1:], resources, assignments):
                return True
            del assignments[task]  # Backtracking

    return False

# Execute o algoritmo CSP
if csp_solve(tasks, resources, assignments):
    print("Atribuições bem-sucedidas:")
    for task, resource in assignments.items():
        print(f"{task} -> {resource}")
else:
    print("Nenhuma atribuição válida encontrada.")
```

Armazeno as tarefas e recursos como listas de strings.

Uso um dicionário **assignments** para acompanhar as atribuições de tarefas a recursos.

A função **valid_assignment** verifica se uma atribuição de tarefa a recurso é válida.

O algoritmo de CSP csp_solve é implementado de forma recursiva. Ele tenta alocar cada tarefa a um recurso disponível, verificando as restrições. Se uma solução é encontrada, o algoritmo imprime as atribuições bem-sucedidas. Caso contrário, ele volta atrás e tenta outras combinações.

## Referências
* NORVIG, P.; RUSSELL, S., Inteligência artificial: Tradução da 3a Edição, [s.l.]: Elsevier Brasil, 2014.
* ROSSI, F., VAN BEEK, P., & WALSH, T. (2006). Handbook of Constraint Programming (Foundations of Artificial Intelligence). Elsevier Science Inc.
* DECHTER, Rina. Constraint Processing. Morgan Kaufmann, 2003.
* KUMAR, V. Algorithms for Constraint-Satisfaction Problems: A Survey. AI Magazine, [s.l.], v. 13, n. 1, p.32, 1992.