# 🎩 Escrevendo como Lewis Carroll: Geração de Texto com LSTM

Este projeto utiliza **Redes Neurais Recorrentes (RNN)**, especificamente a arquitetura **Long Short-Term Memory (LSTM)**, para aprender o estilo literário de **Lewis Carroll** e gerar novos textos inspirados na obra clássica **_Alice no País das Maravilhas_**.

---

## 📖 Visão Geral

O objetivo é criar um modelo de **predição caractere por caractere**.  
Dada uma sequência de texto, o modelo aprende a prever o próximo caractere mais provável, possibilitando a geração de parágrafos inteiros que mimetizam o vocabulário, a estrutura sintática e o ritmo narrativo do autor original.

---

## 🛠️ Tecnologias Utilizadas

- **Python 3**
- **TensorFlow / Keras** — construção e treinamento da rede neural
- **NumPy & Pandas** — manipulação e preparação dos dados
- **Google Colab** — ambiente de desenvolvimento e execução

---

## 🏗️ Arquitetura do Modelo

O modelo foi implementado utilizando a **API Funcional do Keras** e é composto por três camadas principais:

1. **Embedding**  
   Camada de entrada responsável por mapear os IDs dos caracteres em vetores densos.

2. **LSTM**  
   Camada recorrente com **1024 unidades**, encarregada de aprender dependências de longo prazo na sequência textual.

3. **Dense**  
   Camada de saída que projeta a representação aprendida para o tamanho do vocabulário (logits).

---

## 🚀 Fluxo de Trabalho

### 1. Pré-processamento

- **Vetorização**  
  Conversão do texto original em IDs numéricos utilizando `tf.keras.layers.StringLookup`.

- **Criação de Sequências**  
  O texto foi segmentado em janelas deslizantes de **100 caracteres** para treinamento supervisionado.

- **Batching**  
  Organização dos dados em batches de **64 sequências**, com *shuffle* e *prefetch* para otimização de desempenho.

---

### 2. Treinamento

- **Função de Perda (Loss Function)**  
  `SparseCategoricalCrossentropy` (a partir de logits).

- **Otimizador**  
  `Adam`.

- **Épocas**  
  Treinamento realizado por **20 épocas**.

- **Checkpoints**  
  Salvamento automático dos pesos do modelo para retomada do treinamento ou inferência posterior.

---

### 3. Geração de Texto

A geração de texto é realizada por meio de **amostragem com Temperatura**:

- **Temperatura alta** → textos mais criativos e imprevisíveis  
- **Temperatura baixa** → textos mais conservadores e repetitivos

---

## 📊 Resultados

Após o treinamento, o modelo foi capaz de gerar fragmentos textuais contendo:

- Diálogos estruturados  
- Nomes de personagens como *Alice*, *The King* e *The Queen*  
- Uso consistente de pontuação e quebras de linha características da obra original  

**Exemplo de saída:**

```text
Alice: 'Oh! What I'd non. wet tast is be ding one boling
and retting or any--and itself so you filling thome...
