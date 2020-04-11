---
title: Operatory konwersji zdefiniowane przez użytkownika — odwołanie do języka C#
description: Dowiedz się, jak zdefiniować niestandardowe konwersje typu niejawnego i jawnego w języku C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: b59fc27be31f1a38e2a6c3cabd82598933b5ed53
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121406"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operatory konwersji zdefiniowane przez użytkownika (odwołanie do języka C#)

Typ zdefiniowany przez użytkownika można zdefiniować niestandardowe niejawne lub jawne konwersji z lub do innego typu.

Konwersje niejawne nie wymagają specjalnej składni do wywoływania i mogą wystąpić w różnych sytuacjach, na przykład w przypisaniach i wywołaniach metod. Wstępnie zdefiniowane konwersje niejawne języka C# zawsze powiedzie się i nigdy nie zgłaszają wyjątku. Konwersje niejawne zdefiniowane przez użytkownika powinny zachowywać się również w ten sposób. Jeśli konwersja niestandardowa może zgłosić wyjątek lub utracić informacje, zdefiniuj ją jako konwersję jawną.

Konwersje zdefiniowane przez użytkownika nie są uwzględniane przez [operatorów is](type-testing-and-cast.md#is-operator) i [as.](type-testing-and-cast.md#as-operator) Użyj [wyrażenia rzutowego,](type-testing-and-cast.md#cast-expression) aby wywołać konwersję jawną zdefiniowaną przez użytkownika.

Użyj `operator` i `implicit` `explicit` lub słowa kluczowe, aby zdefiniować konwersji niejawnej lub jawnej, odpowiednio. Typ definiujący konwersję musi być typem źródłowym lub typem docelowym tej konwersji. Konwersja między dwoma typami zdefiniowanymi przez użytkownika może być zdefiniowana w jednym z dwóch typów.

W poniższym przykładzie pokazano, jak zdefiniować konwersję niejawną i jawną:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Służy również `operator` słowo kluczowe przeciążenie wstępnie zdefiniowanego operatora języka C#. Aby uzyskać więcej informacji, zobacz [Przeciążanie operatora](operator-overloading.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka języka C#:](~/_csharplang/spec/introduction.md)

- [Operatory konwersji](~/_csharplang/spec/classes.md#conversion-operators)
- [Konwersje zdefiniowane przez użytkownika](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Konwersje niejawne](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Przeładowanie operatora](operator-overloading.md)
- [Operatory testowania typu i rzutowania](type-testing-and-cast.md)
- [Odlewanie i konwersja typu](../../programming-guide/types/casting-and-type-conversions.md)
- [Wytyczne dotyczące projektowania — operatory konwersji](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Konwersje jawne zdefiniowane przez użytkownika w łańcuchu w języku C #](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
