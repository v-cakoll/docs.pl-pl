---
title: Konwertowanie typów danych (C#)
ms.date: 07/20/2015
ms.assetid: 46e5682f-77a1-4302-8f93-a2b53c408808
ms.openlocfilehash: 374ce15b8329c02c6b496a276a40fd9a60596e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33335825"
---
# <a name="converting-data-types-c"></a>Konwertowanie typów danych (C#)
Metody konwersji Zmień typ wejściowy obiektów.  
  
 Konwersja operacje kwerend LINQ są przydatne w wielu aplikacjach. Poniżej przedstawiono kilka przykładów:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metody można użyć do ukrywania typ implementacji niestandardowego operatora standardowej kwerendy.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> — Metoda można włączyć kolekcji bez parametrów na potrzeby zapytań LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metod można użyć, aby wymusić wykonanie zapytania bezpośredniego zamiast odkładanie go, dopóki wyliczeniu zapytania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli wymieniono metody — operator zapytań standardowe, wykonujących konwersji typu danych.  
  
 Zmień typ statyczny kolekcji źródłowej metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako", ale nie wyliczyć. Typ metody, których nazwy rozpoczynają się od "Do wyliczyć kolekcji źródłowej i elementy do odpowiedniej kolekcji".  
  
|Nazwa metody|Opis|Składnia wyrażenia zapytania C#|Więcej informacji|  
|-----------------|-----------------|---------------------------------|----------------------|  
|AsEnumerable|Zwraca dane wejściowe typu <xref:System.Collections.Generic.IEnumerable%601>.|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Rzutowanie|Rzutuje elementy kolekcji do określonego typu.|Można użyć zmiennej zakresu jawnie typu. Na przykład:<br /><br /> `from string str in words`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Filtruje wartości, w zależności od ich możliwości można rzutować na określony typ.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|toArray|Konwertuje kolekcję na tablicę. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|tolist —|Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) oparte na funkcji selektora kluczy. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 Poniższy przykład kodu wykorzystuje zmiennej zakresu jawnie określone typy do rzutowania typu z podtypem przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko na podtyp.  
  
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
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [from, klauzula](../../../../csharp/language-reference/keywords/from-clause.md)  
 [Wyrażenia zapytań LINQ](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Porady: zapytanie w ArrayList za pomocą LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
