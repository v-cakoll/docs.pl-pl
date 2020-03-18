---
title: ?? I?? = operatory - odwołanie c#
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
ms.openlocfilehash: 69294f0fb706868b48b8d7fe8b95fa345af169b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847316"
---
# <a name="-and--operators-c-reference"></a>?? I?? = operatory (odwołanie do Języka C#)

Operator `??` null-łączenie zwraca wartość jego operand po lewej stronie, jeśli `null`nie jest ; w przeciwnym razie ocenia argument po prawej stronie i zwraca jego wynik. Operator `??` nie ocenia jego prawostronny operand, jeśli po lewej stronie operand ocenia non-null.

Dostępne w języku C# 8.0 i nowszych `??=` operator przypisania null-łączenie przypisuje wartość jego operand po prawej stronie do jego operand po lewej stronie tylko wtedy, gdy po lewej stronie operand ocenia . `null` Operator `??=` nie ocenia jego prawostronny operand, jeśli po lewej stronie operand ocenia non-null.

[!code-csharp[null-coalescing assignment](snippets/NullCoalescingOperator.cs#Assignment)]

Operand po lewej stronie `??=` operatora musi być zmienną, [właściwością](../../programming-guide/classes-and-structs/properties.md)lub elementem [indeksatora.](../../programming-guide/indexers/index.md)

W języku C# 7.3 i wcześniejszych typ operandu po lewej stronie `??` operatora musi być [typem odwołania](../keywords/reference-types.md) lub [typem wartości nullable](../builtin-types/nullable-value-types.md). Począwszy od Języka C# 8.0, to wymaganie jest zastępowane następującymi: typ operand po lewej stronie `??` i `??=` operatorów nie może być typem wartości niedopuszczająca wartości. W szczególności, począwszy od Języka C# 8.0, można użyć null-łączenie operatorów z nieograniczonymi parametrami typu:

[!code-csharp[unconstrained type parameter](snippets/NullCoalescingOperator.cs#UnconstrainedType)]

Operatory null-łączenia są zasocjałe. Oznacza to, że wyrażenia formy

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

`??` Operatory `??=` i mogą być przydatne w następujących scenariuszach:

- W wyrażeniach z [operatorami warunkowymi zerowymi ?. i ?[]](member-access-operators.md#null-conditional-operators--and-)można użyć `??` operatora, aby zapewnić wyrażenie alternatywne `null`do oceny w przypadku, gdy wynik wyrażenia z operacjami warunkowymi zerowymi jest:

  [!code-csharp-interactive[with null-conditional](snippets/NullCoalescingOperator.cs#WithNullConditional)]

- Podczas pracy z [typami wartości nullable](../builtin-types/nullable-value-types.md) i trzeba podać wartość podstawowego typu wartości, należy użyć `??` operatora, aby `null`określić wartość, aby podać w przypadku wartości typu nullable jest:

  [!code-csharp-interactive[with nullable types](snippets/NullCoalescingOperator.cs#WithNullableTypes)]

  Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metody, jeśli wartość, która ma być `null` używana, gdy wartość typu nulljest powinna być wartością domyślną podstawowego typu wartości.

- Począwszy od języka C# 7.0, można użyć [ `throw` wyrażenia](../keywords/throw.md#the-throw-expression) jako `??` operand po prawej stronie operatora, aby kod sprawdzania argumentów bardziej zwięzły:

  [!code-csharp[with throw expression](snippets/NullCoalescingOperator.cs#WithThrowExpression)]

  W poprzednim przykładzie pokazano również, jak używać [elementów członkowskich zabudowanych wyrażeniem](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) do definiowania właściwości.

- Począwszy od języka C# 8.0, można użyć `??=` operatora, aby zastąpić kod formularza

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  z następującym kodem:

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a>Przeciążenie operatora

Operatory `??` `??=` i nie mogą być przeciążone.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej `??` informacji na temat operatora, zobacz [null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

Aby uzyskać więcej `??=` informacji na temat operatora, zobacz [notę propozycji funkcji](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [?. I? [] operatorzy](member-access-operators.md#null-conditional-operators--and-)
- [?: operator](conditional-operator.md)
