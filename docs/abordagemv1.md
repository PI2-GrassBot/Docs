# Abordagem V1

## Visão Geral
Esta documentação descreve a abordagem V1 do projeto GrassBot, um simulador de cortador de grama autônomo. O simulador foi desenvolvido em Python e utiliza a biblioteca Pygame para criar uma interface gráfica interativa. O GrassBot é capaz de cortar grama de forma autônoma, evitando obstáculos.


![Abordagem V1](https://github.com/PI2-GrassBot/Docs/blob/main/assets/v1.gif?raw=true)
---

## Arquitetura

### API (`api`)
A api é responsável por fornecer uma servidor web para controle do cortador de grama. Tendo os seguintes endpoints que dispõe atualização em tempo real do estado do cortador. Tais como:
- Ligar/Desligar
- Aumentar/Diminuir Velocidade
- Gerar Mapa Aleatório

A api recebe as requisições e atualiza o arquivo de configuração JSON, que é lido pelo simulador para atualizar o estado do cortador.

---


### Núcleo (`Core`)
O Core contém os componentes centrais do projeto, responsáveis por implementar a lógica de busca em grafos e manipulação de nós. Essas funcionalidades são essenciais para a navegação e tomada de decisão no ambiente da simulação.

O Core realiza leituras sazonais do json de configuração, atualizando o estado do cortador.

---

### **graph_search.py**
Lógica de busca em profundidade (DFS - Depth-First Search) no ambiente da simulação. A DFS é usada para explorar os caminhos possíveis no labirinto ou ambiente de forma sistemática.

#### Principais Funções

#### `dfs(maze, start, gui, coords: Coordinates)`
Executa a busca em profundidade no ambiente definido pela matriz `maze`.

**Parâmetros**:
- `maze`: Uma matriz 2D representando o ambiente, onde valores determinam se uma célula é acessível (0) ou não.
- `start`: A posição inicial (tupla `(x, y)`) para começar a busca.
- `gui`: Interface gráfica (GUI) usada para exibir o progresso da busca.
- `coords: Coordinates`: Objeto que armazena o estado atual da busca, como o nó corrente e listas abertas e fechadas.

**Descrição do Fluxo**:
1. Cria um nó inicial a partir da posição de início.
2. Utiliza duas listas:
   - `open_list`: Contém os nós que serão explorados.
   - `closed_list`: Contém os nós já visitados.
3. Itera enquanto houver nós na `open_list`:
   - Atualiza o nó atual.
   - Verifica vizinhos usando `get_sensors`.
   - Filtra os vizinhos intransitáveis ou já visitados.
   - Adiciona novos vizinhos à `open_list`.
4. Renderiza o progresso na interface gráfica (`gui.sprite(True)`).

**Conexões Importantes**:
- Usa a função `get_sensors` do módulo `sensors.get_sensors` para obter vizinhos do nó atual.
- Utiliza a classe `Node` para manipular nós no grafo.

---

### **node.py**
Define a classe `Node`, que é usada para representar nós no grafo durante a execução do algoritmo de busca.

#### Classe `Node`
Representa um nó no grafo ou na matriz.

**Atributos**:

- `parent`: O nó pai (do tipo `Node`) usado para rastrear o caminho percorrido.
- `position`: A posição do nó, representada como uma tupla `(x, y)`.

**Métodos**:

- `__init__(self, parent: Node, position: Tuple[int, int])`: Inicializa o nó com um pai e uma posição.
- `__eq__(self, other: Node)`: Compara dois nós pela posição, retornando `True` se forem iguais.

**Importante para**:

- Rastrear o caminho percorrido durante a busca.
- Comparar nós e evitar redundâncias.

---
### Simulation (`Simulation`)
O módulo de simulação contém os arquivos responsáveis por criar a interface gráfica do simulador. Ele utiliza a biblioteca Pygame para renderizar o ambiente e exibir o progresso da busca em tempo real.

### **drawer.py**

### **Classe `Coordinates`**
A classe `Coordinates` gerencia os dados relacionados ao labirinto, como posição inicial, obstáculos e listas utilizadas em algoritmos de busca.

#### **Atributos**
- `start`: Nó inicial (`Node`).
- `walls`: Lista de coordenadas que representam paredes no labirinto.
- `maze`: Representação matricial do labirinto.
- `open_list`: Lista de nós a serem processados.
- `closed_list`: Lista de nós já processados.
- `current_node`: Nó atualmente processado.
- `start_point`: Coordenadas do ponto inicial no formato `(x, y)`.

#### **Métodos**
1. **`__init__(self)`**: Inicializa os atributos chamando `clear_all_field()`.
2. **`clear_all_field(self)`**: Reseta todos os atributos para seus valores padrão.
3. **`clear_cut(self)`**: Limpa o labirinto, a lista aberta e a lista fechada, mantendo as paredes.
4. **`largest_distance(self)`**: Calcula o maior índice entre as paredes e o ponto inicial.
5. **`create_maze(self, gui)`**: Cria a matriz do labirinto com base no tamanho da grid e nas paredes definidas.
6. **`generate_random_obstacles(self, gui)`**: Gera obstáculos aleatórios na grid com base em uma probabilidade.

### **gui.py**

### **Classe `Gui`**
A classe `Gui` gerencia a interface gráfica do sistema utilizando o Pygame. Ela também controla os eventos e a lógica do jogo.

#### **Atributos**
- `grid_size`: Tamanho da grid.
- `box_width`: Largura de cada célula no grid.
- `coords`: Instância da classe `Coordinates`.
- `placing_blocks`: Indica se blocos (paredes) estão sendo colocados.
- `removing_blocks`: Indica se blocos estão sendo removidos.
- `cut_speed`: Velocidade de execução do algoritmo.
- `cut_height`: Altura de corte utilizada pelo sistema.
- `pause`: Indica se o jogo está pausado.
- `status`: String representando o estado atual do jogo.
- `running`: Indica se o algoritmo está em execução.

#### **Métodos**
1. **`__init__(self, coords)`**: Inicializa a interface gráfica e os atributos.
2. **`sprite(self, is_running=False)`**: Loop principal que controla o estado do jogo.
3. **`read_event_by_api(self)`**: Lê eventos de um arquivo JSON para integração com uma API externa.
4. **`power(self, running)`**: Controla o estado de execução com base em comandos da API.
5. **`event_handle(self, running)`**: Gerencia eventos do teclado e mouse.
6. **`redraw(self)`**: Atualiza a interface gráfica.
7. **`draw_grid(self)`**: Desenha a grade do labirinto.
8. **`draw_points(self)`**: Desenha os pontos relevantes, como paredes, nós visitados e ponto inicial.
9. **`draw_box(self, box, colour)`**: Desenha uma célula específica do grid.
10. **`get_box_coords(self) -> Tuple[int, int]`**: Retorna as coordenadas da célula sob o mouse.
11. **`place_start(self)`**: Define o ponto inicial com base na posição do mouse.
12. **`place_wall(self)`**: Adiciona uma parede na posição atual do mouse.
13. **`remove(self)`**: Remove uma parede ou ponto inicial da posição atual do mouse.
14. **`run_algorithm(self)`**: Executa o algoritmo DFS com base no estado atual do labirinto.
15. **`panel_status(self)`**: Atualiza o painel lateral com informações do jogo.


### **Sensores** (`Sensors`)

O foco de **`Sensors`** é **identificar os vizinhos diretos de um nó em uma grade ou matriz**, considerando os movimentos básicos em quatro direções: **cima**, **baixo**, **esquerda** e **direita**. Esses vizinhos representam os nós adjacentes que podem ser acessados a partir da posição atual.

### **get_sensors.py**
A função é utilizada no algoritmo de busca em grafos utilizado para mapear o ambiente e calcular a rota, neste caso o **DFS (Depth-First Search)** , para explorar caminhos ou estados vizinhos em problemas de navegação, labirintos ou grade de obstáculos.


### Interface (`Ui`)
A interface do usuário é responsável por fornecer uma página web com os controles do cortador de grama. Ela permite ligar/desligar o cortador, ajustar a velocidade e gerar um mapa aleatório.
