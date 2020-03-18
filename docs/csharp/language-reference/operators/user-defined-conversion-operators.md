---
title: Operatory konwersji zdefiniowane przez użytkownika — odwołanie do języka C#
description: Dowiedz się, jak zdefiniować niestandardowe konwersje typów niejawnych i jawnych w języku C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b6061492cc1a4f756196fb8a9050b68651431e38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847273"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operatory konwersji zdefiniowane przez użytkownika (odwołanie do języka C#)

Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe niejawne konwersji lub jawne z lub do innego typu.

Konwersje niejawne nie wymagają specjalnej składni do wywołania i mogą występować w różnych sytuacjach, na przykład w przypisaniach i wywołaniach metod. Wstępnie zdefiniowane konwersje niejawne C# zawsze się powiedzie i nigdy nie zgłaszać wyjątek. Konwersje niejawne zdefiniowane przez użytkownika powinny również zachowywać się w ten sposób. Jeśli konwersja niestandardowa może zgłosić wyjątek lub utracić informacje, zdefiniuj je jako jawną konwersję.

Konwersje zdefiniowane przez użytkownika nie są brane pod uwagę przez [is](type-testing-and-cast.md#is-operator) i [jako](type-testing-and-cast.md#as-operator) operatory. Użyj [operatora rzutowania ()](type-testing-and-cast.md#cast-operator-) do wywołania konwersji jawnej zdefiniowanej przez użytkownika.

Użyj `operator` i `implicit` `explicit` lub słowa kluczowego, aby zdefiniować konwersję niejawną lub jawną, odpowiednio. Typ definiujący konwersję musi być typem źródłowym lub docelowym tej konwersji. Konwersję między dwoma typami zdefiniowanymi przez użytkownika można zdefiniować w jednym z dwóch typów.

W poniższym przykładzie pokazano, jak zdefiniować konwersję niejawną i jawną:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Słowo `operator` kluczowe służy również do przeciążenia wstępnie zdefiniowanego operatora Języka C#. Aby uzyskać więcej informacji, zobacz [Przeciążenie operatora](operator-overloading.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Operatory konwersji](~/_csharplang/spec/classes.md#conversion-operators)
- [Konwersje zdefiniowane przez użytkownika](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Konwersje niejawne](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Jawne konwersje](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Przeciążenie operatora](operator-overloading.md)
- [Operatory testowania typu i rzutowania](type-testing-and-cast.md)
- [Casting i konwersja typu](../../programming-guide/types/casting-and-type-conversions.md)
- [Wytyczne projektowe - Operatorzy konwersji](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Konwersje jawne zdefiniowane przez użytkownika w łańcuchu w C #](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
