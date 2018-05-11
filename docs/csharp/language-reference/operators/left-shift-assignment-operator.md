---
title: '&lt;&lt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 9e2dbf693f7bee16c2ce97ccc7d52a318b8a3906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= — Operator (odwołanie w C#)
Operator przypisania przesunięcia w lewo.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x <<= y  
```  
  
 jest wykonywane w postaci
  
```  
x = x << y  
```  
  
 z tą różnicą, że `x` jest obliczone tylko raz. [Operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.  
  
 Operatora `<<=` nie można przeciążyć bezpośrednio, ale [ operator <<](../../../csharp/language-reference/operators/left-shift-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
