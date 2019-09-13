---
title: ?? i? = Operatory- C# odwołanie
ms.custom: seodec18
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
ms.openlocfilehash: 1e94038a41a6a6cc19be6c67bff2891397793fb3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924678"
---
# <a name="-and--operators-c-reference"></a>?? i? = — OperatoryC# (odwołanie)

Operator `??` łączenia wartości null zwraca wartość operandu po lewej stronie, jeśli nie jest `null`; w przeciwnym razie oblicza argument operacji po prawej stronie i zwraca wynik. `??` Operator nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.

Dostępne w C# 8,0 i nowszych operator `??=` przypisania łączenia wartości null przypisuje wartość jego operandu po lewej stronie tylko wtedy, gdy argument operacji po lewej stronie jest obliczany do. `null` `??=` Operator nie oblicza swojego operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość różną od null.

[!code-csharp[null-coalescing assignment](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#Assignment)]

Argument operacji `??=` po lewej stronie operatora musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora](../../programming-guide/indexers/index.md) . Aby uzyskać więcej informacji na temat przypisania łączenia z wartością null, zobacz [Uwaga dotycząca oferty funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

W C# 7,3 i starszych typach operandu `??` po lewej stronie operatora musi być typem referencyjnym lub [typem wartości null](../../programming-guide/nullable-types/index.md). Począwszy od C# 8,0, ten wymóg jest zastępowany następującym: typ operandu `??` i operatorów operatora and `??=` nie może być typem wartości niedopuszczających wartości null. W szczególności można użyć operatorów łączenia wartości null z nieokreślonymi parametrami typu w C# 8,0 i późniejszych:

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

Operatory `??` i`??=` mogą być przydatne w następujących scenariuszach:

- W wyrażeniach z [operatorów warunkowych działających z wartością null?. i ?[]](member-access-operators.md#null-conditional-operators--and-), można używać operatora łączenia wartości null zapewnienie alternatywnych wyrażenie do oceny, w przypadku, gdy jest wynikiem wyrażenia warunkowe null operacji `null`:

  [!code-csharp-interactive[with null-conditional](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullConditional)]

- Podczas pracy z [typami wartości null](../../programming-guide/nullable-types/index.md) i musi podać wartość bazowego typu wartości, użyj operatora łączenia wartości null, aby określić wartość, która ma zostać podana w przypadku, gdy wartość typu Nullable to `null`:

  [!code-csharp-interactive[with nullable types](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithNullableTypes)]

  Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , jeśli wartość, która ma zostać użyta, gdy wartość typu `null` dopuszczająca wartości null ma być wartością domyślną dla bazowego typu wartości.

- Począwszy od C# 7,0, można użyć [ `throw` wyrażenia](../keywords/throw.md#the-throw-expression) jako argumentu operacji po prawej stronie operatora łączenia wartości null, aby kod sprawdzania argumentów był bardziej zwięzły:

  [!code-csharp[with throw expression](~/samples/csharp/language-reference/operators/NullCoalescingOperator.cs#WithThrowExpression)]

  W powyższym przykładzie pokazano również, jak używać [składowych wyrażeń](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) w celu zdefiniowania właściwości.

- Począwszy od C# 8,0, można użyć operatora, `??=` aby zamienić kod formularza

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

Operatory `??` i`??=` nie mogą być przeciążone.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji na `??` temat operatora, zobacz sekcję [operator łączenia null](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [?. i ?[] Operatory](member-access-operators.md#null-conditional-operators--and-)
- [?: — operator](conditional-operator.md)
