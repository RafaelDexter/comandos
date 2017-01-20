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
