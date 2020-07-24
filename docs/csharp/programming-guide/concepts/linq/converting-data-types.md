---
title: Konwertowanie typów danych (C#)
description: Metody konwersji zmieniają typ obiektów wejściowych. Zobacz operacje konwersji w zapytaniach LINQ w języku C#, takie jak wyliczalne. AsEnumerable i wyliczalne. OfType.
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 3291690f9aaee945ca7feb04ebbc676db2612894
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105494"
---
# <a name="converting-data-types-c"></a>Konwertowanie typów danych (C#)
Metody konwersji zmieniają typ obiektów wejściowych.

 Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach. Poniżej przedstawiono kilka przykładów:

- <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>Metoda może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.

- <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType>Metoda może służyć do włączenia kolekcji niesparametryzowanej dla zapytań LINQ.

- <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>Metody, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType> , <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> i <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> mogą być używane do wymuszenia natychmiastowego wykonania zapytania zamiast odliczenia go do momentu wyliczenia zapytania.

## <a name="methods"></a>Metody
 W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.

 Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane. Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.

|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|
|-----------------|-----------------|---------------------------------|----------------------|
|AsEnumerable|Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601> .|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (rodzajowy) <xref:System.Linq.IQueryable> .|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Rzutowanie|Rzutuje elementy kolekcji na określony typ.|Użyj jawnie wpisanej zmiennej zakresu. Na przykład:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray —|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> oparciu o funkcję selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList —|Konwertuje kolekcję na <xref:System.Collections.Generic.List%601> . Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) w oparciu o funkcję selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania

Poniższy przykład kodu używa zmiennej jawnie określonego zakresu do rzutowania typu na podtyp przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko dla podtypu.

```csharp
class Plant
{
    public string Name { get; set; }
}

class CarnivorousPlant : Plant
{
    public string TrapType { get; set; }
}

static void Cast()
{
    Plant[] plants = new Plant[] {
        new CarnivorousPlant { Name = "Venus Fly Trap", TrapType = "Snap Trap" },
        new CarnivorousPlant { Name = "Pitcher Plant", TrapType = "Pitfall Trap" },
        new CarnivorousPlant { Name = "Sundew", TrapType = "Flypaper Trap" },
        new CarnivorousPlant { Name = "Waterwheel Plant", TrapType = "Snap Trap" }
    };

    var query = from CarnivorousPlant cPlant in plants
                where cPlant.TrapType == "Snap Trap"
                select cPlant;

    foreach (Plant plant in query)
        Console.WriteLine(plant.Name);

    /* This code produces the following output:

        Venus Fly Trap
        Waterwheel Plant
    */
}
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Linq>
- [Standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md)
- [Klauzula From](../../../language-reference/keywords/from-clause.md)
- [Wyrażenia zapytania LINQ](../../../linq/index.md)
- [Jak zbadać ArrayList za pomocą LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)
