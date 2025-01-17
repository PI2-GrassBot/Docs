# Sensoriamento

## Introdução

O sensoriamento é uma etapa fundamental para o funcionamento de qualquer robô autônomo, incluindo o GrassBot. Sensores são dispositivos que captam informações do ambiente e as convertem em sinais elétricos ou digitais que podem ser processados pelo sistema de controle do robô. Eles fornecem dados essenciais para a navegação, detecção de obstáculos, localização e interação com o ambiente.

Neste documento, apresentamos uma visão geral dos sensores que serão emulados no simulador do GrassBot. Esses sensores são essenciais para a operação autônoma do robô cortador de grama, permitindo que ele navegue de forma segura e eficiente pelo gramado.

Para a definiçao de sensoriamento, foram utilizadas as referencias obtidas durante o [benchmarking](./benchmark.md), que apresentam os sensores mais comuns em robôs cortadores de grama autônomos e o como eles são posicionados no robô.

## Sensores Utilizados

### 1. **Sensores Ultrassônicos**

Os sensores ultrassônicos são amplamente utilizados em robótica para detecção de obstáculos. Eles emitem ondas sonoras de alta frequência e medem o tempo que leva para o som refletido retornar ao sensor. Com base nesse tempo, é possível calcular a distância até o objeto mais próximo.

O modelo sugerido para utilizar é o sensor HC-SR04, que é preciso, de baixo custo e fácil de integrar com microcontroladores.

![Sensor Ultrassônico HC-SR04](https://newportcom.com.br/wp-content/uploads/2019/06/sensor_ultrassonico-e1663846186843.webp)

### 2. **Sensores de Cor**

Os sensores de cor são empregados para identificar diferentes tonalidades e padrões de cores no ambiente. Eles são úteis para detectar linhas de demarcação, áreas de corte e outros elementos visuais que auxiliam na navegação do robô.

O modelo sugerido para utilizar é o sensor TCS230, que é capaz de detectar uma ampla gama de cores e fornecer informações precisas sobre a tonalidade de cada pixel.
![Sensor de Cor TCS230](https://curtocircuito.com.br/pub/media/catalog/product/cache/ebf77fb58d795a2dbe3218c301c821c6/s/e/sensor_de_cor_-_tcs230_-_rgb_1.jpg)

## Posicionamento dos Sensores

Os sensores serão posicionados estrategicamente no GrassBot para garantir uma cobertura eficiente do ambiente. Durante a simulacão, os sensores serão emulados na parte frontal do robô, permitindo a detecção de obstáculos e a identificação de áreas de corte.


