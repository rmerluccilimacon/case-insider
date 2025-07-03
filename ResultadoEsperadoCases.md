#### 1. Ativação e Engajamento de Clientes Recém-Conquistados

* **Solução com a CDP:**
    * **Dados Utilizados:** Dados de produtos de cartão (evento de "Entrega de Cartão", "Ativação de Cartão") e dados de financiamento (status "Aprovado").
    * **Mecanismo:** A CDP, ao receber o evento de "Entrega de Cartão" ou alteração de status de financiamento para "Aprovado", pode identificar automaticamente esses clientes.
    * **Jornada de Ação:** Envio de **comunicações proativas** (e-mails, SMS, notificações push) com instruções claras para ativação do cartão ou próximos passos do financiamento. Se o cliente não ativar o cartão em "X" dias, a CDP pode acionar uma ligação do call center ou uma notificação mais insistente.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **API de Eventos em Tempo Real:** Para "Ativação de Cartão" e "Entrega de Cartão". Dada a necessidade de ações imediatas, a ingestão via API garante que a CDP seja atualizada no exato momento do evento, acionando a jornada sem latência.
    * **Ingestão Batch Diária:** Para "Financiamento Aprovado" (se o sistema fonte não permitir tempo real, ou se o volume for alto para API contínua). Os dados de financiamento são gerados diariamente, então um processo batch noturno ou pela manhã seria eficiente para popular os perfis na CDP e iniciar as jornadas no dia seguinte.
* **Resultado Esperado:** Aumento das taxas de ativação de cartões, maior engajamento inicial com produtos financeiros e redução da inatividade pós-aprovação.

#### 2. Prevenção de Churn e Retenção de Clientes

* **Solução com a CDP:**
    * **Dados Utilizados:** Dados cadastrais (histórico do cliente), dados de produtos de cartão (eventos de "Cancelamento de Cartão", histórico de uso, transações decrescentes) e dados de financiamento (pagamentos em atraso, interesse em quitação antecipada).
    * **Mecanismo:** A CDP pode criar **segmentos dinâmicos de "risco de churn"** com base em múltiplos sinais. Por exemplo, um cliente que reduziu drasticamente o uso do cartão, não acessa o aplicativo há um tempo, ou tem um histórico de pagamentos atrasados.
    * **Jornada de Ação:** Acionamento de **ofertas de retenção personalizadas** (ex: redução de anuidade, taxa de juros diferenciada) ou direcionamento para uma equipe de atendimento especializada para contato proativo.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **Ingestão Batch Diária/Horária:** Para a atualização de dados cadastrais e de financiamento (pagamentos em atraso, status). A periodicidade deve ser suficiente para permitir a identificação precoce de padrões de churn.
    * **API de Eventos (para eventos de alto risco):** Para eventos como "Cancelamento de Cartão" (se houver um gatilho pré-cancelamento) ou "Solicitação de Quitação Antecipada". A interação em tempo real permite uma reação mais rápida para tentar reverter a decisão.
* **Resultado Esperado:** Redução da taxa de cancelamento de produtos, aumento da satisfação do cliente e manutenção da base de clientes valiosos.

#### 3. Cross-Sell e Up-Sell de Produtos Financeiros

* **Solução com a CDP:**
    * **Dados Utilizados:** Todos os dados unificados (cadastrais, histórico de produtos de cartão e financiamento, comportamento de navegação no site/app). A CDP pode usar Machine Learning para inferir a **propensão de compra** de outros produtos.
    * **Mecanismo:** A CDP pode criar segmentos como: "Clientes com financiamento aprovado e perfil de renda compatível com investimento", "Clientes com cartão básico que acessam páginas de cartão premium", ou "Clientes com bom histórico de crédito e sem empréstimos ativos".
    * **Jornada de Ação:** Disparar **campanhas personalizadas** em e-mail, SMS, notificações in-app ou banners no site, oferecendo produtos complementares (ex: seguro de cartão, linhas de crédito pré-aprovadas). Clientes com alta propensão a adquirir um produto complexo podem ser identificados como leads qualificados para a equipe de vendas.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **Ingestão Batch Diária:** Para atualização de dados cadastrais, financeiros e de produtos de cartão, que alimentam os modelos de propensão e a segmentação. A periodicidade diária permite que as ofertas sejam atualizadas com base nos dados mais recentes.
    * **API de Atributos/Eventos (para interações específicas):** Se o cliente interage com uma ferramenta de simulação de produtos no site ou demonstra interesse explícito (um "clique" em um CTA de "saiba mais" sobre um novo produto), um evento via API pode ser disparado para atualizar seu perfil e acionar uma jornada imediata de *cross-sell*.
* **Resultado Esperado:** Aumento da taxa de conversão em campanhas de cross-sell/up-sell, crescimento da carteira de produtos por cliente (Wallet Share) e otimização do ROI em marketing.