# Especificação de Requisitos Funcionais

## Caso de Uso (CDU)

## Histórico de Versões

<!-- markdownlint-disable MD060 -->
| Data       | Versão | Descrição                                                                                         | Autor               |
| ---------- | ------ | ------------------------------------------------------------------------------------------------- | ------------------- |
| 17/11/2026 | 1.0    | Criação do caso de uso UC17 (F-07) a partir do diagrama de casos de uso do AdE, considerando também a Visão da Demanda (VD) já existente. | Ian Carvalho Cirino |
|            |        |                                                                                                   |                     |
<!-- markdownlint-enable MD060 -->

## 1. Nome do Caso de Uso

UC17 – Importar provas em PDF do INEP

## 2. Objetivo

Permitir que o Professor e a Equipe Técnica importem provas em PDF do INEP (e seus gabaritos), extraindo as questões para o banco de questões do AdE, com revisão antes da confirmação (F-07).

## 3. Tipo de Caso de Uso

Concreto.

## 4. Atores

### 4.1 Primário

* Professor.
* Equipe Técnica.

### 4.2 Secundário

* INEP (sistema externo).

## 5. Precondições

* O ator está autenticado no sistema (UC01 – Cadastrar e autenticar usuário).
* O ator possui perfil Professor ou Equipe Técnica.
* O ator dispõe do arquivo PDF da prova (e, preferencialmente, do gabarito oficial) ou das informações da edição para obtê-los no INEP (fluxo A1).

## 6. Fluxo Principal

> Cenário: o ator envia o arquivo PDF da prova e do gabarito e confirma a importação das questões.

### P1. Acessar a importação

O ator aciona a opção "Importar provas do INEP".

### P2. Exibir a tela de importação

O sistema exibe o formulário de importação (ano, aplicação, área/caderno, arquivo da prova e arquivo do gabarito) e a lista das importações anteriores.

### P3. Informar os dados e os arquivos

O ator informa os dados da prova, anexa os arquivos PDF e aciona a opção "Importar".

### P4. Validar os arquivos

O sistema valida o formato (PDF), o tamanho e a legibilidade dos arquivos e verifica se a prova já foi importada.

### P5. Extrair as questões

O sistema extrai de cada questão o enunciado, os textos de apoio, as imagens e as alternativas.

### P6. Associar o gabarito

O sistema associa a alternativa correta do gabarito oficial a cada questão extraída.

### P7. Exibir a pré-visualização

O sistema exibe as questões extraídas com indicação das inconsistências encontradas (por exemplo, questão sem gabarito ou alternativas incompletas).

### P8. Revisar e confirmar

O ator revisa as questões, corrige as inconsistências e aciona a opção "Confirmar importação".

### P9. Registrar as questões

O sistema cadastra as questões no banco de questões (UC10) com situação "Pendente de classificação", preservando a origem (prova, ano, caderno e número da questão), e registra a importação em log, com data, hora, responsável e quantidade de questões importadas e rejeitadas.

### P10. Exibir o resumo

O sistema exibe o resumo da importação e disponibiliza o acesso à classificação das questões (UC18).

O caso de uso é encerrado.

## 7. Fluxos Alternativos

### A1. Obter a prova diretamente do INEP

> Ponto de entrada: passo P3 do fluxo principal (substitui o anexo dos arquivos).

#### A1.1. Informar a edição

O ator informa o ano, a aplicação e o caderno e aciona a opção "Obter do INEP".

#### A1.2. Solicitar os arquivos ao INEP

O sistema solicita ao INEP os arquivos da prova e do gabarito correspondentes.

#### A1.3. Enviar os arquivos

O INEP disponibiliza os arquivos solicitados ao sistema, que segue para o passo P4 do fluxo principal.

### A2. Importar prova sem gabarito

> Ponto de entrada: passo P3 do fluxo principal.

#### A2.1. Importar somente a prova

O ator anexa apenas o arquivo da prova e aciona a opção "Importar".

#### A2.2. Marcar as questões sem gabarito

O sistema segue para o passo P4 do fluxo principal e, no passo P6, marca as questões como "Sem gabarito" para preenchimento posterior pelo ator.

### A3. Consultar importações anteriores

> Ponto de entrada: passo P2 do fluxo principal.

#### A3.1. Acessar o histórico

O ator seleciona uma importação anterior na lista.

#### A3.2. Exibir os detalhes

O sistema exibe os detalhes da importação (arquivos, data, responsável e questões importadas) e retorna ao passo P2 do fluxo principal.

## 8. Fluxos de Exceção

### E1. Arquivo inválido

> Ponto de entrada: passo P4 do fluxo principal.

#### E1.1. Informar o problema

