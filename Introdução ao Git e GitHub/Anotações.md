# Aula 1

#### SHA1: algortimo de criptografia , representa o arquivo em 40 caracteres e pode ser usado para verificar se um arquivo foi alterado, corrompido, aberto. 

openssl sha1 texto.txt   -> retorna um código de 40 char (string) que representa esse arquivo texto.txt

## Objetos:

#### Blobs (bolhas): é uma coleção de dados binários armazenados como uma única entidade em um sistema de gerenciamento de banco de dados. Blobs geralmente são objetos de imagem, áudio ou outro objetos multimedia, apesar de algumas vezes código binário executável ser armazenado como um blob.   (Wikipedia) Contém o tipo do objeto, o tamanho desse arquivo e o conteúdo do arquivo. Tem o sha1 do arquivo.

#### Trees (árvores): armazenam blobs e apontam para tipos diferentes de blobs ou outras árvores. Também contém metadados. Além dos mesmos dados que o blob guarda, guarda o nome do arquivo e mantém a estrutura de onde esta esse arquivo.

#### Se muda o SHA do objeto, muda a informação no blob e por consequência o sha da árvore.

#### Commit : objeto que junta tudo isso. Aponta para uma árvore parente (parent, último commit realizado antes dele), para o autor, para a mensagem relacionada ao commit específico. Também tem um timestamp de quando foi criado e encriptação de seus metadados (alterado dado dentro da blob, muda da árvore, e muda do commit)

#### Como o commit aponta pro parente e assim sucessivamente, o Git é muito seguro, pois é possível fazer uma linha do tempo de intervenções pelos commits. 

#### Git é um sistema distribuído (pode ser compartilhado) seguro (todos contribuintes para um mesmo código online tem cópias seguras dos mesmos).



## Aula 2

## Chaves SSH

#### Autenticação por senha e nome foi desligado do seu computador pro GitHub, por segurança. A autenticação nestas "transações" é feita por chaves ssh ou tokens. Chave ssh é uma forma segura e encriptada de estabelexer uma conezão entre 2 máquinas (sevidor GitHub e a nossa máquina).

#### Produz uma chave pública e uma privada. A pública é colocada no GitHub pra que eles consiga reconhecer a máquina e não precise usar mais senha (em Account settings > SSH keys).

#### Para gerar a chave no Terminal: 

ssh-keygen -t ed25519 -C <email>    -> gera uma chave ssh relacionada a esse email

Na pasta onde as chaves estão:

eval $(ssh-agent -s) -> retorna Agent pid(<numero>)   isso inicia um processo ssh agent que pega as chaves e lida com elas. Copia a chave pública (.pub) e cola no site.

ssh-add id_ed25519 -> passa a chave privada pro sistema 

Agora quando for clonar um repositório do Git não vai pedir senha, pois já vai ter essa troca do agent com o GitHub.

## Tokens de acesso pessoal

#### São outra forma de autenticação do GitHub que usa protocolo HTTPS. Para gerar o Token, no site em Developer Settings > Personal access tokens cria um token. Salva a senha em algum local seguro (mais difícil garantir que esse arquivo não vai ser acessado...) e depois usa qd for clonar algum repositório do GitHub.









