---
title: Zdarzenia rywalizacji ETW
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575570"
---
# <a name="contention-etw-events"></a><span data-ttu-id="d60c2-102">Zdarzenia rywalizacji ETW</span><span class="sxs-lookup"><span data-stu-id="d60c2-102">Contention ETW Events</span></span>
<span data-ttu-id="d60c2-103">Zdarzenia rywalizacji o zasoby są wywoływane zawsze wtedy, gdy istnieje rywalizacji o <xref:System.Threading.Monitor?displayProperty=nameWithType> blokad lub natywnych blokady używany przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d60c2-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="d60c2-104">Rywalizacji występuje, gdy wątek jest oczekiwanie na blokadę, podczas gdy inny wątek posiada blokadę.</span><span class="sxs-lookup"><span data-stu-id="d60c2-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="d60c2-105">W poniższej tabeli przedstawiono — słowo kluczowe, w którym są generowane zdarzenia rywalizacji o zasoby i poziom zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d60c2-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="d60c2-106">(Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="d60c2-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="d60c2-107">Słowo kluczowe dla podnoszonego zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d60c2-107">Keyword for raising the event</span></span>|<span data-ttu-id="d60c2-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="d60c2-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="d60c2-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="d60c2-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="d60c2-110">Komunikat informacyjny (4)</span><span class="sxs-lookup"><span data-stu-id="d60c2-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="d60c2-111">W poniższej tabeli przedstawiono informacje o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="d60c2-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="d60c2-112">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d60c2-112">Event</span></span>|<span data-ttu-id="d60c2-113">Identyfikator zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d60c2-113">Event ID</span></span>|<span data-ttu-id="d60c2-114">Wywołane, gdy</span><span class="sxs-lookup"><span data-stu-id="d60c2-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="d60c2-115">81</span><span class="sxs-lookup"><span data-stu-id="d60c2-115">81</span></span>|<span data-ttu-id="d60c2-116">Rozpoczyna się rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="d60c2-116">Contention starts.</span></span> <span data-ttu-id="d60c2-117">To zdarzenie nie zawiera ilość obrotowych czas, po którym wątek czeka na uzyskanie blokady; jest zgłaszany tylko wtedy, gdy wątek czeka na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="d60c2-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="d60c2-118">81</span><span class="sxs-lookup"><span data-stu-id="d60c2-118">81</span></span>|<span data-ttu-id="d60c2-119">Kończy się rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="d60c2-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="d60c2-120">W poniższej tabeli przedstawiono dane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d60c2-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="d60c2-121">Nazwa pola</span><span class="sxs-lookup"><span data-stu-id="d60c2-121">Field name</span></span>|<span data-ttu-id="d60c2-122">Typ danych</span><span class="sxs-lookup"><span data-stu-id="d60c2-122">Data type</span></span>|<span data-ttu-id="d60c2-123">Opis</span><span class="sxs-lookup"><span data-stu-id="d60c2-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="d60c2-124">Flagi</span><span class="sxs-lookup"><span data-stu-id="d60c2-124">Flags</span></span>|<span data-ttu-id="d60c2-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="d60c2-125">win:UInt8</span></span>|<span data-ttu-id="d60c2-126">0 w przypadku zarządzanych; 1 w przypadku natywnych.</span><span class="sxs-lookup"><span data-stu-id="d60c2-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="d60c2-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="d60c2-127">ClrInstanceID</span></span>|<span data-ttu-id="d60c2-128">win: UInt16.</span><span class="sxs-lookup"><span data-stu-id="d60c2-128">win:UInt16</span></span>|<span data-ttu-id="d60c2-129">Unikatowy identyfikator wystąpienia CLR.</span><span class="sxs-lookup"><span data-stu-id="d60c2-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d60c2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d60c2-130">See also</span></span>
- [<span data-ttu-id="d60c2-131">Zdarzenia CLR ETW</span><span class="sxs-lookup"><span data-stu-id="d60c2-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
