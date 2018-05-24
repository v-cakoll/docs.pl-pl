---
title: Sterty dużego obiektu w systemie Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: abb1f72a10a4aff448dea22b5c9415111c25eaab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="01523-102">Sterty dużego obiektu w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="01523-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="01523-103">Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiektów w małych i dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="01523-104">Gdy obiekt jest duży, niektóre z jego atrybutów stają się większe znaczenie niż Jeśli obiekt jest mała.</span><span class="sxs-lookup"><span data-stu-id="01523-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="01523-105">Na przykład kompaktowania — które skopiować go w innym miejscu pamięci sterty — może być kosztowne.</span><span class="sxs-lookup"><span data-stu-id="01523-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="01523-106">W związku z tym moduł zbierający elementy bezużyteczne .NET umieszcza dużych obiektów na stercie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="01523-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="01523-107">W tym temacie wyjaśniono sterty dużego obiektu szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="01523-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="01523-108">Omówiono co kwalifikuje obiektu jako obiektu dużych, jak te duże obiekty są zbierane i nałożyć rodzaj wydajności wpływ dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01523-109">W tym temacie omówiono sterty dużego obiektu w .NET Framework i .NET Core uruchomiony tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="01523-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="01523-110">Nie obejmuje LOH systemem implementacje .NET na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="01523-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="01523-111">Jak obiekt kończy się na sterty dużego obiektu i jak GC je obsługuje</span><span class="sxs-lookup"><span data-stu-id="01523-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="01523-112">Jeśli obiekt jest większa niż lub równa 85,000 bajtów, uwzględniono dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-112">If an object is greater than or equal to 85,000 bytes, it’s considered a large object.</span></span> <span data-ttu-id="01523-113">Ten numer został ustaleniami dostrajania wydajności.</span><span class="sxs-lookup"><span data-stu-id="01523-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="01523-114">Gdy żądanie alokacji obiektu jest 85,000 lub więcej bajtów, środowisko uruchomieniowe przydziela na sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="01523-115">Aby zrozumieć, co to znaczy, warto zbadać niektóre podstawowe założenia dotyczące odzyskiwania pamięci platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="01523-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="01523-116">Moduł zbierający elementy bezużyteczne .NET jest pokoleniowej modułu zbierającego.</span><span class="sxs-lookup"><span data-stu-id="01523-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="01523-117">Ma trzy generacje: pokolenia 0, generację 1 i generacji 2.</span><span class="sxs-lookup"><span data-stu-id="01523-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="01523-118">Powodem generacje 3 jest fakt, że w dobrze Zaczekaj aplikacji, większość struktury obiektów w gen0.</span><span class="sxs-lookup"><span data-stu-id="01523-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="01523-119">Na przykład w aplikacji serwera, alokacji skojarzone z każdym żądaniem powinien die po zakończeniu żądania.</span><span class="sxs-lookup"><span data-stu-id="01523-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="01523-120">Żądań alokacji locie będzie przekształcić gen1 i die istnieje.</span><span class="sxs-lookup"><span data-stu-id="01523-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="01523-121">Zasadniczo gen1 pełni rolę bufora między obszarów małych obiektów i długotrwałe obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="01523-122">Małych obiektów są zawsze przydzielana podczas generowania 0 i, w zależności od ich istnienia może funkcjonować jako generacji 1 czy generation2.</span><span class="sxs-lookup"><span data-stu-id="01523-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="01523-123">Duże obiekty są zawsze przydzielana podczas generowania 2.</span><span class="sxs-lookup"><span data-stu-id="01523-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="01523-124">Duże obiekty należą do generacji 2, ponieważ są one pobierane tylko podczas zbierania generacji 2.</span><span class="sxs-lookup"><span data-stu-id="01523-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="01523-125">Podczas zbierania generacji jego młodszych generation(s) są także pobierane.</span><span class="sxs-lookup"><span data-stu-id="01523-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="01523-126">Na przykład w przypadku odzyskiwania pamięci generacji 1 są zbierane zarówno generacji 1 i 0.</span><span class="sxs-lookup"><span data-stu-id="01523-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="01523-127">A w przypadku odzyskiwania pamięci generacji 2 są zbierane całego stosu.</span><span class="sxs-lookup"><span data-stu-id="01523-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="01523-128">Z tego powodu GC generacji 2 jest również nazywany *pełne GC*.</span><span class="sxs-lookup"><span data-stu-id="01523-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="01523-129">Ten artykuł dotyczy generacji 2 GC zamiast pełną operacją GC, ale warunki są wymienne.</span><span class="sxs-lookup"><span data-stu-id="01523-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="01523-130">Generacje Podaj widok logiczny stercie GC.</span><span class="sxs-lookup"><span data-stu-id="01523-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="01523-131">Fizycznie obiektów na żywo w segmentach sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="01523-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="01523-132">A *segmentu sterty zarządzanej* to fragment, pamięci, która GC rezerwuje z systemu operacyjnego przez wywołanie metody [funkcji VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) imieniu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="01523-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) on behalf of managed code.</span></span> <span data-ttu-id="01523-133">Podczas ładowania CLR GC przydziela dwa segmenty początkowej sterty: jeden dla małych obiektów (małe sterty obiektów, lub raportu o kondycji) i jeden dla dużych obiektów (sterty obiektów wielkich).</span><span class="sxs-lookup"><span data-stu-id="01523-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the Small Object Heap, or SOH), and one for large objects (the Large Object Heap).</span></span>

