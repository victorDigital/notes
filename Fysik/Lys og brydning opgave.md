## a) Beregn lysets fart i glasset. 
vi kender formlen:
$$
v=\frac{c[m/s]}{n}
$$
der fremgår derfor at:
$$
\frac{3,00\cdot10^8m/s}{1,5}=v
$$
ved beregning har vi tilnærmet os at lysets hastighed igennem glasset er ca. $2\cdot10^8 m/s$


## b) Beregn grænsevinklen for brydning fra glas til luft. 

$$
i_c:=solve\biggr(\frac{\sin(i)}{\sin(90°)}=\frac{1}{1.5}\biggr)≈41.81°
$$

## c) Se på brydning fra glas til luft. Beregn brydningsvinklen for indfaldsvinklen i = 36,4°. 
Snell's lov bruges til udregning af brydningsindekset, det gøres således i Maple:
$$
b:=solve\biggr(\frac{\sin(36.4°)}{\sin(b)}=\frac{1}{1.5}\biggr)≈62.889°
$$

## d) Se på brydning fra luft til glas. Beregn brydningsvinklen for indfaldsvinklen i = 36,4°. 
$$
i:=solve\biggr(\frac{\sin(36.4°)}{\sin(b)}=\frac{1.5}{1}\biggr)≈23.30
$$

## e) Kan der være totalrefleksion for lys, der falder ind mod en glasoverflade fra luft?
brydnings indekset skal altid gå fra højre til lavere