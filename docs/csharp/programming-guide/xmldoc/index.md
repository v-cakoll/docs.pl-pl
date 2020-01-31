---
title: Komentarze dokumentacji XML — C# Przewodnik programowania
ms.date: 07/20/2015
f1_keywords:
- cs.xml
helpviewer_keywords:
- XML [C#], code comments
- comments [C#], XML
- documentation comments [C#]
- C# source code files
- C# language, XML code comments
- XML documentation comments [C#]
ms.assetid: 803b7f7b-7428-4725-b5db-9a6cff273199
ms.openlocfilehash: f5a507bc35b0cc0a679fd055bfc255bb3cb9a090
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789784"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Komentarze dokumentacji XML (C# Przewodnik programowania)

W C#programie można utworzyć dokumentację dla kodu, DOŁĄCZAJĄC elementy XML w specjalnych polach komentarzy (oznaczone przez potrójne ukośniki) w kodzie źródłowym bezpośrednio przed blokiem kodu, do którego odwołuje się komentarz, na przykład.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Podczas kompilowania przy użyciu opcji [-doc](../../language-reference/compiler-options/doc-compiler-option.md) kompilator przeszuka wszystkie tagi XML w kodzie źródłowym i utworzy plik dokumentacji XML. Aby utworzyć ostateczną dokumentację opartą na pliku generowanym przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).

Aby odwołać się do elementów XML (na przykład funkcja przetwarza konkretne elementy XML, które chcesz opisać w komentarzu dokumentacji XML), można użyć standardowego mechanizmu quota (`<` i `>`).  Aby odwołać się do identyfikatorów ogólnych w elementach kodu referencyjnego (`cref`), można użyć znaków ucieczki (na przykład `cref="List&lt;T&gt;"`) lub nawiasów klamrowych (`cref="List{T}"`).  Jest to szczególny przypadek, w którym kompilator analizuje nawiasy klamrowe jako nawiasy kątowe, dzięki czemu komentarz dokumentacji jest wygodniejszy dla autora, gdy ten odwołuje się do identyfikatorów ogólnych.

> [!NOTE]
> Komentarze dokumentacji XML nie są metadanymi; nie są one uwzględniane w kompilowanym zestawie i dlatego są niedostępne za pośrednictwem mechanizmu odbicia.

## <a name="in-this-section"></a>W tej sekcji

- [Zalecane Tagi dla komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

- [Przetwarzanie pliku XML](./processing-the-xml-file.md)

- [Ograniczniki tagów dokumentacji](./delimiters-for-documentation-tags.md)

- [Jak korzystać z funkcji dokumentacji XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [-doc (Przetwarzaj komentarze dokumentacji)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
