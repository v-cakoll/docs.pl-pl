---
title: Klauzula Let (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 9d625db1231687cdad2e24303b2e08ecf736a50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="let-clause-c-reference"></a>Klauzula Let (odwołanie w C#)
W wyrażeniu zapytania czasami jest przydatne do przechowywania wynik wyrażenia podrzędnego, aby można było go używać w klauzulach kolejne. Można to zrobić z `let` — słowo kluczowe, która tworzy nową zmienną zakresu i inicjowania wynik wyrażenia, należy podać. Po zainicjowany z wartością, zmienna zakresu nie może służyć do przechowywania innej wartości. Jednak jeśli posiada kolejność typu zmienną zakresu może być badana.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `let` jest używany na dwa sposoby:  
  
1.  Aby utworzyć typ wyliczalny, który może sam być badana.  
  
2.  Aby umożliwić wykonanie zapytania w celu wywołania `ToLower` tylko jeden raz na zmienną zakresu `word`. Bez użycia `let`, należy wywołać `ToLower` w każdym predykatu w `where` klauzuli.  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Słowa kluczowe zapytania (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Wyrażenia zapytań LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Wprowadzenie do korzystania z LINQ w C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Porady: obsługa wyjątków w wyrażeniach zapytań](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
