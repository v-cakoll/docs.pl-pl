---
title: Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 030c9c2ffa97572298b23f05c23e3af0df7387b0
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913160"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="b6582-102">Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="b6582-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="b6582-103">Zdarzenie może zostać wywołane jedynie z deklaracji miejsca, w którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="b6582-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="b6582-104">W związku z tym klasy nie mogą wywoływać zdarzeń z żadną inną klasę, nawet jeśli jest on z którego pochodzi.</span><span class="sxs-lookup"><span data-stu-id="b6582-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="b6582-105">**Identyfikator błędu:** BC30029</span><span class="sxs-lookup"><span data-stu-id="b6582-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6582-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b6582-106">To correct this error</span></span>  
  
- <span data-ttu-id="b6582-107">Przenieś `Event` instrukcji lub `RaiseEvent` instrukcji, dzięki czemu są one w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="b6582-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6582-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6582-108">See also</span></span>

- [<span data-ttu-id="b6582-109">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6582-109">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="b6582-110">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b6582-110">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
