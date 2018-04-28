---
title: Znaki — Typy danych (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: afd368c00444f136c6d69b02a733c82f0c8eafe0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="8e444-102">Znaki — Typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e444-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="8e444-103">Visual Basic zapewnia *znakowe typy danych* radzenia sobie z znaków drukowalnych i którą można wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="8e444-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="8e444-104">Gdy oba postępowania w przypadku znaków Unicode, `Char` przechowuje pojedynczym znakiem, podczas gdy `String` zawiera nieokreśloną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="8e444-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="8e444-105">Dla tabeli, która zawiera porównanie side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="8e444-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="8e444-106">CHAR — typ</span><span class="sxs-lookup"><span data-stu-id="8e444-106">Char Type</span></span>  
 <span data-ttu-id="8e444-107">`Char` Typ danych to pojedynczy znak Unicode dwubajtowych (16-bitowe).</span><span class="sxs-lookup"><span data-stu-id="8e444-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="8e444-108">Jeśli zmienna przechowuje zawsze dokładnie jeden znak, Zadeklaruj ją jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="8e444-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="8e444-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8e444-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="8e444-110">Każdej możliwej wartości w `Char` lub `String` zmienna jest *punktem kodu*, lub kod znaku w zestawie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="8e444-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="8e444-111">Znaków Unicode należą do zestawu znaków ASCII, różnych innych litery alfabetu, akcentów, symbol waluty, ułamków, znaków diakrytycznych i symbole matematyczne i technicznych.</span><span class="sxs-lookup"><span data-stu-id="8e444-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e444-112">Zestaw znaków Unicode rezerw D800 za pośrednictwem DFFF (55296 za pośrednictwem 55551 decimal) dla punktów kod *dwuskładnikowy pary*, co wymaga dwóch wartości 16-bitowych reprezentuje punkt jeden kod.</span><span class="sxs-lookup"><span data-stu-id="8e444-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="8e444-113">A `Char` zmiennej nie może zawierać para zastępcza, a `String` używa do przechowywania takich parze dwie pozycje.</span><span class="sxs-lookup"><span data-stu-id="8e444-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="8e444-114">Aby uzyskać więcej informacji, zobacz [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8e444-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="8e444-115">String — typ</span><span class="sxs-lookup"><span data-stu-id="8e444-115">String Type</span></span>  
 <span data-ttu-id="8e444-116">`String` — Typ danych jest sekwencją zero lub więcej znaków Unicode (16-bitowy) dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="8e444-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="8e444-117">Jeśli zmienna może zawierać dowolną liczbę znaków, Zadeklaruj ją jako `String`.</span><span class="sxs-lookup"><span data-stu-id="8e444-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="8e444-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8e444-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="8e444-119">Aby uzyskać więcej informacji, zobacz [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="8e444-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e444-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e444-120">See Also</span></span>  
 [<span data-ttu-id="8e444-121">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="8e444-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [<span data-ttu-id="8e444-122">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="8e444-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [<span data-ttu-id="8e444-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e444-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [<span data-ttu-id="8e444-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="8e444-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="8e444-125">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e444-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="8e444-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="8e444-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="8e444-127">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="8e444-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
