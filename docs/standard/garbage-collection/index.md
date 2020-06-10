---
title: Zbieranie elementów bezużytecznych platformy .NET
description: Informacje o odzyskiwaniu elementów bezużytecznych w programie .NET. Moduł zbierający elementy bezużyteczne platformy .NET zarządza alokacją i ilością pamięci dla aplikacji.
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662488"
---
# <a name="garbage-collection"></a><span data-ttu-id="faf60-104">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="faf60-104">Garbage collection</span></span>

<span data-ttu-id="faf60-105">. Moduł wyrzucania elementów bezużytecznych sieci zarządza alokacją i ilością pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faf60-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="faf60-106">Zawsze podczas tworzenia nowego obiektu środowisko uruchomieniowe języka wspólnego przydziela pamięć dla obiektu z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="faf60-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="faf60-107">Tak długo, jak przestrzeń adresowa jest dostępna w zarządzanym stosie, środowisko wykonawcze w dalszym ciągu przydziela miejsce dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="faf60-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="faf60-108">Jednak pamięć nie jest nieskończona.</span><span class="sxs-lookup"><span data-stu-id="faf60-108">However, memory is not infinite.</span></span> <span data-ttu-id="faf60-109">Ostatecznie moduł zbierający elementy bezużyteczne musi wykonać kolekcję w celu zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="faf60-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="faf60-110">Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały.</span><span class="sxs-lookup"><span data-stu-id="faf60-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="faf60-111">Gdy moduł zbierający elementy bezużyteczne wykonuje kolekcję, sprawdza czy istnieją obiekty na zarządzanym stosie, które nie są już używane przez aplikację, i wykonuje niezbędne operacje do odzyskania ich pamięci.</span><span class="sxs-lookup"><span data-stu-id="faf60-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="faf60-112">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="faf60-112">In this section</span></span>
  
|<span data-ttu-id="faf60-113">Tytuł</span><span class="sxs-lookup"><span data-stu-id="faf60-113">Title</span></span>|<span data-ttu-id="faf60-114">Opis</span><span class="sxs-lookup"><span data-stu-id="faf60-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="faf60-115">Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="faf60-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="faf60-116">Opisuje jak działa wyrzucanie elementów bezużytecznych, jak obiekty są przydzielane na zarządzanym stosie oraz inne podstawowe pojęcia.</span><span class="sxs-lookup"><span data-stu-id="faf60-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="faf60-117">Stacja robocza i odzyskiwanie pamięci serwera</span><span class="sxs-lookup"><span data-stu-id="faf60-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="faf60-118">Opisuje różnice między odzyskiwaniem pamięci stacji roboczej dla aplikacji klienckich i odzyskiwania pamięci serwera dla aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="faf60-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="faf60-119">Odzyskiwanie pamięci w tle</span><span class="sxs-lookup"><span data-stu-id="faf60-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="faf60-120">Opisuje wyrzucanie elementów bezużytecznych w tle, czyli zbieranie obiektów generacji 0 i 1, gdy kolekcja generacji 2 jest w toku.</span><span class="sxs-lookup"><span data-stu-id="faf60-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="faf60-121">Sterta obiektów wielkich</span><span class="sxs-lookup"><span data-stu-id="faf60-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="faf60-122">Opisuje stertę dużego obiektu (LOH) i sposób, w jaki duże obiekty są zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="faf60-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="faf60-123">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="faf60-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="faf60-124">Opisuje testy wydajności, które można użyć do diagnozowania problemów z wydajnością wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="faf60-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="faf60-125">Wywołane kolekcje</span><span class="sxs-lookup"><span data-stu-id="faf60-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="faf60-126">Opisuje, jak sprawić, aby nastąpiło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="faf60-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="faf60-127">Tryby opóźnienia</span><span class="sxs-lookup"><span data-stu-id="faf60-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="faf60-128">Opisuje tryby, które określają ingerencję operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="faf60-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="faf60-129">Optymalizacja udostępnionej usługi hostingu internetowego</span><span class="sxs-lookup"><span data-stu-id="faf60-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="faf60-130">Opisuje, jak zoptymalizować wyrzucanie elementów bezużytecznych na serwerach współużytkowanych przez kilka małych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="faf60-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="faf60-131">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="faf60-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="faf60-132">Opisuje, jak określić kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zostało ono ukończone.</span><span class="sxs-lookup"><span data-stu-id="faf60-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="faf60-133">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="faf60-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="faf60-134">Opisuje, jak monitorować wykorzystanie procesora i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="faf60-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="faf60-135">Słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="faf60-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="faf60-136">Opisuje funkcje, które pozwalają modułowi zbierającemu elementy bezużyteczne na zbieranie obiektu, wciąż zezwalając aplikacjom na dostęp do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="faf60-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="faf60-137">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="faf60-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="faf60-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf60-138">See also</span></span>

- [<span data-ttu-id="faf60-139">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="faf60-139">Clean up unmanaged resources</span></span>](unmanaged.md)
