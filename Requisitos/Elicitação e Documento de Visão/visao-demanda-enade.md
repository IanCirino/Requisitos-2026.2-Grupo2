![capa do texto](../Imagens/Amigo_do_Estudante_Aprenda_e_Conquiste.png)

# Visão da Demanda (VD) — Software de auxílio estudantil e preparação para o ENADE

## Identificação e Histórico 

| Campo | Informação |
| --- | --- |
| Nome e identificador da demanda | AdE - Amigo do Estudante: Sistema web de auxílio estudantil e preparação para provas no estilo ENADE |
| Tipo | Novo sistema |
| Sistema ou produto relacionado | QEnade, Descomplica, Qconcurso, PreparaEdu |
| Área solicitante | Coordenação UNIFOR |
| Responsável pela elaboração | Ian Carvalho Cirino - Desenvolvedor/Estudante |
| Responsável pela validação | Prof. Me. Marcelo Bezerra De Alcantara - Docente Avaliador ; Prof. Me. Atila Girao De Oliveira - Representante da demanda e Avaliador|
| Situação do documento |  Finalização do documento de visão |
| Versão e data | 0.3 — 14/11/2026 |

| Data | Versão | Descrição da alteração | Autor |
| --- | --- | --- | --- |
| 01/11/2026 | 0.1 | Criação da primeira versão do VD | Ian Carvalho Cirino |
| 06/11/2026 | 0.2 | Elicitação dos Requisitos | Ian Carvalho Cirino |
| 14/11/2026 | 0.3 | Finalização do documento de visão | Ian Carvalho Cirino |

> **Origem das informações:** todo o conteúdo abaixo vem dos documentos PROJETO DE EXTENSÃO -ENADE- REQUISITOS E MODELAGEM DE SISTEMAS, Propostas_Projetos_Internacionalizacao_ENADE_Unifor e entrevistas com o Professor Marcelo Bezerra. O que não consta nele está marcado como **A definir** ou como hipótese.

## 1. Objetivo

Permitir que estudantes se preparem para o ENADE e provas semelhantes com questões comentadas, simulados cronometrados e acompanhamento do próprio desempenho. Permitir que coordenadores e docentes mantenham o conteúdo, o acesso ao sistema e leiam as estatísticas dos desempenhos dos alunos.

## 2. Contexto, Problema e Descrição Sumária da Demanda

- **Situação atual:** o ENADE é componente curricular obrigatório e indicador fundamental da qualidade do ensino superior brasileiro. Segundo a demanda, os estudantes enfrentam dificuldades no preparo. Não há descrição de como eles se preparam hoje (**a definir**, por entrevistas ou questionários).
- **Problema ou oportunidade:** faltam materiais organizados, simulados práticos e feedback sobre o desempenho dos estudantes.
- **Públicos afetados e impactos:** estudantes que farão o ENADE ou provas similares (dificuldade de preparo), coordenação dos cursos e professores. Juntamente com administradores técnicos do sistema.
- **Evidências disponíveis:** apenas a afirmação dos documentos de demanda e das declarações verbais dos solicitantes. Não há, no momento, dados, pesquisas ou exemplos coletados que a sustentem. Tratar o problema como **hipótese** até o levantamento com os interessados.
- **Descrição sumária da demanda:** sistema web com banco de questões organizado por ano, curso/área e componente, simulados cronometrados, gabarito comentado, estatísticas de desempenho, fórum de discussão por questão e cadastro/autenticação de estudantes e administradores.


## 3. Proposta de Valor e Sucesso da Demanda

| Benefício esperado | Indicador ou evidência | Resultado desejado | Como e quando avaliar |
| --- | --- | --- | --- |
| Preparo mais organizado para o ENADE | A definir (situação atual desconhecida) | A definir | A definir |
| Prática realista do exame | A definir | A definir | A definir |
| Compreensão dos conceitos por meio de respostas explicadas | A definir | A definir | A definir |
| Visão do próprio desempenho por área de conhecimento | A definir | A definir | A definir |
| Aprendizado colaborativo entre usuários | A definir | A definir | A definir |

## 4. Partes Interessadas

