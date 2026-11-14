# Roteiro de Entrevistas — Auxílio Estudantil e Preparação para o ENADE

Baseado na Visão da Demanda (VD) v0.1 de 01/11/2026. Elaborado para a equipe de requisitos (Ian Carvalho Cirino).

*Entrevistas simuladas, realizadas como exercício da disciplina de Engenharia de Requisitos. Nomes de estudantes, coordenação e administração são fictícios.*

---

## 1. Objetivo das entrevistas

A VD trata o problema como hipótese: não há evidências, métricas nem descrição de como os estudantes se preparam hoje (PQ-02). As entrevistas servem para:

- Confirmar ou refutar as necessidades NEC-01 a NEC-07.
- Entender a situação atual de preparo para o ENADE.
- Definir o produto mínimo e a priorização das funcionalidades F-01 a F-08 (PQ-01).
- Identificar outros perfis, responsabilidades e regras de operação (PQ-04, PQ-08).
- Investigar a relação com PreparaEdu e a Plataforma de Questões e Avaliações da Unifor (PQ-06).
- Levantar restrições legais e de uso: LGPD e provas do INEP (PQ-05, PQ-07).

## 2. Plano geral e entrevistas realizadas

| Bloco | Entrevistado | Duração | Pendências cobertas |
|-------|--------------|---------|---------------------|
| A | Prof. Me. Atila Girao De Oliveira (solicitante) | 45 min | PQ-01, PQ-03, PQ-04, PQ-08 |
| B | Josué Pereira (ASD) | 30 a 40 min cada | PQ-02, NEC-01 a NEC-05 |
| C | Prof. Me. Atila Girao De Oliveira (coordenação de curso) | 35 min | PQ-02, PQ-04, PQ-08, NEC-07 |
| D | Ian Carvalho Cirino | 35 min | PQ-04, PQ-06, PQ-07 |
| E | Prof. Me. Marcelo Bezerra De Alcantara (docente avaliador) | 25 min | Expectativas de entrega e escopo acadêmico |

**Perfis dos estudantes entrevistados**

| Nome | Perfil |
|------|--------|
| Josué Pereira | Concluinte do curso de Análise e Desenvolvimento de Sistemas, trabalha meio período, estuda mais pelo celular |

## 3. Roteiro de abertura (todas as entrevistas)

1. Apresente-se e explique o contexto: atividade acadêmica de engenharia de requisitos, em que o sistema será especificado, não necessariamente implementado.
2. Explique o tema: um sistema web/mobile para auxiliar a preparação para o ENADE.
3. Informe que não há respostas certas ou erradas, e que o interesse é na experiência real da pessoa.
4. Peça autorização para gravar ou anotar. Informe que os dados serão usados só para o trabalho, que a identificação pode ser anonimizada e que a pessoa pode parar a qualquer momento (cuidado com a LGPD).
5. Pergunte se há dúvidas antes de começar.

---

## 4. Bloco A — Solicitante da demanda

Entrevistado: Prof. Me. Atila Girao De Oliveira · Duração: 45 min

Objetivo: fechar escopo, prioridades e decisões pendentes.

### Contexto e problema

**1. Como surgiu essa demanda? Houve algum fato ou dado que motivou o pedido?**

> Surgiu de conversas com coordenadores e alunos ao longo dos últimos semestres. Eu percebia que, perto do ENADE, havia um corre-corre: o aluno procurava prova antiga, ninguém sabia onde achar a do curso certo e quase ninguém tinha como conferir o gabarito com explicação. Não foi um estudo formal, foi uma observação repetida.

*Sondagem: "Houve algum episódio específico?"*

> Teve um semestre em que um grupo de concluintes me procurou uma semana antes da prova pedindo material. Eu não tinha nada organizado para indicar.

**2. Que dificuldades de preparo dos estudantes o senhor já observou? Há exemplos concretos ou dados? (PQ-02)**

