---
title: OrderBy — klauzula C# -Reference
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: d88b2b40f63f0616cfd54e8abb62f1bc2183f776
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713297"
---
# <a name="orderby-clause-c-reference"></a>Klauzula orderby (odwołanie w C#)

W wyrażeniu zapytania klauzula `orderby` powoduje, że zwracaną sekwencję lub podsekwencję (grupę) można sortować w kolejności rosnącej lub malejącej. Można określić wiele kluczy, aby wykonać jedną lub więcej pomocniczych operacji sortowania. Sortowanie jest wykonywane przez domyślną funkcję porównującą dla typu elementu. Domyślna kolejność sortowania to Ascending. Można również określić niestandardową funkcję porównującą. Jednak jest on dostępny tylko przy użyciu składni opartej na metodzie. Aby uzyskać więcej informacji, zobacz [Sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pierwsze zapytanie sortuje wyrazy w kolejności alfabetycznej, zaczynając od A, a drugie zapytanie sortuje te same wyrazy w kolejności malejącej. (`ascending` słowo kluczowe jest domyślną wartością sortowania i można je pominąć).

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje sortowanie podstawowe dla nazwisk uczniów, a następnie pomocnicze sortowanie według ich imion.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji klauzula `orderby` jest tłumaczona na wywołanie metody <xref:System.Linq.Enumerable.OrderBy%2A>. Wiele kluczy w klauzuli `orderby` przetłumaczy na wywołania metody <xref:System.Linq.Enumerable.ThenBy%2A>.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [group, klauzula](group-clause.md)
- [Wprowadzenie do korzystania z LINQ w C#](/dotnet/csharp/programming-guide/concepts/linq/)
