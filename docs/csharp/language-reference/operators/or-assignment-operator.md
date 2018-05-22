---
title: '|= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: 18246d013275c8d6c8ad7e05409387457afc3442
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>|= — Operator (odwołanie w C#)
Operator przypisania OR.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `|=` operator przypisania, takich jak  
  
```csharp  
x |= y  
```  
  
 jest równoważny  
  
```csharp  
x = x | y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) dokonuje logicznego OR operacji na całkowite operandy i logiczne lub argumentów bool.  
  
 `|=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
