# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição | Autor |
| ---------- | ------ | --------- | ----- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC07 (F-05) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |           |       |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC07 – Participar do fórum de discussão

## 2. Objetivo

Permitir que os usuários criem tópicos, leiam e respondam discussões no fórum, promovendo a troca de conhecimento sobre questões e conteúdos (F-05).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Estudante.
* Professor.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O usuário está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O usuário não está suspenso do fórum.

## 6. Fluxo Principal

> Cenário: o usuário acessa um tópico existente e publica uma resposta.

### P1. Acessar o fórum

O ator seleciona a opção "Fórum" no menu do sistema.

### P2. Exibir os tópicos

O sistema exibe a lista paginada de tópicos, com título, autor, data da última atividade e quantidade de respostas.

### P3. Selecionar um tópico

O ator seleciona um tópico da lista.

### P4. Exibir o tópico

O sistema exibe o conteúdo do tópico, a questão vinculada (quando houver) e as respostas em ordem cronológica.

### P5. Redigir a resposta

O ator redige o texto da resposta e aciona a opção "Publicar".

### P6. Validar o conteúdo

O sistema valida se o texto não está vazio, respeita o tamanho máximo e não contém termos proibidos.

### P7. Registrar a resposta

O sistema registra a resposta, a exibe no tópico e notifica o autor do tópico.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Criar novo tópico

> Ponto de entrada: passo P2 do fluxo principal. Retorna ao passo P2.

#### A1.1. Solicitar novo tópico

O ator aciona a opção "Novo tópico".

#### A1.2. Exibir o formulário

O sistema exibe o formulário com título, categoria, texto e questão vinculada (opcional).

#### A1.3. Preencher e publicar

O ator preenche os dados e aciona a opção "Publicar".

#### A1.4. Registrar o tópico

O sistema valida os dados, registra o tópico e retorna ao passo P2.

### A2. Pesquisar tópicos

> Ponto de entrada: passo P2 do fluxo principal. Retorna ao passo P2.

#### A2.1. Informar o termo

O ator informa um termo de busca e/ou filtros de categoria.

#### A2.2. Filtrar a lista

O sistema atualiza a lista de tópicos e retorna ao passo P2.

### A3. Denunciar conteúdo

> Ponto de entrada: passo P4 do fluxo principal. Retorna ao passo P4.

#### A3.1. Solicitar a denúncia

O ator aciona a opção "Denunciar" em um tópico ou resposta e informa o motivo.

#### A3.2. Registrar a denúncia

O sistema registra a denúncia, a encaminha à fila de moderação (UC08) e retorna ao passo P4.

## 8. Fluxos de Exceção

### E1. Conteúdo inválido

> Pontos de entrada: passo P6 do fluxo principal e passo A1.4 do fluxo alternativo A1.

#### E1.1. Informar a inconsistência

O sistema exibe mensagem indicando o problema (texto vazio, tamanho excedido ou termos proibidos).

#### E1.2. Retornar ao passo de origem

O sistema retorna ao passo P5 (fluxo principal) ou ao passo A1.3 (fluxo A1).

### E2. Tópico fechado ou removido

> Pontos de entrada: passos P3 e P5 do fluxo principal.

#### E2.1. Informar a indisponibilidade

O sistema exibe a mensagem informando que o tópico está fechado ou foi removido.

#### E2.2. Retornar à lista

O sistema retorna ao passo P2 do fluxo principal.

### E3. Usuário suspenso do fórum

> Ponto de entrada: passo P1 do fluxo principal.

#### E3.1. Informar a suspensão

O sistema permite apenas a leitura e exibe a mensagem informando que o usuário está suspenso de publicar.

#### E3.2. Encerrar publicação

O sistema oculta as opções de publicação e o fluxo segue apenas com consulta.

### E4. Falha ao publicar

> Ponto de entrada: passo P7 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando falha ao publicar e preserva o texto digitado.

#### E4.2. Retornar à resposta

O sistema retorna ao passo P5 do fluxo principal.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* A resposta ou o tópico está registrado e visível aos demais usuários.
* O autor do tópico foi notificado da nova resposta.
* Denúncias registradas estão disponíveis para a moderação (UC08).

## 10. Requisitos Não Funcionais

* **Segurança:** o conteúdo publicado deve ser sanitizado para impedir a injeção de código.
* **Desempenho:** a lista de tópicos deve ser exibida em até 3 segundos.
* **Usabilidade:** o fórum deve ser responsivo e utilizável em dispositivos móveis.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Média.

## 13. Interface Visual

### IV1. Lista de Tópicos

Leiaute com a lista de tópicos, busca, filtros e botão "Novo tópico". Referência: _a definir (ex.: `prototipos/UC07-IV1.png`)_.

### IV2. Tela do Tópico

Leiaute com o conteúdo do tópico, respostas e editor de resposta. Referência: _a definir (ex.: `prototipos/UC07-IV2.png`)_.

## 14. Observações

* O diagrama associa o UC07 aos atores Estudante e Professor; validar se a Equipe Técnica também participa do fórum além de moderar.
* Definir categorias de tópicos, regras de uso e lista de termos proibidos.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-05.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC02 – Consultar banco de questões (F-01).
* UC08 – Moderar fórum.

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
