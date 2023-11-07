---
title: Portifolio 2 - IA
date: 2023-10-31 19:27:00 -0400
categories: [portfolio - inteligencia artificial, portifolio 1]
tags: [ai, portfolios, algoritmos de busca]
---

## Agente de soluções de problema
Na ciência da Computação, um Agente de Resolução de Problemas é um agente inteligente projetado para resolver problemas específicos de forma autônoma ou semi-autônoma. Esses problemas abrangem diversos tipos de complexidade tal como sistemas de diagnóstico médico, sistemas de recomendação em plataformas de streaming como a Netflix, entre outros.

Para exemplificar, usarei  o problema do quebra-cabeça de 8 peças. Nesse jogo existem uma grade 3x3 onde as peças estão numeradas e existe um espaço em branco. O objetivo é movimentar as peças para que o quebra cabeça esteja montado. 

```
import copy
from collections import deque

class Eight_Puzzle:
    def __init__(self, state):
        self.state = state
        self.final_state = [[1, 2, 3], [4, 5, 6], [7, 8, 0]]

    def print_solution(self):
        for row in self.state:
            print(row)
        print()

    def find_blank(self):
        for i, row in enumerate(self.state):
            for j, tile in enumerate(row):
                if tile == 0:
                    return i, j

    def is_finished(self):
        return self.state == self.final_state

    def actions(self):
        i, j = self.find_blank()
        possible_actions = []

        if i > 0:
            possible_actions.append('up')
        if i < 2:
            possible_actions.append('down')
        if j > 0:
            possible_actions.append('left')
        if j < 2:
            possible_actions.append('right')

        return possible_actions

    def result(self, action):
        i, j = self.find_blank()
        new_state = copy.deepcopy(self.state)

        if action == 'up':
            new_state[i][j], new_state[i - 1][j] = new_state[i - 1][j], new_state[i][j]
        elif action == 'down':
            new_state[i][j], new_state[i + 1][j] = new_state[i + 1][j], new_state[i][j]
        elif action == 'left':
            new_state[i][j], new_state[i][j - 1] = new_state[i][j - 1], new_state[i][j]
        elif action == 'right':
            new_state[i][j], new_state[i][j + 1] = new_state[i][j + 1], new_state[i][j]

        return EightPuzzle(new_state)

def solve_puzzle(initial_state):
    start_node = EightPuzzle(initial_state)

    if start_node.is_finished():
        return [initial_state]

    node_list = deque([start_node])
    closed_set = set()

    while node_list:
        actual_node = node_list.popleft()
        closed_set.add(tuple(map(tuple, actual_node.state)))

        for action in actual_node.actions():
            child_node = actual_node.result(action)
            child_state_tuple = tuple(map(tuple, child_node.state))

            if child_state_tuple not in closed_set:
                node_list.append(child_node)

                if child_node.is_finished():
                    path = [child_node.state]
                    while actual_node.state != initial_state:
                        path.insert(0, actual_node.state)
                        actual_node = actual_node.parent
                    path.insert(0, initial_state)
                    return path

# Exemplo de uso:
initial_state = [[1, 3, 2], [4, 0, 5], [8, 7, 6]]
solution_path = solve_puzzle(initial_state)

for state in solution_path:
    EightPuzzle(state).print_solution()

```
1. Primeiramente serão importadas as bibliotecas que irei utilizar: **copy** será usadaa para criar cópias dos estados do quebra-cabeça e **deque** da biblioteca collections para importar uma fila (FIFO) já pronta.

2. Foi criada a classe **EightPuzzle**, usada para representar o quebra-cabeça em si. Essa classe possui os seguintes métodos:

    * __init__(self, state): Construtor da classe, será quem irá inicializar o objeto com o estado inicial.

    * print_solution(self): Irá exibir o estado atual do quebra-cabeça.

    * find_blank(self): Usado para encontrar onde está o espaço em branco (representado por 0).

    * actions(self): Retorna uma lista de possíveis ações a serem tomadas a partir do estado atual (podendo mover para cima, baixo, esquerda ou direita).

    * is_finished(self): Verifica se o estado atual é o estado desejado (o quebra cabeça já está resolvido).

    * result(self, action): Retorna o novo objeto EightPuzzle após uma ação ser tomada.

