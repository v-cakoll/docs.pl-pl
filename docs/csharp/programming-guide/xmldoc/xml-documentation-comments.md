---
title: Komentarze dokumentacji XML (Przewodnik programowania w języku C#)
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
ms.openlocfilehash: 2f3bc5780e202bc5905cc027821f937b75335454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-documentation-comments-c-programming-guide"></a>Komentarze dokumentacji XML (Przewodnik programowania w języku C#)
W języku Visual C# można tworzyć dokumentację kodu, umieszczając elementy XML w specjalnych polach komentarzy (wskazywanych przez potrójne ukośniki) w kodzie źródłowym bezpośrednio przed blokiem kodu, do którego odwołują się komentarze, na przykład:  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 Podczas kompilacji z [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) opcja, kompilator będzie Wyszukaj wszystkie tagi XML źródła kodu i tworzenie pliku dokumentacji XML. Aby utworzyć końcowego dokumentację na podstawie pliku generowane przez kompilator, można utworzyć niestandardowego narzędzia lub za pomocą narzędzia, takie jak [Sandcastle](https://github.com/EWSoftware/SHFB).  
  
 Aby odwołać się do elementów XML (na przykład funkcja procesów określonych XML elementów przeznaczone do opisywania w komentarzu XML dokumentacji), można użyć standardowego mechanizmu otwierający (`<` i `>`).  Aby odwołać się do ogólnego identyfikatorów kodu — odwołanie (`cref`) elementy, można użyć znaków ucieczki (na przykład `cref="List&lt;T&gt;"`) lub nawiasów klamrowych (`cref="List{T}"`).  Jest to szczególny przypadek, w którym kompilator analizuje nawiasy klamrowe jako nawiasy kątowe, dzięki czemu komentarz dokumentacji jest wygodniejszy dla autora, gdy ten odwołuje się do identyfikatorów ogólnych.  
  
> [!NOTE]
>  Komentarze dokumentacji XML nie są metadanymi; nie są one uwzględniane w kompilowanym zestawie i dlatego są niedostępne za pośrednictwem mechanizmu odbicia.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Zalecane tagi przeznaczone do komentarzy dokumentacji](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [Przetwarzanie pliku XML](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [Ograniczniki tagów dokumentacji](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [Instrukcje: użycie funkcji dokumentacji XML](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [/ doc (przetwarzanie komentarzy dokumentacji)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
