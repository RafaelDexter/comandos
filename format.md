# Format

## mke2fs

Cria um sistema de arquivos do tipo ext2/ext3/ext4

+ **```-c```**

Verifica se há bad blocks no dispositivo antes de criar o sistema de arquivos. Se esta opção
for especificada duas vezes, será utilizado um teste de leitura-escrita mais lento em vez de
um teste de leitura rápida.

+ **```-F```**

Força o **mke2fs** a criar um sistema de arquivos, mesmo que o dispositivo especificado não
seja uma partição em um dispositivo especial de bloco ou se outros parâmetros não fizerem sentido.
Para forçar o **mke2fs** a criar um sistema de arquivos mesmo se o sistema de arquivos parece
estar em uso ou está montado (uma coisa verdadeiramente perigosa de se fazer), esta opção deve
ser especificada duas vezes.

+ **```-j```**

Cria um sistema de arquivos com um *journal* ext3. Se a opção **```-J```** não for especificada,
os parâmetros do *journal* padrão serão usados para criar um *journal* de tamanho apropriado
(dado o tamanho do sistema de arquivos) armazenado no sistema de arquivos. Note que você deve estar
usando um kernel que tenha suporte ext3 para realmente fazer uso do *journal*.

+ **```-l```** *filename*

Lê uma lista de blocos defeituosos a partir de um arquivo (*filename*). Observe que os números
de bloco na lista de bad block devem ser gerados usando o mesmo tamanho de bloco usado pelo
**mke2fs**. Como resultado, a opção **```-c```** para **mke2fs** é um método muito mais simples
e menos propenso a erros de verificar um disco para blocos ruins antes de formatá-lo, como **mke2fs**
passará automaticamente os parâmetros corretos para o programa **badblocks**.

+ **```-L```** *new-volume-labe*

Define o rótulo do volume para o sistema de arquivos como *new-volume-labe*. O comprimento máximo
do rótulo é de 16 bytes.


+ **```-O```** *feature[,...]*


Cria um sistema de arquivos com os recursos fornecidos (opções de sistema de arquivos), substituindo
as opções de sistema de arquivos padrão. Os recursos que são ativados por padrão são especificados
pela relação *base_features*, que na seção [*default*] no arquivo de configuração **/etc/mke2fs.conf**,
ou nas subseções [*fs_types*] para os tipos de uso especificados pela opção **```-T```**, modificados
adicionalmente pela relação de recursos encontrada nas subseções [*fs_types*] para o sistema de arquivos
e os tipos de uso.

+ **```-q```**

Execução silenciosa. Útil se o **mke2fs** for executado em um script.

+ **```-t```** *fs-type*

Especifica o tipo de sistema de arquivos (ext2, ext3, ext4, etc.) que deve ser criado.
Se esta opção não for especificada, o **mke2fs** escolherá um padrão por meio de como o comando
foi executado (por exemplo, usando o **mkfs.ext2**, **mkfs.ext3**, etc.) ou por padrão como
definido pelo arquivo **/etc/mke2fs.conf**.

Se a opção **```-O```** for usada para adicionar ou remover explicitamente opções de sistema de
arquivos que devem ser definidas no sistema de arquivos recém-criado, o sistema de arquivos
resultante pode não ser suportado pelo *fs-type* solicitado.

+ **```-T```** *usage-type[,...]*

Especifica como o sistema de arquivos será usado, para que o **mke2fs** possa escolher os melhores 
parâmetros do sistema de arquivos para esse uso. Os tipos de uso suportados são definidos no arquivo
de configuração **/etc/mke2fs.conf**. O usuário pode especificar um ou mais tipos de uso usando uma
lista separada por vírgulas.

+ **```-U```** *UUID*

Cria o sistema de arquivos com o UUID especificado.


+ **```-v```**

Verbose execution.


+ **```-V```**

Imprimi o número da versão do **mke2fs** e sai.

### Exemplo

```
mkfs -c -L d320 -t ext4 -v /dev/sdb1
```



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
