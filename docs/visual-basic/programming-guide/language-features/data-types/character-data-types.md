---
title: Znaki — Typy danych
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346395"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="7b576-102">Znaki — Typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b576-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="7b576-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span><span class="sxs-lookup"><span data-stu-id="7b576-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="7b576-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span><span class="sxs-lookup"><span data-stu-id="7b576-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="7b576-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b576-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="7b576-106">Char Type</span><span class="sxs-lookup"><span data-stu-id="7b576-106">Char Type</span></span>  
 <span data-ttu-id="7b576-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span><span class="sxs-lookup"><span data-stu-id="7b576-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="7b576-108">If a variable always stores exactly one character, declare it as `Char`.</span><span class="sxs-lookup"><span data-stu-id="7b576-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="7b576-109">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7b576-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="7b576-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span><span class="sxs-lookup"><span data-stu-id="7b576-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="7b576-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span><span class="sxs-lookup"><span data-stu-id="7b576-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b576-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span><span class="sxs-lookup"><span data-stu-id="7b576-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="7b576-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span><span class="sxs-lookup"><span data-stu-id="7b576-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="7b576-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7b576-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="7b576-115">String Type</span><span class="sxs-lookup"><span data-stu-id="7b576-115">String Type</span></span>  
 <span data-ttu-id="7b576-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="7b576-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="7b576-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span><span class="sxs-lookup"><span data-stu-id="7b576-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="7b576-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7b576-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="7b576-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="7b576-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b576-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b576-120">See also</span></span>

- [<span data-ttu-id="7b576-121">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="7b576-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="7b576-122">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="7b576-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="7b576-123">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b576-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7b576-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="7b576-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="7b576-125">Type Conversions in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b576-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="7b576-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="7b576-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="7b576-127">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="7b576-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
