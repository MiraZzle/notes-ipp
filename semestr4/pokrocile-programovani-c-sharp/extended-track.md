- indexování od konce
	- pomocí stříšky
	- lze použít na libovolném typu s klasickým indexerem a vlastností Count
	- pokud má typ indexer, který přijímá typ Index, tak se použije ten
		- Index je readonly struktura s číslem a boolem (zda je to od konce, nebo ne)
	- `Index i = ^2;` vyrobí korektní instanci typu Index
- rozsahy (ranges, dvě tečky)
	- použije se metoda Slice
		- nedá se dodat extension metodou
	- nebo se použije indexer s readonly strukturou Range
		- ten má prioritu
- namespaces a názvy typů
	- při hledání typů podle názvu se postupuje postupně po vrstvách od aktuálního kontextu směrem nahoru, dokud se nenajde vhodný typ
	- někdy chceme vynutit „absolutní“ název typu
		- např. uvnitř třídy A.B.C chceme použít typ B (tedy nikoliv typ A.B)
		- můžeme napsat `global::B`
	- v souboru `csproj` se dá nastavit alias danému projektu (knihovně), takže pak nespadá do `global`
		- v C# zdrojáku je potřeba napsat `extern alias …`
		- tím se dá řešit problém, kdy se v různých knihovnách typy jmenují stejně
		- teoreticky se tak dají rozlišovat dvě různé verze jedné knihovny apod.
	- using
		- funguje jenom v rámci jednoho zdrojáku
		- „importuje“ typy z daného namespacu, ale už ne vnořené namespacy
		- pomocí `using X = Y;` můžu namespace `Y` používat i pod jménem `X`, ale je důležité s tím šetřit