3. A função **solve_puzzle(initial_state)** é quem irá resolver o quebra-cabeça a partir do estado inicial passado. O algoritmo utilizado para resolver o quebra-cabeça é a busca em largura (BFS).

    * É criado o primeiro nó com o estado inicial fornecido.

    * É verificamos se o nó inicial já é o estado que reolve o quebra-cabeça. Se for, retornamos uma lista contendo apenas o estado inicial, indicando que o quebra-cabeça já foi resolvido.

    * Uma deque (fila) é incializada chamada **node_list** com o nó inicial

    * Inicializo um conjunto chamado **closed_set** para manter o controle dos estados que já foram explorados.

    * Inicio um loop while que irá executar até que fila **node_list** esteja vazia, representando que não há mais estados para explorar.

    * Removo o primeiro nó da fila **node_list**, que é o nó atual que está sendo explorado.

    * Adiciono o estado do nó atual explorado no **closed_set**.

    * Itero sobre as ações possíveis a partir do nó atual.

    * Para cada ação possível, gero um novo nó filho aplicando essa ação ao nó atual.

    * Crio uma tupla **child_state_tuple** para representar o estado do nó filho. A tupĺa será usada usado para verificar se o estado do nó filho já está no conjunto **closed_set**.

    * Verifico se o estado do nó filho não está no **closed_set**. Se não estiver, o adiciono à **node_list** para explorá-lo posteriormente.
    
    * Verifico se o nó filho é o estado final. Se for, a solução foi encontrada.

    * Inicializo uma lista **path** com o estado do nó filho, que será a solução.

    * Começo a retroceder a partir do nó filho até o nó inicial, adicionando os estados à lista **path**.

    * Por fim, a lista path completa será retornada, que é a sequência de estados que leva da configuração inicial à configuração final.


## Problemas de malha aberta e de malha fechada
* **Malha aberta:** Esses tipos de problemas são caracterizados por situações em que a solução não dependem de ações do agente de soluções de problemas em relação ao ambiente. Isso significa que independentemente das suas escolhas ou ações, a solução continuará a mesma. Um exemplo clássico desse tipo de problema é o desafio do caixeiro-viajante. Nesse problema clássico o objetivo é determinar o caminho mais curto para visitar um conjunto de cidades e por fim, retornar a cidade de origem. Para solucionar o desafio é necessário desenvolver uma solução ótima que minimize a distância total percorrida, levando em consideração todas as cidades. No entanto, devido à quantidade de combinações possíveis, encontrar a solução mais eficiente pode ser computacionalmente complicado, já que os recursos são limitados, sendo que várias abordagens, como algoritmos de otimização, são empregadas para resolver. Esse tipo de problema tem aplicações em logística, planejamento de rotas, distribuição de recursos e otimização de trajetos em diversas áreas, tornando-o um desafio fundamental em ciência da computação e pesquisa operacional.

```
import itertools

def distance(a, b):
    return ((a[0] - b[0]) ** 2 + (a[1] - b[1]) ** 2) ** 0.5

def total_distance(path, cities):
    return sum(distance(cities[i], cities[i + 1]) for i in range(len(path) - 1))

cities = [(1, 2), (2, 4), (4, 4), (4, 1)]

smallest_distance = float('inf')
smallest_path = None

for path in itertools.permutations(cities):
    path_distance = total_distance(path, cities)
    if path_distance < smallest_distance:
        smallest_distance = path_distance
        smallest_path = path

print(smallest_path)
```
Neste exemplo em Python, o código resolve o problema do caixeiro-viajante encontrando a rota mais curta para um conjunto de cidades usando apenas algumas linhas de código.

