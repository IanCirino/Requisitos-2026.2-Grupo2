# Especificação de Requisitos de Software (SRS)

**Projeto:** AdE – Amigo do Estudante (Sistema web de auxílio estudantil e preparação para provas no estilo ENADE)  
**Instituição:** Universidade de Fortaleza (UNIFOR)  
**Versão:** 1.0  
**Data:** 22/11/2026  
**Autor:** Ian Carvalho Cirino (Desenvolvedor / Equipe de Requisitos)  
**Validadores:** Prof. Me. Marcelo Bezerra De Alcantara (Docente Avaliador) e Prof. Me. Atila Girao De Oliveira (Solicitante e Avaliador)  

---

## Histórico de Versões

| Data | Versão | Descrição da Alteração | Autor |
| :--- | :--- | :--- | :--- |
| 22/11/2026 | 1.0 | Criação da Especificação de Requisitos de Software (SRS) consolidando a Visão da Demanda (v0.3), RNF (v0.1) e Diagramas UML (Casos de Uso, Componentes e Implantação). | Ian Carvalho Cirino |

---

## 1. Introdução

### 1.1. Propósito
Este documento apresenta a Especificação de Requisitos de Software (SRS) para o sistema **AdE – Amigo do Estudante**. Seu objetivo é detalhar de forma precisa, verificável e rastreável o escopo funcional, as regras de negócio, as interfaces externas e os requisitos não funcionais da solução, servindo como contrato técnico e pedagógico entre a equipe de desenvolvimento, os docentes, a coordenação de cursos e a equipe de TI da UNIFOR.

### 1.2. Escopo do Produto
O **AdE – Amigo do Estudante** é uma aplicação web (*Single Page Application* - SPA integrada a uma API REST) voltada para a preparação acadêmica de estudantes do ensino superior para o Exame Nacional de Desempenho dos Estudantes (ENADE) e avaliações similares.

O produto divide-se em dois horizontes de entrega:
* **Escopo de Entrega (MVP):** Banco de questões filtrado, realização de simulados cronometrados, consulta a gabaritos comentados, painéis de estatísticas de desempenho (individual e por turma/curso), cadastro e gestão de questões/simulados por docentes, administração de cadastros pela equipe técnica e integração com o **Unifor Online** (autenticação SSO e sincronização de turmas/alunos).
* **Evolução Futura / Em Avaliação:** Fórum de discussão por questão com moderação, importação automatizada de provas em PDF do INEP, classificação avançada por temas/competências vinculadas à grade curricular e comparação de desempenho com estatísticas oficiais do INEP.

### 1.3. Definições, Acrônimos e Abreviações

| Termo / Sigla | Definição |
| :--- | :--- |
| **AdE** | Amigo do Estudante (nome do sistema especificado). |
| **ENADE** | Exame Nacional de Desempenho dos Estudantes, componente curricular obrigatório avaliado pelo INEP. |
| **INEP** | Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira (fonte das provas e microdados/estatísticas oficiais). |
| **LGPD** | Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018). |
| **MVP** | *Minimum Viable Product* (Produto Mínimo Viável acordado para a primeira entrega). |
| **RF / RNF / RN** | Requisito Funcional / Requisito Não Funcional / Regra de Negócio. |
| **SPA** | *Single Page Application* (arquitetura adotada no front-end web do AdE). |
| **SSO** | *Single Sign-On* (autenticação única institucional via Unifor Online). |
| **UC** | Caso de Uso (*Use Case*). |
| **Unifor Online** | Plataforma acadêmica institucional da UNIFOR, fonte oficial de dados de alunos, professores, turmas e disciplinas. |

### 1.4. Referências
1. **Visão da Demanda (VD) – AdE**, versão 0.3, de 14/11/2026.
2. **Especificação de Requisitos Não Funcionais (RNF) – AdE**, versão 0.1, de 22/11/2026.
3. **Diagrama de Casos de Uso UML (`diagrama-casos-de-uso-ade.png`)**, contemplando UC01 a UC19.
4. **Diagrama de Componentes UML (`ade-diagramas-de-componentes.png`)**, arquitetura SPA Web + API REST.
5. **Diagrama de Implantação UML (`ade-diagramas-de-implantacao.png`)**, topologia física e artefatos.

---

## 2. Descrição Geral

### 2.1. Perspectiva do Produto
O AdE é um sistema web independente e complementar às plataformas acadêmicas existentes na UNIFOR (como o *Unifor Online* e o *PreparaEdu*), projetado para não duplicar cadastros institucionais. 

