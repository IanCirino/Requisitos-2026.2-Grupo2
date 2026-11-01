# Visão da Demanda (VD) — Software de auxílio estudantil e preparação para o ENADE

## Identificação e Histórico

| Campo | Informação |
| --- | --- |
| Nome e identificador da demanda | Sistema web/mobile de auxílio estudantil e preparação para o ENADE |
| Tipo | Novo sistema |
| Sistema ou produto relacionado | QEnade, Descomplica, Qconcurso, PreparaEdu |
| Área solicitante | Coordenação UNIFOR |
| Responsável pela elaboração | Ian Carvalho Cirino - Desenvolvedor/Estudante |
| Responsável pela validação | Prof. Me. Marcelo Bezerra De Alcantara - Docente Avaliador ; Prof. Me. Atila Girao De Oliveira - Representante da demanda e Avaliador|
| Situação do documento | Rascunho |
| Versão e data | 0.1 — 01/11/2026 |

| Data | Versão | Descrição da alteração | Autor |
| --- | --- | --- | --- |
| 01/11/2026 | 0.1 | Criação da primeira versão do VD | Ian Carvalho Cirino |

> **Origem das informações:** todo o conteúdo abaixo vem dos documentos PROJETO DE EXTENSÃO -ENADE- REQUISITOS E MODELAGEM DE SISTEMAS e Propostas_Projetos_Internacionalizacao_ENADE_Unifor, além de declarações verbais do Professor Marcelo Bezerra. O que não consta nele está marcado como **A definir** ou como hipótese.

## 1. Objetivo

Permitir que estudantes se preparem para o ENADE com questões comentadas, simulados cronometrados e acompanhamento do próprio desempenho. Permitir que administradores mantenham o conteúdo e o acesso ao sistema.

## 2. Contexto, Problema e Descrição Sumária da Demanda

- **Situação atual:** o ENADE é componente curricular obrigatório e indicador fundamental da qualidade do ensino superior brasileiro. Segundo a demanda, os estudantes enfrentam dificuldades no preparo. Não há descrição de como eles se preparam hoje (**a definir**, por entrevistas ou questionários).
- **Problema ou oportunidade:** faltam materiais organizados, simulados práticos e feedback sobre o desempenho dos estudantes.
- **Públicos afetados e impactos:** estudantes que farão o ENADE (dificuldade de preparo) e administradores do sistema. Juntamente como docentes e coordenações dos cursos.
- **Evidências disponíveis:** apenas a afirmação dos documentos de demanda e das declarações verbais dos solicitantes. Não há, no momento, dados, pesquisas ou exemplos coletados que a sustentem. Tratar o problema como **hipótese** até o levantamento com os interessados.
- **Descrição sumária da demanda:** sistema web/mobile com banco de questões organizado por ano, curso/área e componente, simulados cronometrados, gabarito comentado, estatísticas de desempenho, fórum de discussão por questão e cadastro/autenticação de estudantes e administradores.

> **Contexto da atividade:** a demanda faz parte de uma atividade acadêmica de engenharia de requisitos. O sistema será **especificado**, não necessariamente implementado. A definição do produto mínimo e dos limites do sistema faz parte da análise.

## 3. Proposta de Valor e Sucesso da Demanda

| Benefício esperado | Indicador ou evidência | Resultado desejado | Como e quando avaliar |
| --- | --- | --- | --- |
| Preparo mais organizado para o ENADE | A definir (situação atual desconhecida) | A definir | A definir |
| Prática realista do exame | A definir | A definir | A definir |
| Compreensão dos conceitos por meio de respostas explicadas | A definir | A definir | A definir |
| Visão do próprio desempenho por área de conhecimento | A definir | A definir | A definir |
| Aprendizado colaborativo entre usuários | A definir | A definir | A definir |

> A demanda não traz metas nem indicadores. Nenhum valor foi inventado. O levantamento de métricas está registrado em PQ-02.

## 4. Partes Interessadas

