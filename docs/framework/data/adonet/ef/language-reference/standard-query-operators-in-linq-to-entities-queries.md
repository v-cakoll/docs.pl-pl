---
title: Standardowe operatory zapytań w zapytaniach składnika LINQ to Entities
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 76d32db5c81d88db28194da19e722b1a80c1a870
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249147"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardowe operatory zapytań w zapytaniach składnika LINQ to Entities
W zapytaniu należy określić informacje, które mają zostać pobrane ze źródła danych. Zapytanie może również określać, jak te informacje powinny być sortowane, grupowane i ukształtowane przed zwróceniem. LINQ zawiera zestaw standardowych metod zapytań, których można użyć w zapytaniu. Większość z tych metod operuje na sekwencjach; w tym kontekście sekwencja jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> Interfejs <xref:System.Linq.IQueryable%601> lub interfejs. Standardowe zapytania operatorów zapytań obejmują filtrowanie, projekcję, agregację, sortowanie, grupowanie, stronicowanie i nie tylko. Niektóre z często używanych standardowych operatorów zapytań mają dedykowaną składnię słowa kluczowego, dzięki czemu mogą być wywoływane przy użyciu składni wyrażeń zapytania. Wyrażenie zapytania jest innym, bardziej czytelnym sposobem wyrażania zapytania niż odpowiednik oparty na metodzie. Klauzule wyrażenia zapytania są tłumaczone na wywołania metod zapytania w czasie kompilacji. Aby uzyskać listę standardowych operatorów zapytań, które mają równoważne klauzule wyrażenia zapytania, zobacz [Omówienie standardowych operatorów zapytań](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 Nie wszystkie standardowe operatory zapytań są obsługiwane w zapytaniach LINQ to Entities. Aby uzyskać więcej informacji, zobacz [obsługiwane i nieobsługiwane metody LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md). Ten temat zawiera informacje dotyczące standardowych operatorów zapytań, które są specyficzne dla LINQ to Entities. Aby uzyskać więcej informacji o znanych problemach w LINQ to Entities zapytaniach, zobacz [znane problemy i zagadnienia w programie LINQ to Entities](known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Metody projekcji i filtrowania  
 *Projekcja* odnosi się do przekształcenia elementów zestawu wyników w żądany formularz. Na przykład można zaprojektować podzbiór właściwości, które są potrzebne z każdego obiektu w zestawie wyników, można zaprojektować Właściwość i wykonać na niej obliczenia matematyczne lub można zaprojektować cały obiekt z zestawu wyników. Metody projekcji są `Select` i `SelectMany`.  
  
 *Filtrowanie* odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które pasują do określonego warunku. Metoda filtrowania to `Where`.  
  
 Większość przeciążenia metod projekcji i filtrowania jest obsługiwana w LINQ to Entities, z wyjątkiem tych, które akceptują argument pozycyjny.  
  
## <a name="join-methods"></a>Metody join  
 Łączenie jest ważną operacją w zapytaniach, które są przeznaczone dla źródeł danych, które nie mają relacji nawigacji ze sobą. Sprzężenie dwóch źródeł danych to skojarzenie obiektów w jednym źródle danych z obiektami w innym źródle danych, które współużytkują wspólny atrybut lub właściwość. Metody join są `Join` i `GroupJoin`.  
  
 Obsługiwane są większość przeciążeń metod join, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IEqualityComparer%601>. Dzieje się tak, ponieważ nie można przetłumaczyć modułu porównującego na źródło danych.  
  
## <a name="set-methods"></a>Ustaw metody  
 Operacje Set w LINQ to operacje zapytań, które stanowią podstawę ich zestawów wyników na obecność lub brak równoważnych elementów w obrębie tej samej lub innej kolekcji (lub zestawu). Metody Set `All`to, `Any`, `Concat` `Contains` ,,`EqualAll`, ,,`Except`, i .`Union` `DefaultIfEmpty` `Distinct` `Intersect`  
  
 Większość przeciążeń metod set jest obsługiwanych w LINQ to Entities, chociaż istnieją pewne różnice w zachowaniu w porównaniu z LINQ to Objects. Jednakże metody, które używają elementu <xref:System.Collections.Generic.IEqualityComparer%601> nie są obsługiwane, ponieważ nie można przetłumaczyć tego ustawienia na źródło danych.  
  
## <a name="ordering-methods"></a>Kolejność metod  
 Porządkowanie lub sortowanie odwołuje się do kolejności elementów zestawu wyników na podstawie jednego lub większej liczby atrybutów. Określając więcej niż jedno kryterium sortowania, można przerwać powiązania w grupie.  
  
 Obsługiwane są większość przeciążeń metod porządkowania, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IComparer%601>. Dzieje się tak, ponieważ nie można przetłumaczyć modułu porównującego na źródło danych. Metody `OrderBy`sortowania to, `ThenBy`, `OrderByDescending` ,`ThenByDescending`i .`Reverse`  
  
 Ponieważ zapytanie jest wykonywane w źródle danych, zachowanie porządkowania może się różnić od zapytań wykonywanych w środowisku CLR. Wynika to z faktu, że Opcje porządkowania, takie jak porządkowanie przypadku, porządkowanie kanji i porządkowanie wartości null, można ustawić w źródle danych. W zależności od źródła danych Opcje porządkowania mogą generować różne wyniki niż w środowisku CLR.  
  
 W przypadku określenia tego samego selektora kluczy w więcej niż jednej operacji porządkowania zostanie utworzone zduplikowane porządkowanie. To nie jest prawidłowe i zostanie zgłoszony wyjątek.  
  
## <a name="grouping-methods"></a>Metody grupowania  
 Grupowanie odwołuje się do umieszczania danych w grupach, tak aby elementy w każdej grupie miały wspólny atrybut. Metoda grupowania to `GroupBy`.  
  
 Obsługiwane są większość przeciążenia metod grupowania, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IEqualityComparer%601>. Dzieje się tak, ponieważ nie można przetłumaczyć modułu porównującego na źródło danych.  
  
 Metody grupowania są mapowane do źródła danych przy użyciu odrębnego podzapytania dla selektora kluczy. Podzapytanie porównania selektora kluczy jest wykonywane przy użyciu semantyki źródła danych, w tym problemów związanych z porównywaniem `null` wartości.  
  
## <a name="aggregate-methods"></a>Metody agregujące  
 Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Na przykład Obliczanie średniej dziennej temperatury z miesięcznej wartości temperatury dziennej jest operacją agregacji. Metody agregujące to `Aggregate`, `Average`, `Count` `LongCount`,,, i`Sum`. `Max` `Min`  
  
 Obsługiwane są większość przeciążenia metod agregujących. W przypadku zachowania związanego z wartościami null, metody agregujące używają semantyki źródła danych. Zachowanie metod agregacji w przypadku, gdy wartości null są uwzględnione, mogą być różne w zależności od tego, które źródło danych zaplecza jest używane. Zachowanie metody agregacji przy użyciu semantyki źródła danych może być również inne niż oczekiwane w metodach CLR. Na przykład domyślne zachowanie `Sum` metody na SQL Server ma ignorować wszystkie wartości null zamiast zgłaszać wyjątek.  
  
 Wszystkie wyjątki, które wynikają z agregacji, takie jak przepełnienie z `Sum` funkcji, są generowane jako wyjątki ze źródła danych lub Entity Framework wyjątki podczas materializację wyników zapytania.  
  
 Dla tych metod, które obejmują obliczenia w sekwencji, takie jak `Sum` lub `Average`, rzeczywiste obliczenie jest wykonywane na serwerze. W efekcie konwersje typów i utrata dokładności mogą wystąpić na serwerze, a wyniki mogą się różnić od tego, co jest oczekiwane przy użyciu semantyki CLR.  
  
 Domyślne zachowanie metod agregowania dla wartości null/innych niż null jest pokazane w poniższej tabeli:  
  
|Metoda|Brak danych|Wszystkie wartości null|Niektóre wartości null|Brak wartości null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Zwraca wartość null.|Zwraca wartość null.|Zwraca średnią wartości innych niż null w sekwencji.|Oblicza średnią sekwencji wartości liczbowych.|  
|`Count`|Zwraca wartość 0|Zwraca liczbę wartości null w sekwencji.|Zwraca liczbę wartości null i innych niż null w sekwencji.|Zwraca liczbę elementów w sekwencji.|  
|`Max`|Zwraca wartość null.|Zwraca wartość null.|Zwraca maksymalną wartość różną od null w sekwencji.|Zwraca maksymalną wartość w sekwencji.|  
|`Min`|Zwraca wartość null.|Zwraca wartość null.|Zwraca minimalną wartość różną od null w sekwencji.|Zwraca minimalną wartość w sekwencji.|  
|`Sum`|Zwraca wartość null.|Zwraca wartość null.|Zwraca sumę wartości innej niż null w sekwencji.|Oblicza sumę sekwencji wartości liczbowych.|  
  
## <a name="type-methods"></a>Metody typu  
 Dwie metody LINQ, które zajmują się konwersją typu i testowaniem, są obsługiwane w kontekście Entity Framework. Oznacza to, że jedynymi obsługiwanymi typami są typy, które mapują do odpowiedniego typu Entity Framework. Aby zapoznać się z listą tych typów, zobacz [koncepcyjne typy modeli (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl). Metody typu są `Convert` i `OfType`.  
  
 `OfType`jest obsługiwana w przypadku typów jednostek. `Convert`jest obsługiwana w przypadku typów pierwotnych modelu koncepcyjnego.  Obsługiwane są `as` również metody i.`is` C#  
  
## <a name="paging-methods"></a>Metody stronicowania  
 Operacje stronicowania zwracają pojedynczy element lub wiele elementów z sekwencji. Obsługiwane metody stronicowania to `First` `Single`, `FirstOrDefault` `SingleOrDefault` ,,`Take`, i. `Skip`  
  
 Niektóre metody stronicowania nie są obsługiwane z powodu niemożności mapowania funkcji do źródła danych lub braku jawnej kolejności zestawów w źródle danych. Metody, które zwracają wartość domyślną, są ograniczone do typów pierwotnych modelu koncepcyjnego i typów referencyjnych z wartościami domyślnymi null. Metody stronicowania wykonywane na pustej sekwencji zwróci wartość null.  
  
## <a name="see-also"></a>Zobacz także

- [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](supported-and-unsupported-linq-methods-linq-to-entities.md)
- [Standardowe operatory zapytań — przegląd](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))
