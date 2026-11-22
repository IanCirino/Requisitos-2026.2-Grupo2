# Especificação de Requisitos Não Funcionais

**AdE – Amigo do Estudante:** sistema web de auxílio estudantil e preparação para provas no estilo ENADE.

## Histórico de Versões

<!-- markdownlint-disable MD060 -->

| Data       | Versão | Descrição                                                                 | Autor                |
| ---------- | ------- | ------------------------------------------------------------------------- | -------------------- |
| 22/11/2026 | 0.1     | Primeira versão dos requisitos não funcionais, a partir da Visão da Demanda e do diagrama de casos de uso | Ian Carvalho Cirino  |
|            |         |                                                                           |                      |

<!-- markdownlint-enable MD060 -->

## Escopo, Premissas e Convenções

**Escopo da solução.** O AdE é um sistema web para preparação ao ENADE e a provas semelhantes. Ele oferece banco de questões, simulados cronometrados, gabarito comentado, estatísticas de desempenho, fórum por questão, painel de turmas para professores e coordenação, administração de cadastros e integração com a Unifor Online e com dados do INEP. Os atores são Estudante, Professor, Coordenação, Equipe Técnica, INEP (sistema externo) e Unifor Online (sistema externo).

**Fontes.** Visão da Demanda (VD) v0.3, diagrama de casos de uso (UC01 a UC19), catálogo de funcionalidades (F-01 a F-14), riscos e questões em aberto (PQ-01 a PQ-12).

**Premissa importante.** A VD registra que desempenho, acessibilidade, disponibilidade e compatibilidade **não foram definidos** pela instituição (VD, seção 9) e que a TI ainda deve confirmá-los (PQ-10). Por isso, **todos os valores numéricos deste documento são propostas de linha de base**, para validação com a TI da Unifor, a coordenação e o solicitante (Prof. Atila Girao De Oliveira) antes da versão definitiva.

**Convenções.**

* **ID:** `RNF-<categoria>-<nº>`.
* **Prioridade:** Alta (necessário para o MVP ou exigido por lei), Média ou Baixa.
* **Origem:** seção da VD, funcionalidade (F-xx), caso de uso (UCxx), questão em aberto (PQ-xx) ou norma.
* **MVP (PQ-01):** banco de questões (F-01), simulado cronometrado (F-02), gabarito comentado (F-03), desempenho básico (F-04) e cadastro/login institucional (F-06). Fórum (F-05), importação de PDF (F-07), classificação (F-08) e comparação com o INEP (F-14) são evolução futura ou estão em avaliação. Os requisitos desses itens estão marcados como **(evolução)**.

## 1. Requisitos de Produto

Especificam o comportamento da solução.

### 1.1. Eficiência de Desempenho

Capacidade da solução operar no tempo, rendimento e recursos definidos.

#### 1.1.1. Comportamento temporal

Capacidade da solução operar nos tempos e contextos de uso definidos.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-DES-01 | A consulta ao banco de questões com filtros por ano, curso/área e componente deve responder rapidamente. | Tempo de resposta ≤ 2 s no percentil 95, com 500 usuários simultâneos e banco de 10.000 questões. Teste de carga. | Alta | F-01, UC02 |
| RNF-DES-02 | O início de um simulado deve carregar a prova completa sem espera perceptível. | Carga inicial ≤ 3 s no percentil 95. Troca entre questões ≤ 1 s. | Alta | F-02, UC03 |
| RNF-DES-03 | O cronômetro do simulado deve ser preciso e não depender do relógio do cliente. | O horário de término é definido pelo servidor. Desvio ≤ 1 s em simulado de 4 h. O tempo restante é preservado ao recarregar a página. | Alta | F-02, UC03 |
| RNF-DES-04 | A exibição do resultado e do gabarito comentado ao fim do simulado deve ser imediata. | Resultado e gabarito exibidos ≤ 3 s após a finalização, no percentil 95. | Alta | F-03, UC04 |
| RNF-DES-05 | Os painéis de estatísticas do estudante e de turmas devem ser carregados em tempo aceitável. | Painel do estudante ≤ 3 s. Painel de turma com até 100 alunos ≤ 5 s, no percentil 95. | Média | F-04, F-11, UC05, UC09 |
| RNF-DES-06 | O login deve ser rápido. | Autenticação ≤ 3 s no percentil 95, sem contar o tempo do provedor institucional. | Alta | F-06, UC01 |
| RNF-DES-07 | A sincronização com a Unifor Online não deve afetar a navegação dos usuários. | A sincronização roda em segundo plano. Os tempos de RNF-DES-01 a RNF-DES-06 são mantidos durante a sincronização. | Média | F-12, UC16 |
| RNF-DES-08 **(evolução)** | A importação de provas em PDF do INEP deve ser assíncrona. | Prova processada em ≤ 10 min. O usuário vê o status do processamento e não fica bloqueado. | Baixa | F-07, UC17 |

#### 1.1.2. Capacidade

Capacidade da solução operar nos limites máximos de parâmetros da solução.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-DES-09 | O sistema deve suportar o pico de acesso em época de prova. | 1.000 usuários simultâneos, com 200 simulados em andamento ao mesmo tempo, atendendo RNF-DES-01 a RNF-DES-04. Teste de carga antes da entrada em produção. | Alta | PQ-10, F-02 |
| RNF-DES-10 | O banco de questões deve crescer sem perda de desempenho. | Suporte a pelo menos 10.000 questões ativas, com anexos (imagens e textos de apoio), sem violar RNF-DES-01. | Média | F-01, F-09 |
| RNF-DES-11 | O histórico de tentativas deve ser guardado por tempo suficiente para acompanhamento. | Histórico de pelo menos 5 anos letivos disponível para consulta, respeitando o ciclo de vida de dados do RNF-PRI-09. | Média | F-04, F-11 |

