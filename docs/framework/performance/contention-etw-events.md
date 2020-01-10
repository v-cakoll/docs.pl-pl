---
title: Zdarzenia ETW dotyczące rywalizacji — .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
ms.openlocfilehash: 98fc2adcaebe4c9646ab9960f796982681a9015a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716134"
---
# <a name="contention-etw-events"></a><span data-ttu-id="127ca-102">Zdarzenia ETW dotyczące rywalizacji</span><span class="sxs-lookup"><span data-stu-id="127ca-102">Contention ETW events</span></span>

<span data-ttu-id="127ca-103">Zdarzenia rywalizacji są wywoływane zawsze wtedy, gdy istnieje rywalizacja o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokad lub blokad natywnych używanych przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="127ca-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="127ca-104">Rywalizacja występuje, gdy wątek oczekuje na blokadę, a inny wątek posiada blokadę.</span><span class="sxs-lookup"><span data-stu-id="127ca-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="127ca-105">W poniższej tabeli przedstawiono słowo kluczowe, pod którym są wywoływane zdarzenia rywalizacji, oraz poziom zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="127ca-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="127ca-106">Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="127ca-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="127ca-107">Słowo kluczowe do podniesienia zdarzenia</span><span class="sxs-lookup"><span data-stu-id="127ca-107">Keyword for raising the event</span></span>|<span data-ttu-id="127ca-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="127ca-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="127ca-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="127ca-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="127ca-110">Informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="127ca-110">Informational (4)</span></span>|

<span data-ttu-id="127ca-111">W poniższej tabeli przedstawiono informacje o zdarzeniach:</span><span class="sxs-lookup"><span data-stu-id="127ca-111">The following table shows event information:</span></span>

|<span data-ttu-id="127ca-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="127ca-112">Event</span></span>|<span data-ttu-id="127ca-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="127ca-113">Event ID</span></span>|<span data-ttu-id="127ca-114">Wywoływane, gdy</span><span class="sxs-lookup"><span data-stu-id="127ca-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="127ca-115">81</span><span class="sxs-lookup"><span data-stu-id="127ca-115">81</span></span>|<span data-ttu-id="127ca-116">Rozpocznie się rywalizację.</span><span class="sxs-lookup"><span data-stu-id="127ca-116">Contention starts.</span></span> <span data-ttu-id="127ca-117">To zdarzenie nie obejmuje ilości czasu nawirowania, zanim wątek czeka na uzyskanie blokady; jest uruchamiany tylko wtedy, gdy wątek czeka na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="127ca-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="127ca-118">91</span><span class="sxs-lookup"><span data-stu-id="127ca-118">91</span></span>|<span data-ttu-id="127ca-119">Zakończyło się rywalizację.</span><span class="sxs-lookup"><span data-stu-id="127ca-119">Contention ends.</span></span>|

<span data-ttu-id="127ca-120">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="127ca-120">The following table shows event data:</span></span>

|<span data-ttu-id="127ca-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="127ca-121">Field name</span></span>|<span data-ttu-id="127ca-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="127ca-122">Data type</span></span>|<span data-ttu-id="127ca-123">Opis</span><span class="sxs-lookup"><span data-stu-id="127ca-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="127ca-124">Flagi</span><span class="sxs-lookup"><span data-stu-id="127ca-124">Flags</span></span>|<span data-ttu-id="127ca-125">win: UInt8</span><span class="sxs-lookup"><span data-stu-id="127ca-125">win:UInt8</span></span>|<span data-ttu-id="127ca-126">0 dla zarządzanych; 1 w przypadku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="127ca-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="127ca-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="127ca-127">ClrInstanceID</span></span>|<span data-ttu-id="127ca-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="127ca-128">win:UInt16</span></span>|<span data-ttu-id="127ca-129">Unikatowy identyfikator wystąpienia środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="127ca-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="127ca-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="127ca-130">See also</span></span>

- [<span data-ttu-id="127ca-131">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="127ca-131">CLR ETW Events</span></span>](clr-etw-events.md)
