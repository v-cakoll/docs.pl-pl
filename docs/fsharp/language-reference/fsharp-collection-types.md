---
title: Typy kolekcji F#
description: 'Poznaj typy kolekcji F # i jak będą się różnić od typy kolekcji w programie .NET Framework.'
ms.date: 05/16/2016
ms.openlocfilehash: a3cfc3f06582c31a79dce43b583eca39f69ddf1e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43864764"
---
# <a name="f-collection-types"></a>Typy kolekcji F#

Przeglądając w tym temacie, można określić, które typów języka F # kolekcji najlepiej pasujące do potrzebne. Te typy kolekcji różnią się od typy kolekcji w programie .NET Framework, takich jak te w `System.Collections.Generic` przestrzeni nazw, w tym typy kolekcji F # są przeznaczone na widzenia programowania funkcjonalnego, a nie na perspektywy zorientowane obiektowo. Dokładniej mówiąc tylko kolekcja tablicy ma modyfikowalnych elementów. W związku z tym podczas modyfikowania kolekcji utworzysz wystąpienie zmodyfikowaną kolekcję, zamiast zmieniania oryginalnej kolekcji.

Typy kolekcji różnią się także w rodzaju strukturę danych, w którym przechowywane są obiekty. Struktury danych, takie jak tabele zbędnych danych, połączonej listy i tablic mają różną charakterystykę wydajności i inny zestaw dostępnych operacji.

## <a name="f-collection-types"></a>Typy kolekcji F#

W poniższej tabeli przedstawiono typy kolekcji F #.

