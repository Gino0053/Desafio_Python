# **Análise de Rentabilidade de Carteira de Ações**

Este script realiza uma análise da rentabilidade de uma carteira de ações, comparando o desempenho dessa carteira com o índice **IBOVESPA** (representado pelo ticker `^BVSP`). O código busca informações históricas de preços de fechamento das ações listadas na carteira e calcula a rentabilidade de cada ativo, bem como a rentabilidade total da carteira.

## **Pré-requisitos**

Antes de rodar o código, certifique-se de que você tem os seguintes pacotes instalados:

- `pandas`
- `yfinance`

Você pode instalar esses pacotes via pip se ainda não os tiver:

```bash
pip install pandas yfinance
```

## **Estrutura do Código**

### 1. **Carregando a Carteira de Ações**

O código começa lendo uma lista de ações e valores associados de um arquivo de texto chamado `Carteira.txt`. Cada linha do arquivo contém o **ticker** da ação (por exemplo, `ITUB4.SA`) e o **valor investido** nessa ação. O formato de cada linha deve ser:

```
TICKER-VALOR
```

Exemplo do conteúdo de `Carteira.txt`:

```
ITUB4-10000
BBAS3-15000
EGIE3-20000
```

Após ler o arquivo, o código organiza essas informações em um **dicionário** chamado `carteira`, onde a chave é o ticker da ação e o valor é o montante investido.

### 2. **Baixando Dados de Preço das Ações**

O próximo passo é baixar os preços históricos das ações para o ano de 2024. Isso é feito utilizando a biblioteca `yfinance`, que permite buscar dados financeiros diretamente do Yahoo Finance. O código seleciona as ações que estão na carteira e adiciona também o índice **IBOVESPA** (`^BVSP`) para comparações posteriores.

As datas de início e fim para o período de análise são definidas nas variáveis `data_inicial` e `data_final`:

```python
data_inicial = "2024-01-01"
data_final = "2024-12-15"
```

### 3. **Calculando Rentabilidade de Cada Ativo**

O código então calcula a **rentabilidade** de cada ativo na carteira. A rentabilidade de um ativo é calculada pela seguinte fórmula:

**Rentabilidade = (Preço Final / Preço Inicial) - 1**

A rentabilidade é armazenada em um dicionário `rentabilidades`, onde a chave é o ticker e o valor é a rentabilidade do ativo.

### 4. **Calculando Rentabilidade Total da Carteira**

Após calcular as rentabilidades individuais dos ativos, o script calcula a **rentabilidade total da carteira**. Para isso, ele utiliza a fórmula:

**Rentabilidade da Carteira = (Valor Final da Carteira / Valor Inicial da Carteira) - 1**

Aqui, o **valor final da carteira** é obtido multiplicando a rentabilidade de cada ativo pelo valor investido inicial em cada um, e somando todos esses resultados.

### 5. **Comparação com o Índice IBOVESPA**

Além de calcular a rentabilidade da carteira, o código também calcula a rentabilidade do índice **IBOVESPA** no mesmo período para fazer uma comparação. A rentabilidade do IBOVESPA é calculada da mesma forma que para os ativos individuais, e a rentabilidade da carteira é comparada com a rentabilidade do índice.

### 6. **Exibição dos Resultados**

Por fim, o código imprime:

- Rentabilidade de cada ativo.
- Rentabilidade total da carteira.
- Rentabilidade do índice **IBOVESPA**.

---

## **Como Usar**

1. **Prepare o arquivo `Carteira.txt`:** 
   - Crie um arquivo de texto chamado `Carteira.txt` com a lista de ativos e os respectivos valores investidos, no formato `TICKER-VALOR`.

   Exemplo:

   ```
   ITUB4-10000
   BBAS3-15000
   EGIE3-20000
   ```

2. **Execute o Código:**
   - Execute o script Python. O código irá:
     1. Ler a carteira de ações do arquivo `Carteira.txt`.
     2. Baixar os preços históricos das ações e do índice **IBOVESPA**.
     3. Calcular a rentabilidade de cada ativo e da carteira.
     4. Comparar a rentabilidade da carteira com a do índice **IBOVESPA**.

3. **Verifique os Resultados:**
   - O código imprimirá no console as rentabilidades de cada ativo, a rentabilidade total da carteira e a rentabilidade do índice **IBOVESPA**.

---

## **Exemplo de Saída**

A saída do código será algo como:

```
ITUB4.SA 10000.0
BBAS3.SA 15000.0
EGIE3.SA 20000.0
{'ITUB4.SA': 10000.0, 'BBAS3.SA': 15000.0, 'EGIE3.SA': 20000.0}
Rentabilidade de cada ativo:
{'ITUB4.SA': 1.025, 'BBAS3.SA': 1.010, 'EGIE3.SA': 1.030}
Rentabilidade da carteira: 3.2%
Rentabilidade do IBOVESPA: 1.5%
```
