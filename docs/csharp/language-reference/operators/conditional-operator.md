---
title: '?: operator — odwołanie do języka C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 1a17ba092d4228ba909c8774a2f7e15c2c50cfdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399519"
---
# <a name="-operator-c-reference"></a>?: operator (odwołanie do języka C#)

Operator `?:`warunkowy `true` `false`, znany również jako operator warunkowy wzięcia wt.

Składnia operatora warunkowego jest następująca:

```csharp
condition ? consequent : alternative
```

Wyrażenie `condition` musi oceniać do `true` lub `false`. Jeśli `condition` zostanie `true`obliczona `consequent` wartość , wyrażenie zostanie obliczone, a jego wynik stanie się wynikiem operacji. Jeśli `condition` zostanie `false`obliczona `alternative` wartość , wyrażenie zostanie obliczone, a jego wynik stanie się wynikiem operacji. Tylko `consequent` `alternative` lub jest oceniana.

Typ `consequent` i `alternative` musi być taka sama lub musi istnieć niejawna konwersja z jednego typu na drugi.

Operator warunkowy ma charakter asocjatywny, to oznacza, że jest wyrazem formy

```csharp
a ? b : c ? d : e
```

jest oceniana jako

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> Za pomocą następującego urządzenia mnemonic można zapamiętać sposób oceny operatora warunkowego:
>
> ```text
> is this condition true ? yes : no
> ```

W poniższym przykładzie przedstawiono użycie operatora warunkowego:

[!code-csharp-interactive[non ref conditional](snippets/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Warunkowe wyrażenie ref

Począwszy od C# 7.2 ref [lokalnej](../keywords/ref.md#ref-locals) lub [ref odczytu tylko](../keywords/ref.md#ref-readonly-locals) zmienna lokalna może być przypisana warunkowo z warunkowego wyrażenia ref. Można również użyć wyrażenia warunkowego ref jako [wartości zwracanej odwołania](../keywords/ref.md#reference-return-values) lub jako [ `ref` argumentu metody](../keywords/ref.md#passing-an-argument-by-reference).

Składnia wyrażenia warunkowego ref jest następująca:

```csharp
condition ? ref consequent : ref alternative
```

Podobnie jak oryginalny operator warunkowy, warunkowe wyrażenie ref oblicza `consequent` tylko `alternative`jedno z dwóch wyrażeń: albo .

W przypadku wyrażenia warunkowego ref typ `consequent` `alternative` i musi być taki sam.

W poniższym przykładzie przedstawiono użycie wyrażenia warunkowego ref:

[!code-csharp-interactive[conditional ref](snippets/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operator warunkowy i oświadczenie `if..else`

Użycie operatora warunkowego zamiast [instrukcji if-else](../keywords/if-else.md) może spowodować bardziej zwięzły kod w przypadkach, gdy trzeba warunkowo obliczyć wartość. W poniższym przykładzie przedstawiono dwa sposoby klasyfikacji liczby całkowitej jako ujemnej lub nienegatywnej:

[!code-csharp[conditional and if-else](snippets/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika nie może przeciążać operatora warunkowego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

Aby uzyskać więcej informacji na temat wyrażenia warunkowego ref, zobacz [notę propozycji funkcji](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [instrukcja if-else](../keywords/if-else.md)
- [?. I? [] operatorzy](member-access-operators.md#null-conditional-operators--and-)
- [?? I?? = operatorzy](null-coalescing-operator.md)
- [ref — słowo kluczowe](../keywords/ref.md)