| Parte interessada | Papel e interesse | Responsabilidade | Representante |
| --- | --- | --- | --- |
| Estudantes | Usuários finais. Querem se preparar para o ENADE | Fornecer necessidades e validar a solução, quando houver acesso | A definir |
| Administradores do sistema | Mantêm o conteúdo e o acesso | A definir | A definir |
| Solicitante da demanda | Origem da demanda | Decidir escopo e validar a visão | Prof. Me. Atila Girao De Oliveira  |
| Equipe de requisitos | Elabora a VD e as especificações | Elicitação, especificação e documentação | Ian Carvalho Cirino |
| Comunidade acadêmica | Público da apresentação final | Receber o pitch do projeto |Prof. Me. Marcelo Bezerra De Alcantara |
| Responsáveis pelo PreparaEdu e pela Plataforma de Questões e Avaliações da Unifor | Possíveis soluções relacionadas (a investigar) | A definir | A definir |

## 5. Usuários e Atores Externos

| ID | Usuário, sistema ou dispositivo | Objetivo ou papel na interação | Contexto de uso relevante |
| --- | --- | --- | --- |
| AT-01 | Estudante | Estuda questões, faz simulados, consulta gabaritos comentados e estatísticas e participa do fórum | Acesso via web e mobile. |
| AT-02 | Administrador do sistema | Gerencia o sistema e os cadastros. Ter um feedback do desempenho dos alunos | Leitura dos dados via web/mobile |
| AT-03 | INEP (provas e dados) | Fonte das provas e das estatísticas oficiais |  Uso de provas do INEP |

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
- Por ora, a **Plataforma de Gestão Acadêmica e Inteligência do ENADE** (identificação de enadistas, inscrições, painéis institucionais) fica fora, por ser proposta distinta e ainda não selecionada (ver PQ-03).

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
| NEC-01 | Ter materiais de estudo do ENADE organizados | Documento de demanda, seção 1 (a confirmar) | AT-01 |
| NEC-02 | Praticar com simulados em condições próximas às do exame | Documento de demanda, seções 1 e 3 (a confirmar) | AT-01 |
| NEC-03 | Receber feedback sobre o próprio desempenho | Documento de demanda, seção 1 (a confirmar) | AT-01 |
| NEC-04 | Compreender os conceitos por trás das respostas | Documento de demanda, seção 3 (a confirmar) | AT-01 |
| NEC-05 | Aprender de forma colaborativa, discutindo as questões | Documento de demanda, seção 3 (a confirmar) | AT-01 |
| NEC-06 | Garantir acesso seguro e administração do sistema | Documento de demanda, seção 3 (a confirmar) | AT-01, AT-02 |
| NEC-07 | Obter provas do INEP de forma ágil e classificá-las por tema, competência e grade curricular | Documento de demanda, seção 5, proposta sugerida (hipótese; a confirmar) | AT-02, AT-03 |

| ID | Funcionalidade e resultado esperado | Necessidade | Atores (IDs) | Prioridade | Valor | Frequência | Escopo ou entrega | Especificação |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| F-01 | **Banco de questões:** consultar questões organizadas por ano, curso/área e componente (formação geral e conhecimento específico) | NEC-01 | AT-01, AT-02 | A definir | A definir | A definir | Entrega | A elaborar |
| F-02 | **Simulados cronometrados:** realizar simulados com tempo controlado | NEC-02 | AT-01 | A definir | A definir | A definir | Entrega | A elaborar |
| F-03 | **Gabarito comentado:** consultar explicações detalhadas das respostas | NEC-04 | AT-01, AT-02 | A definir | A definir | A definir | Entrega | A elaborar |
| F-04 | **Estatísticas de desempenho:** ver análise por área de conhecimento, com gráficos | NEC-03 | AT-01 | A definir | A definir | A definir | Entrega | A elaborar |
| F-05 | **Fórum de discussão:** interagir com outros usuários em cada questão | NEC-05 | AT-01, AT-02 | A definir | A definir | A definir | Entrega | A elaborar |
| F-06 | **Cadastro e autenticação:** cadastrar e autenticar estudantes e administradores de forma segura | NEC-06 | AT-01, AT-02 | A definir | A definir | A definir | Entrega | A elaborar |
| F-07 | **Importação de provas em PDF do INEP** (hipótese, proposta da seção 5) | NEC-07 | AT-02, AT-03 | A definir | A definir | A definir | Em avaliação | A elaborar, se confirmada |
| F-08 | **Classificação por temas e competências e relação com a grade curricular** (hipótese, proposta da seção 5) | NEC-07 | AT-02 | A definir | A definir | A definir | Em avaliação | A elaborar, se confirmada |

