---
title: Zdarzenia wyjątku ETW Thrown_V1
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716051"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="73d40-102">Zdarzenia wyjątku ETW Thrown_V1</span><span class="sxs-lookup"><span data-stu-id="73d40-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="73d40-103">To zdarzenie przechwytuje informacje o wygenerowanych wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="73d40-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="73d40-104">W poniższej tabeli przedstawiono słowo kluczowe, pod którym zdarzenie jest zgłaszane, oraz poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73d40-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="73d40-105">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="73d40-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="73d40-106">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="73d40-106">Keyword for raising the event</span></span>|<span data-ttu-id="73d40-107">Poziom</span><span class="sxs-lookup"><span data-stu-id="73d40-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="73d40-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="73d40-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="73d40-109">Ostrzeżenie (2)</span><span class="sxs-lookup"><span data-stu-id="73d40-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="73d40-110">W poniższej tabeli przedstawiono informacje o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="73d40-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="73d40-111">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="73d40-111">Event</span></span>|<span data-ttu-id="73d40-112">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="73d40-112">Event ID</span></span>|<span data-ttu-id="73d40-113">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="73d40-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="73d40-114">80</span><span class="sxs-lookup"><span data-stu-id="73d40-114">80</span></span>|<span data-ttu-id="73d40-115">Generowany jest wyjątek zarządzany.</span><span class="sxs-lookup"><span data-stu-id="73d40-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="73d40-116">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73d40-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="73d40-117">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="73d40-117">Field name</span></span>|<span data-ttu-id="73d40-118">Typ danych</span><span class="sxs-lookup"><span data-stu-id="73d40-118">Data type</span></span>|<span data-ttu-id="73d40-119">Opis</span><span class="sxs-lookup"><span data-stu-id="73d40-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="73d40-120">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="73d40-120">Exception Type</span></span>|<span data-ttu-id="73d40-121">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="73d40-121">win:UnicodeString</span></span>|<span data-ttu-id="73d40-122">Typ wyjątku; na przykład `System.NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="73d40-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="73d40-123">Komunikat o wyjątku</span><span class="sxs-lookup"><span data-stu-id="73d40-123">Exception Message</span></span>|<span data-ttu-id="73d40-124">win: UnicodeString</span><span class="sxs-lookup"><span data-stu-id="73d40-124">win:UnicodeString</span></span>|<span data-ttu-id="73d40-125">Rzeczywisty komunikat o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="73d40-125">Actual exception message.</span></span>|  
|<span data-ttu-id="73d40-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="73d40-126">EIPCodeThrow</span></span>|<span data-ttu-id="73d40-127">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="73d40-127">win:Pointer</span></span>|<span data-ttu-id="73d40-128">Wskaźnik instrukcji, w którym wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="73d40-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="73d40-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="73d40-129">ExceptionHR</span></span>|<span data-ttu-id="73d40-130">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="73d40-130">win:UInt32</span></span>|<span data-ttu-id="73d40-131">Wyjątek [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span><span class="sxs-lookup"><span data-stu-id="73d40-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="73d40-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="73d40-132">ExceptionFlags</span></span>|<span data-ttu-id="73d40-133">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="73d40-133">win:UInt16</span></span>|<span data-ttu-id="73d40-134">0x01: HasInnerException (zobacz [zdarzenia ETW CLR](clr-etw-events.md) w dokumentacji Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="73d40-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="73d40-135">0x02: isnestexception.</span><span class="sxs-lookup"><span data-stu-id="73d40-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="73d40-136">0x04: IsRethrownException.</span><span class="sxs-lookup"><span data-stu-id="73d40-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="73d40-137">0x08: IsCorruptedStateException (wskazuje, że stan procesu jest uszkodzony; zobacz [Obsługa wyjątków uszkodzonego stanu](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span><span class="sxs-lookup"><span data-stu-id="73d40-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="73d40-138">0x10: IsCLSCompliant (wyjątek pochodzący z <xref:System.Exception> jest zgodny ze specyfikacją CLS; w przeciwnym razie nie jest zgodny ze specyfikacją CLS).</span><span class="sxs-lookup"><span data-stu-id="73d40-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="73d40-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="73d40-139">ClrInstanceID</span></span>|<span data-ttu-id="73d40-140">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="73d40-140">win:UInt16</span></span>|<span data-ttu-id="73d40-141">Unikatowy identyfikator wystąpienia CLR lub CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="73d40-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73d40-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73d40-142">See also</span></span>

- [<span data-ttu-id="73d40-143">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="73d40-143">CLR ETW Events</span></span>](clr-etw-events.md)
