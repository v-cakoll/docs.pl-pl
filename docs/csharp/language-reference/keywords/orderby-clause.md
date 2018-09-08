---
title: Klauzula orderby (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217441"
---
# <a name="orderby-clause-c-reference"></a>Klauzula orderby (odwołanie w C#)

W wyrażeniu zapytania `orderby` klauzuli powoduje, że zwracana sekwencja lub podsekwencję (grupa) mają być sortowane w porządku rosnącym lub malejącym. Można określić wiele kluczy w celu wykonywania operacji dodatkowej sortowania jeden lub więcej. Sortowanie jest wykonywane przez domyślny moduł porównujący dla typu elementu. Domyślna kolejność sortowania jest rosnąca. Można również określić Niestandardowa funkcja porównująca. Jednak go jest dostępna tylko za pomocą składni oparte na metodzie. Aby uzyskać więcej informacji, zobacz [sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pierwsze zapytanie sortuje słów w kolejności alfabetycznej, zaczynając od A, i drugie zapytanie sortuje te same wyrazy w kolejności malejącej. ( `ascending` — Słowo kluczowe jest wartością domyślną sortowania i można je pominąć.)

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a>Przykład

Poniższy przykład wykonuje głównej Sortuj według nazwiska uczniów i drugiego sortowania na ich imiona.

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a>Uwagi

W czasie kompilacji `orderby` klauzula jest tłumaczona na wywołanie <xref:System.Linq.Enumerable.OrderBy%2A> metody. Wiele kluczy w `orderby` klauzuli przełożyć na <xref:System.Linq.Enumerable.ThenBy%2A> wywołania metody.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [Language Integrated Query (LINQ)](../../linq/index.md)
- [group, klauzula](group-clause.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)