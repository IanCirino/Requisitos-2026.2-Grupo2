# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC16 (F-12) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC16 – Sincronizar dados com a Unifor Online

## 2. Objetivo

Permitir que a Equipe Técnica execute e acompanhe a sincronização de dados entre o AdE e a Unifor Online (sistema externo), mantendo atualizados usuários, cursos, turmas e vínculos (F-12).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Equipe Técnica.

### 4.2 Secundário

* Unifor Online (sistema externo).

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil Equipe Técnica.
* A integração com a Unifor Online está configurada (endereço, credenciais e escopo de dados).

## 6. Fluxo Principal

> Cenário: a Equipe Técnica aciona manualmente a sincronização de dados.

### P1. Acessar a sincronização

O ator aciona a opção "Sincronizar com a Unifor Online".

### P2. Exibir o painel de sincronização

O sistema exibe a data e o resultado da última sincronização e as opções de execução.

### P3. Solicitar a sincronização

O ator seleciona os dados a sincronizar (usuários, cursos, turmas e vínculos) e aciona a opção "Sincronizar agora".

### P4. Solicitar os dados à Unifor Online

O sistema solicita à Unifor Online os dados selecionados.

### P5. Enviar os dados

A Unifor Online disponibiliza os dados solicitados ao sistema.

### P6. Validar e comparar os dados

O sistema valida o formato e a consistência dos dados recebidos e os compara com os dados existentes, identificando registros novos, alterados e inativados.

### P7. Aplicar as alterações

O sistema cria, atualiza e inativa os registros correspondentes (UC14, UC15), preservando o histórico.

### P8. Registrar o resultado

O sistema registra a sincronização em log, com data, hora, responsável e quantidade de registros processados, criados, alterados e rejeitados.

### P9. Exibir o resumo

O sistema exibe o resumo da sincronização ao ator.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Sincronização agendada

> Ponto de entrada: passo P4 do fluxo principal (substitui os passos P1 a P3).

#### A1.1. Disparar no horário configurado

O sistema dispara a sincronização automaticamente no horário agendado e segue para o passo P4 do fluxo principal.

#### A1.2. Notificar o resultado

Ao final do passo P8, o sistema notifica a Equipe Técnica caso haja falhas ou registros rejeitados.

### A2. Reprocessar registros rejeitados

> Ponto de entrada: passo P9 do fluxo principal.

#### A2.1. Solicitar o reprocessamento

O ator seleciona os registros rejeitados e aciona a opção "Reprocessar".

#### A2.2. Reprocessar

O sistema reaplica a validação aos registros selecionados e retorna ao passo P8 do fluxo principal.

### A3. Consultar histórico de sincronizações

> Ponto de entrada: passo P2 do fluxo principal.

#### A3.1. Acessar o histórico

O ator aciona a opção "Histórico".

#### A3.2. Exibir o histórico

O sistema exibe as sincronizações anteriores com seus resultados e retorna ao passo P2 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Unifor Online indisponível

> Pontos de entrada: passos P4 e P5 do fluxo principal.

#### E1.1. Informar a indisponibilidade

O sistema informa que a Unifor Online não respondeu no tempo esperado e registra a falha em log.

#### E1.2. Encerrar caso de uso

O sistema mantém os dados atuais sem alteração e o caso de uso é encerrado.

### E2. Falha de autenticação da integração

> Ponto de entrada: passo P4 do fluxo principal.

#### E2.1. Informar a falha

O sistema informa que a autenticação com a Unifor Online foi recusada e orienta verificar a configuração da integração.

#### E2.2. Encerrar caso de uso

O caso de uso é encerrado.

### E3. Dados inválidos ou inconsistentes

> Ponto de entrada: passo P6 do fluxo principal.

#### E3.1. Rejeitar os registros inválidos

O sistema rejeita os registros inválidos, mantém os dados anteriores correspondentes e registra o motivo em log.

#### E3.2. Prosseguir com os demais

O sistema segue para o passo P7 do fluxo principal com os registros válidos.

### E4. Sincronização em andamento

> Ponto de entrada: passo P3 do fluxo principal.

#### E4.1. Informar a restrição

O sistema informa que já existe uma sincronização em execução.

#### E4.2. Retornar ao painel

O sistema retorna ao passo P2 do fluxo principal.

### E5. Falha ao aplicar alterações

> Ponto de entrada: passo P7 do fluxo principal.

#### E5.1. Desfazer alterações parciais

O sistema desfaz as alterações do lote com falha, preservando a consistência dos dados.

#### E5.2. Informar erro

O sistema exibe mensagem informando a falha e encerra o caso de uso.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal executado pelo ator.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Usuários, cursos, turmas e vínculos do AdE ficam atualizados conforme a Unifor Online.
* O resultado da sincronização fica registrado em log e disponível no histórico.

## 10. Requisitos Não Funcionais

* **Segurança:** a comunicação com a Unifor Online deve ser protegida por canal criptografado e credenciais armazenadas de forma segura.
* **Confiabilidade:** a sincronização deve ser idempotente e atômica por lote, permitindo reprocessamento sem duplicar registros.
* **Rastreabilidade:** cada execução deve ser registrada em log, com origem (manual ou agendada), responsável, data e hora.
* **Privacidade:** apenas os dados estritamente necessários devem ser importados, conforme a LGPD.
* **Desempenho:** a sincronização não deve degradar a disponibilidade do sistema para os demais usuários.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa para execução manual; periódica (por exemplo, diária) para execução agendada.

## 13. Interface Visual

### IV1. Tela de Painel de Sincronização

Leiaute com status da última execução, seleção de dados, botão "Sincronizar agora" e histórico. Referência: _a definir (ex.: `prototipos/IV1-painel-sincronizacao.png`)_.

### IV2. Tela de Resumo da Sincronização

Leiaute com contagem de registros criados, alterados, inativados e rejeitados e detalhes das rejeições. Referência: _a definir (ex.: `prototipos/IV2-resumo-sincronizacao.png`)_.

## 14. Observações

* A Unifor Online é o ator secundário («sistema externo») e está associada ao UC16 no diagrama.
* Definir o mecanismo de integração (API, arquivo ou banco intermediário), a periodicidade e o sentido da sincronização (somente importação ou bidirecional).
* Definir a regra de prevalência em caso de conflito entre dado local e dado da Unifor Online (relação com os fluxos E3 dos UC14 e UC15).
* Definir se resultados de simulados serão enviados à Unifor Online.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-12 – Integração com a Unifor Online.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC14 – Gerenciar usuários e perfis (F-13).
* UC15 – Gerenciar cadastros de apoio: cursos e áreas (F-13).

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