> A coluna "Escopo ou entrega" indica **Entrega** para os itens listados no escopo geral da demanda (seção 3 do documento original). Isso ainda precisa ser confirmado quando o produto mínimo for definido. A prioridade, o valor e a frequência não foram informados; ficam como **A definir**, sem estimativa inventada.
>
> O gabarito comentado (F-03) e o fórum (F-05) podem exigir atribuições do administrador ou de outros perfis na gestão do conteúdo. Essa dúvida está em PQ-04.

## 8. Visão Geral da Solução e Impactos

- **Responsabilidades da solução:** manter o banco de questões e os gabaritos comentados, executar simulados cronometrados, calcular e exibir estatísticas de desempenho, oferecer o fórum por questão e gerenciar cadastro e autenticação.
- **Sistemas ou dispositivos externos:** a definir. Hipóteses: INEP (provas e estatísticas), PreparaEdu e Plataforma de Questões e Avaliações da Unifor (possível relação, a investigar).
- **Integrações principais:** não definidas. A demanda condiciona integrações com plataformas institucionais ou dados pessoais a autorização, acesso e observância da LGPD.
- **Diagrama de contexto — opcional:** não se aplica por ora.
- **Arquitetura e contratos detalhados:** a elaborar.

### 8.1. Sistemas e processos impactados

| Sistema ou processo | Impacto esperado | Responsável ou dependência | Situação |
| --- | --- | --- | --- |
| PreparaEdu | Relação com a solução a investigar (complemento, sobreposição ou integração) | A definir | A definir |
| Plataforma de Questões e Avaliações da Unifor | Relação com a solução a investigar | A definir | A definir |
| Provas do INEP | Possível fonte de questões | INEP; direitos de uso a validar | Hipótese |

### 8.2. Representações visuais — opcionais

- **Mapa de histórias ou diagrama geral de casos de uso:** a elaborar na especificação (a demanda prevê diagramas de casos de uso).
- **Protótipo de baixa fidelidade:** a demanda prevê wireframes de média ou alta fidelidade das principais telas; a elaborar.
- **Diagramas de componentes/implantação:** não se aplica por ora.

## 9. Condições Gerais da Demanda

| Tipo | Condição e impacto na demanda | Responsável ou fonte | Referência, se houver |
| --- | --- | --- | --- |
| Restrição | A demanda pode ser adaptada conforme a viabilidade do semestre | Documento de demanda, observações | — |
| Restrição | Não se exige implementar todas as funcionalidades. O produto mínimo e os limites do sistema fazem parte da análise | Documento de demanda, observações | — |
| Dependência | Integrações com plataformas institucionais ou dados pessoais dependem de autorização e acesso | A definir | A definir |
| Regra geral | Observância da LGPD no tratamento de dados pessoais | Documento de demanda, observações | A definir |
| Premissa | Direitos de uso das provas do INEP e a qualidade da extração dos PDFs precisam ser validados antes de se contar com a importação | A definir | A definir |
| Qualidade | O cadastro e a autenticação devem ser seguros. Outros requisitos de qualidade (desempenho, acessibilidade, disponibilidade, compatibilidade web/mobile) não foram definidos | A definir | A definir |

## 10. Riscos e Questões em Aberto

