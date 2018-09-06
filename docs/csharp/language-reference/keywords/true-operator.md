---
title: true — Operator (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- true operator [C#]
ms.assetid: acaba817-5da5-4364-b3b2-2e5c75ec1839
ms.openlocfilehash: 54b8d764dc673598474d6adbbee82e0223a16b93
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43733852"
---
# <a name="true-operator-c-reference"></a>true — Operator (odwołanie w C#)
Zwraca [bool](../../../csharp/language-reference/keywords/bool.md) wartość `true` aby wskazać, że argument ma wartość true i zwraca `false` inaczej.  
  
 Przed C# w wersji 2.0 `true` i `false` operatorów były używane do tworzenia typów zdefiniowanych przez użytkownika wartości null, które były zgodne z typami, takich jak `SqlBool`. Jednak język teraz udostępnia wbudowaną obsługę typy o wartości zerowalnej i w miarę możliwości należy używać tych zamiast przeciążenia `true` i `false` operatorów. Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).  
  
 Za pomocą wartości logicznych dopuszczającego wartość null, wyrażenie `a != b` nie jest zawsze równa `!(a == b)` , ponieważ co najmniej jeden z wartości może mieć wartości null. Musisz oba przeciążenia `true` i `false` operatory oddzielnie, aby wykryć wartości null w wyrażeniu. Poniższy przykład pokazuje, jak przeciążenia i użyj `true` i `false` operatorów.  
  
 [!code-csharp[csrefKeywordsOperator#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/true-operator_1.cs)]  
  
 Typ, który przeciążenia `true` i `false` operatorzy mogą służyć do kontrolowania wyrażenia w [Jeśli](../../../csharp/language-reference/keywords/if-else.md), [czy](../../../csharp/language-reference/keywords/do.md), [podczas](../../../csharp/language-reference/keywords/while.md), i [ Aby uzyskać](../../../csharp/language-reference/keywords/for.md) instrukcji i [wyrażenia warunkowe](../../../csharp/language-reference/operators/conditional-operator.md).  
  
 Jeśli typ definiuje operator `true`, również muszą definiować operator [false](../../../csharp/language-reference/keywords/false.md).  
  
 Typ bezpośrednio nie mogą przeciążać operatory logiczne warunkowe ([ && ](../../../csharp/language-reference/operators/conditional-and-operator.md) i [ &#124; &#124; ](../../../csharp/language-reference/operators/conditional-or-operator.md)), ale taki sam efekt można osiągnąć przez przeciążenie zwykłych logiczne operatory i operatory `true` i `false`.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [false](../../../csharp/language-reference/keywords/false.md)
