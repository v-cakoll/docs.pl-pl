---
title: '&lt;&lt;= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5c2a177182561075442afc3f1b76603c6646bd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= — Operator (odwołanie w C#)
Operator przypisania przesunięcia w lewo.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x <<= y  
```  
  
 Jest wykonane w postaci  
  
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
