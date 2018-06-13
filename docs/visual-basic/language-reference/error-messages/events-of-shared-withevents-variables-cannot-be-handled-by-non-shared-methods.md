---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585174"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="0889b-102">Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione</span><span class="sxs-lookup"><span data-stu-id="0889b-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="0889b-103">Zmienna zadeklarowana ze `Shared` modyfikator jest udostępniona zmienna.</span><span class="sxs-lookup"><span data-stu-id="0889b-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="0889b-104">Udostępniona zmienna identyfikuje dokładnie jedną lokalizację magazynu.</span><span class="sxs-lookup"><span data-stu-id="0889b-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="0889b-105">Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmienna obsługuje zbioru zdarzeń zgłasza zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0889b-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="0889b-106">Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracji unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowy program obsługi zdarzeń za pomocą `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="0889b-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="0889b-107">**Identyfikator błędu:** BC30594</span><span class="sxs-lookup"><span data-stu-id="0889b-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0889b-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="0889b-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0889b-109">Zadeklaruj procedury obsługi zdarzenia `Shared`.</span><span class="sxs-lookup"><span data-stu-id="0889b-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0889b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0889b-110">See Also</span></span>  
 [<span data-ttu-id="0889b-111">Shared</span><span class="sxs-lookup"><span data-stu-id="0889b-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="0889b-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="0889b-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
