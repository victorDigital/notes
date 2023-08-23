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


# operatorer
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