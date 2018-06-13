---
title: Zdarzenie ETW stosu
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 073622c22b957975ed799cf5b3bc3826473114b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396357"
---
# <a name="stack-etw-event"></a><span data-ttu-id="ae358-102">Zdarzenie ETW stosu</span><span class="sxs-lookup"><span data-stu-id="ae358-102">Stack ETW Event</span></span>
<span data-ttu-id="ae358-103">Zdarzenie stosu stosuje się w połączeniu z innymi zdarzeniami, można wygenerować śladów stosu po wywołaniu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae358-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="ae358-104">Jest on rejestrowane, gdy dostawca środowiska uruchomieniowego jest włączony.</span><span class="sxs-lookup"><span data-stu-id="ae358-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="ae358-105">Jest to zdarzenie bardzo wysokiej częstotliwości, ponieważ jest wywoływane, gdy innego środowiska uruchomieniowego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae358-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="ae358-106">Z tego powodu zaleca się, użyj tego zdarzenia z rozwagą.</span><span class="sxs-lookup"><span data-stu-id="ae358-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="ae358-107">W poniższej tabeli przedstawiono — słowo kluczowe i poziom.</span><span class="sxs-lookup"><span data-stu-id="ae358-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="ae358-108">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="ae358-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="ae358-109">Słowo kluczowe wywołaniem zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae358-109">Keyword for raising the event</span></span>|<span data-ttu-id="ae358-110">Poziom</span><span class="sxs-lookup"><span data-stu-id="ae358-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="ae358-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="ae358-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="ae358-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="ae358-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="ae358-113">W poniższej tabeli przedstawiono informacje dotyczące zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae358-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="ae358-114">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="ae358-114">Event</span></span>|<span data-ttu-id="ae358-115">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ae358-115">Event ID</span></span>|<span data-ttu-id="ae358-116">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="ae358-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="ae358-117">82</span><span class="sxs-lookup"><span data-stu-id="ae358-117">82</span></span>|<span data-ttu-id="ae358-118">W połączeniu z innymi zdarzeniami, aby wygenerować ślady stosu, następujące zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ae358-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="ae358-119">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ae358-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="ae358-120">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="ae358-120">Field name</span></span>|<span data-ttu-id="ae358-121">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ae358-121">Data Type</span></span>|<span data-ttu-id="ae358-122">Opis</span><span class="sxs-lookup"><span data-stu-id="ae358-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="ae358-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="ae358-123">ClrInstanceID</span></span>|<span data-ttu-id="ae358-124">Windows: Uint16</span><span class="sxs-lookup"><span data-stu-id="ae358-124">win:Uint16</span></span>|<span data-ttu-id="ae358-125">Środowisko uruchomieniowe Unikatowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ae358-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="ae358-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="ae358-126">Reserved1</span></span>|<span data-ttu-id="ae358-127">Windows: UInt8</span><span class="sxs-lookup"><span data-stu-id="ae358-127">win:UInt8</span></span>|<span data-ttu-id="ae358-128">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="ae358-128">Reserved.</span></span>|  
|<span data-ttu-id="ae358-129">Zarezerwowane2</span><span class="sxs-lookup"><span data-stu-id="ae358-129">Reserved2</span></span>|<span data-ttu-id="ae358-130">Windows: UInt8</span><span class="sxs-lookup"><span data-stu-id="ae358-130">win:UInt8</span></span>|<span data-ttu-id="ae358-131">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="ae358-131">Reserved.</span></span>|  
|<span data-ttu-id="ae358-132">Wartości FrameCount</span><span class="sxs-lookup"><span data-stu-id="ae358-132">FrameCount</span></span>|<span data-ttu-id="ae358-133">Windows: UInt32.</span><span class="sxs-lookup"><span data-stu-id="ae358-133">win:UInt32</span></span>|<span data-ttu-id="ae358-134">Liczba ramek w ślad stosu.</span><span class="sxs-lookup"><span data-stu-id="ae358-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="ae358-135">Stos</span><span class="sxs-lookup"><span data-stu-id="ae358-135">Stack</span></span>|<span data-ttu-id="ae358-136">Windows: wskaźnik</span><span class="sxs-lookup"><span data-stu-id="ae358-136">win:Pointer</span></span>|<span data-ttu-id="ae358-137">Kolumny wskaźników instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae358-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae358-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae358-138">See Also</span></span>  
 [<span data-ttu-id="ae358-139">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="ae358-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
