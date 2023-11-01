#CTF
>  Capture the Flag (CTF) em segurança da computação é um exercício no qual os participantes tentam achar Strings, chamadas de "bandeiras" (flags), que estão secretamente escondidas em programas ou sites propositadamente vulneráveis, com o objetivo de passar para o próximo nível.
>
> Este guia tem o intuito de mostrar para iniciantes na área de Segurança da Informação o básico de como funciona o exercício e algumas soluções do site OverTheWire.org.
>
>O site divide suas questões em níveis, sendo alguns deles:
>   - Bandit
>   - Natas
>   - Leviathan
>   - Krypton 
---
> 
>
>
### Comandos Basicos
> - **cd**: Usado para mudar o diretório atual no sistema de arquivos. Isso permite que você navegue entre diretórios e acesse diferentes pastas no sistema. Você fornece o nome do diretório para o qual deseja mudar como argumento, e o comando "cd" o levará para esse diretório.
> - **ls**: Utilizado para listar o conteúdo de um diretório. Ele exibe os arquivos e subdiretórios no diretório atual. Pode ser personalizado com várias opções para exibir informações adicionais, como tamanhos de arquivos, datas de modificação, permissões e muito mais. É uma ferramenta útil para visualizar o conteúdo de um diretório específico no sistema de arquivos.
> - **cat**: Utilizado para imprimir no terminal o conteúdo de um arquivo. Ele é frequentemente usado para visualizar o conteúdo de arquivos de texto
> - **grep**: Ferramenta de busca que permite localizar padrões ou texto específico dentro de arquivos. Ele é amplamente utilizado para filtrar e extrair informações relevantes de grandes volumes de texto.
> - **ssh**: Protocolo que permite a conexão segura com outros sistemas ou servidores por meio de uma rede. Ele é comumente utilizado para acesso remoto a sistemas e transferência segura de arquivos.
> - **file**: Usado para determinar o tipo de arquivo com base em sua estrutura e conteúdo. Ele pode identificar se um arquivo é um arquivo de texto, imagem, executável, entre outros.
> - **find**: Ferramenta de busca de arquivos e diretórios em um sistema de arquivos. Ele permite localizar arquivos com base em critérios como nome, tamanho, data de modificação, e outros.
> - **du**: Usado para exibir o uso de espaço em disco por arquivos e diretórios. Ele ajuda a determinar quanto espaço ocupam no sistema de arquivos.
> - **strings**: Extrair sequências de caracteres legíveis de arquivos binários. Isso pode ser útil para encontrar informações legíveis, como mensagens de erro ou texto embutido em executáveis.
> - **man**: Usado para exibir informações detalhadas sobre como outros comandos funcionam. Basta fornecer o nome do comando como argumento, e o "man" fornece documentação completa sobre seu uso e opções disponíveis.
>
>

## Bandit 0-12

>#### Bandit 0
> - se conectar no level 0, utilizando ssh:
> - ssh bandit0@bandit.labs.overthewire.org -p 2220
> - bandit0 corresponde ao Usuario
> - bandit.labs.overthewire.org Corresponde ao Host
> - ***-p*** indica que a conexão vai ser por uma porta específica
> - 2220 A porta
>
> - *Senha*: **bandit0** 
>
> *Obs*: Para acessar o proximo nivel, guarde a senha do nivel atual, saia da conexao SSH (crtl + D) e conecte-se com a proxima questao alterando o usuario para corresponder a sua questao
>
>Exemplo: bandit1@bandit.labs.overthewire.org -p 2220
>
>Esse comando corresponde a conexao do nivel 1.
>
>
 #### Bandit 0-1
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cat para ler o arquivo "readme"
>
> - *Senha:* **NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL** 
>
 #### Bandit 1-2
> - utilizar o comando ls para ver o que tem no diretorio
> - utiliar o comando cat, porem ao passar o arquivo "-" utilizar o caminho completo, ja que o "-" se trata de um caractere especial, portanto ao utilizar somente "cat -" nao vai funcionar, logo utilizar "cat ./-"
>
> - *Senha*: **rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi**
>
 #### Bandit 2-3
