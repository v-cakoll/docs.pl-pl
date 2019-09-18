---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5dc23f5105b589d5b74c9ea6b7f40b84c2b04e6a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046159"
---
# <a name="stack-etw-event"></a><span data-ttu-id="f5162-102">Zdarzenie ETW stosu</span><span class="sxs-lookup"><span data-stu-id="f5162-102">Stack ETW Event</span></span>
<span data-ttu-id="f5162-103">Zdarzenia stosu należy używać w połączeniu z innymi zdarzeniami w celu generowania śladów stosu po podniesieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f5162-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="f5162-104">Jest on rejestrowany po włączeniu dostawcy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f5162-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="f5162-105">Jest to zdarzenie o dużej częstotliwości, ponieważ jest zgłaszane przy każdym wywołaniu innego zdarzenia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f5162-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="f5162-106">Z tego powodu zaleca się użycie tego zdarzenia z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="f5162-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="f5162-107">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="f5162-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="f5162-108">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="f5162-108">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f5162-109">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f5162-109">Keyword for raising the event</span></span>|<span data-ttu-id="f5162-110">Poziom</span><span class="sxs-lookup"><span data-stu-id="f5162-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f5162-111">`StackKeyword`0x40000000</span><span class="sxs-lookup"><span data-stu-id="f5162-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="f5162-112">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="f5162-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="f5162-113">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="f5162-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f5162-114">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="f5162-114">Event</span></span>|<span data-ttu-id="f5162-115">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f5162-115">Event ID</span></span>|<span data-ttu-id="f5162-116">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="f5162-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="f5162-117">82</span><span class="sxs-lookup"><span data-stu-id="f5162-117">82</span></span>|<span data-ttu-id="f5162-118">W połączeniu z innymi zdarzeniami do generowania śladów stosu po zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="f5162-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="f5162-119">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f5162-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f5162-120">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="f5162-120">Field name</span></span>|<span data-ttu-id="f5162-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="f5162-121">Data Type</span></span>|<span data-ttu-id="f5162-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f5162-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f5162-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f5162-123">ClrInstanceID</span></span>|<span data-ttu-id="f5162-124">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="f5162-124">win:Uint16</span></span>|<span data-ttu-id="f5162-125">Unikatowy identyfikator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f5162-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="f5162-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="f5162-126">Reserved1</span></span>|<span data-ttu-id="f5162-127">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="f5162-127">win:UInt8</span></span>|<span data-ttu-id="f5162-128">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="f5162-128">Reserved.</span></span>|  
|<span data-ttu-id="f5162-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="f5162-129">Reserved2</span></span>|<span data-ttu-id="f5162-130">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="f5162-130">win:UInt8</span></span>|<span data-ttu-id="f5162-131">Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="f5162-131">Reserved.</span></span>|  
|<span data-ttu-id="f5162-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="f5162-132">FrameCount</span></span>|<span data-ttu-id="f5162-133">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="f5162-133">win:UInt32</span></span>|<span data-ttu-id="f5162-134">Liczba ramek w śladzie stosu.</span><span class="sxs-lookup"><span data-stu-id="f5162-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="f5162-135">Stos</span><span class="sxs-lookup"><span data-stu-id="f5162-135">Stack</span></span>|<span data-ttu-id="f5162-136">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="f5162-136">win:Pointer</span></span>|<span data-ttu-id="f5162-137">Kolumny wskaźników instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f5162-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5162-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5162-138">See also</span></span>

- [<span data-ttu-id="f5162-139">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="f5162-139">CLR ETW Events</span></span>](clr-etw-events.md)
