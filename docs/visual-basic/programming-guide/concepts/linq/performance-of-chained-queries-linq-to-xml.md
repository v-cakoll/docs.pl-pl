---
title: "Wydajność kwerend łańcuchowa (LINQ do XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 281eb8ea62760507da991ea878270befe458bb38
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Wydajność kwerend łańcuchowa (LINQ do XML) (Visual Basic)
Jest jedną z najważniejszych zalet LINQ (i LINQ do XML), czy łańcuchowa zapytania można wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.  
  
 Łańcuchowa zapytanie jest kwerenda, która używa innego zapytania jako źródło. Na przykład w poniższym kodzie proste `query2` ma `query1` jako źródło:  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
4  
```  
  
 To zapytanie łańcuchowa zawiera ten sam profil wydajności jako iteracja listy połączonej.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracja listy połączonej. <xref:System.Xml.Linq.XContainer.Elements%2A>jest implementowany jako iteratora o wykonanie odroczone. Oznacza to, że go działa niektórych dodatkowo iteracja listy połączonej, takich jak przydzielanie obiektu iteratora i rejestrowanie informacji o stanie do wykonania. Tę pracę można podzielić na dwie kategorie: pracy, którą można wykonać w czasie, o których skonfigurowano iteratora i pracy, który jest wykonywane podczas każdej iteracji. Praca Instalatora jest mały, stały ilość pracy oraz pracy wykonanej w każdej iteracji jest proporcjonalny do liczby elementów w kolekcji źródłowej.  
  
-   W `query1`, `Where` klauzuli powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Where%2A> metody. Ta metoda również jest implementowany jako iteratora. Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda, a także normalnej konfiguracji dla iteratora. A każda iteracja delegat nazywa się do wykonywania predykatu. Praca Instalatora i pracy w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.  
  
-   W `query1`, klauzula select powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Select%2A> metody. Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.  
  
-   W `query2`, oba `Where` klauzuli i `Select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.  
  
 Iteracja przez `query2` jest bezpośrednio proporcjonalne do liczby elementów w źródle pierwszy, innymi słowy, liniowego czas kwerendy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
