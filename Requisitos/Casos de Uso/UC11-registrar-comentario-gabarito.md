# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC11 a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC11 – Registrar comentário do gabarito

## 2. Objetivo

Permitir que o Professor registre ou atualize o comentário explicativo da alternativa correta de uma questão, que será exibido aos estudantes na consulta do gabarito comentado.

## 3. Tipo de Caso de Uso

Concreto (incluído pelo UC10 e acionável a partir do UC04).

## 4. Atores

### 4.1 Primário

* Professor.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O Professor está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* A questão está ativa e possui alternativa correta definida.

## 6. Fluxo Principal

> Cenário: o Professor registra o comentário de uma questão durante o seu cadastro (UC10).

### P1. Exibir o editor de comentário

O sistema exibe o editor de comentário associado à questão, com o enunciado e a alternativa correta para referência.

### P2. Informar o comentário

O Professor redige o comentário explicativo, podendo aplicar formatação básica e incluir referências.

### P3. Validar o comentário

O sistema valida se o comentário foi preenchido e se respeita o tamanho máximo permitido.

### P4. Salvar o comentário

O Professor confirma, e o sistema salva o comentário com identificação do autor e da data da última atualização.

### P5. Confirmar o registro

O sistema exibe a mensagem de sucesso e retorna ao caso de uso de origem.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Editar comentário existente

> Ponto de entrada: passo P1 do fluxo principal.

#### A1.1. Exibir o comentário atual

O sistema exibe o editor com o comentário já registrado.

#### A1.2. Alterar o comentário

O Professor altera o texto e segue para o passo P3 do fluxo principal.

### A2. Acionar a partir do gabarito comentado

> Ponto de entrada: passo P1 do fluxo principal.

#### A2.1. Acionar a edição

O Professor, ao consultar o gabarito (UC04, fluxo A3), aciona a opção "Editar comentário".

#### A2.2. Prosseguir com a edição

O sistema segue para o passo A1.1 do fluxo alternativo A1 ou, se não houver comentário, para o passo P1 do fluxo principal. Ao final, retorna ao UC04.

### A3. Remover comentário

> Ponto de entrada: passo P1 do fluxo principal (comentário existente).

#### A3.1. Solicitar a remoção

O Professor aciona a opção "Remover comentário" e o sistema solicita confirmação.

#### A3.2. Remover o comentário

O Professor confirma, e o sistema remove o comentário, passando a questão a exibir a mensagem "Esta questão ainda não possui comentário" (UC04, fluxo E2).

## 8. Fluxos de Exceção

### E1. Comentário inválido

> Ponto de entrada: passo P3 do fluxo principal.

#### E1.1. Informar a inconsistência

O sistema informa que o comentário está vazio ou excede o tamanho máximo permitido.

#### E1.2. Retornar à edição

O sistema retorna ao passo P2 do fluxo principal.

### E2. Questão inativa

> Ponto de entrada: passo P1 do fluxo principal.

#### E2.1. Informar a restrição

O sistema informa que não é possível alterar o comentário de uma questão inativa.

#### E2.2. Encerrar caso de uso

O caso de uso é encerrado.

### E3. Falha ao salvar

> Ponto de entrada: passo P4 do fluxo principal.

#### E3.1. Informar erro

O sistema exibe mensagem informando a falha, preserva o texto digitado e orienta tentar novamente.

#### E3.2. Retornar à edição

O sistema retorna ao passo P4 do fluxo principal.

### E4. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E4.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* O comentário fica associado à questão, com autor e data da última atualização.
* O comentário atualizado passa a ser exibido no UC04 – Consultar gabarito comentado.

## 10. Requisitos Não Funcionais

* **Segurança:** apenas usuários com perfil Professor podem registrar ou alterar comentários, inclusive por acesso direto à API.
* **Rastreabilidade:** as alterações devem ser registradas em log, com autor, data e hora.
* **Usabilidade:** o editor deve oferecer pré-visualização do comentário como será exibido ao estudante.

## 11. Ponto de Extensão

Não se aplica. Este caso de uso é incluído pelo UC10 – Cadastrar, editar e inativar questões («include»).

## 12. Frequência de Utilização

Média, acompanhando o cadastro e a revisão de questões.

## 13. Interface Visual

### IV1. Tela de Edição de Comentário

Leiaute com enunciado, alternativa correta, editor de texto e pré-visualização. Referência: _a definir (ex.: `prototipos/IV1-editar-comentario.png`)_.

## 14. Observações

* No diagrama, o UC11 é incluído pelo UC10 e está associado ao Professor.
* Definir se o Professor pode editar comentários registrados por outro professor e se haverá histórico de versões do comentário.
* Definir se o comentário poderá conter imagens, fórmulas ou links externos.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-03 – Gabarito comentado.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC04 – Consultar gabarito comentado (F-03).
* UC10 – Cadastrar, editar e inativar questões (F-09).

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
