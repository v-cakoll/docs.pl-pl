---
title: Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 5652139ab139ea93258eb116f97ba21b76986a24
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400386"
---
# <a name="region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="24b9f-102">Instrukcje „#Region” i „#End Region” nie są prawidłowe w treści metod/wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="24b9f-102">'#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="24b9f-103">`#Region`Blok musi być zadeklarowany na poziomie klasy, modułu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="24b9f-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="24b9f-104">Region zwijany może zawierać jedną lub więcej procedur, ale nie może zaczynać się ani kończyć wewnątrz procedury.</span><span class="sxs-lookup"><span data-stu-id="24b9f-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="24b9f-105">**Identyfikator błędu:** BC32025</span><span class="sxs-lookup"><span data-stu-id="24b9f-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="24b9f-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="24b9f-106">To correct this error</span></span>  
  
1. <span data-ttu-id="24b9f-107">Upewnij się, że poprzednia procedura została prawidłowo `End Function` zakończona `End Sub` instrukcją or.</span><span class="sxs-lookup"><span data-stu-id="24b9f-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="24b9f-108">Upewnij się, `#Region` że `#End Region` dyrektywy i znajdują się w tym samym bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="24b9f-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b9f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24b9f-109">See also</span></span>

- [<span data-ttu-id="24b9f-110">#Region — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="24b9f-110">#Region Directive</span></span>](../directives/region-directive.md)