O sistema informa que o arquivo não é um PDF válido, está corrompido ou excede o tamanho permitido.

#### E1.2. Retornar à tela de importação

O sistema retorna ao passo P2 do fluxo principal.

### E2. Prova já importada

> Ponto de entrada: passo P4 do fluxo principal.

#### E2.1. Informar a duplicidade

O sistema informa que a prova já foi importada e exibe a data e o responsável pela importação anterior.

#### E2.2. Retornar à tela de importação

O sistema retorna ao passo P2 do fluxo principal.

### E3. Falha na extração do conteúdo

> Ponto de entrada: passo P5 do fluxo principal.

#### E3.1. Informar a falha

O sistema informa que não foi possível extrair as questões (por exemplo, PDF digitalizado sem texto reconhecível) e registra o motivo em log.

#### E3.2. Encerrar caso de uso

O sistema descarta o processamento e o caso de uso é encerrado.

### E4. INEP indisponível

> Pontos de entrada: passos A1.2 e A1.3 do fluxo alternativo A1.

#### E4.1. Informar a indisponibilidade

O sistema informa que o INEP não respondeu ou não localizou os arquivos e registra a falha em log.

#### E4.2. Retornar à tela de importação

O sistema orienta o ator a anexar os arquivos manualmente e retorna ao passo P2 do fluxo principal.

### E5. Falha ao registrar as questões

> Ponto de entrada: passo P9 do fluxo principal.

#### E5.1. Desfazer o registro parcial

O sistema desfaz o registro das questões da importação, preservando a consistência do banco de questões.

#### E5.2. Informar erro

O sistema exibe mensagem informando a falha e encerra o caso de uso.

### E6. Sessão expirada

> Ponto de entrada: qualquer passo do fluxo principal executado pelo ator.

#### E6.1. Redirecionar para autenticação

O sistema informa que a sessão expirou e direciona o ator ao UC01 – Cadastrar e autenticar usuário.

## 9. Pós-condições

* As questões da prova ficam cadastradas no banco de questões com a origem preservada e a situação "Pendente de classificação".
* O gabarito oficial fica associado às questões (ou as questões ficam marcadas como "Sem gabarito").
* A importação fica registrada em log e disponível no histórico.

## 10. Requisitos Não Funcionais

* **Desempenho:** a extração de uma prova completa deve ser concluída em tempo aceitável e sem degradar a disponibilidade para os demais usuários.
* **Confiabilidade:** a importação deve ser atômica por prova, sem gerar questões duplicadas em caso de falha ou nova tentativa.
* **Segurança:** os arquivos enviados devem ser validados quanto ao tipo e ao conteúdo antes do processamento, e a comunicação com o INEP deve ocorrer por canal criptografado.
* **Rastreabilidade:** cada importação deve registrar origem do arquivo, responsável, data e hora.
* **Usabilidade:** a pré-visualização deve permitir corrigir enunciados, alternativas e gabarito antes da confirmação.

## 11. Ponto de Extensão

Não se aplica.

## 12. Frequência de Utilização

Baixa; concentrada após a divulgação de novas provas pelo INEP.

## 13. Interface Visual

### IV1. Tela de Importação de Provas

Leiaute com formulário de dados da prova, campos de anexo (prova e gabarito), opção "Obter do INEP", botão "Importar" e lista de importações anteriores. Referência: _a definir (ex.: `prototipos/IV1-importacao-provas.png`)_.

### IV2. Tela de Pré-visualização das Questões

Leiaute com a lista de questões extraídas, indicação de inconsistências, edição de enunciado, alternativas e gabarito e botão "Confirmar importação". Referência: _a definir (ex.: `prototipos/IV2-previsualizacao-questoes.png`)_.

## 14. Observações

* O INEP é o ator secundário («sistema externo») e está associado ao UC17 no diagrama.
* Definir se a obtenção direta no INEP (fluxo A1) será implementada ou se a importação será somente por envio manual do arquivo.
* Definir a estratégia de extração (leitura de texto, OCR ou revisão manual) e o tratamento de imagens, fórmulas e tabelas.
* Confirmar as condições de uso e de reprodução do conteúdo das provas do INEP.
* A classificação das questões importadas é realizada no UC18 e o cadastro individual no UC10.

## 15. Referências

* Diagrama de Casos de Uso do AdE – Amigo do Estudante (`diagrama-casos-de-uso-ade.png`).
* Visão da Demanda (VD) do projeto.
* Funcionalidade F-07 – Importação de provas em PDF do INEP.
* UC01 – Cadastrar e autenticar usuário (F-06).
* UC10 – Cadastrar, editar e inativar questões (F-09).
* UC18 – Classificar por tema, competência e grade curricular (F-08).

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