| Parte interessada | Papel e interesse | Responsabilidade | Representante |
| --- | --- | --- | --- |
| Estudantes | Usuários finais. Querem se preparar para o ENADE e similares| Fornecer necessidades e validar a solução, quando houver acesso | Josué Pereira - curso: ADS |
| Coordenação dos cursos | Mantêm o acesso ao desempenho das turmas | Coletar os dados para análise posterior e manter o controle de cadastros | Prof. Me. Atila Girao De Oliveira |
| Docentes | Auxiliar os alunos por meio do sistema| Criar questões e simulados, e analisar o desempenho individual dos alunos | Prof. Me. Marcelo Bezerra De Alcantara |
| Equipe Técnica |  Manter o sistema em funcionamento | Gerenciar, administrar e atualizar o sistema a nível de software| Ian Carvalho Cirino |
| Solicitante da demanda | Origem da demanda | Decidir escopo e validar a visão | Prof. Me. Atila Girao De Oliveira  |
| Equipe de requisitos | Elabora a VD e as especificações | Elicitação, especificação e documentação | Ian Carvalho Cirino |
| Comunidade acadêmica | Público da apresentação final | Receber o pitch do projeto |Prof. Me. Marcelo Bezerra De Alcantara |

## 5. Usuários e Atores Externos

| ID | Usuário, sistema ou dispositivo | Objetivo ou papel na interação | Contexto de uso relevante |
| --- | --- | --- | --- |
| AT-01 | Estudante | Estuda questões, faz simulados, consulta gabaritos comentados e estatísticas e participa do fórum | Acesso via web. |
| AT-02 | Equipe Técnica | Gerencia o sistema e os cadastros. | Manutenção do Sistema. |
| AT-03 | Coordenação | Ter um feedback geral do desempenho das turmas e dos alunos| Leitura dos dados via web. |
| AT-04 | Professores | Criar simulados, questões e ter um feedback do desempenho dos seus alunos  | Leitura dos dados e implementação de questões e simulados via web.|
| AT-05 | INEP  | Fonte das provas e das estatísticas oficiais |  Uso de provas do INEP. |
| AT-06 | Unifor Online | Plataforma fonte dos dados das turmas, alunos e disciplinas | Uso dos dados e APIs. |

## 6. Escopo e Entregas Previstas

### 6.1. Incluído na demanda

- Banco de questões organizado por ano, curso/área de conhecimento e componente (formação geral e conhecimento específico).
- Simulados com tempo cronometrado.
- Gabarito comentado, com explicações detalhadas das respostas.
- Estatísticas de desempenho por área de conhecimento, com visualizações gráficas.
- Fórum de discussão por questão.
- Cadastro e autenticação segura de estudantes e administradores.

### 6.2. Fora do escopo

- Não foram definidas exclusões. **A definir** pela equipe.
- A demanda informa que não é obrigatório implementar todas as funcionalidades e que o produto mínimo deve ser definido na análise. Ver PQ-01.

### 6.3. Evoluções futuras — opcional

- Itens da proposta "Plataforma de Gestão do Conhecimento e Aprendizagem": importação de provas em PDF do INEP, classificação por temas e competências, relação com a grade curricular e apoio a ações de reforço. Estão **em avaliação** (F-07 e F-08), sem compromisso.

### 6.4. Entregas e marcos — quando conhecidos

| Entrega ou marco | Resultado previsto | Data ou condição | Natureza do prazo |
| --- | --- | --- | --- |
| Documento de Visão | Problema, público-alvo e necessidades do negócio definidos | 02/11/26 | Primeira versão - Rascunho |
| Requisitos elicitados | Técnicas aplicadas (entrevistas, questionários) e resultados obtidos | 02/11/26 | Primeira versão - Rascunho|
| Especificação de Requisitos (SRS) | Requisitos funcionais e não funcionais completos | 23/11/26 | Versão definitiva ou próxima a definitiva |
| Modelagem UML | Diagramas de Caso de Uso, Classes, Sequência e Atividades | 23/11/26| Versão definitiva ou próxima a definitiva|
| Protótipos de interface | Wireframes de média ou alta fidelidade das principais telas | 23/11/26 | Primeira versão - Rascunho |
| Apresentação final | Pitch do projeto para a comunidade acadêmica | 30/11/26 | Entrega Final |

## 7. Necessidades e Catálogo de Funcionalidades

