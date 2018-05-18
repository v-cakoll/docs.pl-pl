---
title: += — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bcd56acad8e2b08585e5ae60f1c3cf8183b5664a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>+= — Operator (odwołanie w C#)
Operator przypisania dodawania.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `+=` operator przypisania, takich jak  
  
```csharp  
x += y  
```  
  
 jest równoważny  
  
```csharp  
x = x + y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. Znaczenie [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) zależy od typów `x` i `y` (oprócz dla argumentów operacji liczbowych, łączenia dla argumentów ciągu i tak dalej).  
  
 `+=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` Operator służy również do określają metodę, która będzie wywoływana w odpowiedzi na zdarzenia; metody te są wywoływane programy obsługi zdarzeń. Korzystanie z `+=` operatora w tym kontekście jest określany jako *subskrybowanie zdarzeń*. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
