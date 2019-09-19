# PROBLEMA 6

En una festa, un *convidat* es diu que és una *celebritat* si tothom el coneix, però ell no coneix a ningú (tret d’ell mateix). Les relacions de coneixença donen lloc a un graf dirigit: cada *convidat* és un vèrtex, i hi ha un arc entre *u* i *v* si *u* coneix a *v*. Doneu un algorisme que, donat un graf dirigit representat amb una matriu d’adjacència, indica si hi ha o no cap *celebritat*. En el cas que hi sigui, cal dir qui és.
El vostre algorisme ha de funcionar en temps O(n), on n és el nombre de vèrtexs.

```c++
troba_celebritats(convidats):
    descartats = null; // Cua
    for (int i = 0; i < n; i++):
        no_coneix = 0
        if (descartats.front() == i):
            descartats.pop()
            break
    	for (int j = 0; j < n; j++):
            if (convidats[i][j] == 1 and i != j):
                //Saltem perquè si un convidat coneix a algú no és una celebritat.
                break 
            if (convidats[i][j] == 0):
            	no_coneix++;
            	if (no_coneix == n-1):
              		return i;
            	// Descartem perquè si algú no el coneix no pot ser celebritat.
            descartats.push(j); 
	return -1 // No hem trobat cap celebritat.
            
        
```

A cada iteració prenem una decisió, per tant a cada iteració un convidat queda descartat. La *celebritat* es troba un cop s'han descartat la resta de *convidats*, per tant necessitem fer *n* passos per a descobrir qui és la *celebritat*.