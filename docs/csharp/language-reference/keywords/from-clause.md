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
ms.openlocfilehash: e8bb7782fc60a3af20d5926e609a5edea68fd1a3
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027983"
---
# <a name="from-clause-c-reference"></a>Klauzula From (odwołanie w C#)

Wyrażenia zapytania musi rozpoczynać się od `from` klauzuli. Ponadto wyrażeniu zapytania może zawierać podzapytaniach, które również rozpoczynać `from` klauzuli. `from` Klauzuli określa następujące elementy:

- Źródło danych, na którym uruchomiona jest zapytaniu lub podzapytaniu.

- Lokalny *zmiennej zakresu* reprezentujący każdego elementu w sekwencji źródłowej.

Zarówno zmienną zakresu, jak i źródła danych są silnie typizowane. Źródło danych, do którego odwołuje się `from` klauzuli musi mieć typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, ani typem pochodnym, takich jak <xref:System.Linq.IQueryable%601>.

W poniższym przykładzie `numbers` jest źródłem danych i `num` jest zmienną zakresu. Należy pamiętać, że obie zmienne są silnie typizowane nawet za pomocą [var](var.md) słowo kluczowe jest używane.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Zmienna zakresu

Kompilator wnioskuje typu zmienną zakresu, jeśli źródło danych implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na przykład, jeśli źródłowy ma typ `IEnumerable<Customer>`, następnie zmienna zakresu jest wywnioskowany jako `Customer`. Tylko wtedy, który należy określić typ jawnie jest, gdy źródłem jest inny niż ogólny `IEnumerable` wpisz na przykład <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [porady: zapytanie w ArrayList za pomocą LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

W poprzednim przykładzie `num` jest wartością typu `int`. Ponieważ silnie jest typu zmienną zakresu, można wywoływać metod w nim lub go używać w innych operacji. Na przykład zamiast zapisywania `select num`, można zapisać `select num.ToString()` spowodować wyrażenia zapytania do zwrócenia sekwencję ciągów zamiast liczb całkowitych. Lub można zapisać `select n + 10` spowodować wyrażenie, które ma zwrócić sekwencji 14, 11, 13, 12, 10. Aby uzyskać więcej informacji, zobacz [klauzuli select](select-clause.md).

Zmienna zakresu jest podobna do zmiennej iteracji w [foreach](foreach-in.md) instrukcji z wyjątkiem jednego bardzo istotną różnicą: zmienna zakresu nigdy przechowuje dane ze źródła. Go, który właśnie składni wygody umożliwiającą kwerenda Opisz, co ma miejsce, gdy zapytanie jest wykonywane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Złożone klauzul from

W niektórych przypadkach każdego elementu w sekwencji źródłowej może sam być albo sekwencji lub zawierać sekwencji. Na przykład źródło danych może być `IEnumerable<Student>` gdzie każdy obiekt uczniów w sekwencji zawiera listę wyniki testów. Dostęp do listy wewnętrzny w ramach każdej `Student` elementu, można użyć złożonego `from` klauzul. Techniki działa jak przy użyciu zagnieżdżone [foreach](foreach-in.md) instrukcje. Możesz dodać [gdzie](partial-method.md) lub [orderby](orderby-clause.md) klauzule albo `from` klauzuli do filtrowania wyników. W poniższym przykładzie przedstawiono sekwencję `Student` obiektów, z których każdy zawiera wewnętrzny `List` liczb całkowitych reprezentujący wyników testów. Dostęp do wewnętrznych listy, użyj związek `from` klauzuli. Możesz wstawić klauzule między nimi `from` klauzule, jeśli to konieczne.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Wykonanie sprzężeń za pomocą wielu klauzul from

Związek `from` klauzuli umożliwia dostęp do kolekcji wewnętrznej w pojedynczego źródła danych. Jednak zapytanie może również zawierać wiele `from` klauzule generujących uzupełniające zapytania ze źródeł danych niezależne. Ta technika pozwala na wykonywanie pewnych operacji łączenia, które nie są możliwe przy użyciu [klauzuli join](join-clause.md).

W poniższym przykładzie przedstawiono sposób dwóch `from` klauzule można tworzyć pełne sprzężenie krzyżowe dwóch źródeł danych.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Aby uzyskać więcej informacji na temat operacji łączenia, które używają wielu `from` klauzule, zobacz [wykonaj Lewe sprzężenia zewnętrzne](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe zapytania (LINQ)](query-keywords.md)  
[Language Integrated Query (LINQ)](../../linq/index.md)  