* **Malha fechada:** A solução dos problemas de malha fechada, diferente dos problemas de malha aberta, dependem das ações do agente e das condições do ambiente, tendo como resultado uma interação contínua e feedback periódico entre esses elementos. Nos problemas desse tipo, as decisões tomadas pelo agente não se baseiam apenas em informações imediatas, mas também em considerações de longo prazo, uma vez que as ações podem influenciar o resultado final. Um exemplo clássico desse tipo de problema é o jogo da velha. A solução final do jogo depende não apenas das ações individuais de cada jogador, mas também das estratégias e movimentos do adversário. O jogo da velha ilustra como a tomada de decisões está diretamente ligada ao comportamento do oponente, tornando-o um desafio que vai além de simples cálculos ou regras predefinidas. Essa característica de interdependência torna os problemas de malha fechada uma área de estudo fundamental em ciência da computação, teoria dos jogos e inteligência artificial.

```
def check_winner(board):
    # Verifica linhas e colunas
    for i in range(3):
        if board[i][0] == board[i][1] == board[i][2] and board[i][0] != 0:
            return board[i][0]
        if board[0][i] == board[1][i] == board[2][i] and board[0][i] != 0

    # Verifica diagonais
    if board[0][0] == board[1][1] == board[2][2] and board[0][0] != 0:
        return board[0][0]
    if board[0][2] == board[1][1] == board[2][0] and board[0][2] != 0

    return None

def result(board):
    winner = check_winner(board)
    if winner is not None:
        return winner
    return "Velha" if all(cell != 0 for row in board for cell in row) else None

board = [[1, 2, 0], [2, 1, 0], [2, 1, 1]]
print(result(board))

```

Neste exemplo em Python, o código verifica o resultado do jogo da velha em um tabuleiro 3x3 usando apenas algumas linhas de código. A solução deste problema envolve a interação entre os jogadores, com feedback constante do estado do tabuleiro, que é afetado pelas ações de ambos os agentes.

## Algoritmos de busca

Os algoritmos de busca cega, também conhecidos como busca não-informada, não utilizam de informações específicas do problema para tomar decisões. Como exemplo de algoritmos temos:

### Busca Cega
* Uniform Cost Search (UCS)
O UCS explora os nós com menor custo acumulado primeiro. Ele é útil para encontrar soluções de menor custo em problemas onde o custo de cada ação é relevante.

```
import heapq

def ucs(problem):
    border = [(0, problem.initial_state())]
    explored = set()

    while border:
        cost, node = heapq.heappop(border)

        if problem.is_finished(node):
            return node

        explored.add(node)

        for child, action_cost in problem.successors_with_costs(node):
            new_cost = cost + action_cost

            if child not in explored:
                # Verifique se o nó não está na fila com um custo menor
                child_in_border = False
                for i, (old_cost, old_node) in enumerate(border):
                    if old_node == child:
                        if old_cost > new_cost:
                            border[i] = (new_cost, child)
                            heapq.heapify(border)
                        child_in_border = True
                        break

                if not child_in_border:
                    heapq.heappush(border, (new_cost, child))

    return None

```

Ao escolher um algoritmo de busca cega, é importante considerar os requisitos e as características específicas do problema em questão. Cada algoritmo tem suas vantagens e desvantagens, e a seleção do método de busca apropriado pode ter um impacto significativo no desempenho e na qualidade da solução.

### Busca informada

A busca informada utiliza informações específicas do problema para guiar a busca. As funções heurísticas são usadas para estimar o custo para alcançar o objetivo. Algoritmos comuns de busca informada incluem A* e Busca Gulosa.

* A*: O algoritmo A* é um exemplo popular de busca informada. Ele combina os custos reais do caminho com os custos estimados pela função heurística para determinar a próxima ação a ser tomada. O A* é uma generalização da busca de custo uniforme e é ótimo quando a função heurística é admissível e consistente.

