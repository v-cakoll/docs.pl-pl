---
title: Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: c59212a28ba27123a7db9163ff7437c159a3d310
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409702"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a><span data-ttu-id="b3e92-102">Klasy pochodne nie mogą wywoływać zdarzeń klasy bazowej</span><span class="sxs-lookup"><span data-stu-id="b3e92-102">Derived classes cannot raise base class events</span></span>
<span data-ttu-id="b3e92-103">Zdarzenie może być zgłaszane tylko z przestrzeni deklaracji, w której jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="b3e92-103">An event can be raised only from the declaration space in which it is declared.</span></span> <span data-ttu-id="b3e92-104">W związku z tym Klasa nie może wywoływać zdarzeń z żadnej innej klasy, nawet jednego z nich, z której pochodzą.</span><span class="sxs-lookup"><span data-stu-id="b3e92-104">Therefore, a class cannot raise events from any other class, even one from which it is derived.</span></span>  
  
 <span data-ttu-id="b3e92-105">**Identyfikator błędu:** BC30029</span><span class="sxs-lookup"><span data-stu-id="b3e92-105">**Error ID:** BC30029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b3e92-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b3e92-106">To correct this error</span></span>  
  
- <span data-ttu-id="b3e92-107">Przenieś `Event` instrukcję lub `RaiseEvent` instrukcję tak, aby znajdowały się w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="b3e92-107">Move the `Event` statement or the `RaiseEvent` statement so they are in the same class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3e92-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3e92-108">See also</span></span>

- [<span data-ttu-id="b3e92-109">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3e92-109">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="b3e92-110">RaiseEvent — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="b3e92-110">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
