---
title: "select — Klauzula (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f40bc26d1812e76ac618c5a0ddf23c4cef2700d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-c-reference"></a>select — Klauzula (odwołanie w C#)
W wyrażeniu zapytania `select` klauzuli Określa typ wartości, które będą tworzone podczas wykonywania zapytania. Wynik jest oparta na obliczanie poprzedniego klauzule i wszystkie wyrażenia w `select` klauzuli samej siebie. Wyrażenia zapytania musi kończyć się albo `select` klauzuli lub [grupy](../../../csharp/language-reference/keywords/group-clause.md) klauzuli.  
  
 W poniższym przykładzie przedstawiono prosty `select` klauzuli w wyrażeniu zapytania.  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 Typ sekwencji utworzonego przez `select` klauzuli określa typu zmienną zapytania `queryHighScores`. Ogólnie rzecz biorąc `select` klauzuli właśnie Określa zmienną zakresu. Powoduje to, że zwrócony sekwencja zawierać elementów tego samego typu jako źródła danych. Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md). Jednak `select` klauzuli również zapewnia zaawansowany mechanizm Przekształcanie (lub *projekcji*) źródła danych na nowe typy. Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono różne formy `select` klauzuli może potrwać. W każdym zapytaniu, należy zwrócić uwagę relacji między `select` klauzul i typ *zmienną zapytania* (`studentQuery1`, `studentQuery2`i tak dalej).  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 Jak pokazano w `studentQuery8` w poprzednim przykładzie, czasem może zaistnieć elementy zwrócony sekwencji zawiera tylko podzbiór właściwości elementów źródła. Utrzymując możliwie najmniejsze zwrócony sekwencji można zmniejszyć wymagania dotyczące pamięci i przyspieszenie wykonywania zapytania. Można to zrobić przez utworzenie typu anonimowego w `select` klauzul i zainicjować go odpowiednie właściwości z elementu źródłowego za pomocą inicjatora obiektów. Na przykład jak to zrobić, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).  
  
## <a name="remarks"></a>Uwagi  
 W czasie kompilacji `select` klauzuli są tłumaczone na wywołanie metody <xref:System.Linq.Enumerable.Select%2A> — operator zapytań standardowa.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Klauzula FROM](../../../csharp/language-reference/keywords/from-clause.md)  
 [Partial — metoda () (odwołanie w C#)](../../../csharp/language-reference/keywords/partial-method.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
