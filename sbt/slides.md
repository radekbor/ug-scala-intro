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
# Sbt 

Radoslaw Borowiecki

scalac 

---
## Jaki jest tego cel

Tworząc jakis projekt korzystamy z zależności. W srodowisku jvm są to zazwyczaj są to    pliki jar. Musimy w jakis sposób je dołączyć do projektu.

---
## Przyklad zalezności
![](https://github.com/radekbor/ug-scala-intro/blob/master/sbt/akka-jar.png?raw=true "Akka actor jar")

---
## Jaki jest problem z dołączaniem pliku jar?

- waga
- odtwarzalność
- brak pewnosci, że dana wersja jest poprawna
- aktualizacja wymaga dystrybunowania pliku jar do wszystkich użytkowników

---
## Źródła