Conforme a arquitetura definida nos diagramas de componentes e implantação:
* **Front-end (`ade-web`):** SPA web servida via HTTPS/TLS, dividida logicamente em três portais de acesso conforme o perfil: *Portal do Estudante*, *Portal Docente e Coordenação* e *Portal de Administração*.
* **Back-end (`ade-api` e `ade-sync`):** API RESTful sobre JSON com controle de acesso baseado em perfis (RBAC) e um agendador em segundo plano (`ade-sync`) responsável pela sincronização diária com o Unifor Online.
* **Camada de Dados (`ade_db` e armazenamento de objetos):** Banco de dados relacional para persistência transacional e repositório de arquivos para PDFs de provas e imagens de enunciados.

### 2.2. Resumo das Funcionalidades (Catálogo F-01 a F-14)

| ID | Funcionalidade | Necessidade | Status no Escopo |
| :--- | :--- | :--- | :--- |
| **F-01** | Banco de questões com filtros por ano, curso/área e componente | NEC-01 | Entrega (MVP) |
| **F-02** | Simulados cronometrados em condições próximas ao exame | NEC-03 | Entrega (MVP) |
| **F-03** | Gabarito comentado com explicações detalhadas e referências | NEC-02, NEC-06 | Entrega (MVP) |
| **F-04** | Estatísticas de desempenho individual do estudante com gráficos | NEC-04 | Entrega (MVP) |
| **F-05** | Fórum de discussão por questão com moderação | NEC-06 | Evolução Futura |
| **F-06** | Cadastro e autenticação segura (SSO institucional e controle de perfis) | NEC-07 | Entrega (MVP) |
| **F-07** | Importação automatizada de provas em PDF do INEP | NEC-08 | Em Avaliação |
| **F-08** | Classificação por temas, competências e relação com a grade curricular | NEC-08 | Em Avaliação |
| **F-09** | Cadastro, edição e inativação de questões e comentários | NEC-01, NEC-02 | Entrega (MVP) |
| **F-10** | Criação, configuração e publicação de simulados para turmas | NEC-02 | Entrega (MVP) |
| **F-11** | Painel de acompanhamento de desempenho de turmas e alunos | NEC-05 | Entrega (MVP) |
| **F-12** | Integração e sincronização de dados com o Unifor Online | NEC-02, NEC-05, NEC-07 | Entrega (MVP) |
| **F-13** | Administração do sistema, usuários, perfis e cadastros de apoio | NEC-07 | Entrega (MVP) |
| **F-14** | Comparação de desempenho com estatísticas oficiais do INEP | NEC-04, NEC-05 | Em Avaliação |

### 2.3. Classes e Características dos Usuários (Atores)

| ID | Ator | Tipo | Descrição e Responsabilidades no Sistema |
| :--- | :--- | :--- | :--- |
| **AT-01** | **Estudante** | Usuário Humano | Aluno matriculado. Consulta o banco de questões, realiza simulados cronometrados, estuda gabaritos comentados, analisa seu desempenho (com comparação anônima da turma) e participa do fórum (evolução). |
| **AT-02** | **Equipe Técnica** | Usuário Humano | Administrador de TI/apoio acadêmico. Gerencia usuários, perfis, cadastros de apoio (cursos/áreas), monitora sincronizações com o Unifor Online e apoia a moderação/carga de questões. |
| **AT-03** | **Coordenação** | Usuário Humano | Coordenador de curso. Acompanha indicadores agregados de desempenho das turmas e cursos, compara resultados com dados oficiais do INEP e valida o alinhamento pedagógico. |
| **AT-04** | **Professor** | Usuário Humano | Docente da instituição. Cadastra/edita questões, redige gabaritos comentados, monta e publica simulados para suas turmas, acompanha o desempenho de seus alunos e modera o fórum. |
| **AT-05** | **INEP** | Sistema Externo | Fonte externa de provas anteriores do ENADE (PDF) e estatísticas/microdados oficiais do exame. |
| **AT-06** | **Unifor Online** | Sistema Externo | Provedor institucional de identidade (SSO) e fonte de dados acadêmicos (alunos, professores, cursos, turmas e disciplinas). |

