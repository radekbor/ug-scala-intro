---
size: 4:3
marp: true
theme: uncover
style: | 
/* @theme uncover */
blockquote {
    font-size: 20px;
} 
img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
---
# GIT INTRO

Radoslaw Borowiecki

scalac 

----
## Co to jest git?

### Wikipedia

> Git – rozproszony system kontroli wersji. Stworzył go Linus Torvalds jako narzędzie wspomagające rozwój jądra Linux. Git stanowi wolne oprogramowanie i został opublikowany na licencji GNU GPL w wersji 2.
Pierwsza wersja narzędzia Git została wydana 7 kwietnia 2005 roku, by zastąpić poprzednio używany w rozwoju Linuksa, niebędący wolnym oprogramowaniem, system kontroli wersji BitKeeper 

----
## Co to jest system kontroli wersji?

Oprogramowanie zlużacze do zledzenia zmian w kodzie zrodlowym.

---
## Co to znaczy dla programisty/uzytkownika?

---
### Moge sledzic moja(mojego zespolu) historię pracy z plikiem, `git log`

```shell
commit fcf6673b4d6441ede94dbecd0c3c3dea7dd5d467 (HEAD -> MyBranch, origin/MyBranch)
Author: Radoslaw Borowiecki <radoslaw.borowiecki@gmail.com>
Date:   Fri Mar 19 20:53:22 2021 +0100

    Serialize properly create ledger, using fixed to_camle method

```

Co tu widzimy?

- commit - hash
- (HEAD -> master) *** wyjaśnimy pózniej
- kto 
- kiedy
- opis

---

### Gdyby to bylo za malo, `git show hash` 
```shell
commit fcf6673b4d6441ede94dbecd0c3c3dea7dd5d467 (HEAD -> MyBranch, origin/MyBranch)
Author: Radoslaw Borowiecki <radoslaw.borowiecki@gmail.com>
Date:   Fri Mar 19 20:53:22 2021 +0100

    Serialize properly create ledger, using fixed to_camle method

diff --git a/app/pysga/command/ledger.py b/app/pysga/command/ledger.py
index f610b1a..6312c26 100644
--- a/app/pysga/command/ledger.py
+++ b/app/pysga/command/ledger.py
@@ -9,7 +9,11 @@ from ..engine import Command
 
 
 def to_camel(string: str) -> str:
-    return "".join(word.capitalize() for word in string.split("_"))
+    capitalized = "".join(
+        word.capitalize() if i > 0 else word.lower()
+        for i, word in enumerate(string.split("_"))
+    )
+    return capitalized
 
 
:

```

----
## A co to znaczy rozproszony? 

- każdy uzytkownik moze posiadac wszstkie zmiany
- mozna wprowadzac zmiany bez wysylania ich na serwer

---
## I jakie sa rodzaje

- lokalne
- scentralizowane 
- rozproszone

---
## Co jest potrzebne aby pracować z gitem?

---
### Lokalnie?

* klient gita

---
### Klienci git

- interfejs tekstowy
- [interfejs graficzny](https://dev.to/theme_selection/best-git-gui-clients-for-developers-5023)

---
### W wersji rozproszonej

* serwer git
   
* dostep do usługi git
    - github
    - bitbucket
    - gitlab

---
## Pierwsze kroki

```shell script
git init
```

---
## Wypychanie zmian na serwer na przykładzie github.com

---
![](https://github.com/radekbor/ug-scala-intro/blob/master/git-intro/github-1.png?raw=true "Create git repo")

---
![50% center](https://github.com/radekbor/ug-scala-intro/blob/master/git-intro/github-2.png?raw=true "Push to repo")

---


## Co to jest branch? Do czego służy


> Rozgałęzienie oznacza odbicie od głównego pnia linii rozwoju i kontynuację pracy bez wprowadzania tam bałaganu.

```shell
git checkout -b <branch>
```

---

## Rejestracja zmian

Po dokonaniu zmian w naszym projekcie należy je dodać przechowalni (stage)
```shell
git add <plik/folder/wzorzec>
```

Nastepnie należy zapisać migawkę
```shell
git commit 
```
lub
```shell
git commit -m <wiadomosc>
```

---
## Publikowanie zmain

W celu publikacji zmian należy użyć komendy 
```shell
git push <server> <branch>
```

---
## Ale co dalej z ta gałęzią?

W tym celu należ użyć scalania (komenda merge).

Czyli zaaplikowanie zmian z jednej gałęzi do drugiej 

---

## Rodzaje mergowania

- Fast forward
- Recursive
- Ours
- Octopus
- Resolve
- Subtree

TODO doczytac

---
## Konflikty

Pojawiają się wtedy, gdy zostały zmienione te same linijki kodu w na dwóch gałeziach.

TODO obrazek

---

## Jak to zrobić szybko i wygodnie?

- Na rynku istnieje wiele narzedzi graficznych ktore pozwalają rozwiązać konflikty.

--- 
## Intelij

![](https://blog.jetbrains.com/wp-content/uploads/2016/10/idea-idea_2016_3_vcs_magic_resolve.png)

---
## Github

Github dodał możliwość rozwiązywanie konflików na stronie
https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-on-github

---
## Korzystanie z zmian

W celu skorzystania ze zmian będących na innej gałęzi należy się sciągnać zmiany z serwera

```shell
git fetch
```
Następnie zaaplikować te zmiany przy użycia komendy merge.
Istnieje tez komenda pozwalająca wykonać te dwie komendy za jendnym razem
```shell
git pull <server> <branch>
```

--- 
## Rabasing

Jest to sposob scalania zmian z taki że lokalne zmiany bedą zapplikowane nad tymi z drugiego brancha.
Najpopularniejszy sposob na korzystanie z rebasingu

```shell
git pull origin master --rebase
```

---
## A co z plikami wyjsciowymi lub innymi?

W celu oznaczenia, że jakiś plik lub katalg nie jest istotny należy dodac wzorzec do pliku `.gitignore`, gdy plik nie istnieje należy go stworzyc.

```.gitignore
# Created by Jayesh J.

*.log
*.iml
*.ipr
*.iws
.idea
target/
```

Wiecej o wzorcach:
https://git-scm.com/docs/gitignore


---
## Workflow 

Jest to okreslony sposob pracy z gałęziami gita, możemy sie spotkać z gałęziami

- master
- develop
- feature
- release
- hotfix

--- 
## Znane workflowy

- [GitFlow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)
- [Github](https://guides.github.com/introduction/flow)
- [GitLab](https://docs.gitlab.com/ee/topics/gitlab_flow.html)

---

---
## Źródła

- https://pl.wikipedia.org/wiki/Git_(oprogramowanie)
- https://git-scm.com/book/pl/v2/Pierwsze-kroki-Podstawy-Git
- https://git-scm.com/docs/gitignore
- https://dev.to/theme_selection/best-git-gui-clients-for-developers-5023
- https://blog.jetbrains.com
- https://docs.github.com
- https://www.atlassian.com/git/tutorials/comparing-workflows
- https://nvie.com/posts/a-successful-git-branching-model/