<span data-ttu-id="01523-134">Alokacja żądań następnie są spełnione przez umieszczenie zarządzanych obiektów na te segmenty sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="01523-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="01523-135">Jeśli obiekt jest mniejszy niż 85,000 bajtów, jest on umieszczany w segmencie dla raportu o kondycji; w przeciwnym razie jest umieszczany w segmencie LOH.</span><span class="sxs-lookup"><span data-stu-id="01523-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="01523-136">Segmenty są zatwierdzone (w mniejsze fragmenty) jako więcej i więcej obiektów są przydzielone do nich.</span><span class="sxs-lookup"><span data-stu-id="01523-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="01523-137">Dla raportu o kondycji obiekty, które pozostają aktualne po wykaz Globalny są awansowane do nowej generacji.</span><span class="sxs-lookup"><span data-stu-id="01523-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="01523-138">Obiekty, które pozostają aktualne po kolekcji pokolenia 0, teraz są traktowane jako obiekty generacji 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="01523-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="01523-139">Obiekty, które pozostają aktualne po najstarsze generowania nadal są uwzględniane w najstarsze generacji.</span><span class="sxs-lookup"><span data-stu-id="01523-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="01523-140">Innymi słowy przy życiu z generacji 2 są obiekty generacji 2; i przy życiu z LOH są obiekty LOH, (które są pobierane z gen2).</span><span class="sxs-lookup"><span data-stu-id="01523-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span> 

<span data-ttu-id="01523-141">Kod użytkownika można alokować podczas generowania 0 (małych obiektów) lub LOH (duże obiekty).</span><span class="sxs-lookup"><span data-stu-id="01523-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="01523-142">Tylko GC "alokowania" obiektów podczas generowania 1 (przez podwyższania poziomu przy życiu z pokolenia 0) i 2 (przez podwyższania poziomu przy życiu z pokolenia 1 i 2).</span><span class="sxs-lookup"><span data-stu-id="01523-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="01523-143">Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi za pośrednictwem obiektów na żywo i kompaktowanie je.</span><span class="sxs-lookup"><span data-stu-id="01523-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="01523-144">Jednak ponieważ kompaktowanie jest kosztowna, GC *wachlarzy* LOH; ułatwia wolnego listy poza martwy obiektów, które mogą być ponownie używane później do spełnienia żądań alokacji dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="01523-145">Sąsiadujących ze sobą obiektów martwy są wprowadzane do jednego obiektu wolne.</span><span class="sxs-lookup"><span data-stu-id="01523-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="01523-146">Oprogramowanie .NET core i .NET Framework (począwszy od platformy .NET Framework 4.5.1) obejmują <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> właściwość, która umożliwia użytkownikom, aby określić, że LOH powinien kompaktowanie podczas następnego pełnego GC blokowania.</span><span class="sxs-lookup"><span data-stu-id="01523-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty="fullname"> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="01523-147">I w przyszłości, .NET mogą zdecydować skompaktować LOH automatycznie.</span><span class="sxs-lookup"><span data-stu-id="01523-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="01523-148">Oznacza to, że jeśli przydzielić duże obiekty i chce mieć pewność, że nie przenoś powinien nadal przypniesz je.</span><span class="sxs-lookup"><span data-stu-id="01523-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="01523-149">Rysunek 1 przedstawiono scenariusz, w którym GC formularzy generacji 1 po pierwszej generacji 0 GC gdzie `Obj1` i `Obj3` są martwy, a formularzy generacji 2 po pierwszej generacji 1 GC gdzie `Obj2` i `Obj5` jest martwy.</span><span class="sxs-lookup"><span data-stu-id="01523-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="01523-150">Należy zauważyć, że to i poniższe rysunki tylko w celach ilustracyjnych; zawierają one bardzo mało obiekty lepiej widoczne, co się dzieje na stosie.</span><span class="sxs-lookup"><span data-stu-id="01523-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="01523-151">W rzeczywistości wiele innych obiektów są zazwyczaj wynikiem wykazem Globalnym.</span><span class="sxs-lookup"><span data-stu-id="01523-151">In reality, many more objects are typically involved in a GC.</span></span>

