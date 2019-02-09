---
title: Standardowe operatory zapytań w technologii LINQ do zapytań jednostki
ms.date: 08/21/2018
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: 558ee35c433475bf3b2d5a3cdb4b24b612197c13
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904648"
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardowe operatory zapytań w technologii LINQ do zapytań jednostki
W zapytaniu należy określić informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje powinny można sortowane, grupowane i kształtowane przed zwróceniem. LINQ zapewnia zestaw metod standardowego zapytania, które można użyć w zapytaniu. Większość z tych metod działają na sekwencje; w tym kontekście sekwencji jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. Funkcjonalność zapytań operatorów standardowej kwerendy obejmuje filtrowania, projekcji, agregacji, sortowanie, grupowanie, stronicowanie i więcej. Niektórych często używane standardowego zapytania, operatory są wyposażone w dedykowane składni słowa kluczowego, dzięki czemu można wywołać przy użyciu składni wyrażeń zapytania. Wyrażenie kwerendy jest inny, bardziej czytelny sposób wyrażania kwerendę, niż odpowiednik oparte na metodzie. Klauzule wyrażenia zapytania są tłumaczone na wywołania do metody zapytania w czasie kompilacji. Aby uzyskać listę standardowych operatorów zapytań, które mają klauzule wyrażenia zapytania równoważne, zobacz [standardowe operatory zapytań — Przegląd](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).  
  
 Nie wszystkie standardowe operatory zapytań są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. Aby uzyskać więcej informacji, zobacz [obsługiwane i nieobsługiwane LINQ metody (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Ten temat zawiera informacje o standardowych operatorów zapytań, które są specyficzne dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Aby uzyskać więcej informacji o znanych problemach w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, zobacz [znane problemy i zagadnienia dotyczące w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Prognoza i filtrowanie metody  
 *Projekcja* odwołuje się do przekształcania elementów zestawu w formie żądanego wyników. Na przykład można poddawać projekcji podzbiór właściwości muszą z każdego obiektu w wyniku ustawisz, można właściwość projektu i przeprowadzania obliczeń matematycznych lub można poddawać projekcji cały obiekt z zestawu wyników. Metody rzutowania są `Select` i `SelectMany`.  
  
 *Filtrowanie* odwołuje się do operacji ograniczyć zestaw wyników, aby zawiera tylko te elementy, które pasują do określonego warunku. Metoda filtrowania jest `Where`.  
  
 Większość przeciążenia projekcji i filtrowania metody są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], z wyjątkiem tych, które akceptują argument pozycyjny.  
  
## <a name="join-methods"></a>Dołącz do metody  
 Łączenie jest operacją ważne w zapytaniach, przeznaczonych dla źródeł danych, które mają relacje nie można nawigować do siebie nawzajem. Przyłączenia dwóch źródeł danych jest skojarzenie obiektów w jednym źródle danych z obiektów w źródle danych, które mają wspólny atrybut lub właściwość. Metody to join `Join` i `GroupJoin`.  
  
 Większość przeciążenia metody przyłączenie do są obsługiwane, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IEqualityComparer%601>. Jest to spowodowane modułu porównującego nie można przetłumaczyć ze źródłem danych.  
  
## <a name="set-methods"></a>Ustaw metody  
 Operacje na zestawie w składniku LINQ to operacje zapytań, które oprzeć ich zestawów wyników na obecność lub Brak elementów równoważnych w tej samej lub innej kolekcji (lub zestaw). Metody set są `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, i `Union`.  
  
 Większość przeciążenia metod zestawu są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], ale istnieją pewne różnice w zachowaniu w porównaniu do programu LINQ do obiektów. Jednak ustawić metody, które używają <xref:System.Collections.Generic.IEqualityComparer%601> nie są obsługiwane, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.  
  
## <a name="ordering-methods"></a>Metody sortowania  
 Porządkowanie i sortowania, odnosi się do porządkowania elementów zestawu wyników, w oparciu o jeden lub więcej atrybutów. Określając z więcej niż jednego kryterium sortowania może przerwać ties w obrębie grupy.  
  
 Większość przeciążenia metod sortowania są obsługiwane, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IComparer%601>. Jest to spowodowane modułu porównującego nie można przetłumaczyć ze źródłem danych. Metody sortowania są `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, i `Reverse`.  
  
 Ponieważ zapytanie jest wykonywane w źródle danych, zachowanie szeregowania może różnić się od zapytania wykonywane w środowisku CLR. Jest to spowodowane można ustawić kolejność opcje, takie jak przypadek, w kolejności, kanji kolejności i kolejność wartości null w źródle danych. W zależności od źródła danych te opcje sortowania może dawać różne wyniki niż w CLR.  
  
 Jeśli określisz tego samego selektora kluczy w więcej niż jedną operację szeregowania zduplikowane porządkowanie zostaną wygenerowane. To nie jest prawidłowa, i zostanie zgłoszony wyjątek.  
  
## <a name="grouping-methods"></a>Grupowanie metody  
 Grupowanie odnosi się do umieszczenia danych w grupy, tak aby elementy w każdej grupie udostępniać wspólny atrybut. Ta metoda grupowania jest `GroupBy`.  
  
 Większość przeciążenia metod grupowania są obsługiwane, z wyjątkiem tych, które używają <xref:System.Collections.Generic.IEqualityComparer%601>. Jest to spowodowane modułu porównującego nie można przetłumaczyć ze źródłem danych.  
  
 Metody grupowania są mapowane na źródło danych przy użyciu różnych podzapytaniu dla selektora kluczy. Porównanie selektora kluczy o podrzędnych zapytanie jest wykonywane przy użyciu semantyki źródło danych, w tym zagadnienia związane z porównanie `null` wartości.  
  
## <a name="aggregate-methods"></a>Metody agregacji  
 Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Na przykład obliczanie średniej temperatury codzienne z miesięcznej codziennie wartości temperatury jest operacją agregacji. Metody agregacji są `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum`.  
  
 Większość przeciążenia metody agregacji są obsługiwane. Zachowania związane z wartości null metody agregacji korzystają bezpośrednio z semantyki źródła danych. Zachowanie metody agregacji w przypadku wartości null mogą się różnić, w zależności od używanego źródła danych zaplecza. Zachowanie metody agregacji za pomocą semantyki źródła danych może być również różni się od oczekiwań w metodach CLR. Na przykład domyślne zachowanie dla `Sum` metodą w programie SQL Server jest ignorują wszelkie wartości null zamiast zgłaszać wyjątek.  
  
 Wszelkie wyjątki, które wynikają z agregacji, takich jak przepełnienie z `Sum` funkcji, zostaną zgłoszone jako źródła danych czy wyjątki platformy Entity Framework podczas materializacja wyników zapytania.  
  
 Dla tych metod, które obejmują obliczenia sekwencji, takich jak `Sum` lub `Average`, faktyczne obliczenie jest wykonywane na serwerze. Co w efekcie konwersje typów i może dojść do utraty dokładności na serwerze, a wyniki mogą się różnić od oczekiwanej, używając semantyki CLR.  
  
 Domyślne zachowanie metody agregacji o wartości null/innych niż null wartości zostały przedstawione w poniższej tabeli:  
  
|Metoda|Brak danych|Wszystkie wartości null|Niektóre wartości null|Nie wartości null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Zwraca wartość null.|Zwraca wartość null.|Zwraca średnią z wartości innych niż null w sekwencji.|Oblicza średnią sekwencję wartości liczbowych.|  
|`Count`|Zwraca wartość 0|Zwraca liczbę wartości null w sekwencji.|Zwraca liczbę wartości null i innych niż null w sekwencji.|Zwraca liczbę elementów w sekwencji.|  
|`Max`|Zwraca wartość null.|Zwraca wartość null.|Zwraca maksymalną wartość inną niż null w sekwencji.|Zwraca maksymalną wartość w sekwencji.|  
|`Min`|Zwraca wartość null.|Zwraca wartość null.|Zwraca minimalną wartość inną niż null w sekwencji.|Zwraca minimalną wartość w sekwencji.|  
|`Sum`|Zwraca wartość null.|Zwraca wartość null.|Zwraca sumę wartości innej niż null w sekwencji.|Oblicza sumę sekwencję wartości liczbowych.|  
  
## <a name="type-methods"></a>Typ metody  
 Oba te dwie metody LINQ, które zajmują się konwersji typu i testowanie są obsługiwane w kontekście programu Entity Framework. Oznacza to, że tylko obsługiwane typy to typy, które mapują do odpowiedniego typu Entity Framework. Aby uzyskać listę tych typów, zobacz [koncepcyjny modelu typy (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl). Metody typu są `Convert` i `OfType`.  
  
 `OfType` jest obsługiwane dla typów jednostek. `Convert` jest obsługiwane dla typów pierwotnych modelu koncepcyjnego.  C# `is` i `as` metody są również obsługiwane.  
  
## <a name="paging-methods"></a>Metody stronicowania  
 Operacja stronicowania zwrócić pojedynczy element lub wiele elementów z sekwencji. Obsługiwane metody stronicowania to `First`, `FirstOrDefault`, `Single`, `SingleOrDefault`, `Skip`, i `Take`.  
  
 Wiele metod stronicowania nie są obsługiwane ze względu na z brakiem, aby mapować funkcje do źródła danych lub brak niejawnego porządkowanie zestawów w źródle danych. Metody, które zwracają wartość domyślna jest ograniczony do typów pierwotnych modelu koncepcyjnego i typy odwołań przy użyciu ustawień domyślnych wartości null. Metody stronicowania, które są wykonywane na pustą sekwencją będzie zwracać wartość null.  
  
## <a name="see-also"></a>Zobacz także
- [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)
- [Standardowe operatory zapytań — przegląd](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))
