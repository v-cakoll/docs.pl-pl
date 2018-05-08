---
title: Operator -= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 33aba2e944c8d0589949e7bdc77aadd4f213da28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="--operator-c-reference"></a>Operator -= (odwołanie w C#)
Operator przypisania odejmowania.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `-=` operator przypisania, takich jak  
  
```  
x -= y  
```  
  
 jest równoważny  
  
```  
x = x - y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. Znaczenie [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) jest zależna od typów `x` i `y` (odejmowania w przypadku argumentów operacji liczbowych, delegować usunięcia operandy delegata i tak dalej).  
  
 `-=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= Operator umożliwia również w języku C# anulowanie subskrypcji zdarzeń. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
