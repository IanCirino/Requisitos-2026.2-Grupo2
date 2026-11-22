# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC18 (F-08) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC18 – Classificar por tema, competência e grade curricular

## 2. Objetivo

Permitir que o Professor e a Equipe Técnica classifiquem as questões do banco por tema, competência e grade curricular, viabilizando filtros, simulados e estatísticas por assunto (F-08).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Professor.
* Equipe Técnica.

### 4.2 Secundário

Não há.

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil Professor ou Equipe Técnica.
* Existem questões cadastradas (UC10) ou importadas (UC17) no banco de questões.
* Os temas, as competências e a grade curricular estão cadastrados no sistema.

## 6. Fluxo Principal

> Cenário: o ator classifica uma questão do banco de questões.

### P1. Acessar a classificação

O ator aciona a opção "Classificar questões".

### P2. Exibir a lista de questões

O sistema exibe a lista de questões com a situação da classificação (pendente, parcial ou completa) e os filtros disponíveis (situação, área, prova, ano e palavra-chave).

### P3. Selecionar a questão

O ator aplica os filtros, se necessário, e seleciona a questão a classificar.

### P4. Exibir os dados da classificação

O sistema exibe o enunciado da questão, a classificação atual e as opções de tema, competência e grade curricular.

### P5. Informar a classificação

O ator seleciona o tema, a competência e a disciplina da grade curricular e aciona a opção "Salvar".

### P6. Validar a classificação

O sistema verifica o preenchimento dos campos obrigatórios e a coerência entre tema, competência e grade curricular.

### P7. Registrar a classificação

O sistema grava a classificação da questão, atualiza sua situação para "Classificada" e registra no histórico o responsável, a data e a hora.

### P8. Exibir a confirmação

O sistema exibe mensagem de sucesso e retorna à lista de questões.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Classificar questões em lote

> Ponto de entrada: passo P3 do fluxo principal.

#### A1.1. Selecionar várias questões

O ator seleciona várias questões da lista e aciona a opção "Classificar em lote".

#### A1.2. Informar a classificação comum

O ator informa o tema, a competência e a grade curricular a aplicar a todas as questões selecionadas e segue para o passo P6 do fluxo principal.

### A2. Reclassificar questão já classificada

> Ponto de entrada: passo P4 do fluxo principal.

#### A2.1. Alterar a classificação

O ator altera os valores atuais de tema, competência ou grade curricular e segue para o passo P5 do fluxo principal.

#### A2.2. Preservar o histórico

No passo P7, o sistema mantém no histórico a classificação anterior junto à nova.

### A3. Salvar e seguir para a próxima questão

> Ponto de entrada: passo P8 do fluxo principal.

#### A3.1. Solicitar a próxima questão

O ator aciona a opção "Salvar e próxima".

#### A3.2. Exibir a próxima questão

O sistema exibe a próxima questão pendente da lista filtrada e retorna ao passo P4 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Classificação incompleta

> Ponto de entrada: passo P6 do fluxo principal.

#### E1.1. Informar os campos obrigatórios

O sistema informa os campos obrigatórios não preenchidos.

#### E1.2. Retornar à classificação

O sistema retorna ao passo P5 do fluxo principal.

### E2. Classificação incoerente

> Ponto de entrada: passo P6 do fluxo principal.

#### E2.1. Informar a incoerência

O sistema informa que o tema, a competência ou a disciplina selecionados não são compatíveis entre si.

#### E2.2. Retornar à classificação

O sistema retorna ao passo P5 do fluxo principal.

### E3. Questão alterada ou inativada por outro usuário

> Ponto de entrada: passo P7 do fluxo principal.

#### E3.1. Informar o conflito

O sistema informa que a questão foi alterada ou inativada desde a abertura e não grava a classificação.

#### E3.2. Retornar à lista

O sistema retorna ao passo P2 do fluxo principal.

### E4. Cadastros de classificação indisponíveis

> Ponto de entrada: passo P4 do fluxo principal.

#### E4.1. Informar a ausência de opções

O sistema informa que não há temas, competências ou grade curricular cadastrados e orienta contatar a Equipe Técnica.

#### E4.2. Encerrar caso de uso

O caso de uso é encerrado.

### E5. Falha ao gravar a classificação

> Ponto de entrada: passo P7 do fluxo principal.

#### E5.1. Desfazer alterações parciais

O sistema desfaz as alterações do lote ou da questão com falha, preservando a consistência dos dados.

#### E5.2. Informar erro

O sistema exibe mensagem informando a falha e encerra o caso de uso.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal executado pelo ator.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* As questões selecionadas ficam classificadas por tema, competência e grade curricular.
* A alteração fica registrada no histórico, com responsável, data e hora.
* As questões classificadas ficam disponíveis para os filtros de consulta (UC02) e para as estatísticas por assunto.

## 10. Requisitos Não Funcionais

* **Rastreabilidade:** toda classificação e reclassificação deve preservar o histórico com responsável, data e hora.
* **Usabilidade:** a classificação em lote e o avanço para a próxima questão devem reduzir o esforço em grandes volumes de questões.
* **Consistência:** a classificação em lote deve ser atômica, sem resultados parciais.
* **Desempenho:** a listagem e a filtragem devem responder em tempo adequado, mesmo com grande volume de questões.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Média; mais intensa após importações de provas (UC17) e cadastros de novas questões (UC10).

## 13. Interface Visual

### IV1. Tela de Lista de Questões para Classificação

Leiaute com filtros, lista de questões com situação da classificação, seleção múltipla e botão "Classificar em lote". Referência: _a definir (ex.: `prototipos/IV1-lista-classificacao.png`)_.

### IV2. Tela de Classificação da Questão

Leiaute com o enunciado da questão, campos de tema, competência e grade curricular, histórico de classificações e botões "Salvar" e "Salvar e próxima". Referência: _a definir (ex.: `prototipos/IV2-classificacao-questao.png`)_.

## 14. Observações

* Definir quem mantém os cadastros de temas e competências (o UC15 cobre apenas cursos e áreas).
* Definir se uma questão pode ter mais de um tema ou competência.
* Definir se a classificação feita pelo Professor requer validação da Equipe Técnica.
* A classificação alimenta os filtros do UC02 e as estatísticas dos UC05, UC09 e UC19.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-08 – Classificação por tema, competência e grade curricular.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC02 – Consultar banco de questões (F-01).
* UC10 – Cadastrar, editar e inativar questões (F-09).
* UC15 – Gerenciar cadastros de apoio: cursos e áreas (F-13).
* UC17 – Importar provas em PDF do INEP (F-07).

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
