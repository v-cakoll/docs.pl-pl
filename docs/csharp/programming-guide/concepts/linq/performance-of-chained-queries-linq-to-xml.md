---
title: "Wydajność kwerend łańcuchowa (LINQ do XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1014b7790f0ea465e10cf8fc03e59ca4d3f2d55c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Wydajność kwerend łańcuchowa (LINQ do XML) (C#)
Jest jedną z najważniejszych zalet LINQ (i LINQ do XML), czy łańcuchowa zapytania można wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.  
  
 Łańcuchowa zapytanie jest kwerenda, która używa innego zapytania jako źródło. Na przykład w poniższym kodzie proste `query2` ma `query1` jako źródło:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
4  
```  
  
 To zapytanie łańcuchowa zawiera ten sam profil wydajności jako iteracja listy połączonej.  
  
-   <xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracja listy połączonej. <xref:System.Xml.Linq.XContainer.Elements%2A>jest implementowany jako iteratora o wykonanie odroczone. Oznacza to, że go działa niektórych dodatkowo iteracja listy połączonej, takich jak przydzielanie obiektu iteratora i rejestrowanie informacji o stanie do wykonania. Tę pracę można podzielić na dwie kategorie: pracy, którą można wykonać w czasie, o których skonfigurowano iteratora i pracy, który jest wykonywane podczas każdej iteracji. Praca Instalatora jest mały, stały ilość pracy oraz pracy wykonanej w każdej iteracji jest proporcjonalny do liczby elementów w kolekcji źródłowej.  
  
-   W `query1`, `where` klauzuli powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Where%2A> metody. Ta metoda również jest implementowany jako iteratora. Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda, a także normalnej konfiguracji dla iteratora. A każda iteracja delegat nazywa się do wykonywania predykatu. Praca Instalatora i pracy w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.  
  
-   W `query1`, klauzula select powoduje wykonanie zapytania w celu wywołania <xref:System.Linq.Enumerable.Select%2A> metody. Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.  
  
-   W `query2`, oba `where` klauzuli i `select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.  
  
 Iteracja przez `query2` jest bezpośrednio proporcjonalne do liczby elementów w źródle pierwszy, innymi słowy, liniowego czas kwerendy. Odpowiedni przykład Visual Basic będzie mieć ten sam profil wydajności.  
  
 Aby uzyskać więcej informacji dotyczących Iteratory, zobacz [yield](../../../../csharp/language-reference/keywords/yield.md).  
  
 Bardziej szczegółowy samouczek dotyczący razem łańcucha zapytań, zobacz [samouczek: tworzenie łańcuchów zapytań razem](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
