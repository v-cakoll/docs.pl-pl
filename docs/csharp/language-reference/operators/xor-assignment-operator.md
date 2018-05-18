---
title: Operator ^= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: b868f2cdbfa8a80f89a12e6194a30154481f0b07
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>Operator ^= (odwołanie w C#)
Operator przypisania OR wyłączne.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```csharp  
x ^= y  
```  
  
 jest szacowana jako  
  
```csharp  
x = x ^ y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacji na całkowite operandy i logicznego OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.  
  
 ^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
