# Relatório inicial
Essa é a branch original. 

## Entendendo a estrutura geral dos programas
Este repositório contém três pastas distintas:

1. **["calibration_data"](calibration_data)**:  
   Contém os dados brutos e os scripts de calibração para as seções do artigo:  
   - *Seção 3 - Um framework abrangente para calibrar o clima em IAMs*  
   - *Seção 4 - CDICE - recalibrando o clima do DICE*  
   O conteúdo e o uso estão detalhados no [README](calibration_data/README.md).  

2. **["DEQN_for_IAMs"](DEQN_for_IAMs)**:  
   Contém os códigos de replicação para *Seção 6 - O custo social do carbono e a redução ótima de emissões na economia DICE*.  
   Aqui, modelos de avaliação integrada (IAMs) não estacionários são resolvidos usando ["Deep Equilibrium Nets (DEQN)"](https://onlinelibrary.wiley.com/doi/epdf/10.1111/iere.12575) no contexto de modelos econômicos climáticos.  

   Como calcular a calibração individual dos modelos está detalhado nos seguintes arquivos README:  
   - [Resultados ótimos](DEQN_for_IAMs/dice_generic/README.md)  
   - [Cenário "business as usual"](DEQN_for_IAMs/gdice_baseline/README.md)  
   - [Resultados do apêndice](DEQN_for_IAMs/dice_generic_FEX)  

   O conteúdo e o uso do framework DEQN para IAMs estão descritos no [README](DEQN_for_IAMs/README.md).  

3. **["figures_replication"](figures_replication)**:  
   Contém as rotinas de replicação para gerar todos os gráficos apresentados no artigo.


## Requisitos do código
### Requisitos de Linguagem
O código é escrito majoritariamente em Python, e uma parte dele, especificamente dos gráficos, escrito em Julia. 

As versões do Python utilizada no projeto pode ser entre a 3.6 e a 3.8, devido às dependências do projeto requererem essas versões. Contudo, foi utilizada a versão mais atual do python nessa faixa, isto é, a 3.8.10, devido a ser a ultima versão de segurança da 3.8. Além disso, a versão de Julia é 

### Requisitos de Dependências
Para executar o código, os frameworks e bibliotecas utilizados são:
- Pandas
- Scipy
- Matplotlib
- Numpy
- Keras
- Tensorflow

As versões estão no arquivo ["requirements.txt"](requirements.txt).

### Requisitos da Máquina
Não foi especificado os requisitos mínimos exatos, contudo, para o artigo, foi executado em uma maquina em um nó de computação Intel de 8 núcleos na plataforma [Nuvolos Cloud](https://nuvolos.cloud), com 64GB de RAM e 100GB de SSD. 

- São necessários cerca de 15 minutos em um "notebook comum" para o modelo convergir.

- Todos os códigos de pós-processamento (para gerar estatísticas resumidas, gráficos, etc.) foram executados em um notebook comum com processador Intel de 4 núcleos, rodando Ubuntu 18.04.5 LTS, e geralmente levam apenas alguns segundos para serem concluídos.

- O tempo aproximado necessário para reproduzir todas as análises deste artigo em um computador desktop padrão (ano 2023) varia entre **1 a 3 dias**.

- **Caso queira usar a GPU para conseguir resultados com maior rapidez, é preciso ter os drivers CUDA 10.1 e cuDNN 7.6.5, devido a versão do TensorFlow ser a 2.2, de acordo com a ["Documentação do Tensorflow"](https://www.tensorflow.org/install/source?hl=pt-br#gpu). Contudo, não foi especificado se foi utilizado a GPU**

Para testar o funcionamento do código, foi utilizada uma máquina com Intel i7 de 11ª geração, 20 cores (40 threads), 32GB de RAM, e 1TB de SSD, com cerca de 800GB de SSD livres.

## Instalação do ambiente para a máquina
### Linux Ubuntu
#### Python
Foi utilizado o pyenv para instalar a versão 3.8.10 do python. Para isso, pode-se instalar o pyenv com:

```bash
sudo apt update
sudo apt install -y build-essential libssl-dev zlib1g-dev \
    libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
    libncurses5-dev libncursesw5-dev xz-utils tk-dev \
    libffi-dev liblzma-dev python-openssl git

curl https://pyenv.run | bash
```

Após isso, deve-se acessar o .bashrc no terminal, com `sudo nano ~/.bashrc`. No final do arquivo, coloque:
```bash
# pyenv
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init --path)"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
Salve o .bashrc, e saia.
Após isso, abra um terminal no diretório em que está o projeto, e execute os comandos:
```bash
#cd para/o/diretorio/
pyenv install 3.8.10
pyenv local 3.8.10
```
Isso instalará o Python 3.8.10 no diretório.

Após isso, no mesmo terminal, crie o ambiente do diretório em Python, e ative o ambiente, instalando as dependencias necessárias:

```bash
#criando ambiente
python -m venv venv
source venv/bin/activate

#instalando dependências
pip install -r "requirements.txt"
```

Com isso, já podemos executar códigos dos diretórios ["DEQN_for_IAMs"](/DEQN_for_IAMs/), ["calibration_data"](/calibration_data/), e a maioria dos códigos de ["figures_replication"](/figures_replication/)
#### Julia 
Para os códigos em Julia, abra um terminal, e execute o comando:

```bash
curl -fsSL https://install.julialang.org | sh
```

## Execução dos Códigos
### Replicação das Seções Apresentadas no ["Artigo"](artigo.pdf)
Para a replicação das seções, há uma ["README.md - Seção de Replicação do Artigo"](README.md##Replication) que explica como executar o código de acordo com o artigo. 
