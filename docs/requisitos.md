# Requisitos

## Introdução
Este documento tem como objetivo apresentar os requisitos funcionais e não funcionais do projeto GrassBot. O sistema deve ser capaz de identificar a área de corte, percorrer a área delimitada seguindo um algoritmo de cobertura eficiente, detectar obstáculos em tempo real e recalcular a rota para evitá-los. O software deve permitir ajuste da altura de corte e velocidade de deslocamento, possuir uma interface para ligar e desligar, iniciar apenas se a bateria estiver acima de 80% e permitir a inserção de obstáculos em tempo real.

## Requisitos Funcionais
| Código  | Descrição |
|---------|------------------------------------------------------------------------------------------------|
| RF01 | O sistema deve identificar a área de corte de forma autônoma. |
| RF02 | O cortador deve ser capaz de percorrer a área delimitada seguindo um algoritmo de cobertura eficiente. |
| RF03 | O software deve detectar obstáculos em tempo real e recalcular a rota para evitá-los. |
| RF04 | O emulador deve simular as funções do cortador, permitindo a validação do algoritmo antes da implementação física. |
| RF05 | O software deve permitir ajuste da altura de corte e velocidade de deslocamento. |
| RF06 | O software deve possuir uma interface para ligar e desligar. |
| RF07 | O sistema só deve iniciar caso a bateria esteja acima de 80%. |
| RF08 | O usuário deverá conseguir inserir obstáculos em tempo real. |



## Requisitos Não Funcionais
| Código  | Descrição |
|---------|------------------------------------------------------------------------------------------------|
| RNF01 | O sistema deve ser desenvolvido utilizando Python e frameworks de simulação para a criação do emulador. |
| RNF02 | A interface do software deve ser intuitiva e acessível para usuários sem conhecimento técnico avançado. |
| RNF03 | O processamento dos dados de sensores deve ocorrer em tempo real para permitir ajustes rápidos no percurso. |
| RNF04 | O consumo energético do sistema embarcado deve ser otimizado para garantir maior autonomia da bateria. |
| RNF05 | O tempo de resposta para recalculo de rota ao detectar um obstáculo deve ser inferior a 2 segundos. |
| RNF06 | A emulação deverá conter mocks de sensores ultrasônicos. |