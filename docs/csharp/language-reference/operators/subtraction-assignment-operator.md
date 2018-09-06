---
title: Operator -= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 7cade0811536d836480f80a56cf8c4d09e089a0b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43773992"
---
# <a name="--operator-c-reference"></a>Operator -= (odwołanie w C#)
Operator przypisania odejmowania.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `-=`, takie jak  
  
```csharp  
x -= y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x - y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. Znaczenie [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) jest zależny od typów `x` i `y` (odejmowania w przypadku argumentów operacji numerycznych, delegowanie usuwania w przypadku argumentów operacji delegata i tak dalej).  
  
 `-=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [-operator](../../../csharp/language-reference/operators/subtraction-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
 -= Operator jest również używany w języku C# można anulować subskrypcję zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#6](codesnippet/CSharp/subtraction-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