#### 1.1.3. Uso de recursos

Capacidade da solução operar conforme as restrições de recursos definidas.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-DES-12 | O servidor deve operar com folga sob carga nominal. | Em carga nominal (500 usuários simultâneos): CPU média ≤ 70% e memória ≤ 80%. Monitoramento com alerta acima desses limites. | Média | PQ-10 |
| RNF-DES-13 | As páginas devem ser leves para uso em dispositivos e redes modestos. | Página inicial e telas de simulado ≤ 2 MB transferidos. Funcionamento em dispositivo com 4 GB de RAM e conexão de 2 Mbps. | Média | VD seção 5 (AT-01) |
| RNF-DES-14 | O armazenamento deve ser monitorado. | Alerta quando o uso do armazenamento atingir 80% da capacidade provisionada. | Baixa | F-09, F-07 |

### 1.2. Flexibilidade (portabilidade)

Capacidade da solução adaptar-se a mudanças em seus requisitos, contextos de uso e ambientes.

#### 1.2.1. Escalabilidade

Capacidade da solução de lidar com aumento ou redução de carga de trabalho, ou adaptar sua capacidade para lidar com variações.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-FLX-01 | A solução deve escalar para novos cursos e para picos sazonais sem alteração de código. | Triplicar a carga (de 1.000 para 3.000 usuários simultâneos), apenas com ajuste de infraestrutura, mantém os tempos do RNF-DES-01 com degradação ≤ 10%. | Média | PQ-10, F-12 |
| RNF-FLX-02 | Os recursos devem poder ser reduzidos fora do período de prova. | Redução de capacidade fora de pico sem perda de dados nem indisponibilidade. | Baixa | PQ-10 |

#### 1.2.2. Adaptabilidade

Capacidade da solução ser adaptada ou transferida de forma eficaz e eficiente para diferentes ambientes de hardware, software ou operação.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-FLX-03 | A interface deve ser responsiva (computador, tablet e celular). | Funcional e sem rolagem horizontal em larguras de 360 px a 1920 px. Teste nos fluxos de UC01 a UC05. | Alta | VD seção 9 (web/mobile não definido) |
| RNF-FLX-04 | A solução deve funcionar nos navegadores atuais. | Chrome, Edge, Firefox e Safari, nas duas últimas versões estáveis. Testes manuais e automatizados de regressão. | Alta | VD seção 5 |
| RNF-FLX-05 | Endereços e credenciais de sistemas externos devem ser configuráveis. | URLs, chaves e parâmetros da Unifor Online e do INEP alterados por configuração, sem recompilar o sistema. | Média | F-12, PQ-06 |

#### 1.2.3. Instalabilidade

Capacidade da solução ser instalada e/ou desinstalada com eficácia e eficiência em um ambiente especificado.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-FLX-06 | A implantação deve ser automatizada e documentada. | A Equipe Técnica implanta uma versão nova em ≤ 1 h, seguindo apenas a documentação (script ou contêiner). | Média | VD seção 4 (Equipe Técnica) |
| RNF-FLX-07 | Deve ser possível reverter uma implantação com falha. | Rollback para a versão anterior em ≤ 30 min, sem perda de dados. | Média | RNF-CNF-04 |

#### 1.2.4. Substituibilidade

Capacidade de um produto de substituir outro produto especificado para o mesmo propósito no mesmo ambiente.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-FLX-08 | Os dados do sistema devem poder ser exportados em formato aberto. | Exportação de questões, gabaritos e resultados em CSV ou JSON, com 100% dos campos do cadastro (enunciado, alternativas, gabarito, comentário, ano, área e componente). | Média | PQ-06, F-09 |
| RNF-FLX-09 | O AdE deve complementar a PreparaEdu e a Plataforma de Questões da Unifor, sem duplicar cadastro nem conteúdo. | Usuários identificados pelo identificador institucional. Nenhum cadastro manual de usuário duplicado em relação à Unifor Online. | Média | PQ-06 |

### 1.3. Confiabilidade

Capacidade da solução de manter o desempenho sob condições específicas. Essa categoria considera as seguintes subcategorias.

#### 1.3.1. Maturidade

Capacidade da solução de funcionar sem falhas.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CNF-01 | A versão liberada para produção não deve conter defeitos graves conhecidos. | Zero defeitos críticos ou altos abertos na liberação. Registro no relatório de testes. | Alta | F-01 a F-06 |
| RNF-CNF-02 | O sistema deve ter baixa taxa de falhas em operação. | No máximo 1 falha crítica (que impede simulado, login ou consulta) por mês, medida pelo registro de incidentes. | Média | F-02, F-06 |

#### 1.3.2. Disponibilidade

Capacidade da solução estar operacional e acessível quando necessário.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CNF-03 | O sistema deve estar disponível durante o uso normal. | Disponibilidade mensal ≥ 99,5%, excluindo manutenção programada. | Alta | PQ-10 |
| RNF-CNF-04 | A disponibilidade deve ser reforçada nas janelas de simulados publicados. | Disponibilidade ≥ 99,9% durante a janela de simulados publicados para turmas (UC13) e nas duas semanas anteriores à data do ENADE. | Alta | UC13, PQ-10 |
| RNF-CNF-05 | A manutenção programada deve ter impacto mínimo. | Realizada entre 00h e 05h (horário de Brasília) e comunicada com 48 h de antecedência, sem coincidir com simulados publicados. | Média | UC13 |

