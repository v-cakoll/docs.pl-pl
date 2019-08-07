---
title: '?: — odwołanie C# do operatora'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 923591634599a6bbac74d43b105f4e46b492fa1a
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796465"
---
# <a name="-operator-c-reference"></a>?: — operatorC# (odwołanie)

Operator `?:`warunkowy, często znany jako operator warunkowy Trzyelementowy, ocenia wyrażenie logiczne i zwraca wynik oceny jednego z dwóch wyrażeń, w zależności od tego, czy wyrażenie logiczne daje `true` lub `false`. Począwszy od C# 7,2, [wyrażenie warunkowe](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.

Składnia operatora warunkowego jest następująca:

```csharp
condition ? consequent : alternative
```

Wyrażenie musi być szacowane do `true` lub `false`. `condition` Jeśli `condition` jest wynikiem obliczenia `true`, `consequent` wyrażenie jest oceniane, a jego wynik zmieni się na wynik operacji. Jeśli `condition` jest wynikiem obliczenia `false`, `alternative` wyrażenie jest oceniane, a jego wynik zmieni się na wynik operacji. Tylko `consequent` lub`alternative` jest oceniane.

Typ `consequent` i`alternative` musi być taki sam lub musi być niejawną konwersją z jednego typu na drugi.

Operator warunkowy jest prawym przyciskiem asocjacyjnym, czyli wyrażeniem formularza

```csharp
a ? b : c ? d : e
```

jest wykonywane jako

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Poniższego urządzenia można użyć do zapamiętania, jak jest oceniany operator warunkowy:
>
> ```text
> is this condition true ? yes : no
> ```

Poniższy przykład ilustruje użycie operatora warunkowego:

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Wyrażenie warunkowe ref

Począwszy od C# 7,2, można użyć wyrażenia ref warunkowego do zwrócenia odwołania do wyniku jednego z dwóch wyrażeń. Można przypisać to odwołanie do zmiennej lokalnej [ref](../keywords/ref.md#ref-locals) lub [ref tylko do odczytu](../keywords/ref.md#ref-readonly-locals) , lub użyć jej jako [](../keywords/ref.md#reference-return-values) [ `ref` ](../keywords/ref.md#passing-an-argument-by-reference)wartości zwracanej przez odwołanie lub jako parametru metody.

Składnia wyrażenia ref warunkowego jest następująca:

```csharp
condition ? ref consequent : ref alternative
```

Podobnie jak w przypadku oryginalnego operatora warunkowego wyrażenie ref oblicza tylko jedno z dwóch wyrażeń: `consequent` albo lub. `alternative`

W przypadku warunkowego wyrażenia ref typ `consequent` i `alternative` musi być taki sam.

Poniższy przykład demonstruje użycie warunkowego wyrażenia ref:

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

Aby uzyskać więcej informacji, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operator warunkowy i `if..else` instrukcja

Użycie operatora warunkowego nad instrukcją [if-else](../keywords/if-else.md) może spowodować zwiększenie zwięzłego kodu w przypadkach, gdy konieczne jest warunkowe obliczenie wartości. Poniższy przykład ilustruje dwa sposoby klasyfikowania liczby całkowitej jako ujemnej lub nieujemnej:

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatorów warunkowych nie można przeciążać.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [warunkowego operatora](~/_csharplang/spec/expressions.md#conditional-operator) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [if-else, instrukcja](../keywords/if-else.md)
- [?. i?\[\] Operatory](member-access-operators.md#null-conditional-operators--and-)
- [?? zakład](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