> Três principais: não saber por onde começar, material espalhado e falta de explicação das respostas. Sobre dados, a participação nos aulões que a coordenação oferece em alguns cursos costuma ficar em torno de um terço dos concluintes, segundo relato de coordenadores. Os números oficiais de desempenho por curso estão nos relatórios do INEP e podemos usá-los como referência.

**3. Como a preparação para o ENADE acontece hoje na Unifor? Existe alguma ação institucional?**

> Varia por curso. Alguns fazem aulão e simulado em papel; outros só comunicam a data da prova. Não há uma plataforma única de preparo.

### Sucesso e valor

**4. Se o sistema desse certo, o que mudaria para o estudante? E para a coordenação?**

> O estudante teria um lugar único para treinar, entender os erros e acompanhar sua evolução. A coordenação passaria a enxergar quais temas a turma mais erra e poderia planejar reforços.

**5. Como saberíamos que deu certo? Há meta ou indicador desejado? (Seção 3 da VD)**

> Eu começaria por indicadores de uso: percentual de concluintes cadastrados, média de simulados concluídos por estudante e satisfação. Uma meta razoável para um primeiro semestre seria 40% dos concluintes cadastrados e ao menos um simulado completo por usuário. A melhora na nota do ENADE é o objetivo final, mas leva mais de um ciclo para ser medida.

### Escopo e prioridades

**6. Das funcionalidades previstas, quais são indispensáveis num produto mínimo? (PQ-01)**

> Banco de questões com filtros, simulado cronometrado, gabarito comentado, estatísticas básicas de desempenho e cadastro com autenticação. O fórum é interessante, mas exige moderação, então eu deixaria para uma segunda fase.

**7. Existe algo que deve ficar explicitamente fora do escopo?**

> Integração profunda com sistemas acadêmicos e qualquer tentativa de substituir a Plataforma de Questões e Avaliações. Também não entra gamificação complexa nesta versão.

**8. A demanda traz duas propostas. Qual o senhor considera mais adequada e por quê? (PQ-03)**

> A de Gestão do Conhecimento e Aprendizagem. Está centrada no estudante, entrega valor visível e é viável no prazo. A de Gestão Acadêmica e Inteligência do ENADE depende de dados institucionais que podem demorar a liberar. Ela pode ser uma evolução.

**9. Importação de provas em PDF e classificação por temas e competências (F-07 e F-08): agora ou evolução futura?**

> Evolução futura. No início, as questões podem ser cadastradas manualmente ou por planilha, com tema e componente já informados.

### Perfis e operação

**10. Além de estudantes e administradores, haverá outros perfis? (PQ-04)**

> Sim: docente/coordenador, que elabora conteúdo e consulta relatórios agregados. O moderador pode ser uma função do docente no começo.

**11. Quem escreve os comentários dos gabaritos e modera o fórum? (PQ-08)**

> Os docentes, idealmente. Ainda não há acordo de carga horária. Pode-se começar com um grupo pequeno de professores voluntários por curso e ampliar depois.

**12. Quem seriam os administradores do sistema na prática?**

> Provavelmente uma equipe de apoio acadêmico ligada à TI, com a coordenação cuidando do conteúdo do seu curso.

### Relações e restrições

**13. O sistema deve conviver, complementar ou substituir PreparaEdu e a Plataforma de Questões e Avaliações? (PQ-06)**

> Complementar. O foco é o ENADE. Se houver integração, melhor, mas não como requisito do produto mínimo.

**14. Há restrições institucionais de dados, identidade visual, hospedagem ou autenticação?**

> Sim: LGPD, identidade visual da universidade e preferência por login institucional. Os detalhes técnicos o pessoal de TI pode confirmar.

**15. Quem valida os documentos e em que momento?**

> Eu valido a VD e a SRS em reuniões de revisão antes de cada entrega. A avaliação final é do professor da disciplina.

---

## 5. Bloco B — Estudantes

Objetivo: entender o comportamento atual e validar necessidades.

### Perfil

**1. Qual é o seu curso e semestre? Você já fez ou vai fazer o ENADE?**

