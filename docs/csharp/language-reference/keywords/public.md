---
title: Public — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: b2e09bdb16d6128d69a3eb33cf2cffd4cba60376
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43518189"
---
# <a name="public-c-reference"></a>public (odwołanie w C#)

`public` — Słowo kluczowe jest modyfikatorem dostępu dla typów i elementów członkowskich typu. Dostęp publiczny jest restrykcyjny poziom dostępu. Istnieją ograniczenia związane z dostępem do publicznych składowych, jak w poniższym przykładzie:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Zobacz [modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomów ułatwień dostępu](accessibility-levels.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

W poniższym przykładzie zadeklarowano dwóch klas, `PointTest` i `MainClass`. Publiczne elementy członkowskie `x` i `y` z `PointTest` są dostępne bezpośrednio z `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Jeśli zmienisz `public` poziom dostępu do [prywatnej](private.md) lub [chronione](protected.md), otrzymasz komunikat o błędzie:

"PointTest.y" jest niedostępny z powodu swojego poziomu ochrony.

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](../language-specification/index.md). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](modifiers.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)