---
title: Wydajność zapytań łańcuchowych (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: 7deff9205e6535877efabd85257baa5b3906f41a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253122"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Wydajność zapytań łańcuchowych (LINQ do XML) (C#)

Jedną z najważniejszych zalet LINQ (i LINQ do XML) jest to, że zapytania łańcuchowe mogą wykonywać, a także pojedyncze większe, bardziej skomplikowane zapytanie.

Kwerenda łańcuchowa to kwerenda, która używa innej kwerendy jako źródła. Na przykład w następującym `query2` prostym `query1` kodzie ma jako źródło:

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

```output
4
```

Ta kwerenda łańcuchowa zapewnia ten sam profil wydajności, co iteracji za pośrednictwem listy połączonej.

- Oś <xref:System.Xml.Linq.XContainer.Elements%2A> ma zasadniczo taką samą wydajność jak iteracji za pośrednictwem listy połączonej. <xref:System.Xml.Linq.XContainer.Elements%2A>jest implementowana jako iterator z odroczonego wykonania. Oznacza to, że wykonuje pewną pracę oprócz iteracji za pośrednictwem listy połączonej, takich jak przydzielanie obiektu iteratora i śledzenie stanu wykonywania. Tę pracę można podzielić na dwie kategorie: pracę wykonywaną w momencie skonfigurowania iterator i pracę wykonywaną podczas każdej iteracji. Praca konfiguratowana jest niewielką, stałą ilością pracy, a praca wykonywana podczas każdej iteracji jest proporcjonalna do liczby elementów w kolekcji źródłowej.

- W `query1`klauzuli `where` powoduje, że <xref:System.Linq.Enumerable.Where%2A> kwerenda do wywołania metody. Ta metoda jest również implementowana jako iterator. Praca konfiguratorna polega na uprzedzeniu delegata, który będzie odwoływał się do wyrażenia lambda, a także normalnej konfiguracji sterująca. Z każdą iteracją pełnomocnik jest wywoływany do wykonania predykatu. Praca konfiguratora i praca wykonywana podczas każdej iteracji jest podobna do pracy wykonanej podczas iteracji przez oś.

- W `query1`programie select klauzula powoduje, <xref:System.Linq.Enumerable.Select%2A> że kwerenda wywołać metodę. Ta metoda ma ten sam <xref:System.Linq.Enumerable.Where%2A> profil wydajności co metoda.

- W `query2`, `where` zarówno klauzula, jak i klauzula `select` mają taki sam profil wydajności jak w `query1`.

Iteracja jest `query2` zatem bezpośrednio proporcjonalna do liczby elementów w źródle pierwszego zapytania, innymi słowy, czas liniowy. Odpowiedni przykład języka Visual Basic będzie miał ten sam profil wydajności.

Aby uzyskać więcej informacji na temat iteratorów, zobacz [wydajność](../../../language-reference/keywords/yield.md).

Aby uzyskać bardziej szczegółowy samouczek dotyczący łączenia zapytań, zobacz [Samouczek: Łączenie zapytań razem](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).
