# Roteiro de Entrevistas — Auxílio Estudantil e Preparação para o ENADE

Baseado na Visão da Demanda (VD) v0.1 de 01/11/2026. Elaborado para a equipe de requisitos (Ian Carvalho Cirino).

## 1. Objetivo das entrevistas

A VD trata o problema como hipótese: não há evidências, métricas nem descrição de como os estudantes se preparam hoje (PQ-02). As entrevistas servem para:

- Confirmar ou refutar as necessidades NEC-01 a NEC-07.

- Entender a situação atual de preparo para o ENADE.

- Definir o produto mínimo e a priorização das funcionalidades F-01 a F-08 (PQ-01).

- Identificar outros perfis, responsabilidades e regras de operação (PQ-04, PQ-08).

- Investigar a relação com PreparaEdu e a Plataforma de Questões e Avaliações da Unifor (PQ-06).

- Levantar restrições legais e de uso: LGPD e provas do INEP (PQ-05, PQ-07).

## 2. Plano geral

| Bloco | Entrevistado                                                                                     | Duração          | Pendências cobertas                        |
|-------|--------------------------------------------------------------------------------------------------|------------------|--------------------------------------------|
| A     | Solicitante da demanda (Prof. Me. Atila Girao De Oliveira)                                       | 40 a 50 min      | PQ-01, PQ-03, PQ-04, PQ-08                 |
| B     | Estudantes (concluintes ou prestes a fazer o ENADE)                                              | 30 a 40 min cada | PQ-02, NEC-01 a NEC-05                     |
| C     | Coordenação de curso e docentes                                                                  | 30 a 40 min      | PQ-02, PQ-04, PQ-08, NEC-07                |
| D     | Administradores / responsáveis pelas plataformas existentes (PreparaEdu, Plataforma de Questões) | 30 a 40 min      | PQ-04, PQ-06, PQ-07                        |
| E     | Prof. Me. Marcelo Bezerra De Alcantara (docente avaliador)                                       | 20 a 30 min      | Expectativas de entrega e escopo acadêmico |

Sugestão de amostra para os estudantes: 5 a 8 entrevistas, variando curso, semestre e nível de contato prévio com o ENADE. Se o prazo de 02/11/26 for apertado, priorize os blocos A e B e use os demais como complemento até a SRS (23/11/26).

## 3. Roteiro de abertura (todas as entrevistas)

1.  Apresente-se e explique o contexto: atividade acadêmica de engenharia de requisitos, em que o sistema será especificado, não necessariamente implementado.

2.  Explique o tema: um sistema web/mobile para auxiliar a preparação para o ENADE.

3.  Informe que não há respostas certas ou erradas, e que o interesse é na experiência real da pessoa.

4.  Peça autorização para gravar ou anotar. Informe que os dados serão usados só para o trabalho, que a identificação pode ser anonimizada e que a pessoa pode parar a qualquer momento (cuidado com a LGPD).

5.  Pergunte se há dúvidas antes de começar.

## 4. Bloco A — Solicitante da demanda

Objetivo: fechar escopo, prioridades e decisões pendentes.

**Contexto e problema**

1.  Como surgiu essa demanda? Houve algum fato ou dado que motivou o pedido?

2.  Que dificuldades de preparo dos estudantes o senhor já observou? Há exemplos concretos ou dados (notas, relatos, índices de participação)? *(PQ-02)*

3.  Como a preparação para o ENADE acontece hoje na Unifor? Existe alguma ação institucional?

**Sucesso e valor**

4.  Se o sistema desse certo, o que mudaria para o estudante? E para a coordenação?

5.  Como saberíamos que deu certo? Há alguma meta ou indicador desejado (uso, desempenho, satisfação)? *(Seção 3 da VD)*

**Escopo e prioridades**

6.  Das funcionalidades previstas (banco de questões, simulados cronometrados, gabarito comentado, estatísticas, fórum, cadastro/autenticação), quais são indispensáveis num produto mínimo? *(PQ-01)*

7.  Existe algo que deve ficar explicitamente fora do escopo?

