---
title: Standardowe operatory zapytań w składniku LINQ to Entities zapytań
ms.date: 03/30/2017
ms.assetid: 7fa55a9b-6219-473d-b1e5-2884a32dcdff
ms.openlocfilehash: a65f759ef51d34cc3ac6d37fe3575b9e89aadf7c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="standard-query-operators-in-linq-to-entities-queries"></a>Standardowe operatory zapytań w składniku LINQ to Entities zapytań
W zapytaniu możesz określić informacje, które mają zostać pobrane ze źródła danych. Zapytania można również określić, jak te informacje sortowania, grupowane i w kształcie przed zwróceniem jest. LINQ udostępnia zestaw metod standardowych zapytania, które można użyć w zapytaniu. Większość tych metod działać na sekwencji; w tym kontekście sekwencji jest obiektem, którego typ implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu lub <xref:System.Linq.IQueryable%601> interfejsu. Funkcja zapytania operatorów standardowej kwerendy obejmuje filtrowania, projekcji agregacji, sortowanie, grupowanie, stronicowania i więcej. Standardowe operatory są wyposażone w dedykowane składni słowa kluczowego, dzięki czemu można wywołać przy użyciu składni wyrażeń zapytania zapytań niektórych często używane. Wyrażenia zapytania jest inny, bardziej czytelny sposobem express zapytania niż równoważne oparte na metodzie. Klauzule wyrażenia zapytania są przekształcane na wywołania metody zapytań w czasie kompilacji. Listę standardowych operatorów zapytań zawierających klauzule wyrażenia zapytania równoważne zawiera [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
 Nie wszystkie standardowe operatory zapytań są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania. Aby uzyskać więcej informacji, zobacz [obsługiwane i nieobsługiwane metody LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md). Ten temat zawiera informacje o standardowych operatorów zapytań, które są specyficzne dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)]. Aby uzyskać więcej informacji o znanych problemach w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytań, zobacz [znanych problemów i uwagi w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md).  
  
## <a name="projection-and-filtering-methods"></a>Filtrowanie metod i projekcji  
 *Projekcja* odwołuje się do przekształcania elementy zestawu w formie żądanego wyników. Na przykład można wyświetlać podzbiór właściwości muszą z każdego obiektu w wyniku ustawisz, możesz właściwości projektu i wykonać obliczenia matematyczne na nim lub można wyświetlać cały obiekt z zestawu wyników. Metody projekcji `Select` i `SelectMany`.  
  
 *Filtrowanie* odwołuje się do operacji ograniczyć zestaw wyników do zawierać tylko elementy, spełniające określony warunek. Metoda filtrowania jest `Where`.  
  
 Większość przeciążeń projekcji i filtrowanie metody są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], z wyjątkiem tych, które akceptują argument pozycyjny.  
  
## <a name="join-methods"></a>Dołącz do metody  
 Sprzęganie jest ważne operacji w zapytaniach, które odnoszą się do źródła danych, których nie można nawigować relacje między sobą. Sprzężenia dwóch źródeł danych jest skojarzenie obiektów w jedno źródło danych z obiektami w źródle danych, które współużytkują wspólne atrybutu lub właściwości. Metody sprzężenia `Join` i `GroupJoin`.  
  
 Większość przeciążenia metody sprzężenia są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IEqualityComparer%601>. Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.  
  
## <a name="set-methods"></a>Ustaw metody  
 Operacje na zestawie w składniku LINQ to operacji zapytania, które podstawą ich zestawów wyników obecności lub braku równoważne elementów w tym samym lub w innej kolekcji (lub zestawu). Metody set `All`, `Any`, `Concat`, `Contains`, `DefaultIfEmpty`, `Distinct`, `EqualAll`, `Except`, `Intersect`, i `Union`.  
  
 Większość przeciążenia metody set są obsługiwane w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], ale istnieją pewne różnice w zachowaniu w porównaniu do LINQ do obiektów. Jednak ustawić metody, które używają <xref:System.Collections.Generic.IEqualityComparer%601> nie są obsługiwane, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.  
  
## <a name="ordering-methods"></a>Metody sortowania  
 Porządkowanie lub sortowania, odwołuje się do kolejność elementów na podstawie atrybutów co najmniej jeden zestaw wyników. Określając więcej niż jednego kryterium sortowania, mogą być dzielone powiązania w grupie.  
  
 Większość przeciążenia metody sortowania są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IComparer%601>. Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych. Metody sortowania są `OrderBy`, `OrderByDescending`, `ThenBy`, `ThenByDescending`, i `Reverse`.  
  
 Ponieważ zapytanie jest wykonywane w źródle danych, porządkowania zachowanie może różnić się od zapytania wykonywane w środowisku CLR. Jest to spowodowane porządkowania opcje, takie jak przypadku porządkowania kanji kolejności i kolejność wartości null, można ustawić w źródle danych. W zależności od źródła danych te opcje sortowania może wygenerować różne wyniki niż w środowisku CLR.  
  
 Jeśli określisz tego samego selektora kluczy w więcej niż jedną operację porządkowania zostaną utworzone zduplikowane porządkowania. To nie jest prawidłowy i zostanie wygenerowany wyjątek.  
  