#### 1.3.3. Tolerância a falhas

Capacidade da solução continuar operando conforme o esperado, mesmo na presença de falhas de hardware ou software.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CNF-06 | A indisponibilidade da Unifor Online não deve impedir o uso do AdE. | Com a Unifor Online fora do ar, usuários já sincronizados continuam acessando o sistema e fazendo simulados, com base nos dados da última sincronização. | Alta | F-12, UC16 |
| RNF-CNF-07 | A falha de conexão do estudante durante um simulado não deve causar perda de respostas. | Cada resposta é salva no servidor em ≤ 5 s. Ao reconectar, o estudante retoma de onde parou, com o cronômetro do servidor preservado. Teste com queda de rede simulada. | Alta | F-02, UC03 |
| RNF-CNF-08 | A falha do INEP ou da importação de PDF não deve afetar as demais funções. | Falha de UC17 ou UC19 não interrompe UC01 a UC16. Mensagem de erro clara ao usuário. | Baixa | F-07, F-14 |

#### 1.3.4. Recuperabilidade

Capacidade da solução para recuperar dados afetados e restabelecer o estado desejado após falha ou interrupção.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CNF-09 | Os dados devem ter backup automático e restauração testada. | Backup diário, retenção de 30 dias. RPO ≤ 24 h e RTO ≤ 4 h. Teste de restauração a cada semestre, com evidência registrada. | Alta | F-09, F-04 |
| RNF-CNF-10 | A sincronização com a Unifor Online deve se recuperar de erros. | Até 3 novas tentativas com intervalo crescente. Falha persistente gera alerta à Equipe Técnica e registro em log. Nenhum dado parcial corrompido. | Média | F-12, UC16 |

### 1.4. Segurança

Capacidade da solução para proteger as informações e garantir operações seguras.

#### 1.4.1. Confidencialidade

Capacidade da solução proteger os dados contra acesso não autorizado.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-SEG-01 | Todo tráfego deve ser criptografado. | 100% das conexões via HTTPS com TLS 1.2 ou superior. HTTP redirecionado. Verificação por ferramenta de varredura TLS. | Alta | VD seção 9 |
| RNF-SEG-02 | O acesso deve ser controlado por perfil. | Estudante acessa apenas seus dados. Professor, apenas suas turmas. Coordenação, apenas visão agregada. Equipe Técnica, apenas administração. Testes negativos de autorização para cada perfil, em 100% dos casos de uso. | Alta | F-06, F-11, PQ-07, UC01 |
| RNF-SEG-03 | Dados pessoais devem ser protegidos em repouso. | Criptografia AES-256 (ou equivalente) para dados pessoais e de desempenho individual no armazenamento e nos backups. | Alta | PQ-07 |
| RNF-SEG-04 | A comparação com a média da turma não deve expor indivíduos. | A média só é exibida para turmas com pelo menos 5 estudantes. Nenhum dado de outro aluno é identificável na resposta. | Alta | PQ-12, UC06 |
| RNF-SEG-05 | O gabarito não deve ser acessível antes do fim do simulado. | Respostas corretas e comentários não são enviados ao navegador antes da finalização. Verificação pela inspeção das respostas da API. | Alta | UC03, UC04 |

#### 1.4.2. Integridade

Capacidade da solução de garantir que os dados não sejam alterados indevidamente.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-SEG-06 | Respostas e resultados de simulados finalizados devem ser imutáveis. | Nenhuma interface ou API permite alterar respostas após a finalização. Teste de tentativa de alteração. | Alta | F-02, F-04 |
| RNF-SEG-07 | Alterações em questões, gabaritos e comentários devem ser rastreáveis. | Toda criação, edição e inativação registra usuário, data e hora, valor anterior e novo valor. | Alta | F-09, UC10, UC11 |
| RNF-SEG-08 | Entradas de usuário devem ser validadas no servidor. | Nenhuma vulnerabilidade de injeção ou XSS em varredura. Conteúdo do fórum sanitizado. | Alta | F-05, F-09 |

#### 1.4.3. Não repúdio

Capacidade da solução de impedir a negação de ações realizadas.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-SEG-09 | Ações administrativas devem ficar registradas em trilha de auditoria. | Registro de usuário, ação, data e hora para UC10, UC12, UC13, UC14, UC15 e UC16. Logs protegidos contra edição e guardados por pelo menos 12 meses. | Alta | F-09, F-10, F-13, F-12 |
| RNF-SEG-10 | A finalização de um simulado deve ter data e hora registradas. | Cada simulado finalizado possui carimbo de data e hora do servidor, consultável pelo estudante e pelo professor. | Média | F-02, F-10 |

#### 1.4.4. Autenticidade (autenticação)

Capacidade da solução de garantir que as identidades sejam genuínas.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-SEG-11 | A autenticação deve usar o login institucional. | Autenticação delegada ao provedor institucional (protocolo a confirmar com a TI). Se não for possível, senhas armazenadas com hash forte (Argon2 ou bcrypt) e senha mínima de 8 caracteres. | Alta | F-06, PQ-06, PQ-10, UC01 |
| RNF-SEG-12 | O sistema deve resistir a tentativas de acesso indevido. | Bloqueio temporário de 15 min após 5 tentativas falhas consecutivas. Sessão expira após 30 min de inatividade (exceto durante simulado em andamento). | Alta | F-06, UC01 |
| RNF-SEG-13 | Contas privilegiadas devem ter proteção adicional. | Autenticação em dois fatores para Equipe Técnica e Coordenação, quando suportada pelo provedor institucional. | Média | F-13, UC14 |

