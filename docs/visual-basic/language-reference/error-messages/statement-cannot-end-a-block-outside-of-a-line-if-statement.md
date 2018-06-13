---
title: Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja
ms.date: 07/20/2015
f1_keywords:
- vbc32005
- bc32005
helpviewer_keywords:
- BC32005
ms.assetid: 4039f51b-e0ee-4789-a89b-45d06de06b5d
ms.openlocfilehash: af3006ddc35dfcaa52a54229881baa48cfb7809a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596687"
---
# <a name="statement-cannot-end-a-block-outside-of-a-line-39if39-statement"></a><span data-ttu-id="33782-102">Instrukcja nie może kończyć bloku poza wiersza &#39;Jeśli&#39; — instrukcja</span><span class="sxs-lookup"><span data-stu-id="33782-102">Statement cannot end a block outside of a line &#39;If&#39; statement</span></span>
<span data-ttu-id="33782-103">Jeden wiersz `If` instrukcji zawiera wiele instrukcji oddzielone dwukropkiem (:), z których jeden jest `End` instrukcji dla bloków sterowania poza jeden wiersz `If`.</span><span class="sxs-lookup"><span data-stu-id="33782-103">A single-line `If` statement contains several statements separated by colons (:), one of which is an `End` statement for a control block outside the single-line `If`.</span></span> <span data-ttu-id="33782-104">Jednowierszowe `If` nie należy używać instrukcji `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="33782-104">Single-line `If` statements do not use the `End If` statement.</span></span>  
  
 <span data-ttu-id="33782-105">**Identyfikator błędu:** BC32005</span><span class="sxs-lookup"><span data-stu-id="33782-105">**Error ID:** BC32005</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="33782-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="33782-106">To correct this error</span></span>  
  
-   <span data-ttu-id="33782-107">Przenieś jeden wiersz `If` instrukcji poza blokiem formant, który zawiera `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="33782-107">Move the single-line `If` statement outside the control block that contains the `End If` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33782-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="33782-108">See Also</span></span>  
 [<span data-ttu-id="33782-109">If...Then...Else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="33782-109">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
