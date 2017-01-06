# Format

## mkdosfs
```
mkdosfs -F 32 -I /dev/sdbX
```

+ **```-F```**

Especifica o tipo de tabela de alocação de arquivo usado (12, 16 ou 32 bit)

+ **```-I```**

Esta opção forçará o **mkdosfs** a funcionar corretamente.

+ **```-n```** *volume-name*

Define o nome do volume (*label*) do sistema de arquivo. O nome do volume pode
ter até 11 caracteres. O padrão é sem etiqueta.

+ **```-c```**

Verifica se há bad blocks no dispositivo antes de criar o sistema de arquivo.

+ **```-l```** *filename*

Lê os bad blocks a partir de uma lista  *filename*.

+ **```-v```**

Verbose execution.
