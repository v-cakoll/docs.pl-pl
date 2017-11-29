---
title: "Konwertowanie typów danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b0cf1ab-de48-4c6e-9f00-05b40fade46e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5fb0e9dfb0f1fb882116449757ed0f0bf9029b39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="converting-data-types-visual-basic"></a>Konwertowanie typów danych (Visual Basic)
Metody konwersji Zmień typ wejściowy obiektów.  
  
 Konwersja operacje kwerend LINQ są przydatne w wielu aplikacjach. Poniżej przedstawiono kilka przykładów:  
  
-   <xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType> Metody można użyć do ukrywania typ implementacji niestandardowego operatora standardowej kwerendy.  
  
-   <xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType> — Metoda można włączyć kolekcji bez parametrów na potrzeby zapytań LINQ.  
  
-   <xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>, I <xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType> metod można użyć, aby wymusić wykonanie zapytania bezpośredniego zamiast odkładanie go, dopóki wyliczeniu zapytania.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli wymieniono metody — operator zapytań standardowe, wykonujących konwersji typu danych.  
  
 Zmień typ statyczny kolekcji źródłowej metody konwersji w tej tabeli, których nazwy rozpoczynają się od "Jako", ale nie wyliczyć. Typ metody, których nazwy rozpoczynają się od "Do wyliczyć kolekcji źródłowej i elementy do odpowiedniej kolekcji".  
  
|Nazwa metody|Opis|Składnia wyrażeń języka Visual Basic|Więcej informacji|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|AsEnumerable|Zwraca dane wejściowe typu <xref:System.Collections.Generic.IEnumerable%601>.|Nie dotyczy.|<xref:System.Linq.Enumerable.AsEnumerable%2A?displayProperty=nameWithType>|  
|AsQueryable|Konwertuje (ogólny) <xref:System.Collections.IEnumerable> do (ogólny) <xref:System.Linq.IQueryable>.|Nie dotyczy.|<xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=nameWithType>|  
|Rzutowanie|Rzutuje elementy kolekcji do określonego typu.|`From … As …`|<xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Cast%2A?displayProperty=nameWithType>|  
|OfType|Filtruje wartości, w zależności od ich możliwości można rzutować na określony typ.|Nie dotyczy.|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|toArray|Konwertuje kolekcję na tablicę. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToArray%2A?displayProperty=nameWithType>|  
|ToDictionary|Umieszcza elementy do <xref:System.Collections.Generic.Dictionary%602> oparte na funkcji selektora kluczy. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToDictionary%2A?displayProperty=nameWithType>|  
|tolist —|Konwertuje kolekcję do <xref:System.Collections.Generic.List%601>. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType>|  
|ToLookup|Umieszcza elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) oparte na funkcji selektora kluczy. Ta metoda powoduje wykonanie kwerendy.|Nie dotyczy.|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a>Przykład składni wyrażenia zapytania  
 Poniższy przykład kodu wykorzystuje `From As` klauzuli do rzutowania typu z podtypem przed uzyskaniem dostępu do elementu członkowskiego, który jest dostępny tylko na podtyp.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq>  
 [Operatory standardowe zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [Klauzula FROM](../../../../visual-basic/language-reference/queries/from-clause.md)  
 [Porady: zapytanie w ArrayList za pomocą LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)