| ID | Necessidade | Fonte ou evidência | Públicos ou atores relacionados |
| --- | --- | --- | --- |
| NEC-01 | Ter materiais de estudo do ENADE organizados fornecido pela INEP | Documento Propostas Projetos Internacionalizacao ENADE Unifor | AT-01, AT-04, AT-05, AT-06|
| NEC-02 | Permitir que os professores criem simulados, com as respostas comentadas ao final, para os alunos | Documento Projeto De Extensão -Enade- Requisitos E Modelagem De Sistemas| AT-04, AT-05, AT-06 |
| NEC-03 | Praticar com simulados em condições próximas às do exame | Documento Projeto De Extensão -Enade- Requisitos E Modelagem De Sistemas | AT-01|
| NEC-04 | Receber feedback sobre o próprio desempenho | Documento Projeto De Extensão -Enade- Requisitos E Modelagem De Sistemas | AT-01 |
| NEC-05 | Receber feedback sobre o desempenho dos alunos | Documento Projeto De Extensão -Enade- Requisitos E Modelagem De Sistemas | AT-03, AT-04 |
| NEC-06 | Compreender os conceitos por trás das respostas | Entrevista com o Prof. Marcelo| AT-01 |
| NEC-07 | Garantir acesso seguro e administração do sistema | Documento Projeto De Extensão -Enade- Requisitos E Modelagem De Sistemas| AT-02 |
| NEC-08 | Obter provas do INEP de forma ágil e classificá-las por tema, competência e grade curricular | Documento Propostas Projetos Internacionalizacao ENADE Unifor| AT-04, AT-05, AT-06 |

### 7.2 Catálogo de funcionalidades (com estimativas)


| ID | Funcionalidade e resultado esperado | Necessidade | Atores (IDs) | Prioridade | Valor | Frequência | Escopo ou entrega | Especificação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| F-01 | **Banco de questões:** consultar questões organizadas por ano, curso/área e componente (formação geral e conhecimento específico) | NEC-01 | AT-01, AT-02, AT-04 | Alta | Alto | Diária (estudantes); Semanal (professores e equipe técnica) | Entrega | A elaborar |
| F-02 | **Simulados cronometrados:** realizar simulados com tempo controlado, em condições próximas às do exame | NEC-03 | AT-01 | Alta | Alto | Semanal, com aumento perto da data do exame | Entrega | A elaborar |
| F-03 | **Gabarito comentado:** consultar explicações detalhadas das respostas ao final do simulado e em cada questão | NEC-02, NEC-06 | AT-01, AT-04 | Alta | Alto | Diária (estudantes); Eventual (equipe técnica) | Entrega | A elaborar |
| F-04 | **Estatísticas de desempenho do estudante:** ver análise do próprio desempenho por área de conhecimento, com gráficos | NEC-04 | AT-01 | Média | Alto | Semanal | Entrega | A elaborar |
| F-05 | **Fórum de discussão:** interagir com outros usuários em cada questão, para esclarecer conceitos, com moderação | NEC-06 | AT-01, AT-02, AT-04 | Baixa | Médio | Semanal (estudantes); Diária (moderação, se houver volume) | Entrega | A elaborar |
| F-06 | **Cadastro e autenticação:** cadastrar e autenticar estudantes, professores, coordenação e equipe técnica de forma segura, com controle de acesso por perfil | NEC-07 | AT-01, AT-02, AT-03, AT-04 | Alta | Alto | Diária (login a cada acesso); Eventual (cadastro) | Entrega | A elaborar |
| F-07 | **Importação de provas em PDF do INEP** (hipótese, proposta da seção 5) | NEC-08 | AT-02, AT-04 (fonte: AT-05) | Baixa | Médio | Anual (a cada nova edição do exame) | Em avaliação | A elaborar, se confirmada |
| F-08 | **Classificação por temas e competências e relação com a grade curricular** | NEC-08 | AT-02, AT-04 | Média | Médio | Mensal (concentrada na carga inicial e em novas edições) | Em avaliação | A elaborar |
| F-09 | **Cadastro de questões:** cadastrar, editar e inativar questões (enunciado, alternativas, gabarito, comentário, ano, área e componente) | NEC-01, NEC-02, NEC-08 | AT-02, AT-04 | Alta | Alto | Semanal (alta na carga inicial) | Entrega | A elaborar |
| F-10 | **Criação e gestão de simulados:** montar simulados a partir do banco de questões, definir tempo e turmas destinatárias e publicá-los para os alunos | NEC-02 | AT-04 | Alta | Alto | Mensal (maior perto do exame) | Entrega | A elaborar |
| F-11 | **Painel de desempenho de turmas e alunos:** acompanhar o desempenho por turma, aluno e área de conhecimento (professores: suas turmas; coordenação: visão geral) | NEC-05 | AT-03, AT-04 | Média | Alto | Semanal (professores); Mensal (coordenação) | Entrega | A elaborar |
| F-12 | **Integração com a Unifor Online:** obter turmas, alunos e disciplinas via dados e APIs da plataforma | NEC-02, NEC-05, NEC-07 | AT-02, AT-06 | Alta | Alto | Diária (sincronização automática); Semestral (virada de turmas) | Entrega | A elaborar |
| F-13 | **Administração do sistema e dos cadastros:** gerir usuários, perfis, cursos, áreas e demais cadastros de apoio | NEC-07 | AT-02 | Média | Médio | Semanal (alta no início, depois eventual) | Entrega | A elaborar |
| F-14 | **Comparação com estatísticas oficiais do INEP** (hipótese: confrontar o desempenho dos alunos com dados oficiais) | NEC-04, NEC-05 | AT-01, AT-03, AT-04 (fonte: AT-05) | Baixa | Médio | Eventual (anual, após a divulgação dos dados) | Em avaliação | A elaborar, se confirmada |

