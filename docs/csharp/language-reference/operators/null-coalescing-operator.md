---
title: ?? i? = Operatory- C# odwołanie
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: b3d56c6c08443d344002b8e780a72fc547c316bb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712653"
---
# <a name="-and--operators-c-reference"></a>?? i? = — OperatoryC# (odwołanie)

Operator łączenia wartości null `??` zwraca wartość operandu po lewej stronie, jeśli nie `null`; w przeciwnym razie oblicza argument operacji po prawej stronie i zwraca jego wynik. Operator `??` nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.

Dostępne w C# 8,0 i późniejszych, operator przypisania łączącej wartości null `??=` przypisuje wartość jego operandu po lewej stronie tylko wtedy, gdy operand po lewej stronie jest obliczany do `null`. Operator `??=` nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

Argument operacji po lewej stronie operatora `??=` musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora](../../programming-guide/indexers/index.md) .

W C# 7,3 i starszych typach operandu po lewej stronie operatora `??` musi być [typem referencyjnym](../keywords/reference-types.md) lub [typem wartości null](../builtin-types/nullable-value-types.md). Począwszy od C# 8,0, ten wymóg jest zastępowany następującymi: typem operandu po lewej stronie operatorów `??` i `??=` nie może być typ wartości niedopuszczający wartości null. W szczególności, począwszy od C# 8,0, można użyć operatorów łączenia wartości null z nieokreślonymi parametrami typu:

[!code-csharp[unconstrained type parameter](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#UnconstrainedType)]

Operatory łączenia wartości null są z prawej strony skojarzenia. To jest wyrażenie w postaci

```csharp
a ?? b ?? c
d ??= e ??= f
```

są oceniane jako

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a>Przykłady

Operatory `??` i `??=` mogą być przydatne w następujących scenariuszach:

- W wyrażeniach zawierających [Operatory warunkowe o wartości null?. i? []](member-access-operators.md#null-conditional-operators--and-)można użyć operatora `??`, aby podać alternatywne wyrażenie do obliczenia w przypadku, gdy wynik wyrażenia z operacjami warunkowymi o wartości null jest `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Podczas pracy z [typami wartości null](../builtin-types/nullable-value-types.md) i musi podać wartość bazowego typu wartości, użyj operatora `??`, aby określić wartość, która ma zostać podana w przypadku, gdy wartość typu null jest `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, jeśli wartość, która ma zostać użyta, gdy wartość typu null jest `null` powinna być wartością domyślną bazowego typu wartości.

- Począwszy od C# 7,0, można użyć [wyrażenia`throw`](../keywords/throw.md#the-throw-expression) jako wiersza operacji po prawej stronie operatora `??`, aby kod sprawdzania argumentów był bardziej zwięzły:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  W powyższym przykładzie pokazano również, jak używać [składowych wyrażeń](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) w celu zdefiniowania właściwości.

- Począwszy od C# 8,0, można użyć operatora `??=`, aby zamienić kod formularza

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  przy użyciu następującego kodu:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Przeciążanie operatora

Operatory `??` i `??=` nie mogą być przeciążone.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji na temat operatora `??`, zobacz sekcję [operator łączenia wartości null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Aby uzyskać więcej informacji na temat operatora `??=`, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [?. i ?[] Operatory](member-access-operators.md#null-conditional-operators--and-)
- [?: — operator](conditional-operator.md)
