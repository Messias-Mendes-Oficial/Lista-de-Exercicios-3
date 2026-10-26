# Diário de Bordo — Uso de IA

* **Disciplina:** Teoria dos Grafos — Lista 3 (Caminhos mínimos: Dijkstra, Bellman-Ford e Floyd-Warshall • 3º Período — 2026/2 • Prof. Newarney T. Costa)
* **Dupla:** Messias Junio da Silva Mendes + Bruno Alves Mendonça De Abreu Filho
* **Chat utilizado:** Gemini / ChatGPT

## Entrada 1 — 25/10/2026 (21:30 – 22:30)

* **Questão(ões):** Questão 1 — Algoritmo de Dijkstra (funcionamento, limitações com pesos negativos, tabela manual passo a passo e implementação da matriz simétrica e relaxamento).
* **Onde travamos / objetivo da conversa:** Queríamos conferir a ordem exata de fechamento dos vértices na tabela manual (especialmente quando o caminho $a \to c \to b$ de peso $2+1=3$ melhora a estimativa inicial $a \to b$ de peso $4$) e completar a condição de relaxamento no esqueleto em C e Python.
* **O que perguntamos ao tutor (resumo):** Perguntamos por que a escolha gulosa de Dijkstra falha na presença de arestas negativas e pedimos para validar nossa condição `if (!visitado[v] && grafo[u][v] && dist[u] != INT_MAX && dist[u] + grafo[u][v] < dist[v])` no código.
* **O que o tutor respondeu ou perguntou (resumo):** O tutor questionou a cada passo *"qual vértice aberto tem a menor distância?"*, confirmando a ordem de fechamento $a(0) \to c(2) \to b(3) \to d(8) \to e(10) \to f(13)$, e explicou que proteger `dist[u] != INT_MAX` evita overflow inteiro em C antes de somar `dist[u] + grafo[u][v]`.
* **O que fizemos com isso (aceitamos? questionamos? corrigimos?):** Montamos a matriz de adjacência simétrica $6 \times 6$ (lembrando que o grafo é não orientado, logo `grafo[i][j] = grafo[j][i]`), rodamos no Google Colab e reconstruímos a trilha de antecessores $f \leftarrow e \leftarrow d \leftarrow b \leftarrow c \leftarrow a$.
* **A IA tentou dar a resposta pronta ou errou? Como percebemos e reagimos?** No início, pedimos que validasse uma iteração por vez em vez de gerar a tabela inteira de uma só vez, conferindo manualmente cada atualização de antecessor.
* **O que aprendemos:** Entendemos como o fecho guloso garante otimalidade apenas quando pesos são não negativos e como traduzir um grafo não orientado ponderado para matriz simétrica.

## Entrada 2 — 25/10/2026 (22:30 – 23:45)

* **Questão(ões):** Questão 2 — Algoritmo de Bellman-Ford (pesos negativos, detecção de ciclo negativo e implementação em C/Python).
* **Onde travamos / objetivo da conversa:** Na aplicação manual a partir de $A$, notamos que na 1ª iteração o arco $D \to F(2)$ foi avaliado antes do arco negativo $E \to D(-3)$, deixando `dist[F] = 7` no fim da 1ª rodada e só caindo para `dist[F] = 3` na 2ª rodada. Queríamos confirmar se esse comportamento dependia da ordem das arestas.
* **O que perguntamos ao tutor (resumo):** Perguntamos por que foram necessárias 2 iterações para `dist[F]` convergir para 3 e como implementar o laço da $V$-ésima verificação de ciclo negativo.
* **O que o tutor respondeu ou perguntou (resumo):** Explicou que cada iteração $k$ do Bellman-Ford garante os caminhos mínimos com até $k$ arestas independentemente da ordem de listagem, mas como o caminho ótimo $A \to C \to E \to D \to F$ possui 4 arestas e `E -> D(-3)` aparece depois de `D -> F(2)` no vetor de arestas, a redução de `dist[D]` para 1 só se propaga para `F` na 2ª iteração.
* **O que fizemos com isso (aceitamos? questionamos? corrigimos?):** Implementamos no Colab um rastreador que imprime o vetor `dist[]` e `ant[]` após cada uma das $V-1 = 5$ iterações, comprovando que da 2ª à 5ª iteração os valores permanecem estáveis em `[0, 4, 2, 1, 4, 3]` e que a verificação de ciclo negativo retorna falso.
* **A IA tentou dar a resposta pronta ou errou? Como percebemos e reagimos?** Verificamos manualmente cada um dos 9 arcos na ordem exata do vetor `struct Edge arestas[E]` fornecido no enunciado.
* **O que aprendemos:** Compreendemos na prática por que Bellman-Ford precisa de até $V-1$ rodadas para propagar reduções geradas por arcos negativos como $E \to D(-3)$ sem sofrer do problema de fechamento precoce do Dijkstra.

