# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                 | Autor         |
| ---------- | ------ | ------------------------------------------------------------------------- | ------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC02 a partir do documento de visão e do diagrama de casos de uso do AdE (F-01). | Ian Carvalho Cirino |
|            |        |                                                                           |               |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC02 – Consultar banco de questões

## 2. Objetivo

Permitir que o usuário pesquise, filtre e visualize as questões cadastradas no banco de questões do AdE – Amigo do Estudante, para estudo individual ou para apoiar a montagem de simulados (F-01).

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
* Existem questões ativas cadastradas no banco de questões.

## 6. Fluxo Principal

> Cenário: usuário pesquisa questões aplicando filtros e visualiza uma questão.

### P1. Acessar o banco de questões

O ator seleciona a opção "Banco de questões" no menu do sistema.

### P2. Exibir a tela de consulta

O sistema exibe a tela de consulta com os filtros disponíveis e a listagem paginada das questões ativas, da mais recente para a mais antiga.

### P3. Informar critérios de busca

O ator informa um ou mais critérios de busca e aciona a opção "Pesquisar".

#### P3.1. Filtrar por curso e área

O ator seleciona o curso e/ou a área de conhecimento, conforme os cadastros de apoio (UC15).

#### P3.2. Filtrar por demais atributos

O ator informa, opcionalmente, o ano ou a prova de origem, o tema, o nível de dificuldade e/ou uma palavra-chave presente no enunciado.

### P4. Listar resultados

O sistema consulta as questões ativas que atendem aos critérios e exibe a listagem paginada com o código, um resumo do enunciado, o curso, a área e o ano de cada questão, além do total de resultados encontrados.

### P5. Selecionar uma questão

O ator seleciona uma questão da listagem.

### P6. Exibir a questão

O sistema exibe o enunciado completo, as alternativas e os metadados da questão.

### P7. Encerrar a consulta

O ator retorna à listagem ou encerra a consulta.

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Limpar filtros

> Ponto de entrada: passo P4 do fluxo principal.

#### A1.1. Solicitar limpeza dos filtros

O ator aciona a opção "Limpar filtros".

#### A1.2. Restaurar listagem padrão

O sistema remove os critérios aplicados e retorna ao passo P2 do fluxo principal.

### A2. Ordenar resultados

> Ponto de entrada: passo P4 do fluxo principal.

#### A2.1. Selecionar ordenação

O ator seleciona o critério de ordenação (data, dificuldade ou código).

#### A2.2. Reordenar listagem

O sistema reordena a listagem e retorna ao passo P4 do fluxo principal.

### A3. Consultar gabarito comentado

> Ponto de entrada: passo P6 do fluxo principal.

#### A3.1. Solicitar gabarito

O ator aciona a opção "Ver gabarito comentado".

#### A3.2. Direcionar para o gabarito

O sistema direciona o ator ao caso de uso UC04 – Consultar gabarito comentado, e, ao concluir, retorna ao passo P6 do fluxo principal.

### A4. Selecionar questões para simulado

> Ponto de entrada: passo P4 do fluxo principal. Aplicável somente quando o caso de uso é utilizado pelo UC12 – Criar e gerenciar simulados.

#### A4.1. Marcar questões

O ator marca uma ou mais questões da listagem.

#### A4.2. Devolver seleção

O sistema devolve as questões marcadas ao UC12 e encerra o caso de uso.

## 8. Fluxos de Exceção

### E1. Nenhuma questão encontrada

> Ponto de entrada: passo P4 do fluxo principal.

#### E1.1. Informar ausência de resultados

O sistema exibe a mensagem "Nenhuma questão encontrada para os critérios informados" e sugere ampliar ou limpar os filtros.

#### E1.2. Retornar à tela de consulta

O sistema retorna ao passo P3 do fluxo principal.

### E2. Critérios de busca inválidos

> Ponto de entrada: passo P3 do fluxo principal.

#### E2.1. Informar inconsistência

O sistema destaca o critério inválido (por exemplo, intervalo de anos incoerente) e exibe mensagem orientando a correção.

#### E2.2. Retornar aos critérios

O sistema retorna ao passo P3 do fluxo principal.

### E3. Questão indisponível

> Ponto de entrada: passo P6 do fluxo principal.

#### E3.1. Informar indisponibilidade

Caso a questão tenha sido inativada ou removida após a listagem (UC10), o sistema exibe a mensagem "Questão indisponível".

#### E3.2. Retornar à listagem

O sistema retorna ao passo P4 do fluxo principal com a listagem atualizada.

### E4. Falha na consulta

> Pontos de entrada: passos P4 e P6 do fluxo principal.

#### E4.1. Informar erro

O sistema exibe mensagem informando indisponibilidade temporária da consulta e orienta tentar novamente.

#### E4.2. Encerrar caso de uso

O caso de uso é encerrado.

### E5. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal.

#### E5.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* Nenhum dado do sistema é alterado por este caso de uso (consulta somente leitura).
* A questão selecionada é exibida ao usuário, ou, no fluxo A4, as questões marcadas são devolvidas ao caso de uso chamador.

## 10. Requisitos Não Funcionais

* **Desempenho:** a listagem deve ser exibida em até 3 segundos para consultas com até 10.000 questões cadastradas.
* **Usabilidade:** a tela deve ser responsiva e utilizável em dispositivos móveis.
* **Usabilidade:** a listagem deve ser paginada (por exemplo, 20 questões por página).
* **Segurança:** o gabarito e as informações restritas ao perfil Professor não devem ser expostos na listagem pública do Estudante, conforme as regras do UC04.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Alta. É uma das funcionalidades centrais do estudante; as informações mais acessadas são as questões filtradas por curso, área e tema.

## 13. Interface Visual

### IV1. Tela de Consulta ao Banco de Questões

Leiaute com painel de filtros, listagem paginada de resultados e opções de ordenação. Referência: _a definir (ex.: `prototipos/IV1-consulta-questoes.png`)_.

### IV2. Tela de Visualização da Questão

Leiaute com enunciado, alternativas, metadados e o botão "Ver gabarito comentado". Referência: _a definir (ex.: `prototipos/IV2-visualizacao-questao.png`)_.

## 14. Observações

* No diagrama, o UC02 é incluído pelo UC12 («include»), o que fundamenta o fluxo alternativo A4; por isso o Professor foi listado como ator primário.
* O Estudante é o ator que se liga diretamente ao UC02 no diagrama; confirmar se Coordenação e Equipe Técnica também devem consultar o banco.
* Os filtros por tema, competência e grade curricular dependem da classificação prevista no UC18 (evolução futura); inicialmente o tema é considerado atributo simples da questão.
* A importação de questões de provas do INEP (UC17) é evolução futura e não faz parte deste caso de uso.
* Definir se o Estudante visualiza o gabarito diretamente ou somente após responder à questão.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Funcionalidade F-01 – Banco de questões.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC04 – Consultar gabarito comentado (F-03).
* UC10 – Cadastrar, editar e inativar questões (F-09).
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