#### 1.4.5. Resistência

Capacidade da solução de proteger-se contra ataques e falhas de segurança.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-SEG-14 | A solução deve seguir boas práticas contra as vulnerabilidades mais comuns. | Aderência ao OWASP Top 10. Análise de vulnerabilidades antes de cada liberação, sem achados críticos ou altos abertos. | Alta | VD seção 9 |
| RNF-SEG-15 | O sistema deve limitar abuso de requisições. | Limite de requisições por usuário e por IP, com bloqueio e registro ao ultrapassá-lo. | Média | RNF-SEG-12 |
| RNF-SEG-16 | As dependências de software devem ser mantidas atualizadas. | Verificação automática de dependências. Vulnerabilidades críticas corrigidas em até 7 dias. | Média | F-06 |

### 1.5. Privacidade

#### 1.5.1. Licitude

Legislação normatizadora; amparo legal; excepcionalidades; aspectos jurídicos diversos.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-PRI-01 | Cada tratamento de dado pessoal deve ter base legal definida. | Base legal (Lei nº 13.709/2018, LGPD) registrada para 100% dos tratamentos e validada pelo encarregado de dados antes da produção. | Alta | PQ-07, VD seção 9 |
| RNF-PRI-02 | O acesso individual da coordenação ao desempenho de alunos exige consentimento. | Sem consentimento registrado, a coordenação só vê dados agregados. Teste de autorização. | Alta | PQ-07, UC09 |

#### 1.5.2. Finalidade

Objetivos de negócio sobre os dados pessoais.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-PRI-03 | As finalidades do tratamento devem ser declaradas e respeitadas. | Finalidades documentadas: preparação para o ENADE, acompanhamento pedagógico e gestão de acesso. Nenhum uso comercial ou publicitário dos dados. | Alta | PQ-07, PQ-09 |
| RNF-PRI-04 | O estudante deve saber quem acessa seus dados. | Aviso de privacidade acessível no cadastro e no perfil, informando finalidade, perfis com acesso e prazo de guarda. | Alta | PQ-07 |

#### 1.5.3. Necessidade

Reais necessidades de tratamento de dados pessoais.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-PRI-05 | Só devem ser coletados os dados estritamente necessários. | Dados obtidos da Unifor Online limitados a identificador, nome, e-mail institucional, curso, turma e disciplinas. Qualquer outro dado exige justificativa registrada. | Alta | F-12, PQ-07 |
| RNF-PRI-06 | O dado individual de desempenho deve ser restrito. | Dados individuais visíveis apenas ao próprio estudante e ao professor da turma. Revisão de permissões antes de cada release. | Alta | PQ-07, UC05, UC09 |

#### 1.5.4. Tratamento

Catálogo e descrição dos tratamentos de dados pessoais; ciclo de vida dos tratamentos dos dados pessoais; adequação às finalidades (proporcionalidade); compartilhamentos e integrações.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-PRI-07 | Deve existir um inventário de tratamentos de dados pessoais. | Documento com dados, finalidade, base legal, local de armazenamento, compartilhamentos e prazo de retenção, revisado a cada semestre. | Alta | PQ-07 |
| RNF-PRI-08 | O titular deve poder exercer seus direitos. | Pedidos de acesso, correção e eliminação atendidos em até 15 dias. Procedimento registrado e testado. | Alta | LGPD, PQ-07 |
| RNF-PRI-09 | Os dados devem ter ciclo de vida definido. | Desempenho individual mantido enquanto o vínculo estiver ativo e por até 12 meses depois, sendo então anonimizado ou eliminado, salvo decisão institucional diferente (a validar). | Média | PQ-07, RNF-DES-11 |
| RNF-PRI-10 | A integração com a Unifor Online não deve devolver dados pessoais. | Fluxo da Unifor Online para o AdE. Nenhum dado de desempenho individual é enviado a sistemas externos (Unifor Online ou INEP). | Alta | F-12, F-14, UC16, UC19 |
| RNF-PRI-11 | Incidentes de segurança com dados pessoais devem ser tratados com rapidez. | Equipe Técnica comunica o encarregado de dados em ≤ 24 h após a ciência do incidente. Plano de resposta documentado. | Média | PQ-07 |

### 1.6. Capacidade de Interação (UX, usabilidade e acessibilidade)

Capacidade da solução relacionar-se com os usuários em variados contextos de uso.

#### 1.6.1. Reconhecimento de adequação

Capacidade da solução de evidenciar para o usuário que ela atende às suas necessidades.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-01 | A página inicial de cada perfil deve destacar suas ações principais. | Em teste com pelo menos 5 usuários por perfil, ≥ 80% identificam em até 30 s onde iniciar um simulado (estudante) ou criar um simulado (professor). | Média | NEC-03, NEC-02 |
| RNF-USA-02 | O estudante deve ter orientação sobre o ENADE do seu curso. | Guia ou calendário por curso (data da prova, estrutura e conteúdo cobrado), caso aprovado para o MVP. | Baixa | PQ-11 |

#### 1.6.2. Facilidade de aprendizado (learnability)

Capacidade da solução de ter seu uso com baixo esforço de aprendizagem.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-03 | O estudante deve usar o sistema sem treinamento. | ≥ 80% dos participantes do teste concluem o primeiro simulado, do login ao resultado, sem ajuda. | Alta | F-02 |
| RNF-USA-04 | O professor deve criar seu primeiro simulado com pouco esforço. | Em teste de usabilidade, ≥ 80% dos professores criam e publicam um simulado em ≤ 10 min sem treinamento. | Média | F-10, UC12, UC13 |

