---
title: Wyrzucanie elementów bezużytecznych .NET
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
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102245"
---
# <a name="garbage-collection"></a><span data-ttu-id="89679-102">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="89679-102">Garbage collection</span></span>

<span data-ttu-id="89679-103">. Moduł zbierający elementy bezużyteczne net zarządza alokacji i wydania pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="89679-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="89679-104">Zawsze podczas tworzenia nowego obiektu środowisko uruchomieniowe języka wspólnego przydziela pamięć dla obiektu z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="89679-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="89679-105">Tak długo, jak przestrzeń adresowa jest dostępna w zarządzanym stosie, środowisko wykonawcze w dalszym ciągu przydziela miejsce dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="89679-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="89679-106">Jednak pamięć nie jest nieskończona.</span><span class="sxs-lookup"><span data-stu-id="89679-106">However, memory is not infinite.</span></span> <span data-ttu-id="89679-107">Ostatecznie moduł zbierający elementy bezużyteczne musi wykonać kolekcję w celu zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="89679-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="89679-108">Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały.</span><span class="sxs-lookup"><span data-stu-id="89679-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="89679-109">Gdy moduł zbierający elementy bezużyteczne wykonuje kolekcję, sprawdza czy istnieją obiekty na zarządzanym stosie, które nie są już używane przez aplikację, i wykonuje niezbędne operacje do odzyskania ich pamięci.</span><span class="sxs-lookup"><span data-stu-id="89679-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89679-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="89679-110">In this section</span></span>
  
|<span data-ttu-id="89679-111">Tytuł</span><span class="sxs-lookup"><span data-stu-id="89679-111">Title</span></span>|<span data-ttu-id="89679-112">Opis</span><span class="sxs-lookup"><span data-stu-id="89679-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="89679-113">Podstawy wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="89679-113">Fundamentals of garbage collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="89679-114">Opisuje jak działa wyrzucanie elementów bezużytecznych, jak obiekty są przydzielane na zarządzanym stosie oraz inne podstawowe pojęcia.</span><span class="sxs-lookup"><span data-stu-id="89679-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="89679-115">Wyrzucanie elementów bezużytecznych stacji roboczych i serwera</span><span class="sxs-lookup"><span data-stu-id="89679-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="89679-116">W tym artykule opisano różnice między wyrzucania elementów bezużytecznych stacji roboczej dla aplikacji klienckich i wyrzucania elementów bezużytecznych serwera dla aplikacji serwera.</span><span class="sxs-lookup"><span data-stu-id="89679-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="89679-117">Wyrzucanie elementów bezużytecznych w tle</span><span class="sxs-lookup"><span data-stu-id="89679-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="89679-118">W tym artykule opisano wyrzucania elementów bezużytecznych tła, który jest kolekcji generacji 0 i 1 obiektów, podczas gdy kolekcja generacji 2 jest w toku.</span><span class="sxs-lookup"><span data-stu-id="89679-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="89679-119">Sterta dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="89679-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="89679-120">Opisuje sterty dużych obiektów (LOH) i jak duże obiekty są zbierane śmieci.</span><span class="sxs-lookup"><span data-stu-id="89679-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="89679-121">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="89679-121">Garbage collection and performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="89679-122">Opisuje testy wydajności, które można użyć do diagnozowania problemów z wydajnością wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="89679-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="89679-123">Wywołane kolekcje</span><span class="sxs-lookup"><span data-stu-id="89679-123">Induced collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="89679-124">Opisuje, jak sprawić, aby nastąpiło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="89679-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="89679-125">Tryby opóźnienia</span><span class="sxs-lookup"><span data-stu-id="89679-125">Latency modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="89679-126">Opisuje tryby, które określają ingerencję operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="89679-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="89679-127">Optymalizacja udostępnionej usługi hostingu internetowego</span><span class="sxs-lookup"><span data-stu-id="89679-127">Optimization for shared web hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="89679-128">Opisuje, jak zoptymalizować wyrzucanie elementów bezużytecznych na serwerach współużytkowanych przez kilka małych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="89679-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="89679-129">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="89679-129">Garbage collection notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="89679-130">Opisuje, jak określić kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zostało ono ukończone.</span><span class="sxs-lookup"><span data-stu-id="89679-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="89679-131">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="89679-131">Application domain resource monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="89679-132">Opisuje, jak monitorować wykorzystanie procesora i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="89679-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="89679-133">Słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="89679-133">Weak references</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="89679-134">Opisuje funkcje, które pozwalają modułowi zbierającemu elementy bezużyteczne na zbieranie obiektu, wciąż zezwalając aplikacjom na dostęp do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="89679-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="89679-135">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="89679-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="89679-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89679-136">See also</span></span>

- [<span data-ttu-id="89679-137">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="89679-137">Clean up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