8.  A demanda traz duas propostas (Gestão do Conhecimento e Aprendizagem; Gestão Acadêmica e Inteligência do ENADE). Qual o senhor considera mais adequada e por quê? *(PQ-03)*

9.  As funcionalidades de importação de provas em PDF e classificação por temas e competências (F-07 e F-08) devem ser consideradas agora ou ficam como evolução futura?

**Perfis e operação**

10. Além de estudantes e administradores, haverá outros perfis (docentes, coordenações, moderadores)? *(PQ-04)*

11. Quem seria o responsável por escrever os comentários dos gabaritos e por moderar o fórum? *(PQ-08)*

12. Quem seriam os administradores do sistema na prática?

**Relações e restrições**

13. O sistema deve conviver, complementar ou substituir PreparaEdu e a Plataforma de Questões e Avaliações da Unifor? *(PQ-06)*

14. Há restrições institucionais de dados, identidade visual, hospedagem ou autenticação (por exemplo, login institucional)?

15. Quem valida os documentos e em que momento?

## 5. Bloco B — Estudantes

Objetivo: entender o comportamento atual e validar necessidades. Use perguntas abertas e peça exemplos reais ("me conte a última vez que...").

**Perfil**

1.  Qual é o seu curso e semestre? Você já fez ou vai fazer o ENADE?

2.  Que importância o ENADE tem para você? E para o seu curso?

**Situação atual de preparo** *(PQ-02, NEC-01)*

3.  Como você se preparou, ou pretende se preparar, para o ENADE?

4.  Que materiais você usa ou usou (provas anteriores, apostilas, cursos, sites, grupos)? Onde os encontra?

5.  O que é mais difícil nessa preparação? Pode contar um exemplo?

6.  Você conhece plataformas como QEnade, Descomplica, Qconcurso ou PreparaEdu? Já usou alguma? O que funcionou e o que não funcionou?

7.  Quanto tempo você dedica, ou dedicaria, a essa preparação? Em que momentos e dispositivos (celular, computador)?

**Simulados** *(NEC-02, F-02)*

8.  Você já fez algum simulado? Como foi a experiência?

9.  O tempo cronometrado ajudaria? Que tipo de simulado você prefere (prova completa, por área, por quantidade de questões)?

10. O que você esperaria ver ao terminar um simulado?

**Questões e gabarito comentado** *(NEC-01, NEC-04, F-01, F-03)*

11. Como você gostaria de encontrar as questões (por ano, curso, componente, tema)? Que filtros seriam importantes?

12. Quando você erra uma questão, o que faz para entender o erro?

13. O que torna uma explicação de gabarito boa para você? Texto, vídeo, passo a passo?

**Desempenho** *(NEC-03, F-04)*

14. Que informações sobre seu desempenho você gostaria de acompanhar (acertos por área, evolução, comparação com a turma)?

15. Comparar seu resultado com o de outros estudantes ajudaria ou incomodaria?

**Fórum** *(NEC-05, F-05)*

16. Você discute questões com colegas hoje? Onde e como?

17. Você participaria de um fórum por questão? Que cuidados seriam necessários (moderação, anonimato, respeito)?

**Cadastro e privacidade** *(NEC-06, PQ-07)*

18. Como você se sentiria cadastrando seus dados e tendo seu desempenho registrado?

19. Preferiria entrar com login institucional ou criar uma conta própria?

**Fechamento**

20. Se pudesse ter só uma funcionalidade nesse sistema, qual seria?

21. O que faria você deixar de usar um sistema como esse?

22. Há algo importante que não perguntei?

## 6. Bloco C — Coordenação de curso e docentes

Objetivo: entender a visão institucional e o papel do conteúdo.

1.  Qual é o papel da coordenação no preparo para o ENADE hoje? Há ações, aulões, simulados ou materiais?

2.  Que dados vocês acompanham sobre o desempenho dos estudantes no ENADE? Como os usam? *(PQ-02)*

3.  Que dificuldades dos estudantes vocês observam com mais frequência?

4.  Que informações de desempenho dos alunos a coordenação gostaria de receber de um sistema? Em que formato? *(AT-02)*

5.  Docentes poderiam elaborar ou revisar questões e comentários? Há disponibilidade para isso? *(PQ-04, PQ-08)*

