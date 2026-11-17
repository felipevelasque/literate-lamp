# T2 — Verificação e Validação: PIM › Dependents (OrangeHRM)

**Responsável:** contribuição individual na pasta `felipe-velasque/` do repositório compartilhado `masmangan/literate-lamp`.

**Estado:** preparação documental e primeira suíte unitária **ainda não executada**. Não declarar aprovação, defeito ou cobertura quantitativa sem evidência de execução.

## Rastreabilidade e atividades

| Etapa | Artefato | Situação |
|---|---|---|
| Análise dos testes existentes e terceiros | `analise/01-codigo-original-e-terceiros.md` | Análise estática realizada; complementar após execução dos testes originais e revisão detalhada de material externo |
| Jornada de usuário | `docs/01-jornada.md` | Planejada com base no código do OrangeHRM |
| Plano e projeto de casos | `docs/02-plano-de-testes.md` | Planejados; confirmar cenários exploratórios no ambiente |
| Testes unitários | `unitario/T2Dependents/EmpDependentAndServiceUnitTest.php` | Implementação inicial, **sintaxe PHP conferida**; PHPUnit ainda não executado |
| Testes de integração | `integracao/README.md` | A implementar e executar no OrangeHRM + banco isolado |
| Testes de sistema | `sistema/README.md` | A implementar e executar no navegador |
| Relatório de execução | `docs/03-relatorio-execucao.md` | Modelo a preencher somente após execução |
| Relatório unificado | `docs/04-relatorio-unificado.md` | Estrutura inicial; completar com evidências reais |
| GitHub Issues | `issues/roteiro.md` | Sugestões para registrar no **repositório do professor**, atribuir ao executor e vincular PRs |

## Sistema e versão

- Repositório fonte: https://github.com/orangehrm/orangehrm
- Revisão verificada no ZIP fornecido: `56e23b3b09e7af29317a0943523b825843fff527`.
- Código de `Dependents`: `src/plugins/orangehrmPimPlugin/`.
- Front-end: `src/client/src/orangehrmPimPlugin/components/{SaveDependent,EditDependent}.vue` e `pages/employee/EmployeeDependents.vue`.

## Organização local sugerida

```text
pasta-pai/
├── literate-lamp/
│   └── felipe-velasque/    # estes arquivos, submetidos ao fork
└── orangehrm/             # clone do sistema sob teste, não adicionar ao fork
```

## Próximos passos

1. Registrar no repositório original as Issues da análise, do plano e da execução, todas atribuídas a você. Se não houver permissão para se atribuir, pedir cadastramento no Moodle/professor.
2. Revisar com o professor a exclusividade da jornada `PIM-Dependents`.
3. Publicar documentação de análise e plano no seu fork por commits separados, com PR para o repositório da turma.
4. Preparar PHP, Composer, banco isolado e PHPUnit; executar suíte original e anexar saída com versão e comando exato.
5. Executar os testes novos em três níveis; registrar falhas e limitações sem inventar resultados.
6. Completar o relatório de execução e integrar tudo ao relatório unificado da turma.

## Uso de IA

A organização dos artefatos, a leitura estática inicial e o código de testes unitários foram auxiliados por **ChatGPT (OpenAI)** em 17/11/2026. Os documentos e testes precisam ser revisados pelo responsável; não houve execução do PHPUnit nem de testes no navegador nesta preparação.
