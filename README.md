<h1>Projeto de Dados - Tiktok</h1>


<h1>Introdução</h1>
Este projeto tem como finalidade analisar os 100 principais influenciadores do TikTok em 2025. O objetivo é fornecer insights detalhados sobre os influenciadores mais populares, suas métricas de engajamento e permitir a comparação entre eles.

<hr>
<br>

<h1>Objetivos</h1>
Apresentar métricas importantes como número de seguidores, curtidas, uploads e taxa de engajamento.
Permitir comparações diretas entre influenciadores.

<h1>Tecnologias Utilizadas</h1>
<b>Linguagem:</b> Python

<h3><b>Bibliotecas:</b></h3>
<b>pandas:</b> Manipulação e análise de dados.
<b>streamlit:</b> Criação do dashboard
<b>plotly.express:</b> Visualização de dados com gráficos.

<hr>
<br>

<h1>Estrutura do Código</h1>
O código do projeto está estruturado da seguinte maneira:

<h3><b>Carregamento dos Dados</b></h3>
O arquivo delimitado por vírgula, com a extensão .csv é carregado no dataframe.

```python
import pandas as pd

def load_data():
    file_path = "Top 100 tiktokers in 2025.csv"
    df = pd.read_csv(file_path)
    return df

df = load_data()
```

<br>

<h3><b>Configuração do Streamlit</b></h3>
Definindo o título principal do dashboard.

```python
import streamlit as st
import plotly.express as px

st.title("Dashboard: Top 100 TikTokers em 2025")
```

<br>

<h3><b>Criação de Abas</b></h3>
Faço a criação detrês abas principais para organizar as análises.
```python
aba1, aba2, aba3 = st.tabs(["Visão Geral", "Análise de Engajamento", "Comparação de Influenciadores"])
```
**Descrição:**
- O dashboard possui três abas principais para organizar as análises.

## 5. Análises Implementadas

### 5.1 Visão Geral
Esta aba apresenta uma visão geral das métricas dos TikTokers:
- **Gráfico de dispersão Seguidores vs. Curtidas**
- **Top 10 TikTokers por número de seguidores**
- **Top 10 TikTokers por uploads**

### 5.2 Análise de Engajamento
Foca na relação entre curtidas e seguidores:
- **Taxa de engajamento (curtidas/seguidores)**
- **Distribuição da taxa de engajamento**
- **Boxplot da taxa de engajamento**

### 5.3 Comparação de Influenciadores
Permite a seleção de múltiplos influenciadores para comparação direta:
- **Comparação de seguidores, curtidas e uploads**
- **Relação entre seguidores e uploads**
- **Relação entre curtidas e uploads**

## 6. Como Executar o Projeto
1. Instale as dependências:
   ```sh
   pip install streamlit pandas plotly
   ```
2. Salve o arquivo **Top 100 tiktokers in 2025.csv** no diretório do projeto.
3. Execute o aplicativo Streamlit:
   ```sh
   streamlit run nome_do_arquivo.py
   ```

## 7. Possíveis Melhorias
- Adicionar mais métricas como taxa de crescimento de seguidores.
- Implementar um filtro para visualizar influenciadores por categoria.
- Criar um ranking dinâmico baseado no engajamento.

## 8. Conclusão
Este projeto oferece uma maneira eficiente e interativa de analisar os principais influenciadores do TikTok em 2025. Com gráficos dinâmicos e filtros flexíveis, o dashboard permite obter insights valiosos sobre a popularidade e o engajamento dos criadores de conteúdo.

---
Caso precise de mais funcionalidades ou otimizações, entre em contato! 🚀

