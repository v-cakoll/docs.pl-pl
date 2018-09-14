---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 54ef612ad4e92058d9af4d96b7b3cde9732b2f9c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45585749"
---
# <a name="converting-data-types-c"></a>Konwertowanie typów danych (C#)
Metody konwersji zmienić typ danych wejściowych obiektów.  
  
 Operacje konwersji w zapytaniach LINQ są przydatne w wielu różnych aplikacji. Poniżej przedstawiono kilka przykładów:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda może służyć do ukrywanie niestandardowych implementacji standardowego operatora zapytania typu.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda może służyć do włączenia kolekcji zdefiniowanych na potrzeby zapytań LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody może służyć do wymuszenia wykonanie zapytania bezpośredniego zamiast odracza ją do czasu wyliczenia zapytania.  
  
## <a name="methods"></a>Metody  
 Poniższa tabela zawiera listę metod standardowych operatorów zapytań, które wykonują konwersje typów danych.  
  
 Metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako" Zmiana typu statycznego kolekcji źródłowej, ale nie wyliczyć. Typ metody, których nazwy rozpoczynają się od "Do wyliczania kolekcji źródłowej i umieść elementy w odpowiedniej kolekcji".  
  
|Nazwa metody|Opis|Składnia wyrażeń zapytania języka C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Zwraca dane wejściowe wpisanych w formie <xref:System.Collections.Generic.IEnumerable%601>.|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Rzutowanie|Rzutuje elementy kolekcji do określonego typu.|Można użyć zmiennej jawnie wpisanych zakresu. Na przykład:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Służy do przefiltrowania wartości, w zależności od ich możliwości, można rzutować do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|Tolist —|Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 Poniższy przykład kodu używa zmiennej zakresu jawnie wpisane rzutowanie typu podtypem przed uzyskaniem dostępu do składowej, która jest dostępna tylko na podtypu.  
  
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
- [Omówienie operatorów standardowej kwerendy (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [from, klauzula](../../../../csharp/language-reference/keywords/from-clause.md)  
- [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Porady: zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
