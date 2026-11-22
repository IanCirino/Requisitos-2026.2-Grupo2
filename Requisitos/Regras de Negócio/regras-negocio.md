# Regras de Negócio da Solução (RN) - AdE (Amigo do Estudante)

## 1. Regras de negócio

* **Identificador:** RN01 - Usuários institucionais acessam o sistema mediante autenticação segura[cite: 2].
* **Descrição:** Todo estudante, docente, coordenador ou membro da equipe técnica deve possuir cadastro validado e autenticar-se (preferencialmente via login único institucional da Unifor) antes de acessar qualquer funcionalidade interna da plataforma[cite: 2]. (Origem: NEC-07, F-06, PQ-06, PQ-10)[cite: 2].

---

* **Identificador:** RN02 - Sistema restringe funcionalidades de acordo com o perfil do usuário[cite: 2].
* **Descrição:** O controle de acesso deve separar as permissões por perfil[cite: 2]: estudantes realizam questões, simulados e consultam o próprio desempenho[cite: 2]; docentes cadastram questões/simulados e visualizam o desempenho de suas turmas[cite: 2]; coordenadores visualizam indicadores gerais e relatórios agregados dos cursos[cite: 2]; e a equipe técnica administra usuários, perfis e cadastros estruturais[cite: 2]. (Origem: F-06, F-11, F-13, PQ-04)[cite: 2].

---

* **Identificador:** RN03 - Sistema protege dados individuais de desempenho em conformidade com a LGPD[cite: 2].
* **Descrição:** Os dados detalhados de desempenho individual são restritos exclusivamente ao próprio estudante[cite: 2]. A coordenação e os docentes têm acesso apenas a relatórios estatísticos agregados das turmas, sendo o acesso ao desempenho individual de um aluno permitido somente mediante consentimento explícito do titular[cite: 2]. (Origem: Seção 8, Seção 9, PQ-07)[cite: 2].

---

* **Identificador:** RN04 - Sistema realiza comparação de desempenho entre estudantes de forma opcional e anônima[cite: 2].
* **Descrição:** A exibição de métricas comparativas (como a média geral da turma ou do curso) deve ocorrer sem identificação nominal dos colegas (sem ranking público nominal) e deve ser de habilitação/visualização opcional para o estudante[cite: 2]. (Origem: PQ-12)[cite: 2].

---

* **Identificador:** RN05 - Docentes e equipe técnica estruturam questões conforme critérios pedagógicos e taxonomia padrão[cite: 2].
* **Descrição:** Toda questão cadastrada no banco deve obrigatoriamente conter enunciado, alternativas, gabarito oficial, justificativa comentada, ano de aplicação, curso/área de conhecimento e componente (Formação Geral ou Conhecimento Específico), seguindo a matriz de competências do exame[cite: 2]. (Origem: F-01, F-09, PQ-05)[cite: 2].

---

* **Identificador:** RN06 - Sistema libera o gabarito comentado somente após a submissão da resposta[cite: 2].
* **Descrição:** Durante a realização de um simulado cronometrado, o gabarito e as explicações detalhadas das questões permanecem ocultos, sendo liberados ao estudante apenas após a finalização ou encerramento do tempo do simulado[cite: 2]. Na resolução livre pelo banco de questões, a explicação é exibida imediatamente após o registro da resposta do aluno[cite: 2]. (Origem: F-02, F-03)[cite: 2].

---

* **Identificador:** RN07 - Sistema encerra automaticamente o simulado ao término do tempo estipulado[cite: 2].
* **Descrição:** Ao iniciar um simulado cronometrado, o sistema inicia a contagem regressiva conforme a duração definida pelo docente na criação do simulado[cite: 2]. Caso o tempo se esgote antes do envio manual, o sistema encerra a tentativa e registra automaticamente as respostas marcadas até aquele momento[cite: 2]. (Origem: NEC-03, F-02, F-10)[cite: 2].

---

* **Identificador:** RN08 - Docentes direcionam simulados para turmas específicas[cite: 2].
* **Descrição:** Na criação e publicação de um simulado, o docente deve vincular as turmas destinatárias (obtidas via integração com a Unifor Online) e o tempo de duração, tornando o simulado disponível exclusivamente para os estudantes matriculados nas respectivas turmas[cite: 2]. (Origem: F-10, F-12)[cite: 2].

---

* **Identificador:** RN09 - Integração institucional depende de autorização formal e sincronização controlada[cite: 2].
* **Descrição:** A obtenção de dados de alunos, turmas e disciplinas da plataforma Unifor Online (e eventuais estatísticas/provas do INEP) deve ocorrer apenas mediante autorização institucional formal, respeitando os direitos de uso do conteúdo e a minimização de dados pessoais[cite: 2]. (Origem: F-12, Seção 8, Seção 9, PQ-05, PQ-07)[cite: 2].

---

* **Identificador:** RN10 - Moderadores e docentes gerenciam postagens do fórum conforme regras de conduta[cite: 2].
* **Descrição:** *(Aplicável na evolução pós-MVP)* As interações no fórum de discussão vinculado a cada questão estão sujeitas à moderação por docentes ou monitores designados, que podem ocultar ou remover mensagens denunciadas que violem as diretrizes acadêmicas ou revelem respostas sem construtividade[cite: 2]. (Origem: F-05, PQ-01, PQ-08)[cite: 2].

---

## 2. Checklist de Validação da Regra de Negócio

### 2.1 Estrutura mínima

* [x] Identificador único e padronizado (ex.: RN1, RN1.1, RN2)[cite: 1].
* [x] Nome da regra no formato sujeito + verbo + objeto[cite: 1].
* [x] Descrição clara, direta e sem ambiguidades[cite: 1].

### 2.2 Qualidade da regra

* [x] A regra descreve apenas uma decisão/comportamento principal[cite: 1].
* [x] Condições de aplicação (gatilho/contexto) estão explícitas[cite: 1].
* [x] Resultado esperado da regra está explícito[cite: 1].
* [x] A regra é verificável e testável[cite: 1].

### 2.3 Consistência e rastreabilidade

* [x] Não há conflito com outras regras já existentes[cite: 1].
* [x] A regra referencia origem (negócio, norma, lei ou decisão do cliente), quando aplicável[cite: 1].
* [x] A regra está alinhada com CDU, RNF e demais artefatos relacionados[cite: 1].

### 2.4 Prontidão

* [ ] Conteúdo revisado por pares[cite: 1].
* [ ] Regra pronta para uso em análise, desenvolvimento e testes[cite: 1].