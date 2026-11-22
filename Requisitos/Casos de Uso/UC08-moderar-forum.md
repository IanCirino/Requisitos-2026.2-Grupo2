# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição | Autor |
| ---------- | ------ | --------- | ----- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC08 a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |           |       |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC08 – Moderar fórum

## 2. Objetivo

Permitir que os moderadores analisem conteúdos denunciados ou recentes do fórum e apliquem as ações de moderação cabíveis.

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Professor.
* Equipe Técnica.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O usuário está autenticado no sistema com perfil habilitado para moderação (UC01 – Cadastrar e autenticar usuário).
* Existem conteúdos denunciados ou publicados no fórum (UC07).

## 6. Fluxo Principal

> Cenário: o moderador analisa um conteúdo denunciado e decide removê-lo.

### P1. Acessar a moderação

O ator seleciona a opção "Moderação do fórum" no menu do sistema.

### P2. Exibir a fila de moderação

O sistema exibe a lista de conteúdos denunciados e recentes, com o motivo e a quantidade de denúncias, ordenada por prioridade.

### P3. Selecionar um conteúdo

O ator seleciona um conteúdo da fila.

### P4. Exibir o conteúdo

O sistema exibe o conteúdo no seu contexto, as denúncias recebidas e o histórico de moderação do autor.

### P5. Decidir a ação

O ator seleciona a ação: manter, ocultar, remover ou suspender o autor do fórum.

### P6. Informar a justificativa

O ator informa a justificativa da decisão e aciona a opção "Confirmar".

### P7. Registrar a decisão

O sistema aplica a ação, registra a decisão (moderador, data e justificativa) e notifica o autor do conteúdo.

### P8. Atualizar a fila

O sistema remove o item da fila e retorna ao passo P2.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Fechar tópico

> Ponto de entrada: passo P4 do fluxo principal. Retorna ao passo P2.

#### A1.1. Solicitar o fechamento

O ator aciona a opção "Fechar tópico".

#### A1.2. Bloquear novas respostas

O sistema bloqueia novas respostas, registra a ação e retorna ao passo P2.

### A2. Marcar denúncia como improcedente

> Ponto de entrada: passo P5 do fluxo principal. Retorna ao passo P2.

#### A2.1. Indicar improcedência

O ator aciona a opção "Denúncia improcedente".

#### A2.2. Manter o conteúdo

O sistema mantém o conteúdo visível, registra a decisão e retorna ao passo P2.

## 8. Fluxos de Exceção

### E1. Conteúdo já tratado

> Pontos de entrada: passos P3 e P7 do fluxo principal.

#### E1.1. Informar o tratamento prévio

O sistema exibe a mensagem informando que o conteúdo já foi tratado por outro moderador ou removido.

#### E1.2. Retornar à fila

O sistema atualiza a fila e retorna ao passo P2.

### E2. Justificativa não informada

> Ponto de entrada: passo P6 do fluxo principal.

#### E2.1. Informar a obrigatoriedade

O sistema destaca o campo e exibe mensagem informando que a justificativa é obrigatória.

#### E2.2. Retornar à decisão

O sistema retorna ao passo P6.

### E3. Falha ao registrar a decisão

> Ponto de entrada: passo P7 do fluxo principal.

#### E3.1. Informar erro

O sistema exibe mensagem informando falha ao aplicar a ação e mantém o item na fila.

#### E3.2. Retornar à decisão

O sistema retorna ao passo P5.

### E4. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E4.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* A decisão de moderação está aplicada e registrada com autor, data e justificativa.
* O autor do conteúdo foi notificado da decisão.

## 10. Requisitos Não Funcionais

* **Rastreabilidade:** todas as ações de moderação devem ser registradas em log de auditoria, não editável.
* **Segurança:** apenas perfis habilitados podem acessar as funcionalidades de moderação.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa a média, conforme o volume de denúncias.

## 13. Interface Visual

### IV1. Fila de Moderação

Leiaute com a lista de conteúdos denunciados, filtros e indicadores de prioridade. Referência: _a definir (ex.: `prototipos/UC08-IV1.png`)_.

### IV2. Tela de Análise do Conteúdo

Leiaute com o conteúdo em contexto, denúncias, ações disponíveis e campo de justificativa. Referência: _a definir (ex.: `prototipos/UC08-IV2.png`)_.

## 14. Observações

* O diagrama não apresenta código de funcionalidade (F-xx) para este caso de uso; confirmar na Visão da Demanda (provável relação com F-05).
* Os atores foram atribuídos conforme as ligações do diagrama; validar quais perfis atuam como moderadores.
* Definir políticas de suspensão (prazo e reincidência).

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC07 – Participar do fórum de discussão (F-05).

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
