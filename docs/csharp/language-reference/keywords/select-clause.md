---
title: SELECT — klauzula - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 3ba52fccc0521df1a0bb5b6177575dc5d2152248
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633847"
---
# <a name="select-clause-c-reference"></a>select — Klauzula (odwołanie w C#)

W wyrażeniu zapytania `select` klauzula Określa typ wartości, które zostaną wygenerowane, gdy zapytanie jest wykonywane. Wynik jest oparty na obliczanie poprzedniego klauzul i wszystkie wyrażenia w `select` klauzuli sam. Wyrażenie zapytania musi kończyć się albo `select` klauzuli lub [grupy](group-clause.md) klauzuli.

W poniższym przykładzie przedstawiono prosty `select` klauzula w wyrażeniu zapytania.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekwencji generowany przez `select` klauzula Określa typ zmiennej zapytania `queryHighScores`. W najprostszym przypadku `select` klauzula określa tylko zmiennej zakresu. Powoduje to, że zwracana sekwencja zawiera elementy tego samego typu co źródło danych. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Jednak `select` klauzuli również zapewnia zaawansowany mechanizm przekształcenie (lub *przewidywania*) dane źródłowe do nowych typów. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono różne formy `select` klauzuli może potrwać. W każdym zapytaniu Pamiętaj relacji między `select` klauzuli i typu *zmienna zapytania* (`studentQuery1`, `studentQuery2`i tak dalej).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak pokazano na `studentQuery8` w poprzednim przykładzie, czasami konieczne może być elementy zwracana sekwencja zawiera tylko podzbiór właściwości elementy źródłowe. Poprzez zapewnienie możliwie najmniejsze zwracanej sekwencji można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania zapytania. Można to zrobić, tworząc typ anonimowy w `select` klauzula i za pomocą inicjatora obiektów, aby go zainicjować za pomocą odpowiednich właściwości z elementu źródłowego. Na przykład jak to zrobić, zobacz [inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Uwagi

W czasie kompilacji `select` klauzula jest tłumaczona na wywołanie metody do <xref:System.Linq.Enumerable.Select%2A> standardowego operatora zapytania.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [from, klauzula](from-clause.md)
- [Partial (metoda) (odwołanie w C#)](partial-method.md)
- [Typy anonimowe](../../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań LINQ](../../programming-guide/linq-query-expressions/index.md)
- [Wprowadzenie do korzystania z LINQ w C#](../../programming-guide/concepts/linq/getting-started-with-linq.md)
