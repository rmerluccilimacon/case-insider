Certo! Adicionei ao escapé e aos casos de uso a melhor forma de interação com a plataforma Insider CDP, considerando as necessidades específicas de cada tipo de dado e objetivo.

---

## Case de Ingestão de Dados para a Insider CDP: Instituição Financeira

Este documento detalha o processo de ingestão de dados para uma instituição financeira na plataforma Insider Customer Data Platform (CDP). O objetivo é unificar e normalizar dados de diversas fontes, garantindo um perfil de cliente 360° robusto e acionável.

---

### Etapas de Implementação

A implementação da Insider CDP para este caso de uso será dividida em quatro etapas principais, garantindo um fluxo de trabalho organizado e eficiente:

1.  **Criação do Ambiente:**
    * **Download do Projeto do Git:** Obtenção do código-fonte e estruturas iniciais para a ingestão de dados.
    * **Parametrização do Projeto:** Configuração de variáveis e ajustes específicos para o ambiente da instituição financeira.
    * **Geração de Credenciais de API da Insider:** Obtenção das chaves de acesso necessárias para a comunicação segura com a plataforma CDP.

2.  **Estruturação dos Dados:**
    * **Limpeza:** Identificação e correção de erros, inconsistências e dados faltantes nas bases de origem.
    * **Tratamento de Duplicatas:** Eliminação de registros repetidos para garantir a unicidade do perfil do cliente.
    * **Normalização de Dados:** Padronização dos formatos de dados (ex: datas, endereços, telefones) para assegurar a consistência e a interoperabilidade.

3.  **Ingestão dos Dados na Plataforma:**
    * Envio dos dados processados das três bases de dados para a Insider CDP, utilizando os métodos de ingestão apropriados (ex: API, batch).
    * Configuração dos mapeamentos de campos para que os dados sejam corretamente atribuídos aos atributos do perfil do cliente na CDP.

4.  **Criação das Jornadas:**
    * Desenvolvimento e configuração de fluxos de automação (jornadas do cliente) dentro da plataforma Insider.
    * Estas jornadas serão desenhadas para **atender diretamente aos casos de uso** definidos, acionando comunicações e ações personalizadas em tempo real ou programadas.

---

### Casos de Uso para o Cenário da Instituição Financeira

A implementação da Insider CDP habilita uma série de casos de uso estratégicos, permitindo à instituição financeira otimizar a experiência do cliente e impulsionar resultados de negócios. Abaixo, destacamos 3 cenários-chave:

#### 1. Ativação e Engajamento de Clientes Recém-Conquistados

* **Problema:** Clientes que recebem um novo cartão ou têm um financiamento aprovado nem sempre ativam ou utilizam o produto imediatamente, resultando em receita perdida e oportunidades de engajamento desaproveitadas.
* **Solução com a CDP:**
    * **Dados Utilizados:** Dados de produtos de cartão (evento de "Entrega de Cartão", "Ativação de Cartão") e dados de financiamento (status "Aprovado").
    * **Mecanismo:** A CDP, ao receber o evento de "Entrega de Cartão" ou alteração de status de financiamento para "Aprovado", pode identificar automaticamente esses clientes.
    * **Jornada de Ação:** Envio de **comunicações proativas** (e-mails, SMS, notificações push) com instruções claras para ativação do cartão ou próximos passos do financiamento. Se o cliente não ativar o cartão em "X" dias, a CDP pode acionar uma ligação do call center ou uma notificação mais insistente.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **API de Eventos em Tempo Real:** Para "Ativação de Cartão" e "Entrega de Cartão". Dada a necessidade de ações imediatas, a ingestão via API garante que a CDP seja atualizada no exato momento do evento, acionando a jornada sem latência.
    * **Ingestão Batch Diária:** Para "Financiamento Aprovado" (se o sistema fonte não permitir tempo real, ou se o volume for alto para API contínua). Os dados de financiamento são gerados diariamente, então um processo batch noturno ou pela manhã seria eficiente para popular os perfis na CDP e iniciar as jornadas no dia seguinte.
* **Resultado Esperado:** Aumento das taxas de ativação de cartões, maior engajamento inicial com produtos financeiros e redução da inatividade pós-aprovação.

#### 2. Prevenção de Churn e Retenção de Clientes

