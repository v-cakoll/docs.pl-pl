---
title: Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 808cf35fb05da092cdef560721b2f667778aa78f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409663"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="af114-102">Instrukcja „#ElseIf” musi być poprzedzona odpowiadającą jej instrukcją „#If” lub „#ElseIf”</span><span class="sxs-lookup"><span data-stu-id="af114-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="af114-103">`#ElseIf`jest dyrektywy kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="af114-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="af114-104">`#ElseIf`Klauzula musi być poprzedzona odpowiadającą jej `#If` `#ElseIf` klauzulą or.</span><span class="sxs-lookup"><span data-stu-id="af114-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="af114-105">**Identyfikator błędu:** BC30014</span><span class="sxs-lookup"><span data-stu-id="af114-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af114-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="af114-106">To correct this error</span></span>  
  
1. <span data-ttu-id="af114-107">Sprawdź, czy poprzedni `#If` lub `#ElseIf` nie został oddzielony od tego `#ElseIf` przez inicjowany przez Ciebie blok kompilacji warunkowej lub nieprawidłowo umieszczony `#End If` .</span><span class="sxs-lookup"><span data-stu-id="af114-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2. <span data-ttu-id="af114-108">Jeśli `#ElseIf` jest poprzedzona przez `#Else` dyrektywę, Usuń `#Else` lub Zmień ją na `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="af114-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3. <span data-ttu-id="af114-109">Jeśli wszystko inne jest w porządku, Dodaj `#If` dyrektywę na początku bloku kompilacji warunkowej.</span><span class="sxs-lookup"><span data-stu-id="af114-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af114-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af114-110">See also</span></span>

- [<span data-ttu-id="af114-111">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="af114-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
