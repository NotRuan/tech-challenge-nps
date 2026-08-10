# Tech Challenge Fase 1 — NPS Preditivo

> 🚧 **Projeto em construção.** Este README será atualizado conforme as próximas etapas (modelo preditivo, apresentação executiva) forem concluídas.

## Objetivo do projeto

Uma empresa de e-commerce coleta o NPS apenas após o encerramento da jornada de compra, o que limita sua capacidade de antecipar problemas e agir de forma proativa. Este projeto busca responder à pergunta de negócio: **quais fatores operacionais realmente influenciam a satisfação do cliente, e como a empresa pode agir antes mesmo da aplicação da pesquisa de NPS?**

O trabalho parte do entendimento do negócio e da definição da variável-alvo, passa por uma análise exploratória de dados (EDA) com foco em negócio, e — na etapa final — propõe uma abordagem de modelo preditivo para antecipar a satisfação do cliente.

## Descrição da base de dados

Base histórica de pedidos, entregas e interações com o atendimento ao cliente (`data/desafio_nps_fase_1.csv`), com 2.500 registros e 19 colunas, cobrindo:

- **Dados do pedido**: valor, quantidade de itens, desconto, parcelamento
- **Dados logísticos**: tempo de entrega, atraso, tentativas de entrega, frete
- **Dados de atendimento**: contatos com o suporte, tempo de resolução, reclamações
- **Indicadores internos**: CSAT interno, recompra em 30 dias
- **Variável-alvo**: `nps_score` — nota de satisfação (0 a 10), coletada após a experiência de compra

## Estrutura do repositório

```
tech-challenge-nps/
├── data/               # base de dados original
├── notebooks/          # EDA e (futuramente) pipeline do modelo preditivo
├── docs/               # entendimento do negócio e definição do target
├── reports/            # apresentação executiva (em construção)
└── models/             # modelo preditivo, caso o desafio opcional seja realizado (em construção)
```

## Metodologia utilizada

🚧 *Seção em construção.*

Até o momento, o projeto cobre:
1. **Entendimento do negócio e definição do target** — ver [`docs/entendimento_negocio.md`](docs/entendimento_negocio.md)
2. **Análise exploratória de dados (EDA)** — ver [`notebooks/EDA.ipynb`](notebooks/EDA.ipynb), estruturada em:
   - Qualidade dos dados
   - Exploração variável por variável
   - Ranking de fatores mais críticos para a satisfação
   - Perfil de detratores
   - Ponto de ruptura na experiência do cliente

Ainda pendente: modelo preditivo (desafio opcional) e apresentação executiva.

## Como reproduzir os resultados

🚧 *Seção em construção — será detalhada com o `requirements.txt` e instruções de ambiente.*

Por ora:
1. Clone o repositório
2. Instale as dependências (pandas, numpy, matplotlib, jupyter)
3. Abra `notebooks/EDA.ipynb` e execute as células em ordem
