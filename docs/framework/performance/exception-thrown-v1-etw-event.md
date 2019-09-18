---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91abd9e6f31380b7e8cd3df1a14aa5c5722901ba
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046518"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="8342b-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="8342b-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="8342b-103">To zdarzenie przechwytuje informacje o wygenerowanych wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="8342b-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="8342b-104">W poniższej tabeli przedstawiono słowo kluczowe, pod którym zdarzenie jest zgłaszane, oraz poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8342b-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="8342b-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="8342b-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="8342b-106">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8342b-106">Keyword for raising the event</span></span>|<span data-ttu-id="8342b-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="8342b-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="8342b-108">`ExceptionKeyword`0x8000</span><span class="sxs-lookup"><span data-stu-id="8342b-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="8342b-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="8342b-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="8342b-110">W poniższej tabeli przedstawiono informacje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="8342b-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="8342b-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="8342b-111">Event</span></span>|<span data-ttu-id="8342b-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8342b-112">Event ID</span></span>|<span data-ttu-id="8342b-113">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="8342b-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="8342b-114">80</span><span class="sxs-lookup"><span data-stu-id="8342b-114">80</span></span>|<span data-ttu-id="8342b-115">Generowany jest wyjątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8342b-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="8342b-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8342b-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="8342b-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="8342b-117">Field name</span></span>|<span data-ttu-id="8342b-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="8342b-118">Data type</span></span>|<span data-ttu-id="8342b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="8342b-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="8342b-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="8342b-120">Exception Type</span></span>|<span data-ttu-id="8342b-121">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8342b-121">win:UnicodeString</span></span>|<span data-ttu-id="8342b-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="8342b-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="8342b-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="8342b-123">Exception Message</span></span>|<span data-ttu-id="8342b-124">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="8342b-124">win:UnicodeString</span></span>|<span data-ttu-id="8342b-125">Rzeczywisty komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="8342b-125">Actual exception message.</span></span>|  
|<span data-ttu-id="8342b-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="8342b-126">EIPCodeThrow</span></span>|<span data-ttu-id="8342b-127">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="8342b-127">win:Pointer</span></span>|<span data-ttu-id="8342b-128">Wskaźnik instrukcji, w którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8342b-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="8342b-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="8342b-129">ExceptionHR</span></span>|<span data-ttu-id="8342b-130">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="8342b-130">win:UInt32</span></span>|<span data-ttu-id="8342b-131">Wyjątek [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span><span class="sxs-lookup"><span data-stu-id="8342b-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="8342b-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="8342b-132">ExceptionFlags</span></span>|<span data-ttu-id="8342b-133">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="8342b-133">win:UInt16</span></span>|<span data-ttu-id="8342b-134">0x01: HasInnerException (zobacz [zdarzenia ETW CLR](clr-etw-events.md) w dokumentacji Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8342b-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="8342b-135">0x02: IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="8342b-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="8342b-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="8342b-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="8342b-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [Obsługa wyjątków uszkodzonych Stanów](https://go.microsoft.com/fwlink/?LinkId=179681) w witrynie MSDN).</span><span class="sxs-lookup"><span data-stu-id="8342b-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="8342b-138">0x10 IsCLSCompliant (wyjątek pochodzący z <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="8342b-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="8342b-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="8342b-139">ClrInstanceID</span></span>|<span data-ttu-id="8342b-140">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="8342b-140">win:UInt16</span></span>|<span data-ttu-id="8342b-141">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="8342b-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8342b-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8342b-142">See also</span></span>

- [<span data-ttu-id="8342b-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="8342b-143">CLR ETW Events</span></span>](clr-etw-events.md)
