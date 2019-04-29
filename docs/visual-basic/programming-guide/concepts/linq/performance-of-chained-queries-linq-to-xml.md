---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
ms.openlocfilehash: 8634ca224f5892918721996114649c392a5080a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665874"
---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Wydajność zapytań łańcuchowych (LINQ to XML) (Visual Basic)

Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że zapytań łańcuchowych może wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.

Łańcuchowe zapytań jest zapytanie, które używa innego zapytania jako źródło. Na przykład w poniższym kodzie prosty `query2` ma `query1` jako źródło:

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

To zapytanie łańcuchowych zawiera ten sam profil wydajności jako iteracji przez listę połączoną.

- <xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracji przez listę połączoną. <xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iterator za pomocą odroczonego wykonania. Oznacza to, że robi jakąś pracę dodatkowo do iteracji w połączonej listy, takich jak obiekt iteratora do przydzielania i śledzeniu stanu wykonywania. Tę pracę można podzielić na dwie kategorie: prac, które odbywa się w czasie, o których iterator który jest skonfigurowany i czynności, które odbywa się podczas każdej iteracji. Praca Instalatora jest mały, stały ilość pracy i Praca wykonana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.

- W `query1`, `Where` klauzuli powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Where%2A> metody. Ta metoda jest również implementowana jako iterator. Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz zwykłej instalacji dla iteratora. Z każdą iteracją delegat jest wywoływana, aby wykonać predykat. Praca Instalatora i pracy wykonanej w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.

- W `query1`, klauzula select powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Select%2A> metody. Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.

- W `query2`, zarówno `Where` klauzuli i `Select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.

 Iteracja przez `query2` jest zatem bezpośrednio proporcjonalnie do liczby elementów w źródle pierwsze zapytanie, innymi słowy, liniowo.

## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
