---
title: '&gt;&gt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171421"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= — Operator (odwołanie w C#)
Operator przypisania przesunięcia w prawo.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```csharp  
x >>= y  
```  
  
 jest wykonywane jako  
  
```csharp  
x = x >> y  
```  
  
 z tą różnicą, że `x` jest obliczone tylko raz. [Operator >>](../../../csharp/language-reference/operators/right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.  
  
 Operatora [ nie można przeciążyć bezpośrednio, ale ](../../../csharp/language-reference/operators/right-shift-operator.md)operator >>[ (zobacz ](../../../csharp/language-reference/keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
