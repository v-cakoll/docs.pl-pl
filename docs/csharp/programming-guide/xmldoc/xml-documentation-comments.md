---
title: "Komentarze dokumentacji XML (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f8718096a7bce08b18a00ec04a5a8b0adb12bca
ms.sourcegitcommit: e2bf8e6bc365bd9a0e86fe81eeae7d14f85f48c1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2018
---
# <a name="xml-documentation-comments-c-programming-guide"></a><span data-ttu-id="cba88-102">Komentarze dokumentacji XML (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="cba88-102">XML Documentation Comments (C# Programming Guide)</span></span>
<span data-ttu-id="cba88-103">W języku Visual C# można tworzyć dokumentację kodu, umieszczając elementy XML w specjalnych polach komentarzy (wskazywanych przez potrójne ukośniki) w kodzie źródłowym bezpośrednio przed blokiem kodu, do którego odwołują się komentarze, na przykład:</span><span class="sxs-lookup"><span data-stu-id="cba88-103">In Visual C# you can create documentation for your code by including XML elements in special comment fields (indicated by triple slashes) in the source code directly before the code block to which the comments refer, for example:</span></span>  
  
```  
/// <summary>  
///  This class performs an important function.  
/// </summary>  
public class MyClass{}  
```  
  
 <span data-ttu-id="cba88-104">Podczas kompilacji z [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) opcja, kompilator będzie Wyszukaj wszystkie tagi XML źródła kodu i tworzenie pliku dokumentacji XML.</span><span class="sxs-lookup"><span data-stu-id="cba88-104">When you compile with the [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) option, the compiler will search for all XML tags in the source code and create an XML documentation file.</span></span> <span data-ttu-id="cba88-105">Aby utworzyć końcowego dokumentację na podstawie pliku generowane przez kompilator, można utworzyć niestandardowego narzędzia lub za pomocą narzędzia, takie jak [Sandcastle](https://github.com/EWSoftware/SHFB).</span><span class="sxs-lookup"><span data-stu-id="cba88-105">To create the final documentation based on the compiler-generated file, you can create a custom tool or use a tool such as [Sandcastle](https://github.com/EWSoftware/SHFB).</span></span>  
  
 <span data-ttu-id="cba88-106">Aby odwołać się do elementów XML (na przykład funkcja procesów określonych XML elementów przeznaczone do opisywania w komentarzu XML dokumentacji), można użyć standardowego mechanizmu otwierający (`<` i `>`).</span><span class="sxs-lookup"><span data-stu-id="cba88-106">To refer to XML elements (for example, your function processes specific XML elements that you want to describe in an XML documentation comment), you can use the standard quoting mechanism (`<` and `>`).</span></span>  <span data-ttu-id="cba88-107">Aby odwołać się do ogólnego identyfikatorów kodu — odwołanie (`cref`) elementy, można użyć znaków ucieczki (na przykład `cref="List&lt;T&gt;"`) lub nawiasów klamrowych (`cref="List{T}"`).</span><span class="sxs-lookup"><span data-stu-id="cba88-107">To refer to generic identifiers in code reference (`cref`) elements, you can use either the escape characters (for example, `cref="List&lt;T&gt;"`) or braces (`cref="List{T}"`).</span></span>  <span data-ttu-id="cba88-108">Jest to szczególny przypadek, w którym kompilator analizuje nawiasy klamrowe jako nawiasy kątowe, dzięki czemu komentarz dokumentacji jest wygodniejszy dla autora, gdy ten odwołuje się do identyfikatorów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="cba88-108">As a special case, the compiler parses the braces as angle brackets to make the documentation comment less cumbersome to author when referring to generic identifiers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cba88-109">Komentarze dokumentacji XML nie są metadanymi; nie są one uwzględniane w kompilowanym zestawie i dlatego są niedostępne za pośrednictwem mechanizmu odbicia.</span><span class="sxs-lookup"><span data-stu-id="cba88-109">The XML documentation comments are not metadata; they are not included in the compiled assembly and therefore they are not accessible through reflection.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cba88-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="cba88-110">In This Section</span></span>  
  
-   [<span data-ttu-id="cba88-111">Zalecane tagi przeznaczone do komentarzy dokumentacji</span><span class="sxs-lookup"><span data-stu-id="cba88-111">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="cba88-112">Przetwarzanie pliku XML</span><span class="sxs-lookup"><span data-stu-id="cba88-112">Processing the XML File</span></span>](../../../csharp/programming-guide/xmldoc/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="cba88-113">Ograniczniki tagów dokumentacji</span><span class="sxs-lookup"><span data-stu-id="cba88-113">Delimiters for Documentation Tags</span></span>](../../../csharp/programming-guide/xmldoc/delimiters-for-documentation-tags.md)  
  
-   [<span data-ttu-id="cba88-114">Instrukcje: użycie funkcji dokumentacji XML</span><span class="sxs-lookup"><span data-stu-id="cba88-114">How to: Use the XML Documentation Features</span></span>](../../../csharp/programming-guide/xmldoc/how-to-use-the-xml-documentation-features.md)  
  
## <a name="related-sections"></a><span data-ttu-id="cba88-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="cba88-115">Related Sections</span></span>  
 <span data-ttu-id="cba88-116">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="cba88-116">For more information, see:</span></span>  
  
-   [<span data-ttu-id="cba88-117">/ doc (przetwarzanie komentarzy dokumentacji)</span><span class="sxs-lookup"><span data-stu-id="cba88-117">/doc (Process Documentation Comments)</span></span>](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="cba88-118">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cba88-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cba88-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cba88-119">See Also</span></span>  
 [<span data-ttu-id="cba88-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cba88-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
