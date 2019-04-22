---
title: Konwertowanie typów danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
ms.openlocfilehash: ad9594cabe0e2382ae4e19f2541eec4aa74ccd75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837055"
---
# <a name="converting-data-types-visual-basic"></a>Konwertowanie typów danych (Visual Basic)
Metody konwersji zmienić typ danych wejściowych obiektów.  
  
 Operacje konwersji w zapytaniach LINQ są przydatne w wielu różnych aplikacji. Poniżej przedstawiono kilka przykładów:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metoda może służyć do ukrywanie niestandardowych implementacji standardowego operatora zapytania typu.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> Metoda może służyć do włączenia kolekcji zdefiniowanych na potrzeby zapytań LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metody może służyć do wymuszenia wykonanie zapytania bezpośredniego zamiast odracza ją do czasu wyliczenia zapytania.  
  
## <a name="methods"></a>Metody  
 Poniższa tabela zawiera listę metod standardowych operatorów zapytań, które wykonują konwersje typów danych.  
  
 Metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako" Zmiana typu statycznego kolekcji źródłowej, ale nie wyliczyć. Typ metody, których nazwy rozpoczynają się od "Do wyliczania kolekcji źródłowej i umieść elementy w odpowiedniej kolekcji".  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|Zwraca dane wejściowe wpisanych w formie <xref:System.Collections.Generic.IEnumerable%601>.|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Rzutowanie|Rzutuje elementy kolekcji do określonego typu.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Służy do przefiltrowania wartości, w zależności od ich możliwości, można rzutować do określonego typu.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|ToArray|Konwertuje kolekcję na tablicę. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|Tolist —|Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji. Ta metoda wymusza wykonanie zapytania.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 Poniższy przykład kodu wykorzystuje `From As` klauzuli rzutowanie typu podtypem przed uzyskaniem dostępu do składowej, która jest dostępna tylko na podtypu.  
  
```vb  
Class Plant  
    Public Property Name As String  
End Class  
  
Class CarnivorousPlant  
    Inherits Plant  
    Public Property TrapType As String  
End Class  
  
Sub Cast()  
  
    Dim plants() As Plant = {   
        New CarnivorousPlant With {.Name = "Venus Fly Trap", .TrapType = "Snap Trap"},   
        New CarnivorousPlant With {.Name = "Pitcher Plant", .TrapType = "Pitfall Trap"},   
        New CarnivorousPlant With {.Name = "Sundew", .TrapType = "Flypaper Trap"},   
        New CarnivorousPlant With {.Name = "Waterwheel Plant", .TrapType = "Snap Trap"}}  
  
    Dim query = From plant As CarnivorousPlant In plants   
                Where plant.TrapType = "Snap Trap"   
                Select plant  
  
    Dim sb As New System.Text.StringBuilder()  
    For Each plant In query  
        sb.AppendLine(plant.Name)  
    Next  
  
    ' Display the results.  
    MsgBox(sb.ToString())  
  
    ' This code produces the following output:  
  
    ' Venus Fly Trap  
    ' Waterwheel Plant  
  
End Sub  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Linq>
- [Omówienie operatorów standardowej kwerendy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [From, klauzula](../../../../visual-basic/language-reference/queries/from-clause.md)
- [Instrukcje: Zapytanie w ArrayList za pomocą LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
