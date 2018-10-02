---
title: Klauzula From (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: c8c124f44df292b8323560cce541cca2765e2790
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863237"
---
# <a name="from-clause-c-reference"></a>Klauzula From (odwołanie w C#)

Wyrażenie zapytania musi zaczynać się od `from` klauzuli. Ponadto wyrażenie zapytania może zawierać podzapytaniach, które również zaczynają się od `from` klauzuli. `from` Klauzula określa następujące czynności:

- Źródło danych, na którym uruchomiona jest zapytaniu lub podzapytaniu.

- Lokalny *zmiennej zakresu* reprezentujący każdego elementu w sekwencji źródłowej.

Zmienna zakresu i źródła danych są silnie typizowane. Źródło danych, do którego odwołuje się `from` klauzula musi mieć typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, lub typ pochodny, takie jak <xref:System.Linq.IQueryable%601>.

W poniższym przykładzie `numbers` jest źródłem danych i `num` jest zmiennej zakresu. Należy pamiętać, że obie zmienne są silnie typizowane mimo [var](var.md) słowo kluczowe jest używane.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Zmienna zakresu

Kompilator wnioskuje typ zmiennej zakresu, gdy źródło danych implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na przykład, jeśli źródło ma typ `IEnumerable<Customer>`, a następnie wywnioskowana jest zmienna zakresu można `Customer`. Jedyną sytuacją, który musi określać typ jawnie jest, gdy źródłem jest nieogólnego `IEnumerable` wpisz na przykład <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [porady: zapytanie w ArrayList za pomocą LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

W poprzednim przykładzie `num` jest wnioskowany typ `int`. Ponieważ zmienna zakresu zdecydowanie jest wpisane, można wywoływać metody na nim lub używać go w innych operacji. Na przykład zamiast zapisywania `select num`, można napisać `select num.ToString()` spowodować wyrażenia zapytania w celu zwrócenia sekwencji, a nie liczby całkowite. Lub możesz napisać `select n + 10` spowodować wyrażenia w celu zwrócenia sekwencji 14, 11, 13, 12, 10. Aby uzyskać więcej informacji, zobacz [klauzuli select](select-clause.md).

Zmienna zakresu jest podobna do zmiennej iteracji w [foreach](foreach-in.md) instrukcji, z wyjątkiem jednego bardzo istotną różnicą: zmienną zakresu faktycznie nigdy nie przechowuje dane ze źródła. On po prostu składni wygody umożliwiająca zapytania do opisywania, co ma miejsce, gdy zapytanie jest wykonywane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Złożone z klauzul

W niektórych przypadkach każdego elementu w sekwencji źródłowej sam jest sekwencją albo lub zawiera sekwencję. Na przykład źródła danych może być `IEnumerable<Student>` gdzie każdy obiekt dla uczniów w sekwencji zawiera listę wyniki testów. Dostępu do wewnętrznej listy w ramach każdej `Student` elementu, można użyć złożonego `from` klauzul. Technika działa jak przy użyciu zagnieżdżonych [foreach](foreach-in.md) instrukcji. Możesz dodać [gdzie](partial-method.md) lub [orderby](orderby-clause.md) klauzule albo `from` klauzuli do filtrowania wyników. W poniższym przykładzie przedstawiono sekwencję `Student` obiektów, z których każdy zawiera wewnętrzny `List` liczb całkowitych reprezentujących wyników testów. Aby uzyskać dostęp do wewnętrznej listy, należy użyć związek `from` klauzuli. Możesz wstawić klauzule między tymi dwoma `from` klauzul, jeśli to konieczne.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Wykonywanie sprzężeń za pomocą wielu z klauzul

Związek `from` klauzuli umożliwia dostęp do wewnętrznego kolekcji w jednym źródle danych. Jednak zapytanie może również zawierać wiele `from` klauzul, które generują zapytania uzupełniające ze źródeł danych niezależnych. Ta technika pozwala na wykonywanie pewnych operacji łączenia, która nie jest możliwa przy użyciu [klauzuli join](join-clause.md).

W poniższym przykładzie pokazano jak dwa `from` klauzule może służyć w celu utworzenia pełne sprzężenie krzyżowe z dwoma źródłami danych.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Aby uzyskać więcej informacji na temat operacji łączenia, które używają wielu `from` zdań, zobacz [wykonaj Lewe sprzężenia zewnętrzne](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)  
- [Language Integrated Query (LINQ)](../../linq/index.md)  
