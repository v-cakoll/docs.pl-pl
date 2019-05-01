---
title: Element „<eventname>” jest zdarzeniem i nie można go wywołać bezpośrednio
ms.date: 07/20/2015
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords:
- BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
ms.openlocfilehash: bf900566bdb4ecf8d8961a12b5dd67ba426caf27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803327"
---
# <a name="eventname-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="8c752-102">"\<eventname >" jest zdarzeniem i nie można wywołać bezpośrednio</span><span class="sxs-lookup"><span data-stu-id="8c752-102">'\<eventname>' is an event, and cannot be called directly</span></span>
<span data-ttu-id="8c752-103">"<`eventname`>" jest zdarzeniem i dlatego nie można wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="8c752-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="8c752-104">Użyj `RaiseEvent` instrukcję, aby wywołać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8c752-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="8c752-105">Wywołanie procedury określa zdarzenie dla nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="8c752-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="8c752-106">Program obsługi zdarzeń jest procedurą samego zdarzenia jest jednak sygnalizowanie urządzenia, które muszą być zgłaszane i obsługi.</span><span class="sxs-lookup"><span data-stu-id="8c752-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="8c752-107">**Identyfikator błędu:** BC32022</span><span class="sxs-lookup"><span data-stu-id="8c752-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8c752-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8c752-108">To correct this error</span></span>  
  
1. <span data-ttu-id="8c752-109">Użyj `RaiseEvent` instrukcję w celu zasygnalizowania zdarzenia i wywoływać procedury lub procedury, które go obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="8c752-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c752-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c752-110">See also</span></span>

- [<span data-ttu-id="8c752-111">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8c752-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
