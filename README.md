# Task1-Git
Task 1 de do módulo de Git do programa Vem ser DBC

Funcionamento, sintaxe e aplicação do comando git rebase:

O comando git *rebase* seleciona um grupo de commits (pode ser do branch atual ou entre outro branch e o estado do branch atual) e dá ao usuário algumas opções para fazer a *rebase* dos commits selecionados. Podemos aplicar o *rebase* através dos comandos squash, pick, reword, edit, fixup e exec. Detalhe: se já tivermos dado um "push" para o repositório remoto, o comando pode deixar o código embaraçado caso tenham outros colaboradores, pois estaremos alterando o histórico do código.

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
git rebase --interactive HEAD~7
para fazer o rebase dos últimos commits da nossa branch atual (no caso seria 7, por conta do dígito após o "~")

Funcionamento, sintaxe e aplicação do comando git reverse:
O comando *git reverse* é utilizado para reverter as alterações feitas em um determinado commit ou um intervalo de commits, criando um commit que desfaz todas as modificações que você quer corrigir.

Sintaxe:
git revert [--[no-]edit] [-n] [-m <parent-number>] [-s] [-S[<keyid>]] <commit>…​
git revert (--continue | --skip | --abort | --quit)

Uso: 
Revertendo os ultimos 3 commits:
git revert HEAD~3

Revertendo commits em um intervalo de commits
git revert -n master~5..master~2

