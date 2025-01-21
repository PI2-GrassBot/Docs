# Abordagem V2

## Visão Geral
Esta documentação descreve a abordagem V2 do projeto GrassBot, um simulador de cortador de grama autônomo. O simulador foi desenvolvido em Python e utiliza a biblioteca Pygame para criar uma interface gráfica interativa. O GrassBot é capaz de cortar grama de forma autônoma, evitando obstáculos e otimizando rotas.


![Abordagem V2](https://raw.githubusercontent.com/PI2-GrassBot/Docs/f6502e73a82b199e4432b45a43b3f6cfd3267995/assets/v2.gif)
---

## Arquitetura

### Núcleo (`Core`)
O núcleo do projeto gerencia os estados principais do cortador, como posição, velocidade e estado de energia.

#### Exemplo de Código:
```python
class Core:
    def __init__(self, x: int, y: int):
        self.x = x
        self.y = y
        self.atualiza_comando()
        self.posicao_atual = (self.x, self.y)

    def ligar(self):
        self.power = True

    def desligar(self):
        self.power = False

    def atualiza_comando(self):
        with open('src/api/data/data.json') as f:
            data = json.load(f)

        self.power = data['ligado']
        self.velocidade = data['velocidade']
        self.altura = data['altura_corte']
        return self.power, self.velocidade, self.altura
```

O método `atualiza_comando` sincroniza o estado do cortador com o arquivo de configuração JSON, que recebe os valores de acordo com a interface de usuário web.

### Sensores
Os sensores simulados detectam obstáculos, grama e zonas de concreto, permitindo ao cortador recalcular rotas de forma autônoma.

#### Exemplo de Código:
```python
class MockSensors:
    def get_data(self, x, y):
        return [
            {"posicao": (x + 30, y), "direcao": "RIGHT", "tipo": "Grama"},
            {"posicao": (x, y + 30), "direcao": "DOWN", "tipo": "Concreto"}
        ]
```
Os sensores retornam dados sobre o ambiente ao redor, que são usados no planejamento de movimento.

### Simulação
Usa o Pygame para criar uma interface gráfica interativa que representa o campo de grama, obstáculos e o cortador.

#### Exemplo de Código:
```python
class Cortador:
    def mover(self):
        if self.direcao == "UP":
            self.core.y -= TAMANHO_CORTADOR
        elif self.direcao == "DOWN":
            self.core.y += TAMANHO_CORTADOR
        elif self.direcao == "LEFT":
            self.core.x -= TAMANHO_CORTADOR
        elif self.direcao == "RIGHT":
            self.core.x += TAMANHO_CORTADOR

        self.core.x = max(0, min(self.core.x, LARGURA - TAMANHO_CORTADOR))
        self.core.y = max(0, min(self.core.y, ALTURA - TAMANHO_CORTADOR))
```
O cortador se move no ambiente, ajustando sua posição conforme os limites do mapa e evitando áreas intransitáveis.

### Interface de Usuário
Exibe informações em tempo real, como a posição do cortador e sua velocidade.

#### Exemplo de Código:
```python
class Painel:
    def desenhar(self):
        texto_posicao = fonte.render(f"Posição: ({self.cortador.core.x // TAMANHO_CORTADOR}, {self.cortador.core.y // TAMANHO_CORTADOR})", True, COR_TEXTO)
        tela.blit(texto_posicao, (LARGURA + 10, 310))
```
O painel fornece feedback visual detalhado durante a execução do simulador.

---

## Algoritmo de Autonomia
O cortador utiliza um algoritmo de navegação para explorar a área de forma eficiente.

### Passos Principais:
1. **Coleta de Dados**
   Os sensores identificam o tipo de terreno e a presença de obstáculos.

   ```python
   dados_sensores = self.sensores.get_data(self.core.x, self.core.y)
   ```

2. **Recalculo de Rotas**
   Quando encontra um obstáculo, o cortador recalcula a rota com base nos dados dos sensores.

   ```python
   def recaucular_rota(self):
       for dado in dados_sensores:
           if dado["tipo"] == "Grama" and not dado["posicao"] in self.visitados:
               return dado["direcao"]
   ```

3. **Busca em Largura (BFS)**
   Caso todas as direções imediatas estejam bloqueadas, o algoritmo utiliza BFS para encontrar a célula de grama mais próxima.

   ```python
   def buscar_grama_mais_proxima(self):
       fila = [(self.core.x, self.core.y)]
       while fila:
           x, y = fila.pop(0)
           if not grama_cortada[y // TAMANHO_CORTADOR][x // TAMANHO_CORTADOR]:
               return (x, y)
   ```

---

## Fluxo de Execução
1. O simulador é iniciado pelo script principal (`main.py`).
2. O cortador começa na posição inicial, verificando a grama ao redor e movendo-se conforme as condições do ambiente.
3. O painel exibe informações em tempo real.
4. O simulador encerra automaticamente quando toda a grama é cortada.

---

## Possíveis Extensões
- **Mapas Personalizáveis:** Permitir que os usuários configurem mapas com obstáculos e zonas especiais.
- **Integração com IA:** Incorporar aprendizado de máquina para otimizar o padrão de corte.
- **Melhorias nos Sensores:** Simular condições ambientais, como chuva ou iluminação variável.

---

Este projeto fornece uma base para simulações de dispositivos autônomos e pode ser expandido para incluir funcionalidades mais avançadas.