| ID | Tipo | Risco ou questão | Impacto | Próxima ação | Responsável e prazo | Situação |
| --- | --- | --- | --- | --- | --- | --- |
| PQ-01 | Decisão pendente | Qual é o produto mínimo e quais funcionalidades entram na entrega? | Escopo indefinido para a especificação | Decidir com a equipe e o solicitante | A definir | Aberto |
| PQ-02 | Dúvida | Não há evidências nem indicadores do problema, nem da situação atual de preparo dos estudantes | Não é possível medir o sucesso nem priorizar | Planejar entrevistas, questionários ou análise documental | A definir | Aberto |
| PQ-03 | Decisão pendente | A demanda traz duas propostas (Gestão do Conhecimento e Aprendizagem; Gestão Acadêmica e Inteligência) e pede selecionar uma e justificar. Esta VD se baseia no escopo geral, mais próximo da primeira proposta | Risco de escopo desalinhado | Selecionar a proposta e registrar a justificativa | A definir | Aberto |
| PQ-04 | Dúvida | Outros perfis (docentes, coordenações, moderadores) e as atribuições do administrador no conteúdo, no gabarito e no fórum | Atores e funcionalidades incompletos | Levantar com as partes interessadas | A definir | Aberto |
| PQ-05 | Risco | Direitos de uso, qualidade da extração e critérios pedagógicos das provas do INEP | Inviabilidade ou retrabalho do banco de questões | Investigar condições de uso e testar a extração | A definir | Aberto |
| PQ-06 | Dúvida | Relação com PreparaEdu e com a Plataforma de Questões e Avaliações da Unifor | Duplicação ou necessidade de integração | Investigar as plataformas | A definir | Aberto |
| PQ-07 | Risco | Tratamento de dados pessoais de estudantes (cadastro, desempenho) e a LGPD | Impedimento legal ou ajustes de escopo | Levantar requisitos legais e de consentimento | A definir | Aberto |
| PQ-08 | Dúvida | Quem elabora os comentários dos gabaritos e modera o fórum? | Operação do sistema sem responsável | Definir com o solicitante | A definir | Aberto |

## 11. Documentos Relacionados

| Documento | Conteúdo sob sua responsabilidade | Referência e situação |
| --- | --- | --- |
| Documento de demanda "O que foi comunicado até agora da demanda" | Fonte original desta VD | Arquivo de origem |
| Regras de negócio compartilhadas | Políticas e condições comuns a vários casos de uso | A elaborar |
| Requisitos não funcionais ou de qualidade | Requisitos detalhados e critérios de verificação | A elaborar |
| Arquitetura e contratos de integração | Decisões técnicas e interfaces | A elaborar (se houver integrações) |
| Glossário | Termos do domínio (ENADE, enadista, simulado, gabarito comentado, entre outros) | A elaborar |
| Especificação de Requisitos (SRS) e casos de uso | Detalhamento das funcionalidades F-01 a F-08 | A elaborar |

## 12. Validação da Visão

### 12.1. Checklist

- [x] Objetivo, contexto e problema estão claros, com hipóteses identificadas.
- [ ] Benefícios e condições de sucesso estão descritos, com hipóteses identificadas. *(metas pendentes — PQ-02)*
- [ ] Responsáveis por decisões e validação estão identificados.
- [ ] Usuários e atores externos relevantes estão representados. *(PQ-04)*
- [ ] Escopo, exclusões e possíveis evoluções estão diferenciados. *(PQ-01, PQ-03)*
- [x] Necessidades têm identificadores e fontes/evidências (ou indicação de levantamento pendente).
- [ ] Funcionalidades têm identificadores, prioridades, atores por ID e vínculo com necessidades. *(prioridades pendentes)*
- [ ] Valor e frequência são tratados separadamente e estimados quando úteis, ou marcados como **A definir**.
- [x] Cada funcionalidade tem referência à especificação ou indicação de que será elaborada.
- [ ] A visão geral da solução esclarece seus limites, interações externas e impactos em outros sistemas ou processos.
- [x] Diagramas e protótipos foram incluídos apenas quando agregam clareza, sem detalhamento técnico indevido.
- [x] Restrições, premissas, dependências e pendências relevantes estão registradas.
- [x] Informações detalhadas estão nos documentos apropriados, com referências consistentes.
- [ ] O conteúdo foi revisado pelos responsáveis, inclusive por ter sido elaborado com apoio de IA.

### 12.2. Critérios de conclusão e encaminhamento

Condição atual proposta: **Com pendências impeditivas**. Faltam a seleção da proposta e a definição do produto mínimo (PQ-01 e PQ-03), além do levantamento de evidências e partes interessadas (PQ-02 e PQ-04). Resolvidas essas pendências, a VD pode ser reavaliada como **Apta para iniciar a especificação**.

### 12.3. Registro da validação

| Versão | Responsável e papel | Data | Condição da VD | Resultado e ressalvas |
| --- | --- | --- | --- | --- |
| 0.1 | A definir | A definir | Com pendências impeditivas (proposta, sujeita a revisão) | Rascunho inicial elaborado a partir do documento de demanda. Pendências em PQ-01 a PQ-08 |
