---
title: Operatory konwersji zdefiniowane przez użytkownika — C# odwołania
description: Dowiedz się, jak zdefiniować niestandardowe jawne i niejawne konwersje plików w C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67788499"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operatory konwersji zdefiniowane przez użytkownika (C# odwołania)

Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe jawnych lub niejawnych konwersji z lub do innego typu.

Niejawne konwersje nie wymagają specjalnej składni wywoływanej i mogą występować w wielu sytuacjach, na przykład w wywołania zadania i metody. Wstępnie zdefiniowane C# niejawne konwersje zawsze powiedzie się i nigdy nie zgłoszą wyjątek lub utratę informacji. Niejawne konwersje zdefiniowane przez użytkownika, powinny zachowywać się w ten sposób, jak również. Jeśli konwersja niestandardowych mogą zgłosić wyjątek lub utratę informacji, zdefiniuj je jako jawnej konwersji.

Konwersje zdefiniowane przez użytkownika nie są uwzględniane przy [jest](type-testing-and-conversion-operators.md#is-operator) i [jako](type-testing-and-conversion-operators.md#as-operator) operatorów. Użyj [rzutowania (operatora)](type-testing-and-conversion-operators.md#cast-operator-) do wywoływania jawnej konwersji zdefiniowanych przez użytkownika.

Użyj `operator` i `implicit` lub `explicit` słów kluczowych, aby zdefiniować jawnych lub niejawnych konwersji, odpowiednio. Typ, który definiuje konwersja musi być typ źródła lub elementu docelowego typu tej konwersji. Konwersja między dwoma typami zdefiniowanych przez użytkownika można zdefiniować w jednym z dwóch typów.

Poniższy przykład pokazuje jak zdefiniować niejawne i jawne konwersji:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Możesz także użyć `operator` — słowo kluczowe próby przeciążania wstępnie zdefiniowanej C# operatora. Aby uzyskać więcej informacji, zobacz [przeciążania operatora](operator-overloading.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operatory konwersji](~/_csharplang/spec/classes.md#conversion-operators)
- [Konwersje zdefiniowane przez użytkownika](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Niejawne konwersje](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Przeładowanie operatora](operator-overloading.md)
- [Operatory badania typu i konwersji](type-testing-and-conversion-operators.md)
- [Rzutowanie i typ konwersji](../../programming-guide/types/casting-and-type-conversions.md)
- [Tworzenie łańcucha zdefiniowanych przez użytkownika Konwersje jawne w języku C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
