---
title: false — Operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- false operator keyword [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f2001d92e99476131d6f03e13f0bc12104f638b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218261"
---
# <a name="false-operator-c-reference"></a>false — Operator (odwołanie w C#)
Zwraca [bool](../../../csharp/language-reference/keywords/bool.md) wartość `true` do wskazywania operand `false` i zwraca `false` inaczej.  
  
 Przed C# 2.0 `true` i `false` operatory były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`. Jednak język teraz udostępnia wbudowaną obsługę dla typów wartości null, a w miarę możliwości należy używać tych zamiast przeładowanie `true` i `false` operatorów. Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
 O wartości null wartości logiczne, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` ponieważ jedną lub obie wartości może mieć wartości null. Masz przeciążenia obu `true` i `false` operatorom oddzielnie poprawnie Obsługa wartości zerowych w wyrażeniu. Poniższy przykład przedstawia sposób przeciążenia i użyj `true` i `false` operatorów.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/false-operator_1.cs)]  
  
 Typ, który overloads `true` i `false` operatorów można używać do kontrolowania wyrażenie w [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), i [ Aby uzyskać](../../../csharp/language-reference/keywords/for.md) instrukcje i [wyrażenia warunkowe](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Jeśli typ definiuje operator `false`, również muszą definiować operator [true](../../../csharp/language-reference/keywords/true.md).  
  
 Typem bezpośrednio nie mogą przeciążać operatory logiczne warunkowe [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md), ale sam efekt można osiągnąć przez przeładowanie operatorów logicznych regularne operatory i `true` i `false`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [true](../../../csharp/language-reference/keywords/true.md)
