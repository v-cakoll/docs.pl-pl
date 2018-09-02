---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43400825"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="ed488-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="ed488-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="ed488-103">To zdarzenie znajdują się informacje dotyczące wyjątków, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="ed488-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="ed488-104">W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest wywoływane, a poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ed488-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="ed488-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ed488-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ed488-106">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ed488-106">Keyword for raising the event</span></span>|<span data-ttu-id="ed488-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="ed488-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ed488-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="ed488-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="ed488-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="ed488-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="ed488-110">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="ed488-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="ed488-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ed488-111">Event</span></span>|<span data-ttu-id="ed488-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ed488-112">Event ID</span></span>|<span data-ttu-id="ed488-113">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="ed488-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="ed488-114">80</span><span class="sxs-lookup"><span data-stu-id="ed488-114">80</span></span>|<span data-ttu-id="ed488-115">Zarządzane wyjątek jest generowany.</span><span class="sxs-lookup"><span data-stu-id="ed488-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="ed488-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ed488-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="ed488-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ed488-117">Field name</span></span>|<span data-ttu-id="ed488-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ed488-118">Data type</span></span>|<span data-ttu-id="ed488-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ed488-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ed488-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="ed488-120">Exception Type</span></span>|<span data-ttu-id="ed488-121">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ed488-121">win:UnicodeString</span></span>|<span data-ttu-id="ed488-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="ed488-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="ed488-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="ed488-123">Exception Message</span></span>|<span data-ttu-id="ed488-124">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="ed488-124">win:UnicodeString</span></span>|<span data-ttu-id="ed488-125">Komunikat o wyjątku rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="ed488-125">Actual exception message.</span></span>|  
|<span data-ttu-id="ed488-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="ed488-126">EIPCodeThrow</span></span>|<span data-ttu-id="ed488-127">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="ed488-127">win:Pointer</span></span>|<span data-ttu-id="ed488-128">Wskaźnik instrukcji, w którym wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="ed488-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="ed488-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="ed488-129">ExceptionHR</span></span>|<span data-ttu-id="ed488-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ed488-130">win:UInt32</span></span>|<span data-ttu-id="ed488-131">Wyjątek [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="ed488-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="ed488-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="ed488-132">ExceptionFlags</span></span>|<span data-ttu-id="ed488-133">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ed488-133">win:UInt16</span></span>|<span data-ttu-id="ed488-134">0x01: HasInnerException (zobacz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ed488-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="ed488-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="ed488-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="ed488-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="ed488-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="ed488-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](https://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).</span><span class="sxs-lookup"><span data-stu-id="ed488-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="ed488-138">0x10: IsCLSCompliant (wyjątek, który pochodzi od klasy <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="ed488-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="ed488-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ed488-139">ClrInstanceID</span></span>|<span data-ttu-id="ed488-140">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="ed488-140">win:UInt16</span></span>|<span data-ttu-id="ed488-141">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="ed488-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed488-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed488-142">See Also</span></span>  
 [<span data-ttu-id="ed488-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ed488-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