- **Josué Pereira:** Análise e Desenvolvimento de Sistemas, último semestre. Vou fazer este ano.

**2. Que importância o ENADE tem para você? E para o seu curso?**

- **Josué Pereira:** Para mim, é uma obrigação para poder colar grau. Sei que para o curso pesa na avaliação.

### Situação atual de preparo (PQ-02, NEC-01)

**3. Como você se preparou, ou pretende se preparar?**

- **Josué Pereira:** Ainda nada estruturado. Pretendo ver a prova do ano passado na semana anterior.

*Sondagem à Josué Pereira: "E o que te faz deixar para a última semana?"*

- **Josué Pereira:** Falta de tempo e de saber por onde começar. Se eu tivesse um plano pronto, começaria antes.

**4. Que materiais você usa ou usou? Onde os encontra?**

- **Josué Pereira:** Baixei provas do site do INEP, mas é difícil achar a do meu curso rápido e não tem resolução.

**5. O que é mais difícil nessa preparação? Pode contar um exemplo?**

- **Josué Pereira:** A falta de gabarito explicado. Errei uma questão de formação geral e fiquei sem saber por quê.

**6. Você conhece plataformas como QEnade, Descomplica, Qconcurso ou PreparaEdu? Já usou alguma?**

- **Josué Pereira:** Conheço de nome. Usei um site de questões gratuito, mas era cheio de anúncio e limitava as questões por dia.

**7. Quanto tempo você dedica, ou dedicaria? Em que momentos e dispositivos?**

- **Josué Pereira:** Uns 20 minutos por dia, no celular, no ônibus ou no intervalo do trabalho.

### Simulados (NEC-02, F-02)

**8. Você já fez algum simulado? Como foi a experiência?**
- **Josué Pereira:** Nunca fiz.

**9. O tempo cronometrado ajudaria? Que tipo de simulado você prefere?**

- **Josué Pereira:** Ajudaria, mas prefiro simulados curtos, por quantidade de questões.

**10. O que você esperaria ver ao terminar um simulado?**

- **Josué Pereira:** Nota, acertos por área e o gabarito comentado das que errei.

### Questões e gabarito comentado (NEC-01, NEC-04, F-01, F-03)

**11. Como você gostaria de encontrar as questões?**

- **Josué Pereira:** Por curso e ano, e também por tema.

**12. Quando você erra uma questão, o que faz para entender o erro?**

- **Josué Pereira:** Pesquiso no Google ou pergunto a um colega.

**13. O que torna uma explicação de gabarito boa para você?**

- **Josué Pereira:** Passo a passo curto e objetivo. Vídeo só se for rápido.

### Desempenho (NEC-03, F-04)

**14. Que informações sobre seu desempenho você gostaria de acompanhar?**

- **Josué Pereira:** Acertos por área e evolução semana a semana.

**15. Comparar seu resultado com o de outros estudantes ajudaria ou incomodaria?**

- **Josué Pereira:** Comparar com a média da turma é ok, se for anônimo.

### Fórum (NEC-05, F-05)

**16. Você discute questões com colegas hoje? Onde e como?**

- **Josué Pereira e Camila:** Em grupos de WhatsApp, de forma informal.

**17. Você participaria de um fórum por questão? Que cuidados seriam necessários?**

- **Josué Pereira:** Leria, mas dificilmente postaria.respeito.

### Cadastro e privacidade (NEC-06, PQ-07)

**18. Como você se sentiria cadastrando seus dados e tendo seu desempenho registrado?**

- **Josué Pereira:** Sem problema, desde que só eu veja.

**19. Preferiria entrar com login institucional ou criar uma conta própria?**

- **Josué Pereira e Camila:** Institucional, para não criar mais uma senha.

### Fechamento

**20. Se pudesse ter só uma funcionalidade, qual seria?**

- **Josué Pereira:** Gabarito comentado.

**21. O que faria você deixar de usar um sistema como esse?**
- **Josué Pereira:** Lentidão, anúncios e muitos passos para começar um simulado.

