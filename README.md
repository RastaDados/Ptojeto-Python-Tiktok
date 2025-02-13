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
<b>pandas:</b> Manipulação e análise de dados./n
<b>streamlit:</b> Criação do dashboard/n
<b>plotly.express:</b> Visualização de dados com gráficos.

<hr>
<br>

<h1>Estrutura do Código</h1>
O código do projeto está estruturado da seguinte maneira:

<h2><b>Carregamento dos Dados</b></h2>
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

<h2><b>Configuração do Streamlit</b></h2>
Definindo o título principal do dashboard.

```python
import streamlit as st
import plotly.express as px

st.title("Dashboard: Top 100 TikTokers em 2025")
```

<br>

<h2><b>Criação de Abas</b></h2>
Faço a criação detrês abas principais para organizar as análises.

```python
aba1, aba2, aba3 = st.tabs(["Visão Geral", "Análise de Engajamento", "Comparação de Influenciadores"])
```

<br>

<h1>Análises Implementadas</h1>

<h2><b>Visão Geral</b></h2>
Esta aba apresenta uma visão geral das métricas dos TikTokers:

<h3><b>Gráfico de dispersão Seguidores vs. Curtidas</b></h3>

```python
fig = px.scatter(df, x='Followers', y='Likes', hover_data=['Username'],
                     title='Relação entre Seguidores e Curtidas',
                     labels={'Followers': 'Seguidores', 'Likes': 'Curtidas'})
    st.plotly_chart(fig)
```
![Graf 1 pag 1](https://github.com/user-attachments/assets/0cc208a5-e9aa-48c3-b0fb-38e4b9bc2fdb)

<br>

<h4><b>Top 10 TikTokers por número de seguidores</h4></b>

```python
top_10 = df.nlargest(10, 'Followers')
    fig_bar = px.bar(top_10, x='Username', y='Followers',
                     title='Top 10 TikTokers por Seguidores', text='Followers')
    st.plotly_chart(fig_bar)
```
![Graf 2 pag 1](https://github.com/user-attachments/assets/4cab6e6b-b77f-4e6f-a8c0-3df190fbf29a)

<br>

<h3><b>Top 10 TikTokers por uploads</b></h3>

```python
top_10_uploads = df.nlargest(10, 'Uploads')
    fig_uploads = px.bar(top_10_uploads, x='Username', y='Uploads',
                          title='Top 10 TikTokers por Uploads', text='Uploads')
    st.plotly_chart(fig_uploads)
```
![Graf 3 pag 1](https://github.com/user-attachments/assets/449771a0-d84e-407c-87c1-9690577485eb)

<br>

<h2><b>Análise de Engajamento</b></h2>
Foca na relação entre curtidas e seguidores:

<h3><b>Taxa de engajamento (curtidas/seguidores)</b></h3>

```python
df['Engajamento'] = df['Likes'] / df['Followers']
    fig_eng = px.scatter(df, x='Followers', y='Engajamento', hover_data=['Username'],
                          title='Engajamento por Número de Seguidores',
                          labels={'Engajamento': 'Taxa de Engajamento'})
    st.plotly_chart(fig_eng)
```
![Graf 1 pag 2](https://github.com/user-attachments/assets/dcef0d09-1d18-40e8-8cb6-f6a66bf30138)

<br>

<h3><b>Distribuição da taxa de engajamento</b></h3>

```python
fig_hist = px.histogram(df, x='Engajamento', nbins=20,
                            title='Distribuição da Taxa de Engajamento')
    st.plotly_chart(fig_hist)
```
![Graf 2 pag 2](https://github.com/user-attachments/assets/60c8b05a-e35c-42b4-9ac8-904db1704b94)

<br>

<h3><b>Boxplot da taxa de engajamento</b></h3>

```python
fig_box = px.box(df, y='Engajamento', title='Boxplot da Taxa de Engajamento')
    st.plotly_chart(fig_box)
```
![Graf 3 pag 2](https://github.com/user-attachments/assets/8cd5f136-2749-405f-8631-405c16a083b1)

<br>

<h2><b>Comparação de Influenciadores</b></h2>
Permite a seleção de múltiplos influenciadores para comparação direta:

![Graf 1 pag 3](https://github.com/user-attachments/assets/4dca6e05-fca9-476d-97fd-494c7b9d02c3)

<br>

<h3><b>Comparação de seguidores, curtidas e uploads</b></h3>

```python
 options = st.multiselect("Escolha os TikTokers para comparar:", df['Username'])
    df_selected = df[df['Username'].isin(options)]
    if not df_selected.empty:
        fig_compare = px.bar(df_selected, x='Username', y=['Followers', 'Likes', 'Uploads'],
                             title='Comparação de Métricas', barmode='group')
        st.plotly_chart(fig_compare)
```
![Graf 2 pag 3](https://github.com/user-attachments/assets/1d5741cb-e369-4e47-8457-079eeb01d992)

<br>

<h3><b>Relação entre seguidores e uploads</b></h3>

```python
 fig_scatter = px.scatter(df_selected, x='Followers', y='Uploads', hover_data=['Username'],
                                 title='Seguidores vs Uploads')
        st.plotly_chart(fig_scatter)
```
![Graf 3 pag 3](https://github.com/user-attachments/assets/fb851a81-ddeb-4960-b43f-909c8741da48)

<br>

<h3><b>Relação entre curtidas e uploads</b></h3>

```python
fig_scatter2 = px.scatter(df_selected, x='Likes', y='Uploads', hover_data=['Username'],
                                  title='Curtidas vs Uploads')
        st.plotly_chart(fig_scatter2)

```
![Graf 4 pag 3](https://github.com/user-attachments/assets/0c838be4-5079-4a99-ba78-ece16bf47bb3)


<hr>
<br>

<h1>Possíveis Melhorias</h1>

Adicionar mais métricas como taxa de crescimento de seguidores.
Implementação de um filtro para visualizar influenciadores por categoria.
Criação de um ranking dinâmico baseado no engajamento.

<hr>
