# Compactação e descompactação de arquivos com **tar**

A sintaxe do **tar** é a seguinte:

```
  $ tar [parâmetros] [nome_do_arquivo_tar] [arquivos_de_origem]
```

Em parâmetros, é possível utilizar várias opções. Eis as principais:

+ `-c` - cria um novo arquivo tar

+ `-t` - exibe o conteúdo de um arquivo tar

+ `-p` - mantém as permissões originais do(s) arquivo(s)

+ `-r` - adiciona arquivos a um arquivo tar existente

+ `-f` - permite especificar o arquivo tar a ser utilizado

+ `-v` - exibe detalhes da operação

+ `-w` - pede confirmação antes de cada ação no comando

+ `-x` - extrai arquivos de um arquivo tar existente

+ `-z` - comprime o arquivo tar resultante com o gzip (visto mais à frente)

+ `-C` - especifica o diretório dos arquivos a serem armazenados (note que, neste caso, a letra é maiúscula)

O campo `nome_do_arquivo_tar` especifica qual o nome que o arquivo `.tar` terá,
e o campo `arquivos_de_origem` define o diretório ou os arquivos que se tornarão
um `.tar`. Vamos ver alguns exemplos para facilitar a compreensão:

```
  $ tar -cf cidades.tar curitiba londrina maringa
```

O comando acima cria o arquivo `cidades.tar`, que contém os arquivos `curitiba`
`londrina` e `maringa`. Aqui, você deve ter reparado que é possível combinar parâmetros.
Neste exemplo, isso ocorreu com -c e -f.

Vamos supor que todos os arquivos (`curitiba`, `londrina` e `maringa`)
estejam dentro do diretório `parana`. Podemos então compactar o diretório:

```
  $ tar -cvf estado.tar parana
```

assim, todo o seu conteúdo compactado no arquivo `estado.tar` (os detalhes
são exibidos graças à opção `-v`).

O exemplo a seguir lista o conteúdo do arquivo `estado.tar`:

```
  $ tar -tf estado.tar
```

Por sua vez, o comando abaixo faz com que todos os arquivos de `estado.tar`
sejam extraídos:

```
  $ tar -xvf estado.tar
```

Já no comando a seguir, apenas o arquivo `maringa` é extraído:

```
  $ tar -xvf estado.tar maringa
```

Uma coisa interessante é que, se a opção -v for usada duas vezes, detalhes
como permissões e data do(s) arquivo(s) apareção:

```
	$ tar -xvvf estado.tar maringa
```
## Opções de compressão

### gzip

**Compactar**

```
  $ tar -zcvf cidades.tar.gz curitiba londrina maringa
```

**Extrair**

```
  $ tar -zxvf cidades.tar.gz
```

### bzip2

**Compactar**

```
  $ tar -jcvf cidades.tar.bz2 curitiba londrina maringa
```

**Extrair**

```
  $ tar -jxvf cidades.tar.bz2
```

### Automático

Basta utilizar `-a` e colocar a extenção do arquivo.

**Compactar**

```
  $ tar -acvf cidades.tar.gz curitiba londrina maringa
```

ou

```
  $ tar -acvf cidades.tar.bz2 curitiba londrina maringa
```
