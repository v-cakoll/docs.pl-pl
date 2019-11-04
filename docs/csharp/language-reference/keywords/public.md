---
title: Public — słowo C# kluczowe — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422559"
---
# <a name="public-c-reference"></a>public (odwołanie w C#)

Słowo kluczowe `public` jest modyfikatorem dostępu dla typów i elementów członkowskich typu. Dostęp publiczny to najwyższy poziom dostępu. Nie ma żadnych ograniczeń dotyczących uzyskiwania dostępu do publicznych członków, jak w tym przykładzie:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomy dostępności](accessibility-levels.md) .

## <a name="example"></a>Przykład

W poniższym przykładzie są zadeklarowane dwie klasy, `PointTest` i `MainClass`. Publiczne składowe `x` i `y` `PointTest` są dostępne bezpośrednio z `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

W przypadku zmiany poziomu dostępu `public` na [prywatny](private.md) lub [chroniony](protected.md)zostanie wyświetlony komunikat o błędzie:

Element "PointTest. y" jest niedostępny z powodu swojego poziomu ochrony.

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [zadeklarowane ułatwienia dostępu](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz także

- [C#Odwoła](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
