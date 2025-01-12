# Aruiteturara

## Introdução
A arquitetura apresentada na imagem abaixo consiste em um sistema de corte de grama automatizado, que funciona de maneira autônoma, detectando obstáculos, otimizando rotas e garantindo um corte preciso sem intervenção humana direta. O sistema é composto por tres serviços principais: a interface de usuário, a API de comunicação e o simulador de ambiente.

[![Arquitetura](https://raw.githubusercontent.com/PI2-GrassBot/Docs/refs/heads/main/assets/arquitetura.jpg)](https://raw.githubusercontent.com/PI2-GrassBot/Docs/refs/heads/main/assets/arquitetura.jpg)

## Componentes

### Interface de Usuário
A interface de usuário é responsável por permitir a interação com o sistema de corte de grama automatizado. Nela, o usuário pode configurar a altura de corte, visualizar o status do equipamento e monitorar o status da operação de corte. A interface é implementada em uma aplicação web com a utilização de Flask, um framework de desenvolvimento web em Python.

### API de Comunicação

A API de comunicação é responsável por receber as requisições da interface de usuário e repassá-las para o simulador de ambiente. Ela é implementada em Python com o uso do FastAPI, um framework web de alto desempenho.

### Simulador de Ambiente

O simulador de Ambiente é composto por três módulos principais: O Core, o Mock de Sensores, e o Simulador de Movimento. O Core é responsável por gerenciar a lógica de simulação, como a detecção de obstáculos e o cálculo de rotas, funcionando como um microcontrolador virtual. O Mock de Sensores simula a leitura de sensores de proximidade e obstáculos, fornecendo dados para o Core. O Simulador de Movimento, implementado com Pygame, é responsável por exibir a simulação em tempo real, permitindo visualizar o movimento do cortador de grama no ambiente virtual.

<!-- PRINT DO SIMULADOR AQUI -->


## Diagrama de Classes

O diagrama de classes apresenta a estrutura do GrassBot, mostrando as classes e suas relações.


### Diagrama de Classes V1

[![Diagrama de Classes](https://raw.githubusercontent.com/PI2-GrassBot/Docs/refs/heads/main/assets/uml.png)](https://raw.githubusercontent.com/PI2-GrassBot/Docs/refs/heads/main/assets/uml.png)