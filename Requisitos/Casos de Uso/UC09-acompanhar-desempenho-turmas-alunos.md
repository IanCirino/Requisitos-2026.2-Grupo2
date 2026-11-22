# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC09 (F-11) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC09 – Acompanhar desempenho de turmas e alunos

## 2. Objetivo

Permitir que a Coordenação e o Professor acompanhem o desempenho das turmas e de cada aluno nos simulados realizados, apoiando a identificação de dificuldades e a tomada de decisão pedagógica (F-11).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Coordenação.
* Professor.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui vínculo com ao menos uma turma, curso ou área (UC14, UC16).
* Existem simulados publicados para a turma (UC13) com tentativas finalizadas (UC03).

## 6. Fluxo Principal

> Cenário: o ator consulta o desempenho de uma turma e, em seguida, de um aluno específico.

### P1. Acessar o acompanhamento

O ator aciona a opção "Acompanhar desempenho".

### P2. Exibir as turmas disponíveis

O sistema exibe as turmas sob responsabilidade do ator: para o Professor, as turmas em que leciona; para a Coordenação, as turmas dos cursos ou áreas sob sua coordenação.

### P3. Selecionar a turma

O ator seleciona uma turma.

### P4. Exibir o painel da turma

O sistema exibe o painel de desempenho da turma, contendo a média geral, o percentual de participação, a distribuição de notas e o desempenho por simulado.

#### P4.1. Exibir a lista de alunos

O sistema exibe a lista de alunos da turma com nome, quantidade de simulados realizados e média individual.

### P5. Selecionar um aluno

O ator seleciona um aluno da lista.

### P6. Exibir o desempenho do aluno

O sistema exibe o desempenho individual do aluno, contendo os simulados realizados, a nota, o percentual de acertos, o tempo gasto e a evolução ao longo do tempo.

### P7. Navegar entre alunos e turmas

O ator navega para outro aluno, retorna ao painel da turma ou retorna à lista de turmas, repetindo os passos P4 ou P6.

### P8. Encerrar a consulta

O ator aciona a opção "Sair do acompanhamento".

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Filtrar por período ou simulado

> Ponto de entrada: passo P4 do fluxo principal.

#### A1.1. Selecionar os filtros

O ator filtra o painel por período, simulado, área ou tema.

#### A1.2. Atualizar o painel

O sistema recalcula os indicadores e retorna ao passo P4 do fluxo principal.

### A2. Comparar turmas

> Ponto de entrada: passo P2 do fluxo principal (perfil Coordenação).

#### A2.1. Selecionar as turmas

A Coordenação seleciona duas ou mais turmas para comparação.

#### A2.2. Exibir a comparação

O sistema exibe os indicadores das turmas lado a lado (média, participação e distribuição de notas) e retorna ao passo P3 do fluxo principal.

### A3. Buscar aluno

> Ponto de entrada: passo P4 do fluxo principal.

#### A3.1. Informar o critério de busca

O ator informa nome ou matrícula do aluno.

#### A3.2. Exibir o resultado

O sistema exibe os alunos encontrados dentro do escopo do ator e segue para o passo P5 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Ator sem turmas vinculadas

> Ponto de entrada: passo P2 do fluxo principal.

#### E1.1. Informar a ausência de vínculo

O sistema exibe a mensagem "Nenhuma turma vinculada ao seu perfil".

#### E1.2. Encerrar caso de uso

O caso de uso é encerrado.

### E2. Turma sem dados de desempenho

> Ponto de entrada: passo P4 do fluxo principal.

#### E2.1. Informar a ausência de dados

O sistema exibe a mensagem informando que ainda não há tentativas finalizadas para a turma.

#### E2.2. Retornar à lista de turmas

O sistema retorna ao passo P2 do fluxo principal.

### E3. Acesso fora do escopo

> Pontos de entrada: passos P3 e P5 do fluxo principal.

#### E3.1. Negar o acesso

Caso o ator tente acessar turma ou aluno fora do seu escopo (inclusive por URL ou API), o sistema nega o acesso e exibe mensagem de permissão insuficiente.

#### E3.2. Retornar à tela anterior

O sistema retorna ao passo P2 do fluxo principal.

### E4. Falha na consulta

> Pontos de entrada: passos P4 e P6 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando indisponibilidade temporária da consulta e orienta tentar novamente.

#### E4.2. Encerrar caso de uso

