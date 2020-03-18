---
title: klauzula orderby - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173578"
---
# <a name="orderby-clause-c-reference"></a>Klauzula orderby (odwołanie w C#)

W wyrażeniu `orderby` kwerendy klauzula powoduje, że zwracana sekwencja lub podsekwencja (grupa) mają być sortowane w kolejności rosnącej lub malejącej. Można określić wiele kluczy w celu wykonania jednej lub więcej pomocniczych operacji sortowania. Sortowanie jest wykonywane przez domyślny porównywarka dla typu elementu. Domyślna kolejność sortowania jest rosnąco. Można również określić niestandardowego porównania. Jednak jest on aplikowane tylko przy użyciu składni opartej na metodach. Aby uzyskać więcej informacji, zobacz [Sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pierwsza kwerenda sortuje wyrazy w kolejności alfabetycznej, począwszy od A, a druga kwerenda sortuje te same wyrazy w porządku malejącym. (Słowo `ascending` kluczowe jest domyślną wartością sortowania i można je pominąć).

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje sortowanie podstawowe na nazwiska uczniów, a następnie sortowanie dodatkowe na ich imiona.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji `orderby` klauzula jest tłumaczona <xref:System.Linq.Enumerable.OrderBy%2A> na wywołanie metody. Wiele kluczy `orderby` w <xref:System.Linq.Enumerable.ThenBy%2A> klauzuli przetłumaczyć na wywołania metody.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [LINQ w C#](../../linq/index.md)
- [group, klauzula](group-clause.md)
- [Language Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
