---
title: „<methodname>” ma wiele definicji o identycznych podpisach
ms.date: 07/20/2015
f1_keywords:
- vbc30269
- bc30269
helpviewer_keywords:
- BC30269
ms.assetid: 39489621-6617-4e5c-9b24-c2faf8273891
ms.openlocfilehash: fe8d1d8e11e25bcd79894ed82a57dd06748c3d68
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831881"
---
# <a name="methodname-has-multiple-definitions-with-identical-signatures"></a><span data-ttu-id="f7749-102">"\<methodname >" ma wiele definicji o identycznych podpisach</span><span class="sxs-lookup"><span data-stu-id="f7749-102">'\<methodname>' has multiple definitions with identical signatures</span></span>
<span data-ttu-id="f7749-103">A `Function` lub `Sub` deklaracja procedury używa procedury identyczne nazwą i listą argumentów jako poprzedniej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="f7749-103">A `Function` or `Sub` procedure declaration uses the identical procedure name and argument list as a previous declaration.</span></span> <span data-ttu-id="f7749-104">Jedną z możliwych przyczyn jest próba przeciążenia oryginalne procedury.</span><span class="sxs-lookup"><span data-stu-id="f7749-104">One possible cause is an attempt to overload the original procedure.</span></span> <span data-ttu-id="f7749-105">Przeciążona procedury musi mieć listy różnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="f7749-105">Overloaded procedures must have different argument lists.</span></span>  
  
 <span data-ttu-id="f7749-106">**Identyfikator błędu:** BC30269</span><span class="sxs-lookup"><span data-stu-id="f7749-106">**Error ID:** BC30269</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7749-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f7749-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f7749-108">Zmień nazwę procedury lub listy argumentów, lub usuń Zduplikowana deklaracja.</span><span class="sxs-lookup"><span data-stu-id="f7749-108">Change the procedure name or the argument list, or remove the duplicate declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7749-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7749-109">See also</span></span>

- [<span data-ttu-id="f7749-110">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="f7749-110">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="f7749-111">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="f7749-111">Considerations in Overloading Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)
