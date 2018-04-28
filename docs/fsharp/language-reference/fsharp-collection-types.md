---
title: Typy kolekcji F#
description: 'Poznaj typy kolekcji F # i jak są one różne od typy kolekcji w programie .NET Framework.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 0baad5bdf88e8f381240b822a3f6132898dc9ff9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="f-collection-types"></a>Typy kolekcji F#

Zostały podane w tym temacie, można określić, F # kolekcji typu najlepiej pasujące do potrzebne. Typy kolekcji różnią się od typy kolekcji w programie .NET Framework, takich jak te w `System.Collections.Generic` przestrzeni nazw, w tym typy kolekcji F # zostały zaprojektowane z punktu widzenia programowania funkcjonalności zamiast zorientowane obiektowo perspektywy. W szczególności kolekcji tablicy ma modyfikowalną elementów. Po zmodyfikowaniu kolekcji, w związku z tym utworzyć wystąpienia modyfikacji kolekcji zamiast zmieniania oryginalnej kolekcji.

Typy kolekcji różnią się również w typie struktury danych, w której przechowywane są obiekty. Struktury danych, takich jak tabele hash, list połączonych i tablice mają różne charakterystyki i inny zestaw dostępnych operacji.


## <a name="f-collection-types"></a>Typy kolekcji F#
W poniższej tabeli przedstawiono typy kolekcji F #.