---

## 6. Bloco C — Coordenação de curso e docentes

Entrevistado: Prof. Me. Atila Girao De Oliveira · Duração: 35 min

Objetivo: entender a visão institucional e o papel do conteúdo.

**1. Qual é o papel da coordenação no preparo para o ENADE hoje? Há ações, aulões, simulados ou materiais?**

> Fazemos sensibilização dos concluintes e, em alguns semestres, um aulão e um simulado em papel. Não temos material padronizado nem acompanhamento depois do evento.

**2. Que dados vocês acompanham sobre o desempenho dos estudantes no ENADE? Como os usam? (PQ-02)**

> Olhamos o conceito do curso e os relatórios do INEP, e usamos para revisar o planejamento de disciplinas. Uma análise por questão ou por tema é rara, porque dá trabalho e não temos ferramenta para isso.

**3. Que dificuldades dos estudantes vocês observam com mais frequência?**

> Interpretação de texto e questões de formação geral. E a motivação: como a prova não vale nota individual, muitos encaram como formalidade.

**4. Que informações de desempenho dos alunos a coordenação gostaria de receber? Em que formato? (AT-02)**

> Um relatório agregado por turma e por tema, em painel ou PDF. Dado individual só com autorização do aluno.

**5. Docentes poderiam elaborar ou revisar questões e comentários? Há disponibilidade? (PQ-04, PQ-08)**

> Há interesse, mas a carga horária é apertada. Funcionaria com um fluxo simples e reconhecimento da atividade como extensão ou projeto.

**6. Como as provas do INEP são usadas hoje? Há classificação por tema ou competência? (NEC-07, F-07, F-08)**

> São usadas de forma pontual, sem classificação sistemática. Ligar as questões à matriz de competências e à grade curricular seria muito útil.

**7. Que critérios pedagógicos uma questão e um gabarito comentado precisam atender?**

> Fidelidade à matriz de competências do ENADE, linguagem clara, justificativa de todas as alternativas e referência bibliográfica.

**8. Quem deveria moderar o fórum e com quais regras?**

> Docentes ou monitores, com regras de conduta claras e a possibilidade de denunciar e ocultar mensagens.

**9. Há receios sobre o uso do sistema (cola, exposição de desempenho, carga de trabalho)?**

> Exposição individual do desempenho, sobrecarga dos docentes e o uso das questões sem observar condições de uso das provas.

---

## 7. Bloco D — Administradores e responsáveis por plataformas existentes

Entrevistado: Ian Carvalho Cirino · Duração: 35 min

Objetivo: entender sobreposição, integração e operação. (PQ-06, PQ-04, PQ-07)

**1. O que o PreparaEdu e a Plataforma de Questões e Avaliações fazem hoje? Quem são os usuários?**

> São usados por docentes e estudantes em atividades de estudo e avaliação das disciplinas. O foco é o conteúdo das disciplinas, não a preparação para exames nacionais.

**2. Elas já oferecem questões do ENADE, simulados, estatísticas ou fórum? Quais lacunas existem?**

> Não há uma trilha específica para o ENADE. A lacuna é justamente organizar as provas do INEP por curso e ano e oferecer gabarito comentado.

**3. O novo sistema seria visto como complemento, concorrente ou possível integração?**

> Como complemento. O importante é não duplicar cadastro de usuários nem conteúdo.

**4. Existe API, exportação de dados ou autenticação institucional que poderia ser reaproveitada?**

> A autenticação institucional existe e pode ser aproveitada via login único. Exportação de dados é possível sob solicitação; uma API completa teria que ser avaliada com a equipe de desenvolvimento.

**5. Que autorizações e processos são necessários para acessar dados de estudantes? Como a LGPD é tratada?**

> É preciso finalidade definida, base legal e aval do encarregado de dados da instituição. O ideal é coletar o mínimo necessário e deixar claro para o estudante quem acessa o quê.

**6. Como é feita a administração de contas e conteúdo? Quem tem permissão para quê?**