### 2.4. Ambiente Operacional
* **Dispositivos Clientes:** Computadores desktop, notebooks, tablets e smartphones com acesso à internet ou rede institucional, utilizando navegadores modernos (Chrome, Edge, Firefox, Safari) em resoluções de $360\text{ px}$ a $1920\text{ px}$.
* **Ambiente Servidor:** Infraestrutura on-premises da UNIFOR ou nuvem aprovada pela TI, operando com servidor web/proxy reverso (HTTPS na porta 443), servidor de aplicação (runtime da API REST e agendador) e servidor de banco de dados relacional com armazenamento de arquivos.

### 2.5. Restrições de Projeto e Implementação
* **Conformidade Legal (LGPD):** Todo tratamento de dados pessoais deve observar a Lei nº 13.709/2018, garantindo minimização de dados, finalidade explícita e privacidade por padrão.
* **Direitos Autorais e Uso de Provas:** O uso de questões e PDFs do INEP está condicionado à verificação formal dos direitos de uso e citação obrigatória da fonte.
* **Complementaridade:** O sistema não deve exigir novo cadastro manual de alunos já existentes no Unifor Online, reutilizando o identificador institucional.
* **Fuso Horário:** Todos os cronômetros, agendamentos e registros de auditoria devem operar sob o horário oficial de Brasília (`UTC-3`).

### 2.6. Premissas e Dependências
* A integração SSO e de leitura de turmas/alunos depende da liberação de credenciais e contratos de API pela TI da UNIFOR (PQ-06, PQ-10).
* A carga inicial do banco de questões será realizada manualmente ou via importação de planilha estruturada por docentes e equipe técnica, não dependendo da extração automática de PDFs (F-07) para o lançamento do MVP (PQ-05).
* Os limiares quantitativos de desempenho e disponibilidade definidos na seção de RNFs constituem linha de base sujeita à homologação final junto à TI da UNIFOR.

---

## 3. Regras de Negócio (RN)

As regras abaixo governam transversalmente os casos de uso e requisitos funcionais do AdE:

* **RN-01 (Composição do Banco e Componentes ENADE):** Toda questão cadastrada deve pertencer obrigatoriamente a um **Ano/Edição**, um **Curso/Área de Conhecimento** e um **Componente** (`Formação Geral` ou `Conhecimento Específico`), além de possuir enunciado, alternativas, alternativa correta (gabarito), comentário explicativo e referência bibliográfica/fonte.
* **RN-02 (Integridade de Questões em Simulados):** Uma questão já respondida por estudantes em simulados finalizados não pode ser excluída fisicamente nem ter seu gabarito alterado retroativamente sem versionamento; caso precise ser descontinuada, deve ser marcada como **Inativa**, permanecendo íntegra no histórico de tentativas passadas.
* **RN-03 (Cronômetro Autoritativo no Servidor):** O tempo de duração de um simulado é controlado exclusivamente pelo relógio do servidor. Ao iniciar o simulado, o servidor registra o timestamp de início e calcula o limite de encerramento. Caso o tempo expire, o simulado é encerrado e submetido automaticamente com as respostas registradas até o momento.
* **RN-04 (Sigilo do Gabarito Durante o Simulado):** Enquanto uma tentativa de simulado estiver com status `Em Andamento`, a API não deve trafegar para o cliente a alternativa correta nem os comentários das questões. Esses dados só são liberados após a transição da tentativa para `Finalizada`.
* **RN-05 (Imutabilidade Pós-Finalização):** Após finalizado (por submissão voluntária do estudante ou expiração do tempo), o simulado torna-se imutável, impedindo qualquer alteração nas respostas enviadas.
* **RN-06 (Privacidade e Comparação Anônima - PQ-12):** A comparação de desempenho de um estudante com a média da turma é **opcional** (acionada explicitamente pelo aluno) e estritamente **anônima**, sendo proibida a exibição de rankings nominais. A média da turma só será exibida se a turma possuir no mínimo $5$ estudantes com tentativas concluídas no respectivo escopo, evitando identificação indireta.
* **RN-07 (Visibilidade Hierárquica de Desempenho - LGPD):**
  * **Estudante:** Visualiza apenas suas próprias métricas individuais e a média anônima da turma (conforme RN-06).
  * **Professor:** Visualiza métricas agregadas e individuais exclusivamente dos estudantes matriculados nas turmas sob sua responsabilidade.
  * **Coordenação:** Visualiza métricas agregadas por curso, turma e componente. O acesso a dados individuais de um estudante pela coordenação é bloqueado por padrão, sendo liberado apenas mediante registro explícito de consentimento do titular (PQ-07).