## Entrada 3 — 26/10/2026 (00:00 – 01:00)

* **Questão(ões):** Questão 3 (Floyd-Warshall — todos os pares) e Comparação Geral (Dijkstra $\times$ Bellman-Ford $\times$ Floyd-Warshall).
* **Onde travamos / objetivo da conversa:** Ao calcular as matrizes $D^{(k)}$ à mão no Floyd-Warshall, percebemos que existiam múltiplos caminhos empatados com distância 9 entre $A$ e $F$ ($A \to C \to D \to E \to F$, $A \to C \to E \to F$ e $A \to B \to D \to E \to F$). Queríamos conferir a evolução da matriz de roteamento/predecessores para cada $k = 0..5$.
* **O que perguntamos ao tutor (resumo):** Pedimos para verificar em quais valores de $k$ a matriz $D^{(k)}$ efetivamente sofre alterações e como estruturar a matriz de roteamento para recuperar o caminho de $A$ até $F$.
* **O que o tutor respondeu ou perguntou (resumo):** Mostrou passo a passo as atualizações para $k=1 (B)$, $k=2 (C)$, $k=3 (D)$ e $k=4 (E)$ (sendo que para $k=0 (A)$ e $k=5 (F)$ nenhuma entrada muda, pois $A$ não tem arcos de entrada e $F$ não tem arcos de saída), e explicou como usar `dist[i][k] + dist[k][j] < dist[i][j]` para manter o primeiro caminho ótimo descoberto.
* **O que fizemos com isso (aceitamos? questionamos? corrigimos?):** Programamos a impressão das 6 matrizes $D^{(k)}$ e da matriz de roteamento no Google Colab e sintetizamos o quadro comparativo final dos três algoritmos.
* **A IA tentou dar a resposta pronta ou errou? Como percebemos e reagimos?** Conferimos se a condição em C evitava soma com `INF` (ou se `INF = 99999` era seguro contra overflow de `int`) e validamos todas as células da matriz $6 \times 6$.
* **O que aprendemos:** Dominamos a programação dinâmica sobre vértices intermediários $k$ do Floyd-Warshall ($\Theta(V^3)$) e os critérios práticos para escolher entre Dijkstra, Bellman-Ford e Floyd-Warshall.

## Reflexão Final (~½ página)

* **Onde a IA mais ajudou:** A IA foi excelente para instrumentar os códigos em **Python** e **C** no **Google Colab** de modo a imprimir não apenas a saída final pedida no esqueleto, mas também o estado intermediário de cada iteração (a tabela de vértices abertos/fechados no Dijkstra, os vetores `dist[]` das 5 rodadas no Bellman-Ford e as 6 matrizes $D^{(k)}$ no Floyd-Warshall). Isso tornou a conferência do trabalho manual muito mais segura e visual.
* **Onde ela atrapalhou ou tentou entregar a resposta pronta:** Ao consultar sobre a evolução das tabelas de relaxamento, chatbots costumam exibir imediatamente a resposta final. Contornamos isso utilizando a recomendação da própria lista (*"qual vértice aberto tem a menor distância?"*) e exigindo o rastreamento na ordem exata das estruturas de dados do código do professor.
* **Onde ela errou e como verificamos:** Na Questão 1, é preciso atenção redobrada ao fato de o grafo ser **não orientado** (exigindo matriz de adjacência simétrica `grafo[i][j] = grafo[j][i]`), enquanto nas Questões 2 e 3 os grafos são **orientados**. Além disso, na Questão 3 há três caminhos distintos de custo mínimo 9 entre $A$ e $F$; verificamos à mão como a desigualdade estrita (`<` vs `<=`) define qual desses caminhos ótimos fica registrado na matriz de roteamento.
* **O que faríamos diferente na próxima lista:** Continuaremos combinando o teste de mesa manual com scripts de verificação passo a passo no Google Colab, garantindo que cada linha de código (`TODO`) seja compreendida tanto na teoria quanto na execução real em C e Python.
