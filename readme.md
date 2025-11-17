# README.md

# 🚀 Projeto de Análise de Sentimentos e Tópicos (NPS)

Este notebook de Google Colab foi projetado para automatizar a análise de comentários de NPS. Ele realiza as seguintes etapas:

1.  **Carrega** um banco de dados de comentários em formato Excel.
2.  **Limpa** e processa os textos (lematização, remoção de stopwords).
3.  **Classifica** cada comentário usando IA para **Sentimento** (Positivo, Neutro, Negativo) e **Tópico** (Preço, Entrega, Atendimento, etc.).
4.  **Analisa** a frequência e importância de bigramas (termos com duas palavras) usando TF-IDF.
5.  **Salva** os resultados (gráficos e arquivos CSV) localmente no ambiente do Colab.

## 📊 Visualização Web (Dashboard)

Os dados processados por este script podem ser usados para alimentar um dashboard interativo.

Uma visualização web do projeto, contendo vários gráficos e filtros dinâmicos, está disponível em:

**[https://swiftnps.vercel.app](https://swiftnps.vercel.app)**

![SWIFTAnalytics Dashboard](<img src="dashboard.png">)

## 👨‍💻 Criadores

| Eduardo | Fujita |
| :---: | :---: |
| <img src="assets/eduardo.jpg" width="150" alt="Foto do Eduardo"> | <img src="assets/fujita.jpg" width="150" alt="Foto do Fujita"> |

## 📋 Pré-requisitos

* Uma conta Google.
* O notebook deve ser executado no ambiente **Google Colab**.
* Para melhor performance, ative o acelerador de **GPU** (Ambiente de Execução -> Alterar tipo de ambiente de execução -> T4 GPU).

## ⚙️ Como Usar (Passo a Passo)

Siga estas etapas na ordem correta para garantir que o script funcione.

### 1. Importação do Banco de Dados (Obrigatório)

Esta é a etapa mais importante. O script não funcionará se não encontrar o arquivo de dados com o nome exato.

* **Nome do Arquivo Esperado:** `NPS-Comentarios-2024-Louveira_VilaAndrade.xlsx`

**Como fazer o upload no Google Colab:**

1.  No Google Colab, abra a barra lateral esquerda e clique no ícone de **Pasta** (Arquivos).
2.  Arraste o seu arquivo `NPS-Comentarios-2024-Louveira_VilaAndrade.xlsx` do seu computador e solte diretamente nessa área de "Arquivos".
3.  Aguarde o upload ser concluído. Você deve ver o nome do arquivo listado na barra lateral.

> **Atenção:** Se o seu arquivo tiver um nome diferente, você **deve** renomeá-lo para `NPS-Comentarios-2024-Louveira_VilaAndrade.xlsx` **ou** alterar o nome do arquivo na Célula 4 do script:
>
> `df = pd.read_excel('SEU_NOME_DE_ARQUIVO_AQUI.xlsx')`

### 2. Ordem de Execução das Células

Execute as células do notebook na seguinte ordem:

1.  **Células de Instalação (Células 2 e 3):**
    * Rode as células que instalam as bibliotecas (`!python -m spacy download...` e `!pip install pandas...`). Elas preparam o ambiente.

2.  **Célula de Processamento Principal (Célula 4):**
    * Rode a célula longa que começa com `# --- 1. Imports Gerais ---`.
    * Esta é a célula principal que faz todo o trabalho: carrega o Excel, limpa os dados, executa a IA, faz a análise TF-IDF e salva os resultados em CSV e PNGs.
    * **Este processo pode demorar vários minutos**, especialmente na primeira vez, enquanto os modelos de IA são baixados. Você verá barras de progresso (tqdm) para o processo de limpeza e análise.

*(As células 5 e 6 são apenas para exportação para o Google Sheets e podem ser ignoradas se você não precisar dessa funcionalidade).*

## 📤 Resultados (Outputs)

Ao final da execução da Célula 4, você encontrará os seguintes arquivos salvos no painel "Arquivos" do Colab (você pode baixá-los clicando com o botão direito):

* **Arquivos CSV (Resultados Principais):**
    * `NPS_Classificacao_Completa.csv`: O banco de dados original com as colunas de sentimento e tópico.
    * `NPS_TFIDF_Bigramas_COM_FREQ.csv`: A análise de bigramas por classificação (detrator, neutro, promotor).
    * `NPS_TFIDF_Bigramas_POR_TOPICO_SENTIMENTO.csv`: A análise de bigramas por tópico e sentimento combinados.

* **Gráficos (Visualização):**
    * Uma nova pasta chamada `graficos_tfidf_centro` será criada. Dentro dela, você encontrará os gráficos de bigramas salvos como imagens `.png`.
