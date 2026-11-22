# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição | Autor |
| ---------- | ------ | --------- | ----- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC06 a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |           |       |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC06 – Comparar com a média da turma (anônima)

## 2. Objetivo

Permitir que o estudante compare seu desempenho com a média agregada de sua turma, sem identificar os demais estudantes.

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Estudante.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O estudante está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O estudante está consultando suas estatísticas de desempenho (UC05 – Consultar estatísticas do próprio desempenho).
* O estudante está vinculado a ao menos uma turma.

## 6. Fluxo Principal

> Cenário: o estudante compara seu desempenho geral e por área com a média da sua turma.

### P1. Solicitar a comparação

O ator aciona a opção "Comparar com a média da turma" no painel de desempenho.

### P2. Verificar a turma e o anonimato

O sistema identifica a turma do estudante e verifica se ela possui o número mínimo de participantes definido na regra de negócio para garantir o anonimato.

### P3. Calcular as médias

O sistema calcula, de forma agregada, o percentual médio de acertos da turma, geral e por área.

### P4. Exibir o comparativo

O sistema exibe lado a lado o desempenho do estudante e a média da turma, geral e por área, sem apresentar nomes ou dados individuais de outros estudantes.

### P5. Refinar a comparação

O ator seleciona um período e/ou uma área para refinar o comparativo.

### P6. Atualizar o comparativo

O sistema recalcula e exibe o comparativo conforme os filtros selecionados.

### P7. Retornar ao painel

O ator aciona a opção "Voltar" e o sistema retorna ao painel de desempenho (UC05).

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Selecionar turma quando houver mais de uma

> Ponto de entrada: passo P2 do fluxo principal. Retorna ao passo P3.

#### A1.1. Exibir as turmas

O sistema exibe a lista de turmas às quais o estudante está vinculado.

#### A1.2. Selecionar a turma

O ator seleciona a turma desejada e o sistema retorna ao passo P3.

### A2. Comparar um simulado específico

> Ponto de entrada: passo P4 do fluxo principal. Retorna ao passo P4.

#### A2.1. Selecionar o simulado

O ator seleciona um simulado realizado também pela turma.

#### A2.2. Exibir o comparativo do simulado

O sistema exibe o resultado do estudante e a média da turma no simulado selecionado e retorna ao passo P4.

## 8. Fluxos de Exceção

### E1. Dados insuficientes para garantir o anonimato

> Ponto de entrada: passo P2 do fluxo principal.

#### E1.1. Informar a restrição

O sistema exibe a mensagem informando que a turma não possui participantes suficientes para a comparação.

#### E1.2. Retornar ao painel

O sistema retorna ao painel de desempenho (UC05), encerrando o caso de uso.

### E2. Estudante sem turma vinculada

> Ponto de entrada: passo P2 do fluxo principal.

#### E2.1. Informar a ausência de turma

O sistema exibe a mensagem informando que o estudante não está vinculado a nenhuma turma.

#### E2.2. Retornar ao painel

O sistema retorna ao painel de desempenho (UC05), encerrando o caso de uso.

### E3. Falha no cálculo da média

> Pontos de entrada: passos P3 e P6 do fluxo principal.

#### E3.1. Informar erro

O sistema exibe mensagem informando indisponibilidade temporária da comparação e orienta tentar novamente.

#### E3.2. Encerrar caso de uso

O caso de uso é encerrado.

### E4. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E4.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Nenhum dado do sistema é alterado por este caso de uso (consulta somente leitura).
* Nenhuma informação que identifique outros estudantes é exibida ou registrada para o ator.

## 10. Requisitos Não Funcionais

* **Privacidade:** os dados da turma devem ser exibidos apenas de forma agregada, em conformidade com a LGPD.
* **Desempenho:** o comparativo deve ser exibido em até 3 segundos em condições normais de uso.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Média.

## 13. Interface Visual

### IV1. Tela de Comparação com a Turma

Leiaute com gráfico comparativo entre o estudante e a média da turma, filtros de período e área. Referência: _a definir (ex.: `prototipos/UC06-IV1.png`)_.

## 14. Observações

* No diagrama, o UC06 estende o UC05 («extend»), sendo o ponto de extensão PE1 registrado no UC05.
* O diagrama não apresenta código de funcionalidade (F-xx) para este caso de uso; confirmar na Visão da Demanda.
* Definir o número mínimo de participantes da turma para exibir a média.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC05 – Consultar estatísticas do próprio desempenho (F-04).

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
