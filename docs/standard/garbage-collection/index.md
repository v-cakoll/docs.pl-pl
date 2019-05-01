---
title: Odzyskiwanie pamięci
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1f61b63f78ea3c6131d4d1ab4e421be25149035b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931536"
---
# <a name="garbage-collection"></a><span data-ttu-id="1af76-102">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="1af76-102">Garbage Collection</span></span>
<span data-ttu-id="1af76-103">. Moduł wyrzucania elementów bezużytecznych dla NET zarządza alokacją i zwolnieniem pamięci dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1af76-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="1af76-104">Zawsze podczas tworzenia nowego obiektu środowisko uruchomieniowe języka wspólnego przydziela pamięć dla obiektu z zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="1af76-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="1af76-105">Tak długo, jak przestrzeń adresowa jest dostępna w zarządzanym stosie, środowisko wykonawcze w dalszym ciągu przydziela miejsce dla nowych obiektów.</span><span class="sxs-lookup"><span data-stu-id="1af76-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="1af76-106">Jednak pamięć nie jest nieskończona.</span><span class="sxs-lookup"><span data-stu-id="1af76-106">However, memory is not infinite.</span></span> <span data-ttu-id="1af76-107">Ostatecznie moduł zbierający elementy bezużyteczne musi wykonać kolekcję w celu zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="1af76-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="1af76-108">Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały.</span><span class="sxs-lookup"><span data-stu-id="1af76-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="1af76-109">Gdy moduł zbierający elementy bezużyteczne wykonuje kolekcję, sprawdza czy istnieją obiekty na zarządzanym stosie, które nie są już używane przez aplikację, i wykonuje niezbędne operacje do odzyskania ich pamięci.</span><span class="sxs-lookup"><span data-stu-id="1af76-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="1af76-110">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="1af76-110">Related Topics</span></span>  
  
|<span data-ttu-id="1af76-111">Tytuł</span><span class="sxs-lookup"><span data-stu-id="1af76-111">Title</span></span>|<span data-ttu-id="1af76-112">Opis</span><span class="sxs-lookup"><span data-stu-id="1af76-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1af76-113">Podstawy dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="1af76-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="1af76-114">Opisuje jak działa wyrzucanie elementów bezużytecznych, jak obiekty są przydzielane na zarządzanym stosie oraz inne podstawowe pojęcia.</span><span class="sxs-lookup"><span data-stu-id="1af76-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="1af76-115">Odzyskiwanie pamięci i wydajność</span><span class="sxs-lookup"><span data-stu-id="1af76-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="1af76-116">Opisuje testy wydajności, które można użyć do diagnozowania problemów z wydajnością wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1af76-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="1af76-117">Wywołane kolekcje</span><span class="sxs-lookup"><span data-stu-id="1af76-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="1af76-118">Opisuje, jak sprawić, aby nastąpiło wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1af76-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="1af76-119">Tryby opóźnienia</span><span class="sxs-lookup"><span data-stu-id="1af76-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="1af76-120">Opisuje tryby, które określają ingerencję operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1af76-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="1af76-121">Optymalizacja udostępnionej usługi hostingu internetowego</span><span class="sxs-lookup"><span data-stu-id="1af76-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="1af76-122">Opisuje, jak zoptymalizować wyrzucanie elementów bezużytecznych na serwerach współużytkowanych przez kilka małych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1af76-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="1af76-123">Powiadomienia dotyczące odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="1af76-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="1af76-124">Opisuje, jak określić kiedy zbliża się pełne wyrzucanie elementów bezużytecznych i kiedy zostało ono ukończone.</span><span class="sxs-lookup"><span data-stu-id="1af76-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="1af76-125">Monitorowanie zasobów domen aplikacji</span><span class="sxs-lookup"><span data-stu-id="1af76-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="1af76-126">Opisuje, jak monitorować wykorzystanie procesora i pamięci przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1af76-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="1af76-127">Słabe odwołania</span><span class="sxs-lookup"><span data-stu-id="1af76-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="1af76-128">Opisuje funkcje, które pozwalają modułowi zbierającemu elementy bezużyteczne na zbieranie obiektu, wciąż zezwalając aplikacjom na dostęp do tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1af76-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="1af76-129">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="1af76-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="1af76-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1af76-130">See also</span></span>

- [<span data-ttu-id="1af76-131">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="1af76-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
