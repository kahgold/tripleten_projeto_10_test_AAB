# Projeto: Projeto Integrado 2

Você trabalha em uma startup que vende produtos alimentícios. Você precisa analisar o comportamento do usuário para o aplicativo da sua empresa. É um projeto integrado que combina todas as disciplinas anteriores, principalmente Business Analytics, Teste A/B e Data Storytelling.

Como analista de dados de uma startup que vende produtos alimentícios, é essencial entender o comportamento do usuário no aplicativo da empresa. Neste projeto, investigaremos o **funil de vendas** e estudaremos o **comportamento do usuário** usando um **teste A/A/B** para ver como as **alterações na fonte do aplicativo** irão ** impactar o envolvimento do usuário**. Começaremos analisando o funil de vendas para entender como os usuários **chegam ao estágio de compra**, quantos usuários chegam a esse estágio e **quais estágios apresentam mais desistências**. Em seguida, passaremos para o teste A/A/B, onde os usuários são divididos em três grupos: dois grupos de controle que recebem as fontes antigas e um grupo de teste que recebe as novas fontes. Determinaremos **qual** conjunto de fontes **produz melhores resultados** e confirmaremos se os grupos de teste foram divididos corretamente.

Usaremos um conjunto de dados que combina dados gerais e dados de análise A/A/B para conduzir nosso estudo. Este projeto testará nossas habilidades em limpeza de dados, visualização de dados, teste de hipóteses e estatística. Vamos nos aprofundar e ver quais insights podemos descobrir com essa análise.

Para concluir este projeto, precisaremos realizar as seguintes etapas:
- **Abra o arquivo de dados e leia as informações gerais**.
- **Prepare os dados para análise** renomeando colunas, verificando valores ausentes e corrigindo tipos de dados. Adicione uma coluna de data e hora e uma coluna separada para datas.
- Estude e verifique os dados para determinar:
    - o **número de eventos e usuários nos logs**,
    - o **número médio de eventos por usuário**, e
    - o **período de tempo que os dados cobrem**.
    - Trace um **histograma** por data e hora para determinar se você tem dados igualmente completos para todo o período. Encontre o momento em que os dados começam a ficar completos e ignore a seção anterior. Certifique-se de ter usuários de todos os três grupos experimentais.
- Estude o **funil de eventos** determinando:
    - a **frequência de ocorrência de cada evento** nos registros,
    - o **número de usuários que realizaram cada ação**, e
    - a **proporção** de usuários que **realizaram** cada ação **pelo menos uma vez**.
    - Use o funil de eventos para **encontrar a parcela de usuários que passam de cada etapa** para a próxima. Identifique o **estágio em que você perde mais usuários** e **determine a parcela de usuários que fazem toda a jornada** desde o primeiro evento até o pagamento.
- Estudar os resultados do experimento determinando o **número de usuários em cada grupo**, verificando uma **diferença estatisticamente significativa entre as amostras** 246 e 247, e **comparando os resultados** do grupo com alterações fontes para aquelas dos grupos de controle. Calcule o **nível de significância** e determine o número de testes de hipóteses estatísticas que você realizou. Se necessário, ajuste o nível de significância e repita os passos anteriores.
**Data dictionary**

**A tabela logs_exp_us:**
- `EventName` — nome do evento
- `DeviceIDHash` — identificador exclusivo do usuário
- `EventTimestamp` — hora do evento
- `ExpId` — número do experimento: 246 e 247 são os grupos de controle, 248 é o grupo de teste

**Conclusões**

- O **objetivo deste projeto** é **investigar o funil de vendas** e estudar o comportamento do usuário usando um **teste A/A/B** para ver como **as alterações na fonte do aplicativo afetam o envolvimento do usuário**.
- Alguns **pré-processamentos** de dados foram realizados, como **renomear colunas**, **substituir valores** por nomes mais práticos, bem como **converter** algumas colunas nos **tipos de dados apropriados **. Havia alguns **dados duplicados**, mas foram **removidos** e **não havia dados faltantes**.
- A **exploração de dados** preliminar revela que nosso dataframe **contém** alguns **dados desnecessários** anteriores ao período de teste. A remoção desses dados **removeu apenas 1,16% dos eventos** que ocorreram e **0,23% dos usuários**. Este número é insignificante em comparação com os dados totais e não distorcerá os resultados da análise.
- **Análise de funil de eventos**:
    - **Os usuários seguem uma rota semelhante** da tela principal aparece -> tela de ofertas aparece -> tela do carrinho aparece -> tela de pagamento bem-sucedida.
    - A etapa com **maior perda fica entre a primeira e a segunda**, com quase 39% dos usuários (mais de 2.826 id únicos) não conseguindo avançar para o próximo nível.
    - Mais de **47% dos usuários passam por toda a jornada** da tela principal para efetuar um pagamento com sucesso.
- **Teste A/A/B**:
    - **Teste Mann Whitney U** é usado neste projeto
    - O resultado do teste demonstra como o **grupo de teste superou o grupo de controle** em termos de **visitantes** (aparece a tela principal) e **usuários interessados** (aparece a tela de ofertas). No entanto, a alteração da fonte não deve ter efeito nesta fase do funil do evento porque não tem efeito em convencer os usuários iniciantes a usar o aplicativo e prosseguir para a página de ofertas.
    - O teste revela que o **grupo de teste falhou** em ter um aumento que é suficiente **para ultrapassar o limite significativo** em termos de ***usuários Adicionar ao carrinho*** (a tela do carrinho aparece) e ***Compradores*** (tela de pagamento bem-sucedida).
    - O valor de conversão do grupo de teste também não mostra qualquer incremento em comparação com o do grupo de controle.
- **Os testes A/A/B provaram que alterar a fonte do aplicativo não tem o impacto positivo esperado no envolvimento do usuário**.