![Rysunek 1: Operacja gen 0 GC i operacji gen 1 GC](media/loh/loh-figure-1.jpg)   
<span data-ttu-id="01523-153">Rysunek 1: Generacji 0 i GC generacji 1.</span><span class="sxs-lookup"><span data-stu-id="01523-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="01523-154">Rysunek 2 wskazuje, że po GC generacji 2 który był wyświetlany, który `Obj1` i `Obj2` są martwy GC stanowi ciągły wolnego miejsca, za mało pamięci, używany jest zajmowany przez `Obj1` i `Obj2`, który następnie został użyty do spełnienia żądań alokacji Aby uzyskać `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="01523-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="01523-155">Ilość miejsca po ostatni obiekt `Obj3`, do końca segmentu mogą służyć do spełnienia żądań alokacji.</span><span class="sxs-lookup"><span data-stu-id="01523-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>
 
![Rysunek 2: po operacji gen 2 GC](media/loh/loh-figure-2.jpg)  
<span data-ttu-id="01523-157">Rysunek 2: po GC generacji 2</span><span class="sxs-lookup"><span data-stu-id="01523-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="01523-158">Jeśli nie ma wystarczająco dużo wolnego miejsca do dużego obiektu żądań alokacji, wykaz Globalny najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01523-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="01523-159">W przypadku niepowodzenia wyzwala odzyskiwania pamięci generacji 2 w mamy nadzieję, że z zwolnić miejsce.</span><span class="sxs-lookup"><span data-stu-id="01523-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="01523-160">Podczas generacji 1 czy generacji 2 GC, moduł zbierający elementy bezużyteczne zwalnia segmentów, które ma żadnych obiektów na żywo na ich do systemu operacyjnego przez wywołanie metody [funkcja VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="01523-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx).</span></span> <span data-ttu-id="01523-161">Ilość miejsca po ostatni obiekt na żywo na końcu segmentu jest anulowane (z wyjątkiem w segmencie tymczasowych, gdy gen0/gen1 na żywo, a gdy moduł garbage collector zachować niektóre zatwierdzone, ponieważ aplikacja będzie przydziału w nim od razu).</span><span class="sxs-lookup"><span data-stu-id="01523-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="01523-162">I wolnego miejsca do pozostać zatwierdzone, że są one resetowane, co oznacza system operacyjny nie musi zapisywać dane w ich do dysku.</span><span class="sxs-lookup"><span data-stu-id="01523-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="01523-163">Ponieważ LOH są zbierane podczas generowania 2 GC, LOH segment można zwolnić tylko podczas operacji GC.</span><span class="sxs-lookup"><span data-stu-id="01523-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="01523-164">Rysunek 3 przedstawia scenariusz, w której moduł zbierający elementy bezużyteczne zwalnia jednego segmentu (segment 2) do systemu operacyjnego i decommits więcej miejsca na pozostałe segmenty.</span><span class="sxs-lookup"><span data-stu-id="01523-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="01523-165">Jeśli musi używać anulowane miejsca na końcu segmentu do spełnienia żądań alokacji dużego obiektu, jego zatwierdza pamięć ponownie.</span><span class="sxs-lookup"><span data-stu-id="01523-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="01523-166">(Opis commit/zrzeka się w dokumentacji dla [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="01523-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx).</span></span>
 
![Rysunek 3: LOH po operacji gen 2 GC](media/loh/loh-figure-3.jpg)  
<span data-ttu-id="01523-168">Rysunek 3: LOH po GC generacji 2</span><span class="sxs-lookup"><span data-stu-id="01523-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="01523-169">Gdy są zbierane dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="01523-169">When is a large object collected?</span></span>

<span data-ttu-id="01523-170">Ogólnie rzecz biorąc GC występuje, gdy jedna z następujących warunków 3 następujących sytuacji:</span><span class="sxs-lookup"><span data-stu-id="01523-170">In general, a GC occurs when one of the following following 3 conditions happens:</span></span>

- <span data-ttu-id="01523-171">Alokacja przekracza generacji 0 lub próg dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

   <span data-ttu-id="01523-172">Właściwość generacji jest wartość progową.</span><span class="sxs-lookup"><span data-stu-id="01523-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="01523-173">Próg generacji jest ustawiona, gdy moduł garbage collector przydziela obiektów do niej.</span><span class="sxs-lookup"><span data-stu-id="01523-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="01523-174">Po przekroczeniu progu wykaz Globalny jest wyzwalane w tej generacji.</span><span class="sxs-lookup"><span data-stu-id="01523-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="01523-175">Podczas alokowania małych i dużych obiektów można używać generacji 0 i progi LOH odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="01523-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="01523-176">Gdy moduł garbage collector przydziela do generacji 1 i 2, zużywa ich progów.</span><span class="sxs-lookup"><span data-stu-id="01523-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="01523-177">Tych progów są dopasowane dynamicznie, jak program będzie uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="01523-177">These thresholds are dynamically tuned as the program runs.</span></span>

   <span data-ttu-id="01523-178">To jest typową sytuacją; Większość GC się tak zdarzyć z powodu alokacje na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="01523-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="01523-179"><xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="01523-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

   <span data-ttu-id="01523-180">Jeśli bez parametrów <xref:System.GC.Collect?displayProperty=nameWithType> metoda jest wywoływana lub innego przeciążenia jest przekazywany <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument LOH są zbierane wraz z resztą sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="01523-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="01523-181">System jest w sytuacji braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="01523-181">The system is in low memory situation.</span></span>

   <span data-ttu-id="01523-182">Dzieje się tak, gdy moduł garbage collector otrzyma powiadomienie pamięci wysokiej z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01523-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="01523-183">Jeśli moduł zbierający elementy bezużyteczne sądzi, że podczas odzyskiwania pamięci generacji 2 nie będą produktywności, wyzwala jeden.</span><span class="sxs-lookup"><span data-stu-id="01523-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="01523-184">Wpływ na wydajność LOH</span><span class="sxs-lookup"><span data-stu-id="01523-184">LOH Performance Implications</span></span>

<span data-ttu-id="01523-185">Alokacje na stercie dużego obiektu wpływ na wydajność w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="01523-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="01523-186">Alokacja kosztów.</span><span class="sxs-lookup"><span data-stu-id="01523-186">Allocation cost.</span></span>

   <span data-ttu-id="01523-187">Środowisko CLR sprawia, że gwarancji czyszczeniu pamięci dla każdego nowego obiektu udostępnia.</span><span class="sxs-lookup"><span data-stu-id="01523-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="01523-188">Oznacza to, że koszt alokacji dużego obiektu całkowicie jest zdominowany przez pamięci wyczyszczenie (chyba że wyzwala wykaz Globalny).</span><span class="sxs-lookup"><span data-stu-id="01523-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="01523-189">Jeśli trwa cykli 2, aby wyczyścić jednego bajtu przyjmuje 170,000 cykle, aby wyczyścić najmniejszą dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="01523-190">Wyczyszczenie memmory obiektu 16MB na komputerze, 2GHz trwa około 16 ms.</span><span class="sxs-lookup"><span data-stu-id="01523-190">Clearing the memmory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="01523-191">To jest raczej dużych kosztów.</span><span class="sxs-lookup"><span data-stu-id="01523-191">That's a rather large cost.</span></span>

- <span data-ttu-id="01523-192">Kolekcja kosztów.</span><span class="sxs-lookup"><span data-stu-id="01523-192">Collection cost.</span></span>

   <span data-ttu-id="01523-193">Ponieważ LOH i generacji 2 są zbierane ze sobą, po przekroczeniu progu jednej firmy, zostanie wywołany kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="01523-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="01523-194">Jeśli generowania wyzwolenia kolekcji 2 z powodu LOH generacji 2 nie koniecznie znacznie mniejszy po GC.</span><span class="sxs-lookup"><span data-stu-id="01523-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="01523-195">Jeśli w generacji 2 nie jest dużą ilość danych, to ma minimalny wpływ.</span><span class="sxs-lookup"><span data-stu-id="01523-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="01523-196">Ale jeśli generacji 2 jest duży, może spowodować problemy z wydajnością, jeśli wiele GC generacji 2 są wyzwalane.</span><span class="sxs-lookup"><span data-stu-id="01523-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="01523-197">Jeśli wiele duże obiekty są przydzielane na bardzo tymczasowego i konieczne jest duża raportu o kondycji, może spędzać zbyt dużo czasu wykonywania wykazów globalnych.</span><span class="sxs-lookup"><span data-stu-id="01523-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="01523-198">Ponadto koszt alokacji można naprawdę sumują Jeśli zachowasz przydziału, dzięki czemu Przejdź naprawdę dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="01523-199">Elementy tablicy z typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="01523-199">Array elements with reference types.</span></span>

   <span data-ttu-id="01523-200">Bardzo dużych obiektów na LOH są zazwyczaj tablic (jest bardzo rzadko mają naprawdę dużego obiektu wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="01523-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="01523-201">W przypadku elementów tablicy odwołania bogate generuje koszt, który nie jest obecny, jeśli elementy nie są bogate odwołania.</span><span class="sxs-lookup"><span data-stu-id="01523-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="01523-202">Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie musi przechodzić przez tablicy na wszystkich.</span><span class="sxs-lookup"><span data-stu-id="01523-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="01523-203">Na przykład użycie tablicy do przechowywania węzłów w drzewie binarne jednym ze sposobów ją wdrożyć jest do odwoływania się do prawej i lewej węzła węzła za rzeczywiste węzłów:</span><span class="sxs-lookup"><span data-stu-id="01523-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      Node left;
      Node right;
   };

   Node[] binary_tr = new Node [num_nodes];
   ```

   <span data-ttu-id="01523-204">Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przechodzić przez co najmniej dwa odwołania dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="01523-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="01523-205">Informacje o innym podejściu ma indeks prawej i lewej węzłów magazynu:</span><span class="sxs-lookup"><span data-stu-id="01523-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

   ```csharp
   class Node
   {
      Data d;
      uint left_index;
      uint right_index;
   } ;
   ```

   <span data-ttu-id="01523-206">Zamiast odwołujących się po lewej stronie węzła dane jako `left.d`, możesz odwoływać się do niego jako `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="01523-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="01523-207">I nie trzeba przyjrzeć się wszystkie odwołania dla węzła lewy i prawy moduł garbage collector.</span><span class="sxs-lookup"><span data-stu-id="01523-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="01523-208">Poza trzech czynników dwa pierwsze są zazwyczaj większe znaczenie niż trzeci.</span><span class="sxs-lookup"><span data-stu-id="01523-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="01523-209">W związku z tym zaleca się przydzielenie puli dużych obiektów, które można ponownie użyć zamiast przydzielania czasowe.</span><span class="sxs-lookup"><span data-stu-id="01523-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span> 

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="01523-210">Zbieranie danych o wydajności dla LOH</span><span class="sxs-lookup"><span data-stu-id="01523-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="01523-211">Aby zebrać dane wydajności dla określonego obszaru, użytkownik powinien już zostały wykonane następujące:</span><span class="sxs-lookup"><span data-stu-id="01523-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="01523-212">Znaleziono dowód, że użytkownik powinien patrzeć na ten obszar.</span><span class="sxs-lookup"><span data-stu-id="01523-212">Found evidence that you should be looking at this area.</span></span>

1. <span data-ttu-id="01523-213">Wyczerpane innych obszarów, które znasz niczego nie objaśniające problem z wydajnością, który został wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="01523-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="01523-214">Znajduje się we wpisie [zrozumieć przed podjęciem próby rozwiązania](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji o podstawowe informacje dotyczące procesora CPU i pamięci.</span><span class="sxs-lookup"><span data-stu-id="01523-214">See the blog [Understand the problem before you try to find a solution](https://blogs.msdn.microsoft.com/maoni/2006/09/01/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="01523-215">Następujące narzędzia służy do zbierania danych dotyczących wydajności LOH:</span><span class="sxs-lookup"><span data-stu-id="01523-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="01523-216">Liczniki wydajności pamięci .NET CLR</span><span class="sxs-lookup"><span data-stu-id="01523-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="01523-217">Zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="01523-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="01523-218">Debuger</span><span class="sxs-lookup"><span data-stu-id="01523-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="01523-219">Liczniki wydajności pamięci .NET CLR</span><span class="sxs-lookup"><span data-stu-id="01523-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="01523-220">Te liczniki wydajności są zwykle dobry, pierwszym krokiem w badaniu problemów z wydajnością (mimo że firma Microsoft zaleca użycie [zdarzenia ETW](#etw)).</span><span class="sxs-lookup"><span data-stu-id="01523-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw)).</span></span> <span data-ttu-id="01523-221">Możesz skonfigurować Monitor wydajności, dodając liczniki, które mają, jak pokazano na rysunku 4.</span><span class="sxs-lookup"><span data-stu-id="01523-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="01523-222">Te, które są odpowiednie dla LOH są:</span><span class="sxs-lookup"><span data-stu-id="01523-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="01523-223">**\# Kolekcje Gen 2**</span><span class="sxs-lookup"><span data-stu-id="01523-223">**\# Gen 2 Collections**</span></span>

   <span data-ttu-id="01523-224">Wyświetla liczbę powtórzeń generacji 2 GC miały miejsce od rozpoczęcia procesu.</span><span class="sxs-lookup"><span data-stu-id="01523-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="01523-225">Licznik jest zwiększany po zakończeniu kolekcji generacji 2 (nazywanej także pełną wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="01523-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="01523-226">Ten licznik wskazuje ostatnią odczytaną wartość.</span><span class="sxs-lookup"><span data-stu-id="01523-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="01523-227">**Rozmiar sterty obiektów wielkich**</span><span class="sxs-lookup"><span data-stu-id="01523-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="01523-228">Wyświetla bieżący rozmiar w bajtach, włącznie z wolnego miejsca, LOH.</span><span class="sxs-lookup"><span data-stu-id="01523-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="01523-229">Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.</span><span class="sxs-lookup"><span data-stu-id="01523-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="01523-230">Jest to często stosowana metoda przyjrzeć się liczniki wydajności z Monitora wydajności (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="01523-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="01523-231">Użyj "Dodaj liczniki" można dodać licznika interesujące dla procesów, które są dla Ciebie ważne.</span><span class="sxs-lookup"><span data-stu-id="01523-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="01523-232">Dane liczników wydajności można zapisać do pliku dziennika, jak pokazano na rysunku 4.</span><span class="sxs-lookup"><span data-stu-id="01523-232">You can save the performance counter data to a log file, as Figure 4 shows.</span></span>

![Rysunek 4: Dodawanie liczników wydajności.](media/loh/perfcounter.png)    
<span data-ttu-id="01523-234">Rysunek 4: LOH po GC generacji 2</span><span class="sxs-lookup"><span data-stu-id="01523-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="01523-235">Liczniki wydajności można również można zbadać programowo.</span><span class="sxs-lookup"><span data-stu-id="01523-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="01523-236">Wiele osób zebrać je jako część procesu testowania rutynowych dzięki temu.</span><span class="sxs-lookup"><span data-stu-id="01523-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="01523-237">Po ich dodatkowe liczniki z wartościami, które są niezwykłe, korzystają z innych metod Aby uzyskać bardziej szczegółowe dane ułatwiające dochodzenia.</span><span class="sxs-lookup"><span data-stu-id="01523-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="01523-238">Firma Microsoft zaleca, czy można użyć zdarzenia ETW zamiast wydajności liczników, ponieważ ETW zapewnia bardziej rozbudowane dużej ilości informacji.</span><span class="sxs-lookup"><span data-stu-id="01523-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw"></a><span data-ttu-id="01523-239">ETW</span><span class="sxs-lookup"><span data-stu-id="01523-239">ETW</span></span>

<span data-ttu-id="01523-240">Moduł zbierający elementy bezużyteczne zawiera bogaty zestaw zdarzeń ETW, aby lepiej zrozumieć czynności sterty i dlaczego.</span><span class="sxs-lookup"><span data-stu-id="01523-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="01523-241">Następujących wpisach w blogu pokazują, jak zbierać i zrozumieć zdarzenia GC za pomocą funkcji ETW:</span><span class="sxs-lookup"><span data-stu-id="01523-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="01523-242">Zdarzenia GC ETW - 1 </span><span class="sxs-lookup"><span data-stu-id="01523-242">GC ETW Events - 1 </span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/22/gc-etw-events.aspx)

- [<span data-ttu-id="01523-243">Zdarzenia GC ETW - 2</span><span class="sxs-lookup"><span data-stu-id="01523-243">GC ETW Events - 2</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-2.aspx)

- [<span data-ttu-id="01523-244">Zdarzenia GC ETW - 3</span><span class="sxs-lookup"><span data-stu-id="01523-244">GC ETW Events - 3</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/25/gc-etw-events-3.aspx) 

- [<span data-ttu-id="01523-245">Zdarzenia GC ETW - 4</span><span class="sxs-lookup"><span data-stu-id="01523-245">GC ETW Events - 4</span></span>](http://blogs.msdn.com/b/maoni/archive/2014/12/30/gc-etw-events-4.aspx)

<span data-ttu-id="01523-246">Aby zidentyfikować generowania nadmiernej GC 2 spowodowany tymczasowego alokacji LOH, poszukaj w kolumnie Przyczyna wyzwalacza wykazów globalnych.</span><span class="sxs-lookup"><span data-stu-id="01523-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="01523-247">Prosty test tylko przydziela duże obiekty tymczasowe, można zbierać informacje dotyczące zdarzeń ETW z następującymi [narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567) wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="01523-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="01523-248">Wynik jest podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="01523-248">The result is something like this:</span></span>
 
![Rysunek 5: Sprawdzenie zdarzenia ETW przy użyciu narzędzia PerfView](media/loh/perfview.png)  
<span data-ttu-id="01523-250">Rysunek 5: Zdarzenia ETW pokazano przy użyciu narzędzia PerfView</span><span class="sxs-lookup"><span data-stu-id="01523-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="01523-251">Jak widać, wszystkich wykazów globalnych są generacji 2 GC, a ich są wszystkie wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwalane to GC.</span><span class="sxs-lookup"><span data-stu-id="01523-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="01523-252">Wiemy, że te przydziały są tymczasowe ponieważ **% szybkość przetrwania LOH** kolumny mówi 1%.</span><span class="sxs-lookup"><span data-stu-id="01523-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="01523-253">Można zbierać dodatkowe zdarzenia ETW określające, kto przydzielone te dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="01523-254">Następujący wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="01523-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="01523-255">zbiera zdarzenia AllocationTick uruchamiane mniej więcej co 100k warto alokacji.</span><span class="sxs-lookup"><span data-stu-id="01523-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="01523-256">Innymi słowy zdarzenie jest wywoływane zawsze, gdy jest przydzielany dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="01523-257">Następnie zapoznanie się z jednego z widoków alokacji sterty GC, których opisano callstacks, która przydzielona dużych obiektów:</span><span class="sxs-lookup"><span data-stu-id="01523-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>
 
![Rysunek 6: Widok alokacji sterty GC](media/loh/perfview2.png)  
<span data-ttu-id="01523-259">Rysunek 6: Widok alokacji sterty GC</span><span class="sxs-lookup"><span data-stu-id="01523-259">Figure 6: A GC Heap Alloc view</span></span>
 
<span data-ttu-id="01523-260">Jak widać, jest bardzo proste test, który właśnie przydziela duże obiekty z jego `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="01523-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="01523-261">Debuger</span><span class="sxs-lookup"><span data-stu-id="01523-261">A debugger</span></span>

<span data-ttu-id="01523-262">Jeśli masz zrzut pamięci jest i należy przyjrzeć się, jakie obiekty są faktycznie na LOH, można użyć [rozszerzenia debugera SoS](http://msdn2.microsoft.com/ms404370.aspx) dostarczonych przez .NET.</span><span class="sxs-lookup"><span data-stu-id="01523-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](http://msdn2.microsoft.com/ms404370.aspx) provided by .NET.</span></span> 

> [!NOTE]
> <span data-ttu-id="01523-263">Debugowania polecenia wymienione w tej sekcji mają zastosowanie do [debugery Windows](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="01523-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](http://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="01523-264">Poniżej przedstawiono przykładowe dane wyjściowe analizowanie LOH:</span><span class="sxs-lookup"><span data-stu-id="01523-264">The following shows sample output from analyzing the LOH:</span></span>

```
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="01523-265">Rozmiar sterty LOH jest (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bajtów.</span><span class="sxs-lookup"><span data-stu-id="01523-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="01523-266">Między 023e1000 adresy i 033db630 bajtów 8,008,736 są zajęte przez tablicę <xref:System.Object?displayProperty=fullName> obiekty bajtów 6,663,696 są zajęte przez tablicę <xref:System.Byte?displayProperty=nameWithType> obiektów i 2,081,792 bajtów są zajęte przez ilość wolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="01523-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=fullName> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="01523-267">Czasami debuger pokazuje, czy całkowity rozmiar LOH jest mniejsza niż 85,000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="01523-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="01523-268">Dzieje się tak, ponieważ wykonawcze używa LOH przydzielić niektóre obiekty, które są mniejsze niż dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="01523-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="01523-269">Ponieważ nie jest kompaktowanie LOH, czasami LOH jest thoought na źródło fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="01523-269">Because the LOH is not compacted, sometimes the LOH is thoought to be the source of fragmentation.</span></span> <span data-ttu-id="01523-270">Fragmentacja oznacza:</span><span class="sxs-lookup"><span data-stu-id="01523-270">Fragmentation means:</span></span>

- <span data-ttu-id="01523-271">Fragmentacja sterty zarządzanej, który jest wskazywany przez ilość wolnego miejsca między zarządzanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="01523-272">W SoS `!dumpheap –type Free` polecenie wyświetla ilość wolnego miejsca między zarządzanych obiektów.</span><span class="sxs-lookup"><span data-stu-id="01523-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="01523-273">Fragmentacja przestrzeni adresów pamięci wirtualnej (VM), który jest pamięć oznaczony jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="01523-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="01523-274">Możesz pobrać go przy użyciu różnych poleceń debugera w windbg.</span><span class="sxs-lookup"><span data-stu-id="01523-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="01523-275">W poniższym przykładzie przedstawiono fragmentacji przestrzeni maszyny Wirtualnej:</span><span class="sxs-lookup"><span data-stu-id="01523-275">The following example shows fragmentation in the VM space:</span></span>

   ```
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="01523-276">Jest więcej częściej można zobaczyć fragmentacji maszyny Wirtualnej spowodowane tymczasowego duże obiekty, które wymagają modułu zbierającego elementy bezużyteczne często uzyskać nowy zarządzanych segmentów sterty z systemu operacyjnego i wersji pustych z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="01523-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="01523-277">Aby sprawdzić, czy LOH powoduje fragmentację maszyny Wirtualnej, należy ustawić punkt przerwania na [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) i [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) aby zobaczyć, kto połączeń telefonicznych z nimi.</span><span class="sxs-lookup"><span data-stu-id="01523-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) and [VirtualFree](https://msdn.microsoft.com/library/windows/desktop/aa366892(v=vs.85).aspx) to see who call them.</span></span> <span data-ttu-id="01523-278">Na przykład aby zobaczyć, kto próbował Przydziel większy niż 8MBB fragmentów pamięci wirtualnej z systemu operacyjnego, można ustawić punkt przerwania następująco:</span><span class="sxs-lookup"><span data-stu-id="01523-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="01523-279">To polecenie przechodzi do debugera i pokazuje tylko wtedy, gdy stos wywołań [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) jest wywoływana z rozmiarem alokacji większa niż 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="01523-279">This command breaks into the debugger and shows the callstack only if [VirtualAlloc](https://msdn.microsoft.com/library/windows/desktop/aa366887(v=vs.85).aspx) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="01523-280">CLR 2.0 dodano funkcję *Hoarding maszyny Wirtualnej* które może być przydatne w przypadku scenarious gdzie segmenty (w tym na duże i małe obiektu stosów) są często nabyte i wydane.</span><span class="sxs-lookup"><span data-stu-id="01523-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarious where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="01523-281">Aby określić Hoarding maszyny Wirtualnej, należy określić flagę uruchamiania o nazwie `STARTUP_HOARD_GC_VM` za pomocą obsługi interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="01523-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="01523-282">Zamiast zwalnianie pusty segmentów do systemu operacyjnego, środowisko CLR decommits pamięci na te segmenty i umieszcza je na liście wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="01523-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="01523-283">(Należy pamiętać, że środowisko CLR nie tym segmentów, które są za duże). Środowisko CLR później używa tych segmentów do spełnienia żądania nowego segmentu.</span><span class="sxs-lookup"><span data-stu-id="01523-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="01523-284">Przy następnym, że Twoja aplikacja powinna nowy segment, CLR korzysta z tej listy gotowości Jeśli znajdziesz taki, który jest wystarczająco duży.</span><span class="sxs-lookup"><span data-stu-id="01523-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="01523-285">Hoarding maszyny Wirtualnej jest również przydatne w przypadku aplikacji, które mają być przechowywane na segmenty, które już nabyte, takie jak niektóre aplikacje serwera, które są dominującą aplikacje uruchomione w systemie, aby uniknąć poza wyjątkami pamięci.</span><span class="sxs-lookup"><span data-stu-id="01523-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="01523-286">Zdecydowanie zaleca się starannie przetestować aplikację podczas upewnij się, że aplikacja ma użycie pamięci stabilny za pomocą tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="01523-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
