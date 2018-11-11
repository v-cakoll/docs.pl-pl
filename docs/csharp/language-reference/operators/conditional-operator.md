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
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980625"
---
# <a name="-operator-c-reference"></a>?: — Operator (odwołanie w C#)

Operator warunkowy (`?:`), powszechnie znane jako trójargumentowy operator warunkowy zwraca jedną z dwóch wartości w zależności od wartości wyrażenia logicznego. Poniżej przedstawiono składnię operatora warunkowego.  

```csharp
condition ? first_expression : second_expression;  
```

Począwszy od C# 7.2, `first_expression` i `second_expression` Moje można [ `ref` wyrażeń](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

Wynik może być przypisana do `ref` lub `ref readonly` zmiennej lub zmiennej za pomocą modyfikatora ani.

## <a name="remarks"></a>Uwagi

`condition` Musi zwrócić `true` lub `false`. Jeśli `condition` jest `true`, `first_expression` jest obliczane i staje się wynik. Jeśli `condition` jest `false`, `second_expression` jest obliczane i staje się wynik. Obliczane jest tylko jedno z dwóch wyrażeń. Jest to szczególnie ważne dla wyrażeń, których wynikiem jest `ref`, ponieważ następujące jest prawidłowy:

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

Odwołanie do `storage` nie jest oceniany, jeśli `storage` ma wartość null.

Gdy wynik jest wartością typu `first_expression` i `second_expression` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi. Jeśli wynik jest `ref`, typ `first_expression` i `second_expression` musi być taka sama.

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

Operator warunkowy, którego wynikiem jest wartość można znaleźć w poniższym przykładzie:

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

Alternatywne pokazuje operatora warunkowego, gdy wynik jest odwołaniem:

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
- [if-else](../../../csharp/language-reference/keywords/if-else.md)  
- [Operatory ?. i ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)  
- [??, operator](../../../csharp/language-reference/operators/null-coalescing-operator.md)
