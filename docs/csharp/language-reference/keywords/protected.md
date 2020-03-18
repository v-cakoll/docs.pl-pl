---
title: chronione słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713186"
---
# <a name="protected-c-reference"></a>protected (odwołanie w C#)

Słowo `protected` kluczowe jest modyfikatorem dostępu do elementów członkowskich.

 > Ta strona `protected` obejmuje dostęp. Słowo `protected` kluczowe jest również [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) częścią modyfikatorów i dostępu.

Chroniony element członkowski jest dostępny w jego klasie i przez wystąpienia klasy pochodnej.

Aby porównać `protected` inne modyfikatory dostępu, zobacz [Poziomy ułatwień dostępu](accessibility-levels.md).

## <a name="example"></a>Przykład

Chroniony element członkowski klasy podstawowej jest dostępny w klasie pochodnej tylko wtedy, gdy dostęp występuje za pośrednictwem typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Instrukcja `a.x = 10` generuje błąd, ponieważ jest wykonany w ramach metody statycznej Main, a nie wystąpienie klasy B.

Elementy członkowskie struktury nie mogą być chronione, ponieważ struktura nie może być dziedziczona.

## <a name="example"></a>Przykład

W tym przykładzie `DerivedPoint` klasa pochodzi `Point`od . W związku z tym można uzyskać dostęp do chronionych elementów członkowskich klasy podstawowej bezpośrednio z klasy pochodnej.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Jeśli zmienisz poziomy `x` dostępu `y` i [prywatne,](private.md)kompilator wyda komunikaty o błędach:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [Publicznego](public.md)
- [Prywatny](private.md)
- [Wewnętrznego](internal.md)
- [Obawy dotyczące zabezpieczeń wewnętrznych wirtualnych słów kluczowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
