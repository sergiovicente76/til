# Corrigir a mensagem de um commit

**Problema:** fiz um commit no GitHub Desktop sem preencher o **Summary**, e ele usou a sugestão genérica `Update README.md`. Na segunda tentativa escrevi a mensagem na **Description**, e o título continuou genérico.

**Aprendizado:** no GitHub Desktop, o **Summary** (campo de cima, uma linha) é o **título** do commit, que aparece no histórico e no GitHub. A **Description** é o corpo, um texto opcional abaixo do título.

## Antes do push: pode corrigir à vontade

**Terminal**
```bash
# troca a mensagem do último commit
git commit --amend -m "docs: inicia módulo de Git e GitHub"

# ou desfaz o commit mantendo as alterações, para commitar de novo
git reset --soft HEAD~1
```

**GitHub Desktop**
- Botão **Undo** logo após o commit (as alterações voltam para *Changes*), ou
- Aba **History** → botão direito no commit → **Amend commit…**

Para saber se o commit já foi enviado:
```bash
git status -sb
# main...origin/main [ahead 1]  → ainda não foi enviado (pode corrigir)
# main...origin/main            → já está no GitHub
```

## Depois do push: em geral, deixe como está

Corrigir exige reescrever o histórico e forçar o envio:
```bash
git commit --amend -m "nova mensagem"
git push --force-with-lease
```
⚠️ Só faça isso em repositório **seu e sem outras pessoas trabalhando nele**. Em repositório compartilhado, isso quebra o histórico dos colegas. `--force-with-lease` é mais seguro que `--force` porque recusa o envio se o remoto tiver commits que você ainda não baixou.

## Boa mensagem de commit
[Conventional Commits](https://www.conventionalcommits.org/pt-br/): `tipo: descrição no imperativo`
- `feat:` nova funcionalidade · `fix:` correção · `docs:` documentação · `chore:` manutenção · `refactor:` refatoração · `test:` testes
- Ex.: `docs: inicia módulo de Git e GitHub`