* **RN-08 (Fluxo Unidirecional com o Unifor Online):** A sincronização de dados acadêmicos ocorre estritamente no sentido `Unifor Online -> AdE`. O AdE nunca grava notas, frequência ou desempenho de simulados de volta no Unifor Online.
* **RN-09 (Moderação de Conteúdo no Fórum - Evolução):** Publicações no fórum de discussão exigem aceite prévio das regras de conduta. Mensagens denunciadas por usuários ficam sinalizadas para análise de moderadores (Docentes ou Equipe Técnica), que podem ocultá-las ou removê-las com registro de auditoria.

---

## 4. Requisitos Funcionais

Os requisitos funcionais estão agrupados por módulo arquitetural (conforme o Diagrama de Componentes) e rastreados aos Casos de Uso (`UC01` a `UC19`) e Funcionalidades (`F-01` a `F-14`).

### 4.1. Módulo: Autenticação, Perfis e Administração (`F-06`, `F-12`, `F-13`)

| ID | Requisito Funcional | Caso de Uso | Escopo | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF-01** | O sistema deve autenticar usuários institucionalmente via protocolo SSO integrado ao Unifor Online, vinculando automaticamente o usuário ao seu identificador institucional e perfil(is) correspondente(s). | UC01 | MVP | Alta |
| **RF-02** | O sistema deve permitir o primeiro acesso/autocadastro complementar de usuários autenticados via SSO, apresentando o Termo de Privacidade (LGPD) com a descrição das finalidades e perfis com acesso aos dados. | UC01 | MVP | Alta |
| **RF-03** | O sistema deve aplicar controle de acesso baseado em perfis (Estudante, Professor, Coordenação, Equipe Técnica), direcionando o usuário ao respectivo portal após o login. Usuários com múltiplos perfis (ex.: Professor e Coordenação) devem poder alternar o contexto de atuação. | UC01 | MVP | Alta |
| **RF-04** | O sistema deve permitir que a Equipe Técnica consulte, ative, inative usuários e atribua ou revogue perfis de acesso (incluindo permissões de moderação ou tempo adicional de prova). | UC14 | MVP | Média |
| **RF-05** | O sistema deve permitir que a Equipe Técnica cadastre, edite e inative entidades de apoio: Cursos, Áreas de Conhecimento, Componentes Curriculares (`Formação Geral` e `Conhecimento Específico`) e Edições/Anos de exame. | UC15 | MVP | Média |
| **RF-06** | O sistema deve executar rotina agendada (diária) e sob demanda para sincronizar cursos, disciplinas, turmas, docentes e estudantes ativos a partir da API do Unifor Online, gerando log e relatório de inconsistências. | UC16 | MVP | Alta |

### 4.2. Módulo: Banco de Questões e Gabarito Comentado (`F-01`, `F-03`, `F-07`, `F-08`, `F-09`)

| ID | Requisito Funcional | Caso de Uso | Escopo | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF-07** | O sistema deve permitir que Estudantes, Professores e Equipe Técnica pesquisem e filtrem questões ativas no banco por **Ano**, **Curso/Área de Conhecimento**, **Componente**, **Palavra-chave** e status de resolução pelo aluno (resolvidas/não resolvidas). | UC02 | MVP | Alta |
| **RF-08** | O sistema deve permitir que o Estudante responda questões avulsas diretamente no banco de questões, visualizando imediatamente após a confirmação da resposta o gabarito oficial, o comentário explicativo e as referências bibliográficas. | UC02, UC04 | MVP | Alta |
| **RF-09** | O sistema deve permitir que Professores e Equipe Técnica cadastrem novas questões (individualmente ou via importação de planilha estruturada), informando enunciado (com suporte a texto formatado e imagens), texto de apoio, alternativas (A a E), alternativa correta, ano, curso/área e componente. | UC10 | MVP | Alta |
| **RF-10** | O sistema deve exigir o registro do comentário explicativo do gabarito (justificando a alternativa correta e as incorretas, além da fonte/referência) como etapa obrigatória (`«include»`) para que uma questão seja publicada como ativa no banco. | UC10, UC11 | MVP | Alta |
| **RF-11** | O sistema deve permitir que Professores e Equipe Técnica editem questões existentes ou alterem seu status para `Inativa` mediante confirmação explícita, preservando o histórico de auditoria (conforme RN-02). | UC10 | MVP | Alta |
| **RF-12** | O sistema deve permitir que Professores e Equipe Técnica importem arquivos PDF de provas oficiais do INEP, extraindo automaticamente enunciados e alternativas para uma fila de rascunhos sujeita à revisão e aprovação humana antes da publicação. | UC17 | Em Avaliação | Baixa |
| **RF-13** | O sistema deve permitir que Professores e Equipe Técnica classifiquem questões por temas específicos, competências da matriz do ENADE e disciplinas da grade curricular do curso. | UC18 | Em Avaliação | Média |

