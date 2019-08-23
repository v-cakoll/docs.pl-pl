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
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965678"
---
# <a name="character-data-types-visual-basic"></a><span data-ttu-id="0906d-102">Znaki — Typy danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0906d-102">Character Data Types (Visual Basic)</span></span>
<span data-ttu-id="0906d-103">Visual Basic zawiera *typy danych znakowych* , które umożliwiają rozproszenie i drukowalne znaki.</span><span class="sxs-lookup"><span data-stu-id="0906d-103">Visual Basic provides *character data types* to deal with printable and displayable characters.</span></span> <span data-ttu-id="0906d-104">Chociaż obydwie zajmują się znakami `Char` Unicode, przechowuje pojedynczy `String` znak, a zawiera nieokreśloną liczbę znaków.</span><span class="sxs-lookup"><span data-stu-id="0906d-104">While they both deal with Unicode characters, `Char` holds a single character whereas `String` contains an indefinite number of characters.</span></span>  
  
 <span data-ttu-id="0906d-105">W przypadku tabeli wyświetlającej porównanie obok Visual Basic typów danych, zobacz [typy danych](../../../../visual-basic/language-reference/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="0906d-105">For a table that displays a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).</span></span>  
  
## <a name="char-type"></a><span data-ttu-id="0906d-106">Typ char</span><span class="sxs-lookup"><span data-stu-id="0906d-106">Char Type</span></span>  
 <span data-ttu-id="0906d-107">Typ `Char` danych to pojedynczy dwubajtowy znak Unicode (16-bitowy).</span><span class="sxs-lookup"><span data-stu-id="0906d-107">The `Char` data type is a single two-byte (16-bit) Unicode character.</span></span> <span data-ttu-id="0906d-108">Jeśli zmienna zawsze przechowuje dokładnie jeden znak, zadeklaruj go jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="0906d-108">If a variable always stores exactly one character, declare it as `Char`.</span></span> <span data-ttu-id="0906d-109">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0906d-109">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 <span data-ttu-id="0906d-110">Każda możliwa wartość w `Char` zmiennej or `String` jest *punktem kodu*lub kodem znaku w zestawie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0906d-110">Each possible value in a `Char` or `String` variable is a *code point*, or character code, in the Unicode character set.</span></span> <span data-ttu-id="0906d-111">Znaki Unicode obejmują podstawowy zestaw znaków ASCII, różne litery alfabetu, akcenty, symbole waluty, ułamki, znaki diakrytyczne i symbole matematyczne i techniczne.</span><span class="sxs-lookup"><span data-stu-id="0906d-111">Unicode characters include the basic ASCII character set, various other alphabet letters, accents, currency symbols, fractions, diacritics, and mathematical and technical symbols.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0906d-112">Zestaw znaków Unicode rezerwuje punkty kodu D800 przez DFFF (55296 do 55551 dziesiętnych) dla *par surogatów*, które wymagają wartości 2 16-bitowych do reprezentowania pojedynczego punktu kodu.</span><span class="sxs-lookup"><span data-stu-id="0906d-112">The Unicode character set reserves the code points D800 through DFFF (55296 through 55551 decimal) for *surrogate pairs*, which require two 16-bit values to represent a single code point.</span></span> <span data-ttu-id="0906d-113">Zmienna nie może zawierać pary zastępczej `String` i używa dwóch pozycji do przechowywania takiej pary. `Char`</span><span class="sxs-lookup"><span data-stu-id="0906d-113">A `Char` variable cannot hold a surrogate pair, and a `String` uses two positions to hold such a pair.</span></span>  
  
 <span data-ttu-id="0906d-114">Aby uzyskać więcej informacji, zobacz [char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0906d-114">For more information, see [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span>  
  
## <a name="string-type"></a><span data-ttu-id="0906d-115">Typ ciągu</span><span class="sxs-lookup"><span data-stu-id="0906d-115">String Type</span></span>  
 <span data-ttu-id="0906d-116">Typ `String` danych jest sekwencją zero lub więcej dwubajtowych (16-bitowych) znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="0906d-116">The `String` data type is a sequence of zero or more two-byte (16-bit) Unicode characters.</span></span> <span data-ttu-id="0906d-117">Jeśli zmienna może zawierać nieokreśloną liczbę znaków, zadeklaruj ją jako `String`.</span><span class="sxs-lookup"><span data-stu-id="0906d-117">If a variable can contain an indefinite number of characters, declare it as `String`.</span></span> <span data-ttu-id="0906d-118">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0906d-118">For example:</span></span>  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 <span data-ttu-id="0906d-119">Aby uzyskać więcej informacji, zobacz [Typ danych ciągu](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0906d-119">For more information, see [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0906d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0906d-120">See also</span></span>

- [<span data-ttu-id="0906d-121">Typy danych podstawowych</span><span class="sxs-lookup"><span data-stu-id="0906d-121">Elementary Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [<span data-ttu-id="0906d-122">Złożone typy danych</span><span class="sxs-lookup"><span data-stu-id="0906d-122">Composite Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [<span data-ttu-id="0906d-123">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0906d-123">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="0906d-124">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="0906d-124">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [<span data-ttu-id="0906d-125">Konwersje typów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0906d-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="0906d-126">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="0906d-126">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="0906d-127">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="0906d-127">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
