# Contribuição para o relatório unificado da turma — PIM / Dependents

**Status:** estrutura parcial; seção de execução não pode ser concluída antes de rodar os testes.

## Introdução: sistema e execução

O OrangeHRM é um sistema de gestão de recursos humanos com backend PHP, API REST e interface Vue. O módulo **PIM** gerencia informações de colaboradores, incluindo dependentes. Para a análise foi utilizado o repositório oficial `orangehrm/orangehrm`, revisão `56e23b3b09e7af29317a0943523b825843fff527`.

**Obtenção e preparação:** clonar `https://github.com/orangehrm/orangehrm`; preparar as dependências PHP por Composer, banco de testes e a suíte PHPUnit indicada em `phpunit.xml`. Registrar no relatório os comandos efetivamente executados e todos os detalhes necessários à reprodução. Para a interface, utilizar uma instalação controlada e navegador automatizado. **A compilação e instalação ainda precisam ser realizadas/confirmadas pelo executor.**

## Objetivos e jornada

Avaliar e complementar a qualidade dos testes do módulo PIM em operações de cadastro, consulta, atualização e exclusão de dependentes de funcionário. Descrição e critérios de aceitação: [`01-jornada.md`](01-jornada.md).

## Casos de teste

O projeto contempla equivalência, valores-limite, tabela de decisão e transições CRUD em três níveis. Especificação completa: [`02-plano-de-testes.md`](02-plano-de-testes.md).

## Análise crítica de testes existentes

Inventário e análise por nível, lacunas e fontes de terceiros: [`../analise/01-codigo-original-e-terceiros.md`](../analise/01-codigo-original-e-terceiros.md).

## Resultados e defeitos

**PENDENTE de execução verificável.** Preencher com os resultados de [`03-relatorio-execucao.md`](03-relatorio-execucao.md), links para logs/evidências e Issues de defeitos quando existirem. Não afirmar que todos os testes passaram antes da execução.

## Registro de contribuições

**PENDENTE**: links de Issues atribuídas, commits autorais e PRs aceitos no repositório compartilhado.

## Fontes e uso de IA

Fontes primárias: enunciado do Moodle e código original OrangeHRM; outras referências listadas na análise crítica. ChatGPT (OpenAI) usado para apoio à análise e à redação inicial, sujeito à revisão e validação pelo estudante.