O caso de uso é encerrado.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Nenhum dado de turmas, alunos ou simulados é alterado por este caso de uso (consulta somente leitura).

## 10. Requisitos Não Funcionais

* **Desempenho:** o painel da turma deve ser exibido em até 5 segundos em condições normais de uso.
* **Segurança:** o ator só pode visualizar turmas e alunos dentro do seu escopo de atuação, inclusive por acesso direto à URL ou à API.
* **Privacidade:** o tratamento de dados individuais dos alunos deve observar a LGPD, sendo exibidos apenas a atores autorizados.
* **Usabilidade:** a tela deve ser responsiva e os gráficos devem possuir alternativa textual (tabela) para acessibilidade.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Média, com picos após a conclusão dos simulados publicados para as turmas.

## 13. Interface Visual

### IV1. Tela de Lista de Turmas

Leiaute com as turmas do ator, curso/área e indicadores resumidos. Referência: _a definir (ex.: `prototipos/IV1-lista-turmas.png`)_.

### IV2. Tela de Painel da Turma

Leiaute com indicadores gerais, gráficos, filtros e lista de alunos. Referência: _a definir (ex.: `prototipos/IV2-painel-turma.png`)_.

### IV3. Tela de Desempenho do Aluno

Leiaute com histórico de simulados, evolução e detalhamento de acertos e erros. Referência: _a definir (ex.: `prototipos/IV3-desempenho-aluno.png`)_.

## 14. Observações

* No diagrama, o UC09 está associado à Coordenação; a associação com o Professor foi inferida pelas linhas do diagrama e deve ser confirmada na revisão com o cliente.
* Diferentemente do UC06 (comparação anônima com a média da turma, para o Estudante), o UC09 exibe dados identificados por aluno.
* Definir se haverá exportação de relatórios (PDF/CSV) e se o Professor poderá ver turmas de outros professores.
* Definir os indicadores oficiais exibidos no painel (média, participação, distribuição, evolução, desempenho por tema).
* As turmas e os vínculos dependem dos dados sincronizados pelo UC16 – Sincronizar dados com a Unifor Online.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-11 – Acompanhamento de desempenho de turmas e alunos.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC03 – Realizar simulado cronometrado (F-02).
* UC06 – Comparar com a média da turma (anônima).
* UC13 – Publicar simulado para turmas.
* UC14 – Gerenciar usuários e perfis (F-13).
* UC16 – Sincronizar dados com a Unifor Online (F-12).

## 16. Checklist de Validação do Artefato (CDU)

> Utilize este checklist antes de concluir a versão do caso de uso.

### 16.1 Estrutura mínima

* [ ] Nome do caso de uso iniciado com verbo no infinitivo.
* [ ] Objetivo claro, direto e com foco em um objetivo principal.
* [ ] Tipo do caso de uso informado (concreto/abstrato), quando aplicável.
* [ ] Atores primário e secundários identificados corretamente.
* [ ] Precondições registradas (ou seção marcada como "Não se aplica").
* [ ] Fluxo principal completo e coerente com o objetivo.
* [ ] Fluxos alternativos e de exceção definidos quando necessários.
* [ ] Pós-condições registradas (ou seção marcada como "Não se aplica").
* [ ] Requisitos não funcionais específicos do CDU registrados, quando existirem.
* [ ] Pontos de extensão identificados corretamente, quando existirem.
* [ ] Frequência de utilização estimada.

### 16.2 Qualidade da especificação

* [ ] Passos escritos com linguagem simples e objetiva.
* [ ] Ações descritas com verbos no presente do indicativo (3ª pessoa).
* [ ] Alternância entre ação do ator e ação da solução está clara.
* [ ] Não há ambiguidade (termos vagos sem detalhe técnico).
* [ ] Regras de negócio e mensagens estão referenciadas quando necessário.

### 16.3 Consistência e rastreabilidade

* [ ] Pontos de entrada e saída dos fluxos alternativos estão explícitos.
* [ ] Fluxos de exceção estão vinculados aos passos corretos da solução.
* [ ] Referências internas entre passos (retorna/segue para) estão corretas.
* [ ] Interface visual (IV1 etc.) está coerente com o fluxo descrito.
* [ ] Referências para visão da demanda, glossário e RNF estão atualizadas.

### 16.4 Revisão final

* [ ] Não há contradições entre seções do artefato.
* [ ] Links internos e externos foram validados.
* [ ] Documento revisado por pares.
* [ ] Artefato pronto para uso em desenvolvimento e testes.
