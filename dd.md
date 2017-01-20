# dd

O programa **dd**  é extremamente útil quando se trabalha com dispositivos de bloco e
caracteres. A única função deste programa é ler a partir de um arquivo de
entrada ou *stream* e gravar em um arquivo de saída ou *stream*, possivelmente fazendo
alguma conversão de codificação no caminho.

**dd** copia os dados em blocos de tamanho fixo. Veja como usar o **dd** com um
dispositivo de caracteres e algumas opções comuns:

```
	$ dd if=/dev/zero of=new_file bs=1024 count=1
```

O exemplo anterior copia um único bloco de 1024 bytes de `/dev/zero`
(um fluxo contínuo de zero bytes) para `new_file`.

Estas são as opções importantes do **dd**:

+ `if=file` - O arquivo de entrada. O padrão é a entrada padrão.
+ `of=file` - O arquivo de saída. O padrão é a saída padrão.
+ `bs=size` - O tamanho do bloco.
+ `ibs=size obs=size` - Os tamanhos de bloco de entrada e saída.
Use a opção `bs` Se você quiser usar o mesmo tamanho de bloco para entrada e saída.
Se não, use `ibs` e `obs` para entrada e saída, respectivamente.
+ `count=num` - O número total de blocos a copiar.
Quando se trabalha com um arquivo enorme - ou com um dispositivo que fornece um
fluxo interminável de dados, como `/dev/zero` - você quer que o **dd** pare em um
ponto fixo ou você pode desperdiçar muito espaço em disco, tempo de CPU, ou
ambos. Use `count` com o parâmetro `skip` para copiar um pequeno pedaço de um
arquivo ou dispositivo grande.
+ `skip=num` - Ignore os primeiros `num` blocos no arquivo de entrada e não
os copia para a saída.

:bangbang:
**dd** é muito poderoso, então certifique-se de saber o que você está fazendo quando
você executá-lo. É muito fácil corromper arquivos e dados em dispositivos. Muitas
vezes escrever a saída para um novo arquivo ajuda, se você não tem certeza do que ele vai fazer.

