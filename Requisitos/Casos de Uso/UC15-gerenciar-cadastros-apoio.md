# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC15 (F-13) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC15 – Gerenciar cadastros de apoio: cursos e áreas

## 2. Objetivo

Permitir que a Equipe Técnica mantenha os cadastros de apoio de cursos e áreas, utilizados na classificação de questões, na organização de turmas e nos vínculos de usuários (F-13).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Equipe Técnica.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil Equipe Técnica.

## 6. Fluxo Principal

> Cenário: a Equipe Técnica cadastra um novo curso.

### P1. Acessar os cadastros de apoio

O ator aciona a opção "Cadastros de apoio".

### P2. Selecionar o tipo de cadastro

O ator seleciona "Cursos" ou "Áreas".

### P3. Exibir a lista de registros

O sistema exibe a lista dos registros do cadastro selecionado, com nome, situação (ativo ou inativo) e quantidade de vínculos.

### P4. Iniciar o cadastro

O ator aciona a opção "Novo registro".

### P5. Informar os dados

O ator informa o nome, o código (quando aplicável) e, para áreas, o curso ao qual se vincula.

### P6. Validar os dados

O sistema valida o preenchimento dos campos obrigatórios e a unicidade do registro.

### P7. Salvar o registro

O ator confirma, e o sistema salva o registro como ativo e registra a operação em log.

### P8. Confirmar a operação

O sistema exibe a mensagem de sucesso e retorna ao passo P3 do fluxo principal.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Editar registro

> Ponto de entrada: passo P3 do fluxo principal.

#### A1.1. Selecionar o registro

O ator seleciona um registro e aciona a opção "Editar".

#### A1.2. Alterar os dados

O sistema exibe os dados e o ator os altera, seguindo para o passo P6 do fluxo principal.

### A2. Inativar ou reativar registro

> Ponto de entrada: passo P3 do fluxo principal.

#### A2.1. Solicitar a alteração de situação

O ator seleciona um registro e aciona a opção "Inativar" (ou "Reativar"). O sistema solicita confirmação informando os vínculos existentes.

#### A2.2. Atualizar a situação

O ator confirma, e o sistema atualiza a situação, preservando os vínculos históricos, e retorna ao passo P3 do fluxo principal.

### A3. Buscar registro

> Ponto de entrada: passo P3 do fluxo principal.

#### A3.1. Informar o critério

O ator busca por nome ou código.

#### A3.2. Atualizar a lista

O sistema atualiza a lista e retorna ao passo P3 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Registro duplicado

> Ponto de entrada: passo P6 do fluxo principal.

#### E1.1. Informar a duplicidade

O sistema informa que já existe registro com o mesmo nome ou código.

#### E1.2. Retornar ao preenchimento

O sistema retorna ao passo P5 do fluxo principal.

### E2. Dados obrigatórios inválidos

> Ponto de entrada: passo P6 do fluxo principal.

#### E2.1. Informar os campos inválidos

O sistema destaca os campos obrigatórios não preenchidos.

#### E2.2. Retornar ao preenchimento

O sistema retorna ao passo P5 do fluxo principal.

### E3. Registro gerenciado pela sincronização

> Ponto de entrada: passos A1.2 e A2.1 do fluxo alternativo.

#### E3.1. Informar a restrição

Caso o registro seja mantido pela sincronização com a Unifor Online (UC16), o sistema informa que a alteração deve ser feita na origem.

#### E3.2. Retornar à lista

O sistema retorna ao passo P3 do fluxo principal.

### E4. Falha ao salvar

> Ponto de entrada: passo P7 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando a falha, preserva os dados e orienta tentar novamente.

#### E4.2. Retornar ao cadastro

O sistema retorna ao passo P5 do fluxo principal.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Os cursos e áreas cadastrados ficam disponíveis para uso no UC10 (classificação de questões), UC14 (vínculos de usuários) e UC13 (turmas).
* Registros inativados deixam de ser oferecidos em novos cadastros, preservando o histórico.

## 10. Requisitos Não Funcionais

* **Segurança:** apenas a Equipe Técnica pode alterar os cadastros de apoio, inclusive por acesso direto à API.
* **Rastreabilidade:** toda criação, edição e inativação deve ser registrada em log, com autor, data e hora.
* **Integridade:** registros com vínculos não podem ser excluídos fisicamente.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa, concentrada na configuração inicial e no início dos períodos letivos.

## 13. Interface Visual

### IV1. Tela de Cadastros de Apoio

Leiaute com seleção do tipo de cadastro, lista de registros, busca e ações. Referência: _a definir (ex.: `prototipos/IV1-cadastros-apoio.png`)_.

### IV2. Tela de Formulário de Curso ou Área

Leiaute com nome, código, vínculo e situação. Referência: _a definir (ex.: `prototipos/IV2-formulario-apoio.png`)_.

## 14. Observações

* O título do caso de uso no diagrama cita "cursos e áreas"; confirmar com o cliente se outros cadastros de apoio (por exemplo, disciplinas ou períodos letivos) fazem parte do escopo da F-13.
* Definir quais registros são alimentados pela sincronização com a Unifor Online (UC16) e quais podem ser editados manualmente.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-13 – Administração de usuários e cadastros de apoio.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC10 – Cadastrar, editar e inativar questões (F-09).
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
