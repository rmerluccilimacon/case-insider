

## Case de Ingestão de Dados para a Insider CDP: Instituição Financeira

Este documento detalha o processo de ingestão de dados para uma instituição financeira na plataforma Insider Customer Data Platform (CDP). O objetivo é unificar e normalizar dados de diversas fontes, garantindo um perfil de cliente 360° robusto e acionável.

---

### Etapas de Implementação

A implementação da Insider CDP para este caso de uso será dividida em quatro etapas principais, garantindo um fluxo de trabalho organizado e eficiente:

0. **Estudo dos Casos:**
    * **Compreeção dos Problemas:** Entenda os casos e estude formas de solucionar e atender as expectativas do cliente.
    * **Mapa de Dados:** Mapeie os dados que deverão ser utilizados nas jornadas.
    * **Mecanismo da CDP:** Entenda os mecanismos disponiveis na CDP para atender a jornada.
    * **Jornada:** Desenhe uma solução para cada caso para a compreenção total, antes da aplicação.

1.  **Criação do Ambiente:**
    * **Download do Projeto do Git:** Obtenção do código-fonte e estruturas iniciais para a ingestão de dados.
    * **Parametrização do Projeto:** Configuração de variáveis e ajustes específicos para o ambiente da instituição financeira.
    * **Geração de Credenciais de API da Insider:** Obtenção das chaves de acesso necessárias para a comunicação segura com a plataforma CDP.

2.  **Estruturação dos Dados:**
    * **Limpeza:** Identificação e correção de erros, inconsistências e dados faltantes nas bases de origem.
    * **Identificação do Identificador Unico:** Garantir que as bases possuam um identificador unico entre todas as bases e interações dentro da plataforma.
    * **Tratamento de Duplicatas:** Eliminação de registros repetidos para garantir a unicidade do perfil do cliente.
    * **Normalização de Dados:** Padronização dos formatos de dados (ex: datas, endereços, telefones) para assegurar a consistência e a interoperabilidade.

3.  **Ingestão dos Dados na Plataforma:**
    * Envio dos dados processados das três bases de dados para a Insider CDP, utilizando os métodos de ingestão apropriados (ex: API, batch).
    * Configuração dos mapeamentos de campos para que os dados sejam corretamente atribuídos aos atributos do perfil do cliente na CDP.

4.  **Criação das Jornadas:**
    * Desenvolvimento e configuração de fluxos de automação (jornadas do cliente) dentro da plataforma Insider.
    * Estas jornadas serão desenhadas para **atender diretamente aos casos de uso** definidos, acionando comunicações e ações personalizadas em tempo real ou programadas.

---

### Casos de Uso

A implementação da Insider CDP habilita uma série de casos de uso estratégicos, permitindo à instituição financeira otimizar a experiência do cliente e impulsionar resultados de negócios. Abaixo, destacamos 3 cenários-chave:

#### 1. Ativação e Engajamento de Clientes Recém-Conquistados

* **Problema:** Clientes que recebem um novo cartão ou têm um financiamento aprovado nem sempre ativam ou utilizam o produto imediatamente, resultando em receita perdida e oportunidades de engajamento desaproveitadas.

#### 2. Prevenção de Churn e Retenção de Clientes

* **Problema:** Dificuldade em identificar clientes em risco de cancelar serviços (cartão, financiamento) antes que a decisão seja final, o que impede intervenções proativas para retenção.

#### 3. Cross-Sell e Up-Sell de Produtos Financeiros

* **Problema:** Dificuldade em identificar os clientes mais propensos a adquirir novos produtos ou fazer um *upgrade* de seus serviços, resultando em campanhas genéricas e baixa taxa de conversão.

---

### Escopo e Fontes de Dados

Para este caso de uso, a instituição financeira possui três fontes de dados distintas que serão unificadas na Insider CDP:

1.  **Dados Cadastrais:** Contêm informações essenciais sobre os clientes.
    * **Arquivo** bases/cadastro.csv
    * **Conteúdo:** Nome, CPF, endereço, contato (e-mail, telefone), data de nascimento, gênero, entre outros.
    * **Atualização:** Diariamente, com foco nas **atualizações de perfis existentes e novas entradas de clientes**. Isso garante que a CDP sempre tenha a informação cadastral mais recente.
    * **Volume:** Moderado, refletindo o fluxo de novos clientes e alterações cadastrais.
    * **Melhor Forma de Interagir com a Plataforma:** **Ingestão Batch Diária.** Dados cadastrais atualizados uma vez ao dia são suficientes para manter os perfis na CDP precisos, dada a natureza dessas informações.

2.  **Dados de Produtos de Cartão:** Abrangem o ciclo de vida e eventos transacionais relacionados aos cartões de crédito e/ou débito.
    * **Arquivo** bases/produto_cartoes.csv
    * **Conteúdo:**
        * **Entrega de Cartão:** Confirmação da entrega física ao cliente.
        * **Ativação de Cartão:** Registro da primeira utilização ou ativação formal do cartão.
        * **Cancelamento de Cartão:** Sinalização do encerramento do produto pelo cliente ou pela instituição.
        * **Sugestão de Outros Dados/Eventos:** Transações de compra (data, valor, categoria), pagamentos realizados, alterações de limite, bloqueios e desbloqueios.
    * **Atualização:** **Tempo real**, para capturar eventos críticos e comportamentos do cliente no momento em que ocorrem, permitindo ações imediatas.
    * **Volume:** Elevado e contínuo, dada a alta frequência de interações e transações com cartões.
    * **Melhor Forma de Interagir com a Plataforma:** **API de Eventos.** A natureza em tempo real desses dados demanda uma integração via API para garantir que cada ação do cliente com o cartão (ativação, transação) seja imediatamente registrada na CDP e possa acionar jornadas instantâneas. Para dados históricos ou de menor criticidade, um batch complementar pode ser usado.

3.  **Dados de Financiamento:** Detalham o status e informações relevantes dos contratos de financiamento.
    * **Arquivo** bases/produto_financeira.csv
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

### Soluções dos Cases
 Arquivo ResultadoEsperadoCases.md