* **Problema:** Dificuldade em identificar clientes em risco de cancelar serviços (cartão, financiamento) antes que a decisão seja final, o que impede intervenções proativas para retenção.
* **Solução com a CDP:**
    * **Dados Utilizados:** Dados cadastrais (histórico do cliente), dados de produtos de cartão (eventos de "Cancelamento de Cartão", histórico de uso, transações decrescentes) e dados de financiamento (pagamentos em atraso, interesse em quitação antecipada).
    * **Mecanismo:** A CDP pode criar **segmentos dinâmicos de "risco de churn"** com base em múltiplos sinais. Por exemplo, um cliente que reduziu drasticamente o uso do cartão, não acessa o aplicativo há um tempo, ou tem um histórico de pagamentos atrasados.
    * **Jornada de Ação:** Acionamento de **ofertas de retenção personalizadas** (ex: redução de anuidade, taxa de juros diferenciada) ou direcionamento para uma equipe de atendimento especializada para contato proativo.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **Ingestão Batch Diária/Horária:** Para a atualização de dados cadastrais e de financiamento (pagamentos em atraso, status). A periodicidade deve ser suficiente para permitir a identificação precoce de padrões de churn.
    * **API de Eventos (para eventos de alto risco):** Para eventos como "Cancelamento de Cartão" (se houver um gatilho pré-cancelamento) ou "Solicitação de Quitação Antecipada". A interação em tempo real permite uma reação mais rápida para tentar reverter a decisão.
* **Resultado Esperado:** Redução da taxa de cancelamento de produtos, aumento da satisfação do cliente e manutenção da base de clientes valiosos.

#### 3. Cross-Sell e Up-Sell de Produtos Financeiros

* **Problema:** Dificuldade em identificar os clientes mais propensos a adquirir novos produtos ou fazer um *upgrade* de seus serviços, resultando em campanhas genéricas e baixa taxa de conversão.
* **Solução com a CDP:**
    * **Dados Utilizados:** Todos os dados unificados (cadastrais, histórico de produtos de cartão e financiamento, comportamento de navegação no site/app). A CDP pode usar Machine Learning para inferir a **propensão de compra** de outros produtos.
    * **Mecanismo:** A CDP pode criar segmentos como: "Clientes com financiamento aprovado e perfil de renda compatível com investimento", "Clientes com cartão básico que acessam páginas de cartão premium", ou "Clientes com bom histórico de crédito e sem empréstimos ativos".
    * **Jornada de Ação:** Disparar **campanhas personalizadas** em e-mail, SMS, notificações in-app ou banners no site, oferecendo produtos complementares (ex: seguro de cartão, linhas de crédito pré-aprovadas). Clientes com alta propensão a adquirir um produto complexo podem ser identificados como leads qualificados para a equipe de vendas.
* **Melhor Forma de Interagir com a Plataforma para este Caso:**
    * **Ingestão Batch Diária:** Para atualização de dados cadastrais, financeiros e de produtos de cartão, que alimentam os modelos de propensão e a segmentação. A periodicidade diária permite que as ofertas sejam atualizadas com base nos dados mais recentes.
    * **API de Atributos/Eventos (para interações específicas):** Se o cliente interage com uma ferramenta de simulação de produtos no site ou demonstra interesse explícito (um "clique" em um CTA de "saiba mais" sobre um novo produto), um evento via API pode ser disparado para atualizar seu perfil e acionar uma jornada imediata de *cross-sell*.
* **Resultado Esperado:** Aumento da taxa de conversão em campanhas de cross-sell/up-sell, crescimento da carteira de produtos por cliente (Wallet Share) e otimização do ROI em marketing.

---

### Escopo e Fontes de Dados

Para este caso de uso, a instituição financeira possui três fontes de dados distintas que serão unificadas na Insider CDP:

1.  **Dados Cadastrais:** Contêm informações essenciais sobre os clientes.
    * **Conteúdo:** Nome, CPF, endereço, contato (e-mail, telefone), data de nascimento, gênero, entre outros.
    * **Atualização:** Diariamente, com foco nas **atualizações de perfis existentes e novas entradas de clientes**. Isso garante que a CDP sempre tenha a informação cadastral mais recente.
    * **Volume:** Moderado, refletindo o fluxo de novos clientes e alterações cadastrais.
    * **Melhor Forma de Interagir com a Plataforma:** **Ingestão Batch Diária.** Dados cadastrais atualizados uma vez ao dia são suficientes para manter os perfis na CDP precisos, dada a natureza dessas informações.

