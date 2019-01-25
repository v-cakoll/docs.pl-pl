---
title: Zdarzenia rywalizacji ETW — .NET
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 95f56a6c8b51c58ed36d5d0de428bf57b728009c
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857648"
---
# <a name="contention-etw-events"></a><span data-ttu-id="a0857-102">Zdarzenia rywalizacji ETW</span><span class="sxs-lookup"><span data-stu-id="a0857-102">Contention ETW events</span></span>

<span data-ttu-id="a0857-103">Zdarzenia rywalizacji o zasoby są wywoływane zawsze wtedy, gdy istnieje rywalizacji o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokad lub natywnych blokady używany przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="a0857-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="a0857-104">Rywalizacji występuje, gdy wątek jest oczekiwanie na blokadę, podczas gdy inny wątek posiada blokadę.</span><span class="sxs-lookup"><span data-stu-id="a0857-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>

<span data-ttu-id="a0857-105">W poniższej tabeli przedstawiono — słowo kluczowe, w którym są generowane zdarzenia rywalizacji o zasoby i poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a0857-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="a0857-106">Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="a0857-106">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="a0857-107">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a0857-107">Keyword for raising the event</span></span>|<span data-ttu-id="a0857-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="a0857-108">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="a0857-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="a0857-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="a0857-110">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="a0857-110">Informational (4)</span></span>|

<span data-ttu-id="a0857-111">W poniższej tabeli przedstawiono informacje o zdarzeniach:</span><span class="sxs-lookup"><span data-stu-id="a0857-111">The following table shows event information:</span></span>

|<span data-ttu-id="a0857-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="a0857-112">Event</span></span>|<span data-ttu-id="a0857-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a0857-113">Event ID</span></span>|<span data-ttu-id="a0857-114">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="a0857-114">Raised when</span></span>|
|-----------|--------------|-----------------|
|`ContentionStart_V1`|<span data-ttu-id="a0857-115">81</span><span class="sxs-lookup"><span data-stu-id="a0857-115">81</span></span>|<span data-ttu-id="a0857-116">Rozpoczyna się rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="a0857-116">Contention starts.</span></span> <span data-ttu-id="a0857-117">To zdarzenie nie zawiera ilość obrotowych czas, po którym wątek czeka na uzyskanie blokady; jest zgłaszany tylko wtedy, gdy wątek czeka na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="a0857-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|
|`ContentionStop`|<span data-ttu-id="a0857-118">91</span><span class="sxs-lookup"><span data-stu-id="a0857-118">91</span></span>|<span data-ttu-id="a0857-119">Kończy się rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="a0857-119">Contention ends.</span></span>|

<span data-ttu-id="a0857-120">W poniższej tabeli przedstawiono dane zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="a0857-120">The following table shows event data:</span></span>

|<span data-ttu-id="a0857-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="a0857-121">Field name</span></span>|<span data-ttu-id="a0857-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="a0857-122">Data type</span></span>|<span data-ttu-id="a0857-123">Opis</span><span class="sxs-lookup"><span data-stu-id="a0857-123">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="a0857-124">Flagi</span><span class="sxs-lookup"><span data-stu-id="a0857-124">Flags</span></span>|<span data-ttu-id="a0857-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="a0857-125">win:UInt8</span></span>|<span data-ttu-id="a0857-126">0 w przypadku zarządzanych; 1 w przypadku natywnych.</span><span class="sxs-lookup"><span data-stu-id="a0857-126">0 for managed; 1 for native.</span></span>|
|<span data-ttu-id="a0857-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a0857-127">ClrInstanceID</span></span>|<span data-ttu-id="a0857-128">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="a0857-128">win:UInt16</span></span>|<span data-ttu-id="a0857-129">Unikatowy identyfikator wystąpienia CLR.</span><span class="sxs-lookup"><span data-stu-id="a0857-129">Unique ID for the instance of CLR.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a0857-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0857-130">See also</span></span>

- [<span data-ttu-id="a0857-131">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="a0857-131">CLR ETW Events</span></span>](clr-etw-events.md)