## 8. Visão Geral da Solução e Impactos

- **Responsabilidades da solução:** manter o banco de questões e os gabaritos comentados, executar simulados cronometrados, calcular e exibir estatísticas de desempenho, oferecer o fórum por questão e gerenciar cadastro e autenticação.
- **Sistemas ou dispositivos externos:** a definir. Hipóteses: INEP (provas e estatísticas), PreparaEdu e Plataforma de Questões e Avaliações da Unifor (possível relação, a investigar).
- **Integrações principais:** não definidas. A demanda condiciona integrações com plataformas institucionais ou dados pessoais a autorização, acesso e observância da LGPD.
- **Diagrama de contexto — opcional:** não se aplica por ora.
- **Arquitetura e contratos detalhados:** a elaborar.

### 8.1. Sistemas e processos impactados

| Sistema ou processo | Impacto esperado | Responsável ou dependência | Situação |
| --- | --- | --- | --- |
|Unifor Online | Sistema a ser integrado | Ian Carvalho Cirino| Confirmado |
| Provas do INEP | Possível fonte de questões | INEP; direitos de uso a validar | Confirmado |

### 8.2. Representações visuais — opcionais

- **Mapa de histórias ou diagrama geral de casos de uso:** a elaborar na especificação (a demanda prevê diagramas de casos de uso).
- **Protótipo de baixa fidelidade:** a demanda prevê wireframes de média ou alta fidelidade das principais telas; a elaborar.
- **Diagramas de componentes/implantação:** não se aplica por ora.

## 9. Condições Gerais da Demanda

| Tipo | Condição e impacto na demanda | Responsável ou fonte | Referência, se houver |
| --- | --- | --- | --- |
| Restrição | A demanda pode ser adaptada conforme a viabilidade do semestre | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra| — |
| Restrição | Não se exige implementar todas as funcionalidades. O produto mínimo e os limites do sistema fazem parte da análise | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra | — |
| Dependência | Integrações com plataformas institucionais ou dados pessoais dependem de autorização e acesso | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra | — |
| Regra geral | Observância da LGPD no tratamento de dados pessoais | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra | — |
| Premissa | Direitos de uso das provas do INEP e a qualidade da extração dos PDFs precisam ser validados antes de se contar com a importação | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra | — |
| Qualidade | O cadastro e a autenticação devem ser seguros. Outros requisitos de qualidade (desempenho, acessibilidade, disponibilidade, compatibilidade web/mobile) não foram definidos | Documentos do projeto enade e declarações dos prof. Marcelo Bezerra| — |

## 10. Riscos e Questões em Aberto

