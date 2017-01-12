# Format

## mke2fs

Cria um sistema de arquivos do tipo ext2/ext3/ext4

+ **```-c```**

Verifica se há bad blocks no dispositivo antes de criar o sistema de arquivos. Se esta opção
for especificada duas vezes, será utilizado um teste de leitura-escrita mais lento em vez de
um teste de leitura rápida.

+ **```-F```**

Força o ```mke2fs``` a criar um sistema de arquivos, mesmo que o dispositivo especificado não
seja uma partição em um dispositivo especial de bloco ou se outros parâmetros não fizerem sentido.
Para forçar o ```mke2fs``` a criar um sistema de arquivos mesmo se o sistema de arquivos parece
estar em uso ou está montado (uma coisa verdadeiramente perigosa de se fazer), esta opção deve
ser especificada duas vezes.

+ **```-j```**

Cria um sistema de arquivos com um *journal* ext3. Se a opção **```-J```** não for especificada,
os parâmetros do *journal* padrão serão usados para criar um *journal* de tamanho apropriado
(dado o tamanho do sistema de arquivos) armazenado no sistema de arquivos. Note que você deve estar
usando um kernel que tenha suporte ext3 para realmente fazer uso do *journal*.


## mkdosfs


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

### Exemplo

```
mkdosfs -F 32 -I /dev/sdbX
```