> Há perfis separados: administrador, docente e estudante. Docentes gerenciam o conteúdo das suas turmas; administradores gerenciam contas e configurações.

**7. Que dificuldades operacionais vocês enfrentam?**

> Suporte a usuários, atualização de conteúdo e moderação consomem bastante tempo de uma equipe pequena. Picos de acesso em época de prova também são um desafio.

**8. Que requisitos de segurança, disponibilidade e acessibilidade a instituição exige?**

> Autenticação segura, backup periódico, disponibilidade reforçada em períodos de pico e acessibilidade seguindo as diretrizes WCAG.

---

## 8. Bloco E — Docente avaliador

Entrevistado: Prof. Me. Marcelo Bezerra De Alcantara · Duração: 25 min

**1. Quais são as expectativas para o Documento de Visão, a SRS e os protótipos?**

> Documentos coerentes entre si, com rastreabilidade das necessidades até os requisitos, requisitos claros e verificáveis, e protótipos que mostrem os fluxos principais.

**2. O que seria um produto mínimo aceitável para fins da disciplina?**

> Um escopo enxuto, bem especificado e justificado vale mais do que muitas funcionalidades mal definidas. Pensem no que dá para especificar com qualidade até a data da SRS.

**3. Como deve ser registrada a seleção e justificativa da proposta? (PQ-03)**

> Com critérios explícitos, como valor, viabilidade, risco e prazo, e a decisão do solicitante registrada.

**4. Há critérios específicos de avaliação da elicitação?**

> Sim: variedade de técnicas, qualidade dos registros e uso das evidências na VD e na SRS.

---

## 9. Fechamento (todas as entrevistas)

1. Resuma em 2 ou 3 pontos o que você entendeu e peça confirmação.
2. Pergunte se a pessoa indicaria outros entrevistados.
3. Pergunte se pode ser contatada para validar os requisitos ou testar protótipos.
4. Agradeça e informe os próximos passos (consolidação das respostas e revisão da VD).

**Fechamento simulado (exemplo, entrevista com Camila)**

> **Entrevistador:** Então, resumindo: você começa a se preparar tarde, usa provas em PDF e o grupo da turma, quer simulados com resultado detalhado e prefere login institucional. É isso?
> **Camila:** É isso mesmo. Acrescento que não quero que a coordenação veja meu desempenho individual sem eu saber.
> **Entrevistador:** Anotado. Você indicaria algum colega para conversarmos?
> **Camila:** O Lucas e a Josué Pereira, que estão em cursos diferentes. E pode me chamar para testar o protótipo.

## 10. Boas práticas durante a entrevista

- Faça perguntas abertas e peça exemplos reais, em vez de opiniões gerais.
- Evite perguntas que induzam a resposta, como "você não acha que um fórum ajudaria?".
- Use sondagens: "Pode dar um exemplo?", "E o que aconteceu depois?", "Por que isso é importante?".
- Separe o que a pessoa faz hoje do que ela diz que faria. O comportamento atual é uma evidência mais forte.
- Registre números, termos e expressões usadas pelos entrevistados. Alimentam o glossário.
- Não apresente soluções prontas antes de ouvir o problema.

---

## 11. Modelo de registro (consolidado)

