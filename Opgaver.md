Ændringer til fredag:

Ændrer broadcast i ``basket.ts`` til at selv give category count fremfor at broadcaste det til navbaren.
Ændrer ``basket.ts`` update funktioner til at være get funktioner, så de steder som skal bruge pris og mængden af varer skal kalde en function i stedet.

Ændrer navbaren til ikke have have den ``backbutton``, men i stedet at den ændrer selve knappen som man har trykket på til en ``backbutton``.

Sørg for at navbaren skifter til ingen navbar hvis der er mindre en 2 kategorier.
Sørg for at navbaren skifter til ``topbar`` hvis der er mellem 2-6 kategorier
Sørg for at navbaren skifter til ``sidebar`` hvis der er mellem 6+ kategorier

Ryd op i events så de ligger samlet som f.eks. i ``productItem.ts``, der kan man ligge ``inits`` i toppen som f.eks. events som ``rootscope.on`` og update

Lav en factory som behandler alt data som der skal bruges til menuerne, og til navbaren fremfor at have to forskellige filer som vi har nu.
Kombiner payment options med den.

Færdiggør order detail siden.

Lav overvejelser til resource keys til en fuld angular løsning til hvis man skal gøre siden 2 sproget.

Ændrer JSON data til at være consistent, ingen duplicate ID'er og ingen forkerte categories.
Giv JSON data en path til nogle rigtige billeder, men de kan være fordelt vilkårligt 