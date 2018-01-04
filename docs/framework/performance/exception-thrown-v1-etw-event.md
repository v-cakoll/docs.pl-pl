---
title: "Zdarzenia wyjątku ETW Thrown_V1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60013d0df8c63033f6da8d61479bacac7b944094
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="af947-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="af947-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="af947-103">To zdarzenie znajdują się informacje dotyczące wyjątków, które są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="af947-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="af947-104">W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest zgłaszane, a poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="af947-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="af947-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="af947-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="af947-106">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="af947-106">Keyword for raising the event</span></span>|<span data-ttu-id="af947-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="af947-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="af947-108">`ExceptionKeyword`(0x8000)</span><span class="sxs-lookup"><span data-stu-id="af947-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="af947-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="af947-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="af947-110">W poniższej tabeli przedstawiono informacje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="af947-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="af947-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="af947-111">Event</span></span>|<span data-ttu-id="af947-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="af947-112">Event ID</span></span>|<span data-ttu-id="af947-113">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="af947-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="af947-114">80</span><span class="sxs-lookup"><span data-stu-id="af947-114">80</span></span>|<span data-ttu-id="af947-115">Zarządzanych wyjątku.</span><span class="sxs-lookup"><span data-stu-id="af947-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="af947-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="af947-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="af947-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="af947-117">Field name</span></span>|<span data-ttu-id="af947-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="af947-118">Data type</span></span>|<span data-ttu-id="af947-119">Opis</span><span class="sxs-lookup"><span data-stu-id="af947-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="af947-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="af947-120">Exception Type</span></span>|<span data-ttu-id="af947-121">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="af947-121">win:UnicodeString</span></span>|<span data-ttu-id="af947-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="af947-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="af947-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="af947-123">Exception Message</span></span>|<span data-ttu-id="af947-124">Windows: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="af947-124">win:UnicodeString</span></span>|<span data-ttu-id="af947-125">Komunikat o wyjątku rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="af947-125">Actual exception message.</span></span>|  
|<span data-ttu-id="af947-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="af947-126">EIPCodeThrow</span></span>|<span data-ttu-id="af947-127">Windows: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="af947-127">win:Pointer</span></span>|<span data-ttu-id="af947-128">Wskaźnik instrukcji, w którym wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="af947-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="af947-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="af947-129">ExceptionHR</span></span>|<span data-ttu-id="af947-130">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="af947-130">win:UInt32</span></span>|<span data-ttu-id="af947-131">Wyjątek [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="af947-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="af947-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="af947-132">ExceptionFlags</span></span>|<span data-ttu-id="af947-133">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="af947-133">win:UInt16</span></span>|<span data-ttu-id="af947-134">0x01: HasInnerException (zobacz [zdarzenia ETW CLR](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji programu Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="af947-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="af947-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="af947-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="af947-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="af947-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="af947-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](http://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).</span><span class="sxs-lookup"><span data-stu-id="af947-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="af947-138">0x10: IsCLSCompliant (wyjątek, która jest pochodną <xref:System.Exception> zgodne ze specyfikacją CLS, a w przeciwnym razie nie jest zgodne ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="af947-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="af947-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="af947-139">ClrInstanceID</span></span>|<span data-ttu-id="af947-140">Windows: UInt16</span><span class="sxs-lookup"><span data-stu-id="af947-140">win:UInt16</span></span>|<span data-ttu-id="af947-141">Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="af947-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af947-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af947-142">See Also</span></span>  
 [<span data-ttu-id="af947-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="af947-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
