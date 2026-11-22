# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                 | Autor         |
| ---------- | ------ | ------------------------------------------------------------------------- | ------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC01 a partir do documento de visão e do diagrama de casos de uso do AdE (F-06). | Ian Carvalho Cirino|
|            |        |                                                                           |               |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC01 – Cadastrar e autenticar usuário

## 2. Objetivo

Permitir que um usuário do AdE – Amigo do Estudante crie sua conta e acesse o sistema de forma autenticada, de modo que as funcionalidades disponíveis sejam liberadas conforme o seu perfil (F-06).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Usuário não autenticado, que pode assumir um dos perfis: Estudante, Professor, Coordenação ou Equipe Técnica.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O usuário possui acesso ao sistema por meio de um navegador web.
* Para autenticar (fluxo principal), o usuário já possui cadastro ativo no sistema.

## 6. Fluxo Principal

> Cenário: usuário já cadastrado realiza autenticação com sucesso.

### P1. Acessar a tela de login

O ator acessa o endereço do sistema.

### P2. Exibir a tela de login

O sistema exibe a tela de autenticação com os campos de identificação (e-mail ou matrícula) e senha, e as opções "Criar conta" e "Esqueci minha senha".

### P3. Informar credenciais

O ator informa suas credenciais e aciona a opção "Entrar".

### P4. Validar credenciais

O sistema valida os campos obrigatórios e verifica se as credenciais correspondem a um usuário ativo.

### P5. Identificar perfil

O sistema identifica o perfil do usuário autenticado (Estudante, Professor, Coordenação ou Equipe Técnica).

### P6. Iniciar sessão

O sistema inicia a sessão do usuário e o direciona à página inicial correspondente ao seu perfil.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Cadastrar novo usuário

> Ponto de entrada: passo P2 do fluxo principal.

#### A1.1. Selecionar a opção de cadastro

O ator aciona a opção "Criar conta".

#### A1.2. Exibir formulário de cadastro

O sistema exibe o formulário de cadastro com os campos nome completo, e-mail, perfil, senha e confirmação de senha.

#### A1.3. Preencher dados

O ator preenche os dados e aciona a opção "Cadastrar".

#### A1.4. Validar dados

O sistema valida os campos obrigatórios, o formato do e-mail, a política de senha e a unicidade do e-mail.

#### A1.5. Registrar usuário

O sistema registra o usuário com o perfil informado e exibe a mensagem de cadastro realizado com sucesso.

#### A1.6. Retornar ao login

O sistema retorna ao passo P2 do fluxo principal.

### A2. Recuperar senha

> Ponto de entrada: passo P2 do fluxo principal.

#### A2.1. Selecionar a opção de recuperação

O ator aciona a opção "Esqueci minha senha".

#### A2.2. Solicitar identificação

O sistema solicita o e-mail cadastrado.

#### A2.3. Informar e-mail

O ator informa o e-mail e confirma.

#### A2.4. Enviar instruções

O sistema envia ao e-mail informado as instruções para redefinição de senha e exibe mensagem de confirmação.

#### A2.5. Redefinir senha

O ator acessa o link recebido e informa a nova senha.

#### A2.6. Atualizar senha

O sistema valida a nova senha, a atualiza e retorna ao passo P2 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Credenciais inválidas

> Ponto de entrada: passo P4 do fluxo principal.

#### E1.1. Informar falha de autenticação

O sistema exibe a mensagem "Usuário ou senha inválidos" sem indicar qual dos campos está incorreto.

#### E1.2. Retornar à tela de login

O sistema retorna ao passo P2 do fluxo principal.

### E2. Campos obrigatórios não preenchidos

> Pontos de entrada: passo P4 do fluxo principal e passo A1.4 do fluxo alternativo A1.

#### E2.1. Destacar campos pendentes

O sistema destaca os campos obrigatórios não preenchidos e exibe mensagem orientando o preenchimento.

#### E2.2. Retornar ao passo de origem

O sistema retorna ao passo P3 (fluxo principal) ou ao passo A1.3 (fluxo A1).

