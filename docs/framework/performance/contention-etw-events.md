---
title: Zdarzenia ETW dotyczące rywalizacji — .NET
description: Uzyskaj szczegółowe informacje o zdarzeniach ETW, które są wywoływane za każdym razem, gdy istnieje rywalizacja dla elementu System. Threading. monitoruje blokady lub blokady natywne używane przez środowisko uruchomieniowe.
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: a36b091e0896562fffdb66e895d70049ce0667d7
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309602"
---
# <a name="contention-etw-events"></a><span data-ttu-id="322fc-103">Zdarzenia ETW dotyczące rywalizacji</span><span class="sxs-lookup"><span data-stu-id="322fc-103">Contention ETW events</span></span>

<span data-ttu-id="322fc-104">Zdarzenia rywalizacji są wywoływane zawsze wtedy, gdy istnieje rywalizacja o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokady lub blokady natywne używane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="322fc-104">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="322fc-105">Rywalizacja występuje, gdy wątek oczekuje na blokadę, a inny wątek posiada blokadę.</span><span class="sxs-lookup"><span data-stu-id="322fc-105">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="322fc-106">W poniższej tabeli przedstawiono słowo kluczowe, pod którym są wywoływane zdarzenia rywalizacji, oraz poziom zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="322fc-106">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="322fc-107">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="322fc-107">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="322fc-108">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="322fc-108">Keyword for raising the event</span></span>|<span data-ttu-id="322fc-109">Poziom</span><span class="sxs-lookup"><span data-stu-id="322fc-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="322fc-110">`ContentionKeyword`0x4000</span><span class="sxs-lookup"><span data-stu-id="322fc-110">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="322fc-111">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="322fc-111">Informational (4)</span></span>|

<span data-ttu-id="322fc-112">W poniższej tabeli przedstawiono informacje o zdarzeniach:</span><span class="sxs-lookup"><span data-stu-id="322fc-112">The following table shows event information:</span></span>

|<span data-ttu-id="322fc-113">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="322fc-113">Event</span></span>|<span data-ttu-id="322fc-114">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="322fc-114">Event ID</span></span>|<span data-ttu-id="322fc-115">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="322fc-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="322fc-116">81</span><span class="sxs-lookup"><span data-stu-id="322fc-116">81</span></span>|<span data-ttu-id="322fc-117">Rozpocznie się rywalizację.</span><span class="sxs-lookup"><span data-stu-id="322fc-117">Contention starts.</span></span> <span data-ttu-id="322fc-118">To zdarzenie nie obejmuje ilości czasu nawirowania, zanim wątek czeka na uzyskanie blokady; jest uruchamiany tylko wtedy, gdy wątek czeka na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="322fc-118">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="322fc-119">91</span><span class="sxs-lookup"><span data-stu-id="322fc-119">91</span></span>|<span data-ttu-id="322fc-120">Zakończyło się rywalizację.</span><span class="sxs-lookup"><span data-stu-id="322fc-120">Contention ends.</span></span>|

<span data-ttu-id="322fc-121">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="322fc-121">The following table shows event data:</span></span>

|<span data-ttu-id="322fc-122">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="322fc-122">Field name</span></span>|<span data-ttu-id="322fc-123">Typ danych</span><span class="sxs-lookup"><span data-stu-id="322fc-123">Data type</span></span>|<span data-ttu-id="322fc-124">Opis</span><span class="sxs-lookup"><span data-stu-id="322fc-124">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="322fc-125">Flagi</span><span class="sxs-lookup"><span data-stu-id="322fc-125">Flags</span></span>|<span data-ttu-id="322fc-126">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="322fc-126">win:UInt8</span></span>|<span data-ttu-id="322fc-127">0 dla zarządzanych; 1 w przypadku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="322fc-127">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="322fc-128">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="322fc-128">ClrInstanceID</span></span>|<span data-ttu-id="322fc-129">win: UInt16</span><span class="sxs-lookup"><span data-stu-id="322fc-129">win:UInt16</span></span>|<span data-ttu-id="322fc-130">Unikatowy identyfikator wystąpienia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="322fc-130">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="322fc-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="322fc-131">See also</span></span>

- [<span data-ttu-id="322fc-132">Zdarzenia ETW CLR</span><span class="sxs-lookup"><span data-stu-id="322fc-132">CLR ETW Events</span></span>](clr-etw-events.md)
