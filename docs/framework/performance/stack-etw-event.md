---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0cb166f2753b910465aabb8abd68c31c6f56ff8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497541"
---
# <a name="stack-etw-event"></a><span data-ttu-id="cd2f0-102">Zdarzenie ETW stosu</span><span class="sxs-lookup"><span data-stu-id="cd2f0-102">Stack ETW Event</span></span>
<span data-ttu-id="cd2f0-103">Zdarzenie stosu powinny służyć w połączeniu z innymi zdarzeniami można wygenerować ślady stosu, po wydarzenie jest podniesione.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="cd2f0-104">Jest on rejestrowane, gdy jest włączony dostawca środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="cd2f0-105">To wydarzenie bardzo wysokiej częstotliwości, ponieważ jest zgłaszany w każdym przypadku, gdy inne zdarzenie środowiska wykonawczego jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="cd2f0-106">Z tego powodu zaleca się używać tego wydarzenia z ostrożnością.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="cd2f0-107">W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="cd2f0-108">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="cd2f0-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="cd2f0-109">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cd2f0-109">Keyword for raising the event</span></span>|<span data-ttu-id="cd2f0-110">Poziom</span><span class="sxs-lookup"><span data-stu-id="cd2f0-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="cd2f0-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="cd2f0-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="cd2f0-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="cd2f0-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="cd2f0-113">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="cd2f0-114">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="cd2f0-114">Event</span></span>|<span data-ttu-id="cd2f0-115">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cd2f0-115">Event ID</span></span>|<span data-ttu-id="cd2f0-116">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="cd2f0-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="cd2f0-117">82</span><span class="sxs-lookup"><span data-stu-id="cd2f0-117">82</span></span>|<span data-ttu-id="cd2f0-118">W połączeniu z innymi zdarzeniami, aby wygenerować ślady stosu, następujące zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="cd2f0-119">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="cd2f0-120">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="cd2f0-120">Field name</span></span>|<span data-ttu-id="cd2f0-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="cd2f0-121">Data Type</span></span>|<span data-ttu-id="cd2f0-122">Opis</span><span class="sxs-lookup"><span data-stu-id="cd2f0-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="cd2f0-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="cd2f0-123">ClrInstanceID</span></span>|<span data-ttu-id="cd2f0-124">win: Uint16.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-124">win:Uint16</span></span>|<span data-ttu-id="cd2f0-125">Identyfikator unikatowy środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="cd2f0-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="cd2f0-126">Reserved1</span></span>|<span data-ttu-id="cd2f0-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="cd2f0-127">win:UInt8</span></span>|<span data-ttu-id="cd2f0-128">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-128">Reserved.</span></span>|  
|<span data-ttu-id="cd2f0-129">Zarezerwowane2</span><span class="sxs-lookup"><span data-stu-id="cd2f0-129">Reserved2</span></span>|<span data-ttu-id="cd2f0-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="cd2f0-130">win:UInt8</span></span>|<span data-ttu-id="cd2f0-131">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-131">Reserved.</span></span>|  
|<span data-ttu-id="cd2f0-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="cd2f0-132">FrameCount</span></span>|<span data-ttu-id="cd2f0-133">win: UInt32.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-133">win:UInt32</span></span>|<span data-ttu-id="cd2f0-134">Liczba klatek ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="cd2f0-135">Stos</span><span class="sxs-lookup"><span data-stu-id="cd2f0-135">Stack</span></span>|<span data-ttu-id="cd2f0-136">win: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="cd2f0-136">win:Pointer</span></span>|<span data-ttu-id="cd2f0-137">Kolumny wskaźników instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cd2f0-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd2f0-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd2f0-138">See also</span></span>
- [<span data-ttu-id="cd2f0-139">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="cd2f0-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
