[[L 2di Pro]]
# Programmerings logbog
_Skrevet i Obsidian.md og hostes af Netlify_
hjemmeside lavet i SvelteKit med Prisim.js. Hjemmesiden kan køre udvalgte scripts kan køres ved brug af processing.js biblioteket
[link til logbog hjemmeside](https://victornielsen.netlify.app/logbog)
[link til forløb hjemmeside](https://prog2di.github.io/)

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
_har anvendt tildelingsoperatorer hvor det giver mening_

## Kodeopgave til logbogen 18/08/2023
*I skal lave et program, der bevæger en firkant hen over skærmen på forskellige måder, uden brug af if-statements, men kun ved brug af **modulus** og **division** af frameCount!*

```java
void setup() {
    clear();
    size(500,500);
    background(0);
}

void draw() {
    stroke(frameCount / 50% 2 * 30 * 100, frameCount / 75 % 2 * 30 * 100, frameCount / 100 % 2 * 30 * 100);
    line(frameCount % width, 10, frameCount % width, 40);
    //istedet for background
    noStroke();
    blurCanvas();
    //firkant tegnes nu, og der kommer et "trace"  
    fill(255);
    rect(frameCount % width,100,4,4);
    fill(255);
    rect(frameCount % width,200 + (frameCount / 50 % 2 * 30),4,4);
    fill(255);
    rect(frameCount % width,300 + (frameCount / 75 % 2 * 30),4,4);
    fill(255);
    rect(frameCount % width,400 + (frameCount / 100 % 2 * 30),4,4);
}

// ikke nødvendigt 
void blurCanvas() {
    if (frameCount % 10 != 0) {
        return;
    }
    loadPixels();
    // Loop through every pixel and set the color of that pixel to the average color of the surrounding pixels.
    for (int x = 1; x < width-1; x++) {
        for (int y = 1; y < height-1; y++ ) {
            float sumRed = 0;
            float sumGreen = 0;
            float sumBlue = 0;
            for (int xoffset = -1; xoffset <= 1; xoffset++) {
                for (int yoffset = -1; yoffset <= 1; yoffset++) {
                    int xpos = x + xoffset;
                    int ypos = y + yoffset;
                    int loc = xpos + ypos * width;
                    color c = pixels[loc];
                    sumRed += red(c);
                    sumGreen += green(c);
                    sumBlue += blue(c);
                }
            }
            int loc = x + y * width;
            color c = color(sumRed/9, sumGreen/9, sumBlue/9);
            //slightly darken all pixels
            c = color(red(c) * 0.999, green(c) * 0.999, blue(c) * 0.999);
            pixels[loc] = c;
        }
    }
    updatePixels();
}
```

det skal siges at `blurCanvas()` og farve striberne ikke er nødvendig for opgaven :)  

## Operatorer
## if-else, relations-operatorer og logiske-operatorer

## Kodeopgaver til logbogen

Løsningen til nedenstående opgaver skal beskrives i jeres logbog.

- I skal i nedenstående opgaver tænke over hvordan i undgår at gentage jer selv “DRY”:  
```java
if (keyPressed == true) {
    if (key == 'a') {
        kSpeed = -kSpeed;
    } else {
        kSpeed = kSpeed;
    }
}
if (keyPressed == true) {
    if (key == 'd') {
        k2Speed = -k2Speed;
    } else {
        k2Speed = k2Speed;
    }
}
if (keyPressed == true) {
    if (key == 'a') {
        color1 = color(0);
    } else {
        color1 = color1;
    }
}

//samme som ovenfor, bare forkortet ved brug af inline conditionel operator

if (keyPressed == true) {
    key == 'a' ? kSpeed = -kSpeed : kSpeed = kSpeed;
    key == 'd' ? k2Speed = -k2Speed : k2Speed = k2Speed;
    key == 'a' ? color1 = color(0) : color1 = color1;
}
```


    
- Det er ikke et krav at anvende et baggrundsbilleder eller billeder i dine programmer. Men hvis du ønsker det, læs da følgende:  
```java
PImage photo;

void setup() {
  size(400, 400);
  photo = loadImage("Toyokawa-city.jpg");
}

void draw() {
  image(photo, 0, 0);
}
```

### 3. del - Kvadrant-opgaven
```java
void setup() {
    size(500, 500);
}

void draw() {
    background(255);
    drawQuadrants();
    fill(0);
    noStroke();
    textSize(100);
    text(determineQuadrant(), 10, 70);
}

void drawQuadrants() {
    stroke(0);
    strokeWeight(2);
    line(0, height / 2, width, height / 2);
    line(width / 2, 0, width / 2, height);
}

int determineQuadrant() {
    int q = 0;
    q = mouseX < width / 2 ? mouseY < height / 2 ? q + 1 : q + 2 : mouseY < height / 2 ? q : q + 3;
    return q + 1;
}
```
## Kodeopgave til logbogen 01/09/2023

- Skriv en for og while-løkke, der udskriver tal fra 1 til 10.
```java
for (int i = 1; i =< 10; i++) {
	println(i);
}
```
- Lav en for og while-løkke, der udskriver de første 5 lige tal (2, 4, 6, osv.).
```java
for (int i = 1; i =< 10; i+=2) {
	println(i);
}
```
- Lav en for og while-løkke, der udskriver summen af tal fra 1 til 100.
```java
for (int i = 1, sum = 0; i <= 100; i++) {
    sum += i; println(sum);
}

```
- Skriv en for og while-løkke, der tæller ned fra 10 til 1 og udskriver tallene.
```java
for (int i = 10; i > 0; i--) {
	println(i);
}
```
- Lav en for og while-løkke, der udskriver gangetabellen for tallet 5 (5, 10, 15, osv. op til 50).
```java
for (int i = 5; i <= 50; i+=5) {
    println(i);
}
```
- Lav en for og while-løkke, der udskriver de første 5 potenser af 2 (2^1, 2^2, 2^3, osv.).
```java
for (int i = 1; i <= 5; i++) {
	println(pow(2, i));
}
```
- Tegn en for og serie af lodrette linjer ved hjælp af en while-løkke, der ændrer deres x-koordinat for hver gentagelse.
```java
for (int x = 0, y = 0;x <= width;x += 10) {
    line(x, y, x, y + 50);
}
```
- Skriv en for og while-løkke, der tegner en spiral ved at ændre både x- og y-koordinaterne for hver gentagelse.
```java
size(500, 500);
background(0);

for (int i = 0; i < 200; i++) {
    float x = width / 2 + i * cos(i / 10.0);
    float y = height / 2 + i * sin(i / 10.0);
    circle(x, y, 10);
}
```
- Lav en for og while-løkke, der tegner en regnbue af farverige linjer ved at ændre farverne gradvist for hver gentagelse.
```java
size(500, 500);
background(0);
for (int i = 0; i < 500; i++) {
    colorMode(HSB);
    stroke(i/2, 255, 255);
    line(i, 0, i, 500);
}
```
- Tegn en for og slags “trappe” ved at bruge en while-løkke til at skabe forskellige brede rektangler ved hvert trin.
```java
size(500,500);
background(0);

int i = 0;
while(i < 50) {
    int j = 0;
    while(j < i) {
        rect(j * 10, i * 10, 10, 10);
        j++;
    }
    i++;
}
```

_lav 10x10 små firkanter i midten af skærmen hvor firkanterne bliver gradvist mere røde nedad og gradvist mere grønne mod højre_

```java
size(500, 500);
background(0);
noStroke();

for (int i = 0; i < 10; i++) {
    for (int j = 0; j < 10; j++) {
        fill(255 * j / 10, 255 * i / 10, 0);
        rect(50 + 40 * i, 50 + 40 * j, 40, 40);
    }
}
```

## Nestede for-loops
### opg_1 
```java
size(500,500);
background(0);

for(int i = 0; i < 50; i++) {
    for(int j = 0; j < 50; j++) {
        circle(i*10+5, j*10+5, 10);
    }
}
```

### opg_2
```java
size(500,500);
background(0);

for(int i = 0; i < 50*50; i++) {
    int x = i % 50;
    int y = i / 50;
    noStroke();
    fill((x+y)%2*255);
    rect(x*10, y*10, 10, 10);
}
```
### opg_3
```java
size(500,500);
background(0);

for(int i = 0; i < 50; i++) {
    for(int j = 0; j < i; j++) {
        stroke(255);
        strokeWeight(1);
        fill(i * 3);
        rect(j * 10, i * 10, 10, 10);
    }
}
```


## Diverse opgaver i arrays
1. Opret et array af heltal med 5 elementer og tildel det værdierne 1, 2, 3, 4 og 5. Udskriv arrayet.
```java
int[] array = new int[5];
for (int i = 0; i < array.length; i++) {
    array[i] = i + 1;
}
println(array);
```
3. Lav et array af strenge, der indeholder navnene på dine yndlingsfarver. Udskriv alle farverne i arrayet.
```java
String[] list = {"gul", "pisgul", "mørkegul"};
for (int i = 0; i < list.length; i++) {
    println(list[i]);
}
```
5. Opret et array af kommatal, der indeholder temperaturen for hver dag i en uge. Beregn gennemsnittet af temperaturerne.
```java
float[] temperaturer = { 30, 20, 14, 16, 19, 23, 30 };
float sum = 0;
for (int i = 0; i < temperaturer.Length; i++) {
    sum += temperaturer[i];
}
println("Gennemsnitet er " + sum / temperaturer.Length);
```
7. Lav et array af boolean-værdier, der repræsenterer tilstanden af ​​10 lamper (tændt/slukket). Skriv en løkke, der tænder alle lamperne. (prøv at se om du kan gøre det grafisk)
```java
size(500, 500);
boolean[] lamper = new boolean[10];
for (int i = 0; i < lamper.length; i++)
{
    lamper[i] = true;
    rect(10 + i * 20, 10, 10, 10);
}
```
9. Byt om på det første og sidste element i et array. (uanset indhold)
```java
boolean[] array = {true, false};
boolean temp = array[0];
array[0] = array[array.length-1];
array[array.length-1] = temp;
println(array[0] + " " + array[1]);
```
11. Opret et array af strenge med navnene på forskellige frugter. Brug en for-løkke til at finde og udskrive indekset (positionen) for den første forekomst af “æble” i arrayet.
```java
String[] frugter = {"æble", "pære", "banan", "æble", "melon", "æble", "kiwi", "æble", "appelsin", "æble"};
for (int i = 0; i < frugter.length; i++) {
    if (frugter[i] == "æble") {
        println(i);
        break;
    }
}
```
13. Opret et array af strenge med navnene på månederne i den korrekte rækkefølge (januar, februar, marts, osv.). Skriv en for-løkke, der bytter om på rækkefølgen, så arrayet nu indeholder månederne i omvendt rækkefølge (december, november, oktober, osv.).
```java
String[] months = {"januar", "februar", "marts", "april", "maj", "juni", "juli", "august", "september", "oktober", "november", "december"};
for (int i = 0; i < 12; i++) {
  String temp = months[i];
  months[i] = months[11-i];
  months[11-i] = temp;
}
for (int i = 0; i < 12; i++) {
  println(months[i]);
}
```

## Flerdimensionelle arrays opgaver
1. Opret en 3x3 matrix og find værdien i midten (anden række, anden kolonne).
```java
int[][] liste = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

println(liste[1][1]);
```

3. Opret en 2D matrix med 3 rækker og 4 kolonner, fyld den med tilfældige tal og beregn summen af hver række. Udskriv resultaterne.
```java
int[][] liste = new int[3][4];

for (int i = 0; i < liste.length; i++) {
    for (int j = 0; j < liste[i].length; j++) {
        liste[i][j] = (int) (Math.random() * 100);
    }
}

//sum
for (int i = 0; i < liste.length; i++) {
    int sum = 0;
    for (int j = 0; j < liste[i].length; j++) {
        sum += liste[i][j];
    }
    println("Summen af række " + i + " er " + sum);
}
```

1. Opret en 2D matrix, og transponer den, dvs. skift rækker og kolonner. Udskriv både den oprindelige og transponerede matrix
```java
int[][] matrix = {
  {1, 2, 3},
  {4, 5, 6},
  {7, 8, 9}
};

//transponer matrix
int[][] transponeredeMatrix = new int[matrix[0].length][matrix.length];
for (int i = 0; i < matrix.length; i++) {
  for (int j = 0; j < matrix[0].length; j++) {
    transponeredeMatrix[j][i] = matrix[i][j];
  }
}

//udskriv
for (int i = 0; i < matrix.length; i++) {
  for (int j = 0; j < matrix[0].length; j++) {
    print(matrix[i][j] + " ");
  }
  println();
}

println();

for (int i = 0; i < transponeredeMatrix.length; i++) {
  for (int j = 0; j < transponeredeMatrix[0].length; j++) {
    print(transponeredeMatrix[i][j] + " ");
  }
  println();
}
```

1. Opret to 2D matricer og find en metode der kan sammenligne om de har ens indhold
```java
int[][] matrix1 = {
    {1, 2, 3} ,
    {4, 5, 6} ,
    {7, 8, 9}
};

int[][] matrix2 = {
    {2, 2, 3} ,
    {6, 5, 7} ,
    {7, 8, 6}
};

if (matrix1.length != matrix2.length || matrix1[0].length != matrix2[0].length) {
    println("The matrices cannot be compared.");
    System.exit(1);
}

for (int i = 0; i < matrix1.length; i++) {
    for (int j = 0; j < matrix1[0].length; j++) {
        print(matrix1[i][j] == matrix2[i][j] ? "T " : "F ");
    }
    println();
}
```

1. Skriv program der kan multiplicere to matricer
```java
int[][] matrix1 = {
    {1, 2},
    {4, 5}
};

int[][] matrix2 = {
    {2, 8},
    {5, 5}
};

int[][] result = new int[matrix1.length][matrix2[0].length];

for (int i = 0; i < result.length; i++) {
    for (int j = 0; j < result[0].length; j++) {
        // k er lig kollonner i matrix1 og rækker i matrix2 jeg jeg under 2 hjerneceller tilbage
        for (int k = 0; k < matrix1[0].length; k++) {
            result[i][j] += matrix1[i][k] * matrix2[k][j];
        }
    }
}

// Display result
for (int i = 0; i < result.length; i++) {
    for (int j = 0; j < result[0].length; j++) {
        print(result[i][j] + " ");
    }
    println();
}
```
## Opgaver i funktioner
1. Hvad bruges krølle-parenteser til i en funktion (og hvad bruges krølle-parenteser til generelt…)
Krølle-parenteser bruges til at definere en funktion, og til at definere sub-rutiner i koden

2. Hvad anvendes almindelige parenteser til i en funktion
Parenteser bruges til at definere parametre i en funktion


3. Hvad betyder “returtype” og hvor skrives den i en funktion
Returtype er den type data som funktionen returnere, den skrives før funktionens navn F.eks. `int funktion() { ... }`

4. Hvad er forskellen på argumenter og parametre
Parametre bruges når en funktion defineres, argumenter bruges når funktionen kaldes

5. Hvornår er det smart at bruge funktioner
funktioner er brugbare når der er brug for at gentage en bestemt opgave flere gange, eller når der er brug for at opdele koden i mindre dele

6. Hvad betyder “return” og hvordan anvendes det
return bruges til at returnere en værdi fra en funktion, f.eks. `return 5;`. Dog skal denne værdi være af samme type som funktionens returtype

7. Hvad betyder “void” og hvordan anvendes det
void betyder at funktionen ikke returnere noget, f.eks. `void funktion() { ... }`

8. Lav en funktion med navnet “udskriv10”, der kan udskrive 10-tabellen.
```java
void udskriv10() {
    for (int i = 1; i <= 10; i++) {
        println(i * 10);
    }
}
```

9.  Lav en funktion med navnet “gangMed10”, der modtager et tal som parameter og returnere tallet multipliceret med 10
```java
// denne funktion returnere kun hele tal (int) da funktionen kun tager imod hele tal i parameteren tal 
int gangMed10(int tal) {
    return tal * 10;
}
```
10. Lav en funktion med navnet “udskrivTabel”, der modtager et tal og udskriver de første 10 tal af den tabel, der svarer til inputtet
```java
void udskrivTabel(int tal) {
    for (int i = 1; i <= 10; i++) {
        println(i * tal);
    }
}
```
11. Lav en funktion “mult”, der modtager to tal som parametre, og returnere resultatet som er de to tal ganget sammen
```java
int mult(int tal1, int tal2) {
    return tal1 * tal2;
}
```
12. Lav en ny funktion med samme navn “mult”, der modtager tre tal som parametre. Den nye funktion skal anvende funktionen fra spørgsmål 2 til at gange 3 tal sammen
```java
int mult3(int tal1, int tal2, int tal3) {
    return mult(tal1, tal2) * tal3;
}
```
13. (frivillig) Hvad betyder rekursion - prøv at slå det op
rekursion er når en funktion kalder sig selv, f.eks. `void funktion() { funktion(); }` dette er et eksempel på en uendelig løkke som vil resultere i et crash af systemet :(
1.  (frivillig) Give et eksempel på en funktion, der anvender rekursion. Funktionen skal modtage et tal som parameter og returnere fakultet af tallet. F.eks. beregnes fakultet af 5 således 5! = 5x4x3x2x1
```java
int fakultet(int tal) {
    if (tal == 1) {
        return 1;
    }
    return tal * fakultet(tal - 1);
}
```

## Opgaver:

1. Arbejde med Primitiver: Opret to variabler af typen int og tildel dem samme værdi. Prøv at ændre værdien af den ene variabel og se, hvordan det påvirker den anden.
```java	
int a = 5;
int b = a;
a = 10;
println(b); // b er stadig 5
```
2. Arbejde med Primitiv Arrays: Opret et primitivt array, f.eks. int[], og tildel det til en anden reference. Prøv at ændre værdierne i det originale array og se, om det påvirker den anden reference.
```java
int[] a = {1, 2, 3};
int[] b = a;
a[0] = 10;
println(b[0]); // b[0] er nu 10
```
3. Arbejde med Arrays: Opret et array af strenge og tildel det til en anden reference. Fjern eller tilføj elementer til det originale array og se, hvordan det påvirker den anden reference.
```java
String[] a = {"a", "b", "c"};
String[] b = a;
a[0] = "d";
println(b[0]); // b[0] er nu "d"
```


## Meget svære opgaver i funktioner
1. Lav en rekursiv funktion “int fib(int t)” der kan retunere et bestemt tal i fibonacci-talrækken. F.eks. fib(6) = 5 og fib(8) = 13.  
    https://da.wikipedia.org/wiki/Fibonacci-tal  
    https://en.wikipedia.org/wiki/Recursion
```java
int fib(int t) {
    if (t == 0) {
        return 0;
    }
    if (t == 1) {
        return 1;
    }
    return fib(t - 1) + fib(t - 2);
}
```

2. Lav en anden funktion, som vha. “fib” tegner følgende mønster:  
    https://da.wikipedia.org/wiki/Fibonacci-tal#/media/Fil:FibonacciBlocks.svg
```java

int fib(int t) {
    if (t == 0) {
        return 0;
    }
    if (t == 1) {
        return 1;
    }
    return fib(t - 1) + fib(t - 2);
}
void setup() {
    size(500, 500);
    background(0);
    stroke(255);
    strokeWeight(2);
    noFill();
    translate(250, 250);

    
    for(int i = 0; i < 15 ; i++) {
        rect(0,0,fib(i),fib(i));
        rotate(radians(90));
        translate(-fib(i)*0.61803398875,0);
    }
}
```
NOTE: 0.61803398875 er den gyldne ratio -1 (jeg startede med at approksimere denne værdi før jeg kiggede på Wikipedia 🤠 som var klogere end mig)

## Opgaver
### Opgave 2.1 : Largest number
```java
void setup(){
	//fejrnelse af en enkelt char
	println(removeNr("3412",1));//udskriver strengen 312
	println(removeNr("4990",3));//udskriver strengen 499
	println(removeNr("8193",2));//udskriver strengen 813
  
	//opnåelse af størst mulige tal ved at fjernelse af et enkelt ciffer
	println(largest(3412));     //udskriver 412
	println(largest(4990));     //udskriver 990
	println(largest(8193));     //udskriver 893
}

String removeNr(String s, int i){
	return s.substring(0,i)+s.substring(i+1);
}

int largest(int n){
	String s = str(n);
	int max = 0;
	for(int i=0;i<s.length();i++){
	    int nr = int(removeNr(s,i));
	    if(nr>max) max = nr;
	}
	return max;
}
```

### Opgave 2.2 : Count in string
```java
void setup(){
    println(countChar("abcdahahaah",'a')); //udskriver 5
    println(countChar("abcdahahaah",'h')); //udskriver 3
    println(countChar("abcdahahaah",'d')); //udskriver 1
}

int countChar(String s, char c) {
    int count = 0;
    for (int i = 0; i < s.length(); i++) {
        if (s.charAt(i) == c) count++;
    }
    return count;
}
```

### Opgave 2.3 - Beauty factor
```java
void setup(){
  //Beregner sum af cifre i et tal
  println(beautifyOnce(123)); //udskriver tallet 6,  da 1+2+3=6
  println(beautifyOnce(234)); //udskriver tallet 9,  da 2+3+4=9
  println(beautifyOnce(444)); //udskriver tallet 12, da 4+4+4=12

  //Beregner "beauty factor" ...
  println(beautyFactor(444)); //udskriver tallet 3, da 4+4+4=12,og 1+2=3
  println(beautyFactor(1987));//udskriver tallet 7, da 1+9+8+7=25, og 2+5=7
}

int beautifyOnce(int x) {
    String s = str(x);
    int sum = 0;
    for(int i = 0 ; i < s.length() ; i++) {
        sum += int(s.charAt(i) - '0'); //processing forum siger at man skal minus '0' for at få det rigtige tal IDK (HELP ME)
    }
    return sum;
}

int beautyFactor(int x) {
    int sum = beautifyOnce(x);
    while(sum >= 10) {
        sum = beautifyOnce(sum);
    }
    return sum;
}
```

### Opgave 2.4 - min max
```java
void setup() {
    int[] list1 = {1,2,3,5,6};
    int[] list2 = {9,8,7,6,5};
    int[] list3 = {1,1,4,3,2};
    int[] list4 = {1,1,0,0,9};
    
    //Indeholder et array et bestemt tal?
    println(contains(list1,1));  //udskriver true,  da 1 er i arrayet
    println(contains(list2,2));  //udskriver false, da 2 ikke er i arrayet
    println(contains(list3,3));  //udskriver true,  da 3 er i arrayet
    println(contains(list4,4));  //udskriver false, da 4 ikke er i arrayet
    
    //Eksisterer alle tal imellem min og max?
    println(min_max(list1)); //udskriver NO , max=6 og min=1, og 4, der ligger imellem 1 og 6 mangler! 
    println(min_max(list2)); //udskriver YES, max=9 og min=5, og alle tal imellem 9 og 5 er i arrayet
    println(min_max(list3)); //udskriver YES, max=4 og min=1, og alle tal imellem 1 og 4 er i arrayet
    println(min_max(list4)); //udskriver NO , max=9 og min=0, og 2,3,4,5,6,7,8 mangler
}

boolean contains(int[] list, int number) {
    for (int i = 0; i < list.length; i++) {
        if (list[i] ==  number) {
            returntrue;
        }
	}
return false;
}

String min_max(int[] list) {
    int min = list[0];
    int max = list[0];
    for (int i = 0; i < list.length; i++) {
        if (list[i] < min) {
            min = list[i];
        }
        if (list[i] > max) {
            max = list[i];
        }
	}
    for (int i = min + 1; i < max; i++) {
        if (!contains(list,i)) {
            return"NO";
        }
	}
    return "YES";
}
```

## Opgave til logbog

Se følgende tre videoer, der introducerer oop. Efter hver video skal i svare på spørgsmålene nedenfor og skrive udførlige svar i jeres log-bog.

Video 1: [https://youtu.be/YcbcfkLzgvs](https://youtu.be/YcbcfkLzgvs)

- Forklar hvad der menes med “class”
	- en "class" eller klasse kan forklares som en sammensætning af både data, funktioner og andet, pakket sammen i en klasse og bruges som helhed i programmet.
- Forklar hvad der menes med “object”
	- et objekt er blot et eksemplar på denne klasse, oprettes med `new` keyword

Video 2: [https://youtu.be/lmgcMPRa1qw](https://youtu.be/lmgcMPRa1qw)

- Forklar hvordan og hvorfor man anvender “new”
	- bruges når vi skal instansiere en klasse til et objekt. 
- Forklar hvad er “dot-syntax”
	- hvis vi f.eks. har defineret variablen `s` man en datatype `Skib` som har melodeon `sejl()`. Så kan vi anvende denne metode ved brug at dot-syntax således: `s.sejl();` her fortæller vi altså objektet (skibet) `s` til at sejle.   

Video 3: [https://youtu.be/XwfOVFelLoo](https://youtu.be/XwfOVFelLoo)

- Hvad er en “constructor”
	- en constructor bruges når et objekt skal konstrueres, altså der definereres nogle parameter i en constructor som efterfølgende kan blivet givet som argumenter når et objekt skal konstrueres, noget som start position f.eks.

## Kode-opgave - array af bubbles

Nu med farve og kollision med væggene! de kan også hoppe i alle retninger fordi vi befinder os på månen!!!

```java
ArrayList<Ball> balls = new ArrayList<Ball>();

void setup() {
    size(500, 500);
    for (int i = 0; i < 10; i++) {
        balls.add(new Ball(random(width), random(height), random(-5, 5), random(-5, 5), random(10, 50), color(random(255), random(255), random(255))));
    }
}

void draw() {
    background(0);
    for (Ball ball : balls) {
        ball.move();
        ball.display();
    }
}


class Ball {
    float x, y, speedX, speedY, size;
    color c;

    Ball(float x, float y, float speedX, float speedY, float size, color c) {
        this.x = x;
        this.y = y;
        this.speedX = speedX;
        this.speedY = speedY;
        this.size = size;
        this.c = c;
    }

    void move() {
        x += speedX;
        y += speedY;
        if (x < 0 || x > width) {
            speedX *= -1;
        }
        if (y < 0 || y > height) {
            speedY *= -1;
        }
    }

    void display() {
        fill(c);
        ellipse(x, y, size, size);
    }
}

void mousePressed() {
    //add a ball at the mouse position
    balls.add(new Ball(mouseX, mouseY, random(-5, 5), random(-5, 5), random(10, 50), color(random(255), random(255), random(255))));
}
```


## Kode opgave OOP del 2
```java
Btn plusknap = new Btn(10, 100, 100, 20, "plus");
Btn minusknap = new Btn(10, 130, 100, 20, "minus");
Btn resetknap = new Btn(10, 160, 100, 20, "reset");

Bar bar = new Bar(130, 100, 200, 20, 0, 0, 100);

void setup() {
    size(400,400);
    background(0);
    noStroke();
}

void draw() {
    background(0);

    if (mousePressed) {
        if (plusknap.clicked()) {
            bar.change(3);
        }
        if (minusknap.clicked()) {
            bar.change(-3);
        }
        if (resetknap.clicked()) {
            bar.reset();
        }
    }

    plusknap.draw();
    minusknap.draw();
    resetknap.draw();

    bar.draw();
}

void mouseReleased() {
    plusknap.btnClicked = false;
    minusknap.btnClicked = false;
    resetknap.btnClicked = false;
}



class Btn {
    float x;
    float y;
    float w;
    float h;
    float targetColor = 255;
    float actualColor = 255;
    String text;
    boolean btnClicked = false; //internal state

    Btn(float _x, float _y, float _w, float _h, String _text) {
        x = _x;
        y = _y;
        w = _w;
        h = _h;
        text = _text;
    }

    void draw() {
        if (btnClicked) {
            targetColor = 50;
        } else {
            targetColor = 255;
        }
        actualColor += (targetColor - actualColor) * 0.3;
        fill(actualColor);
        rect(x, y, w, h, 5);
        fill(0);
        textAlign(CENTER, CENTER);
        textSize(20);
        text(text, x + w / 2, y + h / 2);
    }

    boolean clicked() {
        if (mouseX > x && mouseX < x + w && mouseY > y && mouseY < y + h) {
            btnClicked = true;
            return true;
        } else {
            btnClicked = false;
            return false;
        }
    }
}

class Bar {
    float x;
    float y;
    float w;
    float h;
    float targetValue;
    float value;
    float min;
    float max;

    Bar(float _x, float _y, float _w, float _h, float _targetValue, float _min, float _max) {
        x = _x;
        y = _y;
        w = _w;
        h = _h;
        targetValue = _targetValue;
        min = _min;
        max = _max;
    }

    void draw() {
        stroke(255);
        strokeWeight(2);
        noFill();
        rect(x-1, y-1, w+1, h+1, 5); //outline
        noStroke();
        fill(255);
        value += (targetValue - value) * 0.1;
        rect(x, y, map(value, min, max, 0, w), h, 5);
    }

    void change(float amount) {
        targetValue += amount;
        targetValue = constrain(targetValue, min, max);
    }

    void reset() {
        targetValue = 0;
    }
}
```

## Raket opgave 20/11/23
```java
PImage img;

Knap upKnap;
Knap downKnap;
Knap rightKnap;
Knap leftKnap;

Ship ship;
Ship ship2;

void setup() {
    size(400, 400);
    background(0);
    
    upKnap = new Knap(50, 100, "up");
    downKnap = new Knap(50, 160, "down");
    rightKnap = new Knap(90, 130, "right");
    leftKnap = new Knap(10, 130, "left");

    img = loadImage("rocket.png");
    
    ship = new Ship(200, 200);
    ship2 = new Ship(100, 100);
}

void draw() {
    background(0);
    upKnap.display();
    downKnap.display();
    rightKnap.display();
    leftKnap.display();
    upKnap.mouseDown();
    downKnap.mouseDown();
    rightKnap.mouseDown();
    leftKnap.mouseDown();
    ship.draw();
    ship2.draw();
    ship.select();
    ship2.select();
}

void mouseReleased() {
    upKnap.mouseUp();
    downKnap.mouseUp();
    rightKnap.mouseUp();
    leftKnap.mouseUp();
}

void up() {
    ship.move(0, -1);
    ship2.move(0, -1);
}

void down() {
    ship.move(0, 1);
    ship2.move(0, 1);
}

void right() {
    ship.move(1, 0);
    ship2.move(1, 0);
}

void left() {
    ship.move(-1, 0);
    ship2.move(-1, 0);
}

class Knap {
    String action;
    boolean clicked;
    int x, y, w = 30, h = 30;

    Knap(int x, int y, String a) {
        action = a;
        this.x = x;
        this.y = y;
    }

    void mouseDown() {
        if (mouseX > x && mouseX < x + w && mouseY > y && mouseY < y + h && mousePressed) {
            clicked = true;
            method(action);
        }
    }

    void mouseUp() {
        clicked = false;
    }

    void display() {
        if (!clicked) {
            fill(255);
        } else {
            fill(0);
        }
        rect(x, y, w, h);
    }
    
    void method(String action) {
        if (action.equals("up")) {
            up();
        } else if (action.equals("down")) {
            down();
        } else if (action.equals("right")) {
            right();
        } else if (action.equals("left")) {
            left();
        }
    }
}

class Ship {
    float x;
    float y;
    boolean isSelected = false;

    Ship(float _x, float _y) {
        x = _x;
        y = _y;
    }

    void draw() {
        fill(255);
        image(img, x, y, 50, 73);
    }

    void move(int xc, int yc) {
        if (isSelected) {
            x += xc;
            y += yc;
        }
    }

    void select() {
        if (mouseX > x && mouseX < x + 50 && mouseY > y && mouseY < y + 73 && mousePressed) {
            // Deselect the previously selected ship
            ship.deselect();
            ship2.deselect();
            
            // Select the current ship
            isSelected = true;
        }
    }

    void deselect() {
        isSelected = false;
    }
}
```

# Opgaver i funktioner, syntaks og terminologi
## Opgaver i funktions terminologi

- **_Opgave 1:_** Forklar begrebet **_funktion_** i programmering, herunder betydningen af et **_funktionskald_**. Giv et eksempel.
En funktion er en samling af kode, som kan kaldes fra andre steder i programmet.
Et funktionskald er når en funktion bliver kaldt:
```java
minFunktion();
```
- **_Opgave 2:_** Definér **_parametre_**, **_argumenter_** og metode-krop i programmering. Giv et eksempel
En parameter er når en funktion kaldes, og et argument bruges når en funktion defineres og metodes krop er det der står i funktionen.
```java
sum(2, 3); // 2 og 3 er argumenter

int sum(int a, int b) { // a og b er parametre
  return a + b; // return er metode-krop
}
```
- **_Opgave 3:_** Forklar begrebet **_variabel-scope_** i programmering. Og forskellen på **_lokale variable_** og **_globale variable_**. Giv et eksempel
En variable det defineres i en funktion er en lokal variable, og kan kun bruges i den funktion. En global variable kan bruges i hele programmet og den defineres i top-level eller i global scope.

- **_Opgave 4:_** Definér **_returtype_** og **_returværdi_** i programmering.
Returtype er den type værdi, som en funktion returnerer. Returværdien er den værdi, som funktionen returnerer.
## Opgaver i programmering af funktioner

- **_Opgave 5:_** Skab “givHilsen”, en funktion med to inputparametre: en liste af hilsner og et tal, der bestemmer hvilken hilsen der skal returneres.
```java
String givHilsen(String[] hilsner, int index) {
  return hilsner[index];
}
```
- **_Opgave 6:_** Implementer “beregnAreal”, en funktion til at beregne og returnere arealet af en vilkårlig cirkel.
```java
Float beregnAreal(float radius) {
    float areal = radius * radius * PI;
    return areal;
}
```
- **_Opgave 7:_** Skriv en funktion, der kan håndtere et vilkårligt antal punkter og skabe en tegning, der forbinder dem.
```java
void connectPoints(PVector[] points) {
  for (int i = 0; i < points.length-1; i++) {
    line(points[i].x, points[i].y, points[i+1].x, points[i+1].y);
  }
}
```
- **_Opgave 8:_** Frivillig: Udvikl en funktion, der kan tegne en vilkårlig N-kant med et valgfrit centrum.
```java
// tak til https://stackoverflow.com/questions/54639789/how-to-make-a-shape-move-while-keeping-a-shape-static-without-re-rendering-the-s
void polygon(float n, float x, float y, float r) {
    float angle = 2 * PI / n;
    float x1 = x + r * cos(0);
    float y1 = y + r * sin(0);
    for (int i = 1; i <= n; i++) {
        float x2 = x + r * cos(angle * i);
        float y2 = y + r * sin(angle * i);
        line(x1, y1, x2, y2);
        x1 = x2;
        y1 = y2;
    }
}
```