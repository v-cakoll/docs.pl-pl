---
title: "Oczekiwano końca instrukcji"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="bf1bf-102">Oczekiwano końca instrukcji</span><span class="sxs-lookup"><span data-stu-id="bf1bf-102">End of statement expected</span></span>
<span data-ttu-id="bf1bf-103">Wykonywanie instrukcji zostało składniowo ukończone, ale dodatkowy element programowania zgodny element kończące instrukcję.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="bf1bf-104">Terminator wiersza jest wymagany na końcu każdej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="bf1bf-105">Terminator wiersza dzieli znaki plik źródłowy języka Visual Basic wierszy.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="bf1bf-106">Przykłady terminatory wiersza są Unicode karetki zwracanych znaków (& HD), Unicode wysuwu wiersza znak (& HA), a znak Unicode wysuwu wiersza znak powrotu karetki Unicode.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="bf1bf-107">Aby uzyskać więcej informacji o wierszu terminatory, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf1bf-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="bf1bf-108">**Identyfikator błędu:** BC30205</span><span class="sxs-lookup"><span data-stu-id="bf1bf-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="bf1bf-109">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="bf1bf-109">To correct this error</span></span>
  
1.  <span data-ttu-id="bf1bf-110">Sprawdź, czy dwa różne instrukcje przypadkowo zostały wprowadzone w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="bf1bf-111">Wstaw terminator wiersza po elemencie kończące instrukcję.</span><span class="sxs-lookup"><span data-stu-id="bf1bf-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bf1bf-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf1bf-112">See Also</span></span>  
 [<span data-ttu-id="bf1bf-113">Porady: przerywanie i łączenie instrukcji w Code</span><span class="sxs-lookup"><span data-stu-id="bf1bf-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="bf1bf-114">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="bf1bf-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
