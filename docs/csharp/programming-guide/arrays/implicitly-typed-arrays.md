---
title: Tablice niejawnie wpisane — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705720"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Niejawnie wpisane tablice (Przewodnik programowania w języku C#)

Można utworzyć tablicę niejawnie wpisaną, w której typ wystąpienia tablicy jest wywnioskowany z elementów określonych w inicjatorze tablicy. Reguły dla dowolnej zmiennej niejawnie wpisane stosuje się również do tablic niejawnie wpisane. Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../classes-and-structs/implicitly-typed-local-variables.md).

Tablice niejawnie typu są zwykle używane w wyrażeniach kwerend y wraz z typami anonimowymi oraz inicjazatory obiektów i kolekcji.

W poniższych przykładach przedstawiono sposób tworzenia tablicy wpisanej niejawnie:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

W poprzednim przykładzie należy zauważyć, że z tablic wpisanych niejawnie, nawiasy kwadratowe są używane po lewej stronie instrukcji inicjowania. Należy również zauważyć, że postrzępione `new []` tablice są inicjowane przy użyciu takich jak tablice jednowymiarowe.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Tablice wpisane niejawnie w inicjatorach obiektów

Podczas tworzenia typu anonimowego, który zawiera tablicę, tablica musi być niejawnie wpisany w inicjatorze obiektu typu. W poniższym `contacts` przykładzie jest niejawnie wpisany tablicy typów anonimowych, `PhoneNumbers`z których każdy zawiera tablicę o nazwie . Należy zauważyć, że `var` słowo kluczowe nie jest używany wewnątrz inicjatorów obiektów.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Jawnie wpisana zmienna lokalna](../classes-and-structs/implicitly-typed-local-variables.md)
- [Tablice](./index.md)
- [Typy anonimowe](../classes-and-structs/anonymous-types.md)
- [Inicjatory obiektów i kolekcji](../classes-and-structs/object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ w C#](../../linq/index.md)
