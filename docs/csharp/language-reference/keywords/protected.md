---
title: Protected — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 6e3f72226d10910152f7a2139a5a1be35e681ec7
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50183181"
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)

`protected` — Słowo kluczowe jest modyfikator dostępu składowej.

 > Ta strona obejmuje `protected` dostępu. `protected` — Słowo kluczowe jest również częścią [ `protected internal` ](protected-internal.md) i [ `private protected` ](private-protected.md) modyfikatorach dostępu.

Chroniony element członkowski jest dostępny w ramach swojej klasy i wystąpienia klasy pochodnej.

Porównanie `protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](accessibility-levels.md).

## <a name="example"></a>Przykład

Chronione elementy członkowskie klasy bazowej jest dostępna w klasie pochodnej, tylko wtedy, gdy dostęp odbywa się przez typ klasy pochodnej. Na przykład rozważmy następujący segment kodu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Wykonywanie instrukcji `a.x = 10` generuje błąd, ponieważ staje się wewnątrz metody statycznej Main, a nie jest wystąpieniem klasy B.

Składowe struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.

## <a name="example"></a>Przykład

W tym przykładzie klasa `DerivedPoint` jest tworzony na podstawie `Point`. W związku z tym dostęp chronionych elementów członkowskich klasy podstawowej, bezpośrednio z klasy pochodnej.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Jeśli zmienisz poziomy dostępu `x` i `y` do [prywatnej](private.md), kompilator zgłosi komunikaty o błędach:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Kwestie bezpieczeństwa wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))