#### 1.6.3. Operabilidade

Capacidade da solução de ser operada e controlada facilmente.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-05 | As funções principais devem estar a poucos cliques. | Banco de questões e início de simulado a no máximo 3 cliques da página inicial. | Média | F-01, F-02 |
| RNF-USA-06 | O simulado deve oferecer controle claro de tempo e navegação. | Cronômetro sempre visível. Painel de navegação mostrando questões respondidas e pendentes. Possibilidade de marcar questões para revisão. | Alta | F-02, UC03 |
| RNF-USA-07 | Os filtros do banco de questões devem ser combináveis. | Filtros por ano, curso/área e componente usados simultaneamente, com retorno do total de resultados. | Média | F-01, UC02 |

#### 1.6.4. Proteção contra erros do usuário

Capacidade da solução de evitar erros durante o uso.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-08 | Ações irreversíveis devem pedir confirmação. | Confirmação antes de finalizar simulado (com aviso de questões em branco), inativar questão ou usuário e publicar simulado. | Alta | UC03, UC10, UC13, UC14 |
| RNF-USA-09 | Erros de preenchimento devem ser evitados e explicados. | Validação em tempo real com mensagem em português indicando o campo e como corrigir. Rascunho automático ao cadastrar questão (perda máxima de 1 min de digitação). | Média | F-09, UC10 |

#### 1.6.5. Inclusividade (acessibilidade)

Capacidade da solução de ser acessível a diferentes perfis de usuários.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-10 | A interface deve atender a critérios de acessibilidade digital. | Conformidade com WCAG 2.1 nível AA (nível a confirmar com a TI). Auditoria automatizada e revisão manual nas telas de UC01 a UC05. | Alta | PQ-10, LBI |
| RNF-USA-11 | A interface deve ser compatível com leitores de tela e teclado. | Navegação completa por teclado e leitura correta em NVDA ou VoiceOver nas funções principais (login, banco, simulado, gabarito). | Alta | PQ-10 |
| RNF-USA-12 | Gráficos devem ter alternativa textual. | Todo gráfico de estatística tem tabela ou descrição textual equivalente. Contraste de texto ≥ 4,5:1. | Média | F-04, UC05, UC09 |
| RNF-USA-13 | O tempo do simulado deve poder ser ajustado para necessidades específicas. | A Equipe Técnica ou o professor define tempo adicional por estudante, registrado em auditoria. | Baixa | F-02, F-10 |

#### 1.6.6. Assistência ao usuário (acessibilidade)

Capacidade da solução de fornecer suporte e ajuda durante o uso.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-14 | O sistema deve oferecer ajuda contextual e canal de suporte. | Página de ajuda (perguntas frequentes) em cada fluxo principal. Canal de suporte com resposta em até 2 dias úteis. | Média | VD seção 4 |
| RNF-USA-15 | As mensagens de erro devem orientar o usuário. | 100% das mensagens em português, sem códigos técnicos, indicando a ação a tomar. | Média | RNF-USA-09 |

#### 1.6.7. Engajamento do usuário

Capacidade da solução de promover envolvimento e satisfação na interação.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-USA-16 | A interface deve ser agradável, rápida e sem anúncios. | Nenhum anúncio ou conteúdo de terceiros. Pontuação SUS ≥ 70 em avaliação com usuários. | Média | PQ-09 |
| RNF-USA-17 | O estudante deve acompanhar sua evolução. | Painel com evolução por área e total de simulados concluídos, atualizado até 1 min após cada simulado. | Média | F-04, PQ-02 |
| RNF-USA-18 | A adoção deve ser medida. | Indicadores coletados: percentual de concluintes cadastrados (meta inicial de 40%) e simulados concluídos por usuário. | Média | PQ-02 |

### 1.7. Manutenibilidade

Capacidade da solução de evoluir com custo baixo e sem introdução de novos erros.

#### 1.7.1. Modularidade

Capacidade da solução de limitar o impacto de alterações em um componente sobre os demais.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-MNT-01 | A solução deve ser dividida em módulos com interfaces definidas. | Módulos independentes: autenticação, banco de questões, simulados, estatísticas, fórum, administração e integrações. Documentados na arquitetura. | Alta | VD seção 8 |
| RNF-MNT-02 | As integrações externas devem ser isoladas. | Unifor Online e INEP acessados por adaptadores. A troca de um deles não altera os demais módulos. | Alta | F-12, F-07, PQ-06 |
| RNF-MNT-03 | Funcionalidades de evolução devem poder ser ativadas separadamente. | Fórum, importação de PDF, classificação e comparação com o INEP desligáveis sem afetar o MVP. | Média | PQ-01 |

#### 1.7.2. Reusabilidade

Capacidade da solução de reutilizar componentes.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-MNT-04 | As regras de negócio compartilhadas devem estar em um único componente. | Cálculo de desempenho, regra de comparação anônima e controle de acesso implementados uma única vez. Verificação em revisão de código. | Média | PQ-12, VD seção 11 |
| RNF-MNT-05 | Componentes de interface devem ser reutilizados. | Biblioteca de componentes comum (formulários, tabelas, gráficos) usada em todas as telas. | Baixa | F-04, F-11 |

#### 1.7.3. Analisabilidade

