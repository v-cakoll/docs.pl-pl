---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 69ed09addb50ac45e7b46cd0322d4df076b5875b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834953"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)

Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że kwerendy łańcuchowe mogą wykonywać, a także pojedyncze, bardziej skomplikowane zapytania.

Zapytanie łańcuchowe jest kwerendą, która używa innego zapytania jako źródła. Na przykład w poniższym kodzie prostym `query2` ma `query1` jako Źródło:

```vb
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))

Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x

Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e

For Each i As var In query2
    Console.WriteLine("{0}", CInt(i))
Next
```

Ten przykład generuje następujące dane wyjściowe:

```console
4
```

To zapytanie łańcuchowe zapewnia ten sam profil wydajności co iteracja w połączonej liście.

- Oś <xref:System.Xml.Linq.XContainer.Elements%2A> ma zasadniczo taką samą wydajność jak iteracja w połączonej liście. <xref:System.Xml.Linq.XContainer.Elements%2A> jest zaimplementowany jako iterator z odroczonym wykonywaniem. Oznacza to, że wykonuje kilka zadań oprócz iteracji przez połączoną listę, na przykład przydzielanie obiektu iteratora i śledzenie stanu wykonywania. Ta czynność może zostać podzielona na dwie kategorie: pracy, która jest wykonywana w chwili, gdy iterator jest skonfigurowany, i pracy, która jest wykonywana podczas każdej iteracji. Konfiguracja pracy jest małą, stałą ilością pracy i pracy wykonywanej podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.

- W `query1` klauzula `Where` powoduje, że zapytanie wywoła metodę <xref:System.Linq.Enumerable.Where%2A>. Ta metoda jest również zaimplementowana jako iterator. Konfiguracja zadań składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz normalnej konfiguracji iteratora. Dla każdej iteracji delegat jest wywoływany, aby wykonać predykat. Konfiguracja pracy i pracy wykonanej podczas każdej iteracji jest podobna do wykonanej pracy podczas iteracji na osi.

- W `query1` klauzula SELECT powoduje, że zapytanie wywołuje metodę <xref:System.Linq.Enumerable.Select%2A>. Ta metoda ma ten sam profil wydajności co Metoda <xref:System.Linq.Enumerable.Where%2A>.

- W `query2` zarówno klauzula `Where`, jak i klauzula `Select` mają taki sam profil wydajności jak w `query1`.

 Iteracja przez `query2` jest w związku z tym bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, czyli czasu liniowego.

## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