> - utilizar o comando ls para ver o que tem no diretorio
> - utilizar o comando cat, porem por se tratar de um arquivo com espacos no nome (Exemplo: espacos no nome), devesse utilizar contra barras "\\" ao dar espacos 
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
> - o que temos que fazer é pegar todos os arquivos do diretorio e verificar qual o tipo deles, para assim determinarmos qual o correto
>
> - primeiro: utilizamos o comando find, para pegarmos todos os arquivos
> - segundo: temos que passar o retorno (o que o comando find encontrou) para o comando file
>
> - Comando final:
>       find ./ -exec file {} \;
>
> - Explicando o comando:
>   - **find**: comando utilizado para encontrar arquivos, diretorios em
>   - **./**: diz para o comando find, em qual diretorio ele deve buscar os arquivos, "./" indica o diretorio atual
>   - **-exec**: uma flag de **find** que permite utilizar comandos nos retornos do comando, portanto essa flag nos permite utilizar o file em cada retorno do find
>   - **file**: comando que retorna o tipo de um arquivo passado como argumento
>   - **{}**: par de chaves que indica aonde o retorno do comando find vai ser substituido, ele indica que cada retorno do find vai ser utilizado como argumento do file
>   - **\\;**: indica aonde o comando deve terminar ao fim de cada instancia, portanto ao utilizar um dos retornos da funcao find, aquela instancia de execucao deve acabar ali
>
>
> - *Senha*: **lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR**
>
 #### Bandit 5-6
> - Utilizar o comando ls para verificar o que tem dentro do diretorio
> - Utilizar o comando cd para entrar no diretorio inhere
> - Utilizar o comando ls para verificar o que tem dentro do diretorio inhere
> - Nessa questao precisamos encontrar um arquivo especifico que contenha 3 propriedades chaves
>   - human-readable
>   - 1033 bytes in size
>   - not executable
>
>```Comando final:```
``` bash 
find -size 1033c -exec file {} \; | grep    "ASCII >text" | grep -v "executable"
```
> 
> - Explicando o comando:
>   - **find**: comando utilizado para encontrar um "match" com o nome de arquivos ou diretorios a partir de um path.
>   - **-size**: flag de find, que permite alterar os criterios de busca, para buscar um arquivo com o tamanho exato
>   - **1033**: argumento da flag *-size*, 1033 sendo o tamanho do arquivo, e *c* indicando a unidade, no caso bytes (essas informacoes estao disponiveis no comando "man find")
>   - **-exec**: uma flag de **find** que permite utilizar comandos nos retornos do comando, portanto essa flag nos permite utilizar o file em cada retorno do find
>   - **file**: comando que retorna o tipo de um arquivo passado como argumento
>   - **{}**: par de chaves que indica aonde o retorno do comando find vai ser substituido, ele indica que cada retorno do find vai ser utilizado como argumento do file
>   - **\\;**: indica aonde o comando deve terminar ao fim de cada instancia, portanto ao utilizar um dos retornos da funcao find, aquela instancia de execucao deve acabar ali
>   - **|**: a opcao "pipe" permite continuarmos a execucao, adicionando comandos
>   - **grep**: comando para filtrarmos, escolhendo padroes, ou uma string em especifico
>   - **ASCII text**: indica que queremos filtrar as linhas que contenham essa string
>   - **grep -v**: Mesmo comando utilizando anteriormente, porem com a flag -v, que altera os criteiros, e ao inves de pegar as linhas que contenham essa string, o comando pega as linhas que nao contem (mais informacoes no "man grep")
>
> *Senha*: **P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU**
>
 #### Bandit 6-7
>
> find ./ -group bandit6 -a -user bandit7 -a -size 33c 2> /
> dev/null
>
> *Senha*: **z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S**
>
#### Bandit 7-8
>
> cat data.txt | grep "millionth"
>
> *Senha*: **TESKZC0XvTetK0S9xNwm25STk5iWrBvP**
>
 #### Bandit 8-9
>
> cat data.txt | sort | uniq -u
>
> *Senha*: **EN632PlfYiZbn3PhVK3XOGSlNInNE00t**
>
 #### Bandit 9-10
>
>   strings data.txt | grep "="
>
> *Senha*:**G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s**
>
#### Bandit 10-11
>
>
>   base64 -d data.txt
> *Senha*:**6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM**
>
 #### Bandit 11-12
>
> tr 'A-Za-z' 'N-ZA-Mn-za-m'
>
> *Senha*: **JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv**
>
 #### Bandit 12-11