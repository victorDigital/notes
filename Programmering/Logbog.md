[[L 2di Pro]]
# Programmerings logbog
_Skrevet i Obsidian.md og hostes af GitHub_
[link til hjemmeside](https://prog2di.github.io/)

## Logbog-opgave 1: Opret jeres logbog

_I skal nu oprette en logbog (i bestemmer selv hvordan). Kravet er at det skal være et online dokument eller lignende, som der skal være tilgængeligt for mig i resten af jeres studietid.
Når i har oprettet jeres logbog skal i aflevere et dokument, med et link til logbogen, i den dertilhørende aflevering på lectio._

ja, det lader til at funke ✨


## Logbog-opgave 2: Spørgsmål til walking creature

I skal åbne jeres logbog og skriv svaret på følgende spørgsmål, relateret til “walking cerature” afleveringen:

- hvad bruger man semikolonner til i processing?
	- afslutte en linje eller separere instruktioner 
- hvad er datatyper og hvilke datatyper kender du?
	- En data type en forskellige måder at opbevare data på bruges til forskellige typer af data. Der findes bl.a.: int, float, bool, double, "String", char.  
- hvordan opretter man en variabel?
	- det kan generelt gøres således `[datatype] [variablens navn] = [værdi];` her er et eksempel `float b = 12.1;`
- hvilke datatyper anvendte du i din kode og hvorfor?
	- Jeg arbejdede med hele tal, af den grund brugte jeg `int` til alt bortsøt fra teksten i taleboblen hvor jeg brugte `String`. 
- hvad betyder “parametre” og “argumenter” i prgrammering, og hvornår anvender du dem i din kode?
	- parametre bruges når en funktion defineres, argumenter bruges når funktionen kaldes
- hvor har du brugt curly brackets (krølleparanteser) i din kode,- og hvilken betydning har de?
	- bruges til af definerer sub-rutiner i koden
- i programmering taler man om “variabel-scope” , prøv at se om du kan finde svaret på hvad det betyder og om det betyder noget i din kode?
	- variabel-scope bruges til at holde styr på variable i sub-rutiner eller funktioner, dvs. hvis en variabel er defineret i en funktion er den kun tilgængelig i funktionen, den er altså en "lokal variable", det er i modsætning til en "global variable" 


## Spørgsmål til creature aflevering
- hvor anvendes argumenter og parametre?
	-  parametre bruges når en funktion defineres, argumenter bruges når funktionen kaldes
- hvor anvender du primitive datatyper - og hvor anvender du objekt-typer? Og hvad er forskellen?
	- i min bruges objekt-typen "String" til at opbevare taleboblens tekst, hvor mine andre variabler bruger datatypen `int` som er en primitive datatyper

## 18/08/2023
- længden og bredden af en rektangel er henholdsvis 5 og 7. Skriv et program til at beregne arealet og omkredsen af ​​rektanglen.
```java
int længde = 5;
int bredde = 7;

int areal = længde * bredde;
int omkreds = 2 * (længde + bredde);

println("Areal: " + areal);
println("Omkreds: " + omkreds);
```
- skriv et program der beregner omkredsen og arealet af en retvinklet trekant.
```java
int base = 5;
int height = 7;
int hypotenuse = int(sqrt(base*base + height*height)); //Pythagoras 

int area = base * height / 2;
int omkreds = base + height + hypotenuse;

println("Area: " + area);
println("Omkreds: " + omkreds);
```
- skriv et program der tager modulus 10 af frameCount og udskriver frameCount og resultatet. Hvordan fungerer modulus?
```java
void setup() {
  size(400, 100);
  frameRate(10);
}

void draw() {
  background(0);
  int result = frameCount % 10;
  text("frameCount: " + frameCount + ", result: " + result, 20, 20);
}
```
_modulus er resten af en heltals division_
- skriv et program der tager division 100 af frameCount og udskriver frameCount og resultatet. Hvordan fungerer division i dette tilfælde?
```java
void setup() {
  size(400, 100);
  frameRate(10);
}

void draw() {
  background(0);
  int result = frameCount / 100;
  text("frameCount: " + frameCount + ", result: " + result, 20, 20);
}
```
- løs nu de ovenstående spørgsmål ved hjælp af tildelingsoperatorer (f.eks. +=, -=, *=)
__