|Typ|Opis|Linki pokrewne|
|----|-----------|-------------|
|[Lista](https://msdn.microsoft.com/library/c627b668-477b-4409-91ed-06d7f1b3e4a7)|Seria uporządkowany i modyfikować elementów tego samego typu. Zaimplementowane jako listy połączonej.|[Listy](lists.md)<br /><br />[Lista modułów](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)|
|[Tablica](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)|Stały rozmiar, liczony od zera, modyfikowalną kolekcję elementów kolejnych danych, które znajdują się tego samego typu.|[Tablice](arrays.md)<br /><br />[Moduł tablic](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1)<br /><br />[Array2d — moduł](https://msdn.microsoft.com/library/ae1a9746-7817-4430-bcdb-a79c2411bbd3)<br /><br />[Array3d — moduł](https://msdn.microsoft.com/library/c8355e2d-add8-48a4-8aa6-1c57ae74c560)|
|[SEQ](https://msdn.microsoft.com/library/2f0c87c6-8a0d-4d33-92a6-10d1d037ce75)|Seria logiczne elementy, które są tylko jeden typ. Sekwencje są szczególnie przydatne, gdy ma dużą, uporządkowanych zbierania danych, ale niekoniecznie nie powinien być wszystkie elementy. Sekwencja poszczególne elementy są obliczane tylko jako wymagana, więc sekwencję zapewnia lepszą wydajność niż listy, jeśli nie wszystkie elementy są używane. Sekwencje są reprezentowane przez `seq<'T>` typu, który jest aliasem dla `IEnumerable<T>`. W związku z tym dowolnego typu .NET Framework, który implementuje `System.Collections.Generic.IEnumerable<'T>` mogą być używane jako sekwencję.|[Sekwencje](sequences.md)<br /><br />[SEQ — moduł](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)|
|[mapy](https://msdn.microsoft.com/library/975316ea-55e3-4987-9994-90897ad45664)|Niezmienne słownikiem elementów. Elementy są dostępne dla klucza.|[Map — moduł](https://msdn.microsoft.com/library/bfe61ead-f16c-416f-af98-56dbcbe23e4f)|
|[zestaw](https://msdn.microsoft.com/library/50cebdce-0cd7-4c5c-8ebc-f3a9e90b38d8)|Niezmienne zestaw, który jest oparty na drzew binarnych porównania w przypadku F # Funkcja porównywania strukturalnego, który używa potencjalnie implementacje `System.IComparable` interfejsu wartości klucza.|[Set — moduł](https://msdn.microsoft.com/library/61efa732-d55d-4c32-993f-628e2f98e6a0)|

### <a name="table-of-functions"></a>Tabela w funkcji
Ta sekcja zawiera porównanie funkcji, które są dostępne na typy kolekcji F #. Podano obliczeniową złożoność funkcji, gdzie N jest rozmiarem pierwszej kolekcji i M jest większy niż druga kolekcja, jeśli istnieje. Łączniki (-) wskazuje, że ta funkcja nie jest dostępna w kolekcji. Ponieważ sekwencje opóźnieniem są oceniane, funkcji, takich jak SEQ.DISTINCT — może być O(1) ponieważ zwraca ono natychmiast, mimo że nadal ma wpływ na wydajność sekwencji, gdy wyliczenie.



|Funkcja|Tablica|Lista|Sekwencja|mapy|zestaw|Opis|
|--------|-----|----|--------|---|---|-----------|
|Dołącz|O(M)|O(N)|O(N)|-|-|Zwraca nową kolekcję zawierającą elementy pierwsza kolekcja następuje elementy druga kolekcja.|
|add|-|-|-|O (dziennik N)|O (dziennik N)|Zwraca nowy zbiór z elementem dodane.|
|Średnia|O(N)|O(N)|O(N)|-|-|Zwraca średnią elementów w kolekcji.|
|averageBy|O(N)|O(N)|O(N)|-|-|Zwraca średnią wyników określona funkcja zastosowane do każdego elementu.|
|blit —|O(N)|-|-|-|-|Kopiuje sekcji tablicy.|
|pamięć podręczna|-|-|O(N)|-|-|Oblicza i przechowuje elementy sekwencji.|
|rzutowanie|-|-|O(N)|-|-|Konwertuje elementy określonego typu.|
|Wybierz pozycję|O(N)|O(N)|O(N)|-|-|Ma zastosowanie dana funkcja `f` do każdego elementu `x` listy. Zwraca listę, zawierającego wyniki dla każdego elementu, w którym funkcja zwraca `Some(f(x))`.|
|zbieranie|O(N)|O(N)|O(N)|-|-|Do każdego elementu w kolekcji ma zastosowanie dana funkcja łączy wszystkie wyniki i zwraca połączonej listy.|
|comparewith —|-|-|O(N)|-|-|Porównuje dwie sekwencje przy użyciu funkcji podany porównanie elementów.|
|concat|O(N)|O(N)|O(N)|-|-|Łączy danego wyliczenie elementu wyliczeń jako pojedyncze wyliczenie połączonych.|
|zawiera|-|-|-|-|O (dziennik N)|Zwraca wartość PRAWDA, jeśli zestaw zawiera określony element.|
|containsKey|-|-|-|O (dziennik N)|-|Sprawdza, czy element znajduje się w domenie mapy.|
|count|-|-|-|-|O(N)|Zwraca liczbę elementów w zestawie.|
|countby —|-|-|O(N)|-|-|Dotyczy funkcji generowania klucza do każdego elementu w sekwencji i zwraca sekwencję zwracające unikatowy kluczy i ich liczbę wystąpień w oryginalnej sekwencji.|
|copy|O(N)|-|O(N)|-|-|Kopiuje kolekcję.|
|tworzenie|O(N)|-|-|-|-|Tworzy tablicę całego elementy, które są wszystkie początkowo podanej wartości.|
|Opóźnienie|-|-|O(1)|-|-|Zwraca sekwencję, która składa się ze specyfikacji opóźnione danej sekwencji.|
|różnica|-|-|-|-|O (M &#42; dziennika N)|Zwraca nowy zbiór z elementami drugiego zbioru usuniętego z pierwszego zestawu.|
|Różne|||O(1)&AMP;#42;|||Zwraca sekwencję, która nie zawiera żadnych zduplikowanych pozycji zgodnie z ogólnego porównania wyznaczania wartości skrótu i o równość zapisów. Jeśli element występuje wiele razy w sekwencji, nowsze wystąpienia są odrzucane.|
|distinctby —|||O(1)&AMP;#42;|||Zwraca sekwencję, która nie zawiera żadnych zduplikowanych pozycji zgodnie z ogólnego porównania wyznaczania wartości skrótu i o równość kluczy, które zwraca daną funkcję generowania klucza. Jeśli element występuje wiele razy w sekwencji, nowsze wystąpienia są odrzucane.|
|empty|O(1)|O(1)|O(1)|O(1)|O(1)|Tworzy pustą kolekcję.|
|istnieje|O(N)|O(N)|O(N)|O (dziennik N)|O (dziennik N)|Sprawdza, czy dowolny element sekwencji spełnia danego predykatu.|
|exists2 —|O(min(N,M))|-|O(min(N,M))|||Sprawdza, czy w jakiejkolwiek parze odpowiednie elementy sekwencji wejściowych spełnia danego predykatu.|
|fill|O(N)|||||Ustawia zakres elementów tablicy podanej wartości.|
|filtr|O(N)|O(N)|O(N)|O(N)|O(N)|Zwraca nową kolekcję, która zawiera tylko elementy kolekcji, dla którego zwraca podanego predykatu `true`.|
|find|O(N)|O(N)|O(N)|O (dziennik N)|-|Zwraca pierwszy element, dla których dana funkcja zwraca `true`. Zwraca `System.Collections.Generic.KeyNotFoundException` Jeśli nie zawiera żadnego takiego elementu.|
|findIndex|O(N)|O(N)|O(N)|-|-|Zwraca indeks pierwszego elementu w tablicy, która spełnia danego predykatu. Zgłasza `System.Collections.Generic.KeyNotFoundException` Jeśli żaden element nie będzie spełniał predykatu.|
|findKey —|-|-|-|O (dziennik N)|-|Ocenia funkcja na każdym mapowanie w kolekcji, a następnie zwraca klucz dla pierwszego mapowania, gdy funkcja zwraca `true`. Jeśli żaden taki element istnieje, ta funkcja podnosi `System.Collections.Generic.KeyNotFoundException`.|
|fold|O(N)|O(N)|O(N)|O(N)|O(N)|Dotyczy funkcji każdy element kolekcji wątkowość argumentu akumulatora do obliczenia. Jeśli funkcja wejściowych jest f, elementy są i0... w tej funkcji oblicza f (...) (f s i0)...) w programie.|
|fold2 —|O(N)|O(N)|-|-|-|Stosuje funkcję do odpowiednich elementów dwie kolekcje wątkowość argumentu akumulatora do obliczenia. Kolekcje muszą mieć taki sam rozmiar. Jeśli funkcja wejściowych jest f i elementy są i0... w i j0 —... jN, ta funkcja oblicza f (...) (j0 — i0 f s)...) w jN.|
|foldback —|O(N)|O(N)|-|O(N)|O(N)|Dotyczy funkcji każdy element kolekcji wątkowość argumentu akumulatora do obliczenia. Jeśli funkcja wejściowy jest f, elementy są i0... w tej funkcji oblicza f i0 (...) (f w s)).|
|foldback2 —|O(N)|O(N)|-|-|-|Stosuje funkcję do odpowiednich elementów dwie kolekcje wątkowość argumentu akumulatora do obliczenia. Kolekcje muszą mieć taki sam rozmiar. Jeśli funkcja wejściowych jest f i elementy są i0... w i j0 —... jN, ta funkcja oblicza j0 — i0 f (...) (f w jN s)).|
|ForAll —|O(N)|O(N)|O(N)|O(N)|O(N)|Sprawdza, czy wszystkie elementy kolekcji spełniają danego predykatu.|
|forall2 —|O(N)|O(N)|O(N)|-|-|Sprawdza, czy wszystkie odpowiednie elementy kolekcji parowania spełniają danego predykatu.|
|Pobierz / n-ty|O(1)|O(N)|O(N)|-|-|Zwraca element z kolekcji podane jej indeks.|
|HEAD|-|O(1)|O(1)|-|-|Zwraca pierwszy element w kolekcji.|
|init|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję wymiaru i funkcja generator obliczeniowe elementy.|
|initinfinite —|-|-|O(1)|-|-|Generuje sekwencję, gdy iterowane, zwraca kolejnych elementów przez wywołanie metody danej funkcji.|
|INTERSECT|-|-|-|-|O (dziennika N &#42; dziennika M)|Oblicza część wspólną dwóch zestawów.|
|intersectmany —|-|-|-|-|O (N1 &AMP;#42; N2...)|Oblicza przecięcie sekwencji zestawów. Sekwencja nie może być pusta.|
|IsEmpty|O(1)|O(1)|O(1)|O(1)|-|Zwraca `true` Jeśli kolekcja jest pusta.|
|ispropersubset —|-|-|-|-|O (M &#42; dziennika N)|Zwraca `true` są wszystkie elementy pierwszego zbioru w drugim zbiorze i co najmniej jeden element drugi zestaw nie znajduje się w pierwszym zestawie.|
|ispropersuperset —|-|-|-|-|O (M &#42; dziennika N)|Zwraca `true` są wszystkie elementy drugiego zestawu w pierwszym zestawie i co najmniej jeden element pierwszy zestaw nie znajduje się w drugim zbiorze.|
|issubset —|-|-|-|-|O (M &#42; dziennika N)|Zwraca `true` Jeśli wszystkie elementy pierwszego zbioru znajdują się w drugim zbiorze.|
|issuperset —|-|-|-|-|O (M &#42; dziennika N)|Zwraca `true` Jeśli wszystkie elementy drugi zestaw znajdują się w pierwszym zestawie.|
|ITER|O(N)|O(N)|O(N)|O(N)|O(N)|Ma zastosowanie dana funkcja do każdego elementu w kolekcji.|
|iteri —|O(N)|O(N)|O(N)|-|-|Ma zastosowanie dana funkcja do każdego elementu w kolekcji. Liczba całkowita, która została przekazana do funkcji wskazuje indeks elementu.|
|iteri2 —|O(N)|O(N)|-|-|-|Dotyczy dana funkcja dwa elementy, które są pobierane z odpowiadającym indeksy w dwóch tablic. Liczba całkowita, która została przekazana do funkcji wskazuje indeks elementów. Dwie tablice musi mieć taką samą długość.|
|iter2 —|O(N)|O(N)|O(N)|-|-|Dotyczy dana funkcja dwa elementy, które są pobierane z odpowiadającym indeksy w dwóch tablic. Dwie tablice musi mieć taką samą długość.|
|length|O(1)|O(N)|O(N)|-|-|Zwraca liczbę elementów w kolekcji.|
|map|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję, której elementy są wyniki zastosowania danej funkcji, aby każdy element tablicy.|
|map2 —|O(N)|O(N)|O(1)|-|-|Tworzy kolekcję, której elementy są wyniki zastosowania danej funkcji do odpowiednich elementów dwie kolekcje parowania. Dwie tablice wejściowy musi mieć taką samą długość.|
|map3 —|-|O(N)|-|-|-|Tworzy kolekcję, której elementy są wyniki zastosowania danej funkcji do odpowiednich elementów trzech zbiorów jednocześnie.|
|MAPI|O(N)|O(N)|O(N)|-|-|Tworzy tablicę, której elementy są wyniki zastosowania danej funkcji, aby każdy element tablicy. Indeks liczba całkowita, która została przekazana do funkcji wskazuje indeks elementu, który transformacji.|
|mapi2 —|O(N)|O(N)|-|-|-|Tworzy kolekcję, której elementy są wyniki zastosowania danej funkcji do odpowiednich elementów dwie kolekcje parowania, również przekazywanie indeksu elementów. Dwie tablice wejściowy musi mieć taką samą długość.|
|max|O(N)|O(N)|O(N)|-|-|Zwraca największy element w kolekcji porównywane za pomocą [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) operatora.|
|maxBy|O(N)|O(N)|O(N)|-|-|Zwraca największy element w kolekcji porównywane za pomocą [max](https://msdn.microsoft.com/library/9a988328-00e9-467b-8dfa-e7a6990f6cce) wyniku funkcji.|
|maxelement —|-|-|-|-|O (dziennik N)|Zwraca największy element w zestawie zgodnie z kolejność, który jest używany dla zestawu.|
|min|O(N)|O(N)|O(N)|-|-|Zwraca co najmniej element w kolekcji porównywane za pomocą [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operatora.|
|minBy|O(N)|O(N)|O(N)|-|-|Zwraca co najmniej element w kolekcji porównywane za pomocą [min](https://msdn.microsoft.com/library/adea4fd7-bfad-4834-989c-7878aca81fed) operator wyniku funkcji.|
|minelement —|-|-|-|-|O (dziennik N)|Zwraca najniższy element w zestawie zgodnie z kolejność, który jest używany dla zestawu.|
|ofarray —|-|O(N)|O(1)|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako podanej tablicy.|
|oflist —|O(N)|-|O(1)|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako danej listy.|
|ofseq —|O(N)|O(N)|-|O(N)|O(N)|Tworzy kolekcję, która zawiera te same elementy jako danej sekwencji.|
|parowania|-|-|O(N)|-|-|Zwraca sekwencję każdego elementu w sekwencji wejściowych i jego poprzednik, z wyjątkiem pierwszego elementu, który jest zwracany tylko jako poprzedzającego drugiego elementu.|
|partition|O(N)|O(N)|-|O(N)|O(N)|Dzieli kolekcji do dwóch kolekcji. Pierwsza kolekcja zawiera elementy, dla których zwraca podanego predykatu `true`, a druga kolekcja zawiera elementy, dla których zwraca podanego predykatu `false`.|
|permute —|O(N)|O(N)|-|-|-|Zwraca informacje o wszystkich elementach cieniowania zgodnie z określonym permutacji.|
|Wybierz|O(N)|O(N)|O(N)|O (dziennik N)|-|Dotyczy kolejnych elementów, zwracanie pierwszego wyniku, gdy funkcja zwraca niektóre danej funkcji. Jeśli funkcja nigdy nie powraca, niektóre `System.Collections.Generic.KeyNotFoundException` jest wywoływane.|
|readonly|-|-|O(N)|-|-|Tworzy obiekt sekwencji, który deleguje do danego obiektu sekwencji. Ta operacja gwarantuje, że rzutowanie typu nie może ponownie odnaleźć i zmodyfikować oryginalny sekwencji. Na przykład jeśli podana tablica, zwracane sekwencji zwróci elementów tablicy, ale nie można rzutować obiektu sekwencji zwrócony do tablicy.|
|Zmniejsz|O(N)|O(N)|O(N)|-|-|Dotyczy funkcji każdy element kolekcji wątkowość argumentu akumulatora do obliczenia. Ta funkcja rozpoczyna, stosując funkcję do dwóch pierwszych elementów, wynik jest przekazywana do funkcji wraz z trzeciego elementu i tak dalej. Funkcja zwraca wynik końcowy.|
|reduceback —|O(N)|O(N)|-|-|-|Dotyczy funkcji każdy element kolekcji wątkowość argumentu akumulatora do obliczenia. Jeśli funkcja wejściowy jest f, elementy są i0... w tej funkcji oblicza f i0 (...) (f w 1 w)).|
|remove|-|-|-|O (dziennik N)|O (dziennik N)|Usuwa element z domeny mapy. Żaden wyjątek jest wywoływany, jeśli element nie jest obecny.|
|Replikowanie|-|O(N)|-|-|-|Tworzy listę o określonej długości z każdym elementem ustawić podanej wartości.|
|Rev|O(N)|O(N)|-|-|-|Zwraca nową listę elementów w odwrotnej kolejności.|
|skanowanie|O(N)|O(N)|O(N)|-|-|Dotyczy funkcji każdy element kolekcji wątkowość argumentu akumulatora do obliczenia. Ta operacja dotyczy funkcji drugi argument i pierwszy element listy. Operacja następnie przekazuje i tak dalej tego wyniku do funkcji wraz z drugiego elementu. Na koniec operacji zwraca listę wyników pośrednich i wynik końcowy.|
|scanback —|O(N)|O(N)|-|-|-|Przypomina operacji foldback —, ale zwraca wyniki pośrednie i końcowe.|
|pojedyncze|-|-|O(1)|-|O(1)|Zwraca sekwencji, której wynikiem jest tylko jeden element.|
|set|O(1)|-|-|-|-|Ustawia wartość określonego elementu tablicy.|
|Pomiń|-|-|O(N)|-|-|Zwraca sekwencję pomija N elementy sekwencji źródłowej, która daje w wyniku pozostałe elementy sekwencji.|
|skipWhile|-|-|O(N)|-|-|Zwraca sekwencji, gdy iterowane, pomija elementy sekwencji źródłowej podczas danego predykatu zwraca `true` , a następnie zwraca pozostałe elementy sekwencji.|
|sort|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|O (dziennik N N)|O (dziennik N N)|-|-|Wartość elementu sortowania kolekcji. Elementy są porównywane przy użyciu [porównania](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortBy|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|O (dziennik N N)|O (dziennik N N)|-|-|Sortuje danej listy przy użyciu kluczy, które zapewnia danego projekcji. Klucze są porównywane przy użyciu [porównania](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplace —|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Sortuje elementy tablicy mutacja go w miejscu i przy użyciu funkcji danego porównania. Elementy są porównywane za pomocą [porównania](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplaceby —|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Sortuje elementy tablicy mutacja go w miejscu i przy użyciu danego projekcji kluczy. Elementy są porównywane za pomocą [porównania](https://msdn.microsoft.com/library/295e1320-0955-4c3d-ac31-288fa80a658c).|
|sortinplacewith —|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|-|-|-|-|Mutacja go w miejscu i przy użyciu funkcji podany porównanie jako kolejność sortowania elementów tablicy.|
|sortwith —|Średnia O (dziennik N N)<br /><br />Najgorszy O(N^2)|O (dziennik N N)|-|-|-|Sortuje elementy kolekcji, przy użyciu funkcji podany porównanie jako kolejność i zwracanie nową kolekcję.|
|Sub|O(N)|-|-|-|-|Tworzy tablicę zawierającą danego Podzakres, określonym przez indeks i długość uruchomienia.|
|Suma|O(N)|O(N)|O(N)|-|-|Zwraca sumę elementów w kolekcji.|
|sumBy|O(N)|O(N)|O(N)|-|-|Zwraca sumę wyniki, które są generowane, stosując funkcję do każdego elementu w kolekcji.|
|Tail|-|O(1)|-|-|-|Zwraca listę bez pierwszego elementu.|
|podejmij|-|-|O(N)|-|-|Zwraca elementy do określonej liczby sekwencji.|
|takeWhile|-|-|O(1)|-|-|Zwraca sekwencji, gdy iterowane, generuje elementy sekwencji źródłowej podczas danego predykatu zwraca `true` , a następnie zwraca ma więcej elementów.|
|toArray|-|O(N)|O(N)|O(N)|O(N)|Tworzy tablicę z danej kolekcji.|
|tolist —|O(N)|-|O(N)|O(N)|O(N)|Tworzy listę z danej kolekcji.|
|toseq —|O(1)|O(1)|-|O(1)|O(1)|Tworzy sekwencję z danej kolekcji.|
|TRUNCATE|-|-|O(1)|-|-|Zwraca sekwencję, gdy wyliczone, zwraca więcej niż N elementów.|
|tryFind|O(N)|O(N)|O(N)|O (dziennik N)|-|Wyszukuje element, który spełnia podanego predykatu.|
|tryfindindex —|O(N)|O(N)|O(N)|-|-|Wyszukuje pierwszy element, który spełnia podanego predykatu i zwraca indeks elementu pasującego lub `None` Jeśli nie zawiera żadnego takiego elementu.|
|tryfindkey —|-|-|-|O (dziennik N)|-|Zwraca klucz pierwszego mapowanie w kolekcji, która spełnia podanego predykatu lub zwraca `None` Jeśli nie zawiera żadnego takiego elementu.|
|trypick —|O(N)|O(N)|O(N)|O (dziennik N)|-|Dotyczy dana funkcja kolejnych elementów, zwracanie pierwszego wyniku, gdy funkcja zwraca `Some` dla niektórych wartości. Jeśli żaden taki element istnieje, zwraca operacji `None`.|
|unfold —|-|-|O(N)|-|-|Zwraca sekwencję, która zawiera elementy, które generuje danego obliczeń.|
|unia|-|-|-|-|O (M &#42; dziennika N)|Oblicza sumę dwóch zestawów.|
|unionmany —|-|-|-|-|O (N1 &AMP;#42; N2...)|Oblicza Unii sekwencji zestawów.|
|Rozpakowywanie|O(N)|O(N)|O(N)|-|-|Dzieli listę par na dwie listy.|
|unzip3 —|O(N)|O(N)|O(N)|-|-|Dzieli listę triples na trzy listy.|
|okna|-|-|O(N)|-|-|Zwraca sekwencję daje przesuwanego okna zawierającego elementy, które są pobierane z sekwencji wejściowych. Każde okno jest zwracana jako pierwszą tablicy.|
|ZIP|O(N)|O(N)|O(N)|-|-|Łączy dwie kolekcje w postaci listy pary. Dwie listy muszą mieć takie same długości.|
|zip3 —|O(N)|O(N)|O(N)|-|-|Łączy trzy kolekcji na listę triples. Listy muszą mieć takie same długości.|

## <a name="see-also"></a>Zobacz też
[Typy F#](fsharp-types.md)

[Dokumentacja języka F#](index.md)