6.  Como as provas do INEP são usadas hoje? Há classificação por tema, competência ou ligação com a grade curricular? *(NEC-07, F-07, F-08)*

7.  Que critérios pedagógicos uma questão e um gabarito comentado precisam atender?

8.  Quem deveria moderar o fórum e com quais regras?

9.  Há receios sobre o uso do sistema (cola, exposição de desempenho, carga de trabalho)?

## 7. Bloco D — Administradores e responsáveis por plataformas existentes

Objetivo: entender sobreposição, integração e operação. *(PQ-06, PQ-04, PQ-07)*

1.  O que o PreparaEdu e a Plataforma de Questões e Avaliações da Unifor fazem hoje? Quem são os usuários?

2.  Elas já oferecem questões do ENADE, simulados, estatísticas ou fórum? Quais lacunas existem?

3.  O novo sistema seria visto como complemento, concorrente ou possível integração?

4.  Existe API, exportação de dados ou autenticação institucional que poderia ser reaproveitada?

5.  Que autorizações e processos são necessários para acessar dados de estudantes? Como a LGPD é tratada na instituição?

6.  Como é feita a administração de contas e conteúdo? Quem tem permissão para quê?

7.  Que dificuldades operacionais vocês enfrentam (suporte, moderação, atualização de conteúdo)?

8.  Que requisitos de segurança, disponibilidade e acessibilidade a instituição exige?

## 8. Bloco E — Docente avaliador

1.  Quais são as expectativas para o Documento de Visão, a SRS e os protótipos?

2.  O que seria um produto mínimo aceitável para fins da disciplina?

3.  Como deve ser registrada a seleção e justificativa da proposta (PQ-03)?

4.  Há critérios específicos de avaliação da elicitação (técnicas, evidências, registro)?

## 9. Fechamento (todas as entrevistas)

1.  Resuma em 2 ou 3 pontos o que você entendeu e peça confirmação.

2.  Pergunte se a pessoa indicaria outros entrevistados.

3.  Pergunte se pode ser contatada para validar os requisitos ou testar protótipos.

4.  Agradeça e informe os próximos passos (consolidação das respostas e revisão da VD).

## 10. Boas práticas durante a entrevista

- Faça perguntas abertas e peça exemplos reais, em vez de opiniões gerais.

- Evite perguntas que induzam a resposta, como "você não acha que um fórum ajudaria?".

- Use sondagens: "Pode dar um exemplo?", "E o que aconteceu depois?", "Por que isso é importante?".

- Separe o que a pessoa faz hoje do que ela diz que faria. O comportamento atual é uma evidência mais forte.

- Registre números, termos e expressões usadas pelos entrevistados. Alimentam o glossário.

- Não apresente soluções prontas antes de ouvir o problema.

## 11. Modelo de registro

| Campo                                                    | Preenchimento |
|----------------------------------------------------------|---------------|
| Entrevistado e papel                                     |               |
| Data, duração e entrevistador                            |               |
| Autorização de gravação / LGPD                           |               |
| Necessidades confirmadas (NEC-xx)                        |               |
| Necessidades novas ou refutadas                          |               |
| Funcionalidades mencionadas (F-xx) e prioridade indicada |               |
| Regras de negócio e restrições citadas                   |               |
| Riscos e dúvidas novas (PQ-xx)                           |               |
| Citações relevantes                                      |               |
| Próximas ações                                           |               |

## 12. Como o resultado alimenta a VD

| Resultado das entrevistas                          | Atualiza na VD               |
|----------------------------------------------------|------------------------------|
| Situação atual de preparo e dificuldades           | Seção 2 (evidências) e PQ-02 |
| Metas e indicadores de sucesso                     | Seção 3                      |
| Novos perfis e responsabilidades                   | Seções 4 e 5, PQ-04 e PQ-08  |
| Prioridade, valor e frequência das funcionalidades | Seção 7                      |
| Produto mínimo e proposta escolhida                | Seção 6, PQ-01 e PQ-03       |
| Relação com plataformas existentes                 | Seção 8.1 e PQ-06            |
| Restrições legais e de uso de provas               | Seção 9, PQ-05 e PQ-07       |
