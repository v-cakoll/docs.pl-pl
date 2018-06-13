---
title: Operator %= (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: aadcb5ef969ff408cc1e738fc0f5b67152fdc78b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171970"
---
# <a name="-operator-c-reference"></a>Operator %= (odwołanie w C#)
Operator przypisania reszty.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `%=` operator przypisania, takich jak  
  
```csharp  
x %= y  
```  
  
 jest równoważny  
  
```csharp  
x = x % y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [% Operator](../../../csharp/language-reference/operators/remainder-operator.md) jest wstępnie zdefiniowane na typy liczbowe do obliczenia resztę po dzielenia.  
  
 `%=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [% operator](../../../csharp/language-reference/operators/remainder-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
