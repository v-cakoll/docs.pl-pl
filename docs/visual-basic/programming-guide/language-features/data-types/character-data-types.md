---
title: Znaki — Typy danych (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840981"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="710f0-102">Znaki — Typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="710f0-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="710f0-103">Visual Basic oferuje *typ danych znakowych* radzenia sobie z drukowania i zawiera znaki.</span><span class="sxs-lookup"><span data-stu-id="710f0-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="710f0-104">Gdy oba postępowania ze znakami Unicode `Char` zawiera pojedynczy znak, natomiast `String` zawiera nieokreśloną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="710f0-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="710f0-105">Dla tabeli, która wyświetla porównania side-by-side typy danych Visual Basic, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="710f0-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="710f0-106">CHAR — typ</span><span class="sxs-lookup"><span data-stu-id="710f0-106">Char Type</span></span>  
 <span data-ttu-id="710f0-107">`Char` Typ danych jest jednym dwóch-bajtowych wartości znakowych Unicode (16-bitowy).</span><span class="sxs-lookup"><span data-stu-id="710f0-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="710f0-108">Jeśli zmienna przechowuje zawsze dokładnie jeden znak, Zadeklaruj go jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="710f0-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="710f0-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="710f0-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="710f0-110">Każdej możliwej wartości w `Char` lub `String` zmienna jest *punktem kodu*, lub kod znaku w zestawie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="710f0-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="710f0-111">Znaki Unicode obejmują podstawowy zestaw znaków ASCII, różne inne litery alfabetu, akcentów, symbole walut, ułamki, znaki diakrytyczne i symbole matematyczne i technicznych.</span><span class="sxs-lookup"><span data-stu-id="710f0-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="710f0-112">Zestaw znaków Unicode rezerwy kod wskazuje D800 za pośrednictwem DFFF (55296 za pośrednictwem 55551 dziesiętna) dla *zastępczych par*, które wymagają dwóch wartości 16-bitowych reprezentuje punkt kodu jednego.</span><span class="sxs-lookup"><span data-stu-id="710f0-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="710f0-113">A `Char` zmiennej nie może utrzymywać para zastępcza i `String` używa dwóch pozycji do przechowywania tych pary.</span><span class="sxs-lookup"><span data-stu-id="710f0-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="710f0-114">Aby uzyskać więcej informacji, zobacz [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="710f0-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="710f0-115">String — typ</span><span class="sxs-lookup"><span data-stu-id="710f0-115">String Type</span></span>  
 <span data-ttu-id="710f0-116">`String` — Typ danych to sekwencja zero lub więcej znaków Unicode (16-bitowy) dwóch bajtów.</span><span class="sxs-lookup"><span data-stu-id="710f0-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="710f0-117">Jeśli zmienna może zawierać dowolną liczbę znaków, Zadeklaruj go jako `String`.</span><span class="sxs-lookup"><span data-stu-id="710f0-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="710f0-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="710f0-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="710f0-119">Aby uzyskać więcej informacji, zobacz [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="710f0-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="710f0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="710f0-120">See also</span></span>

- [<span data-ttu-id="710f0-121">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="710f0-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="710f0-122">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="710f0-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="710f0-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="710f0-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="710f0-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="710f0-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="710f0-125">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="710f0-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="710f0-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="710f0-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="710f0-127">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="710f0-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
