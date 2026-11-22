# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC10 (F-09) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC10 – Cadastrar, editar e inativar questões

## 2. Objetivo

Permitir a manutenção do banco de questões, incluindo o cadastro, a edição e a inativação de questões com suas alternativas, gabarito e comentário explicativo (F-09).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Professor.
* Equipe Técnica.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil com permissão de gerenciar questões.
* Os cadastros de apoio (cursos e áreas) estão disponíveis (UC15).

## 6. Fluxo Principal

> Cenário: o ator cadastra uma nova questão no banco de questões.

### P1. Acessar a gestão de questões

O ator aciona a opção "Gerenciar questões".

### P2. Exibir a lista de questões

O sistema exibe a lista de questões cadastradas, com situação (ativa ou inativa), área e data de atualização.

### P3. Iniciar o cadastro

O ator aciona a opção "Nova questão".

### P4. Informar os dados da questão

O ator informa o enunciado, as alternativas, a alternativa correta, o curso e a área.

### P5. Validar os dados

O sistema valida o preenchimento dos campos obrigatórios e a consistência da questão (ao menos duas alternativas e exatamente uma correta).

### P6. Registrar o comentário do gabarito

O sistema aciona o UC11 – Registrar comentário do gabarito («include»), no qual o ator registra o comentário explicativo da questão.

### P7. Salvar a questão

O ator confirma o cadastro, e o sistema salva a questão como ativa.

### P8. Confirmar o cadastro

O sistema exibe a mensagem de sucesso e retorna ao passo P2 do fluxo principal.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Editar questão

> Ponto de entrada: passo P2 do fluxo principal.

#### A1.1. Selecionar a questão

O ator seleciona uma questão da lista e aciona a opção "Editar".

#### A1.2. Alterar os dados

O sistema exibe os dados da questão e o ator altera os campos desejados, retornando ao passo P5 do fluxo principal.

### A2. Inativar questão

> Ponto de entrada: passo P2 do fluxo principal.

#### A2.1. Solicitar a inativação

O ator seleciona uma questão ativa e aciona a opção "Inativar".

#### A2.2. Confirmar a inativação

O sistema solicita confirmação informando que a questão deixará de aparecer no banco de questões e em novos simulados.

#### A2.3. Inativar a questão

O ator confirma, e o sistema altera a situação da questão para inativa, preservando o histórico de simulados já realizados, e retorna ao passo P2 do fluxo principal.

### A3. Filtrar e buscar questões

> Ponto de entrada: passo P2 do fluxo principal.

#### A3.1. Informar os critérios

O ator filtra a lista por situação, curso, área ou texto do enunciado.

#### A3.2. Atualizar a lista

O sistema atualiza a lista e retorna ao passo P2 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Dados obrigatórios inválidos

> Ponto de entrada: passo P5 do fluxo principal.

#### E1.1. Informar os campos inválidos

O sistema destaca os campos inválidos ou não preenchidos e exibe a mensagem correspondente.

#### E1.2. Retornar ao preenchimento

O sistema retorna ao passo P4 do fluxo principal.

### E2. Questão em simulado em andamento

> Ponto de entrada: passos A1.2 e A2.3 do fluxo alternativo.

#### E2.1. Bloquear a alteração

Caso a questão pertença a simulado com tentativa em andamento, o sistema informa que a alteração do enunciado, das alternativas ou do gabarito não é permitida no momento.

#### E2.2. Retornar à lista

O sistema retorna ao passo P2 do fluxo principal.

### E3. Questão duplicada

> Ponto de entrada: passo P5 do fluxo principal.

#### E3.1. Alertar sobre a duplicidade

O sistema informa que existe questão com enunciado semelhante e solicita confirmação para prosseguir.

#### E3.2. Prosseguir ou cancelar

Se o ator confirmar, o sistema segue para o passo P6 do fluxo principal; caso contrário, retorna ao passo P4.

### E4. Falha ao salvar

> Ponto de entrada: passo P7 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando a falha, preserva os dados digitados e orienta tentar novamente.

#### E4.2. Retornar ao cadastro

O sistema retorna ao passo P7 do fluxo principal.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* A questão cadastrada ou editada fica registrada no banco de questões com autor e data de atualização.
* A questão inativada deixa de ser exibida no UC02 e de ser selecionável no UC12, mantendo o histórico dos simulados já realizados.

## 10. Requisitos Não Funcionais

* **Segurança:** apenas atores com perfil autorizado podem cadastrar, editar ou inativar questões, inclusive por acesso direto à API.
* **Rastreabilidade:** toda criação, edição e inativação deve ser registrada em log, com autor, data e hora.
* **Integridade:** a inativação não deve excluir fisicamente a questão nem alterar resultados de tentativas já finalizadas.
* **Usabilidade:** o editor deve permitir formatação básica do enunciado e a inclusão de imagens.

## 11. Ponto de Extensão

Não se aplica. Este caso de uso inclui o UC11 – Registrar comentário do gabarito («include»), no passo P6.

## 12. Frequência de Utilização

Média, com maior concentração nos períodos de preparação de simulados.

## 13. Interface Visual

### IV1. Tela de Lista de Questões (Gestão)

Leiaute com lista, filtros, situação e ações de editar e inativar. Referência: _a definir (ex.: `prototipos/IV1-gestao-questoes.png`)_.

### IV2. Tela de Formulário de Questão

Leiaute com enunciado, alternativas, seleção da correta, curso, área e campo de comentário. Referência: _a definir (ex.: `prototipos/IV2-formulario-questao.png`)_.

## 14. Observações

* No diagrama, o UC10 inclui o UC11 («include»).
* A associação com a Equipe Técnica foi inferida pelas linhas do diagrama e deve ser confirmada na revisão com o cliente.
* A classificação automática por tema, competência e grade curricular (UC18 – evolução futura) não faz parte deste caso de uso; neste momento, apenas curso e área são informados.
* Definir se o Professor pode editar questões de outros professores e se haverá fluxo de reativação de questões inativas.
* Definir a política de versionamento quando uma questão já utilizada em simulados finalizados for editada.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-09 – Gestão de questões.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC02 – Consultar banco de questões (F-01).
* UC04 – Consultar gabarito comentado (F-03).
* UC11 – Registrar comentário do gabarito.
* UC12 – Criar e gerenciar simulados (F-10).
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
