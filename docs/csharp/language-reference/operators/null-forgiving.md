---
title: '! (null-łagodniejszej) — C# odwołanie'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291726"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-łagodniejszej) — operatorC# (odwołanie)

Dostępne w C# 8,0 i nowszych operatory jednoargumentowe `!` jest operatorem null-łagodniejszej. W kontekście włączonego [dopuszczającego wartość](../../nullable-references.md#nullable-annotation-context)null należy użyć operatora null-łagodniejszej, aby zadeklarować, że wyrażenie `x` typu referencyjnego nie ma wartości null: `x!`. Prefiks jednoargumentowy `!` operator jest [logicznym operatorem negacji](boolean-logical-operators.md#logical-negation-operator-).

Operator null-łagodniejszej nie ma wpływu w czasie wykonywania. Ma wpływ tylko na analizę przepływu statycznego kompilatora przez zmianę stanu null wyrażenia. W czasie wykonywania wyrażenie `x!` szacuje wynik wyrażenia bazowego `x`.

Aby uzyskać więcej informacji na temat funkcji typów referencyjnych dopuszczających wartość null, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md).

## <a name="examples"></a>Przykłady

Jednym z przypadków użycia operatora null-łagodniejszej jest Testowanie logiki walidacji argumentów. Rozważmy na przykład następujące klasy:

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

Używając [platformy testów MSTest](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki walidacji w konstruktorze:

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla poprzedniego kodu: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Korzystając z operatora łagodniejszej o wartości null, można poinformować kompilator, że oczekiwane jest przekazywanie `null` i nie powinno być ostrzegane o.

Można również użyć operatora o wartości null-łagodniejszej, gdy wiadomo, że wyrażenie nie może być `null`, ale kompilator nie rozpoznaje tego. W poniższym przykładzie, jeśli metoda `IsValid` zwróci `true`, jego argument nie jest `null` i można bezpiecznie go wywoływać:

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla kodu `p.Name`: `Warning CS8602: Dereference of a possibly null reference.`.

Jeśli można zmodyfikować metodę `IsValid`, można użyć atrybutu [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) , aby dać kompilatorowi, że argument metody `IsValid` nie może być `null`, gdy metoda zwraca `true`:

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

W poprzednim przykładzie nie trzeba używać operatora łagodniejszej o wartości null, ponieważ kompilator ma wystarczającą ilość informacji, aby dowiedzieć się, że `p` nie może być `null` w instrukcji `if`. Aby uzyskać więcej informacji o atrybutach, które umożliwiają określenie dodatkowych informacji o stanie null zmiennej, zobacz [uaktualnianie interfejsów API z atrybutami w celu zdefiniowania oczekiwań o wartości null](../../nullable-attributes.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [C#zainteresowanych](index.md)
- [Samouczek: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null](../../tutorials/nullable-reference-types.md)
