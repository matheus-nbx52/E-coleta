# eColeta Igarassu: Plataforma de Logística Reversa sob Demanda

### Conectando Pessoas, Tecnologia e Sustentabilidade em Igarassu

---

## 🧐 Sobre o Projeto

Inspirado em modelos de aplicativos de entrega (*delivery*), o eColeta conecta o cidadão que deseja descartar corretamente com Eco-Coletores e a cadeia de reciclagem de forma eficiente e transparente.

---

## 🎯 O Desafio Ambiental de Igarassu (Problemática)

O Descarte Inadequado de Resíduos Especiais: Materiais de alto valor ou risco, como **óleo de cozinha usado**, **eletrônicos** e certos plásticos, acabam indo para o lixo comum ou para o meio ambiente, contribuindo para:

* Entupimento de bueiros e alagamentos.
* Contaminação de manguezais e mananciais.

O Impacto Social e Econômico: A ineficiência logística impede que as cooperativas e catadores informais trabalhem de forma otimizada, perdendo a oportunidade de gerar renda a partir desses resíduos.

---

## ✨ Solução: A Plataforma Ecoleta

O Ecoleta é a ponte tecnológica que profissionaliza a coleta e incentiva o cidadão através de três pilares:

### 1. Engajamento do Morador (Geração de Demanda)
* **Solicitam Coleta pelo App:** Moradores agendam a coleta de recicláveis (ex: plástico, papelão, óleo) de forma simples e sob demanda.

### 2. Eficiência Logística (O Coração da Aplicação)
* **Eco-Coletores:** Profissionais (autônomos ou cooperados) recebem os pedidos mais próximos, com rotas otimizadas por um algoritmo inteligente para maximizar ganhos e minimizar o custo de combustível.

### 3. Comercialização e Renda (O Lucro Sustentável)
* **Cooperativas/Parceiros:** Recebem e processam materiais limpos e já triados.
* **Logística Reversa Inteligente:** O sistema conecta toda a cadeia de reciclagem, transformando o lixo em um ativo comercial.

---

## 🛠️ Estrutura do Banco de Dados (Modelo Entidade-Relacionamento)

Para garantir a **eficiência logística** e a **transparência** na cadeia de reciclagem, a plataforma Ecoleta utiliza um modelo de banco de dados relacional que conecta todos os *stakeholders*: Moradores, Eco-Coletores, Resíduos e a gestão de transações.

O diagrama abaixo ilustra a arquitetura, focando nas principais entidades e seus relacionamentos:

![Diagrama Entidade-Relacionamento do Banco de Dados eColeta Igarassu](Untitled%20diagram-2025-11-13-011101.png)

---

### 🔑 Entidades Principais e Funções

* **`Morador`** 👤
    * **Função:** Geração de demanda. Contém dados de endereço para a coleta e é o solicitante das `Coleta`s.

* **`EcoColetor`** 🚚
    * **Função:** Execução do serviço. Pode ser um autônomo ou cooperado (`fk_cooperativa`), e é responsável por realizar a `Coleta`.

* **`Cooperativa`** 🏢
    * **Função:** Gestão dos Eco-Coletores e destino final dos resíduos.

* **`Coleta`** 📅
    * **Função:** O coração do sistema. Representa o agendamento de coleta, ligando o `Morador` que solicita ao `EcoColetor` que a realiza.

* **`Residuo`** ♻️
    * **Função:** Define os tipos de materiais que podem ser coletados (ex: óleo de cozinha, eletrônicos).

* **`Itens_Coleta`** e **`Coletor_Residuo`** 📊
    * **Função:** Detalham o que foi coletado. `Itens_Coleta` armazena o peso final exato para a transação.

* **`Avaliacao`** ⭐
    * **Função:** Qualidade do serviço. Permite que o Morador avalie a `Coleta` realizada pelo Eco-Coletor.

* **`Transacao_Pontuacao`** 💰
    * **Função:** Incentivo e engajamento. Armazena o valor (monetário ou em pontos) gerado por uma `Coleta`, incentivando o Morador a descartar corretamente.

---

### 🔗 Relacionamentos Chave

| Entidades | Relacionamento (Cardinalidade) | Descrição |
| :--- | :--- | :--- |
| `Morador` e `Coleta` | 1:N (Um Morador solicita N Coletas) | Rastreia o histórico de descarte de cada cidadão. |
| `EcoColetor` e `Coleta` | 1:N (Um Eco-Coletor realiza N Coletas) | Essencial para a otimização de rotas e cálculo de rendimento. |
| `Coleta` e `Itens_Coleta` | 1:N (Uma Coleta contém N Itens) | Permite detalhar a quantidade (`peso_final_kg`) de cada tipo de resíduo. |
| `Coleta` e `Transacao_Pontuacao` | 1:1 | Cada coleta finalizada e validada gera uma única transação de valor/pontuação para o Morador. |
