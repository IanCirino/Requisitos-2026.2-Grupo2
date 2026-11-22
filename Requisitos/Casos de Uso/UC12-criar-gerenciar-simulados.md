# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC12 (F-10) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC12 – Criar e gerenciar simulados

## 2. Objetivo

Permitir que o Professor crie, edite e gerencie simulados a partir de questões do banco de questões, definindo duração e regras de liberação do gabarito (F-10).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Professor.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O Professor está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* Existem questões ativas no banco de questões (UC10).

## 6. Fluxo Principal

> Cenário: o Professor cria um novo simulado e o publica para as turmas.

### P1. Acessar a gestão de simulados

O Professor aciona a opção "Gerenciar simulados".

### P2. Exibir a lista de simulados

O sistema exibe os simulados do Professor com título, situação (rascunho, publicado ou encerrado) e data de atualização.

### P3. Iniciar a criação

O Professor aciona a opção "Novo simulado".

### P4. Informar os dados do simulado

O Professor informa o título, a descrição, a duração e a regra de liberação do gabarito (imediata, após o encerramento do período ou definida pelo Professor).

### P5. Selecionar as questões

O sistema aciona o UC02 – Consultar banco de questões («include») para que o Professor pesquise e selecione as questões do simulado.

### P6. Definir a ordem das questões

O Professor ordena as questões e, quando aplicável, define o peso de cada uma.

### P7. Revisar o simulado

O sistema exibe o resumo do simulado com quantidade de questões, duração e regras definidas.

### P8. Salvar o simulado

O Professor confirma, e o sistema salva o simulado como rascunho.

### P9. Publicar o simulado

O sistema aciona o UC13 – Publicar simulado para turmas («include») quando o Professor opta por publicar.

### P10. Confirmar a operação

O sistema exibe a mensagem de sucesso e retorna ao passo P2 do fluxo principal.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Editar simulado

> Ponto de entrada: passo P2 do fluxo principal.

#### A1.1. Selecionar o simulado

O Professor seleciona um simulado em rascunho e aciona a opção "Editar".

#### A1.2. Alterar os dados

O sistema exibe os dados do simulado e o Professor os altera, retornando ao passo P7 do fluxo principal.

### A2. Duplicar simulado

> Ponto de entrada: passo P2 do fluxo principal.

#### A2.1. Solicitar a duplicação

O Professor seleciona um simulado e aciona a opção "Duplicar".

#### A2.2. Criar a cópia

O sistema cria uma cópia em rascunho, sem turmas vinculadas, e segue para o passo A1.2 do fluxo alternativo A1.

### A3. Excluir simulado em rascunho

> Ponto de entrada: passo P2 do fluxo principal.

#### A3.1. Solicitar a exclusão

O Professor seleciona um simulado em rascunho e aciona a opção "Excluir". O sistema solicita confirmação.

#### A3.2. Excluir o simulado

O Professor confirma, e o sistema exclui o simulado e retorna ao passo P2 do fluxo principal.

### A4. Salvar sem publicar

> Ponto de entrada: passo P9 do fluxo principal.

#### A4.1. Manter como rascunho

O Professor opta por não publicar, e o sistema mantém o simulado como rascunho e segue para o passo P10 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Simulado sem questões

> Ponto de entrada: passo P8 do fluxo principal.

#### E1.1. Informar a restrição

O sistema informa que o simulado deve possuir ao menos uma questão.

#### E1.2. Retornar à seleção

O sistema retorna ao passo P5 do fluxo principal.

### E2. Dados do simulado inválidos

> Ponto de entrada: passo P4 do fluxo principal.

#### E2.1. Informar os campos inválidos

O sistema destaca os campos obrigatórios não preenchidos ou valores inválidos (por exemplo, duração igual a zero).

#### E2.2. Retornar ao preenchimento

O sistema retorna ao passo P4 do fluxo principal.

### E3. Questão inativada

> Ponto de entrada: passo A1.2 do fluxo alternativo A1.

#### E3.1. Alertar sobre a questão inativa

O sistema informa que uma ou mais questões do simulado foram inativadas (UC10) e solicita a substituição ou a remoção.

#### E3.2. Retornar à seleção

O sistema retorna ao passo P5 do fluxo principal.

### E4. Simulado já publicado

> Ponto de entrada: passo A1.1 do fluxo alternativo A1.

#### E4.1. Bloquear a edição

Caso o simulado já esteja publicado e possua tentativas iniciadas, o sistema informa que a edição de questões não é permitida.

#### E4.2. Retornar à lista

O sistema retorna ao passo P2 do fluxo principal.

### E5. Falha ao salvar

> Ponto de entrada: passo P8 do fluxo principal.

#### E5.1. Informar erro

O sistema exibe mensagem informando a falha, preserva os dados e orienta tentar novamente.

#### E5.2. Retornar à revisão

O sistema retorna ao passo P7 do fluxo principal.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* O simulado fica registrado com situação rascunho ou publicado.
* A regra de liberação do gabarito definida fica disponível para o UC04 – Consultar gabarito comentado.

## 10. Requisitos Não Funcionais

* **Segurança:** apenas Professores autorizados podem criar e gerenciar simulados, e cada Professor só edita os simulados sob sua responsabilidade.
* **Integridade:** simulados com tentativas iniciadas não podem ter questões alteradas.
* **Usabilidade:** a seleção de questões deve permitir filtros e visualização prévia do enunciado.

## 11. Ponto de Extensão

Não se aplica. Este caso de uso inclui o UC02 – Consultar banco de questões e o UC13 – Publicar simulado para turmas («include»).

## 12. Frequência de Utilização

Média, concentrada no início dos períodos de avaliação.

## 13. Interface Visual

### IV1. Tela de Lista de Simulados

Leiaute com lista, situação e ações (editar, duplicar, excluir, publicar). Referência: _a definir (ex.: `prototipos/IV1-lista-simulados.png`)_.

### IV2. Tela de Formulário de Simulado

Leiaute com dados gerais, seleção e ordenação de questões e resumo. Referência: _a definir (ex.: `prototipos/IV2-formulario-simulado.png`)_.

## 14. Observações

* No diagrama, o UC12 inclui o UC02 e o UC13 («include»), conforme as setas tracejadas.
* A regra de liberação do gabarito (pendência registrada no UC04) é definida neste caso de uso.
* Definir se o simulado terá embaralhamento de questões/alternativas e número máximo de tentativas.
* Definir se simulados poderão ser compartilhados entre professores.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-10 – Gestão de simulados.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC02 – Consultar banco de questões (F-01).
* UC04 – Consultar gabarito comentado (F-03).
* UC10 – Cadastrar, editar e inativar questões (F-09).
* UC13 – Publicar simulado para turmas.

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
