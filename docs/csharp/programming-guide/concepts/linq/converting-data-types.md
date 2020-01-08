---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347202"
---
# <a name="converting-data-types-c"></a>Konwertowanie typów danych (C#)
Metody konwersji zmieniają typ obiektów wejściowych.

 Operacje konwersji w zapytaniach LINQ są przydatne w różnych aplikacjach. Poniżej przedstawiono kilka przykładów:

- Metoda <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> może służyć do ukrycia niestandardowej implementacji standardowego operatora zapytań.

- Za pomocą metody <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> można włączyć kolekcje niesparametryzowane dla zapytań LINQ.

- Metody <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>i <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> mogą być używane do wymuszenia natychmiastowego wykonania zapytania, zamiast odliczenia go do momentu wyliczenia zapytania.

## <a name="methods"></a>Metody
 W poniższej tabeli wymieniono standardowe metody operatorów zapytań, które wykonują konwersje typów danych.

 Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają typ statyczny kolekcji źródłowej, ale nie są wyliczane. Metody, których nazwy zaczynają się od "do", wyliczają kolekcję źródłową i umieszczają elementy w odpowiednim typie kolekcji.

|Nazwa metody|Opis|C#Składnia wyrażenia zapytania|Więcej informacji|
|-----------------|-----------------|---------------------------------|----------------------|
|AsEnumerable|Zwraca dane wejściowe wpisane jako <xref:System.Collections.Generic.IEnumerable%601>.|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|AsQueryable|Konwertuje (ogólne) <xref:System.Collections.IEnumerable> na (ogólne) <xref:System.Linq.IQueryable>.|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Rzutowanie|Rzutuje elementy kolekcji na określony typ.|Użyj jawnie wpisanej zmiennej zakresu. Na przykład:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|OfType|Filtruje wartości w zależności od ich zdolności do rzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|ToArray —|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|ToDictionary|Umieszcza elementy w <xref:System.Collections.Generic.Dictionary%602> na podstawie funkcji selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|ToList —|Konwertuje kolekcję na <xref:System.Collections.Generic.List%601>. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|ToLookup|Umieszcza elementy w <xref:System.Linq.Lookup%602> (słownik jeden-do-wielu) na podstawie funkcji selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Standardowe operatory zapytań — OmówienieC#()](./standard-query-operators-overview.md)
- [from, klauzula](../../../language-reference/keywords/from-clause.md)
- [Wyrażenia zapytania LINQ](../../../linq/index.md)
- [Jak zbadać ArrayList za pomocą LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)
