---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723020"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="b5c40-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="b5c40-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="b5c40-103">To zdarzenie znajdują się informacje dotyczące wyjątków, które są generowane.</span><span class="sxs-lookup"><span data-stu-id="b5c40-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="b5c40-104">W poniższej tabeli przedstawiono — słowo kluczowe, w którym zdarzenie jest wywoływane, a poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c40-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="b5c40-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="b5c40-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b5c40-106">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b5c40-106">Keyword for raising the event</span></span>|<span data-ttu-id="b5c40-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="b5c40-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="b5c40-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="b5c40-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="b5c40-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="b5c40-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="b5c40-110">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="b5c40-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="b5c40-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="b5c40-111">Event</span></span>|<span data-ttu-id="b5c40-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b5c40-112">Event ID</span></span>|<span data-ttu-id="b5c40-113">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="b5c40-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="b5c40-114">80</span><span class="sxs-lookup"><span data-stu-id="b5c40-114">80</span></span>|<span data-ttu-id="b5c40-115">Zarządzane wyjątek jest generowany.</span><span class="sxs-lookup"><span data-stu-id="b5c40-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="b5c40-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b5c40-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="b5c40-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="b5c40-117">Field name</span></span>|<span data-ttu-id="b5c40-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b5c40-118">Data type</span></span>|<span data-ttu-id="b5c40-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b5c40-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b5c40-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="b5c40-120">Exception Type</span></span>|<span data-ttu-id="b5c40-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b5c40-121">win:UnicodeString</span></span>|<span data-ttu-id="b5c40-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="b5c40-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="b5c40-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="b5c40-123">Exception Message</span></span>|<span data-ttu-id="b5c40-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b5c40-124">win:UnicodeString</span></span>|<span data-ttu-id="b5c40-125">Komunikat o wyjątku rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="b5c40-125">Actual exception message.</span></span>|  
|<span data-ttu-id="b5c40-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="b5c40-126">EIPCodeThrow</span></span>|<span data-ttu-id="b5c40-127">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="b5c40-127">win:Pointer</span></span>|<span data-ttu-id="b5c40-128">Wskaźnik instrukcji, w którym wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="b5c40-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="b5c40-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="b5c40-129">ExceptionHR</span></span>|<span data-ttu-id="b5c40-130">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="b5c40-130">win:UInt32</span></span>|<span data-ttu-id="b5c40-131">Wyjątek [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="b5c40-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="b5c40-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="b5c40-132">ExceptionFlags</span></span>|<span data-ttu-id="b5c40-133">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="b5c40-133">win:UInt16</span></span>|<span data-ttu-id="b5c40-134">0x01: HasInnerException (zobacz [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) w dokumentacji języka Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b5c40-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="b5c40-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="b5c40-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="b5c40-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="b5c40-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="b5c40-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [obsługi wyjątków stan uszkodzony](https://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).</span><span class="sxs-lookup"><span data-stu-id="b5c40-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="b5c40-138">0x10: IsCLSCompliant (wyjątek, który pochodzi od klasy <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="b5c40-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="b5c40-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b5c40-139">ClrInstanceID</span></span>|<span data-ttu-id="b5c40-140">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="b5c40-140">win:UInt16</span></span>|<span data-ttu-id="b5c40-141">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="b5c40-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b5c40-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b5c40-142">See also</span></span>

- [<span data-ttu-id="b5c40-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="b5c40-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
