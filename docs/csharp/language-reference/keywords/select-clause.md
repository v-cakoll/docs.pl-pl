---
title: select klauzula - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173513"
---
# <a name="select-clause-c-reference"></a>select — Klauzula (odwołanie w C#)

W wyrażeniu `select` kwerendy klauzula określa typ wartości, które zostaną wyprodukowane podczas wykonywania kwerendy. Wynik opiera się na ocenie wszystkich poprzednich klauzul i na `select` wszelkich wyrażeniach w samej klauzuli. Wyrażenie kwerendy musi zakończyć `select` się klauzulą lub klauzulą [grupową.](group-clause.md)

W poniższym przykładzie `select` przedstawiono prostą klauzulę w wyrażeniu zapytania.

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

Typ sekwencji produkowane przez `select` klauzulę określa typ zmiennej `queryHighScores`kwerendy . W najprostszym przypadku `select` klauzula określa tylko zmienną zakresu. Powoduje to, że zwrócona sekwencja zawiera elementy tego samego typu co źródło danych. Aby uzyskać więcej informacji, zobacz [Wpisywanie relacji w operacjach kwerend LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Jednak klauzula `select` zapewnia również zaawansowany mechanizm przekształcania (lub *projekcji)* danych źródłowych w nowe typy. Aby uzyskać więcej informacji, zobacz [Transformacje danych z LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono wszystkie `select` różne formy, które może podjąć klauzula. W każdym zapytaniu należy `select` zwrócić uwagę na relację między `studentQuery2`klauzulą a typem *zmiennej zapytania* (`studentQuery1`, i tak dalej).

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

Jak pokazano w `studentQuery8` poprzednim przykładzie, czasami może chcesz elementy zwróconej sekwencji zawierać tylko podzbiór właściwości elementów źródłowych. Utrzymując zwróconą sekwencję tak małą, jak to możliwe, można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania kwerendy. Można to osiągnąć, tworząc typ `select` anonimowy w klauzuli i przy użyciu inicjatora obiektu, aby zainicjować go z odpowiednimi właściwościami z elementu źródłowego. Aby uzyskać przykład, jak to zrobić, zobacz [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="remarks"></a>Uwagi

W czasie kompilacji `select` klauzula jest tłumaczona <xref:System.Linq.Enumerable.Select%2A> na wywołanie metody do standardowego operatora kwerendy.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Słowa kluczowe zapytania (LINQ)](query-keywords.md)
- [z klauzuli](from-clause.md)
- [częściowe (metoda) (odwołanie do języka C#)](partial-method.md)
- [Typy anonimowe](../../programming-guide/classes-and-structs/anonymous-types.md)
- [LINQ w C#](../../linq/index.md)
- [Language Integrated Query (LINQ)](../../programming-guide/concepts/linq/index.md)
