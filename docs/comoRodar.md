# Instruções de Run

Para executar o projeto, siga os passos abaixo:

## Ambiente

### Garanta que você tenha o Python 3.8 ou superior instalado

```sh
python --version
```

### Clone o repositório

```sh
git clone https://github.com/PI2-GrassBot/GrassBot.git
```

### Crie um ambiente virtual

```sh
python -m venv .venv
```

### Ative o ambiente virtual

```sh
# Windows
.venv\Scripts\activate

# Linux
source .venv/bin/activate
```

### Instale as dependências

```sh
pip install -r requirements.txt
```

## abordagemV1

```sh
cd abordagemV1
```

### simulador

```sh
python src/main.py
```
Dentro da interface do pygame, você pode posicionar o GrassBot com o cursor do mouse e clicar no número 1 para definir o ponto de partida

### api

```sh
python src/api/app.py
```
Será aberto um servidor no endereço http://localhost:5001/


### interface
```sh
python src/ui/interface.py
```
Será aberta uma janela com os controles de power, velocidade e altura da grama do GrassBot no endereço http://localhost:5000/

## abordagemV2

```sh
cd abordagemV2
```

### simulador
```sh
python src/simulation/main.py
```

### api
```sh
python src/api/api.py
```
Será aberto um servidor no endereço http://localhost:5001/

### interface
```sh
python src/ui/interface.py
```
Será aberta uma janela com os controles de power, velocidade e altura da grama do GrassBot no endereço http://localhost:5000/




