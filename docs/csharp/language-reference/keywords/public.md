---
title: publiczne słowo kluczowe - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 19906d7fd0f7d41ef9e4cdaf951c77825e0bbead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713173"
---
# <a name="public-c-reference"></a>public (odwołanie w C#)

Słowo `public` kluczowe jest modyfikatorem dostępu dla typów i elementów członkowskich typu. Publiczny dostęp jest najbardziej liberalnym poziomem dostępu. Nie ma żadnych ograniczeń dotyczących dostępu do członków publicznych, jak w tym przykładzie:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md) i [poziomy ułatwień dostępu.](accessibility-levels.md)

## <a name="example"></a>Przykład

W poniższym przykładzie zadeklarowane `PointTest` są `MainClass`dwie klasy i . Członkowie `x` publiczni `y` `PointTest` i są dostępowi bezpośrednio z `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Jeśli zmienisz poziom dostępu na `public` [prywatny](private.md) lub [chroniony,](protected.md)zostanie wyświetlony komunikat o błędzie:

"PointTest.y" jest niedostępny ze względu na jego poziom ochrony.

## <a name="c-language-specification"></a>specyfikacja języka C#  

Aby uzyskać więcej informacji, zobacz [Zadeklarowana dostępność](~/_csharplang/spec/basic-concepts.md#declared-accessibility) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Słowa kluczowe języka C#](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Poziomy ułatwień dostępu](accessibility-levels.md)
- [Modyfikatory](index.md)
- [Prywatny](private.md)
- [protected](protected.md)
- [Wewnętrznego](internal.md)
