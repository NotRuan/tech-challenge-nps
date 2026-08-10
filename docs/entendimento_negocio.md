# Entendimento do Negócio e Definição do Target

## Fase 1 — Entendimento do Negócio

### Qual problema de negócio está sendo resolvido?

Identificação de possíveis detratores e implementação de melhorias de processos para diminuir a possibilidade de um cliente virar um detrator, ao responder a pergunta: qual a probabilidade de um cliente ser definido como detrator e quais as características que reforçam esse comportamento?

### Por que o NPS é importante para um e-commerce?

O Net Promoter Score é importante para um e-commerce devido a sua capacidade de medir a satisfação e fidelidade dos clientes da empresa; ele ajuda a prever o crescimento de vendas e também permite identificar falhas no atendimento ao cliente ou na entrega dos produtos. O NPS torna-se parte fundamental de uma empresa que busca entender o sentimento dos clientes para saber quais têm mais chance de recomprar um produto e estão fidelizados com a empresa.

### Quais áreas poderiam se beneficiar desses insights?

Diversas áreas de uma empresa podem se beneficiar dos insights gerados pela análise do NPS, sendo elas:

- **Logística e Supply Chain**: essa área pode monitorar e analisar gargalos operacionais, como o impacto de entregas divididas ou tempo de mercadorias em trânsito. Por exemplo: se após a análise exploratória dos dados forem encontrados atrasos relevantes na entrega de um produto devido a uma transportadora específica não ter um SLA de entrega adequado, e isso estiver ocasionando um número elevado de detratores, a empresa pode decidir penalizar essa transportadora de alguma forma ou até mesmo redesenhar as rotas de entrega dos produtos.
- **Atendimento ao Cliente (Suporte)**: essa área pode ser responsável por monitorar clientes em zona de risco operacional e identificar, por exemplo, que um cliente que teve uma jornada insatisfatória (como um pedido atrasado) precisa de medidas proativas para que ele não vire um detrator — disponibilizando um cupom de desconto na próxima compra, ou frete grátis.
- **Pricing**: após os insights serem fornecidos, a área de pricing pode perceber que uma campanha de frete grátis com prazos muito extensos ocasiona churn ou prejudica a fidelidade do cliente, sendo possível tomar uma medida proativa para equilibrar quando vale a pena focar em entregas mais rápidas para garantir mais clientes promotores da empresa.

### Reflexão: como o NPS impacta recompra, boca a boca e market share

Podemos confirmar a importância do Net Promoter Score dentro de uma empresa de e-commerce, visto que ele ajuda a identificar gargalos operacionais, clientes em zona de risco operacional e campanhas que podem ser prejudiciais ao negócio se implementadas em momentos errados. O NPS é central na tomada de decisões de uma empresa que deixa de ser reativa (que espera o cliente reclamar ou dar nota baixa) para se tornar proativa (que age com base nas probabilidades e padrões identificados por um modelo de previsão).

Dessa forma, é possível ter resultados coerentes ao identificar clientes fidelizados, aumentando a **recompra** dos produtos da empresa e a previsão de faturamento em determinados períodos. Uma boa análise de NPS ajuda a identificar promotores e detratores, mostrando como está o **boca a boca** da empresa no mercado — uma simples subtração da porcentagem de detratores e de fãs já traz um resultado previsível sobre se o efeito comentado no mercado é bom ou ruim.

Já no **market share** do e-commerce, o NPS permite ver uma análise positiva de quanto a empresa está sendo bem recomendada pelos clientes quando comparada aos concorrentes, permitindo tomar medidas estratégicas, como melhorias no site, promoções ou investimentos em propaganda.

### Quais indicadores de mercado poderiam complementar essa análise?

- **Benchmarks de NPS**, como o Opinion Box, plataforma que possui um benchmark de NPS onde é possível comparar os índices de Net Promoter Score com os de outras empresas do mesmo setor.
- **FCR (First Contact Resolution) de mercado**, que permite verificar a taxa média do setor para resolução de problemas no primeiro contato do cliente. Comparar esse índice com o de outras empresas pode ser vantajoso para identificar se os processos internos estão sendo muito burocráticos — hoje um dos maiores causadores de clientes detratores.

## Fase 2 — Definição do Target

### Qual variável representa a satisfação do cliente?

A variável que representa a satisfação do cliente é a `nps_score`, dentro da nossa base de dados.

### Por que ela foi escolhida?

Essa variável é a que melhor representa a resposta para a pergunta central da empresa: "quais fatores operacionais realmente influenciam a satisfação do cliente e como a empresa pode agir de forma proativa para melhorar a experiência antes mesmo da aplicação da pesquisa de NPS?", visto que podemos treinar um modelo de previsão de NPS para prever a satisfação do cliente com base na experiência que ele teve após a compra dos produtos do e-commerce.

### Em que momento da jornada essa informação é coletada?

O NPS, definido pela variável alvo `nps_score`, é colhido após a experiência de compra do cliente — depois de comprar e receber o produto.

### Existe algum risco de usar essa variável de forma inadequada?

Existem riscos relevantes:

- **Escolha do tipo de modelo**: ao optar por um modelo de regressão para prever uma nota de 0 a 10, o modelo pune erros maiores e menores da mesma forma. Por exemplo, prever uma nota 2 quando o real é 4 tem pouco impacto no negócio; mas prever uma nota 10 quando o cliente na verdade dá 8 tem um grande impacto negativo, pois classificaríamos como promotor (10) um cliente que na verdade é neutro (8). Por esse motivo, modelos de **classificação** (que preveem a categoria do cliente) tendem a ser mais adequados a esse problema de negócio.
- **Data leakage**: ocorre quando o modelo é treinado com dados que não estariam disponíveis no momento real da previsão. A variável `repeat_purchase_30d` é um exemplo de vazamento, pois representa a recompra do cliente até 30 dias após a primeira compra — uma informação que facilitaria a previsão de quem é detrator ou não, mas que não está disponível no momento em que a previsão precisaria ser feita.
