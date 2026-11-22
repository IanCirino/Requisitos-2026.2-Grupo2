# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                 | Autor         |
| ---------- | ------ | ------------------------------------------------------------------------- | ------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC03 a partir do documento de visão e do diagrama de casos de uso do AdE(F-02). | Ian Carvalho Cirino |
|            |        |                                                                           |               |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC03 – Realizar simulado cronometrado

## 2. Objetivo

Permitir que o estudante responda a um simulado dentro de um tempo limite previamente definido, registrando suas respostas e o resultado da tentativa (F-02).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Estudante.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O estudante está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* Existe ao menos um simulado publicado e disponível para o estudante (UC13 – Publicar simulado para turmas).
* O estudante ainda possui tentativas disponíveis para o simulado, conforme a configuração definida no UC12.

## 6. Fluxo Principal

> Cenário: o estudante realiza o simulado até o fim, dentro do tempo, e visualiza o resultado.

### P1. Acessar os simulados disponíveis

O ator seleciona a opção "Simulados" no menu do sistema.

### P2. Listar simulados

O sistema exibe a lista de simulados disponíveis para o estudante, com título, quantidade de questões, tempo limite e período de disponibilidade.

### P3. Selecionar um simulado

O ator seleciona um simulado da lista.

### P4. Exibir instruções

O sistema exibe as instruções do simulado (quantidade de questões, tempo limite, regras de navegação e de finalização) e a opção "Iniciar simulado".

### P5. Iniciar o simulado

O ator aciona a opção "Iniciar simulado".

### P6. Iniciar o cronômetro

O sistema registra o horário de início da tentativa, inicia o cronômetro regressivo e exibe a primeira questão.

### P7. Responder às questões

O ator responde às questões do simulado.

#### P7.1. Selecionar a alternativa

O ator seleciona a alternativa de cada questão.

#### P7.2. Registrar a resposta

O sistema registra a resposta de forma automática a cada seleção.

#### P7.3. Navegar entre questões

O ator navega entre as questões, podendo alterar respostas e marcar questões para revisão. O sistema exibe o progresso e o tempo restante em todas as telas.

### P8. Finalizar o simulado

O ator aciona a opção "Finalizar simulado".

### P9. Solicitar confirmação

O sistema exibe a quantidade de questões respondidas e em branco e solicita a confirmação da finalização.

### P10. Confirmar a finalização

O ator confirma a finalização.

### P11. Encerrar a tentativa

O sistema interrompe o cronômetro, registra o horário de término, calcula o resultado e armazena a tentativa.

### P12. Exibir o resultado

O sistema exibe o resultado da tentativa com a quantidade de acertos, erros e questões em branco, o percentual de acertos e o tempo utilizado, além da opção de consultar o gabarito comentado (ponto de extensão PE1).

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Finalizar por esgotamento do tempo

> Ponto de entrada: passo P7 do fluxo principal. Retorna ao passo P11.

#### A1.1. Esgotar o tempo

O cronômetro do sistema chega a zero.

#### A1.2. Encerrar automaticamente

O sistema bloqueia novas respostas, considera as respostas já registradas e informa que o tempo foi esgotado.

#### A1.3. Prosseguir para o encerramento

O sistema segue para o passo P11 do fluxo principal.

### A2. Voltar para revisar questões

> Ponto de entrada: passo P9 do fluxo principal. Retorna ao passo P7.

#### A2.1. Optar por continuar

O ator aciona a opção "Voltar ao simulado" na tela de confirmação.

#### A2.2. Retornar às questões

O sistema retorna ao passo P7 do fluxo principal, mantendo o cronômetro em andamento.

### A3. Retomar tentativa em andamento

> Ponto de entrada: passo P3 do fluxo principal. Retorna ao passo P7.

#### A3.1. Identificar tentativa em andamento

O sistema identifica que o estudante possui uma tentativa não finalizada e ainda dentro do tempo para o simulado selecionado.

#### A3.2. Oferecer a retomada

O sistema exibe a opção "Continuar simulado".

#### A3.3. Retomar a tentativa

O ator aciona a opção, e o sistema restaura as respostas já registradas, atualiza o tempo restante e retorna ao passo P7 do fluxo principal.

### A4. Consultar gabarito comentado

> Ponto de entrada: passo P12 do fluxo principal (ponto de extensão PE1).

#### A4.1. Solicitar o gabarito

O ator aciona a opção "Ver gabarito comentado".

#### A4.2. Direcionar para o gabarito

O sistema direciona o ator ao caso de uso UC04 – Consultar gabarito comentado e, ao concluir, retorna ao passo P12.

## 8. Fluxos de Exceção

### E1. Simulado indisponível

> Ponto de entrada: passo P5 do fluxo principal.

#### E1.1. Informar indisponibilidade

O sistema exibe a mensagem informando que o simulado está fora do período de disponibilidade ou foi despublicado.

