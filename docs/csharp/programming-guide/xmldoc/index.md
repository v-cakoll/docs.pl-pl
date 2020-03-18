---
title: Komentarze dotyczące dokumentacji XML — przewodnik programowania Języka C#
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76789784"
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Komentarze dotyczące dokumentacji XML (przewodnik programowania Języka C#)

W języku C#, można utworzyć dokumentację dla kodu, dołączając elementy XML w specjalnych polach komentarzy (wskazanych przez potrójne ukośniki) w kodzie źródłowym bezpośrednio przed blokiem kodu, do którego odnoszą się komentarze, na przykład.

```csharp
/// <summary>
///  This class performs an important function.
/// </summary>
public class MyClass {}
```

Podczas kompilowania z opcją [-doc](../../language-reference/compiler-options/doc-compiler-option.md) kompilator wyszuka wszystkie znaczniki XML w kodzie źródłowym i utworzy plik dokumentacji XML. Aby utworzyć ostateczną dokumentację na podstawie pliku wygenerowanego przez kompilator, można utworzyć niestandardowe narzędzie lub użyć narzędzia, takiego jak [DocFX](https://dotnet.github.io/docfx/) lub [Sandcastle](https://github.com/EWSoftware/SHFB).

Aby odwołać się do elementów XML (na przykład funkcja przetwarza określone elementy XML, które chcesz opisać w`<` `>`komentarzu dokumentacji XML), można użyć standardowego mechanizmu cytowania ( i ).  Aby odwołać się do identyfikatorów ogólnych w elementach odwołania do kodu (`cref`) można użyć znaków ucieczki (na `cref="List&lt;T&gt;"`przykład) lub nawiasów klamrowych (`cref="List{T}"`).  Jest to szczególny przypadek, w którym kompilator analizuje nawiasy klamrowe jako nawiasy kątowe, dzięki czemu komentarz dokumentacji jest wygodniejszy dla autora, gdy ten odwołuje się do identyfikatorów ogólnych.

> [!NOTE]
> Komentarze dokumentacji XML nie są metadanymi; nie są one uwzględniane w kompilowanym zestawie i dlatego są niedostępne za pośrednictwem mechanizmu odbicia.

## <a name="in-this-section"></a>W tej sekcji

- [Zalecane tagi przeznaczone do komentarzy dokumentacji](./recommended-tags-for-documentation-comments.md)

- [Przetwarzanie pliku XML](./processing-the-xml-file.md)

- [Ograniczniki tagów dokumentacji](./delimiters-for-documentation-tags.md)

- [Używanie funkcji dokumentacji XML](./how-to-use-the-xml-documentation-features.md)

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz:

- [-doc (Komentarze dokumentacji procesu)](../../language-reference/compiler-options/doc-compiler-option.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