Capacidade da solução de ser avaliada de forma eficaz e eficiente quanto ao impacto de mudanças, diagnóstico de falhas ou identificação de partes a serem modificadas.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-MNT-06 | O sistema deve gerar logs estruturados e monitoramento. | Logs com nível, data, módulo e identificador de requisição, sem dados pessoais em texto aberto. Alertas para erros e indisponibilidade. | Alta | RNF-CNF-03 |
| RNF-MNT-07 | Falhas em produção devem ser diagnosticáveis rapidamente. | A causa de uma falha simulada é localizada pela Equipe Técnica em ≤ 1 h usando apenas logs e documentação. | Média | RNF-CNF-02 |
| RNF-MNT-08 | A arquitetura e os contratos de integração devem estar documentados. | Documentos de arquitetura, modelagem UML e contratos (Unifor Online e INEP) atualizados a cada versão. | Média | VD seção 11 |

#### 1.7.4. Modificabilidade

Capacidade da solução de ser modificada de forma eficaz e eficiente sem introduzir defeitos ou degradar a qualidade existente.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-MNT-09 | Novos cursos, áreas e componentes devem ser incluídos sem alteração de código. | Inclusão feita apenas pela tela de cadastros de apoio, em ≤ 5 min. | Alta | F-13, UC15 |
| RNF-MNT-10 | O código deve seguir padrões e análise estática. | Linter e formatador no pipeline, sem erros bloqueantes. Revisão de código por pares em 100% das alterações. | Média | RNF-DEV-03 |

#### 1.7.5. Testabilidade

Capacidade da solução de permitir que testes objetivos e viáveis sejam projetados e executados para verificar se um requisito foi atendido.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-MNT-11 | As regras de negócio devem ter testes automatizados. | Cobertura ≥ 70% nos módulos de regras de negócio. Testes executados a cada alteração. | Alta | RNF-ADF-02 |
| RNF-MNT-12 | Cada requisito deve ter critério de aceitação e teste. | 100% dos requisitos funcionais do MVP e dos requisitos de prioridade Alta deste documento com pelo menos 1 caso de teste associado. | Alta | Template LAPIS |
| RNF-MNT-13 | Deve existir ambiente de testes separado e sem dados reais. | Ambiente de homologação com dados sintéticos ou anonimizados. Integrações simuladas (mocks) para Unifor Online e INEP. | Média | PQ-07, F-12 |

### 1.8. Compatibilidade

Capacidade da solução trocar informações e coexistir com outras soluções.

#### 1.8.1. Interoperabilidade

Capacidade da solução de trocar e usar as informações com outras soluções.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CMP-01 | O sistema deve obter turmas, alunos e disciplinas da Unifor Online por API. | Sincronização automática diária e sob demanda na virada de semestre. Carga completa em ≤ 30 min, com ≥ 99% dos registros importados sem erro. Falhas listadas em relatório. | Alta | F-12, UC16 |
| RNF-CMP-02 | Os formatos de integração devem ser documentados. | Contrato da API da Unifor Online (formato, campos, autenticação) documentado e validado com a TI antes do desenvolvimento. | Alta | PQ-06, PQ-10 |
| RNF-CMP-03 **(evolução)** | A importação de PDF do INEP deve ser confiável. | Pelo menos 90% dos enunciados e alternativas extraídos corretamente em amostra de 3 provas. Toda questão importada passa por revisão humana antes de publicada. | Baixa | F-07, UC17, PQ-05 |
| RNF-CMP-04 **(evolução)** | Estatísticas oficiais do INEP devem entrar em formato aberto. | Importação de dados oficiais em CSV ou planilha para a comparação (UC19), com validação do formato. | Baixa | F-14, UC19 |

#### 1.8.2. Coexistência

Capacidade da solução compartilhar ambiente e recursos com outras soluções.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-CMP-05 | O AdE não deve prejudicar a Unifor Online. | Sincronização fora do horário de pico e com limite de requisições definido com a TI. Sem impacto medido no desempenho da Unifor Online. | Média | F-12, UC16 |
| RNF-CMP-06 | O AdE deve usar a mesma identidade institucional das demais plataformas. | O mesmo identificador de usuário da Unifor Online, sem novo cadastro e sem conflito de identidade. | Média | PQ-06 |

### 1.9. Segurança Operacional (safety)

Capacidade da solução ser segura em relação aos riscos operacionais.

> **Justificativa geral:** o AdE é uma aplicação web educacional, sem controle de equipamentos e sem risco físico a pessoas, propriedades ou ao ambiente. As preocupações de proteção de dados e de continuidade estão tratadas em 1.3 (Confiabilidade) e 1.4 (Segurança).

#### 1.9.1. Restrição operacional

Capacidade da solução de restringir sua operação a parâmetros ou estados seguros ao encontrar perigos operacionais.

Não se aplica.

#### 1.9.2. Identificação de riscos

Capacidade da solução de identificar eventos ou operações que possam expor pessoas, propriedades ou o ambiente a riscos inaceitáveis.

Não se aplica.

#### 1.9.3. Segurança contra falhas (fail-safe)

Capacidade da solução entrar automaticamente em modo seguro ou retornar a uma condição segura em caso de falha.

Não se aplica a riscos físicos. O comportamento seguro em caso de falha durante simulados está em RNF-CNF-06 e RNF-CNF-07.

#### 1.9.4. Aviso de perigo

Capacidade da solução de fornecer alertas sobre riscos inaceitáveis para que ações corretivas possam ser tomadas a tempo.

Não se aplica.

#### 1.9.5. Integração segura

Capacidade da solução de manter a segurança durante e após a integração com outros componentes.

Não se aplica a riscos físicos. A segurança das integrações com a Unifor Online e o INEP está em RNF-PRI-10, RNF-SEG-14 e RNF-CMP-02.

### 1.10. Adequação funcional

Capacidade da solução de fornecer funções que atendam às necessidades dos usuários.