### 4.3. Módulo: Simulados Cronometrados (`F-02`, `F-03`, `F-10`)

| ID | Requisito Funcional | Caso de Uso | Escopo | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF-14** | O sistema deve permitir que Professores criem simulados selecionando questões do banco (manualmente ou por sorteio parametrizado por área/componente), definindo título, instruções, duração máxima em minutos e período de disponibilidade. | UC12 | MVP | Alta |
| **RF-15** | O sistema deve permitir que Professores publiquem simulados criados para uma ou mais turmas vinculadas ao seu perfil, tornando-os visíveis aos estudantes matriculados nessas turmas na janela agendada (`«include»`). | UC12, UC13 | MVP | Alta |
| **RF-16** | O sistema deve permitir que Estudantes iniciem simulados publicados para suas turmas ou gerem simulados livres de treino a partir dos filtros do banco de questões. | UC03 | MVP | Alta |
| **RF-17** | Durante a execução do simulado, o sistema deve exibir cronômetro regressivo sincronizado com o servidor (RN-03), painel de navegação entre questões (indicando respondidas, em branco e marcadas para revisão) e salvamento automático a cada marcação de alternativa. | UC03 | MVP | Alta |
| **RF-18** | O sistema deve permitir que o Estudante retome um simulado em andamento caso ocorra queda de conexão ou fechamento do navegador, mantendo as respostas salvas e o tempo restante calculado pelo servidor. | UC03 | MVP | Alta |
| **RF-19** | O sistema deve encerrar o simulado mediante confirmação do estudante (alertando sobre questões em branco) ou automaticamente ao término do tempo limite, calculando a nota/percentual de acertos e liberando o acesso ao gabarito comentado completo da tentativa (`«extend»`). | UC03, UC04 | MVP | Alta |

### 4.4. Módulo: Desempenho e Estatísticas (`F-04`, `F-11`, `F-14`)

| ID | Requisito Funcional | Caso de Uso | Escopo | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF-20** | O sistema deve exibir ao Estudante um painel de desempenho próprio contendo total de questões resolvidas, simulados concluídos, percentual de acertos geral, evolução temporal e distribuição gráfica por Área de Conhecimento e Componente (`Formação Geral` vs. `Conhecimento Específico`). | UC05 | MVP | Média |
| **RF-21** | O sistema deve permitir que o Estudante ative opcionalmente no seu painel a comparação do seu percentual de acertos com a média anônima de sua turma, respeitando o limiar mínimo de privacidade (RN-06). | UC05, UC06 | MVP | Média |
| **RF-22** | O sistema deve fornecer ao Professor um painel de acompanhamento de desempenho de suas turmas e alunos, permitindo filtrar por simulado, turma, componente e identificar questões com maior índice de erro. | UC09 | MVP | Média |
| **RF-23** | O sistema deve fornecer à Coordenação um painel gerencial com visão consolidada e agregada do desempenho por curso, semestre, turma e componente curricular, respeitando o bloqueio de identificação individual sem consentimento (RN-07). | UC09 | MVP | Média |
| **RF-24** | O sistema deve permitir a importação de indicadores oficiais divulgados pelo INEP (CSV/planilha) e exibir comparativos gráficos entre o desempenho obtido pelos estudantes/cursos no AdE e as médias oficiais do ENADE. | UC19 | Em Avaliação | Baixa |

### 4.5. Módulo: Fórum de Discussão (`F-05`)

| ID | Requisito Funcional | Caso de Uso | Escopo | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF-25** | O sistema deve disponibilizar um espaço de discussão vinculado a cada questão do banco, permitindo que Estudantes, Professores e Equipe Técnica publiquem dúvidas, comentários e respostas, após aceite das regras de conduta. | UC07 | Evolução Futura | Baixa |
| **RF-26** | O sistema deve permitir que usuários denunciem postagens inadequadas e que Professores e Equipe Técnica moderem o fórum (ocultando/excluindo mensagens, fixando respostas relevantes de docentes e registrando justificativa). | UC08 | Evolução Futura | Baixa |