## <a name="grouping-methods"></a>Grupowanie metody  
 Grupowanie odwołuje się do umieszczenia danych w grupy tak, aby Wspólny atrybut Udostępnianie elementów w każdej grupie. Metoda grupowania jest `GroupBy`.  
  
 Większość przeciążenia metody grupowania są obsługiwane, z wyjątkiem tych, które korzystają <xref:System.Collections.Generic.IEqualityComparer%601>. Jest tak, ponieważ nie można przetłumaczyć modułu porównującego do źródła danych.  
  
 Metody grupowania są mapowane do źródła danych przy użyciu różnych podzapytania dla selektora kluczy. Zapytanie podrzędne porównania selektora kluczy jest wykonywane przy użyciu semantyki źródła danych, w tym zagadnienia związane z porównanie `null` wartości.  
  
## <a name="aggregate-methods"></a>Metody agregacji  
 Operacja agregacji oblicza pojedynczą wartość z kolekcji wartości. Na przykład obliczanie średnia temperatura codzienne z miesięcznej codziennie temperatury wartości jest operacją agregacji. Metody agregacji są `Aggregate`, `Average`, `Count`, `LongCount`, `Max`, `Min`, i `Sum`.  
  
 Większość przeciążenia metody agregacji są obsługiwane. Zachowania związane z wartości null metody agregacji korzysta z semantyki źródła danych. Zachowanie metody agregacji w przypadku wartości null, mogą się różnić, w zależności od używanego źródła danych zaplecza. Metoda agregacji zachowanie za pomocą semantyki źródła danych może być również inny niż oczekiwano z metody CLR. Na przykład, domyślne zachowanie dla `Sum` metody na serwerze SQL ma ignorować wszystkie wartości null zamiast generowania wyjątku.  
  
 Wszelkie wyjątki wynikających z agregacji, takie jak przepełnienie z `Sum` działać i będą zgłaszane jako źródło danych czy wyjątki Entity Framework podczas materialization wyników zapytania.  
  
 Dla tych metod, które obejmują obliczenia w sekwencji, takich jak `Sum` lub `Average`, rzeczywiste obliczenia jest wykonywane na serwerze. W związku z tym konwersje typów na serwerze może wystąpić utrata dokładności i wyniki mogą różnić się od oczekiwanej, używając semantyki CLR.  
  
 W poniższej tabeli przedstawiono to domyślne zachowanie metody agregacji wartości null/inne niż null:  
  
|Metoda|Brak danych|Wszystkie wartości null|Niektóre wartości null|Nie wartości null|  
|------------|-------------|---------------------|----------------------|--------------------|  
|`Average`|Zwraca wartość null.|Zwraca wartość null.|Zwraca średnią z wartości inne niż null w sekwencji.|Oblicza średnią sekwencję wartości liczbowych.|  
|`Count`|Zwraca wartość 0|Zwraca liczbę wartości null w sekwencji.|Zwraca liczbę wartości null i innych niż null w sekwencji.|Zwraca liczbę elementów w sekwencji.|  
|`Max`|Zwraca wartość null.|Zwraca wartość null.|Zwraca maksymalną wartość inną niż null w sekwencji.|Zwraca maksymalną wartość w sekwencji.|  
|`Min`|Zwraca wartość null.|Zwraca wartość null.|Zwraca minimalną wartość inną niż null w sekwencji.|Zwraca minimalną wartość w sekwencji.|  
|`Sum`|Zwraca wartość null.|Zwraca wartość null.|Zwraca sumę wartości innych niż null w sekwencji.|Oblicza sumę sekwencję wartości liczbowych.|  
  
## <a name="type-methods"></a>Metody typu  
 Te dwie metody LINQ, które zajmują się konwersji typu i testowania są obsługiwane w kontekście [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)]. Oznacza to, że tylko obsługiwane typy to typy, które mapują do odpowiedniego [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] typu. Aby uzyskać listę tych typów, zobacz [typu modelu koncepcyjnego (CSDL)](http://msdn.microsoft.com/library/987b995f-e429-4569-9559-b4146744def4). Metody typu są `Convert` i `OfType`.  
  
 `OfType` jest obsługiwana dla typów jednostek. `Convert` jest obsługiwana dla typów pierwotnych modelu koncepcyjnego.  C# `is` i `as` metody również są obsługiwane.  
  
## <a name="paging-methods"></a>Metody stronicowania  
 Operacja stronicowania zwrócić element jednej, określonej sekwencji. Metody elementu `ElementAt`, `First`, `FirstOrDefault`, `Last`, `LastOrDefault`, `Single`, `Skip`, `Take`, `TakeWhile`.  
  
 Wiele metod stronicowania nie są obsługiwane ze względu na niemożność mapowania funkcji do źródła danych lub brak niejawnego porządkowanie zestawów w źródle danych. Metody, które zwracają wartości domyślne są ograniczone do modelu koncepcyjnego typy pierwotne i typy referencyjne przy użyciu ustawień domyślnych wartości null. Metody stronicowania, które są wykonywane na pustej sekwencji zwróci wartość null.  
  
## <a name="see-also"></a>Zobacz też  
 [Metody obsługiwane i nieobsługiwane LINQ (LINQ to Entities)](../../../../../../docs/framework/data/adonet/ef/language-reference/supported-and-unsupported-linq-methods-linq-to-entities.md)  
 [Standardowe operatory zapytań — przegląd](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2)
