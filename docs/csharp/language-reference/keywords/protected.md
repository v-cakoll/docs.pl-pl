---
title: chronione słowo kluczowe C# — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a0420dd10d81c4ae893ab0447244a611091ed7b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601975"
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)

`protected` Słowo kluczowe jest modyfikatorem dostępu składowej.

 > Ta strona dotyczy `protected` dostępu. Słowo kluczowe jest również częścią [`protected internal`](protected-internal.md) modyfikatorów [`private protected`](private-protected.md) i dostępu. `protected`

Chroniony element członkowski jest dostępny w jego klasie i wystąpieniach klasy pochodnej.

Aby uzyskać porównanie `protected` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).

## <a name="example"></a>Przykład

Chroniony element członkowski klasy bazowej jest dostępny w klasie pochodnej tylko wtedy, gdy dostęp odbywa się za pomocą typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Instrukcja `a.x = 10` generuje błąd, ponieważ znajduje się w metodzie statycznej Main i nie jest wystąpieniem klasy B.

Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.

## <a name="example"></a>Przykład

W tym przykładzie Klasa `DerivedPoint` pochodzi od. `Point` W związku z tym można uzyskać dostęp do chronionych elementów członkowskich klasy bazowej bezpośrednio z klasy pochodnej.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Jeśli zmienisz poziomy `x` dostępu dla i `y` na [prywatne](private.md), kompilator będzie wystawiał komunikaty o błędach:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
