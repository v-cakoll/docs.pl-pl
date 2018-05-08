---
title: '&gt;&gt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 41203f6e7c9929bb349d29c40cf7cc6c24550c36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= — Operator (odwołanie w C#)
Operator przypisania przesunięcia w prawo.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x >>= y  
```  
  
 jest szacowana jako  
  
```  
x = x >> y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [>> Operator](../../../csharp/language-reference/operators/right-shift-operator.md) przewiduje `x` prawej przez wartość określoną w `y`.  
  
 >> = — Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
