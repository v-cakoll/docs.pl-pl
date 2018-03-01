---
title: "Operator ^= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operator ^= (odwołanie w C#)
Operator przypisania OR wyłączne.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x ^= y  
```  
  
 jest szacowana jako  
  
```  
x = x ^ y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacji na całkowite operandy i logicznego OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.  
  
 ^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
