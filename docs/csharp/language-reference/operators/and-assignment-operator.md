---
title: '&amp;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 092f46ddd8ca52e2d705200768c93a3473f1520f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172051"
---
# <a name="amp-operator-c-reference"></a>&amp;= — Operator (odwołanie w C#)
Operator przypisania AND.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `&=` operator przypisania, takich jak  
  
```csharp  
x &= y  
```  
  
 jest równoważny  
  
```csharp  
x = x & y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [& — Operator](../../../csharp/language-reference/operators/and-operator.md) dokonuje logicznego operacji i na całkowite argumenty i logiczny AND `bool` argumentów operacji.  
  
 `&=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać plik binarny [& — operator](../../../csharp/language-reference/operators/and-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