```
import heapq

def a_star_search(problem, heuristic_function):
    def f_cost(g_cost, state):
        return g_cost + heuristic_function(state)

    border = [(f_cost(0, problem.initial_state()), 0, problem.initial_state())]
    explored = set()
    
    while border:
        _, g_cost, node = heapq.heappop(border)
        
        if problem.is_finished(node):
            return node
        
        explored.add(node)
        
        for child, action_cost in problem.successors_with_costs(node):
            new_g_cost = g_cost + action_cost

            # Verifica se o nó não está na fila com um custo menor
            child_in_border = False
            for i, (old_f_cost, old_g_cost, old_node) in enumerate(border):
                if old_node == child:
                    if new_g_cost < old_g_cost:
                        border[i] = (f_cost(new_g_cost, child), new_g_cost, child)
                        heapq.heapify(border)
                    child_in_border = True
                    break

            if not child_in_border and child not in explored:
                heapq.heappush(border, (f_cost(new_g_cost, child), new_g_cost, child))

    return None

```

De maneira geral, a busca informada utiliza informações específicas do problema para guiar a busca, enquanto a busca cega não. Algoritmos como A* e Busca Gulosa são exemplos de busca informada que usam funções heurísticas para estimar o custo do estado atual até o objetivo. A escolha do algoritmo de busca informada apropriado depende das características e requisitos do problema específico, assim como no caso da busca cega. Analisar cuidadosamente o problema e entender as propriedades de cada algoritmo são essenciais antes de tomar uma decisão.

## Funções heurísticas

Funções heurísticas desempenham um papel de grande importância na previsão do custo do estado atual em direção ao objetivo. Tomando como exemplo o problema do 8-puzzle, duas heurísticas amplamente adotadas incluem a contagem de peças que estão fora da posição e a soma das distâncias das peças em relação à sua posição final no tabuleiro.

```
def misplaced_tiles(state, goal):
    """
    Calcula o número de peças mal posicionadas entre o estado atual e o estado objetivo.
    """
    return sum(s != g for s, g in zip(state, goal) if s != 0)

def manhattan_distance(state, goal, size):
    """
    Calcula a distância de Manhattan entre o estado atual e o estado objetivo.
    """
    distance = 0
    for s, g in zip(state, goal):
        if s != 0 and s != g:
            # Calcula a distância em termos de linhas e colunas
            distance += abs(s // size - g // size) + abs(s % size - g % size)
    return distance

```

O uso de uma função heurística pode ter um grande impacto na otimização da eficiência de algoritmos de busca informada, como o A*. Isso é bastante perceptível em ambientes complexos, nos quais o número de estados possíveis é bastante grande, permitindo uma busca mais focada e rápida em direção à solução desejada.

## Busca em ambientes complexos 
Ambientes complexos apresentam vários desafios, como informações incompletas e restrições (tempo e espaço), além de dinâmicas em constante evolução. Para superar isso, é necessário adotar abordagens adaptativas, planejamento em tempo real e algoritmos desenvolvidos especialmente para ambientes em constante mudança.

As abordagens adaptativas, como o Q-Learning, permitem que os algoritmos de busca aprendam e ajustem suas estratégias com base no feedback obtido do ambiente. O planejamento em tempo real, exemplificado pelo Real-Time A* (RTA), concentra-se em buscar soluções satisfatórias dentro de prazos definidos, tomando decisões com base em informações locais disponíveis.

Além disso, existem algoritmos como o D* Lite, que foram concebidos para lidar com ambientes dinâmicos, atualizando continuamente o caminho ótimo à medida que o ambiente se modifica e novas informações são adquiridas.

Ao enfrentar ambientes complexos, é fundamental compreender os desafios específicos que eles apresentam e escolher os algoritmos de busca mais adequados para garantir soluções eficazes e de alta qualidade. Essas estratégias desempenham um papel crucial na superação das incertezas e restrições inerentes a tais ambientes desafiadores.

