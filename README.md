# Projeto-Completo-Detec-o-de-Anomalias-em-Transa-es-Financeiras
Projeto Completo — Detecção de Anomalias em Transações Financeiras
Projeto Completo — Detecção de Anomalias em Transações Financeiras

Objetivo

Criar um sistema inteligente capaz de detectar transações financeiras suspeitas utilizando Machine Learning com Python.

O projeto utiliza:

Python
Pandas
Scikit-Learn
Matplotlib
Seaborn
Isolation Forest

Estrutura do Projeto

projeto-anomalias/
│
├── data/
│   └── transacoes.csv
│
├── src/
│   ├── preprocessamento.py
│   ├── modelo.py
│   └── visualizacao.py
│
├── notebooks/
│   └── analise.ipynb
│
├── main.py
├── requirements.txt
└── README.md

1. Instalação do Ambiente

Abra o terminal e execute:

pip install pandas numpy matplotlib seaborn scikit-learn jupyter

2. Criando o Dataset

Crie a pasta:
mkdir data

Depois crie o arquivo:
data/transacoes.csv

Adicione:

valor,hora,transacoes_dia
120,10,3
150,11,4
130,12,3
5000,2,25
140,13,2
160,14,3
7000,1,30
170,15,4
200,16,5
250,17,6
8000,0,40

3. Arquivo preprocessamento.py

Crie a pasta:

mkdir src

Depois crie:

src/preprocessamento.py

Código:

import pandas as pd

def carregar_dados(caminho):
    df = pd.read_csv(caminho)

 print("\nDataset carregado com sucesso!\n")

    print(df.head
     return df

    4. Arquivo modelo.py

    src/modelo.py

     from sklearn.ensemble import IsolationForest
     tectar_anomalias(df):

    modelo = IsolationForest(
        contamination=0.1,
        random_state=42
    )

    colunas = [
        'valor',
        'hora',
        'transacoes_dia'
    ]

    modelo.fit(df[colunas])

    df['anomalia'] = modelo.predict(df[colunas])

return df

5. Arquivo visualizacao.py

import matplotlib.pyplot as plt

cores = df['anomalia'].map({
        1: 'blue',
        -1: 'red'
    })

    plt.figure(figsize=(10, 6))

    plt.scatter(
        df['hora'],
        df['valor'],
        c=cores,
        s=120
    )

    plt.xlabel('Hora da Transação')
    plt.ylabel('Valor')
    plt.title('Detecção de Anomalias Financeiras')

    plt.grid(True)

    plt.show()

    6. Arquivo main.py

    main.py

    from src.preprocessamento import carregar_dados
from src.modelo import detectar_anomalias
from src.visualizacao import plotar_anomalias

def main():

    caminho = 'data/transacoes.csv'

    df = carregar_dados(caminho)

    resultado = detectar_anomalias(df)

    print('\nResultado Final:\n')

    print(resultado)

    print('\nTransações Suspeitas:\n')

    suspeitas = resultado[
        resultado['anomalia'] == -1
    ]

    print(suspeitas)

    plotar_anomalias(resultado)


if __name__ == '__main__':
    main()

 7. requirements.txt

 pandas

numpy
matplotlib
seaborn
scikit-learn
jupyter   

8. Como Executar

python main.py

Resultado Esperado

O sistema irá:

Ler os dados
Identificar padrões
Detectar transações fora do normal
Marcar anomalias em vermelho

Resultado da coluna:

1 = normal
-1 = anomalia

