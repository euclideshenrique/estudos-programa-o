# Meus Estudos de Frontend 🚀

Este repositório é o meu diário de bordo na jornada de aprendizado em desenvolvimento web. Aqui documento meus avanços, conceitos aprendidos e os códigos que estou construindo no curso.dev.

## O que aprendi hoje:
##                                                >03/06/2026 < 
Aprendi que o Node.js é uma ferramenta que vai nos permitir trabalhar com a linguagem JavaScript diretamente na nossa maquina, sem depender do navegador, que é o ambiente para o qual ela foi feita para rodar originalmente. No nosso caso, o Node.js será o responsavel por executar codigos JavaScript no servidor do nosso projeto clone TabNews.

Já o NVM é uma outra ferramenta que nos permite trabalhar com várias versões do Node em nossa máquina, facilitando a troca entre elas com um comando simples, sem precisar ficar desinstalando e instalando versões sempre que formos trabalhar em projetos que utilizam diferentes versões do Node.

Exemplo: o Node.js é como um forno elétrico que permite usar uma receita (JavaScript) fora da cozinha tradicional (o navegador). Assim, você pode "cozinhar" programas no servidor.

Já o NVM é como um painel que troca a voltagem do forno. Ele permite usar o forno em diferentes potências (versões do Node.js) conforme a receita pede, sem precisar comprar outro.

O React nos permite programar esses componentes usando uma sintaxe especial (HTML + JavaScript), com a vantagem de poder reutilizá-los em várias partes do site

O Next.js fornece a infraestrutura e a "cola" para juntar e organizar todos esses componentes React nas páginas do site

##                                                >04/06/2026 < 

Depois de uma rápida dica sobre como limpar o seu terminal usando clear ou CTRL + L, chegou a hora de subir de verdade o nosso Servidor Web, mas para isso, precisamos de uma página de verdade e não poderia ser diferente, a não ser começar com a index.


##                                                >07/06/2026 <

## Lista de comandos abordados
git log - listar os commits do repositório.
git add - sobe alterações para a staging area.
git commit - realiza novos commits.
git commit --amend - substitui o commit anterior por um novo, mas aproveita as alterações dele.
git diff - calcula a diferença entre as versões/alterações dos arquivos.

Todos estes comandos funcionam de forma offline no Git e podem ser usados sem a necessidade de uma conexão com a internet, pois nenhum deles transmite informações para fora do seu computador.

## Como o Git consegue ser eficiente em espaço se grava arquivos inteiros em vez de diffs?

O Git consegue ser eficiente nesse aspecto, mesmo gravando arquivos inteiros, graças a três coisas:

Compressão: cada blob é compactado
Deduplicação: arquivos idênticos são armazenados apenas uma vez, pois geram o mesmo hash
Packfiles: periodicamente o Git agrupa os blobs e aplica delta compression para armazenamento de longo prazo

## O Git realmente não armazena as diferenças (diffs) permanentemente?

O Git não armazena os diffs de forma permanente. Cada commit é como uma "foto" do repositório inteiro naquele momento. Os diffs que visualizamos são calculados sob demanda, comparando as "fotos" (snapshots) quando necessário.

Essa abordagem é mais performática porque o Git não precisa reconstruir o arquivo aplicando todas as alterações desde o início do projeto.

## O Git duplica todos os arquivos a cada commit, mesmo os não modificados?

Não! O Git vai armazenar apenas os arquivos que foram alterados. Ele não duplica os arquivos que estão iguais.

Os arquivos não modificados continuam sendo apenas apontamentos (referências) para os blobs já existentes. É por isso que, mesmo tendo muitos commits, o repositório não fica gigantesco.

## Como sair do VIM quando ele abre ao executar git commit?

Quando você executa git commit sem o parâmetro -m, o Git abre um editor de texto para você escrever a mensagem. Por padrão, esse editor é o VIM.

Para salvar e sair do VIM:

Pressione ESC (garante que você está no modo comando)
Digite :wq
Pressione Enter

O commit será salvo e você volta para o terminal normal.

Para configurar o VSCode como editor padrão do Git:

Execute uma vez no terminal:

git config --global core.editor "code --wait"

Depois disso, ao executar git commit, vai abrir uma aba normal no VSCode para você escrever a mensagem.

## O git log fica "preso" mostrando (END) e não consigo digitar novos comandos

Esse é o comportamento normal. O git log deixa o terminal "preso" para que os comandos que você digita no teclado influenciem apenas ele mesmo (permitindo navegar pelo histórico).

Para sair dessa tela, basta pressionar a tecla Q.

## O que acontece com o commit antigo após usar --amend? É possível recuperá-lo?

O comando git commit --amend não altera diretamente um commit existente, pois commits são imutáveis. O que ele faz é criar um novo commit com o conteúdo atualizado e substituir a referência do commit anterior.

O commit antigo é substituído e continua existindo temporariamente no histórico como um commit "órfão", até que o garbage collector do Git faça a remoção automática após um tempo. O garbage collector é um coletor de lixo que faz uma limpeza periódica no repositório para remover objetos que não possuem nenhuma referência apontando para eles, ou seja, que não pertencem a nenhuma branch.

E existe sim uma maneira de recuperar o commit que foi sobrescrito enquanto ele não foi deletado permanentemente pelo garbage collector. Isso pode ser feito através do comando especial reflog

## É possível alterar um commit que não é o último (mais antigo)?

É possível sim, mas não apenas com o --amend sozinho. Seria preciso utilizá-lo em conjunto com outro comando, que é o git rebase. O git rebase é uma espécie de amend turbinado.

processo seria:

Iniciar o rebase interativo: git rebase -i HEAD~N (onde N é o número de commits que você quer visualizar)
No editor, marcar o commit desejado como edit
Fazer as alterações necessárias
Executar git commit --amend
Finalizar com git rebase --continue

## O --amend serve para corrigir vazamento de dados sensíveis (senhas, tokens)?

Depende se o commit já foi enviado para o repositório remoto ou não.

Se o commit ainda está apenas local (não fez git push): Nesse caso, o --amend resolve sim. Você pode remover os dados sensíveis, fazer o amend e seguir normalmente.

Se o commit já foi enviado para o repositório remoto: O --amend não será suficiente, infelizmente. O git push --force também não resolve completamente, porque pode haver caches, reflogs, clones e forks feitos do repositório. O melhor cenário seria invalidar as chaves de acesso (tokens, etc.) e fazer a rotação delas o quanto antes.

##                                                 > <







