---
title: Korzystanie z typów wartości null C# — Przewodnik programowania
ms.custom: seodec18
description: Dowiedz się, jak C# korzystać z typów wartości null
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396164"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>Używanie typów wartości null (C# Przewodnik programowania)

Typy wartości null są typami, które reprezentują wszystkie wartości bazowego typu wartości `T` i dodatkową wartość [null](../../language-reference/keywords/null.md) . Aby uzyskać więcej informacji, zobacz temat [typy wartości null](index.md) .

> [!NOTE]
> C#8,0 wprowadza funkcję typów odwołań do wartości null. Aby uzyskać więcej informacji, zobacz [typy referencyjne dopuszczające wartość null](../../nullable-references.md). Typy wartości null są dostępne od C# 2.

Można odwołać się do typu wartości null w dowolnej z następujących metod zamiennych: `Nullable<T>` lub `T?`. `T` musi być typem wartości.

## <a name="declaration-and-assignment"></a>Deklaracja i przypisanie

Ponieważ typ wartości może być niejawnie konwertowany do odpowiadającego typu wartości null, przypisujesz wartość do typu dopuszczającego wartości null jak dla jego bazowego typu wartości. Można również przypisać wartość `null`. Na przykład:

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Badanie wartości typu dopuszczającego wartość null

Użyj następujących właściwości tylko do odczytu w celu sprawdzenia wystąpienia typu wartości null dla wartości null i pobrania wartości typu podstawowego:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, właściwość <xref:System.Nullable%601.Value%2A> zgłasza <xref:System.InvalidOperationException>.

W poniższym przykładzie kod używa właściwości `HasValue` do sprawdzenia, czy zmienna zawiera wartość przed wyświetleniem:

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

Można także porównać zmienną typu wartości null z `null` zamiast używać właściwości `HasValue`, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Począwszy od C# 7,0, można użyć [dopasowania wzorca](../../pattern-matching.md) do obu badań i pobrać wartość typu wartości null:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Konwersja z typu wartości null na typ podstawowy

Jeśli musisz przypisać wartość typu wartości null do typu, który nie dopuszcza wartości null, użyj [operatora łączenia wartości null `??`](../../language-reference/operators/null-coalescing-operator.md) , aby określić wartość, która ma zostać przypisana, jeśli wartość typu wartości null jest równa null (można również użyć metody <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>, aby to zrobić) :

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, jeśli wartość, która ma zostać użyta, gdy wartość typu wartości null jest `null` powinna być wartością domyślną bazowego typu wartości.

Można jawnie rzutować typ wartości null na typ, który nie dopuszcza wartości null. Na przykład:

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

W czasie wykonywania, jeśli wartość typu wartości null jest `null`, jawne rzutowanie zgłasza <xref:System.InvalidOperationException>.

Typ wartości niedopuszczający wartości null jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.

## <a name="operators"></a>Operatory

Wstępnie zdefiniowane operatory jednoargumentowe i binarne oraz wszelkie Operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą również być używane przez odpowiednie typy dopuszczające wartość null. Te operatory generują `null`, jeśli jeden lub oba operandy są `null`; w przeciwnym razie operator używa zawartych wartości, aby obliczyć wynik. Na przykład:

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> W przypadku typu `bool?` wstępnie zdefiniowane operatory `&` i `|` nie przestrzegają reguł opisanych w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów jest `null`. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../../language-reference/operators/boolean-logical-operators.md) .
  
Dla operatorów relacyjnych (`<`, `>`, `<=`, `>=`), jeśli jeden lub oba operandy są `null`, wynik jest `false`. Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, przeciwieństwo porównania (`>`) zwraca `true`. Poniższy przykład pokazuje, że 10 jest

- nie większe niż ani równe `null`,
- nie mniej niż `null`.

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

Powyższy przykład pokazuje również, że porównanie równości dwóch typów wartości null, które mają wartość null, jest równe `true`.

Aby uzyskać więcej informacji, zobacz sekcję [zniesione operatory](~/_csharplang/spec/expressions.md#lifted-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Pakowanie i rozpakowywanie

Typ wartości null jest [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:

- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, tworzone jest odwołanie o wartości null.
- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, wartość bazowego typu wartości `T` jest opakowany, a nie wystąpieniem <xref:System.Nullable%601>.

Można Unbox opakowany typ wartości do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Zobacz także

- [Typy wartości null](index.md)
- [Co dokładnie ma znaczenie "zniesione"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