## Algorítmos genéticos

Os algoritmos genéticos (AGs) são técnicas de busca inspiradas na seleção natural e evolução, que fazem parte de um campo de estudo conhecido como computação evolutiva. Eles possuem a capacidade de lidar com uma grande quantidade de problemas complexos, se destacando na resolução de problemas de otimização, busca global e até mesmo na geração de soluções criativas.

Dentre suas operação fundamentais, existe a criação de uma população de soluções candidatas, representadas por cromossomos. Esses cromossomos passam por um processo de avaliação, onde suas aptidões são calculadas com base em uma função de adaptação (fitness). Em seguida, os cromossomos mais aptos são selecionados para formar a próxima geração por meio de operadores genéticos, como cruzamento (crossover) e mutação.

Uma das principais vantagens dos AGs é a capacidade de explorar uma grande de soluções em paralelo, permitindo a descoberta de soluções ótimas ou subótimas em espaços de busca de grande dimensão. Além disso, sua adaptabilidade e habilidade de escapar de mínimos locais tornam-nos uma escolha valiosa em problemas que envolvem múltiplos ótimos locais ou cenários complexos em constante evolução.

Embora os AGs ofereçam muitos benefícios, a eficácia de sua aplicação depende da escolha adequada de parâmetros, representação de soluções e função de adaptação, tornando essencial a compreensão profunda do problema em questão. Portanto, os algoritmos genéticos são uma ferramenta poderosa para a resolução de uma ampla variedade de problemas complexos em ciência, engenharia, economia e muito mais.

```
class GeneticSolution:
    def __init__(self, population, fit_function):
        self.population = population
        self.fit_function = fit_function

    def evolve(self):
        # implementação do algoritmo

```
Algoritmos genéticos diferenciam dos algoritmos tradicionais de otimização em quatro aspectos principais:

* Ao invés de apoiar nos parâmetros da otimização em si e não em codificação do conjunto das possíveis soluções.
* A forma que os resultados são apresentados é seguindo uma população de soluções e não como uma solução única.
* Não precisam de nenhum conhecimento derivado do problema, apenas uma forma de avaliação do resultado.
* Usam transições probabilísticas e não regras determinísticas.

## Discussões

Exemplo de algoritmo de busca não discutido em sala

### Tabu search 

Tabu Search é um algoritmo de otimização que utiliza uma abordagem heurística para encontrar soluções de alta qualdiade, especialmente quando a busca em espaço de soluções é complexa. O algoritmo busca explorar o espaço de soluções de maneira mais eficiente do que métodos puramente aleatórios, evitando revisitar soluções previamente exploradas (daí o termo "tabu").

A partir de uma resposta inicial, o processo de busca, acada iteração, avançar em direção a uma solução melhor na vizinhança, evitando movimentos repetidos que podem levar a soluções previamente exploradas. Esses movimentos são registrados em uma lista conhecida como "lista tabu". Essa lista permanece na memória, retendo informações sobre soluções já visitadas (tabu) por um período específico ou um determinado número de iterações (prazo tabu). O resultado final desejado é a identificação de um ótimo global ou uma solução próxima do ótimo global.

## Referências

- NORVIG, P.; RUSSELL, S., Inteligência artificial: Tradução da 3a Edição, [s.l.]: Elsevier Brasil, 2014.

- Engel, P. M. - Busca de Informação e Otimização. Universidade Federal do Rio Grande do  Sul. Porto Alegre, 2004. Disponível em: https://www.inf.ufrgs.br/~engel/data/media/file/inf01048/busca2.pdf.

- https://www.dataex.com.br/tipos-de-inteligencia-artificial/ 

- Stuart Russell and Peter Norvig, Inteligência Artificial, Terceira edição, Elsevier, Prentice Hall, 2010 

