---
title: += — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bd0997ec5b7d79a41e01f9c2b17533293e412c1e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933790"
---
# <a name="-operator-c-reference"></a>+= — Operator (odwołanie w C#)
Operator przypisania dodawania.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `+=`, takie jak  
  
```csharp  
x += y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x + y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. Znaczenie [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) zależy od typów `x` i `y` (Dodawanie liczbową argumentów operacji, łączenia dla argumentów ciągu i tak dalej).  
  
 `+=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [+ — operator](../../../csharp/language-reference/operators/addition-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
 `+=` Operator jest również używany do określają metodę, która będzie wywoływana w odpowiedzi na zdarzenie; metody te są wywoływane programy obsługi zdarzeń. Korzystanie z `+=` operatora w tym kontekście jest określany jako *subskrybowanie zdarzenia*. Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) i [delegatów](../../../csharp/programming-guide/delegates/index.md).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
