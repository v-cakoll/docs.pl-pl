---
title: klauzula FROM — C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715292"
---
# <a name="from-clause-c-reference"></a>Klauzula From (odwołanie w C#)

Wyrażenie zapytania musi rozpoczynać się od klauzuli `from`. Ponadto wyrażenie zapytania może zawierać podzapytania, które również zaczynają się klauzulą `from`. Klauzula `from` określa następujące elementy:

- Źródło danych, w którym zostanie uruchomione zapytanie lub podzapytanie.

- Lokalna *zmienna zakresu* , która reprezentuje każdy element w sekwencji źródłowej.

Zarówno zmienna zakresu, jak i źródło danych, są jednoznacznie wpisane. Źródło danych, do którego istnieje odwołanie w klauzuli `from`, musi mieć typ <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>lub typu pochodnego, takiego jak <xref:System.Linq.IQueryable%601>.

W poniższym przykładzie `numbers` to źródło danych, a `num` to zmienna zakresu. Należy zauważyć, że obie zmienne są silnie określone, mimo że jest używane słowo kluczowe [var](var.md) .

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Zmienna zakresu

Kompilator wnioskuje typ zmiennej zakresu, gdy źródło danych implementuje <xref:System.Collections.Generic.IEnumerable%601>. Na przykład, jeśli źródło ma typ `IEnumerable<Customer>`, zmienna zakresu jest wywnioskowana do `Customer`. Jedynym warunkiem, że należy określić typ jawnie, jest to, że źródło jest nieogólnym typem `IEnumerable`, takim jak <xref:System.Collections.ArrayList>. Aby uzyskać więcej informacji, zobacz [How to Query The ArrayList with LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

W poprzednim przykładzie `num` jest wywnioskowany dla typu `int`. Ponieważ zmienna zakresu jest silnie wpisana, można wywołać metody lub użyć jej w innych operacjach. Na przykład zamiast pisać `select num`, można napisać `select num.ToString()`, aby wyrażeniu zapytania zwracał sekwencję ciągów zamiast liczb całkowitych. Lub można napisać `select num + 10`, aby spowodować zwrócenie przez wyrażenie sekwencji 14, 11, 13, 12, 10. Aby uzyskać więcej informacji, zobacz [SELECT — klauzula](select-clause.md).

Zmienna zakresu jest jak Zmienna iteracji w instrukcji [foreach](foreach-in.md) z wyjątkiem jednej bardzo ważnej różnicy: zmienna zakresu nigdy nie przechowuje danych ze źródła. Jest to tylko wygoda syntaktyczna, która umożliwia zapytanie opisującym, co się dzieje po wykonaniu zapytania. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Złożone z klauzul

W niektórych przypadkach każdy element w sekwencji źródłowej może być sekwencją lub zawierać sekwencję. Na przykład źródło danych może być `IEnumerable<Student>`, gdzie każdy obiekt ucznia w sekwencji zawiera listę wyników testu. Aby uzyskać dostęp do listy wewnętrznej w ramach każdego elementu `Student`, można użyć klauzul `from` złożonych. Technika przypomina użycie zagnieżdżonych instrukcji [foreach](foreach-in.md) . Można dodać klauzule [WHERE](partial-method.md) lub [orderby](orderby-clause.md) do klauzuli `from`, aby przefiltrować wyniki. Poniższy przykład przedstawia sekwencję `Student` obiektów, z których każdy zawiera wewnętrzny `List` liczb całkowitych reprezentujących wyniki testu. Aby uzyskać dostęp do listy wewnętrznej, należy użyć klauzuli `from` złożonej. W razie potrzeby można wstawiać klauzule między dwoma klauzulami `from`.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Używanie wielu klauzul from do wykonywania sprzężeń

Klauzula `from` złożonego służy do uzyskiwania dostępu do kolekcji wewnętrznych w jednym źródle danych. Jednak zapytanie może również zawierać wiele klauzul `from`, które generują dodatkowe zapytania z niezależnych źródeł danych. Ta technika umożliwia wykonywanie pewnych typów operacji JOIN, które nie są możliwe za pomocą [klauzuli join](join-clause.md).

Poniższy przykład pokazuje, jak dwie klauzule `from` mogą być używane do tworzenia pełnego sprzężenia między dwoma źródłami danych.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Aby uzyskać więcej informacji na temat operacji łączenia, które używają wielu klauzul `from`, zobacz [przełączenie do lewej krawędzi zewnętrznej](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Zobacz także

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
