---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409572"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="d6e3f-102">Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione</span><span class="sxs-lookup"><span data-stu-id="d6e3f-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="d6e3f-103">Zmienna zadeklarowana z `Shared` modyfikatorem jest zmienną udostępnioną.</span><span class="sxs-lookup"><span data-stu-id="d6e3f-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="d6e3f-104">Zmienna współdzielona identyfikuje dokładnie jedną lokalizację magazynu.</span><span class="sxs-lookup"><span data-stu-id="d6e3f-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="d6e3f-105">Zmienna zadeklarowana z `WithEvents` modyfikatorem modyfikującym, że typ, do którego należy zmienna, obsługuje zestaw zdarzeń zgłaszanych przez zmienną.</span><span class="sxs-lookup"><span data-stu-id="d6e3f-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="d6e3f-106">Gdy wartość jest przypisana do zmiennej, właściwość utworzona przez `WithEvents` deklarację odłączy wszelkie istniejące procedury obsługi zdarzeń i przechwytuje nowy program obsługi zdarzeń za pośrednictwem `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="d6e3f-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="d6e3f-107">**Identyfikator błędu:** BC30594</span><span class="sxs-lookup"><span data-stu-id="d6e3f-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d6e3f-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d6e3f-108">To correct this error</span></span>  
  
- <span data-ttu-id="d6e3f-109">Zadeklaruj procedurę obsługi zdarzeń `Shared` .</span><span class="sxs-lookup"><span data-stu-id="d6e3f-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e3f-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6e3f-110">See also</span></span>

- [<span data-ttu-id="d6e3f-111">Shared</span><span class="sxs-lookup"><span data-stu-id="d6e3f-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="d6e3f-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="d6e3f-112">WithEvents</span></span>](../modifiers/withevents.md)
