---
title: Korzystanie z typów dopuszczających wartość null — C# Przewodnik programowania
ms.custom: seodec18
description: Dowiedz się, jak C# korzystać z typów dopuszczających wartość null
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588833"
---
# <a name="using-nullable-types-c-programming-guide"></a>Korzystanie z typów dopuszczających wartość null (C# Przewodnik programowania)

Typy dopuszczające wartości null to typy reprezentujące wszystkie wartości bazowego typu `T`wartości oraz dodatkową wartość [null](../../language-reference/keywords/null.md) . Aby uzyskać więcej informacji, zobacz temat [Typy dopuszczające wartość null](index.md) .

Można odwołać się do typu dopuszczającego wartość null w dowolnej z `Nullable<T>` następujących `T?`form: lub. Te dwa formularze są zamienne.  
  
## <a name="declaration-and-assignment"></a>Deklaracja i przypisanie

Jako typ wartości można niejawnie skonwertować do odpowiadającego typu dopuszczającego wartość null, można przypisać wartości do typu dopuszczającego wartość null jak dla jego bazowego typu wartości. Możesz również przypisać `null` wartość.  Na przykład:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Badanie wartości typu dopuszczającego wartość null

Użyj następujących właściwości tylko do odczytu, aby przeanalizować wystąpienie typu dopuszczającego wartość null w celu wyzerowania i pobrać wartość typu podstawowego:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>wskazuje, czy wystąpienie typu wartości null ma wartość jego typu podstawowego.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>Pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest. `true` Jeśli <xref:System.Nullable%601.HasValue%2A> ma `false`wartość ,<xref:System.Nullable%601.Value%2A>Właściwość zgłasza .<xref:System.InvalidOperationException>
  
Kod w poniższym przykładzie używa właściwości, `HasValue` aby sprawdzić, czy zmienna zawiera wartość przed wyświetleniem:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Możesz również porównać zmienną typu Nullable z `null` zamiast `HasValue` używać właściwości, jak pokazano w poniższym przykładzie:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Począwszy od C# 7,0, można użyć [dopasowania wzorca](../../pattern-matching.md) do obu badań i pobrać wartość typu dopuszczającego wartości null:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Konwersja z typu dopuszczającego wartość null na typ podstawowy

Jeśli musisz przypisać wartość typu null do typu niedopuszczający wartości null, użyj [operatora `??` łączenia wartości null](../../language-reference/operators/null-coalescing-operator.md) , aby określić wartość, która ma zostać przypisana, jeśli wartość typu null jest równa null (można <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> również użyć metody, aby to zrobić):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Użyj metody <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , jeśli wartość, która ma zostać użyta, gdy wartość typu null jest równa null powinna być wartością domyślną bazowego typu wartości.
  
Typ dopuszczający wartość null można jawnie rzutować na typ, który nie dopuszcza wartości null. Na przykład:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

W czasie wykonywania, jeśli wartość typu Nullable ma wartość null, jawne rzutowanie zgłosi <xref:System.InvalidOperationException>.

Typ wartości niedopuszczający wartości null jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.
  
## <a name="operators"></a>Operatory

Wstępnie zdefiniowane operatory jednoargumentowe i binarne oraz wszelkie Operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą być również używane przez Typy dopuszczające wartość null. Te operatory tworzą wartość null, jeśli jeden lub oba operandy mają wartość null; w przeciwnym razie operator używa zawartych wartości, aby obliczyć wynik. Na przykład:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Dla typu, wstępnie zdefiniowane `&` operatory i `|` nie przestrzegają zasad opisanych w tej sekcji: wynik oceny operatora może być inny niż null, nawet jeśli jeden z operandów ma wartość null. `bool?` Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne wartości null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) w artykule [Operatory logiczne Boolean](../../language-reference/operators/boolean-logical-operators.md) .
  
W przypadku operatorów relacyjnych`<`( `>`, `<=`, `>=`,), jeśli jeden lub oba operandy mają wartość null, wynik `false`to. Nie należy zakładać, że ponieważ określone porównanie (na przykład `<=`) zwraca `false`, odwrotne porównanie (`>`) zwraca `true`wartość. Poniższy przykład pokazuje, że 10 jest

- nie może być większa niż lub równa null,
- ani mniejsze od wartości null.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Powyższy przykład pokazuje również, że porównanie równości dwóch typów dopuszczających wartości null, które są równe zero `true`.

Aby uzyskać więcej informacji, zobacz sekcję [zniesione operatory](~/_csharplang/spec/expressions.md#lifted-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Pakowanie i rozpakowywanie

Typ wartości null jest [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:

- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca`false`, zostanie utworzone odwołanie o wartości null.  
- Jeśli <xref:System.Nullable%601.HasValue%2A> `T` <xref:System.Nullable%601>zwraca `true`, wartość bazowego typu wartości jest opakowana, a nie wystąpieniem.

Można Unbox opakowany typ wartości do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Zobacz także

- [Typy dopuszczające wartości null](index.md)
- [Przewodnik programowania w języku C#](../index.md)
- [Co dokładnie ma znaczenie "zniesione"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
