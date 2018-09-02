---
title: '?: — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 150149453a67d8e5319461266865cb25be180347
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421507"
---
# <a name="-operator-c-reference"></a>?: — Operator (odwołanie w C#)
Operator warunkowy (`?:`), powszechnie znane jako trójargumentowy operator warunkowy zwraca jedną z dwóch wartości w zależności od wartości wyrażenia logicznego. Poniżej przedstawiono składnię operatora warunkowego.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Uwagi  
 `condition` Musi zwrócić `true` lub `false`. Jeśli `condition` jest `true`, `first_expression` jest obliczane i staje się wynik. Jeśli `condition` jest `false`, `second_expression` jest obliczane i staje się wynik. Obliczane jest tylko jedno z dwóch wyrażeń.  
  
 Typ elementu `first_expression` i `second_expression` musi być taka sama, lub musi istnieć niejawna konwersja z jednego typu na drugi.  
  
 Można wyrazić obliczenia, które w przeciwnym razie może wymagać `if-else` konstruowania bardziej zwięzłym, używając operatora warunkowego. Na przykład w poniższym kodzie użyto najpierw `if` instrukcji, a następnie operator warunkowy w celu zaklasyfikowania liczby całkowitej jako dodatnia lub ujemna.  
  
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
  
 Operator warunkowy ma łączność do prawej strony. Wyrażenie `a ? b : c ? d : e` jest oceniane jako `a ? b : (c ? d : e)`, nie jako `(a ? b : c) ? d : e`.  
  
 Operatorów warunkowych nie można przeciążać.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [Operatory ?. i ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [??, operator](../../../csharp/language-reference/operators/null-coalescing-operator.md)