| Campo | Preenchimento |
|-------|---------------|
| Entrevistado e papel | Atila (solicitante); Josué Pereira, Lucas e Camila (estudantes); Helena Marques (coordenação); Ian Carvalho Cirino (administração); Marcelo (avaliador) |
| Data, duração e entrevistador | Novembro de 2026; 25 a 45 min por entrevista; Ian Carvalho Cirino |
| Autorização de gravação / LGPD | Autorização verbal obtida; identificação dos estudantes anonimizada nos registros |
| Necessidades confirmadas (NEC-xx) | NEC-01 (acesso organizado às provas), NEC-02 (simulados), NEC-03 (acompanhamento de desempenho), NEC-04 (gabarito comentado), NEC-06 (privacidade como condição de uso) |
| Necessidades novas ou refutadas | Nova: guia/calendário do ENADE por curso (Lucas). NEC-05 (fórum) confirmada de forma parcial: há mais interesse em ler do que em escrever. NEC-07 reconhecida pela coordenação como útil, mas para evolução futura |
| Funcionalidades mencionadas (F-xx) e prioridade | Alta: F-01, F-02, F-03. Média: F-04. Baixa/futura: F-05, F-07, F-08. Cadastro com login institucional: alta |
| Regras de negócio e restrições citadas | Comparação de desempenho anônima e opcional; relatório agregado para a coordenação, dado individual só com autorização; comentário com justificativa de cada alternativa; moderação por docentes ou monitores; coleta mínima de dados; acessibilidade WCAG; reforço de disponibilidade em época de prova |
| Riscos e dúvidas novas (PQ-xx) | Baixo engajamento (prova sem nota individual); disponibilidade docente para produzir conteúdo; condições de uso das provas do INEP; viabilidade técnica do login único; carga de moderação |
| Citações relevantes | "Errei uma questão de formação geral e fiquei sem saber por quê." (Josué Pereira); |
| Próximas ações | Revisar a VD com os achados; escolher a proposta de Gestão do Conhecimento e Aprendizagem; definir o MVP (F-01 a F-04 e cadastro); validar os requisitos com o solicitante e testar protótipos com os estudantes |

## 12. Como o resultado alimenta a VD

| Resultado das entrevistas | Atualiza na VD | Conclusão registrada |
|---------------------------|----------------|----------------------|
| Situação atual de preparo e dificuldades | Seção 2 (evidências) e PQ-02 | Preparo tardio e informal, provas em PDF dispersas, ausência de gabarito explicado, ações da coordenação pontuais |
| Metas e indicadores de sucesso | Seção 3 | Indicadores de uso e satisfação; meta inicial de 40% dos concluintes cadastrados e ao menos um simulado completo por usuário |
| Novos perfis e responsabilidades | Seções 4 e 5, PQ-04 e PQ-08 | Perfil docente/coordenador; moderação por docentes ou monitores; administração pela equipe de apoio acadêmico/TI |
| Prioridade, valor e frequência das funcionalidades | Seção 7 | F-01, F-02, F-03 > F-04 > F-05 > F-07/F-08 |
| Produto mínimo e proposta escolhida | Seção 6, PQ-01 e PQ-03 | Proposta de Gestão do Conhecimento e Aprendizagem; MVP com banco de questões, simulado, gabarito comentado, desempenho básico e cadastro |
| Relação com plataformas existentes | Seção 8.1 e PQ-06 | Complementar; login único reaproveitável; sem duplicar cadastros ou conteúdo |
| Restrições legais e de uso de provas | Seção 9, PQ-05 e PQ-07 | LGPD com finalidade definida, coleta mínima e transparência de acesso; verificar condições de uso das provas do INEP |

---

## 13. Síntese das entrevistas

**Principais achados**

1. Estudantes se preparam tarde e de modo informal, com provas em PDF dispersas e apoio de grupos de WhatsApp.
2. O gabarito comentado, com justificativa de cada alternativa, é o maior valor percebido.
3. O uso é misto (celular e computador), em sessões curtas, o que exige interface responsiva.
4. A comparação com outros estudantes divide opiniões e deve ser opcional e anônima.
5. O fórum tem mais leitores que autores e exige moderação, por isso fica para a segunda fase.
6. A transparência sobre quem acessa os dados condiciona a adesão (LGPD).
7. A disponibilidade docente para produzir conteúdo é um risco a tratar.

**Decisões propostas para a VD**

- Adotar a proposta de Gestão do Conhecimento e Aprendizagem.
- Definir como MVP: F-01, F-02, F-03, F-04 (básico) e cadastro com login institucional.
- Tratar F-05, F-07 e F-08 como evolução futura.
- Incluir como possível novo requisito um guia/calendário do ENADE por curso.
