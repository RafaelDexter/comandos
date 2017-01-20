# Comando gzip

Se utilizado isoladamente, o **gzip** faz uso da seguinte sintaxe:

```
gzip [parâmetros] [nome_do_arquivo]
```

Entre os parâmetros disponíveis, tem-se:

+ `-c` - extrai um arquivo para a saída padrão;
+ `-d` - descompacta um arquivo comprimido;
+ `-l` - lista o conteúdo de um arquivo compactado;
+ `-v` - exibe detalhes sobre o procedimento;
+ `-r` - compacta pastas;
+ `-t` - testa a integridade de um arquivo compactado.

Ainda no que se refere às opções de parâmetros, é possível utilizar uma
numeração de 1 a 9 para indicar o nível de compactação. Quanto maior o
número, maior será a compactação do arquivo.

Eis alguns exemplos para facilitar a compreensão do comando `gzip`:

```
	$ gzip bigdata.dat
```

ou

```
	$ gzip -9 bigdata.dat
```

O comando acima compacta o arquivo `bigdata.dat`. Note que os arquivos
compactados com gzip recebem a extensão `.gz`. Para descompacta o arquivo
`bigdata.dat`

```
	$ gzip -d bigdata.dat.gz
```

ou

```
	$ gunzip bigdata.dat.gz
```


# Usando **tar** e **gzip**

O uso conjunto dos comandos **tar** e **gzip** é um belo exemplo de coerência
da frase "a união faz a força". Muitas vezes, é necessário juntar arquivos e,
ao mesmo, fazer com que o arquivo resultante, além de conter todos os outros,
também seja compactado. É aí que entra em cena a capacidade de juntar arquivos
do **tar** com a capacidade de compactação do **gzip**. Para utilizar ambos ao
mesmo tempo, o procedimento é muito simples: basta aplicar o comando **tar**
com o parâmetro `-z`. O arquivo resultante desse procedimento receberá a extensão
`.tar.gz`.

```
	$ tar -zcvf big.tar.gz data1.dat data2.dat data3.dat
```

Para extrair, use

```
  $ tar -zxvf big.tar.gz
```

Se você quiser extrair apenas um dos arquivos contidos no arquivo compactado,
basta indicá-lo no final do comando. Por exemplo, suponha que você queira
extrair o arquivo `data2.dat` de `big.tar.gz`. Eis o que você deve digitar:

```
  $ tar -zxvf big.tar.gz data2.dat
```