2.  **Dados de Produtos de Cartão:** Abrangem o ciclo de vida e eventos transacionais relacionados aos cartões de crédito e/ou débito.
    * **Conteúdo:**
        * **Entrega de Cartão:** Confirmação da entrega física ao cliente.
        * **Ativação de Cartão:** Registro da primeira utilização ou ativação formal do cartão.
        * **Cancelamento de Cartão:** Sinalização do encerramento do produto pelo cliente ou pela instituição.
        * **Sugestão de Outros Dados/Eventos:** Transações de compra (data, valor, categoria), pagamentos realizados, alterações de limite, bloqueios e desbloqueios.
    * **Atualização:** **Tempo real**, para capturar eventos críticos e comportamentos do cliente no momento em que ocorrem, permitindo ações imediatas.
    * **Volume:** Elevado e contínuo, dada a alta frequência de interações e transações com cartões.
    * **Melhor Forma de Interagir com a Plataforma:** **API de Eventos.** A natureza em tempo real desses dados demanda uma integração via API para garantir que cada ação do cliente com o cartão (ativação, transação) seja imediatamente registrada na CDP e possa acionar jornadas instantâneas. Para dados históricos ou de menor criticidade, um batch complementar pode ser usado.

3.  **Dados de Financiamento:** Detalham o status e informações relevantes dos contratos de financiamento.
    * **Conteúdo:**
        * **Status de Contratos:**
            * **Em Aprovação:** Contratos aguardando deliberação da instituição.
            * **Aprovados:** Contratos com aprovação concedida e em processo de liberação.
            * **Rejeitados:** Contratos com solicitação negada.
            * **Finalizados:** Contratos com o processo concluído (ex: quitados, encerrados por término de prazo).
        * Outras informações relevantes: Tipo de financiamento, valor do contrato, número de parcelas, valor da parcela, data de início/fim.
    * **Atualização:** Diariamente, com todos os contratos que passaram por alguma mudança de status ou foram criados/finalizados, garantindo uma visão atualizada do portfólio de financiamentos.
    * **Volume:** Moderado a alto, dependendo do volume de operações de crédito da instituição.
    * **Melhor Forma de Interagir com a Plataforma:** **Ingestão Batch Diária.** Como os dados são gerados e atualizados diariamente, um processo de ingestão batch é o mais eficiente para garantir que a CDP tenha as informações mais recentes sobre os status dos financiamentos.

---

### Gatilhos para Entrada em Jornadas (Architect Starter Elements)

A Insider CDP oferece diversos gatilhos (ou "Starter Elements" no Architect) que permitem que um usuário entre em uma jornada de forma flexível e contextualizada. Esses gatilhos são fundamentais para automatizar as interações com base no comportamento e nos dados do cliente. Abaixo, uma breve descrição de cada um:

* **On Event (Ao Acontecer um Evento):** O usuário entra na jornada instantaneamente quando um evento específico é registrado na CDP. Ideal para ações em tempo real, como "Cartão Ativado" ou "Financiamento Aprovado".
* **On Attribute Change (Na Mudança de um Atributo):** O usuário é inserido na jornada quando o valor de um atributo em seu perfil é alterado para um estado específico. Útil para acionar jornadas baseadas em atualizações de dados como "Score de Crédito" ou "Status de Financiamento" para "Atrasado".
* **User Website Action (Na Ação do Usuário no Site/Aplicativo):** O usuário inicia a jornada com base em suas interações no site ou aplicativo móvel. (Ex: Acessar página de cancelamento, visualizar muitas vezes um produto).
* **On Past Behavior (Com Base em Comportamento Passado):** Os usuários são incluídos na jornada com base em padrões de comportamento históricos que atendem a critérios específicos (ex: baixa utilização do cartão, visitas frequentes a páginas de investimento sem conversão).
* **On Dynamic Date (Em uma Data Dinâmica):** Permite que os usuários entrem em uma jornada com base em uma data específica armazenada em seu perfil (ex: aniversário do cliente, data de vencimento de um contrato, data de aniversário do cartão).
* **On Price Drop (Na Queda de Preço):** Aciona o usuário quando o preço de um produto de interesse cai (menos relevante para o caso financeiro puro, mas adaptável para "Queda de Taxa de Juros").
* **On Back in Stock (Quando o Item Volta ao Estoque):** Não aplicável para este caso de uso de instituição financeira.

Para este cenário de instituição financeira, os gatilhos **On Event**, **On Attribute Change**, **On Past Behavior** e **On Dynamic Date** serão os mais relevantes e frequentemente utilizados para construir as jornadas de cliente.

---