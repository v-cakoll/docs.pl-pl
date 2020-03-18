---
title: from klauzula - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 388b9c0245b112d619fc173f6019b3f7dbf59940
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715292"
---
# <a name="from-clause-c-reference"></a>Klauzula From (odwołanie w C#)

Wyrażenie kwerendy musi `from` zaczynać się od klauzuli. Ponadto wyrażenie kwerendy może zawierać zapytania podrzędne, `from` które również zaczynają się od klauzuli. Klauzula `from` określa następujące elementy:

- Źródło danych, na którym zostanie uruchomione kwerenda lub kwerenda podrzędna.

- *Zmienna zakresu* lokalnego, która reprezentuje każdy element w sekwencji źródłowej.

Zarówno zmienna zakresu, jak i źródło danych są silnie typowane. Źródło danych, do `from` którego odwołuje się <xref:System.Collections.IEnumerable>klauzula, musi mieć typ , <xref:System.Collections.Generic.IEnumerable%601>lub typ pochodny, taki jak <xref:System.Linq.IQueryable%601>.

W poniższym `numbers` przykładzie jest źródłem danych i `num` jest zmienna zakresu. Należy zauważyć, że obie zmienne są silnie wpisane, mimo że var [słowo](var.md) kluczowe jest używane.

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a>Zmienna zakresu

Kompilator wywnioskować typ zmiennej zakresu, <xref:System.Collections.Generic.IEnumerable%601>gdy źródło danych implementuje . Na przykład, jeśli źródło ma `IEnumerable<Customer>`typ , zmienna zakresu jest `Customer`wywnioskować jako . Jedynym czasem, który należy określić typ jawnie jest, gdy `IEnumerable` źródło <xref:System.Collections.ArrayList>jest typem nierodzajowym, takich jak . Aby uzyskać więcej informacji, zobacz [Jak wysyłać zapytania do list tabliczki z linq](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).

W poprzednim `num` przykładzie jest wywnioskować, że jest typu `int`. Ponieważ zmienna zakresu jest silnie typizona, można wywołać metody na nim lub użyć go w innych operacjach. Na przykład zamiast `select num`pisać , `select num.ToString()` można napisać, aby spowodować wyrażenie kwerendy, aby zwrócić sekwencję ciągów zamiast liczb całkowitych. Lub można `select num + 10` napisać spowodować wyrażenie zwrócić sekwencji 14, 11, 13, 12, 10. Aby uzyskać więcej informacji, zobacz [wybierz klauzulę](select-clause.md).

Zmienna zakresu jest jak zmienna iteracji w [foreach](foreach-in.md) instrukcji, z wyjątkiem jednej bardzo ważnej różnicy: zmienna zakresu nigdy nie przechowuje danych ze źródła. To tylko wygoda składni, która umożliwia kwerendzie opisanie, co nastąpi po wykonaniu kwerendy. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do linq zapytania (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="compound-from-clauses"></a>Związek z klauzul

W niektórych przypadkach każdy element w sekwencji źródłowej może być sekwencją lub zawierać sekwencję. Na przykład źródło danych może `IEnumerable<Student>` być, gdzie każdy obiekt studenta w sekwencji zawiera listę wyników testów. Aby uzyskać dostęp do `Student` wewnętrznej listy w `from` ramach każdego elementu, można użyć klauzul złożonych. Technika jest jak przy użyciu zagnieżdżonych [foreach](foreach-in.md) instrukcji. Można [dodać, gdzie](partial-method.md) lub [orderby](orderby-clause.md) klauzule do jednej `from` klauzuli do filtrowania wyników. W poniższym przykładzie `Student` przedstawiono sekwencję obiektów, `List` z których każdy zawiera wewnętrzne liczby całkowite reprezentujące wyniki testów. Aby uzyskać dostęp do listy `from` wewnętrznej, należy użyć klauzuli złożonej. W razie potrzeby można `from` wstawić klauzule między dwiema klauzulami.

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a>Używanie wielu z klauzul do wykonywania sprzężeń

`from` Compound klauzula jest używana do uzyskiwania dostępu do kolekcji wewnętrznych w jednym źródle danych. Jednak kwerenda może również `from` zawierać wiele klauzul, które generują dodatkowe zapytania z niezależnych źródeł danych. Ta technika umożliwia wykonywanie niektórych typów operacji sprzężenia, które nie są możliwe przy użyciu [join klauzuli](join-clause.md).

W poniższym przykładzie `from` pokazano, jak dwie klauzule mogą służyć do utworzenia pełnego sprzężenia krzyżowego dwóch źródeł danych.

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

Aby uzyskać więcej informacji na `from` temat operacji sprzężenia, które używają wielu klauzul, zobacz [Wykonywanie sprzężeń zewnętrznych lewej](../../linq/perform-left-outer-joins.md).

## <a name="see-also"></a>Zobacz też

- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