| ID | Tipo | Risco ou questão | Impacto | Próxima ação | Responsável e prazo | Situação |
| --- | --- | --- | --- | --- | --- | --- |
| PQ-01 | Decisão pendente | Qual é o produto mínimo e quais funcionalidades entram na entrega? | Escopo indefinido para a especificação | Formalizar o produto mínimo indicado nas entrevistas (banco de questões com filtros F-01, simulado cronometrado F-02, gabarito comentado F-03, desempenho básico F-04 e cadastro com login institucional). Fórum (F-05) e F-07/F-08 ficam como evolução futura. Registrar a decisão e obter a validação do solicitante | Equipe de requisitos (Ian) com o Prof. Atila, até 18/11/26 | Em andamento: proposta de MVP definida nas entrevistas, aguardando validação formal |
| PQ-02 | Dúvida | Não há evidências nem indicadores do problema, nem da situação atual de preparo dos estudantes | Não é possível medir o sucesso nem priorizar | As entrevistas indicaram preparo tardio e informal, provas em PDF dispersas, ausência de gabarito explicado e ações pontuais da coordenação. Falta obter dados quantitativos (participação em aulões, desempenho por curso nos relatórios do INEP) e ampliar a amostra de estudantes. Definir como indicadores iniciais o percentual de concluintes cadastrados (meta de 40%) e simulados concluídos por usuário | Equipe de requisitos (Ian), com apoio da coordenação, até 20/11/26 | Parcialmente respondido: evidências qualitativas coletadas, dados quantitativos pendentes |
| PQ-03 | Decisão pendente | A demanda traz duas propostas (Gestão do Conhecimento e Aprendizagem; Gestão Acadêmica e Inteligência) e pede selecionar uma e justificar. Esta VD se baseia no escopo geral, mais próximo da primeira proposta | Risco de escopo desalinhado | Selecionar a proposta de Gestão do Conhecimento e Aprendizagem, com os critérios de valor, viabilidade, risco e prazo, e registrar a decisão do solicitante. Manter a proposta de Inteligência do ENADE como evolução futura | Equipe de requisitos (Ian) e Prof. Atila, até 18/11/26 | Em andamento: solicitante indicou a primeira proposta, falta registrar a justificativa na VD |
| PQ-04 | Dúvida | Outros perfis (docentes, coordenações, moderadores) e as atribuições do administrador no conteúdo, no gabarito e no fórum | Atores e funcionalidades incompletos | Incluir na VD o perfil docente/coordenador (elabora conteúdo e consulta relatórios agregados) e o moderador (docente ou monitor). Definir o administrador como equipe de apoio acadêmico/TI e detalhar as permissões de cada perfil na SRS | Equipe de requisitos (Ian), até 21/11/26 | Parcialmente respondido: perfis identificados, permissões a detalhar |
| PQ-05 | Risco | Direitos de uso, qualidade da extração e critérios pedagógicos das provas do INEP | Inviabilidade ou retrabalho do banco de questões | Investigar as condições de uso das provas do INEP, adotar cadastro manual ou por planilha no início (extração automática só na evolução F-07) e definir critérios pedagógicos com a coordenação (fidelidade à matriz de competências, justificativa de todas as alternativas e referência bibliográfica) | Equipe de requisitos (Ian), até 22/11/26 | Aberto: critérios pedagógicos levantados, condições de uso ainda por verificar |
| PQ-06 | Dúvida | Relação com PreparaEdu e com a Plataforma de Questões e Avaliações da Unifor | Duplicação ou necessidade de integração | Registrar o sistema como complementar às plataformas existentes, sem duplicar cadastro nem conteúdo. Reaproveitar a autenticação institucional (login único) e avaliar com a equipe técnica a exportação de dados e a integração futura | Equipe de requisitos (Ian) e de TI, até 21/11/26 | Parcialmente respondido: relação definida como complementar, viabilidade de integração a confirmar |
| PQ-07 | Risco | Tratamento de dados pessoais de estudantes (cadastro, desempenho) e a LGPD | Impedimento legal ou ajustes de escopo | Definir finalidade e base legal, coletar o mínimo de dados, informar ao estudante quem acessa o quê, manter dado individual restrito ao próprio estudante, limitar a coordenação a relatórios agregados (individual só com consentimento) e validar com o encarregado de dados da instituição | Equipe de requisitos (Ian) com o encarregado de dados, até 22/11/26 | Em andamento: requisitos de privacidade levantados, validação institucional pendente |
| PQ-08 | Dúvida | Quem elabora os comentários dos gabaritos e modera o fórum? | Operação do sistema sem responsável | Docentes elaboram os comentários (grupo piloto de voluntários por curso), com reconhecimento da atividade; moderação por docentes ou monitores com regras de conduta e denúncia de mensagens. Como o fórum está fora do MVP, a moderação só é exigida na fase seguinte. Confirmar carga horária com as coordenações | Prof. Atila com as coordenações, até 22/11/26 | Parcialmente respondido: responsáveis indicados, disponibilidade a confirmar |
| PQ-09 | Risco | Baixo engajamento dos estudantes, já que o ENADE não vale nota individual e muitos o encaram como formalidade | Baixo uso do sistema e metas de adoção não atingidas | Priorizar funcionalidades de maior valor percebido (gabarito comentado e simulado com resultado detalhado), interface rápida e sem anúncios, e prever divulgação pela coordenação | Equipe de requisitos (Ian) e coordenação, até 23/11/26 | Aberto: identificado nas entrevistas |
| PQ-10 | Risco | Viabilidade técnica do login institucional (login único) e dos requisitos de segurança, disponibilidade e acessibilidade (WCAG) exigidos pela instituição | Atraso no cadastro/autenticação e retrabalho de requisitos não funcionais | Confirmar com a TI o protocolo de autenticação, o nível exigido de acessibilidade e a capacidade para picos de acesso em época de prova | Equipe de requisitos (Ian) e TI, até 21/11/26 | Aberto: identificado nas entrevistas |
| PQ-11 | Dúvida | Funcionalidade nova: guia ou calendário do ENADE por curso (data da prova, estrutura e conteúdo cobrado), solicitada por estudante | Escopo incompleto para estudantes que ainda não conhecem o exame | Avaliar se entra no MVP ou na evolução futura e validar com o solicitante e a coordenação | Equipe de requisitos (Ian) com o Prof. Atila, até 20/11/26 | Aberto: requisito novo a priorizar |
| PQ-12 | Decisão pendente | Regra de comparação de desempenho entre estudantes: opinião dividida sobre ranking e média da turma | Insatisfação ou exposição indevida de estudantes | Adotar comparação opcional e anônima (média da turma, sem identificação) e registrar como regra de negócio | Equipe de requisitos (Ian), até 21/11/26 | Em andamento: proposta definida, a validar com o solicitante |

