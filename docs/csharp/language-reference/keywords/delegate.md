---
title: "delegate (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 179e89cea0e683b72e57536d4e4d86b019493aed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-c-reference"></a>delegate (odwołanie w C#)
Deklaracja typu delegowanego jest podobny do sygnatury metody. Ma wartość zwracaną i dowolną liczbę parametrów dowolnego typu:  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 A `delegate` jest typem referencyjnym, który może służyć Hermetyzowanie nazwane ani metoda anonimowa. Obiekty delegowane są podobne do wskaźników funkcji w języku C++; jednak delegatów są bezpieczne i bezpieczne. W przypadku aplikacji o delegatów, zobacz [delegatów](../../../csharp/programming-guide/delegates/index.md) i [delegatów](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## <a name="remarks"></a>Uwagi  
 Obiekty delegowane stanowią podstawę dla [zdarzenia](../../../csharp/programming-guide/events/index.md).  
  
 Delegat można wdrożyć przez skojarzenie za pomocą metody nazwane i anonimowe. Aby uzyskać więcej informacji, zobacz [metody o nazwie](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) i [metod anonimowych](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 Obiekt delegowany musi być utworzone za pomocą wyrażenia metody lub lambda ma niezgodny typ zwracany i parametrów wejściowych. Aby uzyskać więcej informacji na stopień wariancję, jaki jest dozwolony w podpisie metody, zobacz [wariancji w Delegatach](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md). Do użytku z metod anonimowych delegat i kodu ma zostać skojarzony z nim są zadeklarowane jednocześnie. W tej sekcji omówiono obu kierunkach, tworzenie wystąpień obiektów delegowanych.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Typy odwołań](../../../csharp/language-reference/keywords/reference-types.md)  
 [Obiekty delegowane](../../../csharp/programming-guide/delegates/index.md)  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [Obiekty delegowane z nazwanego vs. Metody anonimowe](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [Metody anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