#### 1.10.1. Completude funcional

Capacidade da solução de cobrir todas as tarefas e objetivos especificados.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-ADF-01 | O MVP deve cobrir todas as funcionalidades acordadas. | 100% de F-01, F-02, F-03, F-04 e F-06 implementadas e aceitas, com os casos de uso UC01 a UC05 e UC11 homologados. | Alta | PQ-01 |
| RNF-ADF-02 | Cada caso de uso do escopo deve ter especificação e critérios de aceitação. | 100% dos casos de uso do escopo entregue com especificação e pelo menos 1 critério de aceitação verificável. | Alta | VD seção 11 |

#### 1.10.2. Corretude funcional

Capacidade da solução de fornecer resultados precisos e corretos.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-ADF-03 | Os cálculos de desempenho devem estar corretos. | 100% de acerto em casos de teste de nota, percentual de acertos e estatísticas por área. | Alta | F-04, F-11 |
| RNF-ADF-04 | Toda questão publicada deve ter gabarito e comentário completos. | 100% das questões usadas em simulados possuem alternativa correta, comentário que justifica todas as alternativas e referência bibliográfica. | Alta | PQ-05, F-03, UC11 |
| RNF-ADF-05 | O conteúdo das questões deve ser fiel às provas e à matriz do exame. | Revisão por docente em amostra de 100% das questões cadastradas na carga inicial, com registro do revisor. | Média | PQ-05, F-09 |

#### 1.10.3. Adequação funcional

Capacidade da solução de facilitar a realização das tarefas de forma eficaz.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-ADF-06 | O estudante deve completar o fluxo principal sem assistência. | Em teste de usabilidade, ≥ 90% concluem o fluxo "consultar questão, fazer simulado e ver resultado e gabarito". | Alta | NEC-03, NEC-06 |
| RNF-ADF-07 | O professor deve completar o fluxo de simulado sem assistência. | ≥ 90% concluem "montar simulado, publicar para a turma e ver desempenho". | Média | NEC-02, NEC-05 |

## 2. Requisitos Externos

Derivados de fatores externos à solução e ao seu processo de desenvolvimento.

### 2.1. Ético

Capacidade da solução operar de acordo com critérios de aceitação dos usuários e do público geral.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-ETI-01 | A comparação de desempenho entre estudantes deve ser opcional e anônima, sem ranking identificado. | Nenhum ranking nominal na interface. A comparação com a média da turma exige ação do estudante. | Alta | PQ-12, UC06 |
| RNF-ETI-02 | O fórum deve ter regras de conduta e denúncia de mensagens. | Regras aceitas no primeiro acesso. Mensagem denunciada é analisada pela moderação em até 2 dias úteis. **(evolução)** | Média | PQ-08, F-05, UC08 |
| RNF-ETI-03 | O sistema não deve exibir anúncios nem usar dados para fins comerciais. | Ausência de anúncios e de rastreadores de terceiros em varredura. | Alta | PQ-09 |
| RNF-ETI-04 | O conteúdo pedagógico deve citar suas fontes. | Todo comentário de gabarito traz referência bibliográfica. Todo uso de prova do INEP indica a fonte. | Média | PQ-05 |

### 2.2. Regulatório

Capacidade da solução operar de acordo com critérios de entidades reguladoras.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-REG-01 | O uso das provas do INEP deve respeitar as condições de uso do órgão. | Verificação documentada das condições de uso antes da publicação de qualquer questão oficial. | Alta | PQ-05, VD seção 9 |
| RNF-REG-02 | O conteúdo deve ser coerente com a matriz de competências do ENADE. | Cada questão classificada por componente e competência, com revisão pela coordenação. | Média | PQ-05, F-08 |
| RNF-REG-03 | O sistema deve cumprir as políticas de TI e de proteção de dados da Unifor. | Aprovação da TI e do encarregado de dados antes da entrada em produção. | Alta | PQ-07, PQ-10 |

### 2.3. Legislativo

Capacidade da solução de operar conforme leis, normas e acórdãos.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-LEG-01 | O tratamento de dados pessoais deve estar em conformidade com a LGPD (Lei nº 13.709/2018). | Checklist de conformidade (RNF-PRI-01 a RNF-PRI-11) aprovado pelo encarregado de dados. | Alta | VD seção 9, PQ-07 |
| RNF-LEG-02 | A solução deve observar a Lei Brasileira de Inclusão (Lei nº 13.146/2015) quanto à acessibilidade digital. | Atendimento a RNF-USA-10 a RNF-USA-12. | Alta | PQ-10 |
| RNF-LEG-03 | O uso de provas e textos de terceiros deve respeitar a Lei de Direitos Autorais (Lei nº 9.610/1998). | Fonte e autorização (ou enquadramento legal) registradas para cada conjunto de questões importado. | Alta | PQ-05 |
| RNF-LEG-04 | O sistema deve guardar registros de acesso conforme o Marco Civil da Internet (Lei nº 12.965/2014), quando aplicável. | Registros de acesso guardados por pelo menos 6 meses, com proteção de integridade. Aplicabilidade a confirmar com o jurídico da instituição. | Média | RNF-SEG-09 |

## 3. Requisitos Organizacionais

Derivados de políticas e procedimentos do cliente e do fornecedor.

### 3.1. Ambientais

