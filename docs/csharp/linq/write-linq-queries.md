---
title: Zapisywanie zapytań LINQ w C#
description: Dowiedz się, jak pisać zapytania LINQ w C#.
ms.date: 12/01/2016
ms.assetid: 30703f79-cf3a-4d02-b892-c95d58a1d9ed
ms.openlocfilehash: df77326b921d22d90cf90c12e9c0f472d808ed95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688660"
---
# <a name="write-linq-queries-in-c"></a>Zapisywanie zapytań LINQ w C\#

W tym artykule przedstawiono trzy sposoby, w których można napisać zapytanie LINQ w C#:

1. Za pomocą składni zapytania.

2. Za pomocą składni metody.

3. Użyj kombinacji składnia zapytania a składnia metody.

W poniższych przykładach pokazano pewnych prostych zapytań LINQ, za pomocą danej metody wymienione wcześniej. Ogólnie rzecz biorąc reguła jest użycie (1), jeśli to możliwe, a (2) i (3), jeśli zajdzie taka potrzeba.

> [!NOTE]
> Te zapytania działają na prostych kolekcji w pamięci; Podstawowa składnia jest jednak używaną w składniku LINQ to Entities i LINQ to XML.

## <a name="example---query-syntax"></a>Przykład — składnia zapytań

Zalecanym sposobem pisania zapytań większości jest użycie *składni zapytania* utworzyć *wyrażeniach zapytań*. Poniższy przykład przedstawia trzy wyrażenia zapytania. Pierwsze wyrażenie zapytanie pokazuje, jak filtrowanie lub ograniczanie wyników, stosując warunki z `where` klauzuli. Zwraca wszystkie elementy w sekwencji źródłowej, w których wartości są większe niż 7 lub mniej niż 3. Drugie wyrażenie pokazuje, jak kolejność zwróconych wyników. Trzeci wyrażenie pokazuje, jak grupowanie wyników według klucza. Ta kwerenda zwraca dwie grupy, w oparciu o pierwszą literę wyrazu.

[!code-csharp[csProgGuideLINQ#5](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_1.cs)]

Należy zauważyć, że typ zapytania <xref:System.Collections.Generic.IEnumerable%601>. Wszystkie te zapytania można napisane przy użyciu `var` jak pokazano w poniższym przykładzie:

`var query = from num in numbers...`

W poprzednim przykładzie zapytania nie są faktycznie wykonywane do czasu iteracji nad zmienną kwerendy w `foreach` instrukcji lub innych instrukcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ](../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="example---method-syntax"></a>Przykład — składnia metody

Niektóre operacje zapytania musi być wyrażona jako wywołania metody. Najczęściej są to te, które zwracają pojedyncze wartości liczbowe, takie jak <xref:System.Linq.Enumerable.Sum%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, <xref:System.Linq.Enumerable.Average%2A>i tak dalej. Te metody zawsze należy wywołać ostatnia w każdym zapytaniu ponieważ reprezentuje pojedynczą wartość i nie może służyć jako źródło dla operacji zapytania dodatkowych. Poniższy przykład przedstawia wywołania metody w wyrażeniu zapytania:

[!code-csharp[csProgGuideLINQ#6](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_2.cs)]

Jeśli metoda ma parametry akcji lub Func, są one udostępniane w formie [lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md) wyrażenia, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#7](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_3.cs)]

W poprzednich zapytań tylko zapytania nr 4 wykonuje natychmiast. Jest to spowodowane zwraca pojedynczą wartość, a nie ogólny <xref:System.Collections.Generic.IEnumerable%601> kolekcji. Sama metoda ma używać `foreach` celu obliczenia jego wartość.

Każdy z poprzednich zapytań mogą być zapisywane przy użyciu niejawnego wpisywania z [var](../language-reference/keywords/var.md), jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#8](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_4.cs)]

## <a name="example---mixed-query-and-method-syntax"></a>Przykład — mieszane składnia zapytania i metody

W tym przykładzie pokazano, jak używać składni metody na wynikach klauzuli kwerendy. Po prostu należy umieścić w wyrażeniu zapytania w nawiasach, a następnie zastosowanie operatora kropki i wywołać metodę. W poniższym przykładzie zapytanie #7 zwraca liczbę liczb, którego wartością jest od 3 do 7. Ogólnie rzecz biorąc, lepiej jest używać drugiej zmiennej do przechowywania wynik wywołania metody. W ten sposób zapytanie jest mniej prawdopodobne, należy go mylić z wynikami zapytania.

[!code-csharp[csProgGuideLINQ#9](~/samples/snippets/csharp/concepts/linq/how-to-write-linq-queries_5.cs)]

Ponieważ 7 zapytanie zwraca pojedynczą wartość i nie jest kolekcją, natychmiast wykonuje zapytanie.

Poprzednie zapytanie mogą być zapisywane przy użyciu niejawnego wpisywania z `var`, wykonując następujące czynności:

```csharp
var numCount = (from num in numbers...
```

Może być zapisana w składni metody w następujący sposób:

```csharp
var numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

Mogą być zapisywane za pomocą jawnego wpisywania, w następujący sposób:

```csharp
int numCount = numbers.Where(n => n < 3 || n > 7).Count();
```

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Pisanie zapytań wC#](../programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)
- [Language Integrated Query (LINQ)](index.md)
- [where, klauzula](../language-reference/keywords/where-clause.md)