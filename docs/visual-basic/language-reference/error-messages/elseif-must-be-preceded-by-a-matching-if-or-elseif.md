---
title: Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: fbb8ce974a618349bd4b5e7a2a25a165d91787a7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832258"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="49712-102">Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”</span><span class="sxs-lookup"><span data-stu-id="49712-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="49712-103">`#ElseIf` jest dyrektywą warunkowa.</span><span class="sxs-lookup"><span data-stu-id="49712-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="49712-104">`#ElseIf` Klauzuli musi być poprzedzona odpowiadającą jej instrukcją `#If` lub `#ElseIf` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="49712-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="49712-105">**Identyfikator błędu:** BC30014</span><span class="sxs-lookup"><span data-stu-id="49712-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49712-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="49712-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="49712-107">Sprawdź, czy występuje przed `#If` lub `#ElseIf` nie został rozdzielony ze to `#ElseIf` przez pośredniczące bloku kompilacja warunkowa lub nieprawidłowo umieszczony `#End If`.</span><span class="sxs-lookup"><span data-stu-id="49712-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="49712-108">Jeśli `#ElseIf` jest poprzedzony `#Else` dyrektywy, albo usuń `#Else` lub zmień ją na `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="49712-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="49712-109">Jeśli cała reszta będzie w kolejności, należy dodać `#If` dyrektywę na początku bloku kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="49712-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49712-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49712-110">See also</span></span>

- [<span data-ttu-id="49712-111">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="49712-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
