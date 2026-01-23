# Pipeline ETL - Campanha Bancária Peronalizada

Este projeto foi desenvolvido como parte de um desafio prático de **Ciência de Dados**, com o objetivo de construir um pipeline **ETL (Extract, Transform, Load)** completo utilizando Python.

O sistema simula uma campanha de marketing bancário onde a mensagem enviada ao cliente é personalizada com base em duas variáveis críticas: o **status da fatura** e o **score de crédito**, podendo ser extentida a mais váriaveis dependendo da base de dados disponíveis.

## O Desafio

O objetivo era criar uma solução que não dependesse de APIs externas, focando na lógica de manipulação de dados. O fluxo consiste em:

1.  **Extract:** Leitura de arquivos CSV contendo dados de clientes e modelos de mensagens de marketing.
2.  **Transform:** Aplicação de regras de negócio para definir qual mensagem cada cliente deve receber e personalização do texto com o nome do cliente.
3.  **Load:** Exportação dos dados processados para um arquivo CSV pronto para envio.

## Tecnologias Utilizadas

* **Python 3.12+**
* **Pandas:** Para manipulação e análise de dados tabulares.
* **Jupyter Notebook:** Para desenvolvimento interativo e documentação do código.

## Lógica de Negócio (Transformação)

A "inteligência" do sistema decide a mensagem com base na seguinte árvore de decisão:

| Prioridade | Condição (Status Fatura) | Condição (Score) | Ação / Mensagem |
| :--- | :--- | :--- | :--- |
| **1 (Alta)** | `Vencida` | Qualquer | **Cobrança:** Alerta sobre fatura em atraso. |
| **2 (Média)** | `Próximo ao Vencimento` | Qualquer | **Aviso:** Lembrete preventivo para evitar juros. |
| **3 (Baixa)** | `Paga` ou `Longe` | Score **>= 800** | **Oferta VIP:** Convite para cartão Black ou Investimentos. |
| **4 (Baixa)** | `Paga` ou `Longe` | Score **< 800** | **Padrão:** Dicas de segurança ou aumento de limite. |

## Estrutura do Projeto

```text
├── data/
│   ├── clientes.csv       # Dados brutos dos clientes fictícios gerados por IA
│   ├── mensagens.csv      # Modelos de mensagens de marketing gerados por IA
│   └── campanha_final.csv # Arquivo final processado
├── main.ipynb             # Notebook com o código ETL
└── README.md              # Documentação do projeto
=======
# etl-python-dio
ETL em Python – Desafio DIO