### E3. E-mail já cadastrado

> Ponto de entrada: passo A1.4 do fluxo alternativo A1.

#### E3.1. Informar duplicidade

O sistema exibe a mensagem informando que o e-mail já possui cadastro e sugere a opção "Esqueci minha senha".

#### E3.2. Retornar ao formulário

O sistema retorna ao passo A1.3.

### E4. Senha fora da política de segurança

> Pontos de entrada: passo A1.4 do fluxo A1 e passo A2.6 do fluxo A2.

#### E4.1. Informar requisitos de senha

O sistema exibe os requisitos mínimos de senha não atendidos.

#### E4.2. Retornar ao passo de origem

O sistema retorna ao passo A1.3 ou ao passo A2.5, conforme o fluxo de origem.

### E5. Usuário inativo ou bloqueado

> Ponto de entrada: passo P4 do fluxo principal.

#### E5.1. Informar indisponibilidade de acesso

O sistema exibe a mensagem informando que o acesso do usuário está inativo ou bloqueado e orienta a procurar a Equipe Técnica.

#### E5.2. Encerrar caso de uso

O caso de uso é encerrado.

### E6. Bloqueio temporário por tentativas excessivas

> Ponto de entrada: passo P4 do fluxo principal.

#### E6.1. Bloquear tentativas

Após 5 tentativas consecutivas de autenticação inválidas, o sistema bloqueia temporariamente novas tentativas para o usuário e exibe mensagem com o tempo de espera.

#### E6.2. Encerrar caso de uso

O caso de uso é encerrado.

## 9. Pós-condições

* Em caso de autenticação bem-sucedida, o usuário possui uma sessão ativa associada ao seu perfil de acesso.
* Em caso de cadastro bem-sucedido, o novo usuário está registrado no sistema e apto a se autenticar.
* Em caso de recuperação de senha bem-sucedida, a senha do usuário está atualizada.

## 10. Requisitos Não Funcionais

* **Segurança:** as senhas devem ser armazenadas de forma criptografada (hash com salt), e a comunicação deve ocorrer por canal seguro (HTTPS).
* **Segurança:** a sessão deve expirar após período de inatividade a ser definido na Especificação de RNF.
* **Privacidade:** o tratamento dos dados pessoais deve estar em conformidade com a LGPD.
* **Usabilidade:** a tela de login deve ser responsiva e utilizável em dispositivos móveis.
* **Desempenho:** a autenticação deve ser concluída em até 3 segundos em condições normais de uso.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Alta. O caso de uso é executado a cada acesso ao sistema; as informações mais acessadas são as credenciais do usuário e seu perfil de acesso.

## 13. Interface Visual

### IV1. Tela de Login

Leiaute da tela de autenticação (campos de identificação e senha, botão "Entrar", links "Criar conta" e "Esqueci minha senha"). Referência: _a definir (ex.: `prototipos/IV1-tela-login.png`)_.

### IV2. Tela de Cadastro de Usuário

Leiaute do formulário de cadastro (nome, e-mail, perfil, senha e confirmação). Referência: _a definir (ex.: `prototipos/IV2-tela-cadastro.png`)_.

## 14. Observações

* No diagrama, o UC01 se relaciona aos atores Estudante, Professor, Coordenação e Equipe Técnica; por isso o ator primário foi descrito como usuário genérico com esses quatro perfis.
* A definição de quais perfis podem se autocadastrar (por exemplo, se Professor, Coordenação e Equipe Técnica exigem aprovação prévia) deve ser validada com o cliente.
* A integração com a Unifor Online para autenticação única (SSO) não consta neste caso de uso no diagrama; avaliar se será necessária (relação com o UC16).
* Os valores de política de senha, tempo de bloqueio e expiração de sessão devem ser confirmados na Especificação de RNF.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Funcionalidade F-06 – Cadastro e autenticação de usuário.
* UC10 – Cadastrar, editar e inativar questões (F-09).
* UC14 – Gerenciar usuários e perfis (F-13).

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
