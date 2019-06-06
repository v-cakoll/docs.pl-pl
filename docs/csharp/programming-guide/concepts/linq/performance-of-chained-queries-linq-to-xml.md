---
title: Wydajność zapytań łańcuchowych (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 1ccb7dfec57a4aeea8329456084ca99f5ca3124d
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689995"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Wydajność zapytań łańcuchowych (LINQ to XML) (C#)

Jedną z najważniejszych zalet LINQ (i LINQ to XML) jest to, że zapytań łańcuchowych może wykonywać oraz pojedynczego zapytania większych i bardziej skomplikowane.

Łańcuchowe zapytań jest zapytanie, które używa innego zapytania jako źródło. Na przykład w poniższym kodzie prosty `query2` ma `query1` jako źródło:

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

To zapytanie łańcuchowych zawiera ten sam profil wydajności jako iteracji przez listę połączoną.

- <xref:System.Xml.Linq.XContainer.Elements%2A> Osi jest zasadniczo ta sama wydajność co iteracji przez listę połączoną. <xref:System.Xml.Linq.XContainer.Elements%2A> jest implementowany jako iterator za pomocą odroczonego wykonania. Oznacza to, że robi jakąś pracę dodatkowo do iteracji w połączonej listy, takich jak obiekt iteratora do przydzielania i śledzeniu stanu wykonywania. Tę pracę można podzielić na dwie kategorie: prac, które odbywa się w czasie, o których iterator który jest skonfigurowany i czynności, które odbywa się podczas każdej iteracji. Praca Instalatora jest mały, stały ilość pracy i Praca wykonana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.

- W `query1`, `where` klauzuli powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Where%2A> metody. Ta metoda jest również implementowana jako iterator. Praca Instalatora składa się z tworzenia wystąpienia delegata, który będzie odwoływać się do wyrażenia lambda oraz zwykłej instalacji dla iteratora. Z każdą iteracją delegat jest wywoływana, aby wykonać predykat. Praca Instalatora i pracy wykonanej w każdej iteracji jest podobny do pracy wykonanej podczas iteracji osi.

- W `query1`, klauzula select powoduje, że zapytanie, aby wywołać <xref:System.Linq.Enumerable.Select%2A> metody. Ta metoda ma ten sam profil wydajności jako <xref:System.Linq.Enumerable.Where%2A> metody.

- W `query2`, zarówno `where` klauzuli i `select` klauzuli mieć ten sam profil wydajności, podobnie jak w `query1`.

Iteracja przez `query2` jest zatem bezpośrednio proporcjonalnie do liczby elementów w źródle pierwsze zapytanie, innymi słowy, liniowo. Odpowiedni przykład Visual Basic będą mieć ten sam profil wydajności.

Aby uzyskać więcej informacji dotyczących iteratorów, zobacz [uzyskanie](../../../../csharp/language-reference/keywords/yield.md).

Aby uzyskać bardziej szczegółowy samouczek dotyczący Łączenie łańcuchowe zapytań, zobacz [samouczka: Łączenie łańcuchowe zapytań](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).
