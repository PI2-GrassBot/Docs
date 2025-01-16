# Benchmark

Com o objetivo de elicitar os requisitos do projeto GrassBot, realizamos um benchmarking com produtos similares no mercado. A seguir, apresentamos uma análise de alguns cortadores de grama autônomos existentes no mercado, destacando suas principais características.

Os cortadores de grama autônomos, também conhecidos como robôs cortadores de grama, são dispositivos projetados para operar de forma independente, mantendo o gramado aparado sem a necessidade de intervenção humana constante. Eles utilizam sensores, sistemas de navegação e, em alguns casos, inteligência artificial para mapear e cortar a área designada.

**Principais Características dos Cortadores de Grama Autônomos:**

- **Navegação Inteligente:** Muitos modelos utilizam sensores para detectar obstáculos e evitar colisões, garantindo um corte eficiente e seguro.

- **Programação de Horários:** Permitem agendar horários específicos para o corte, oferecendo conveniência ao usuário.

- **Recarga Automática:** Alguns dispositivos retornam automaticamente à base de carregamento quando a bateria está baixa.

- **Ajuste de Altura de Corte:** Possibilitam a configuração da altura desejada para o corte da grama.

**Vantagens:**

- **Autonomia:** Operam sem supervisão constante, economizando tempo e esforço.

- **Consistência:** Mantêm o gramado com aparência uniforme através de cortes regulares.

- **Eficiência Energética:** Muitos modelos são elétricos, contribuindo para a redução de emissões de carbono.

**Desafios:**

- **Preço:** O investimento inicial pode ser elevado em comparação com cortadores tradicionais.

- **Limitações de Terreno:** Podem enfrentar dificuldades em terrenos muito irregulares ou com declives acentuados.

**Exemplos de Modelos Populares:**

1. **Greenworks Optimow 15:** Um robô cortador de grama adequado para áreas de até 1500 m², conhecido por sua eficiência e facilidade de uso. 

2. **Gardena PowerMax 32/1200 G2:** Embora não seja totalmente autônomo, este modelo elétrico oferece recursos avançados e é ideal para jardins de pequeno a médio porte. 

## Projetos de Código Aberto

Além dos modelos comerciais, existem projetos de código aberto que permitem a construção de cortadores de grama autônomos personalizados.



[**OpenMower** ](https://www.notebookcheck.info/O-OpenMower-e-um-cortador-de-grama-robotico-com-base-em-Raspberry-Pi-e-ArduSimple-que-voce-mesmo-pode-construir.613447.0.html?utm_source=chatgpt.com) 
Desenvolvido por Clemens Elflein, o OpenMower é um cortador de grama robótico que utiliza um Raspberry Pi 4, uma placa GPS ArduSimple RTK para navegação precisa e um microcontrolador Raspberry Pi Pico para tarefas em tempo real. O projeto substitui a eletrônica de um cortador de grama comercial por esses componentes, permitindo navegação sem a necessidade de fios perimetrais. 


[**Mowerino**](https://www.notebookcheck.info/Engenheiro-projeta-o-Mowerino-um-cortador-de-grama-robotico-para-bricolagem-baseado-no-Arduino.615510.0.html?utm_source=chatgpt.com)  
Criado pelo engenheiro eletrônico 'salmec', o Mowerino é um cortador de grama robótico autônomo baseado na plataforma Arduino. Utiliza uma placa Arduino Mega 2560, sensores ultrassônicos para detecção de obstáculos, inclinômetro como sensor antitombamento e módulos Bluetooth para controle manual. O chassi e as rodas foram confeccionados com peças impressas em 3D. 




[**Capinator**](https://github.com/JhonathanNicolas/Capinator-Cortador-de-Grama-Autonomo-Automatic-Lawn-Mower)
Desenvolvido como projeto final da disciplina de Eletrônica Embarcada do curso de Engenharia Eletrônica da Universidade de Brasília, o Capinator é um robô cortador de grama autônomo que utiliza o microcontrolador MSP430G2553, sensores ultrassônicos HC-SR04 para detecção de obstáculos, módulo relé para controle do motor de corte e ponte H L298N para controle dos motores de tração. 



[**Projeto de Robô Cortador de Grama Autônomo para Uso Residencial**](https://rbeg.net/index.php/rbeg/article/view/91/166)  
Este projeto acadêmico da Universidade Federal do Rio de Janeiro detalha o desenvolvimento de um robô cortador de grama autônomo, incluindo a modelagem de seus principais sistemas e componentes. O estudo aborda sistemas de locomoção, corte e sensores, utilizando um programa de CAD para modelagem da estrutura. 


Esses projetos oferecem uma visão dos componentes eletrônicos e sensores empregados no desenvolvimento de cortadores de grama autônomos,além das funcionalidades e desafios enfrentados na construção desses dispositivos.