>## Comandos Basicos
> - cat: printa no terminal o texto/ ler o que tem dentro
> - grep: busca por padroes, ou por algo especifico
> - ssh: conexao com outros via rede
> - file: retorna qual o tipo de arquivo
> - find: procura por algum, nome, arquivo, em diretorios
> - du: Blocos do sistema
> - strings: retorna as strings de um arquivo
> - **man: comando que mostra como outros comandos funciona**
>
>
>
## Bandit 0-12
>
>#### Bandit 0
> - se conectar no level 0, utilizando ssh:
> - ssh bandit0@bandit.labs.overthewire.org -p 2220
> - bandit0 seria o usuario
> - bandit.labs.overthewire.org seria o host
> - "-p"seria um indicativo que a conexao vai ser por uma porta especifica
> - 2220 seria a porta
>
> - *Senha*:**bandit0** 
>
 #### Bandit 0-1
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cat para ler o arquivo "readme"
>
> - *Senha:* **NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL** 
>
 #### Bandit 1-2
> - utilizar o comando ls para ver o que tem no diretorio
> - utiliar o comando cat, porem ao passar o arquivo "-" utilizar o caminho completo, ja que o "-" se trata de um caractere especial, portanto ao utilizar somente "cat -" nao iria funcionar, portanto utilizar cat ./-
>
> - *Senha*: **rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**
>
 #### Bandit 2-3
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cat, porem por se tratar de um arquivo com espacos no nome (Exemplo: espacos no nome), devesse utilizar contra barras "\" ao dar espacos 
> - - cat spaces\ in\ this\ filename 
> - - cat ./spaces\ in\ this\ filename
>
> *Senha*: **aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG**
>
 #### Bandit 3-4
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cd para entrar no diretorio "inhere"
> - utilizar o comando ls
> - ao perceber que ls nao retorna nada, utilizar o comando ls com a flag -a, para listar todos os arquivos, ate os ocultos
> - ls -a
> - utilizar o cat para vizular o arquivo ".hidden"
> - cat ./.hidden
>
> *Senha*: **2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe**
>
#### Bandit 4-5
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cd para entrar no diretorio "inhere"
> - utilizar o comando ls para ver o que tem dentro de inhere
>  
> - o que temos que fazer e pegar todos os arquivos do diretorio e verificar qual o tipo deles, para assim determinarmos qual o correto
>
> - primeiro: utilizamos o comando find, para pegarmos todos os arquivos
> - segundo: temos que passar o retorno (o que o comando find encontrou) para o comando file
>
> - Comando final:
>       find ./ -exec file {} \;
>
> - Explicando o comando:
>   - **find**: comando utilizado para encontrar arquivos, diretorios em
>   - **./**: diz para o comando find, em qual diretorio ele deve buscar os arquivos, ./ indica o diretorio atual
>   - **-exec**: uma flag de **find** que permite utilizar comandos nos retornos do comando, portanto essa flag nos permite utilizar o file em cada retorno do find
>   - **file**: comando que retorna o tipo de um arquivo passado como argumento
>   - **{}**: par de chaves que indica aonde o retorno do comando find vai ser substituido, ele indica que cada retorno do find vai ser utilizado como argumento do file
>   - **\\;**: indica aonde o comando deve terminar ao fim de cada instancia, portanto ao utilizar um dos retornos da funcao find, aquela instancia de execucao deve acabar ali
>
>
> - *Senha*: **lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR**
>
> #### Bandit 5-6
> - Utilizar o comando ls para verificar o que tem dentro do diretorio
> - Utilizar o comando cd para entrar no diretorio inhere
> - Utilizar o comando ls para verificar o que tem dentro do diretorio inhere
> - Nessa questao precisamos encontrar um arquivo especifico que contenha 3 pro priedades chaves
>   - human-readable
>   - 1033 bytes in size
>   - not executable
>
> -  find -size 1033c -exec file {} \; | grep "ASCII text" | grep -v "executable"