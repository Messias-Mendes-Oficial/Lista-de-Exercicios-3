# Lista 3: Caminhos Mínimos (Dijkstra, Bellman-Ford e Floyd-Warshall)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Messias-Mendes-Oficial/Lista-de-Exercicios-3/blob/main/codigo/Lista_3_Teoria_dos_Grafos.ipynb)

📄 **Documentação e Relatórios**

* [Ver Código Completo e Execução no Google Colab](https://colab.research.google.com/github/Messias-Mendes-Oficial/Lista-de-Exercicios-3/blob/main/codigo/Lista_3_Teoria_dos_Grafos.ipynb)
* [Diário de Bordo — Uso de IA](./Di%C3%A1rio%20de%20Bordo%20%E2%80%94%20Uso%20de%20IA)
* [Resolução Oficial em PDF (`respostas/`)](./respostas)
* [Figuras e Gráficos Gerados (`prints/`)](./prints)

Este repositório contém a resolução da **Lista de Exercícios 3** da disciplina de **Teoria dos Grafos** (3º Período — 2026/2), ministrada pelo **Prof. Newarney T. Costa** no **Instituto Federal Goiano — Campus Iporá** (Bacharelado em Ciência da Computação).

O objetivo principal deste trabalho é compreender, aplicar passo a passo e implementar (em **Python** e **C** no **Google Colab**) os três algoritmos clássicos de **Caminhos Mínimos**:
1. **Algoritmo de Dijkstra** (*um-para-todos* em grafos com pesos não negativos);
2. **Algoritmo de Bellman-Ford** (*um-para-todos* em grafos com arestas de peso negativo e detecção de ciclos negativos);
3. **Algoritmo de Floyd-Warshall** (*todos-os-pares* via programação dinâmica matricial e matriz de roteamento).

## 👥 Integrantes

* **Messias Junio da Silva Mendes** (Messias-Mendes-Oficial) | **Bruno Alves Mendonça De Abreu Filho**

## 🛠️ Tecnologias Utilizadas

* **Python 3** (Implementação completa dos esqueletos de Dijkstra, Bellman-Ford e Floyd-Warshall no Google Colab)
* **Linguagem C (`gcc`)** (Implementação e compilação via `!gcc` no Google Colab dos esqueletos em C fornecidos na lista)
* **Google Colab** (Ambiente de execução interativo em nuvem)
* **Matplotlib & NumPy** (Visualização dos grafos ponderados, árvores de caminhos mínimos e matrizes de distância)

## 📂 Estrutura do Repositório

| Caminho / Arquivo | Descrição |
| :--- | :--- |
| `codigo/Lista_3_Teoria_dos_Grafos.ipynb` | Notebook principal configurado para rodar 100% no **Google Colab**, contendo a resolução, rastreamento passo a passo e execução em Python e C das Questões 1, 2, 3 e Comparação Final. |
| `codigo/*.c` | Arquivos-fonte individuais em C (`dijkstra.c`, `bellman_ford.c`, `floyd_warshall.c`) prontos para compilação com `gcc`. |
| `prints/` | Imagens geradas pelo notebook ilustrando os grafos e caminhos mínimos de cada questão (`q01_dijkstra_grafo_caminho.png`, `q02_bellman_ford_pesos_negativos.png`, `q03_floyd_warshall_grafo_matriz.png`). |
| `respostas/` | Documento oficial em PDF (`Respostas_Lista_3_Teoria_dos_Grafos.pdf`) contendo a resolução completa e integralmente digitada de todas as questões da dupla, em conformidade com as adaptações acadêmicas de acessibilidade. |
| `Diário de Bordo — Uso de IA` | Registro detalhado por sessão de trabalho do uso de IA e reflexão crítica (~½ página). |
| `LICENSE` | Licença MIT do repositório. |
| `README.md` | Documentação geral e guia de execução do projeto. |

## 📋 Resumo dos Resultados Obtidos

| Questão / Algoritmo | Escopo e Complexidade | Resultado no Grafo Proposto |
| :--- | :--- | :--- |
| **1. Dijkstra** | Um-para-todos (pesos $\ge 0$)<br>Matriz: $O(V^2)$ \| Heap: $O((V+E)\log V)$ | **Distâncias a partir de `a` (0):** `a:0, b:3, c:2, d:8, e:10, f:13`<br>**Caminho mínimo `a → f`:** $a \xrightarrow{2} c \xrightarrow{1} b \xrightarrow{5} d \xrightarrow{2} e \xrightarrow{3} f$ (**Custo = 13**) |
| **2. Bellman-Ford** | Um-para-todos (aceita pesos negativos; detecta ciclo negativo)<br>Tempo: $O(V \cdot E)$ | **Distâncias a partir de `A` (0):** `A:0, B:4, C:2, D:1, E:4, F:3` (converge na 2ª iteração)<br>**Caminho mínimo `A → F`:** $A \xrightarrow{2} C \xrightarrow{2} E \xrightarrow{-3} D \xrightarrow{2} F$ (**Custo = 3**)<br>**Ciclo negativo:** Não existe. |
| **3. Floyd-Warshall** | Todos-os-pares (aceita pesos negativos sem ciclo negativo)<br>Tempo: $\Theta(V^3)$ \| Espaço: $\Theta(V^2)$ | **Menor distância de `A` até `F`:** **9**<br>**Caminhos mínimos equivalentes (custo 9):**<br>• $A \xrightarrow{2} C \xrightarrow{4} D \xrightarrow{1} E \xrightarrow{2} F$<br>• $A \xrightarrow{2} C \xrightarrow{5} E \xrightarrow{2} F$<br>• $A \xrightarrow{4} B \xrightarrow{2} D \xrightarrow{1} E \xrightarrow{2} F$ |

## 🚀 Como Executar no Google Colab

1. Clique no botão **Open in Colab** no topo deste `README.md` (ou abra `codigo/Lista_3_Teoria_dos_Grafos.ipynb`).
2. No menu superior do Google Colab, selecione **Ambiente de execução > Executar tudo** (`Ctrl + F9`).
3. Todas as células em **Python 3** e as compilações em **C (`gcc`)** serão executadas automaticamente exibindo as tabelas de iteração, matrizes intermediárias e gráficos.
