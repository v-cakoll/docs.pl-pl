---
title: chronione słowo kluczowe C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713186"
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)

Słowo kluczowe `protected` jest modyfikatorem dostępu składowej.

 > Ta strona obejmuje `protected` dostępu. Słowo kluczowe `protected` jest również częścią modyfikatorów dostępu [`protected internal`](protected-internal.md) i [`private protected`](private-protected.md) .

Chroniony element członkowski jest dostępny w jego klasie i wystąpieniach klasy pochodnej.

Aby uzyskać porównanie `protected` z innymi modyfikatorami dostępu, zobacz [poziomy dostępności](accessibility-levels.md).

## <a name="example"></a>Przykład

Chroniony element członkowski klasy bazowej jest dostępny w klasie pochodnej tylko wtedy, gdy dostęp odbywa się za pomocą typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Instrukcja `a.x = 10` generuje błąd, ponieważ znajduje się w metodzie statycznej Main i nie jest wystąpieniem klasy B.

Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.

## <a name="example"></a>Przykład

W tym przykładzie Klasa `DerivedPoint` pochodzi od `Point`. W związku z tym można uzyskać dostęp do chronionych elementów członkowskich klasy bazowej bezpośrednio z klasy pochodnej.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

W przypadku zmiany poziomów dostępu `x` i `y` na [prywatne](private.md), kompilator będzie wystawiał komunikaty o błędach:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Zagadnienia dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
