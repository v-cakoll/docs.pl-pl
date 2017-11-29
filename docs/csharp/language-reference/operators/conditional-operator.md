---
title: "?: — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9abfe4ca6be29b54edd591b503069c15e02c3532
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>?: — Operator (odwołanie w C#)
Operator warunkowy (`?:`) zwraca jedną z dwóch wartości w zależności od wartości wyrażenia logicznego. Poniżej przedstawiono składnię operatora warunkowego.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Uwagi  
 `condition` Musi być `true` lub `false`. Jeśli `condition` jest `true`, `first_expression` jest obliczane i staje się wynik. Jeśli `condition` jest `false`, `second_expression` jest obliczane i staje się wynik. Obliczane jest tylko jedno z dwóch wyrażeń.  
  
 Typ elementu `first_expression` i `second_expression` muszą być takie same lub niejawna konwersja musi istnieć z jednego typu do drugiego.  
  
 Można wyrazić obliczeń, które w przeciwnym razie mogą wymagać `if-else` konstrukcji więcej zwięzłym, przy użyciu operatora warunkowego. Na przykład w poniższym kodzie użyto najpierw `if` instrukcji, a następnie operator warunkowy do klasyfikowania całkowitą jako dodatnią lub ujemną.  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 Operator warunkowy ma łączność do prawej strony. Wyrażenie `a ? b : c ? d : e` jest szacowana jako `a ? b : (c ? d : e)`, nie jako `(a ? b : c) ? d : e`.  
  
 Operatorów warunkowych nie można przeciążać.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)  
 [if-else](../../../csharp/language-reference/keywords/if-else.md)  
 [?. i? Operatory](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [?? Operator](../../../csharp/language-reference/operators/null-conditional-operator.md)
