---
title: LOH w systemie Windows - .NET
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 5125b76dd26ffa4fb363ecf8449f65b490f57b93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74283620"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="fecbf-102">Stos dużych obiektów w systemach Windows</span><span class="sxs-lookup"><span data-stu-id="fecbf-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="fecbf-103">Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiekty na małe i duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="fecbf-104">Gdy obiekt jest duży, niektóre z jego atrybutów stają się bardziej znaczące niż jeśli obiekt jest mały.</span><span class="sxs-lookup"><span data-stu-id="fecbf-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="fecbf-105">Na przykład zagęszczanie go - czyli kopiowanie go w pamięci w innym miejscu na stercie - może być kosztowne.</span><span class="sxs-lookup"><span data-stu-id="fecbf-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="fecbf-106">Z tego powodu moduł odśmiecania pamięci .NET umieszcza duże obiekty na stercie dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="fecbf-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="fecbf-107">W tym temacie przyjrzymy się głębiej sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="fecbf-108">Omówimy, co kwalifikuje obiekt jako duży obiekt, jak te duże obiekty są zbierane i jakie implikacje wydajności dużych obiektów nałożyć.</span><span class="sxs-lookup"><span data-stu-id="fecbf-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fecbf-109">W tym temacie omówiono stertę dużych obiektów w programie .NET Framework i platformie .NET Core działającej tylko w systemach Windows.</span><span class="sxs-lookup"><span data-stu-id="fecbf-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="fecbf-110">Nie obejmuje LOH uruchomiony na implementacje .NET na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="fecbf-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="fecbf-111">Jak obiekt kończy się na stercie dużego obiektu i jak GC obsługuje je</span><span class="sxs-lookup"><span data-stu-id="fecbf-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="fecbf-112">Jeśli obiekt jest większy lub równy rozmiarowi 85 000 bajtów, jest uważany za duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="fecbf-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="fecbf-113">Liczba ta została określona przez dostrajanie wydajności.</span><span class="sxs-lookup"><span data-stu-id="fecbf-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="fecbf-114">Gdy żądanie alokacji obiektu jest dla 85 000 lub więcej bajtów, czas wykonywania przydziela go na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="fecbf-115">Aby zrozumieć, co to oznacza, warto zbadać niektóre podstawy dotyczące .NET GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="fecbf-116">Moduł zbierający elementy bezużyteczne .NET jest modułem zbierającym pokoleń.</span><span class="sxs-lookup"><span data-stu-id="fecbf-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="fecbf-117">Ma trzy pokolenia: pokolenie 0, pokolenie 1 i pokolenie 2.</span><span class="sxs-lookup"><span data-stu-id="fecbf-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="fecbf-118">Powodem posiadania 3 pokoleń jest to, że w dobrze dostrojonej aplikacji większość obiektów ginie w gen0.</span><span class="sxs-lookup"><span data-stu-id="fecbf-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="fecbf-119">Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny zostać umarznięte po zakończeniu żądania.</span><span class="sxs-lookup"><span data-stu-id="fecbf-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="fecbf-120">Wnioski o przydział w locie trafią do gen1 i tam umrą.</span><span class="sxs-lookup"><span data-stu-id="fecbf-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="fecbf-121">Zasadniczo gen1 działa jako bufor między młodymi obszarami obiektów a długowiecznymi obszarami obiektów.</span><span class="sxs-lookup"><span data-stu-id="fecbf-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="fecbf-122">Małe obiekty są zawsze przydzielane w generacji 0 i, w zależności od ich okresu istnienia, mogą być promowane do generacji 1 lub generacji2.</span><span class="sxs-lookup"><span data-stu-id="fecbf-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="fecbf-123">Duże obiekty są zawsze przydzielane w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="fecbf-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="fecbf-124">Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="fecbf-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="fecbf-125">Po zebraniu pokolenia zbierane są również wszystkie jego młodsze pokolenia.</span><span class="sxs-lookup"><span data-stu-id="fecbf-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="fecbf-126">Na przykład, gdy generacji 1 GC się dzieje, zarówno generacji 1 i 0 są zbierane.</span><span class="sxs-lookup"><span data-stu-id="fecbf-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="fecbf-127">A kiedy generacji 2 GC się dzieje, cała sterta jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="fecbf-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="fecbf-128">Z tego powodu, generacji 2 GC jest również nazywany *pełny GC*.</span><span class="sxs-lookup"><span data-stu-id="fecbf-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="fecbf-129">Ten artykuł odnosi się do generacji 2 GC zamiast pełnego GC, ale terminy są wymienne.</span><span class="sxs-lookup"><span data-stu-id="fecbf-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="fecbf-130">Generacje zapewniają logiczny widok sterty GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="fecbf-131">Fizycznie obiekty żyją w zarządzanych segmentach sterty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="fecbf-132">*Zarządzany segment sterty* to fragment pamięci, który GC rezerwuje z systemu operacyjnego, wywołując [funkcję VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="fecbf-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="fecbf-133">Po załadowaniu clr GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterty małych obiektów lub SOH) i jeden dla dużych obiektów (sterty dużych obiektów).</span><span class="sxs-lookup"><span data-stu-id="fecbf-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="fecbf-134">Żądania alokacji są następnie spełnione przez umieszczenie zarządzanych obiektów w tych zarządzanych segmentach sterty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="fecbf-135">Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany w segmencie dla SOH; w przeciwnym razie jest umieszczany w segmencie LOH.</span><span class="sxs-lookup"><span data-stu-id="fecbf-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="fecbf-136">Segmenty są zatwierdzane (w mniejszych fragmentach), ponieważ coraz więcej obiektów jest przydzielanych do nich.</span><span class="sxs-lookup"><span data-stu-id="fecbf-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="fecbf-137">Dla SOH obiekty, które przetrwają GC są promowane do następnej generacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="fecbf-138">Obiekty, które przetrwają generacji 0 kolekcji są teraz uważane za generacji 1 obiektów i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fecbf-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="fecbf-139">Jednak obiekty, które przetrwały najstarsze pokolenie, są nadal uważane za w najstarszym pokoleniu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="fecbf-140">Innymi słowy, osoby, które przeżyły z 2 generacji, są obiektami 2 generacji; i ocalałych z LOH są obiekty LOH (które są zbierane z gen2).</span><span class="sxs-lookup"><span data-stu-id="fecbf-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="fecbf-141">Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty).</span><span class="sxs-lookup"><span data-stu-id="fecbf-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="fecbf-142">Tylko GC może "przydzielić" obiekty w pokoleniu 1 (poprzez promowanie ocalałych z pokolenia 0) i generacji 2 (poprzez promowanie ocalałych z pokoleń 1 i 2).</span><span class="sxs-lookup"><span data-stu-id="fecbf-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="fecbf-143">Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi obiekty na żywo i kompakty je.</span><span class="sxs-lookup"><span data-stu-id="fecbf-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="fecbf-144">Ale ponieważ zagęszczanie jest drogie, GC *zamiata* LOH; tworzy bezpłatną listę martwych obiektów, które mogą być ponownie używane później, aby spełnić żądania alokacji dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="fecbf-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="fecbf-145">Sąsiednie martwe obiekty są wykonane w jeden wolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="fecbf-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="fecbf-146">.NET Core i .NET Framework (począwszy od .NET <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> Framework 4.5.1) zawierają właściwość, która pozwala użytkownikom określić, że LOH powinny być kompaktowane podczas następnego pełnego blokowania GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="fecbf-147">A w przyszłości .NET może zdecydować się na automatyczne kompaktowanie LOH.</span><span class="sxs-lookup"><span data-stu-id="fecbf-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="fecbf-148">Oznacza to, że jeśli przydzielisz duże obiekty i chcesz upewnić się, że nie poruszają się, nadal należy je przypiąć.</span><span class="sxs-lookup"><span data-stu-id="fecbf-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="fecbf-149">Rysunek 1 przedstawia scenariusz, w którym GC tworzy generacji `Obj1` 1 `Obj3` po pierwszej generacji 0 GC gdzie i `Obj2` `Obj5` są martwe, i tworzy generacji 2 po pierwszej generacji 1 GC, gdzie i są martwe.</span><span class="sxs-lookup"><span data-stu-id="fecbf-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="fecbf-150">Należy pamiętać, że to i poniższe rysunki są tylko w celach ilustracyjnych; zawierają bardzo niewiele obiektów, aby lepiej pokazać, co dzieje się na stercie.</span><span class="sxs-lookup"><span data-stu-id="fecbf-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="fecbf-151">W rzeczywistości wiele więcej obiektów są zazwyczaj zaangażowane w GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-151">In reality, many more objects are typically involved in a GC.</span></span>

![Rysunek 1: Gen 0 GC i gc gen 1](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="fecbf-153">Rysunek 1: Generacja 0 i gc generacji 1.</span><span class="sxs-lookup"><span data-stu-id="fecbf-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="fecbf-154">Rysunek 2 pokazuje, że po generacji `Obj1` `Obj2` 2 GC, który widział, że i są martwe, GC tworzy `Obj1` `Obj2`ciągłe wolne miejsce z pamięci, `Obj4`które były zajęte przez i , który następnie został użyty do zaspokojenia żądania alokacji dla .</span><span class="sxs-lookup"><span data-stu-id="fecbf-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="fecbf-155">Spacja po ostatnim `Obj3`obiekcie, do końca segmentu może być również używana do spełnienia żądań alokacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Rysunek 2: Po gc gen 2](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="fecbf-157">Rysunek 2: Po 2 generacji GC</span><span class="sxs-lookup"><span data-stu-id="fecbf-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="fecbf-158">Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużych obiektów, GC najpierw próbuje uzyskać więcej segmentów z os.</span><span class="sxs-lookup"><span data-stu-id="fecbf-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="fecbf-159">Jeśli to się nie powiedzie, wyzwala generacji 2 GC w nadziei na uwolnienie trochę miejsca.</span><span class="sxs-lookup"><span data-stu-id="fecbf-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="fecbf-160">Podczas generacji 1 lub generacji 2 GC moduł zbierający elementy bezużyteczne zwalnia segmenty, które nie mają obiektów na żywo na nich z powrotem do os, wywołując [VirtualFree funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="fecbf-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="fecbf-161">Spacja po ostatnim obiekcie na żywo na końcu segmentu jest uchylana (z wyjątkiem segmentu efemeralnego, w którym działa gen0/gen1, gdzie moduł zbierający elementy bezużyteczne zachowuje pewne zatwierdzone, ponieważ aplikacja będzie przydzielać w nim od razu).</span><span class="sxs-lookup"><span data-stu-id="fecbf-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="fecbf-162">Wolne miejsca pozostają zatwierdzone, mimo że są resetowane, co oznacza, że serwer operacyjny nie musi zapisywać danych w nich z powrotem na dysk.</span><span class="sxs-lookup"><span data-stu-id="fecbf-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="fecbf-163">Ponieważ LOH jest zbierany tylko podczas generacji 2 GC, segment LOH może zostać uwolniony tylko podczas takiego GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="fecbf-164">Rysunek 3 przedstawia scenariusz, w którym moduł odśmiecania pamięci zwalnia jeden segment (segment 2) z powrotem do os i anutuje więcej miejsca na pozostałych segmentach.</span><span class="sxs-lookup"><span data-stu-id="fecbf-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="fecbf-165">Jeśli musi użyć nieprzydzielonych miejsca na końcu segmentu, aby spełnić żądania alokacji dużych obiektów, ponownie zatwierdza pamięć.</span><span class="sxs-lookup"><span data-stu-id="fecbf-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="fecbf-166">(Aby uzyskać wyjaśnienie zatwierdzenia/dezcommit, zobacz dokumentację [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="fecbf-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Rysunek 3: LOH po gc gen 2](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="fecbf-168">Rysunek 3: LOH po 2 generacji GC</span><span class="sxs-lookup"><span data-stu-id="fecbf-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="fecbf-169">Kiedy zbiera się duży obiekt?</span><span class="sxs-lookup"><span data-stu-id="fecbf-169">When is a large object collected?</span></span>

<span data-ttu-id="fecbf-170">Ogólnie rzecz biorąc GC występuje, gdy jeden z następujących 3 warunki dzieje:</span><span class="sxs-lookup"><span data-stu-id="fecbf-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="fecbf-171">Alokacja przekracza próg generacji 0 lub dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="fecbf-172">Próg jest właściwością generacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="fecbf-173">Próg dla generacji jest ustawiany, gdy moduł zbierający elementy bezużyteczne przydziela do niego obiekty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="fecbf-174">Po przekroczeniu progu gc jest wyzwalany na tej generacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="fecbf-175">Podczas przydzielania małych lub dużych obiektów, należy użyć generacji 0 i progi LOH, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fecbf-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="fecbf-176">Gdy moduł zbierający elementy bezużyteczne przydziela do generacji 1 i 2, zużywa ich progi.</span><span class="sxs-lookup"><span data-stu-id="fecbf-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="fecbf-177">Progi te są dynamicznie dostrojone podczas pracy programu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="fecbf-178">Jest to typowy przypadek; większość kontrolerów gcs się odbywa z powodu alokacji na zarządzanym stercie.</span><span class="sxs-lookup"><span data-stu-id="fecbf-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="fecbf-179">Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="fecbf-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="fecbf-180">Jeśli metoda <xref:System.GC.Collect?displayProperty=nameWithType> bezparametrów jest wywoływana lub <xref:System.GC.MaxGeneration?displayProperty=nameWithType> inne przeciążenie jest przekazywane jako argument, LOH jest zbierane wraz z resztą zarządzanego sterty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="fecbf-181">System znajduje się w małej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="fecbf-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="fecbf-182">Dzieje się tak, gdy moduł zbierający elementy bezużyteczne odbiera powiadomienie o wysokiej pamięci z os.</span><span class="sxs-lookup"><span data-stu-id="fecbf-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="fecbf-183">Jeśli moduł zbierający elementy bezużyteczne uważa, że wykonywanie generacji 2 GC będzie produktywne, wyzwala jeden.</span><span class="sxs-lookup"><span data-stu-id="fecbf-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="fecbf-184">Implikacje wydajności LOH</span><span class="sxs-lookup"><span data-stu-id="fecbf-184">LOH Performance Implications</span></span>

<span data-ttu-id="fecbf-185">Alokacje na stercie dużych obiektów wpływ na wydajność w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="fecbf-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="fecbf-186">Koszt alokacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-186">Allocation cost.</span></span>

  <span data-ttu-id="fecbf-187">CLR sprawia, że gwarancja, że pamięć dla każdego nowego obiektu, który rozdaje jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="fecbf-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="fecbf-188">Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez wyczyszczenie pamięci (chyba że wyzwala GC).</span><span class="sxs-lookup"><span data-stu-id="fecbf-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="fecbf-189">Jeśli trwa 2 cykle, aby wyczyścić jeden bajt, trwa 170.000 cykli, aby wyczyścić najmniejszy duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="fecbf-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="fecbf-190">Wyczyszczenie pamięci obiektu o rozmiarze 16 MB na komputerze 2 GHz zajmuje około 16 ms.</span><span class="sxs-lookup"><span data-stu-id="fecbf-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="fecbf-191">To dość duży koszt.</span><span class="sxs-lookup"><span data-stu-id="fecbf-191">That's a rather large cost.</span></span>

- <span data-ttu-id="fecbf-192">Koszt odbioru.</span><span class="sxs-lookup"><span data-stu-id="fecbf-192">Collection cost.</span></span>

  <span data-ttu-id="fecbf-193">Ponieważ LOH i generacji 2 są zbierane razem, jeśli jeden próg zostanie przekroczony, generacji 2 kolekcji jest wyzwalany.</span><span class="sxs-lookup"><span data-stu-id="fecbf-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="fecbf-194">Jeśli kolekcja 2 generacji jest wyzwalana z powodu LOH, generacja 2 nie musi być znacznie mniejsza po GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="fecbf-195">Jeśli nie ma zbyt wiele danych na generacji 2, ma to minimalny wpływ.</span><span class="sxs-lookup"><span data-stu-id="fecbf-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="fecbf-196">Ale jeśli generacja 2 jest duża, może to spowodować problemy z wydajnością, jeśli zostanie wyzwolonych wiele kontrolerów GCs generacji 2.</span><span class="sxs-lookup"><span data-stu-id="fecbf-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="fecbf-197">Jeśli wiele dużych obiektów są przydzielane na bardzo tymczasowe i masz duży SOH, można spędzać zbyt dużo czasu robi GCs.</span><span class="sxs-lookup"><span data-stu-id="fecbf-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="fecbf-198">Ponadto koszt alokacji może naprawdę się sumować, jeśli nadal przydzielania i puszczania naprawdę dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="fecbf-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="fecbf-199">Elementy tablicy z typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="fecbf-199">Array elements with reference types.</span></span>

  <span data-ttu-id="fecbf-200">Bardzo duże obiekty na LOH są zazwyczaj tablice (jest bardzo rzadko mają obiekt wystąpienia, który jest naprawdę duży).</span><span class="sxs-lookup"><span data-stu-id="fecbf-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="fecbf-201">Jeśli elementy tablicy są bogate w odwołania, ponosi koszt, który nie jest obecny, jeśli elementy nie są bogate w odwołania.</span><span class="sxs-lookup"><span data-stu-id="fecbf-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="fecbf-202">Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie musi w ogóle przechodzić przez tablicę.</span><span class="sxs-lookup"><span data-stu-id="fecbf-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="fecbf-203">Na przykład jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów zaimplementowania jest odwoływanie się do węzła prawego i lewego węzła przez rzeczywiste węzły:</span><span class="sxs-lookup"><span data-stu-id="fecbf-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="fecbf-204">Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przejść przez co najmniej dwa odwołania na element.</span><span class="sxs-lookup"><span data-stu-id="fecbf-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="fecbf-205">Alternatywnym podejściem jest przechowywanie indeksu prawego i lewego węzła:</span><span class="sxs-lookup"><span data-stu-id="fecbf-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="fecbf-206">Zamiast odwoływać się do danych lewego węzła `left.d`jako `binary_tr[left_index].d`, można odnosić się do niego jako .</span><span class="sxs-lookup"><span data-stu-id="fecbf-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="fecbf-207">A moduł zbierający elementy bezużyteczne nie musi patrzeć na żadne odwołania dla lewego i prawego węzła.</span><span class="sxs-lookup"><span data-stu-id="fecbf-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="fecbf-208">Z trzech czynników, pierwsze dwa są zwykle bardziej znaczące niż trzeci.</span><span class="sxs-lookup"><span data-stu-id="fecbf-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="fecbf-209">Z tego powodu zaleca się przydzielenie puli dużych obiektów, które są ponownie używane zamiast przydzielania tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="fecbf-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="fecbf-210">Zbieranie danych o wydajności dla LOH</span><span class="sxs-lookup"><span data-stu-id="fecbf-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="fecbf-211">Przed zebraniem danych dotyczących wydajności dla określonego obszaru należy już wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fecbf-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="fecbf-212">Znaleziono dowody, że powinieneś przyjrzeć się tej dziedzinie.</span><span class="sxs-lookup"><span data-stu-id="fecbf-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="fecbf-213">Wyczerpane inne obszary, które znasz, nie znajdując niczego, co mogłoby wyjaśnić problem z wydajnością, który widziałeś.</span><span class="sxs-lookup"><span data-stu-id="fecbf-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="fecbf-214">Zobacz blog [Opis ztym problemem, zanim spróbujesz znaleźć rozwiązanie, aby](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji na temat podstaw pamięci i procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="fecbf-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="fecbf-215">Do zbierania danych na temat wydajności LOH można używać następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="fecbf-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="fecbf-216">Liczniki wydajności pamięci CLR .NET</span><span class="sxs-lookup"><span data-stu-id="fecbf-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="fecbf-217">zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="fecbf-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="fecbf-218">Debuger</span><span class="sxs-lookup"><span data-stu-id="fecbf-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="fecbf-219">Liczniki wydajności pamięci CLR .NET</span><span class="sxs-lookup"><span data-stu-id="fecbf-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="fecbf-220">Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (chociaż zaleca się użycie [zdarzeń ETW).](#etw-events)</span><span class="sxs-lookup"><span data-stu-id="fecbf-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="fecbf-221">Monitor wydajności można skonfigurować, dodając liczniki, które mają, jak pokazano na rysunku 4.</span><span class="sxs-lookup"><span data-stu-id="fecbf-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="fecbf-222">Te, które są istotne dla LOH są:</span><span class="sxs-lookup"><span data-stu-id="fecbf-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="fecbf-223">**Kolekcje Gen 2**</span><span class="sxs-lookup"><span data-stu-id="fecbf-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="fecbf-224">Wyświetla liczbę powtórzeń generacji 2 kontrolerów domeny od czasu rozpoczęcia procesu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="fecbf-225">Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywanerównież pełne wyrzucanie elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="fecbf-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="fecbf-226">Ten licznik wyświetla ostatnio zaobserwowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="fecbf-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="fecbf-227">**Rozmiar sterty dużych obiektów**</span><span class="sxs-lookup"><span data-stu-id="fecbf-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="fecbf-228">Wyświetla bieżący rozmiar, w bajtach, w tym wolne miejsce, LOH.</span><span class="sxs-lookup"><span data-stu-id="fecbf-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="fecbf-229">Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie na każdej alokacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="fecbf-230">Typowym sposobem patrzenia na liczniki wydajności jest monitor wydajności (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="fecbf-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="fecbf-231">Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, na których Ci zależy.</span><span class="sxs-lookup"><span data-stu-id="fecbf-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="fecbf-232">Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:</span><span class="sxs-lookup"><span data-stu-id="fecbf-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="fecbf-233">![Zrzut ekranu przedstawiający dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="fecbf-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="fecbf-234">Rysunek 4: LOH po 2 generacji GC</span><span class="sxs-lookup"><span data-stu-id="fecbf-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="fecbf-235">Liczniki wydajności można również programowo przeszukiwać.</span><span class="sxs-lookup"><span data-stu-id="fecbf-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="fecbf-236">Wiele osób zbiera je w ten sposób w ramach rutynowego procesu testowania.</span><span class="sxs-lookup"><span data-stu-id="fecbf-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="fecbf-237">Kiedy wykrywają liczniki z wartościami, które są nietypowe, używają innych środków, aby uzyskać bardziej szczegółowe dane, aby pomóc w dochodzeniu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="fecbf-238">Zaleca się używanie zdarzeń ETW zamiast liczników wydajności, ponieważ ETW dostarcza znacznie bogatszych informacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="fecbf-239">zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="fecbf-239">ETW events</span></span>

<span data-ttu-id="fecbf-240">Moduł zbierający elementy bezużyteczne udostępnia bogaty zestaw zdarzeń ETW, które pomogą Ci zrozumieć, co robi sterta i dlaczego.</span><span class="sxs-lookup"><span data-stu-id="fecbf-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="fecbf-241">Następujące wpisy na blogu pokazują, jak zbierać i rozumieć zdarzenia GC za pomocą ETW:</span><span class="sxs-lookup"><span data-stu-id="fecbf-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="fecbf-242">Gc ETW Wydarzenia - 1</span><span class="sxs-lookup"><span data-stu-id="fecbf-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="fecbf-243">Gc ETW Wydarzenia - 2</span><span class="sxs-lookup"><span data-stu-id="fecbf-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="fecbf-244">Gc ETW Wydarzenia - 3</span><span class="sxs-lookup"><span data-stu-id="fecbf-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="fecbf-245">Gc ETW Wydarzenia - 4</span><span class="sxs-lookup"><span data-stu-id="fecbf-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="fecbf-246">Aby zidentyfikować nadmierne generacje 2 gcs spowodowane tymczasowymi alokacjami LOH, przyjrzyj się kolumnie Przyczyna wyzwalacza dla kontrolerów GCs.</span><span class="sxs-lookup"><span data-stu-id="fecbf-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="fecbf-247">Aby uzyskać prosty test, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje o zdarzeniach ETW za pomocą następującego wiersza polecenia [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)</span><span class="sxs-lookup"><span data-stu-id="fecbf-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="fecbf-248">Wynik jest coś takiego:</span><span class="sxs-lookup"><span data-stu-id="fecbf-248">The result is something like this:</span></span>

<span data-ttu-id="fecbf-249">![Zrzut ekranu przedstawiający zdarzenia ETW w perfview.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="fecbf-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="fecbf-250">Rysunek 5: Zdarzenia ETW wyświetlane za pomocą PerfView</span><span class="sxs-lookup"><span data-stu-id="fecbf-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="fecbf-251">Jak widać, wszystkie GP generacji 2 i wszystkie są wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwoliło ten GC.</span><span class="sxs-lookup"><span data-stu-id="fecbf-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="fecbf-252">Wiemy, że te przydziały są tymczasowe, ponieważ kolumna **LOH Survival Rate %** mówi 1%.</span><span class="sxs-lookup"><span data-stu-id="fecbf-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="fecbf-253">Można zbierać dodatkowe zdarzenia ETW, które informują, kto przydzielił te duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="fecbf-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="fecbf-254">Następujący wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="fecbf-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="fecbf-255">zbiera AllocationTick zdarzenie, które jest uruchamiane w przybliżeniu co 100k wartości alokacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="fecbf-256">Innymi słowy zdarzenie jest uruchamiany za każdym razem, gdy duży obiekt jest przydzielany.</span><span class="sxs-lookup"><span data-stu-id="fecbf-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="fecbf-257">Następnie można spojrzeć na jeden z widoków GC Heap Alloc, które pokazują stosy wywołań, które adzielone dużych obiektów:</span><span class="sxs-lookup"><span data-stu-id="fecbf-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="fecbf-258">![Zrzut ekranu przedstawiający widok sterty modułu zbierającego elementy bezużyteczne.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="fecbf-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="fecbf-259">Rysunek 6: Widok alloc sterty GC</span><span class="sxs-lookup"><span data-stu-id="fecbf-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="fecbf-260">Jak widać, jest to bardzo prosty test, który po `Main` prostu przydziela duże obiekty z jego metody.</span><span class="sxs-lookup"><span data-stu-id="fecbf-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="fecbf-261">Debuger</span><span class="sxs-lookup"><span data-stu-id="fecbf-261">A debugger</span></span>

<span data-ttu-id="fecbf-262">Jeśli wszystko, co masz jest zrzut pamięci i trzeba spojrzeć na jakie obiekty są faktycznie na LOH, można użyć [rozszerzenia debugera SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) dostarczone przez .NET.</span><span class="sxs-lookup"><span data-stu-id="fecbf-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="fecbf-263">Polecenia debugowania wymienione w tej sekcji mają zastosowanie do [debugerów systemu Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="fecbf-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="fecbf-264">Poniżej przedstawiono przykładowe dane wyjściowe z analizy LOH:</span><span class="sxs-lookup"><span data-stu-id="fecbf-264">The following shows sample output from analyzing the LOH:</span></span>

```console
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

<span data-ttu-id="fecbf-265">Rozmiar sterty LOH wynosi (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów.</span><span class="sxs-lookup"><span data-stu-id="fecbf-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="fecbf-266">Między adresami 023e1000 i 033db630, 8 008 736 bajtów <xref:System.Object?displayProperty=nameWithType> jest zajmowanych przez tablicę obiektów, 6 663 696 bajtów zajmują tablica <xref:System.Byte?displayProperty=nameWithType> obiektów, a 2 081 792 bajtów zajmują wolne miejsce.</span><span class="sxs-lookup"><span data-stu-id="fecbf-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="fecbf-267">Czasami debuger pokazuje, że całkowity rozmiar LOH jest mniejsza niż 85.000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="fecbf-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="fecbf-268">Dzieje się tak, ponieważ czas wykonywania sam używa LOH do przydzielenia niektórych obiektów, które są mniejsze niż duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="fecbf-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="fecbf-269">Ponieważ LOH nie jest zagęszczony, czasami LOH jest uważany za źródło fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="fecbf-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="fecbf-270">Fragmentacja oznacza:</span><span class="sxs-lookup"><span data-stu-id="fecbf-270">Fragmentation means:</span></span>

- <span data-ttu-id="fecbf-271">Fragmentacja zarządzanej sterty, która jest wskazywana przez ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="fecbf-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="fecbf-272">W `!dumpheap –type Free` usg, polecenie wyświetla ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="fecbf-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="fecbf-273">Fragmentacja przestrzeni adresowej pamięci wirtualnej (VM), czyli `MEM_FREE`pamięci oznaczonej jako .</span><span class="sxs-lookup"><span data-stu-id="fecbf-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="fecbf-274">Można go uzyskać za pomocą różnych poleceń debugera w windbg.</span><span class="sxs-lookup"><span data-stu-id="fecbf-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="fecbf-275">W poniższym przykładzie przedstawiono fragmentację w przestrzeni maszyny Wirtualnej:</span><span class="sxs-lookup"><span data-stu-id="fecbf-275">The following example shows fragmentation in the VM space:</span></span>

   ```console
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

<span data-ttu-id="fecbf-276">Jest bardziej powszechne, aby zobaczyć fragmentacji maszyny wirtualnej spowodowane przez tymczasowe dużych obiektów, które wymagają modułzbierający elementy bezużyteczne do często nabywania nowych zarządzanych segmentów sterty z systemu operacyjnego i zwolnić puste z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="fecbf-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="fecbf-277">Aby sprawdzić, czy LOH jest przyczyną fragmentacji maszyn wirtualnych, można ustawić punkt przerwania na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree,](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) aby zobaczyć, kto do nich wywołać.</span><span class="sxs-lookup"><span data-stu-id="fecbf-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="fecbf-278">Na przykład, aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z os, można ustawić punkt przerwania w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="fecbf-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="fecbf-279">To polecenie jest podzielone na debuger i pokazuje stos wywołań tylko wtedy, gdy [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływana o rozmiarze alokacji większym niż 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="fecbf-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="fecbf-280">W clr 2.0 dodano funkcję o nazwie *VM Hoarding,* która może być przydatna w scenariuszach, w których segmenty (w tym na stertach dużych i małych obiektów) są często nabywane i zwalniane.</span><span class="sxs-lookup"><span data-stu-id="fecbf-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="fecbf-281">Aby określić vm hoarding, należy `STARTUP_HOARD_GC_VM` określić flagę uruchamiania wywoływaną za pośrednictwem hostingu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="fecbf-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="fecbf-282">Zamiast zwalniać puste segmenty z powrotem do os, CLR anutuje pamięć w tych segmentach i umieszcza je na liście gotowości.</span><span class="sxs-lookup"><span data-stu-id="fecbf-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="fecbf-283">(Należy zauważyć, że CLR nie robi tego dla segmentów, które są zbyt duże.) CLR później używa tych segmentów do spełnienia nowych żądań segmentu.</span><span class="sxs-lookup"><span data-stu-id="fecbf-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="fecbf-284">Następnym razem, gdy aplikacja potrzebuje nowego segmentu, CLR używa jednego z tej listy gotowości, jeśli może znaleźć taki, który jest wystarczająco duży.</span><span class="sxs-lookup"><span data-stu-id="fecbf-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="fecbf-285">Gromadzenie maszyn wirtualnych jest również przydatne w przypadku aplikacji, które chcą trzymać się segmentów, które już nabyły, takich jak niektóre aplikacje serwera, które są dominującymi aplikacjami działającymi w systemie, aby uniknąć wyjątków z pamięci.</span><span class="sxs-lookup"><span data-stu-id="fecbf-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="fecbf-286">Zdecydowanie zaleca się, aby dokładnie przetestować aplikację podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="fecbf-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
