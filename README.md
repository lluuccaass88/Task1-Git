# Task1-Git

Task 1 de do módulo de Git do programa Vem ser DBC

## git rebase

Funcionamento, sintaxe e aplicação do comando git rebase:

O comando git _rebase_ seleciona um grupo de commits (pode ser do branch atual ou entre outro branch e o estado do branch atual) e dá ao usuário algumas opções para fazer a _rebase_ dos commits selecionados. Podemos aplicar o _rebase_ através dos comandos squash, pick, reword, edit, fixup e exec. Detalhe: se já tivermos dado um "push" para o repositório remoto, o comando pode deixar o código embaraçado caso tenham outros colaboradores, pois estaremos alterando o histórico do código.

Sintaxe:
git rebase pick - este comando mostra apenas que o commit está incluído no rebase;
git rebase reword - igual ao pick, mas permite que a troca de base seja pausada para que o usuário possa alterar a mensagem do commit;
git rebase edit - permite alterar o commit antes da troca de base, podendo dividir commits grandes em versões menores;
git rebase squash - combina dois commits, normalmente com o que está acima dele;
git rebase fixup - funciona tal qual o squash, mas descarta a mensagem do log do commit;
git rebase exec - roda o comando usando shell.

O comando git rebase será usado para editar mensagens anteriores do commit, combinar diversos commits em um só, e excluir ou reverter commits desnecessários.

Podemos usar
git rebase --interactive nome-da-outra-branch
para fazer o rebase de todos os commits entre "outra branch" e o estado atual da branch.

usamos também
git rebase --interactive HEAD\~7
para fazer o rebase dos últimos commits da nossa branch atual (no caso seria 7, por conta do dígito após o "~")

## git revert:

O comando git revert é utilizado para reverter as alterações feitas em um determinado commit ou um intervalo de commits, criando um commit que desfaz todas as modificações que você quer corrigir. <br>

Sintaxe: <br>

```
git revert [--[no-]edit] [-n] [-m <parent-number>] [-s] [-S[<keyid>]] <commit>…​
```
```
git revert (--continue | --skip | --abort | --quit)
```

Uso: <br>

Revertendo os ultimos 3 commits:
```
git revert HEAD~3
```
Revertendo commits em um intervalo de commits:
```
git revert -n master~5..master~2
```

Fontes: <br>

[Git Doc](https://git-scm.com/docs/git-revert)
[Dev.to](https://dev.to/womakerscode/tutorial-git-desfazendo-commits-revert-57c2)
[medium](https://medium.com/@mstuttgart/desfazendo-commits-com-git-revert-f569c12fa6a6)

## git-cherry-pick

É comum e saudável que, durante o desenvolvimento, novas features sejam trabalhadas em branches paralelas à branch principal. Contudo, depois de alguns commits em uma dessas braches paralelas, você acaba descobrindo que há um bug na branch principal que precisa ser corrigido. Mas você ainda não concluiu a feature que está desenvolvendo e, se criar um novo commit com a correção e fizer merge com a branch principal, pode acabar quebrando a aplicação. E é aqui que entra o git cherry-pick. A solução é simples: você cria um novo commit na branch paralela com a correção do bug, faz checkout para a main e, utilizando o git cherry-pick, move apenas esse último commit para a branch principal. Dessa forma, você resolve o bug e ainda pode voltar para a branch paralela para finalizar a feature. Vale ressaltar que o git cherry-pick não é uma boa prática. Para resolver esse mesmo problema, utilizar um hotfix seria o ideal.

```
git cherry-pick [id-do-commit]
```

Outras opções que podem ser utilizadas junto com o comando:

-edit: permite que você edite a mensagem do commit

```
-edit
```

--no-commit: move o commit de uma branch para a outra sem gerar um novo commit

```
--no-commit
```

Fontes:<br>
[Git Doc](https://git-scm.com/docs/git-cherry-pick)<br>
[GeekHunter](https://blog.geekhunter.com.br/git-cherry-pick-o-que-e-quando-usar)<br>
[GeeksForGeeks](https://www.geeksforgeeks.org/git-cherry-pick/)<br>
[Atlassian](https://www.atlassian.com/br/git/tutorials/cherry-pick)

## git squash

Quando se utiliza o git rebase -i, há duas opções que condensam um grupo de commits em apenas um, sendo elas a squash e a fixup. A principal diferença entre as duas está no fato de que a squash guardará um histórico de que essa operação foi realizada. Ao realizar o comando

```
git rebase -i
```

será apresentada uma lista dos commits. No início de todos constará a palavra "pick". Para realizar o squash, basta substituir "pick" por "squash" em todos os commits que serão condensados. Um dos commits deve permanecer como "pick", pois os demais serão condensados nele.

Fontes:<br>
[Git Doc](https://git-scm.com/docs/git-rebase)<br>
[Medium - Daniel Faccini](https://medium.com/cwi-software/utilizando-rebase-e-squash-para-melhorar-o-hist%C3%B3rico-do-git-fdb2d952c09c)<br>
[Novatics - Vitor Ribeiro](https://blog.novatics.com.br/como-fazer-um-git-squash-para-melhorar-seu-hist%C3%B3rico-de-commits-2a93835bfe8f)
