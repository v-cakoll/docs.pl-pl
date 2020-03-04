---
title: '?: — odwołanie C# do operatora'
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 6e8fde8c210b2c33cc514167be7face657cbb618
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239382"
---
# <a name="-operator-c-reference"></a>?: — operatorC# (odwołanie)

Operator warunkowy `?:`, nazywany również operatorem warunkowym Trzyelementowy, oblicza wyrażenie logiczne i zwraca wynik jednego z dwóch wyrażeń, w zależności od tego, czy wyrażenie logiczne ma być szacowane do `true`, czy `false`. Począwszy od C# 7,2, [wyrażenie warunkowe](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.

Składnia operatora warunkowego jest następująca:

```csharp
condition ? consequent : alternative
```

Wyrażenie `condition` musi być szacowane do `true` lub `false`. Jeśli `condition` oblicza `true`, zostanie obliczone wyrażenie `consequent`, a jego wynik zmieni się na wynik operacji. Jeśli `condition` oblicza `false`, zostanie obliczone wyrażenie `alternative`, a jego wynik zmieni się na wynik operacji. Oceniane są tylko `consequent` lub `alternative`.

Typ `consequent` i `alternative` musi być taki sam lub musi być niejawną konwersją z jednego typu na drugi.

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

[!code-csharp-interactive[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Wyrażenie warunkowe ref

Począwszy od C# 7,2, można użyć wyrażenia ref warunkowego do zwrócenia odwołania do wyniku jednego z dwóch wyrażeń. Można przypisać to odwołanie do zmiennej lokalnej [ref](../keywords/ref.md#ref-locals) lub [ref lokalnego tylko do odczytu](../keywords/ref.md#ref-readonly-locals) lub użyć jej jako [wartości zwracanej przez odwołanie](../keywords/ref.md#reference-return-values) lub jako [parametru metody`ref`](../keywords/ref.md#passing-an-argument-by-reference).

Składnia wyrażenia ref warunkowego jest następująca:

```csharp
condition ? ref consequent : ref alternative
```

Podobnie jak w przypadku oryginalnego operatora warunkowego wyrażenie ref oblicza tylko jeden z dwóch wyrażeń: `consequent` lub `alternative`.

W przypadku wyrażenia ref warunkowego typ `consequent` i `alternative` muszą być takie same.

Poniższy przykład demonstruje użycie warunkowego wyrażenia ref:

[!code-csharp-interactive[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operator warunkowy i instrukcja `if..else`

Użycie operatora warunkowego zamiast instrukcji [if-else](../keywords/if-else.md) może spowodować bardziej zwięzły kod w przypadkach, gdy konieczne jest warunkowe obliczenie wartości. Poniższy przykład ilustruje dwa sposoby klasyfikowania liczby całkowitej jako ujemnej lub nieujemnej:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatora warunkowego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [warunkowego operatora](~/_csharplang/spec/expressions.md#conditional-operator) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na temat wyrażenia ref warunkowego, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [if-else, instrukcja](../keywords/if-else.md)
- [?. lub? operator []](member-access-operators.md#null-conditional-operators--and-)
- [?? i? = — Operatory](null-coalescing-operator.md)
- [ref — słowo kluczowe](../keywords/ref.md)
