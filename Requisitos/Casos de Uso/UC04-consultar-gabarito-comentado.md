# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                                                                              | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC04 (F-03) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente.             | Ian Carvalho Cirino |
|            |        |                                                                                                                                                        |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC04 – Consultar gabarito comentado

## 2. Objetivo

Permitir que o usuário visualize a alternativa correta de uma questão e o comentário explicativo associado, apoiando a compreensão da resolução e a revisão de erros (F-03).

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
* A questão a ser consultada está ativa e possui gabarito cadastrado.
* Quando acessado a partir de um simulado, o estudante já finalizou a tentativa correspondente (UC03 – Realizar simulado cronometrado).

## 6. Fluxo Principal

> Cenário: o estudante consulta o gabarito comentado das questões de um simulado que acabou de finalizar.

### P1. Solicitar o gabarito comentado

O ator aciona a opção "Ver gabarito comentado" na tela de resultado do simulado.

### P2. Verificar a disponibilidade

O sistema verifica se a tentativa está finalizada e se o gabarito está liberado para o ator.

### P3. Exibir a lista de questões

O sistema exibe a lista das questões do simulado, indicando para cada uma se o estudante acertou, errou ou deixou em branco.

### P4. Selecionar uma questão

O ator seleciona uma questão da lista.

### P5. Exibir o gabarito comentado

O sistema exibe o enunciado, as alternativas, a resposta marcada pelo estudante, a alternativa correta e o comentário explicativo da questão.

#### P5.1. Destacar o resultado

O sistema destaca visualmente a alternativa marcada e a alternativa correta.

#### P5.2. Exibir o comentário

O sistema exibe o comentário registrado pelo professor (UC11 – Registrar comentário do gabarito), com identificação do autor e da data da última atualização.

### P6. Navegar entre questões

O ator navega para a questão anterior ou seguinte, repetindo o passo P5, ou retorna à lista de questões.

### P7. Encerrar a consulta

O ator aciona a opção "Voltar ao resultado".

### P8. Retornar ao resultado

O sistema retorna à tela de resultado do simulado.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Consultar gabarito a partir do banco de questões

> Ponto de entrada: passo P3 do fluxo principal (substitui os passos P1 a P3).

#### A1.1. Acionar a partir da questão

O ator, ao visualizar uma questão no UC02 – Consultar banco de questões, aciona a opção "Ver gabarito comentado".

#### A1.2. Exibir o gabarito

O sistema exibe o enunciado, a alternativa correta e o comentário explicativo, sem indicação de resposta marcada, e segue para o passo P6 do fluxo principal.

### A2. Filtrar a lista por situação

> Ponto de entrada: passo P3 do fluxo principal.

#### A2.1. Selecionar o filtro

O ator filtra a lista de questões por situação (acertos, erros ou em branco).

#### A2.2. Atualizar a lista

O sistema atualiza a lista de questões e retorna ao passo P3 do fluxo principal.

### A3. Consultar gabarito como Professor

> Ponto de entrada: passo P2 do fluxo principal.

#### A3.1. Identificar o perfil

O sistema identifica que o ator possui o perfil Professor.

#### A3.2. Liberar o gabarito

O sistema libera o gabarito sem exigir tentativa finalizada e exibe a opção "Editar comentário", que direciona ao UC11 – Registrar comentário do gabarito.

#### A3.3. Prosseguir com a consulta

O sistema segue para o passo A1.2 do fluxo alternativo A1.

## 8. Fluxos de Exceção

### E1. Gabarito não liberado

> Ponto de entrada: passo P2 do fluxo principal.

#### E1.1. Informar a restrição

O sistema exibe a mensagem informando que o gabarito ainda não está disponível, por tentativa em andamento ou por restrição definida para o simulado.

#### E1.2. Retornar à tela de origem

O sistema retorna à tela de resultado do simulado, encerrando o caso de uso.

### E2. Questão sem comentário

> Ponto de entrada: passo P5 do fluxo principal.

#### E2.1. Informar a ausência de comentário

O sistema exibe a alternativa correta e a mensagem "Esta questão ainda não possui comentário".

#### E2.2. Prosseguir com a consulta

O sistema segue para o passo P6 do fluxo principal.

### E3. Questão indisponível

> Ponto de entrada: passo P4 do fluxo principal.

#### E3.1. Informar indisponibilidade

Caso a questão tenha sido inativada (UC10) após a realização do simulado, o sistema exibe a mensagem informando a indisponibilidade do conteúdo.

#### E3.2. Retornar à lista

O sistema retorna ao passo P3 do fluxo principal.

### E4. Falha na consulta

> Pontos de entrada: passos P3 e P5 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando indisponibilidade temporária da consulta e orienta tentar novamente.

#### E4.2. Encerrar caso de uso

O caso de uso é encerrado.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Nenhum dado do banco de questões é alterado por este caso de uso (consulta somente leitura).
* A consulta do estudante ao gabarito fica disponível para fins de acompanhamento, quando definido na Especificação de RNF.

## 10. Requisitos Não Funcionais

* **Desempenho:** o gabarito comentado deve ser exibido em até 3 segundos em condições normais de uso.
* **Usabilidade:** a alternativa marcada e a alternativa correta devem ser diferenciadas por mais de um recurso visual (por exemplo, ícone e cor), garantindo acessibilidade.
* **Usabilidade:** a tela deve ser responsiva e utilizável em dispositivos móveis.
* **Segurança:** o gabarito não deve ser acessível a estudantes antes da liberação definida para o simulado, inclusive por acesso direto à URL ou à API.

## 11. Ponto de Extensão

Não se aplica. Este caso de uso é o caso de uso estendido pelo ponto de extensão PE1 do UC03 – Realizar simulado cronometrado («extend»).

## 12. Frequência de Utilização

Alta, concentrada logo após a conclusão dos simulados. As informações mais acessadas são a alternativa correta e o comentário das questões erradas.

## 13. Interface Visual

### IV1. Tela de Lista de Questões do Gabarito

Leiaute com a lista de questões do simulado, indicador de acerto, erro ou branco e filtro por situação. Referência: _a definir (ex.: `prototipos/IV1-lista-gabarito.png`)_.

### IV2. Tela de Gabarito Comentado da Questão

Leiaute com enunciado, alternativas destacadas, comentário explicativo e navegação entre questões. Referência: _a definir (ex.: `prototipos/IV2-gabarito-comentado.png`)_.

## 14. Observações

* No diagrama, o UC04 estende o UC03 («extend»); o ponto de extensão está registrado no UC03 (PE1).
* O comentário exibido é registrado no UC11 – Registrar comentário do gabarito, executado pelo Professor.
* Este caso de uso foi elaborado a partir do diagrama de casos de uso e considerando a Visão da Demanda (VD) já existente; eventuais divergências devem ser tratadas na revisão com o cliente.
* Definir a regra de liberação do gabarito para o estudante: imediatamente após finalizar, somente após o encerramento do período do simulado ou conforme configuração do Professor.
* Avaliar se o estudante poderá sinalizar dúvidas ou feedback sobre o comentário (possível relação com o UC07 – Participar do fórum de discussão).

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-03 – Gabarito comentado.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC02 – Consultar banco de questões (F-01).
* UC03 – Realizar simulado cronometrado (F-02).
* UC10 – Cadastrar, editar e inativar questões (F-09).
* UC11 – Registrar comentário do gabarito.

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
