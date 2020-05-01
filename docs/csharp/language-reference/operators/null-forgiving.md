---
title: '! operator (null-łagodniejszej) — odwołanie w C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 2a8db2882968dbcbe6a8868ab6fe1c128c94a41f
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624881"
---
# <a name="-null-forgiving-operator-c-reference"></a>! (null-łagodniejszej) — operator (odwołanie w C#)

Dostępne w języku C# 8,0 i nowszych, jednoargumentowy operator przyrostkowy `!` jest operatorem łagodniejszej o wartości null. W włączonym [kontekście dopuszczającym wartość null](../../nullable-references.md#nullable-annotation-context)należy użyć operatora null-łagodniejszej, aby zadeklarować wyrażenie `x` typu referencyjnego `null`nie `x!`jest:. Jednoargumentowy `!` operator prefiksu jest [logicznym operatorem negacji](boolean-logical-operators.md#logical-negation-operator-).

Operator null-łagodniejszej nie ma wpływu w czasie wykonywania. Ma wpływ tylko na analizę przepływu statycznego kompilatora przez zmianę stanu null wyrażenia. W czasie wykonywania wyrażenie `x!` oblicza wynik wyrażenia `x`bazowego.

> [!NOTE]
> W języku C# 8 operator łagodniejszej o wartości null kończy listę poprzednich operacji [warunkowych o wartości null](member-access-operators.md#null-conditional-operators--and-) . Na przykład wyrażenie `x?.y!.z` jest analizowane jako `(x?.y)!.z`. Ze względu na tę `z` interpretację, jest `x` oceniane `null`, nawet jeśli jest, co <xref:System.NullReferenceException>może skutkować.

Aby uzyskać więcej informacji na temat funkcji typów referencyjnych dopuszczających wartość null, zobacz [typy referencyjne dopuszczające wartość null](../builtin-types/nullable-reference-types.md).

## <a name="examples"></a>Przykłady

Jednym z przypadków użycia operatora null-łagodniejszej jest Testowanie logiki walidacji argumentów. Rozważmy na przykład następujące klasy:

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

Używając [platformy testów MSTest](../../../core/testing/unit-testing-with-mstest.md), można utworzyć następujący test dla logiki walidacji w konstruktorze:

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla poprzedniego kodu: `Warning CS8625: Cannot convert null literal to non-nullable reference type`. Za pomocą operatora null-łagodniejszej, należy poinformować kompilator, że oczekiwano `null` , i nie powinien być ostrzegany o.

Można również użyć operatora o wartości null-łagodniejszej, gdy wiadomo, że wyrażenie nie może być `null` , ale kompilator nie rozpoznaje tego elementu. W poniższym przykładzie, jeśli metoda zwraca `IsValid` `true`, jego argument nie `null` jest i można bezpiecznie odwoływać się do niego:

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

Bez operatora null łagodniejszej kompilator generuje następujące ostrzeżenie dla `p.Name` kodu:. `Warning CS8602: Dereference of a possibly null reference`

`IsValid` Jeśli można zmodyfikować metodę, można użyć atrybutu [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) do informowania kompilatora, że `IsValid` argument metody nie może być `null` , gdy metoda zwraca: `true`

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

W poprzednim przykładzie nie trzeba używać operatora o wartości null-łagodniejszej, ponieważ kompilator ma wystarczającą ilość informacji, aby dowiedzieć się, `p` że nie `null` może znajdować się wewnątrz `if` instrukcji. Aby uzyskać więcej informacji o atrybutach, które umożliwiają podanie dodatkowych informacji o stanie null zmiennej, zobacz [uaktualnianie interfejsów API z atrybutami w celu zdefiniowania oczekiwań o wartości null](../attributes/nullable-analysis.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [operator null-łagodniejszej](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) w [wersji roboczej specyfikacji typów odwołań dopuszczających wartość null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Samouczek: Projektowanie przy użyciu typów referencyjnych dopuszczających wartość null](../../tutorials/nullable-reference-types.md)
