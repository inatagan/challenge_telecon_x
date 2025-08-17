![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![Debian](https://img.shields.io/badge/Debian-D70A53?style=for-the-badge&logo=debian&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![Neovim](https://img.shields.io/badge/NeoVim-%2357A143.svg?&style=for-the-badge&logo=neovim&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle-F80000?style=for-the-badge&logo=oracle&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)

# challenge_telecon_x
EDA Challenge Telecon X as part of the program Oracle ONE

### Sobre

Este projeto foi realizado como parte do programa Oracle ONE 2025 de Data Science.

### Estrutura do projeto
o codigo "main" se encontra no diretorio `src`, os arquivos gerados, `outputs`, foram colocados no diretorio `/assets/charts`.

Este projeto utiliza um ambiente virtual python `venv` para compartimentalizar a instalacao e esecucao de bibliotecas relacionas a este projeto.

# Instrucoes de como executar o projeto localmente:

### Create a python Environment
On the root dir of the project open the terminal and run the following command:

```
python3 -m venv venv
```

### Activate the venv

```
source venv/bin/activate
```

### Install jupyter kernel for the virtual environment using the following command:

```
ipython kernel install --user --name=venv
```

### Select the installed kernel when you want to use jupyter notebook in this virtual environment:

![venv_example](/assets/img/venv_kernel_example.png)

## Relatório de Análise Exploratória dos Dados - Projeto TelecomX

### 1. Extração dos Dados

O projeto iniciou com a extração dos dados de uma API disponibilizada em formato JSON. Utilizamos as bibliotecas `requests` e `json` para acessar e carregar os dados, que foram posteriormente normalizados e convertidos em um DataFrame do pandas para facilitar a manipulação e análise.

### 2. Limpeza e Transformação dos Dados

Após a extração, realizamos diversas etapas de limpeza e transformação:
- **Remoção de duplicatas:** Garantindo que cada cliente fosse único na base.
- **Ajuste de colunas categóricas:** Padronização dos nomes dos contratos e métodos de pagamento, removendo caracteres desnecessários.
- **Conversão de tipos:** Valores monetários foram convertidos de string para float, e colunas numéricas ajustadas para o tipo adequado.
- **Criação de novas variáveis:** Calculamos, por exemplo, o valor diário das contas (`Contas_Diarias`) a partir do valor mensal.

### 3. Análise Exploratória

Foram realizadas diversas análises para entender o perfil dos clientes e os fatores relacionados à evasão (churn):

- **Distribuição de Evasão:** Identificamos que aproximadamente 27% dos clientes cancelaram o serviço, enquanto 73% permaneceram ativos.
![eva_por](/assets/charts/Evasao_Porcentagem.png)
- **Evasão por Gênero:** A evasão está distribuída de forma semelhante entre homens e mulheres, sem diferença significativa.
![eva_gen](/assets/charts/Evasao_Genero.png)
- **Evasão por Método de Pagamento:** Clientes que utilizam "Electronic check" apresentam maior taxa de evasão, enquanto métodos automáticos têm menor evasão.
![eva_met](/assets/charts/Evasao_Metodo_Pagamento.png)
- **Evasão por Tipo de Contrato:** Contratos mensais têm taxas de evasão muito superiores aos contratos anuais ou bienais.
![eva_tip](/assets/charts/Evasao_Tipo_Contrato.png)
- **Evasão por Senioridade:** Clientes idosos (SeniorCitizen) apresentam uma leve tendência a maior evasão, mas a diferença não é tão expressiva.
![eva_age](/assets/charts/Evasao_Senioridade.png)
- **Relação entre Tempo de Contrato e Total Gasto:** Clientes com menor tempo de contrato e menor valor total gasto concentram a maior parte dos cancelamentos.
![eva_time](/assets/charts/Evasao_Dispersao_Tempo_Contrato_x_Total_Gasto.png)
- **Matriz de Correlação:** Não há correlações fortes entre as variáveis numéricas, mas observa-se relação negativa entre tempo de contrato e evasão.
![mat](/assets/charts/Matriz_Correlacao_Variaveis_Numericas.png)

### 4. Conclusões

A análise indica que o principal fator associado à evasão é o tipo de contrato: clientes com contratos mensais são mais propensos a cancelar. Métodos de pagamento também influenciam, especialmente pagamentos não automáticos. Recomenda-se estratégias de retenção focadas em migrar clientes para contratos mais longos e incentivar métodos de pagamento automáticos.

O dataset foi devidamente tratado e está pronto para análises preditivas ou construção de modelos de machine learning para previsão de churn.