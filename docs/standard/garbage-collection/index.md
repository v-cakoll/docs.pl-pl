---
title: "Odzyskiwanie pamięci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "36"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c8288473b25b3f3cd75666e1da0611dec37c3127
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="garbage-collection"></a><span data-ttu-id="e52bd-102">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="e52bd-102">Garbage Collection</span></span>
<span data-ttu-id="e52bd-103">. Moduł zbierający elementy bezużyteczne w NET zarządza alokacji i wersji pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e52bd-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="e52bd-104">Zawsze podczas tworzenia nowego obiektu środowisko uruchomieniowe języka wspólnego przydziela pamięć dla obiektu z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="e52bd-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="e52bd-105">Tak długo, jak przestrzeń adresowa jest dostępna w zarządzanym stosie, środowisko wykonawcze w dalszym ciągu przydziela miejsce dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="e52bd-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="e52bd-106">Jednak pamięć nie jest nieskończona.</span><span class="sxs-lookup"><span data-stu-id="e52bd-106">However, memory is not infinite.</span></span> <span data-ttu-id="e52bd-107">Ostatecznie moduł zbierający elementy bezużyteczne musi wykonać kolekcję w celu zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="e52bd-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="e52bd-108">Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały.</span><span class="sxs-lookup"><span data-stu-id="e52bd-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="e52bd-109">Gdy moduł zbierający elementy bezużyteczne wykonuje kolekcję, sprawdza czy istnieją obiekty na zarządzanym stosie, które nie są już używane przez aplikację, i wykonuje niezbędne operacje do odzyskania ich pamięci.</span><span class="sxs-lookup"><span data-stu-id="e52bd-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="e52bd-110">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="e52bd-110">Related Topics</span></span>  
  
|<span data-ttu-id="e52bd-111">Tytuł</span><span class="sxs-lookup"><span data-stu-id="e52bd-111">Title</span></span>|<span data-ttu-id="e52bd-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e52bd-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e52bd-113">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="e52bd-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="e52bd-114">Opisuje jak działa wyrzucanie elementów bezużytecznych, jak obiekty są przydzielane na zarządzanym stosie oraz inne podstawowe pojęcia.</span><span class="sxs-lookup"><span data-stu-id="e52bd-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="e52bd-115">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="e52bd-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="e52bd-116">Opisuje testy wydajności, które można użyć do diagnozowania problemów z wydajnością wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e52bd-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="e52bd-117">Wywołane kolekcje</span><span class="sxs-lookup"><span data-stu-id="e52bd-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="e52bd-118">Opisuje, jak sprawić, aby nastąpiło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e52bd-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="e52bd-119">Tryby opóźnienia</span><span class="sxs-lookup"><span data-stu-id="e52bd-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="e52bd-120">Opisuje tryby, które określają ingerencję operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e52bd-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="e52bd-121">Optymalizacja udostępnionej usługi hostingu internetowego</span><span class="sxs-lookup"><span data-stu-id="e52bd-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="e52bd-122">Opisuje, jak zoptymalizować wyrzucanie elementów bezużytecznych na serwerach współużytkowanych przez kilka małych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e52bd-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="e52bd-123">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="e52bd-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="e52bd-124">Opisuje, jak określić kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zostało ono ukończone.</span><span class="sxs-lookup"><span data-stu-id="e52bd-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="e52bd-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="e52bd-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="e52bd-126">Opisuje, jak monitorować wykorzystanie procesora i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e52bd-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="e52bd-127">Słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="e52bd-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="e52bd-128">Opisuje funkcje, które pozwalają modułowi zbierającemu elementy bezużyteczne na zbieranie obiektu, wciąż zezwalając aplikacjom na dostęp do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e52bd-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="e52bd-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e52bd-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="e52bd-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e52bd-130">See Also</span></span>  
 [<span data-ttu-id="e52bd-131">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="e52bd-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
