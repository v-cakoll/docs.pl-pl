---
title: '?: Operator - C# odwołania'
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
ms.openlocfilehash: 82ada5e4d1f56ea93bbd7f41b04cda9f98d678c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672397"
---
# <a name="-operator-c-reference"></a>?: Operator (odwołanie w C#)

Operator warunkowy `?:`, powszechnie znane jako operator warunkowy trójargumentowy ocenia wyrażenie logiczne i zwraca wynik obliczania wartości jednego z dwóch wyrażeń w zależności od tego, czy wyrażenie logiczne daje w wyniku `true` lub `false`. Począwszy od C# 7.2, [wyrażenie warunkowe ref](#conditional-ref-expression) zwraca odwołanie do wyniku jednego z dwóch wyrażeń.

Składnia służąca do operatora warunkowego jest następująca:

```csharp
condition ? consequent : alternative
```

`condition` Wyrażenia musi być `true` lub `false`. Jeśli `condition` daje w wyniku `true`, `consequent` wyrażenie jest obliczane, a jego wynik staje się wynik operacji. Jeśli `condition` daje w wyniku `false`, `alternative` wyrażenie jest obliczane, a jego wynik staje się wynik operacji. Tylko `consequent` lub `alternative` jest oceniany.

Typ `consequent` i `alternative` musi być w tej samej lub występują musi być niejawna konwersja z jednego typu na drugi.

Operator warunkowy jest łączność do prawej strony, oznacza to, że wyrażenie formularza

```csharp
a ? b : c ? d : e
```

jest wykonywane jako

```csharp
a ? b : (c ? d : e)
```

Przydatną urządzenia mnemoników, służących do zapamiętania, jak ocenia Ten operator jest zadając: 
```
is this condition true ? yes : no
```
za pomocą? część operator działający jako znak zapytania do poprzedniej instrukcji i następstwie działający jako logicznych odpowiedzi na to pytanie.

Poniższy przykład ilustruje użycie operatora warunkowego:

[!code-csharp[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Wyrażenie warunkowe ref

Począwszy od C# 7.2, umożliwia wyrażenie warunkowe ref zwraca odwołanie do wyniku jednego z dwóch wyrażeń. Można przypisać tego odwołania do [odwołanie lokalne](../keywords/ref.md#ref-locals) lub [odwołanie lokalne tylko do odczytu](../keywords/ref.md#ref-readonly-locals) zmiennej, lub użyj go jako [odwoływać się do wartości zwracanej](../keywords/ref.md#reference-return-values) lub jako [ `ref` — metoda Parametr](../keywords/ref.md#passing-an-argument-by-reference).

Wyrażenie warunkowe ref składnia jest następująca:

```csharp
condition ? ref consequent : ref alternative
```

Takich jak oryginalne operator warunkowy ref warunkowego wynikiem wyrażenia jest tylko jeden z dwóch wyrażeń: albo `consequent` lub `alternative`.

W przypadku wyrażenie warunkowe ref, typ `consequent` i `alternative` musi być taka sama.

W poniższym przykładzie pokazano użycie wyrażenie warunkowe ref:

[!code-csharp[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

Aby uzyskać więcej informacji, zobacz [Uwaga propozycji funkcji](../../../../_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Operator warunkowy i `if..else` — instrukcja

Użycie operatora warunkowego nad [if-else](../keywords/if-else.md) instrukcji może prowadzić do bardziej zwięzły widok kodu w przypadku, gdy trzeba warunkowo obliczenia wartości. W poniższym przykładzie pokazano zaklasyfikowania liczby całkowitej jako ujemny lub nieujemne na dwa sposoby:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Overloadability — operator

Operatorów warunkowych nie można przeciążać.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operator warunkowy](~/_csharplang/spec/expressions.md#conditional-operator) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [if-else, instrukcja](../keywords/if-else.md)
- [Operatory ?. i ?[]](null-conditional-operators.md)
- [??, operator](null-coalescing-operator.md)
- [ref keyword](../keywords/ref.md)
