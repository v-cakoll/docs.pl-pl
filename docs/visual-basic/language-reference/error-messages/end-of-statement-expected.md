---
title: Oczekiwano końca instrukcji
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 1ce5c793a09df34ac17e70e3253e98108bf76fb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321482"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="c2248-102">Oczekiwano końca instrukcji</span><span class="sxs-lookup"><span data-stu-id="c2248-102">End of statement expected</span></span>
<span data-ttu-id="c2248-103">Instrukcja jest syntaktycznie ukończone, ale dodatkowy element programowania następuje po elemencie, kończące instrukcję.</span><span class="sxs-lookup"><span data-stu-id="c2248-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="c2248-104">Terminator wiersza jest wymagany na końcu każdej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c2248-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="c2248-105">Terminator wiersza dzieli znaki plik źródłowy w języku Visual Basic na wierszach.</span><span class="sxs-lookup"><span data-stu-id="c2248-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="c2248-106">Terminatory wiersza przykłady Unicode karetki zwracany znak (& HD), Unicode wysuwu wiersza znaku (i wysokiej dostępności) i następuje znak wysuwu wiersza Unicode znak powrotu karetki Unicode.</span><span class="sxs-lookup"><span data-stu-id="c2248-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="c2248-107">Aby uzyskać więcej informacji na temat terminatory wiersza zobacz [specyfikacja języka Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="c2248-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="c2248-108">**Identyfikator błędu:** BC30205</span><span class="sxs-lookup"><span data-stu-id="c2248-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c2248-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="c2248-109">To correct this error</span></span>
  
1. <span data-ttu-id="c2248-110">Sprawdź, jeśli dwie różne instrukcje zostały przypadkowo wprowadzone w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="c2248-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2. <span data-ttu-id="c2248-111">Wstaw terminator wiersza po elemencie, kończące instrukcję.</span><span class="sxs-lookup"><span data-stu-id="c2248-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c2248-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2248-112">See also</span></span>

- [<span data-ttu-id="c2248-113">Instrukcje: przerywanie i łączenie instrukcji w kodzie</span><span class="sxs-lookup"><span data-stu-id="c2248-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="c2248-114">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="c2248-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
