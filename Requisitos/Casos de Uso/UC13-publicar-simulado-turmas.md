# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC13 a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC13 – Publicar simulado para turmas

## 2. Objetivo

Permitir que o Professor disponibilize um simulado pronto para as turmas selecionadas, definindo a janela de realização, para que os estudantes possam realizá-lo.

## 3. Tipo de Caso de Uso

Concreto (incluído pelo UC12).

## 4. Atores

### 4.1 Primário

* Professor.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O Professor está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O simulado está criado e possui ao menos uma questão ativa (UC12).
* As turmas estão cadastradas no sistema (UC15, UC16).

## 6. Fluxo Principal

> Cenário: o Professor publica um simulado em rascunho para uma ou mais turmas.

### P1. Selecionar o simulado

O Professor seleciona um simulado em rascunho e aciona a opção "Publicar".

### P2. Validar o simulado

O sistema verifica se o simulado está completo e se todas as questões estão ativas.

### P3. Exibir as turmas disponíveis

O sistema exibe as turmas do Professor disponíveis para publicação.

### P4. Selecionar as turmas

O Professor seleciona uma ou mais turmas.

### P5. Definir a janela de realização

O Professor informa a data e a hora de início e de encerramento do simulado.

### P6. Revisar a publicação

O sistema exibe o resumo com simulado, turmas, janela de realização e regra de liberação do gabarito.

### P7. Confirmar a publicação

O Professor confirma a publicação.

### P8. Publicar o simulado

O sistema altera a situação do simulado para publicado e o torna disponível aos estudantes das turmas selecionadas para realização (UC03 – Realizar simulado cronometrado).

### P9. Confirmar a operação

O sistema exibe a mensagem de sucesso e retorna ao caso de uso de origem.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Alterar a janela ou as turmas antes do início

> Ponto de entrada: passo P1 do fluxo principal (simulado já publicado, ainda não iniciado).

#### A1.1. Exibir a publicação atual

O sistema exibe as turmas e a janela atualmente definidas.

#### A1.2. Alterar os dados

O Professor altera as turmas ou a janela e segue para o passo P6 do fluxo principal.

### A2. Cancelar a publicação

> Ponto de entrada: passo P1 do fluxo principal (simulado publicado, ainda não iniciado).

#### A2.1. Solicitar o cancelamento

O Professor aciona a opção "Cancelar publicação" e o sistema solicita confirmação.

#### A2.2. Despublicar o simulado

O Professor confirma, e o sistema retorna o simulado à situação de rascunho e o retira da visualização dos estudantes.

### A3. Publicar para todas as turmas do Professor

> Ponto de entrada: passo P4 do fluxo principal.

#### A3.1. Selecionar todas

O Professor aciona a opção "Selecionar todas as turmas".

#### A3.2. Prosseguir

O sistema marca todas as turmas disponíveis e segue para o passo P5 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Simulado incompleto ou com questão inativa

> Ponto de entrada: passo P2 do fluxo principal.

#### E1.1. Informar a pendência

O sistema informa as pendências do simulado (sem questões, questão inativada ou dados obrigatórios ausentes).

#### E1.2. Retornar à edição

O sistema retorna ao UC12 – Criar e gerenciar simulados para ajuste.

### E2. Nenhuma turma selecionada

> Ponto de entrada: passo P7 do fluxo principal.

#### E2.1. Informar a restrição

O sistema informa que ao menos uma turma deve ser selecionada.

#### E2.2. Retornar à seleção

O sistema retorna ao passo P4 do fluxo principal.

### E3. Janela de realização inválida

> Ponto de entrada: passo P5 do fluxo principal.

#### E3.1. Informar a inconsistência

O sistema informa que a data de encerramento deve ser posterior à de início e que o período deve comportar a duração do simulado.

#### E3.2. Retornar ao preenchimento

O sistema retorna ao passo P5 do fluxo principal.

### E4. Turma sem estudantes

> Ponto de entrada: passo P4 do fluxo principal.

#### E4.1. Alertar sobre a turma

O sistema informa que a turma selecionada não possui estudantes vinculados e solicita confirmação para prosseguir.

#### E4.2. Prosseguir ou retornar

Se o Professor confirmar, o sistema segue para o passo P5; caso contrário, retorna ao passo P4.

### E5. Falha na publicação

> Ponto de entrada: passo P8 do fluxo principal.

#### E5.1. Informar erro

O sistema exibe mensagem informando a falha, mantém o simulado como rascunho e orienta tentar novamente.

#### E5.2. Retornar à revisão

O sistema retorna ao passo P6 do fluxo principal.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* O simulado fica publicado e visível apenas aos estudantes das turmas selecionadas, dentro da janela definida.
* Os dados de acompanhamento do simulado ficam disponíveis para o UC09 – Acompanhar desempenho de turmas e alunos.

## 10. Requisitos Não Funcionais

* **Segurança:** o simulado não deve ser acessível a estudantes de turmas não selecionadas, inclusive por acesso direto à URL ou à API.
* **Confiabilidade:** a publicação deve ser atômica, não deixando o simulado parcialmente publicado em caso de falha.
* **Rastreabilidade:** publicação e cancelamento devem ser registrados em log, com autor, data e hora.

## 11. Ponto de Extensão

Não se aplica. Este caso de uso é incluído pelo UC12 – Criar e gerenciar simulados («include»).

## 12. Frequência de Utilização

Média, concentrada no início dos períodos de avaliação.

## 13. Interface Visual

### IV1. Tela de Publicação do Simulado

Leiaute com seleção de turmas, janela de realização e resumo da publicação. Referência: _a definir (ex.: `prototipos/IV1-publicar-simulado.png`)_.

## 14. Observações

* No diagrama, o UC13 é incluído pelo UC12 e está associado ao Professor; as linhas para a Equipe Técnica devem ser confirmadas na revisão com o cliente.
* Definir se haverá notificação aos estudantes ao publicar e se a janela poderá ser individualizada por turma.
* Definir o tratamento de simulados com tentativas iniciadas ao cancelar a publicação (atualmente restrito a simulados não iniciados).

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-10 – Gestão de simulados.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC03 – Realizar simulado cronometrado (F-02).
* UC09 – Acompanhar desempenho de turmas e alunos (F-11).
* UC12 – Criar e gerenciar simulados (F-10).
* UC15 – Gerenciar cadastros de apoio: cursos e áreas (F-13).
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
