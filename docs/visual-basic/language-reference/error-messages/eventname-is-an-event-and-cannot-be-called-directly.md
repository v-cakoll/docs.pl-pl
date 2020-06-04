---
title: Element „<eventname>” jest zdarzeniem i nie można go wywołać bezpośrednio
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: 510fff5370e63a31ee271421c0ab6f154518899f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409598"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="95cec-102">Element „\<eventname>” jest zdarzeniem i nie można go wywołać bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="95cec-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="95cec-103">"<`eventname`>" jest zdarzeniem i dlatego nie można go wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="95cec-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="95cec-104">Użyj `RaiseEvent` instrukcji, aby zgłosić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="95cec-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="95cec-105">Wywołanie procedury określa zdarzenie dla nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="95cec-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="95cec-106">Procedura obsługi zdarzeń jest procedurą, ale samo zdarzenie jest urządzeniem sygnalizującym, które musi zostać podniesione i obsłużone.</span><span class="sxs-lookup"><span data-stu-id="95cec-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="95cec-107">**Identyfikator błędu:** BC32022</span><span class="sxs-lookup"><span data-stu-id="95cec-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="95cec-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="95cec-108">To correct this error</span></span>  
  
1. <span data-ttu-id="95cec-109">Użyj `RaiseEvent` instrukcji, aby sygnalizować zdarzenie i wywołać procedury lub procedury, które je obsługują.</span><span class="sxs-lookup"><span data-stu-id="95cec-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95cec-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95cec-110">See also</span></span>

- [<span data-ttu-id="95cec-111">RaiseEvent — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="95cec-111">RaiseEvent Statement</span></span>](../statements/raiseevent-statement.md)
