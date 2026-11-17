# Suíte unitária inicial — PIM Dependents

Arquivo: `T2Dependents/EmpDependentAndServiceUnitTest.php`. Aborda UT-01/02/03/04/05/06, usando PHPUnit com mocks para o DAO (sem abrir banco). **Não há garantia de execução até instalar e rodar as dependências.** A sintaxe PHP do arquivo foi verificada na criação deste pacote.

## Exemplo de execução local (depois de preparar o OrangeHRM)

```bash
# Na raiz de literate-lamp, supondo o clone do OrangeHRM em ../orangehrm:
mkdir -p ../orangehrm/src/plugins/orangehrmPimPlugin/test/T2Dependents
cp felipe-velasque/unitario/T2Dependents/EmpDependentAndServiceUnitTest.php ../orangehrm/src/plugins/orangehrmPimPlugin/test/T2Dependents/

# Na raiz de ../orangehrm, com Composer e ambiente PHP preparados:
cd ../orangehrm
php src/vendor/bin/phpunit --group T2Dependents --testdox
```

**Registrar no relatório:** versão PHP, PHPUnit, comando, data, `PASS/FAIL/BLOCKED`, saída do terminal e passos para reproduzir. Nunca escrever resultado "passou" sem executar.
