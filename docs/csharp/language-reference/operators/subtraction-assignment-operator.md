---
title: "Operator -= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 443f0d717288a491838d23eaa63218150bd346d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