---

## 5. Especificação Detalhada dos Principais Casos de Uso (MVP)

### 5.1. UC01 – Cadastrar e Autenticar Usuário
* **Ator Principal:** Estudante, Professor, Coordenação, Equipe Técnica.
* **Sistemas Envolvidos:** Unifor Online (SSO).
* **Pré-condições:** Usuário possui vínculo ativo registrado na base institucional da UNIFOR.
* **Fluxo Principal:**
  1. O usuário acessa a URL do AdE e seleciona "Entrar com Unifor Online".
  2. O sistema redireciona o navegador para o provedor de autenticação institucional (SSO).
  3. O usuário insere suas credenciais institucionais e é validado pelo Unifor Online.
  4. O Unifor Online retorna o token de identidade ao AdE.
  5. O AdE verifica se o identificador institucional já possui perfil ativo na base local.
  6. O sistema cria a sessão autenticada e redireciona o usuário para o portal correspondente ao seu perfil.
* **Fluxos Alternativos:**
  * **FA01 (Primeiro Acesso):** No passo 5, se for o primeiro acesso do usuário sincronizado, o sistema exibe o Aviso de Privacidade e Finalidade de Dados (LGPD) antes de liberar o acesso ao portal.
  * **FA02 (Múltiplos Perfis):** No passo 6, se o usuário possuir mais de um perfil ativo (ex.: Docente e Coordenador), o sistema apresenta seletor de perfil no cabeçalho.
* **Fluxos de Exceção:**
  * **FE01 (Falha na Autenticação Institucional):** O provedor retorna erro de credencial ou vínculo inativo; o AdE exibe mensagem informativa sem criar sessão.

### 5.2. UC03 – Realizar Simulado Cronometrado
* **Ator Principal:** Estudante.
* **Pré-condições:** Estudante autenticado; existência de simulado publicado para sua turma dentro do prazo ou configuração de simulado livre.
* **Fluxo Principal:**
  1. O Estudante acessa a aba "Simulados" e seleciona um simulado disponível.
  2. O sistema exibe as regras (número de questões, duração, impossibilidade de pausa) e solicita confirmação de início.
  3. O Estudante confirma o início; o servidor cria o registro da tentativa (`Em Andamento`), define o timestamp de encerramento e envia as questões (sem gabarito/comentários).
  4. O Estudante navega pelas questões, seleciona alternativas e, opcionalmente, marca questões para revisão. A cada seleção, o cliente envia a resposta ao servidor em segundo plano.
  5. O Estudante clica em "Finalizar Simulado".
  6. O sistema exibe diálogo de confirmação informando a quantidade de questões respondidas e em branco.
  7. O Estudante confirma a finalização.
  8. O servidor encerra a tentativa, calcula a pontuação e os acertos por componente, e redireciona para a tela de resultado com acesso ao **UC04 – Consultar Gabarito Comentado**.
* **Fluxos Alternativos:**
  * **FA01 (Retomada após Queda de Conexão):** Se o navegador fechar durante o passo 4, ao acessar novamente o simulado dentro do prazo, o sistema recupera as respostas salvas e ajusta o cronômetro pelo relógio do servidor.
* **Fluxos de Exceção:**
  * **FE01 (Tempo Esgotado):** Se o relógio do servidor atingir o limite de duração antes do passo 7, o sistema encerra automaticamente a tentativa com as respostas já persistidas e exibe o resultado.

### 5.3. UC10 e UC11 – Cadastrar Questão e Registrar Comentário do Gabarito
* **Ator Principal:** Professor, Equipe Técnica.
* **Pré-condições:** Usuário autenticado com permissão de edição de conteúdo.
* **Fluxo Principal:**
  1. O usuário acessa "Banco de Questões > Nova Questão".
  2. O sistema exibe o formulário de cadastro (com salvamento automático de rascunho).
  3. O usuário preenche ano, curso/área, componente (`Formação Geral` ou `Conhecimento Específico`), enunciado, anexos de imagem (opcional) e as alternativas.
  4. O sistema aciona obrigatoriamente a etapa **UC11 – Registrar Comentário do Gabarito**.
  5. O usuário indica a alternativa correta, redige a justificativa pedagógica detalhada (explicando a correta e os distratores) e informa a referência bibliográfica/fonte.
  6. O usuário seleciona "Publicar Questão".
  7. O sistema valida os campos obrigatórios, persiste a questão como `Ativa`, registra o log de auditoria e exibe confirmação.

