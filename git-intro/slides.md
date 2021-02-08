---
size: 4:3
marp: true
theme: uncover
style: | 
/* @theme uncover */
blockquote {
    font-size: 20px;
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
### Moge sledzic moja(mojego zespolu) historię pracy z plikiem

![Git history](git-intro/history.png "Git history")

---
Co tu widzimy?

- commit - hash
- (HEAD -> master) *** wyjaśnimy pózniej
- kto 
- kiedy
- opis
---
### Gdyby to bylo za malo
![Git history](git-intro/show.png "Git history")
<p style="display: none;">show_output.txt</p>

\pagebreak
## A co to znaczy rozproszony? 

- każdy uzytkownik moze posiadac wszstkie zmiany
- mozna wprowadzac zmiany bez wysylania ich na serwer

## I jakie sa rodzaje

- lokalne
- scentralizowane 
- rozproszone

\pagebreak
## Co jest potrzebne aby pracować z gitem?

\pagebreak
### Lokalnie?

* klient gita

\pagebreak
### Klienci git

- interfejs tekstowy
- [interfejs graficzny](https://dev.to/theme_selection/best-git-gui-clients-for-developers-5023)

\pagebreak
### W wersji rozproszonej

* serwer git
   
* dostep do usługi git
    - github
    - bitbucket
    - gitlab
    
## Pierwsze kroki

```shell script
git init
```




\pagebreak
## Bibliografia

- https://pl.wikipedia.org/wiki/Git_(oprogramowanie)
- https://git-scm.com/book/pl/v2/Pierwsze-kroki-Podstawy-Git
- https://dev.to/theme_selection/best-git-gui-clients-for-developers-5023