---
title: select — Klauzula (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: dcab29cdbe98b5e49463d9a2781d43d4b9ee9544
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467344"
---
# <a name="select-clause-c-reference"></a>select — Klauzula (odwołanie w C#)
W wyrażeniu zapytania `select` klauzula Określa typ wartości, które zostaną wygenerowane, gdy zapytanie jest wykonywane. Wynik jest oparty na obliczanie poprzedniego klauzul i wszystkie wyrażenia w `select` klauzuli sam. Wyrażenie zapytania musi kończyć się albo `select` klauzuli lub [grupy](../../../csharp/language-reference/keywords/group-clause.md) klauzuli.  
  
 W poniższym przykładzie przedstawiono prosty `select` klauzula w wyrażeniu zapytania.  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 Typ sekwencji generowany przez `select` klauzula Określa typ zmiennej zapytania `queryHighScores`. W najprostszym przypadku `select` klauzula określa tylko zmiennej zakresu. Powoduje to, że zwracana sekwencja zawiera elementy tego samego typu co źródło danych. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Jednak `select` klauzuli również zapewnia zaawansowany mechanizm przekształcenie (lub *przewidywania*) dane źródłowe do nowych typów. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne formy `select` klauzuli może potrwać. W każdym zapytaniu Pamiętaj relacji między `select` klauzuli i typu *zmienna zapytania* (`studentQuery1`, `studentQuery2`i tak dalej).  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 Jak pokazano na `studentQuery8` w poprzednim przykładzie, czasami konieczne może być elementy zwracana sekwencja zawiera tylko podzbiór właściwości elementy źródłowe. Poprzez zapewnienie możliwie najmniejsze zwracanej sekwencji można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania zapytania. Można to zrobić, tworząc typ anonimowy w `select` klauzula i za pomocą inicjatora obiektów, aby go zainicjować za pomocą odpowiednich właściwości z elementu źródłowego. Na przykład jak to zrobić, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="remarks"></a>Uwagi  
 W czasie kompilacji `select` klauzula jest tłumaczona na wywołanie metody do <xref:System.Linq.Enumerable.Select%2A> standardowego operatora zapytania.  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
- [from, klauzula](../../../csharp/language-reference/keywords/from-clause.md)  
- [Partial (metoda) (odwołanie w C#)](../../../csharp/language-reference/keywords/partial-method.md)  
- [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
