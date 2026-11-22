# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição | Autor |
| ---------- | ------ | --------- | ----- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC05 (F-04) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |           |       |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC05 – Consultar estatísticas do próprio desempenho

## 2. Objetivo

Permitir que o estudante visualize indicadores do seu desempenho nos simulados realizados, para acompanhar sua evolução e identificar áreas que precisam de reforço (F-04).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Estudante.

### 4.2 Secundário

* Não se aplica.

## 5. Precondições

* O estudante está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O estudante possui ao menos uma tentativa de simulado finalizada (UC03 – Realizar simulado cronometrado).

## 6. Fluxo Principal

> Cenário: o estudante consulta o painel geral de desempenho e refina os indicadores por período e área.

### P1. Acessar o painel de desempenho

O ator seleciona a opção "Meu desempenho" no menu do sistema.

### P2. Consultar os dados

O sistema consulta as tentativas finalizadas do estudante.

### P3. Exibir o painel geral

O sistema exibe o total de simulados realizados, o percentual geral de acertos, o tempo médio por simulado e a evolução do desempenho ao longo do tempo.

### P4. Exibir desempenho por área

O sistema exibe o percentual de acertos por área e por tema, destacando os pontos fortes e os pontos a melhorar.

### P5. Refinar os indicadores

O ator seleciona um período (últimos 30 dias, semestre ou todo o histórico) e/ou uma área para detalhar.

### P6. Atualizar os indicadores

O sistema recalcula e exibe os indicadores conforme os filtros selecionados.

### P7. Encerrar a consulta

O ator deixa a tela de desempenho.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Detalhar um simulado do histórico

> Ponto de entrada: passo P3 do fluxo principal. Retorna ao passo P3.

#### A1.1. Selecionar o simulado

O ator seleciona um simulado na lista de histórico.

#### A1.2. Exibir o detalhamento

O sistema exibe a nota, a quantidade de acertos, erros e questões em branco, o tempo utilizado e a opção "Ver gabarito comentado" (UC04). Em seguida, retorna ao passo P3.

### A2. Comparar com a média da turma

> Ponto de entrada: passo P3 do fluxo principal (ponto de extensão PE1). Retorna ao passo P3.

#### A2.1. Solicitar a comparação

O ator aciona a opção "Comparar com a média da turma".

#### A2.2. Direcionar para a comparação

O sistema direciona o ator ao UC06 – Comparar com a média da turma (anônima) e, ao concluir, retorna ao passo P3.

## 8. Fluxos de Exceção

### E1. Nenhum simulado finalizado

> Ponto de entrada: passo P2 do fluxo principal.

#### E1.1. Informar ausência de dados

O sistema exibe a mensagem "Você ainda não realizou simulados" e a opção de acessar os simulados disponíveis (UC03).

#### E1.2. Encerrar caso de uso

O caso de uso é encerrado.

### E2. Falha no cálculo dos indicadores

> Pontos de entrada: passos P2 e P6 do fluxo principal.

#### E2.1. Informar erro

O sistema exibe mensagem informando indisponibilidade temporária das estatísticas e orienta tentar novamente.

#### E2.2. Encerrar caso de uso

O caso de uso é encerrado.

### E3. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E3.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Nenhum dado do sistema é alterado por este caso de uso (consulta somente leitura).

## 10. Requisitos Não Funcionais

* **Desempenho:** o painel deve ser exibido em até 3 segundos em condições normais de uso.
* **Privacidade:** as estatísticas individuais devem ser visíveis somente ao próprio estudante e aos perfis autorizados no UC09.
* **Usabilidade:** gráficos devem possuir alternativa textual (tabela ou rótulos) para acessibilidade e ser responsivos para dispositivos móveis.

## 11. Ponto de Extensão

### PE1. Comparar com a média da turma

O caso de uso UC06 – Comparar com a média da turma (anônima) estende («extend») este caso de uso, a partir do passo P3, quando o estudante solicita a comparação.

## 12. Frequência de Utilização

Média. As informações mais acessadas são o percentual geral de acertos e o desempenho por área.

## 13. Interface Visual

### IV1. Painel de Desempenho

Leiaute com indicadores gerais, gráfico de evolução, desempenho por área e filtros de período. Referência: _a definir (ex.: `prototipos/UC05-IV1.png`)_.

### IV2. Detalhamento do Simulado

Leiaute com o resumo da tentativa e acesso ao gabarito comentado. Referência: _a definir (ex.: `prototipos/UC05-IV2.png`)_.

## 14. Observações

* No diagrama, o UC06 estende o UC05 («extend»); o ponto de extensão está registrado na seção 11.
* Definir a lista final de indicadores e o período padrão de exibição.
* Avaliar o impacto da classificação por tema e competência (UC18, evolução futura) no detalhamento por área.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-04.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC03 – Realizar simulado cronometrado (F-02).
* UC04 – Consultar gabarito comentado (F-03).
* UC06 – Comparar com a média da turma (anônima).
* UC09 – Acompanhar desempenho de turmas e alunos (F-11).

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