#### E1.2. Retornar à listagem

O sistema retorna ao passo P2 do fluxo principal.

### E2. Limite de tentativas atingido

> Ponto de entrada: passo P5 do fluxo principal.

#### E2.1. Informar o limite

O sistema exibe a mensagem informando que o limite de tentativas para o simulado foi atingido.

#### E2.2. Retornar à listagem

O sistema retorna ao passo P2 do fluxo principal.

### E3. Perda de conexão durante o simulado

> Ponto de entrada: passo P7 do fluxo principal.

#### E3.1. Informar a falha

O sistema, ao detectar a perda de conexão, exibe aviso de que as respostas não estão sendo salvas e mantém as respostas já registradas localmente.

#### E3.2. Sincronizar as respostas

Ao restabelecer a conexão, o sistema sincroniza as respostas e retorna ao passo P7 do fluxo principal. O cronômetro é controlado pelo servidor e continua em andamento durante a falha.

#### E3.3. Encerrar por tempo esgotado

Se o tempo se esgotar durante a falha, o sistema segue o fluxo alternativo A1 após restabelecida a conexão.

### E4. Falha ao registrar o resultado

> Ponto de entrada: passo P11 do fluxo principal.

#### E4.1. Informar o erro

O sistema exibe a mensagem informando falha ao registrar a tentativa e preserva as respostas para nova tentativa de gravação.

#### E4.2. Tentar novamente

O ator aciona a opção "Tentar novamente" e o sistema retorna ao passo P11 do fluxo principal.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário. Após a autenticação, o sistema aplica o fluxo alternativo A3 caso a tentativa ainda esteja em andamento.

## 9. Pós-condições

* A tentativa do estudante está registrada, com as respostas, o resultado, o tempo utilizado e os horários de início e término.
* O número de tentativas utilizadas do simulado pelo estudante está atualizado.
* O resultado está disponível para as estatísticas de desempenho (UC05, UC06) e para o acompanhamento por turmas e alunos (UC09).

## 10. Requisitos Não Funcionais

* **Integridade:** o controle do tempo deve ser realizado pelo servidor, evitando manipulação do cronômetro pelo cliente.
* **Confiabilidade:** as respostas devem ser salvas automaticamente a cada interação, para evitar perda de dados em caso de falha.
* **Desempenho:** a troca entre questões deve ocorrer em até 1 segundo em condições normais de uso.
* **Usabilidade:** a tela de realização deve ser responsiva e utilizável em dispositivos móveis, com o tempo restante sempre visível.
* **Disponibilidade:** o sistema deve suportar a realização simultânea do simulado por toda a turma no mesmo horário.

## 11. Ponto de Extensão

### PE1. Consultar gabarito comentado

Após a exibição do resultado (passo P12), o caso de uso UC04 – Consultar gabarito comentado estende este caso de uso («extend»), permitindo ao estudante revisar a resolução comentada das questões do simulado realizado.

## 12. Frequência de Utilização

Média a alta, com picos próximos a datas de avaliações e de provas. As informações mais acessadas são o simulado disponível e o resultado da tentativa.

## 13. Interface Visual

### IV1. Tela de Listagem de Simulados

Leiaute com a lista de simulados disponíveis, tempo limite e status. Referência: _a definir (ex.: `prototipos/IV1-lista-simulados.png`)_.

### IV2. Tela de Realização do Simulado

Leiaute com a questão atual, alternativas, cronômetro regressivo, mapa de navegação entre questões e botão "Finalizar simulado". Referência: _a definir (ex.: `prototipos/IV2-realizacao-simulado.png`)_.

### IV3. Tela de Resultado

Leiaute com o resumo da tentativa e a opção "Ver gabarito comentado". Referência: _a definir (ex.: `prototipos/IV3-resultado-simulado.png`)_.

## 14. Observações

* No diagrama, o UC04 estende o UC03 («extend»), o que fundamenta o ponto de extensão PE1.
* O diagrama não indica se o estudante pode montar o próprio simulado a partir do banco de questões (UC02) ou se realiza apenas simulados publicados pelo Professor (UC12 e UC13). Este documento considera apenas simulados publicados; validar com o cliente.
* Definir se, após finalizar, o estudante pode refazer o simulado e se o gabarito fica disponível imediatamente ou somente após o encerramento do período de disponibilidade.
* Definir o comportamento ao fechar o navegador: o cronômetro segue em andamento (adotado neste documento) ou é pausado.
* Os valores de desempenho e o número de tentativas devem ser confirmados na Especificação de RNF.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Funcionalidade F-02 – Simulado cronometrado.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC04 – Consultar gabarito comentado (F-03).
* UC05 – Consultar estatísticas do próprio desempenho (F-04).
* UC06 – Comparar com a média da turma (anônima).
* UC09 – Acompanhar desempenho de turmas e alunos (F-11).
* UC12 – Criar e gerenciar simulados (F-10).
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