---

## 6. Requisitos de Interface Externa

### 6.1. Interfaces de Usuário (UI)
* **Navegação Responsiva:** Layout adaptável (*mobile-first* / fluido entre $360\text{ px}$ e $1920\text{ px}$), sem rolagem horizontal e livre de anúncios ou rastreadores externos.
* **Segregação por Portais:**
  * *Portal do Estudante:* Dashboard de evolução, acesso rápido ao Banco de Questões (máximo 3 cliques) e Simulados.
  * *Portal Docente e Coordenação:* Gestão de questões, construtor de simulados e painéis analíticos com gráficos e tabelas acessíveis.
  * *Portal de Administração:* Gestão de usuários/perfis, cadastros auxiliares e monitor de sincronização.
* **Acessibilidade:** Conformidade com **WCAG 2.1 nível AA**, suporte completo à navegação por teclado, compatibilidade com leitores de tela (NVDA/VoiceOver), contraste mínimo de $4{,}5:1$ e tabelas de dados alternativas para todos os gráficos estatísticos.

### 6.2. Interfaces de Software e Comunicação (APIs)

| Interface | Sistema Externo | Protocolo / Formato | Direção | Descrição e Contrato |
| :--- | :--- | :--- | :--- | :--- |
| **INT-01** | Unifor Online (SSO) | HTTPS / TLS 1.2+ (OAuth2 / OIDC ou SAML a confirmar com TI) | Bidirecional (Auth) | Autenticação institucional única e obtenção de identificador do usuário. |
| **INT-02** | Unifor Online (Acadêmico) | HTTPS / REST / JSON | Entrada (`Unifor -> AdE`) | Sincronização diária e sob demanda de cursos, disciplinas, turmas, matrículas de alunos e vínculos docentes. |
| **INT-03** | Portal do INEP (Provas) | HTTPS / Arquivo PDF | Entrada (`INEP -> AdE`) | Upload/importação de cadernos de provas oficiais do ENADE para extração assistida (Evolução F-07). |
| **INT-04** | Portal do INEP (Dados) | Arquivo CSV / Planilha | Entrada (`INEP -> AdE`) | Importação de médias e conceitos oficiais do ENADE por curso/área para comparativos (Evolução F-14). |

### 6.3. Interfaces de Hardware e Infraestrutura
Conforme o Diagrama de Implantação:
* **Servidor Web / Proxy Reverso:** Terminação TLS (HTTPS porta 443), entrega dos artefatos estáticos da SPA (`ade-web`) e roteamento `/api` em rede interna para o servidor de aplicação.
* **Servidor de Aplicação:** Execução da API REST (`ade-api`) e do serviço agendador (`ade-sync`).
* **Persistência:** Comunicação via SQL (TCP) com SGBD Relacional (`ade_db`) e leitura/escrita em sistema de arquivos/objetos (`provas e anexos`).

---

## 7. Resumo dos Requisitos Não Funcionais (RNF)

Os requisitos não funcionais detalhados constam no documento *Especificação de Requisitos Não Funcionais (v0.1)*. Abaixo sintetizam-se os parâmetros críticos de linha de base (sujeitos à homologação com a TI da UNIFOR):