## 11. Documentos Relacionados

| Documento | Conteúdo sob sua responsabilidade | Referência e situação |
| --- | --- | --- |
| PROJETO DE EXTENSÃO ENADE REQUISITOS E MODELAGEM DE SISTEMAS | Fonte original desta VD | Um dos Arquivos de origem |
| Propostas_Projetos_Internacionalizacao_ENADE_Unifor | Fonte complementar desta VD | Um dos Arquivos de origem |
| Regras de negócio compartilhadas | Políticas e condições comuns a vários casos de uso | A elaborar |
| Requisitos não funcionais ou de qualidade | Requisitos detalhados e critérios de verificação | A elaborar |
| Arquitetura e contratos de integração (INEP e Unifor online) | Decisões técnicas e interfaces | A elaborar |
| Glossário | Termos do domínio (ENADE, enadista, simulado, gabarito comentado, entre outros) | A elaborar |
| Especificação de Requisitos (SRS) e casos de uso | Detalhamento das funcionalidades F-01 a F-08 | A elaborar |

## 12. Validação da Visão

### 12.1. Registro da validação

| Versão | Responsável e papel | Data | Condição da VD | Resultado e ressalvas |
| --- | --- | --- | --- | --- |
| 0.1 | prof. Marcelo Bezerra | 01/11/2026 | rascunho | Rascunho inicial elaborado a partir do documento de demanda. Pendências em PQ-01 a PQ-08 |
| 0.2 | prof. Marcelo Bezerra | 06/11/2026 | versão intermediária | complementação do documento de visão|
| 0.3 | prof. Marcelo Bezerra | 14/11/2026 | versão final | Termino do documento de visão|