Especificam o ambiente operacional da solução.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-AMB-01 | A solução deve ser um sistema web, acessível por navegador, sem instalação no dispositivo do usuário. | Acesso e uso completo por navegador, conforme RNF-FLX-03 e RNF-FLX-04. | Alta | VD seção 5 |
| RNF-AMB-02 | O ambiente de hospedagem deve ser definido e aprovado pela TI da Unifor. | Decisão registrada (infraestrutura própria ou nuvem) antes do início do desenvolvimento. **A definir.** Preferência por hospedagem no Brasil. | Alta | PQ-10 |
| RNF-AMB-03 | O sistema deve usar o horário de Brasília para simulados e relatórios. | Datas e horas exibidas e registradas em UTC-3 (America/Fortaleza e America/Sao_Paulo), com armazenamento em UTC. | Média | F-02 |
| RNF-AMB-04 | O sistema deve poder ser acessado pela rede da instituição e pela internet. | Acesso externo sem VPN, protegido conforme RNF-SEG-01 a RNF-SEG-14. | Média | VD seção 5 (AT-01) |

### 3.2. Operacionais

Especificam como a solução será utilizada.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-OPE-01 | A Equipe Técnica deve administrar usuários, perfis e cadastros de apoio. | Procedimento operacional documentado para UC14 e UC15, com os perfis e permissões definidos na especificação (SRS). | Alta | F-13, PQ-04 |
| RNF-OPE-02 | Os comentários dos gabaritos devem ter responsáveis definidos. | Docentes elaboram os comentários (grupo piloto de voluntários por curso). Disponibilidade confirmada com as coordenações. | Média | PQ-08, UC11 |
| RNF-OPE-03 | A moderação do fórum deve ter responsáveis e regras. | Moderadores (docentes ou monitores) definidos antes da ativação do fórum. **(evolução)** | Baixa | PQ-08, UC08 |
| RNF-OPE-04 | A carga inicial do banco de questões deve ser manual ou por planilha. | Procedimento documentado de cadastro e de importação por planilha. Extração automática de PDF apenas na evolução. | Alta | PQ-05, UC10 |
| RNF-OPE-05 | A operação deve prever o pico de uso em época de prova. | Plano de capacidade e de comunicação revisado ao menos 30 dias antes do ENADE. | Média | PQ-10, RNF-DES-09 |
| RNF-OPE-06 | A virada de semestre deve ser tratada com rotina de sincronização. | Rotina documentada para atualizar turmas e alunos, conferida em até 3 dias após o início do semestre. | Média | F-12, UC16 |

### 3.3. Desenvolvimento

Especificam linguagens, ambientes e padrões de processo de desenvolvimento.

| ID | Requisito | Critério de verificação | Prioridade | Origem |
| --- | --- | --- | --- | --- |
| RNF-DEV-01 | A pilha tecnológica (linguagens, framework e banco de dados) deve ser definida e justificada. | Decisão técnica registrada no documento de arquitetura. **A definir.** | Alta | VD seção 8 |
| RNF-DEV-02 | O código deve ficar sob controle de versão. | Repositório Git com histórico de alterações e ramificações para entregas. | Alta | VD seção 6.4 |
| RNF-DEV-03 | As alterações devem passar por revisão e integração contínua. | Toda alteração integrada por revisão de pares, com testes e análise estática automáticos antes da integração. | Média | RNF-MNT-10, RNF-MNT-11 |
| RNF-DEV-04 | A documentação do projeto deve seguir os artefatos previstos. | Entregas: Documento de Visão, SRS, modelagem UML (casos de uso, classes, sequência e atividades) e protótipos de interface, nas datas dos marcos (SRS e UML em 23/11/2026). | Alta | VD seção 6.4 |
| RNF-DEV-05 | A privacidade e a segurança devem ser consideradas desde o projeto. | Requisitos de privacidade e segurança revisados em cada entrega de projeto e antes da produção. | Alta | PQ-07, RNF-PRI-07 |
| RNF-DEV-06 | O desenvolvimento deve respeitar o MVP e a priorização combinada. | Funcionalidades de evolução (F-05, F-07, F-08, F-14) só são desenvolvidas após validação formal do MVP pelo solicitante. | Alta | PQ-01 |

## 4. Checklist de Validação do Artefato (RNF)

Use este checklist antes de concluir a versão do documento.

### 4.1. Estrutura e escopo

* [x] O documento possui histórico de versões preenchido.
* [x] O escopo da solução está claro no documento.
* [x] Há requisitos registrados nas seções aplicáveis (produto, externos e organizacionais).
* [x] Requisitos não aplicáveis estão explicitamente marcados como "Não se aplica", quando necessário.

### 4.2. Qualidade dos requisitos

* [x] Cada requisito está escrito de forma objetiva e verificável.
* [x] Cada requisito possui critério mensurável (tempo, percentual, limite, condição ou evidência).
* [x] Não há requisito ambíguo com termos vagos (ex.: "rápido", "seguro", "fácil") sem métrica.
* [x] Requisitos duplicados ou conflitantes foram eliminados.

### 4.3. Conformidade e rastreabilidade

* [x] Requisitos regulatórios/legais relevantes foram registrados.
* [x] Requisitos de privacidade e segurança foram contemplados quando aplicáveis.
* [ ] Os requisitos estão alinhados com visão da demanda, glossário e casos de uso. *(Alinhados com a visão e com os casos de uso. O glossário ainda está "a elaborar" na VD.)*
* [x] Existe rastreabilidade dos requisitos para fontes de negócio, norma ou decisão técnica.

### 4.4. Prontidão para uso

* [x] Os requisitos podem ser usados como base para implementação e testes.
* [x] Há insumos suficientes para criar critérios de aceitação.
* [ ] O documento foi revisado por pares.
* [ ] A versão está pronta para aprovação/publicação. *(Depende da validação dos valores propostos com a TI, a coordenação e o solicitante.)*
