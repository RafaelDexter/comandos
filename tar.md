Compactação e descompactação de arquivos com Tar e gzip

A sintaxe do **tar** é a seguinte:

```
tar [parâmetros] [nome_do_arquivo_tar] [arquivos_de_origem]
```

Em parâmetros, é possível utilizar várias opções. Eis as principais:

-c - cria um novo arquivo tar;
-t - exibe o conteúdo de um arquivo tar;
-p - mantém as permissões originais do(s) arquivo(s);
-r - adiciona arquivos a um arquivo tar existente;
-f - permite especificar o arquivo tar a ser utilizado;
-v - exibe detalhes da operação;
-w - pede confirmação antes de cada ação no comando;
-x - extrai arquivos de um arquivo tar existente;
-z - comprime o arquivo tar resultante com o gzip (visto mais à frente);
-C - especifica o diretório dos arquivos a serem armazenados (note que, neste caso, a letra é maiúscula).

O campo `nome_do_arquivo_tar` especifica qual o nome que o arquivo `.tar` terá,
e o campo `arquivos_de_origem` define o diretório ou os arquivos que se tornarão
um `.tar`. Vamos ver alguns exemplos para facilitar a compreensão:

```
tar -cf cidades.tar curitiba londrina maringa
```

O comando acima cria o arquivo `cidades.tar`, que contém os arquivos `curitiba`
`londrina` e `maringa`. Aqui, você deve ter reparado que é possível combinar parâmetros.
Neste exemplo, isso ocorreu com -c e -f.

Vamos supor que todos os arquivos (`curitiba`, `londrina` e `maringa`)
estejam dentro do diretório `parana`. Podemos então compactar o diretório:

```
tar -cvf estado.tar parana
```

assim, todo o seu conteúdo compactado no arquivo `estado.tar` (os detalhes
são exibidos graças à opção `-v`).

O exemplo a seguir lista o conteúdo do arquivo `estado.tar`:

```
tar -tf estado.tar
```

Por sua vez, o comando abaixo faz com que todos os arquivos de `estado.tar`
sejam extraídos:

```
tar -xvf estado.tar
```

Já no comando a seguir, apenas o arquivo saci.txt é extraído:

	tar -xvf lendas.tar saci.txt

Uma coisa interessante é que, se a opção -v for usada duas vezes, detalhes como permissões e data do(s) arquivo(s) apareção:

	tar -xvvf lendas.tar saci.txt

Comando gzip

A ferramenta Tar, por si somente, serve apenas para juntar vários arquivos em um só. No entanto, o programa não é capaz de diminuir o tamanho do arquivo resultante, isto é, de compactá-lo. É neste ponto que entra em cena o gzip (GNU zip) ou outro compactador de sua preferência. Se utilizado isoladamente, o gzip faz uso da seguinte sintaxe:

gzip [parâmetros] [nome_do_arquivo]

Entre os parâmetros disponíveis, tem-se:

-c - extrai um arquivo para a saída padrão;
-d - descompacta um arquivo comprimido;
-l - lista o conteúdo de um arquivo compactado;
-v - exibe detalhes sobre o procedimento;
-r - compacta pastas;
-t testa a integridade de um arquivo compactado.

Ainda no que se refere às opções de parâmetros, é possível utilizar uma numeração de 1 a 9 para indicar o nível de compactação. Quanto maior o número, maior será a compactação do arquivo.

Eis alguns exemplos para facilitar a compreensão do comando gzip:

	gzip infowester.odt

O comando acima compacta o arquivo infowester.odt. Note que os arquivos compactados com gzip recebem a extensão .gz.

	gzip -d infowester.odt.gz

O comando acima descompacta o arquivo infowester.odt.gz.

	gzip -1 colorado.ods

O procedimento acima faz com que o arquivo colorado.ods seja compactado considerando o nível mais baixo de compreensão.

Usando Tar e gzip

O uso conjunto dos comandos Tar e gzip é um belo exemplo de coerência da frase "a união faz a força". Muitas vezes, é necessário juntar arquivos e, ao mesmo, fazer com que o arquivo resultante, além de conter todos os outros, também seja compactado. É aí que entra em cena a capacidade de juntar arquivos do Tar com a capacidade de compactação do gzip. Para utilizar ambos ao mesmo tempo, o procedimento é muito simples: basta aplicar o comando tar com o parâmetro -z. O arquivo resultante desse procedimento receberá a extensão .tar.gz.

Neste ponto, vemos um comando bastante usado na instalação de programas e bibliotecas:

	tar -zxvf nome_do_arquivo.tar.gz

Se você estiver lendo este artigo deste o começo, certamente já sabe o que o comando acima faz, mesmo assim, vamos explicar para não restar dúvidas: a letra z deve ser usada porque o arquivo foi compactado com gzip; a letra x indica que o comando deve extrair o arquivo (portanto, a referida instrução serve para extrair e descompactar o arquivo tar.gz); a letra v exibe os detalhes do procedimento; por fim, a letra f especifica qual arquivo será usado nesta atividade.

Suponha, agora, que você queira deixar em um único pacote os arquivos marvin.png, zaphod.txt e trillian.odt. O arquivo resultante terá o nome guia.tar.gz. Eis o comando que utilizaremos para este exemplo:

	tar -zcvf guia.tar.gz marvin.png zaphod.txt trillian.odt

Note que o comando é muito parecido com o procedimento de descompactação do exemplo anterior, com a diferença de que o parâmetro c foi utilizado no lugar de x, pois o objetivo aqui é criar um arquivo novo, e não fazer a extração de um já existente. Para extrair o conteúdo desse arquivo, basta executar o comando abaixo (também exibido na figura acima):

	tar -zxvf guia.tar.gz

Se você quiser extrair apenas um dos arquivos contidos no arquivo compactado, basta indicá-lo no final do comando. Por exemplo, suponha que você queira extrair o arquivo marvin.png de guia.tar.gz. Eis o que você deve digitar:

	tar -zxvf guia.tar.gz marvin.png