| Categoria | IDs de Referência | Resumo dos Critérios Verificáveis |
| :--- | :--- | :--- |
| **Desempenho e Capacidade** | `RNF-DES-01` a `RNF-DES-14` | Resposta do banco de questões $\le 2\text{ s}$ (p95); carga inicial do simulado $\le 3\text{ s}$; suporte a picos de $1.000$ usuários simultâneos e $200$ simulados ativos; banco dimensionado para $\ge 10.000$ questões e histórico de $5$ anos letivos. |
| **Confiabilidade e Disponibilidade** | `RNF-CNF-01` a `RNF-CNF-10` | Disponibilidade mensal $\ge 99{,}5\%$ (elevada para $\ge 99{,}9\%$ em janelas de simulados publicados); salvamento de respostas em $\le 5\text{ s}$ com tolerância à queda de rede; operação contínua em caso de indisponibilidade do Unifor Online; backup diário ($RPO \le 24\text{ h}$, $RTO \le 4\text{ h}$). |
| **Segurança e Auditoria** | `RNF-SEG-01` a `RNF-SEG-16` | 100% tráfego HTTPS (TLS 1.2+); criptografia AES-256 em repouso para dados pessoais; aderência ao OWASP Top 10; bloqueio após 5 tentativas falhas; trilha de auditoria imutável por $\ge 12\text{ meses}$ para ações administrativas e edição de questões. |
| **Privacidade e Conformidade Legal** | `RNF-PRI-01` a `RNF-PRI-11`, `RNF-LEG-01` a `RNF-LEG-04` | Conformidade integral com a LGPD (Lei nº 13.709/2018), LBI (Lei nº 13.146/2015) e Lei de Direitos Autorais (Lei nº 9.610/1998); retenção de dados individuais até $12\text{ meses}$ após encerramento do vínculo institucional; atendimento a direitos do titular em $\le 15\text{ dias}$. |
| **Usabilidade e Acessibilidade** | `RNF-USA-01` a `RNF-USA-18` | Conformidade WCAG 2.1 AA; taxa de conclusão sem treinamento $\ge 80\%$ para estudantes e professores; pontuação SUS $\ge 70$; confirmação obrigatória em ações irreversíveis. |
| **Manutenibilidade e Portabilidade** | `RNF-FLX-01` a `RNF-FLX-09`, `RNF-MNT-01` a `RNF-MNT-13` | Arquitetura modular com adaptadores isolados para Unifor Online e INEP; exportação aberta de dados em CSV/JSON; cobertura de testes automatizados $\ge 70\%$ nas regras de negócio; implantação automatizada ($\le 1\text{ h}$) e rollback ($\le 30\text{ min}$). |

---

## 8. Matriz de Rastreabilidade

A tabela abaixo relaciona as Necessidades de Negócio (`NEC`), Funcionalidades (`F`), Casos de Uso (`UC`), Requisitos Funcionais (`RF`) e Componentes Arquiteturais:

| Necessidade | Funcionalidade | Caso de Uso | Requisitos Funcionais | Componente Back-end | Portal Front-end |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **NEC-01** | F-01, F-09 | UC02, UC10 | RF-07, RF-08, RF-09, RF-11 | Banco de Questões | Portal Estudante / Docente |
| **NEC-02** | F-03, F-09, F-10, F-12 | UC10, UC11, UC12, UC13 | RF-09, RF-10, RF-14, RF-15 | Simulados / Gabarito Comentado | Portal Docente e Coordenação |
| **NEC-03** | F-02 | UC03 | RF-16, RF-17, RF-18, RF-19 | Simulados | Portal do Estudante |
| **NEC-04** | F-04, F-14 | UC05, UC06, UC19 | RF-20, RF-21, RF-24 | Desempenho e Estatísticas | Portal do Estudante |
| **NEC-05** | F-11, F-12, F-14 | UC09, UC19 | RF-22, RF-23, RF-24 | Desempenho e Estatísticas | Portal Docente e Coordenação |
| **NEC-06** | F-03, F-05 | UC04, UC07, UC08 | RF-08, RF-10, RF-25, RF-26 | Gabarito Comentado / Fórum | Portal Estudante / Docente |
| **NEC-07** | F-06, F-12, F-13 | UC01, UC14, UC15, UC16 | RF-01, RF-02, RF-03, RF-04, RF-05, RF-06 | Autenticação / Admin / Conector Unifor | Todos / Portal Administração |
| **NEC-08** | F-07, F-08, F-09 | UC17, UC18 | RF-12, RF-13 | Importação / Classificação / Conector INEP | Portal Docente e Coordenação |

---

## 9. Pendências e Critérios de Aceitação para Homologação

Para a transição desta SRS para o desenvolvimento e homologação final junto aos solicitantes, devem ser concluídas as seguintes ações:
1. **Homologação do MVP (PQ-01):** Assinatura formal do Prof. Me. Atila Girao De Oliveira confirmando a segregação entre o escopo MVP (`RF-01` a `RF-11`, `RF-14` a `RF-23`) e os itens de evolução (`RF-12`, `RF-13`, `RF-24` a `RF-26`).
2. **Definição de Infraestrutura e Contratos API (PQ-06, PQ-10):** Reunião técnica com a TI da UNIFOR para definição da stack tecnológica, ambiente de hospedagem e contrato de integração SSO/API do Unifor Online.
3. **Validação Jurídica / DPO (PQ-05, PQ-07):** Aprovação do inventário de dados pessoais (LGPD) pelo encarregado de dados da instituição e confirmação dos termos de uso das provas do INEP.