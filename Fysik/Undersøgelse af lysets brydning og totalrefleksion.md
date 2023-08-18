*Af: Victor Østergaard Nielsen 2di*


## Teori
### Snell's lov
$$
\frac{\sin(i)}{\sin(b)}=\frac{n_2}{n_1}
$$
## Forsøgsopstilling
![[Pasted image 20230818094421.png]]
![[Pasted image 20230818094737.png]]
## Fremgangsmåde og resultater 
- Forsøgsopstillingen opsat
- Laserlys påføres til glashalvcirklen
- Ingangs og brydningsvinklen afmåles
- Snell's lov bruges til udregning af brydningsindekset, det gøres således i Maple:
$$
n_1:=solve\biggr(\frac{\sin(40°)}{\sin(70°)}=\frac{1}{n_1}\biggr)≈1,4618
$$
- vi løser for $n_1$ og beregner brydningsindekset af glashalvcirklen til ca. *1,4619*
- for at bestemme den kritiske vinkel for totalrefleksion $i_c$ kan vi bruge variablen $n_1$ fra tidligere til netop dette:
$$
i_c:=solve\biggr(\frac{\sin(i)}{\sin(90°)}=\frac{n_2}{n_1}\biggr)≈43.1602°
$$
- vi løser for $i_c$ og beregner den kritiske vinkel for totalrefleksion $i_c$ til ca. *43.1602°*