---
title: Zdarzenie ETW stosu
description: Przeczytaj o zdarzeniu ETW stosu, który powinien być używany w połączeniu z innymi zdarzeniami w celu wygenerowania śladów stosu po podniesieniu zdarzenia.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474140"
---
# <a name="stack-etw-event"></a><span data-ttu-id="2b7a5-103">Zdarzenie ETW stosu</span><span class="sxs-lookup"><span data-stu-id="2b7a5-103">Stack ETW Event</span></span>
<span data-ttu-id="2b7a5-104">Zdarzenia stosu należy używać w połączeniu z innymi zdarzeniami w celu generowania śladów stosu po podniesieniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="2b7a5-105">Jest on rejestrowany po włączeniu dostawcy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="2b7a5-106">Jest to zdarzenie o dużej częstotliwości, ponieważ jest zgłaszane przy każdym wywołaniu innego zdarzenia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="2b7a5-107">Z tego powodu zaleca się użycie tego zdarzenia z zachowaniem ostrożności.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="2b7a5-108">W poniższej tabeli przedstawiono słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="2b7a5-109">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).</span><span class="sxs-lookup"><span data-stu-id="2b7a5-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2b7a5-110">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2b7a5-110">Keyword for raising the event</span></span>|<span data-ttu-id="2b7a5-111">Poziom</span><span class="sxs-lookup"><span data-stu-id="2b7a5-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2b7a5-112">`StackKeyword`0x40000000</span><span class="sxs-lookup"><span data-stu-id="2b7a5-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="2b7a5-113">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="2b7a5-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="2b7a5-114">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2b7a5-115">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="2b7a5-115">Event</span></span>|<span data-ttu-id="2b7a5-116">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2b7a5-116">Event ID</span></span>|<span data-ttu-id="2b7a5-117">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="2b7a5-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="2b7a5-118">82</span><span class="sxs-lookup"><span data-stu-id="2b7a5-118">82</span></span>|<span data-ttu-id="2b7a5-119">W połączeniu z innymi zdarzeniami do generowania śladów stosu po zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="2b7a5-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2b7a5-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="2b7a5-121">Field name</span></span>|<span data-ttu-id="2b7a5-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="2b7a5-122">Data Type</span></span>|<span data-ttu-id="2b7a5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="2b7a5-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2b7a5-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2b7a5-124">ClrInstanceID</span></span>|<span data-ttu-id="2b7a5-125">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="2b7a5-125">win:Uint16</span></span>|<span data-ttu-id="2b7a5-126">Unikatowy identyfikator środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="2b7a5-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="2b7a5-127">Reserved1</span></span>|<span data-ttu-id="2b7a5-128">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2b7a5-128">win:UInt8</span></span>|<span data-ttu-id="2b7a5-129">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-129">Reserved.</span></span>|  
|<span data-ttu-id="2b7a5-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="2b7a5-130">Reserved2</span></span>|<span data-ttu-id="2b7a5-131">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2b7a5-131">win:UInt8</span></span>|<span data-ttu-id="2b7a5-132">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-132">Reserved.</span></span>|  
|<span data-ttu-id="2b7a5-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="2b7a5-133">FrameCount</span></span>|<span data-ttu-id="2b7a5-134">win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2b7a5-134">win:UInt32</span></span>|<span data-ttu-id="2b7a5-135">Liczba ramek w śladzie stosu.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="2b7a5-136">Stos</span><span class="sxs-lookup"><span data-stu-id="2b7a5-136">Stack</span></span>|<span data-ttu-id="2b7a5-137">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="2b7a5-137">win:Pointer</span></span>|<span data-ttu-id="2b7a5-138">Kolumny wskaźników instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2b7a5-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b7a5-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2b7a5-139">See also</span></span>

- [<span data-ttu-id="2b7a5-140">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="2b7a5-140">CLR ETW Events</span></span>](clr-etw-events.md)
