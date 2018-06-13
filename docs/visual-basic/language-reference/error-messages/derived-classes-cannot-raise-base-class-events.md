---
title: Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 365ce6ece1d964d3fac2a44f7ed4c1e16f44c95d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586402"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="e82b7-102">Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="e82b7-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="e82b7-103">Zdarzenie można wywoływane tylko z miejsca deklaracji, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="e82b7-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="e82b7-104">W związku z tym klasy nie mogą wywoływać zdarzeń z żadną inną klasę, nawet jedną, z którego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="e82b7-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="e82b7-105">**Identyfikator błędu:** BC30029</span><span class="sxs-lookup"><span data-stu-id="e82b7-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e82b7-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e82b7-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e82b7-107">Przenieś `Event` instrukcji lub `RaiseEvent` instrukcji, dzięki czemu są one w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="e82b7-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e82b7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e82b7-108">See Also</span></span>  
 [<span data-ttu-id="e82b7-109">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e82b7-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="e82b7-110">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e82b7-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
