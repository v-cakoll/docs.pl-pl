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
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505226"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="c32ad-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="c32ad-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="c32ad-103">To zdarzenie znajdują się informacje dotyczące wyjątków, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="c32ad-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="c32ad-104">W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest wywoływane, a poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c32ad-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="c32ad-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="c32ad-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c32ad-106">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c32ad-106">Keyword for raising the event</span></span>|<span data-ttu-id="c32ad-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="c32ad-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c32ad-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="c32ad-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="c32ad-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="c32ad-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="c32ad-110">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="c32ad-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="c32ad-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="c32ad-111">Event</span></span>|<span data-ttu-id="c32ad-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c32ad-112">Event ID</span></span>|<span data-ttu-id="c32ad-113">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="c32ad-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="c32ad-114">80</span><span class="sxs-lookup"><span data-stu-id="c32ad-114">80</span></span>|<span data-ttu-id="c32ad-115">Zarządzane wyjątek jest generowany.</span><span class="sxs-lookup"><span data-stu-id="c32ad-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="c32ad-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c32ad-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="c32ad-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="c32ad-117">Field name</span></span>|<span data-ttu-id="c32ad-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="c32ad-118">Data type</span></span>|<span data-ttu-id="c32ad-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c32ad-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c32ad-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="c32ad-120">Exception Type</span></span>|<span data-ttu-id="c32ad-121">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c32ad-121">win:UnicodeString</span></span>|<span data-ttu-id="c32ad-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="c32ad-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="c32ad-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="c32ad-123">Exception Message</span></span>|<span data-ttu-id="c32ad-124">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c32ad-124">win:UnicodeString</span></span>|<span data-ttu-id="c32ad-125">Komunikat o wyjątku rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="c32ad-125">Actual exception message.</span></span>|  
|<span data-ttu-id="c32ad-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="c32ad-126">EIPCodeThrow</span></span>|<span data-ttu-id="c32ad-127">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="c32ad-127">win:Pointer</span></span>|<span data-ttu-id="c32ad-128">Wskaźnik instrukcji, w którym wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="c32ad-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="c32ad-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="c32ad-129">ExceptionHR</span></span>|<span data-ttu-id="c32ad-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="c32ad-130">win:UInt32</span></span>|<span data-ttu-id="c32ad-131">Wyjątek [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="c32ad-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="c32ad-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="c32ad-132">ExceptionFlags</span></span>|<span data-ttu-id="c32ad-133">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="c32ad-133">win:UInt16</span></span>|<span data-ttu-id="c32ad-134">0x01: HasInnerException (zobacz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="c32ad-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="c32ad-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="c32ad-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="c32ad-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="c32ad-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="c32ad-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](https://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).</span><span class="sxs-lookup"><span data-stu-id="c32ad-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="c32ad-138">0x10: IsCLSCompliant (wyjątek, który pochodzi od klasy <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="c32ad-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="c32ad-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c32ad-139">ClrInstanceID</span></span>|<span data-ttu-id="c32ad-140">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="c32ad-140">win:UInt16</span></span>|<span data-ttu-id="c32ad-141">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="c32ad-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c32ad-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c32ad-142">See Also</span></span>  
 [<span data-ttu-id="c32ad-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="c32ad-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
