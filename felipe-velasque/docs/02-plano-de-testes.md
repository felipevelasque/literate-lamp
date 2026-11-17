# Plano de testes e projeto dos casos — PIM / Dependents

**Issue:** [link após criação]  
**Status:** planejamento; nenhum caso executado neste documento.

## Objetivo e escopo

Validar operações CRUD de dependentes e testar regras de validação, persistência, controle de acesso e fluxo de interface. Fora do escopo inicial: performance, estresse de milhares de dependentes e auditoria de todos os módulos PIM. Testes devem ser independentes sempre que possível, com dados distintos e limpeza em `tearDown`.

## Estratégia

| Nível | Sistema sob teste | Ferramenta proposta | Oráculo |
|---|---|---|---|
| Unitário | `EmpDependent` e delegação/tratamento de erro de `EmployeeDependentService` | PHP + PHPUnit 9, mocks de DAO | Tipo aceito/rejeitado, exceções, argumentos e resultados |
| Integração | `EmployeeDependentDao` + banco, API REST + autorização | PHP + PHPUnit + DB isolado | HTTP/status/modelo e estado persistido |
| Sistema | Jornada PIM/Dependents no navegador | Playwright + TypeScript (escolha proposta) | UI, dados após recarga, exclusão e restrições do formulário |

**Critérios de seleção de dados:** equivalência (`child`, `other`, inválido), valores-limite (99/100/101 caracteres; sequência 1/99/100), tabela de decisão (`other` × especificação preenchida), transições CRUD e casos negativos de autorização. Valores-limite de identificador devem ser realizados no DAO/API conforme o contrato de cada camada, não diretamente na UI.

## Casos projetados

| ID | Nível | Entrada/pré-condição | Resultado esperado | Técnica | Requisito |
|---|---|---|---|---|---|
| UT-01 | Unitário | `child` e `other` em `EmpDependent` | Aceitos | Equivalência | CA-06 |
| UT-02 | Unitário | `relationshipType` inválido (ex.: `spouse`) | `InvalidArgumentException` | Equivalência negativa | CA-06 |
| UT-03 | Unitário | Nascimento nulo / data válida | Propriedade preservada | Equivalência | CA-01/02 |
| UT-04 | Unitário | Serviço salva dependente com DAO mock | Delegação exatamente uma vez | Interação/mock | CA-01 |
| UT-05 | Unitário | Serviço exclui IDs `[1,2]` de funcionário 1 | Argumentos corretos e total retornado | Interação/mock | CA-05 |
| UT-06 | Unitário | DAO mock lança `Exception` na busca | Serviço lança `ServiceException` contendo causa | Exceção | CA-07 |
| IT-01 | Integração | Novo dependente de funcionário teste | DAO grava e consulta a mesma informação | Estado persistido | CA-01 |
| IT-02 | Integração | `seqNo` 99 e 100 em dados controlados | 99 aceito conforme contexto; 100 rejeitado | Valores-limite | CA-05 |
| IT-03 | Integração | Excluir IDs de A e tentar afetar B | Registros de B continuam intactos | Isolamento/segurança | CA-05/07 |
| IT-04 | Integração | API `name` com 99/100/101 caracteres | 99/100 aceitos; 101 rejeitado com validação apropriada | Valores-limite | CA-03 |
| IT-05 | Integração | API com tipo não reconhecido | Rejeição de validação; nada gravado | Equivalência negativa | CA-06 |
| IT-06 | Integração | API `other` e `relationship` vazio | **Exploratório**: comparar comportamento com UI; verificar requisito antes de alegar defeito | Tabela de decisão | CA-02 |
| IT-07 | Integração | Consulta/edição de dependente inexistente | Não cria/edita registro; resposta de erro adequada | Exceção | CA-04/07 |
| IT-08 | Integração | Operar sobre funcionário não acessível | Nenhum dado de outra pessoa exposto ou alterado | Segurança | CA-07 |
| ST-01 | Sistema | Cadastrar filho com dados válidos | Dependente aparece na lista após recarga | Fluxo principal | CA-01 |
| ST-02 | Sistema | Selecionar `Other`, deixar especificação vazia | Formulário exige `Please Specify` | Tabela de decisão | CA-02 |
| ST-03 | Sistema | Nome vazio | Salvar impedido | Equivalência negativa | CA-03 |
| ST-04 | Sistema | Nome 100 e 101 caracteres | 100 aceito; 101 impedido | Valores-limite | CA-03 |
| ST-05 | Sistema | Editar nome de dependente | Atualizado após recarga, sem duplicata | Transição | CA-04 |
| ST-06 | Sistema | Cancelar formulário | Sem alteração nos registros | Transição negativa | CA-04 |
| ST-07 | Sistema | Excluir com confirmação | Registro removido | Transição | CA-05 |
| ST-08 | Sistema | Excluir e cancelar diálogo | Registro permanece | Transição negativa | CA-05 |
| ST-09 | Sistema | Informar data inválida | UI impede submissão | Equivalência | CA-06 |

## Registro da execução

Para **cada** teste: código da versão, data/hora, responsável, comando, ambiente, dado de entrada, esperado, observado, PASS/FAIL/BLOCKED, duração (quando disponível), logs/screenshot, e link da Issue. Uma falha de automação ou de ambiente **não é necessariamente um defeito do produto**; confirmar por reprodução antes de abrir defeito.

## Critério de entrada/saída

**Entrada:** versão fixada, banco de testes isolado, dependências instaladas, usuário/funcionário de teste, casos revisados, permissão para executar testes.  
**Saída:** testes dos três níveis executados ou bloqueios justificados, evidências versionadas, defeitos reproduzidos com passos e severidade, relatório consolidado, GitHub Issues/commits/PR vinculados.

## Segurança e ética de testes

Não rodar testes de autorização destrutivos na demonstração compartilhada. Não enviar credenciais, cookies ou dados pessoais nos logs e screenshots. Usar registros fictícios e exclusão de dados ao encerrar os casos.