|Typ|Opis|Linki pokrewne|
|----|-----------|-------------|
|[Lista](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Uporządkowany i niezmienne seria elementów tego samego typu. Zaimplementowane jako połączonej listy.|[Listy](lists.md)<br /><br />[Lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Tablica](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Stałym rozmiarze, zaczynający się od zera, modyfikowalna kolekcja kolejnych elementów danych, które są wszystkie tego samego typu.|[Tablice](arrays.md)<br /><br />[Moduł tablic](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2d — moduł](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3d — moduł](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Logicznej serii elementów, które są wszystkie tego typu. Sekwencje są szczególnie przydatne, gdy masz duży, uporządkowany zbiór danych, ale nie zawsze będziesz wszystkie elementy. Sekwencja poszczególne elementy są obliczane tylko jako wymagane, dlatego sekwencji można mają lepszą wydajność niż listy, jeśli nie wszystkie elementy są używane. Sekwencje są reprezentowane przez `seq<'T>` typ, który jest aliasem dla `IEnumerable<T>`. W związku z tym, dowolny typ .NET Framework, który implementuje `System.Collections.Generic.IEnumerable<'T>` może służyć jako sekwencja.|[Sekwencje](sequences.md)<br /><br />[SEQ — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[Mapy](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Niezmienne słownikiem elementów. Elementy są dostępne przez klucz.|[Map — moduł](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[Set](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Niezmienne zestaw, który jest oparty na drzew binarnych, gdzie porównanie jest funkcją porównania strukturalnego F #, która korzysta z potencjalnie implementacje `System.IComparable` interfejsu na wartościach kluczowych.|[Set — moduł](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabela funkcji

Ta sekcja zawiera porównanie funkcji, które są dostępne na typy kolekcji F #. Obliczeniową złożoność funkcji zostanie podany, gdzie N to rozmiar pierwszej kolekcji i M jest większy niż druga kolekcja, jeśli istnieje. Łączniki (-) wskazuje, że ta funkcja jest niedostępna w kolekcji. Ponieważ sekwencje opóźnieniem są oceniane, funkcji, takich jak Seq.distinct może być O(1) zwraca wynik natychmiast, mimo że nadal ma wpływ na wydajność sekwencji, gdy wyliczenia.

|Funkcja|Tablica|Lista|Sekwencja|Mapy|Zestaw|Opis|
|--------|-----|----|--------|---|---|-----------|
|Dołącz|O(M)|O(N)|O(N)|-|-|Zwraca nową kolekcję zawierającą elementy pierwszej kolekcji następuje elementy druga kolekcja.|
|add|-|-|-|O (log N)|O (log N)|Zwraca nową kolekcję z elementem, który został dodany.|
|Średnia|O(N)|O(N)|O(N)|-|-|Zwraca średnią z elementów w kolekcji.|
|averageby —|O(N)|O(N)|O(N)|-|-|Zwraca średnią z wyników określona funkcja stosowane do każdego elementu.|
|blit —|O(N)|-|-|-|-|Kopiuje część tablicy.|
|pamięć podręczna|-|-|O(N)|-|-|Oblicza i przechowuje elementy sekwencji.|
|rzutowanie|-|-|O(N)|-|-|Konwertuje elementy określonego typu.|
|Wybierz opcję|O(N)|O(N)|O(N)|-|-|Stosuje daną funkcję `f` do każdego elementu `x` listy. Zwraca listę zawierającą wyniki dla każdego elementu, gdzie funkcja zwraca `Some(f(x))`.|
|zbieranie|O(N)|O(N)|O(N)|-|-|Stosuje daną funkcję do do każdego elementu kolekcji, a następnie łączy wszystkie wyniki i zwraca listę połączoną.|
|comparewith —|-|-|O(N)|-|-|Porównuje dwie sekwencje przy użyciu funkcji porównywania danego, element po elemencie.|
|concat|O(N)|O(N)|O(N)|-|-|Łączy danego wyliczenie z wyliczenia jako pojedynczy wyliczenie połączonych.|
|zawiera|-|-|-|-|O (log N)|Zwraca wartość PRAWDA, jeśli zestaw zawiera określony element.|
|containsKey|-|-|-|O (log N)|-|Sprawdza, czy element znajduje się w domenie mapy.|
|count|-|-|-|-|O(N)|Zwraca liczbę elementów w zestawie.|
|countby —|-|-|O(N)|-|-|Dotyczy funkcji generowania klucza do każdego elementu w sekwencji, a następnie zwraca sekwencję zwracające unikatowe klucze i ich liczba wystąpień w oryginalnej sekwencji.|
|copy|O(N)|-|O(N)|-|-|Kopiuje kolekcję.|
|tworzenie|O(N)|-|-|-|-|Tworzy tablicę całego elementy, które są wszystkie wstępnie danej wartości.|
|Opóźnienie|-|-|O(1)|-|-|Zwraca sekwencję, która jest wbudowana ze specyfikacji opóźnione danej sekwencji.|
|różnica|-|-|-|-|O (M &#42; log N)|Zwraca nowy zbiór z elementami drugiego zbioru usuniętego z pierwszego zestawu.|
|Odrębne|||O(1)&AMP;#42;|||Zwraca sekwencję, która nie zawiera żadnych zduplikowanych pozycji zgodnie z rodzajowego mieszania i równości porównania we wpisach. Jeśli element powtarza się wielokrotnie w sekwencji, nowsze wystąpienia są odrzucane.|
|distinctby —|||O(1)&AMP;#42;|||Zwraca sekwencję, która nie zawiera żadnych zduplikowanych pozycji zgodnie z ogólnych porównań mieszania i równości na klucze, które zwraca daną funkcję generowania klucza. Jeśli element powtarza się wielokrotnie w sekwencji, nowsze wystąpienia są odrzucane.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Tworzy pustą kolekcję.|
|Istnieje|O(N)|O(N)|O(N)|O (log N)|O (log N)|Sprawdza, czy jakiegokolwiek elementu w sekwencji spełniają dany predykat.|
|exists2 —|O(min(N,M))|-|O(min(N,M))|||Sprawdza, czy jakaś para odpowiednich elementów sekwencji wejściowych spełnia określonym predykatem.|
|fill|O(N)|||||Ustawia zakres elementów w tablicy na danej wartości.|
|filtr|O(N)|O(N)|O(N)|O(N)|O(N)|Zwraca nową kolekcję, która zawiera tylko elementy kolekcji, dla których dany predykat zwraca `true`.|
|find|O(N)|O(N)|O(N)|O (log N)|-|Zwraca pierwszy element, dla którego należy dana funkcja zwraca `true`. Zwraca `System.Collections.Generic.KeyNotFoundException` jeśli taki element nie istnieje.|
|findindex —|O(N)|O(N)|O(N)|-|-|Zwraca indeks pierwszego elementu w tablicy, która spełnia określonym predykatem. Wywołuje `System.Collections.Generic.KeyNotFoundException` Jeśli predykat nie spełnia żadnego elementu.|
|findKey —|-|-|-|O (log N)|-|Ocenia funkcji w każdym mapowania w kolekcji, a następnie zwraca klucz dla pierwszego mapowania, gdzie funkcja zwraca `true`. Jeśli taki element nie istnieje, ta funkcja podnosi `System.Collections.Generic.KeyNotFoundException`.|
|zwijania|O(N)|O(N)|O(N)|O(N)|O(N)|Stosuje funkcję do każdego elementu kolekcji, wątki argument akumulatora za pomocą obliczeń. Jeśli elementy są i0... w danych wejściowych funkcji jest f, ta funkcja oblicza f (...) (f s i0)...) w programie.|
|fold2 —|O(N)|O(N)|-|-|-|Dotyczy funkcji odpowiednie elementy dwie kolekcje, wątki argument akumulatora za pomocą obliczeń. Kolekcje muszą mieć identyczne rozmiary. Jeśli funkcja danych wejściowych jest f, a elementy są i0... w i j0 —... jN, ta funkcja oblicza f (...) (j0 — i0 f s)...) w jN.|
|foldback —|O(N)|O(N)|-|O(N)|O(N)|Stosuje funkcję do każdego elementu kolekcji, wątki argument akumulatora za pomocą obliczeń. Jeśli elementy są i0... w danych wejściowych funkcji jest f, ta funkcja oblicza f i0 (...) (f w s)).|
|foldback2 —|O(N)|O(N)|-|-|-|Dotyczy funkcji odpowiednie elementy dwie kolekcje, wątki argument akumulatora za pomocą obliczeń. Kolekcje muszą mieć identyczne rozmiary. Jeśli funkcja danych wejściowych jest f, a elementy są i0... w i j0 —... jN, ta funkcja oblicza j0 — i0 f (...) (f w jN s)).|
|ForAll|O(N)|O(N)|O(N)|O(N)|O(N)|Sprawdza, czy wszystkie elementy kolekcji spełniają dany predykat.|
|forall2 —|O(N)|O(N)|O(N)|-|-|Sprawdza, czy wszystkie odpowiednie elementy w kolekcji spełniają dany predykat parowania.|
|Pobierz / n-ty|O(1)|O(N)|O(N)|-|-|Zwraca element z kolekcji, biorąc pod uwagę jego indeksu.|
|główny|-|O(1)|O(1)|-|-|Zwraca pierwszy element w kolekcji.|
|Init|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję, biorąc pod uwagę wymiar i funkcję generatora do obliczenia elementów.|
|initinfinite —|-|-|O(1)|-|-|Generuje sekwencję, w przypadku postanowiliśmy, zwraca kolejne elementy, wywołując daną funkcję.|
|INTERSECT|-|-|-|-|O (log N &#42; dziennika M)|Oblicza część wspólną dwóch zestawów.|
|intersectmany —|-|-|-|-|O (N1 &AMP;#42; N2...)|Oblicza przecięcia sekwencji zestawów. Sekwencja nie może być pusta.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Zwraca `true` Jeśli kolekcja jest pusta.|
|ispropersubset —|-|-|-|-|O (M &#42; log N)|Zwraca `true` wszystkie elementy pierwszego zestawu są w drugim zbiorze i co najmniej jeden element drugiego zestawu nie jest w pierwszym zestawie.|
|ispropersuperset —|-|-|-|-|O (M &#42; log N)|Zwraca `true` wszystkie elementy drugiego zestawu są w pierwszym zestawie i co najmniej jeden element pierwszego zestawu nie znajduje się w drugim zestawie.|
|issubset —|-|-|-|-|O (M &#42; log N)|Zwraca `true` Jeśli wszystkie elementy pierwszego zestawu są w drugim zbiorze.|
|issuperset —|-|-|-|-|O (M &#42; log N)|Zwraca `true` Jeśli wszystkie elementy drugiego zestawu są w pierwszym zestawie.|
|ITER|O(N)|O(N)|O(N)|O(N)|O(N)|Stosuje daną funkcję do do każdego elementu kolekcji.|
|iteri —|O(N)|O(N)|O(N)|-|-|Stosuje daną funkcję do do każdego elementu kolekcji. Liczba całkowita, która jest przekazywana do funkcji wskazuje indeks elementu.|
|iteri2 —|O(N)|O(N)|-|-|-|Stosuje daną funkcję do pary elementów, które są pobierane z dopasowywania indeksów w dwóch tablicach. Liczba całkowita, która jest przekazywana do funkcji wskazuje indeks elementu. Dwie tablice muszą być tej samej długości.|
|iter2 —|O(N)|O(N)|O(N)|-|-|Stosuje daną funkcję do pary elementów, które są pobierane z dopasowywania indeksów w dwóch tablicach. Dwie tablice muszą być tej samej długości.|
|length|O(1)|O(N)|O(N)|-|-|Zwraca liczbę elementów w kolekcji.|
|map|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję, której elementy są wynikami zastosowania danej funkcji do każdego elementu tablicy.|
|map2 —|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję, której elementy są wynikami zastosowania danej funkcji na odpowiednie elementy dwie kolekcje parowania. Dwóch tablic danych wejściowych musi mieć tę samą długość.|
|map3 —|-|O(N)|-|-|-|Tworzy kolekcję, której elementy są wynikami zastosowania danej funkcji na odpowiednie elementy trzy kolekcje jednocześnie.|
|MAPI|O(N)|O(N)|O(N)|-|-|Tworzy tablicę, której elementy są wynikami zastosowania danej funkcji do każdego elementu tablicy. Liczba całkowita indeksu, który jest przekazywany do funkcji wskazuje indeks elementu przekształcanego.|
|mapi2 —|O(N)|O(N)|-|-|-|Tworzy kolekcję, której elementy są wynikami zastosowania danej funkcji na odpowiednie elementy dwie kolekcje parowania, również przenoszenia indeksu elementów. Dwóch tablic danych wejściowych musi mieć tę samą długość.|
|max|O(N)|O(N)|O(N)|-|-|Zwraca największy element w kolekcji, porównywane za pomocą [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operatora.|
|maxby —|O(N)|O(N)|O(N)|-|-|Zwraca największy element w kolekcji, porównywane za pomocą [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) na wynik funkcji.|
|maxelement —|-|-|-|-|O (log N)|Zwraca największy element w zestawie według kolejności, który jest używany dla zestawu.|
|min|O(N)|O(N)|O(N)|-|-|Zwraca najmniejszą element w kolekcji, porównywane za pomocą [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operatora.|
|minby —|O(N)|O(N)|O(N)|-|-|Zwraca najmniejszą element w kolekcji, porównywane za pomocą [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operatora na wynik funkcji.|
|minelement —|-|-|-|-|O (log N)|Zwraca najniższy element w zestawie według kolejności, używany dla zestawu.|
|ofarray —|-|O(N)|O(1)|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako danej tablicy.|
|oflist —|O(N)|-|O(1)|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako danej listy.|
|ofseq —|O(N)|O(N)|-|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako danej sekwencji.|
|parowania|-|-|O(N)|-|-|Zwraca sekwencję każdego elementu w sekwencji wejściowych i jego poprzednik, z wyjątkiem pierwszego elementu, który jest zwracany tylko jako poprzednik drugiego elementu.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Dzieli kolekcji na dwie kolekcje. Pierwsza kolekcja zawiera elementy, dla których dany predykat zwraca `true`, a druga kolekcja zawiera elementy, dla których dany predykat zwraca `false`.|
|permute —|O(N)|O(N)|-|-|-|Zwraca tablicę ze wszystkimi elementami cieniowania zgodnie z określonym permutacji.|
|Wybierz|O(N)|O(N)|O(N)|O (log N)|-|Stosuje daną funkcję do kolejne elementy, zwracając pierwszego wyniku, gdzie funkcja zwraca niektóre. Jeśli funkcja nigdy nie zwraca niektóre, `System.Collections.Generic.KeyNotFoundException` jest wywoływane.|
|readonly|-|-|O(N)|-|-|Tworzy obiekt sekwencji, który deleguje do danego obiektu sekwencji. Ta operacja temu rzutowanie typu nie ponowne odnajdywanie i mutować oryginalnej sekwencji. Na przykład jeśli podana tablica, zwracana sekwencja będzie zwracać elementów tablicy, ale nie można rzutować obiektu zwracanej sekwencji do tablicy.|
|Zmniejsz|O(N)|O(N)|O(N)|-|-|Stosuje funkcję do każdego elementu kolekcji, wątki argument akumulatora za pomocą obliczeń. Ta funkcja rozpoczyna, stosując funkcję na pierwszych dwóch elementów, wynik jest przekazywana do funkcji wraz z trzeciego elementu i tak dalej. Funkcja zwraca wynik końcowy.|
|reduceback —|O(N)|O(N)|-|-|-|Stosuje funkcję do każdego elementu kolekcji, wątki argument akumulatora za pomocą obliczeń. Jeśli elementy są i0... w danych wejściowych funkcji jest f, ta funkcja oblicza f i0 (...) (f w-1 w)).|
|remove|-|-|-|O (log N)|O (log N)|Usuwa element z domeny mapy. Nie wyjątek jest zgłaszany, jeśli element nie jest obecny.|
|Replikacja|-|O(N)|-|-|-|Tworzy listę o określonej długości, z każdym elementem równa podanej wartości.|
|Rev|O(N)|O(N)|-|-|-|Zwraca nową listę z elementami w odwrotnej kolejności.|
|skanowanie|O(N)|O(N)|O(N)|-|-|Stosuje funkcję do każdego elementu kolekcji, wątki argument akumulatora za pomocą obliczeń. Ta operacja stosuje funkcję do drugiego argumentu i pierwszego elementu listy. Następnie operacja jest przekazywana tego wyniku do funkcji wraz z drugiego elementu i tak dalej. Na koniec operacja zwraca listę wyników pośrednich i wynik końcowy.|
|scanback —|O(N)|O(N)|-|-|-|Przypomina operacji foldback —, ale zwraca wyniki pośrednie i końcowe.|
|pojedyncze|-|-|O(1)|-|O(1)|Zwraca sekwencję, która zapewni tylko jeden element.|
|set|O(1)|-|-|-|-|Ustawia element tablicy na określoną wartość.|
|Pomiń|-|-|O(N)|-|-|Zwraca sekwencję, która pomija N elementy sekwencji źródłowej i następnie zwraca pozostałe elementy w sekwencji.|
|Skipwhile —|-|-|O(N)|-|-|Zwraca sekwencję, gdy postanowiliśmy, pomija elementy sekwencji źródłowej podczas danej zwraca predykatu `true` i następnie zwraca pozostałe elementy w sekwencji.|
|sort|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|O (N log N)|O (N log N)|-|-|Sortowania kolekcji wartości elementu. Elementy są porównywane za pomocą [porównaj](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortby —|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|O (N log N)|O (N log N)|-|-|Sortuje listy przy użyciu kluczy, które zapewnia danym projekcji. Klucze są porównywane za pomocą [porównaj](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplace —|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Mutacja go w miejscu i przy użyciu funkcji porównywania danego podczas sortowania elementów tablicy. Elementy są porównywane za pomocą [porównaj](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplaceby —|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Sortuje elementy tablicy mutacja go w miejscu i rozpoczęcie używania danego projekcji kluczy. Elementy są porównywane za pomocą [porównaj](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplacewith —|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Sortowania mutacja go w miejscu i przy użyciu funkcji porównywania danego jak kolejność elementów tablicy.|
|sortwith —|Średnio O (N log N)<br /><br />Najgorszy O(N^2)|O (N log N)|-|-|-|Sortuje elementów kolekcji, używając funkcji porównywania danego jako kolejność i zwraca nową kolekcję.|
|Sub|O(N)|-|-|-|-|Tworzy tablicę zawierającą dany Podzakres, który jest określony przez uruchomienie indeksu i długości.|
|Suma|O(N)|O(N)|O(N)|-|-|Zwraca sumę elementów w kolekcji.|
|sumby —|O(N)|O(N)|O(N)|-|-|Zwraca sumę wyników, które są generowane, stosując funkcję do każdego elementu kolekcji.|
|Tail|-|O(1)|-|-|-|Zwraca listę bez jej pierwszego elementu.|
|Wypełnij|-|-|O(N)|-|-|Zwraca elementy sekwencji do określonej liczby.|
|Takewhile —|-|-|O(1)|-|-|Zwraca sekwencję, gdy postanowiliśmy, plony elementy sekwencji źródłowej podczas danej zwraca predykatu `true` , a następnie zwraca żadnych więcej elementów.|
|ToArray|-|O(N)|O(N)|O(N)|O(N)|Tworzy tablicę z danej kolekcji.|
|Tolist —|O(N)|-|O(N)|O(N)|O(N)|Tworzy listę z danej kolekcji.|
|toseq —|O(1)|O(1)|-|O(1)|O(1)|Tworzy sekwencję z danej kolekcji.|
|Obetnij|-|-|O(1)|-|-|Zwraca sekwencję na, gdy wyliczone, zwraca nie więcej niż N elementów.|
|tryfind —|O(N)|O(N)|O(N)|O (log N)|-|Wyszukuje element, który spełnia określonym predykatem.|
|tryfindindex —|O(N)|O(N)|O(N)|-|-|Wyszukuje pierwszy element, który spełnia dany predykat i zwraca indeks pasujący element lub `None` jeśli taki element nie istnieje.|
|tryfindkey —|-|-|-|O (log N)|-|Zwraca klucz pierwszego mapowania w kolekcji, który spełnia dany predykat lub zwraca `None` jeśli taki element nie istnieje.|
|trypick —|O(N)|O(N)|O(N)|O (log N)|-|Stosuje daną funkcję do kolejne elementy, zwracając pierwszego wyniku, gdzie funkcja zwraca `Some` dla niektórych wartości. Jeśli taki element nie istnieje, operacja zwraca `None`.|
|rozwijania|-|-|O(N)|-|-|Zwraca sekwencję która zawiera elementy, które generuje dane obliczenie.|
|unia|-|-|-|-|O (M &#42; log N)|Oblicza sumę dwóch zestawów.|
|unionmany —|-|-|-|-|O (N1 &AMP;#42; N2...)|Oblicza sumę sekwencji zestawów.|
|Rozpakowywanie|O(N)|O(N)|O(N)|-|-|Dzieli listą par na dwie listy.|
|unzip3 —|O(N)|O(N)|O(N)|-|-|Dzieli listę trójek na trzy listy.|
|okna|-|-|O(N)|-|-|Zwraca sekwencję, która zapewni przewijania systemu windows zawierającego elementy, które są pobierane z sekwencji wejściowych. Każde okno jest zwracana jako nowej tablicy.|
|ZIP|O(N)|O(N)|O(N)|-|-|Łączy dwie kolekcje w postaci listy pary. Dwie listy muszą mieć równą długości.|
|zip3 —|O(N)|O(N)|O(N)|-|-|Łączy trzech kolekcji na listę trójek. Listy musi być równa długości.|

## <a name="see-also"></a>Zobacz także

- [Typy F#](fsharp-types.md)
- [Dokumentacja języka F#](index.md)
