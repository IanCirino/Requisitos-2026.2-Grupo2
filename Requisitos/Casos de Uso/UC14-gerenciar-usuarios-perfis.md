# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC14 (F-13) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC14 – Gerenciar usuários e perfis

## 2. Objetivo

Permitir que a Equipe Técnica gerencie os usuários do sistema e seus perfis de acesso (Estudante, Professor, Coordenação e Equipe Técnica), incluindo vínculos com cursos e turmas e a ativação ou inativação de contas (F-13).

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
* Os cadastros de apoio (cursos e áreas) estão disponíveis (UC15).

## 6. Fluxo Principal

> Cenário: a Equipe Técnica altera o perfil de um usuário existente.

### P1. Acessar a gestão de usuários

O ator aciona a opção "Gerenciar usuários".

### P2. Exibir a lista de usuários

O sistema exibe a lista de usuários com nome, e-mail, perfil, vínculos e situação (ativo ou inativo).

### P3. Buscar e filtrar usuários

O ator busca por nome ou e-mail e filtra por perfil ou situação, e o sistema atualiza a lista.

### P4. Selecionar o usuário

O ator seleciona um usuário e aciona a opção "Editar".

### P5. Exibir os dados do usuário

O sistema exibe os dados cadastrais, o perfil, os vínculos com cursos e turmas e a situação do usuário.

### P6. Alterar perfil e vínculos

O ator altera o perfil e os vínculos do usuário.

### P7. Validar os dados

O sistema valida as alterações e a consistência entre o perfil e os vínculos informados.

### P8. Salvar as alterações

O ator confirma, e o sistema salva as alterações e registra a operação em log.

### P9. Confirmar a operação

O sistema exibe a mensagem de sucesso e retorna ao passo P2 do fluxo principal.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Cadastrar usuário manualmente

> Ponto de entrada: passo P2 do fluxo principal.

#### A1.1. Iniciar o cadastro

O ator aciona a opção "Novo usuário".

#### A1.2. Informar os dados

O ator informa nome, e-mail, perfil e vínculos, e o sistema segue para o passo P7 do fluxo principal.

### A2. Inativar ou reativar usuário

> Ponto de entrada: passo P4 do fluxo principal.

#### A2.1. Alterar a situação

O ator aciona a opção "Inativar" (ou "Reativar") e o sistema solicita confirmação.

#### A2.2. Atualizar a situação

O ator confirma, e o sistema atualiza a situação do usuário, impedindo (ou restabelecendo) seu acesso, e retorna ao passo P2 do fluxo principal.

### A3. Redefinir acesso do usuário

> Ponto de entrada: passo P4 do fluxo principal.

#### A3.1. Solicitar a redefinição

O ator aciona a opção "Redefinir acesso".

#### A3.2. Enviar instruções

O sistema envia ao e-mail do usuário as instruções de redefinição de credenciais e retorna ao passo P2 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Dados inválidos

> Ponto de entrada: passo P7 do fluxo principal.

#### E1.1. Informar as inconsistências

O sistema destaca os campos inválidos ou incoerentes (por exemplo, e-mail já cadastrado ou perfil Estudante sem turma).

#### E1.2. Retornar à edição

O sistema retorna ao passo P6 do fluxo principal.

### E2. Última conta de Equipe Técnica

> Ponto de entrada: passos P8 e A2.2 do fluxo.

#### E2.1. Bloquear a operação

Caso a alteração ou inativação resulte na ausência de usuários ativos com perfil Equipe Técnica, o sistema bloqueia a operação e informa a restrição.

#### E2.2. Retornar à lista

O sistema retorna ao passo P2 do fluxo principal.

### E3. Dado gerenciado pela sincronização

> Ponto de entrada: passo P6 do fluxo principal.

#### E3.1. Informar a restrição

Caso o campo alterado seja mantido pela sincronização com a Unifor Online (UC16), o sistema informa que a alteração deve ser feita na origem ou será sobrescrita na próxima sincronização.

#### E3.2. Retornar à edição

O sistema retorna ao passo P6 do fluxo principal.

### E4. Usuário não encontrado

> Ponto de entrada: passo P3 do fluxo principal.

#### E4.1. Informar a ausência de resultados

O sistema exibe a mensagem "Nenhum usuário encontrado" e retorna ao passo P3 do fluxo principal.

### E5. Falha ao salvar

> Ponto de entrada: passo P8 do fluxo principal.

#### E5.1. Informar erro

O sistema exibe mensagem informando a falha, preserva os dados e orienta tentar novamente.

#### E5.2. Retornar à edição

O sistema retorna ao passo P6 do fluxo principal.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* As alterações de perfil, vínculos e situação ficam registradas e passam a valer no próximo acesso do usuário.
* Usuários inativados não conseguem autenticar-se, mas seu histórico é preservado.

## 10. Requisitos Não Funcionais

* **Segurança:** apenas a Equipe Técnica pode acessar esta funcionalidade, inclusive por acesso direto à API.
* **Rastreabilidade:** toda alteração de perfil, vínculo ou situação deve ser registrada em log, com autor, data e hora.
* **Privacidade:** os dados pessoais dos usuários devem ser tratados conforme a LGPD, com acesso restrito ao necessário.
* **Integridade:** a inativação não deve excluir fisicamente o usuário nem seus resultados.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa a média, com picos no início dos períodos letivos.

## 13. Interface Visual

### IV1. Tela de Lista de Usuários

Leiaute com busca, filtros, lista e ações. Referência: _a definir (ex.: `prototipos/IV1-lista-usuarios.png`)_.

### IV2. Tela de Edição de Usuário

Leiaute com dados cadastrais, perfil, vínculos e situação. Referência: _a definir (ex.: `prototipos/IV2-edicao-usuario.png`)_.

## 14. Observações

* O UC01 cobre o cadastro e a autenticação do próprio usuário; o UC14 cobre a gestão administrativa de contas e perfis.
* Definir a convivência entre usuários criados pela sincronização (UC16) e usuários criados manualmente.
* Definir se um usuário poderá acumular mais de um perfil (por exemplo, Professor e Coordenação).

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-13 – Administração de usuários e cadastros de apoio.
* UC01 – Cadastrar e autenticar usuário (F-06).
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
