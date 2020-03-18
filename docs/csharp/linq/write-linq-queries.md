---
title: Zapisywanie zapytań LINQ w C#
description: Dowiedz się, jak pisać zapytania LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: ed32543b0422e0664a8577f2c27f7c7c00a719a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "65632876"
---
# <a name="write-linq-queries-in-c"></a>Napisz zapytania LINQ w C\#

W tym artykule przedstawiono trzy sposoby, w których można napisać kwerendę LINQ w języku C#:

1. Użyj składni kwerendy.

2. Użyj składni metody.

3. Użyj kombinacji składni kwerendy i składni metody.

W poniższych przykładach przedstawiono kilka prostych zapytań LINQ przy użyciu każdego podejścia wymienione wcześniej. Ogólnie rzecz biorąc, regułą jest stosowanie (1) w miarę możliwości i stosowanie (2) i (3) w razie potrzeby.

> [!NOTE]
> Te zapytania działają na prostych kolekcji w pamięci; Jednak podstawowa składnia jest taka sama jak w LINQ do jednostek i LINQ do XML.

## <a name="example---query-syntax"></a>Przykład — składnia kwerendy

Zalecanym sposobem pisania większości kwerend jest użycie *składni kwerendy* do tworzenia *wyrażeń kwerend .* W poniższym przykładzie przedstawiono trzy wyrażenia kwerendy. Pierwsze wyrażenie kwerendy pokazuje, jak filtrować lub `where` ograniczać wyniki, stosując warunki z klauzulą. Zwraca wszystkie elementy w sekwencji źródłowej, których wartości są większe niż 7 lub mniej niż 3. Drugie wyrażenie pokazuje, jak uporządkować zwrócone wyniki. Trzecie wyrażenie pokazuje, jak grupować wyniki zgodnie z kluczem. Ta kwerenda zwraca dwie grupy na podstawie pierwszej litery wyrazu.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Należy zauważyć, że typ <xref:System.Collections.Generic.IEnumerable%601>kwerend jest . Wszystkie te zapytania mogą `var` być zapisywane przy użyciu, jak pokazano w poniższym przykładzie:

`var query = from num in numbers...`

W każdym poprzednim przykładzie kwerendy faktycznie nie są wykonywane, dopóki `foreach` nie iterate nad zmienną kwerendy w instrukcji lub innej instrukcji. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do linq zapytania](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Przykład — składnia metody

Niektóre operacje kwerendy muszą być wyrażone jako wywołanie metody. Najczęstsze takie metody to te, które zwracają pojedyncze <xref:System.Linq.Enumerable.Sum%2A>wartości <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.Min%2A>liczbowe, takie jak , , , <xref:System.Linq.Enumerable.Average%2A>i tak dalej. Te metody muszą być zawsze wywoływane jako ostatnie w dowolnej kwerendzie, ponieważ reprezentują tylko jedną wartość i nie mogą służyć jako źródło dodatkowej operacji kwerendy. W poniższym przykładzie przedstawiono wywołanie metody w wyrażeniu kwerendy:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Jeśli metoda ma Action lub Func parametry, są one dostarczane w postaci wyrażenia [lambda,](../programming-guide/statements-expressions-operators/lambda-expressions.md) jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

W poprzednich kwerendach tylko kwerenda #4 jest wykonywana natychmiast. Jest to spowodowane zwraca pojedynczą wartość, <xref:System.Collections.Generic.IEnumerable%601> a nie kolekcji ogólnej. Sama metoda musi `foreach` użyć w celu obliczenia jej wartości.

Każde z poprzednich zapytań można zapisać przy użyciu niejawnego wpisywania z [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Przykład — składnia kwerendmieszanych i metod

W tym przykładzie pokazano, jak używać składni metody na wynikach klauzuli kwerendy. Wystarczy ująć wyrażenie kwerendy w nawiasy, a następnie zastosować operator kropki i wywołać metodę. W poniższym przykładzie kwerenda #7 zwraca liczbę liczb, których wartość wynosi od 3 do 7. Ogólnie rzecz biorąc jednak lepiej jest użyć drugiej zmiennej do przechowywania wyniku wywołania metody. W ten sposób kwerenda jest mniej prawdopodobne, aby być mylone z wynikami kwerendy.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Ponieważ #7 kwerendy zwraca pojedynczą wartość, a nie kolekcję, kwerenda jest wykonywana natychmiast.

Poprzednie zapytanie można zapisać przy użyciu `var`niejawnego wpisywania z , w następujący sposób:

```csharp
var numCount = (from num in numbers...
```

Może być napisany w składni metody w następujący sposób:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Można go zapisać przy użyciu jawnego wpisywania, w następujący sposób:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Pisanie zapytań w C #](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Language Integrated Query (LINQ)](index.md)
- [gdzie klauzula](../language-reference/keywords/where-clause.md)
