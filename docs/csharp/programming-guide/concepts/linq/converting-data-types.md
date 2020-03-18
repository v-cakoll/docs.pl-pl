---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 328c790a1a360907c91f69b3b6330b0b25eb414b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347202"
---
# <a name="converting-data-types-c"></a>Konwertowanie typów danych (C#)
Metody konwersji zmieniają typ obiektów wejściowych.

 Operacje konwersji w kwerendach LINQ są przydatne w różnych aplikacjach. Oto kilka przykładów:

- Metoda <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> może służyć do ukrycia implementacji niestandardowej typu standardowego operatora kwerendy.

- Metoda <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> może służyć do włączania kolekcji niesparametryzowanych dla LINQ zapytań.

- The <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> i metody mogą służyć do wymuszenia natychmiastowego wykonywania kwerendy zamiast odroczyć go, dopóki kwerenda nie zostanie wyliczona.

## <a name="methods"></a>Metody
 W poniższej tabeli wymieniono standardowe metody operatora kwerendy, które wykonują konwersje typu danych.

 Metody konwersji w tej tabeli, których nazwy zaczynają się od "As", zmieniają statyczny typ kolekcji źródłowej, ale nie wyliczają jej. Metody, których nazwy zaczynają się od "Do" wyliczyć kolekcji źródłowej i umieścić elementy w odpowiednim typie kolekcji.

|Nazwa metody|Opis|Składnia wyrażenia kwerendy c#|Więcej informacji|
|-----------------|-----------------|---------------------------------|----------------------|
|Asenumerable|Zwraca dane wejściowe <xref:System.Collections.Generic.IEnumerable%601>wpisane jako .|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|
|Asqueryable|Konwertuje (ogólny) <xref:System.Collections.IEnumerable> na <xref:System.Linq.IQueryable>(ogólny) .|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|
|Rzutowanie|Rzutuje elementy kolekcji do określonego typu.|Użyj jawnie wpisanej zmiennej zakresu. Przykład:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|
|Oftype|Filtruje wartości, w zależności od ich zdolności do rzutowania do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|Toarray|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|
|Todictionary|Umieszcza elementy <xref:System.Collections.Generic.Dictionary%602> w oparciu o funkcję selektora kluczy. Ta metoda wymusza wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|
|Tolist|Konwertuje kolekcję na plik <xref:System.Collections.Generic.List%601>. Ta metoda wymusza wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|
|Tolookup|Umieszcza elementy <xref:System.Linq.Lookup%602> w słowniku (jeden-do-wielu) na podstawie funkcji selektora kluczy. Ta metoda wymusza wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia kwerendy

Poniższy przykład kodu używa jawnie wpisane zmiennej zakresu do rzutowania typu do podtypu przed uzyskując dostęp do elementu członkowskiego, który jest dostępny tylko na podtyp.

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
- [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md)
- [z klauzuli](../../../language-reference/keywords/from-clause.md)
- [Wyrażenia zapytań LINQ](../../../linq/index.md)
- [Jak zapytanie ArrayList z LINQ (C#)](./how-to-query-an-arraylist-with-linq.md)
