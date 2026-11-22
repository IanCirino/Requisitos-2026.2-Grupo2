# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC19 (F-14) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC19 – Comparar desempenho com estatísticas oficiais do INEP

## 2. Objetivo

Permitir que a Coordenação e o Professor comparem o desempenho das turmas no AdE com as estatísticas oficiais do INEP, identificando pontos fortes e lacunas por área e competência (F-14).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Coordenação.
* Professor.

### 4.2 Secundário

* INEP (sistema externo).

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil Coordenação ou Professor.
* Existem resultados de simulados realizados pelos estudantes das turmas a comparar (UC09).
* As questões utilizadas estão classificadas por área e competência (UC18).

## 6. Fluxo Principal

> Cenário: o ator compara o desempenho de uma turma com as estatísticas oficiais do INEP, obtidas no momento da consulta.

### P1. Acessar a comparação

O ator aciona a opção "Comparar com estatísticas do INEP".

### P2. Exibir os filtros

O sistema exibe os filtros de comparação (curso, turma, período, edição da prova do INEP, área e competência).

### P3. Solicitar a comparação

O ator seleciona os parâmetros e aciona a opção "Comparar".

### P4. Solicitar as estatísticas ao INEP

O sistema solicita ao INEP as estatísticas oficiais correspondentes aos parâmetros selecionados.

### P5. Enviar as estatísticas

O INEP disponibiliza as estatísticas solicitadas ao sistema.

### P6. Validar as estatísticas

O sistema valida o formato e a consistência das estatísticas recebidas e as armazena com a data e a fonte da obtenção.

### P7. Consolidar o desempenho

O sistema consolida o desempenho das turmas selecionadas (UC09) por área e competência, de forma agregada.

### P8. Calcular o comparativo

O sistema calcula as diferenças entre o desempenho das turmas e as estatísticas oficiais (média, percentual de acertos e diferença por área e competência).

### P9. Exibir o comparativo

O sistema exibe o comparativo em tabelas e gráficos, com a data e a fonte das estatísticas do INEP.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Detalhar por tema ou competência

> Ponto de entrada: passo P9 do fluxo principal.

#### A1.1. Selecionar o detalhamento

O ator seleciona uma área ou competência do comparativo e aciona a opção "Detalhar".

#### A1.2. Exibir o detalhamento

O sistema exibe o comparativo detalhado por tema e competência e retorna ao passo P9 do fluxo principal.

### A2. Exportar o comparativo

> Ponto de entrada: passo P9 do fluxo principal.

#### A2.1. Solicitar a exportação

O ator aciona a opção "Exportar" e escolhe o formato (PDF ou CSV).

#### A2.2. Gerar o arquivo

O sistema gera o arquivo com o comparativo exibido e disponibiliza o download. O caso de uso é encerrado.

### A3. Utilizar estatísticas já armazenadas

> Ponto de entrada: passo P4 do fluxo principal (substitui os passos P4 a P6).

#### A3.1. Localizar as estatísticas armazenadas

O sistema localiza estatísticas do INEP já armazenadas para os parâmetros selecionados e segue para o passo P7 do fluxo principal.

## 8. Fluxos de Exceção

### E1. INEP indisponível

> Pontos de entrada: passos P4 e P5 do fluxo principal.

#### E1.1. Informar a indisponibilidade

O sistema informa que o INEP não respondeu no tempo esperado e registra a falha em log.

#### E1.2. Oferecer as estatísticas armazenadas

Se existirem estatísticas armazenadas para os parâmetros, o sistema as oferece ao ator com a indicação da data de obtenção e, caso o ator aceite, segue para o passo P7 do fluxo principal. Caso contrário, o caso de uso é encerrado.

### E2. Estatísticas oficiais não encontradas

> Ponto de entrada: passo P6 do fluxo principal.

#### E2.1. Informar a ausência de dados

O sistema informa que não há estatísticas oficiais para os parâmetros selecionados.

#### E2.2. Retornar aos filtros

O sistema retorna ao passo P2 do fluxo principal.

### E3. Dados inválidos ou inconsistentes

> Ponto de entrada: passo P6 do fluxo principal.

#### E3.1. Rejeitar as estatísticas

O sistema rejeita as estatísticas recebidas, mantém as armazenadas anteriormente e registra o motivo em log.

#### E3.2. Informar o problema

O sistema informa a falha ao ator e retorna ao passo P2 do fluxo principal.

### E4. Sem dados de desempenho

> Ponto de entrada: passo P7 do fluxo principal.

#### E4.1. Informar a ausência de resultados

O sistema informa que não há resultados de simulados suficientes para os parâmetros selecionados.

#### E4.2. Retornar aos filtros

O sistema retorna ao passo P2 do fluxo principal.

### E5. Turma sem permissão de acesso

> Ponto de entrada: passo P3 do fluxo principal.

#### E5.1. Informar a restrição

O sistema informa que o ator não possui acesso a uma ou mais turmas selecionadas.

#### E5.2. Retornar aos filtros

O sistema retorna ao passo P2 do fluxo principal.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal executado pelo ator.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* O comparativo entre o desempenho das turmas e as estatísticas oficiais do INEP é exibido ao ator.
* As estatísticas obtidas ficam armazenadas com data e fonte da obtenção.
* A consulta fica registrada em log.

## 10. Requisitos Não Funcionais

* **Privacidade:** o comparativo deve usar apenas dados agregados das turmas, sem identificar estudantes, conforme a LGPD.
* **Segurança:** o acesso deve respeitar o perfil do ator (o Professor acessa apenas as próprias turmas) e a comunicação com o INEP deve ocorrer por canal criptografado.
* **Rastreabilidade:** o comparativo deve informar a fonte, a edição e a data de obtenção das estatísticas do INEP.
* **Desempenho:** o comparativo deve ser exibido em tempo adequado, sem degradar a disponibilidade para os demais usuários.
* **Confiabilidade:** a indisponibilidade do INEP não deve impedir a consulta com estatísticas já armazenadas.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa a média; concentrada em períodos de planejamento acadêmico e após a divulgação de novas estatísticas pelo INEP.

## 13. Interface Visual

### IV1. Tela de Filtros do Comparativo

Leiaute com seleção de curso, turma, período, edição da prova do INEP, área e competência e botão "Comparar". Referência: _a definir (ex.: `prototipos/IV1-filtros-comparativo.png`)_.

### IV2. Tela de Comparativo de Desempenho

Leiaute com tabelas e gráficos do desempenho das turmas frente às estatísticas do INEP, data e fonte das estatísticas e opções "Detalhar" e "Exportar". Referência: _a definir (ex.: `prototipos/IV2-comparativo-desempenho.png`)_.

## 14. Observações

* O INEP é o ator secundário («sistema externo») e está associado ao UC19 no diagrama.
* Definir o mecanismo de obtenção das estatísticas (API, dados abertos, microdados ou importação manual) e a periodicidade de atualização.
* Definir a granularidade das estatísticas oficiais disponíveis (por área, competência, curso ou instituição) e a comparabilidade metodológica com os simulados do AdE.
* A qualidade do comparativo depende da classificação das questões (UC18) e dos resultados consolidados (UC09).

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-14 – Comparação com estatísticas oficiais do INEP.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC09 – Acompanhar desempenho de turmas e alunos (F-11).
* UC17 – Importar provas em PDF do INEP (F-07).
* UC18 – Classificar por tema, competência e grade curricular (F-08).

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
