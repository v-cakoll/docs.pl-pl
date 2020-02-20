---
title: Operatory konwersji zdefiniowane przez użytkownika — C# odwołanie
description: Dowiedz się, jak definiować niestandardowe niejawne i C#jawne konwersje typów w.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 379deb20243a13cc608cb7fe119b341065327c1e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450677"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operatory konwersji zdefiniowane przez użytkownika (C# odwołanie)

Typ zdefiniowany przez użytkownika może definiować niestandardową lub niejawną konwersję z lub do innego typu.

Konwersje niejawne nie wymagają wywoływania specjalnej składni i mogą wystąpić w różnych sytuacjach, na przykład w przypisaniach i metodach wywołania. Wstępnie C# zdefiniowane konwersje niejawne zawsze kończą się powodzeniem i nigdy nie generują wyjątku. Niejawne konwersje zdefiniowane przez użytkownika powinny również działać w ten sposób. Jeśli niestandardowa konwersja może zgłosić wyjątek lub utracić informacje, zdefiniuj ją jako konwersję jawną.

Konwersje zdefiniowane przez użytkownika nie są uwzględniane przez operatory [is](type-testing-and-cast.md#is-operator) i [as](type-testing-and-cast.md#as-operator) . Użyj [operatora CAST ()](type-testing-and-cast.md#cast-operator-) do wywołania jawnej konwersji zdefiniowanej przez użytkownika.

Użyj słów kluczowych `operator` i `implicit` lub `explicit`, aby zdefiniować odpowiednio niejawną lub jawną konwersję. Typ, który definiuje konwersję, musi być typem źródłowym lub typem docelowym tej konwersji. Konwersję między dwoma typami zdefiniowanymi przez użytkownika można zdefiniować w jeden z dwóch typów.

Poniższy przykład ilustruje sposób definiowania konwersji niejawnej i jawnej:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Możesz również użyć słowa kluczowego `operator` do przeciążenia wstępnie C# zdefiniowanego operatora. Aby uzyskać więcej informacji, zobacz [przeciążanie operatora](operator-overloading.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operatory konwersji](~/_csharplang/spec/classes.md#conversion-operators)
- [Konwersje zdefiniowane przez użytkownika](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Konwersje niejawne](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Konwersje jawne](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Przeciążanie operatora](operator-overloading.md)
- [Operatory testowania typu i rzutowania](type-testing-and-cast.md)
- [Rzutowanie i Konwersja typów](../../programming-guide/types/casting-and-type-conversions.md)
- [Wytyczne dotyczące projektowania — operatory konwersji](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Jawne konwersje zdefiniowane przez użytkownika wC#](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
