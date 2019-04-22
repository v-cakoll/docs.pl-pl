---
title: Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838654"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="acca8-102">Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione</span><span class="sxs-lookup"><span data-stu-id="acca8-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="acca8-103">Zmienna zadeklarowana ze `Shared` modyfikator jest udostępnionej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="acca8-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="acca8-104">Udostępnionej zmiennej identyfikuje dokładnie jednej lokalizacji magazynu.</span><span class="sxs-lookup"><span data-stu-id="acca8-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="acca8-105">Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmiennej obsługuje zbioru zdarzeń wywołuje zmienną.</span><span class="sxs-lookup"><span data-stu-id="acca8-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="acca8-106">Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracja unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowa procedura obsługi zdarzeń za pośrednictwem `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="acca8-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="acca8-107">**Identyfikator błędu:** BC30594</span><span class="sxs-lookup"><span data-stu-id="acca8-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="acca8-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="acca8-108">To correct this error</span></span>  
  
-   <span data-ttu-id="acca8-109">Zadeklaruj procedury obsługi zdarzenia `Shared`.</span><span class="sxs-lookup"><span data-stu-id="acca8-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acca8-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acca8-110">See also</span></span>

- [<span data-ttu-id="acca8-111">Shared</span><span class="sxs-lookup"><span data-stu-id="acca8-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="acca8-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="acca8-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
