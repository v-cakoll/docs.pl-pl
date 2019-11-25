---
title: LOH w systemie Windows — .NET
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 5125b76dd26ffa4fb363ecf8449f65b490f57b93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283620"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="03808-102">Sterta dużego obiektu w systemach Windows</span><span class="sxs-lookup"><span data-stu-id="03808-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="03808-103">Moduł wyrzucania elementów bezużytecznych platformy .NET (GC) dzieli obiekty na małe i duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="03808-103">The .NET Garbage Collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="03808-104">Gdy obiekt jest duży, niektóre jego atrybuty stają się bardziej znaczące niż wtedy, gdy obiekt jest mały.</span><span class="sxs-lookup"><span data-stu-id="03808-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="03808-105">Na przykład kompaktowanie go — czyli skopiowanie go w pamięci w innym miejscu na stercie — może być kosztowne.</span><span class="sxs-lookup"><span data-stu-id="03808-105">For instance, compacting it -- that is, copying it in memory elsewhere on the heap -- can be expensive.</span></span> <span data-ttu-id="03808-106">Z tego powodu moduł zbierający elementy bezużyteczne platformy .NET umieszcza duże obiekty na stercie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="03808-106">Because of this, the .NET Garbage Collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="03808-107">W tym temacie zawarto szczegółowe omówienie sterty dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-107">In this topic, we'll look at the large object heap in depth.</span></span> <span data-ttu-id="03808-108">Będziemy omawiać, co kwalifikuje obiekt jako duży obiekt, jak zbierane są duże obiekty, oraz jakiego rodzaju wydajność nakłada duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="03808-108">We'll discuss what qualifies an object as a large object, how these large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03808-109">W tym temacie omówiono stertę dużego obiektu w .NET Framework i .NET Core działających tylko w systemach Windows.</span><span class="sxs-lookup"><span data-stu-id="03808-109">This topic discusses the large object heap in the .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="03808-110">Nie obejmuje to LOH działających w ramach implementacji platformy .NET na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="03808-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-large-object-heap-and-how-gc-handles-them"></a><span data-ttu-id="03808-111">Jak obiekt zostaje zakończony na stertie dużego obiektu i jak obsługuje je GC</span><span class="sxs-lookup"><span data-stu-id="03808-111">How an object ends up on the large object heap and how GC handles them</span></span>

<span data-ttu-id="03808-112">Jeśli rozmiar obiektu jest większy lub równy 85 000 bajtów, jest on traktowany jako duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="03808-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="03808-113">Ta liczba została określona przez dostrajanie wydajności.</span><span class="sxs-lookup"><span data-stu-id="03808-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="03808-114">Gdy żądanie alokacji obiektów jest przez 85 000 lub więcej bajtów, środowisko uruchomieniowe przydziela je na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="03808-115">Aby zrozumieć, co to oznacza, warto zapoznać się z podstawą dla programu .NET GC.</span><span class="sxs-lookup"><span data-stu-id="03808-115">To understand what this means, it's useful to examine some fundamentals about the .NET GC.</span></span>

<span data-ttu-id="03808-116">Moduł wyrzucania elementów bezużytecznych platformy .NET jest modułem zbierającym.</span><span class="sxs-lookup"><span data-stu-id="03808-116">The .NET Garbage Collector is a generational collector.</span></span> <span data-ttu-id="03808-117">Ma trzy generacje: generacji 0, generacja 1 i generacja 2.</span><span class="sxs-lookup"><span data-stu-id="03808-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="03808-118">Przyczyna 3 generacji polega na tym, że w dobrze dostrojonej aplikacji większość obiektów jest gen0.</span><span class="sxs-lookup"><span data-stu-id="03808-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="03808-119">Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny być związane po zakończeniu żądania.</span><span class="sxs-lookup"><span data-stu-id="03808-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="03808-120">Żądania alokacji w locie spowodują przekazanie go do Gen1 i umieszczenie w nim.</span><span class="sxs-lookup"><span data-stu-id="03808-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="03808-121">Zasadniczo Gen1 działa jako bufor między terenami młodych obiektów i długotrwałymi obszarami obiektów.</span><span class="sxs-lookup"><span data-stu-id="03808-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="03808-122">Małe obiekty są zawsze przydzieleni w generacji 0 i, w zależności od ich okresu istnienia, mogą zostać podwyższone do generacji 1 lub generation2.</span><span class="sxs-lookup"><span data-stu-id="03808-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="03808-123">Duże obiekty są zawsze przydzieleni w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="03808-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="03808-124">Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="03808-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="03808-125">Po zebraniu generacji zbierane są również wszystkie jego młodsze generacji.</span><span class="sxs-lookup"><span data-stu-id="03808-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="03808-126">Na przykład w przypadku, gdy jest wykonywana generacja 1 GC, zbierane są zarówno generacji 1, jak i 0.</span><span class="sxs-lookup"><span data-stu-id="03808-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="03808-127">Po zakończeniu generacji 2, cała sterta jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="03808-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="03808-128">Z tego powodu generacja 2 GC jest również nazywana *pełną operacją GC*.</span><span class="sxs-lookup"><span data-stu-id="03808-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="03808-129">Ten artykuł odnosi się do generacji 2 GC zamiast pełnego wykazu globalnego, ale warunki są zamienne.</span><span class="sxs-lookup"><span data-stu-id="03808-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="03808-130">Generacji zapewniają logiczny widok sterty GC.</span><span class="sxs-lookup"><span data-stu-id="03808-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="03808-131">Fizyczne obiekty w zarządzanych segmentach sterty.</span><span class="sxs-lookup"><span data-stu-id="03808-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="03808-132">*Segment sterty zarządzanej* jest fragmentem pamięci, która jest rezerwowana przez system operacyjny z systemu operacyjnego przez wywołanie [funkcji funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="03808-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="03808-133">Po załadowaniu środowiska CLR program GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterta małego obiektu lub raport o kondycji) i jeden dla dużych obiektów (sterta dużego obiektu).</span><span class="sxs-lookup"><span data-stu-id="03808-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="03808-134">Następnie żądania alokacji są spełnione przez umieszczenie obiektów zarządzanych w tych segmentach sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="03808-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="03808-135">Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany w segmencie dla raportu o kondycji. w przeciwnym razie jest umieszczany w segmencie LOH.</span><span class="sxs-lookup"><span data-stu-id="03808-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="03808-136">Segmenty są zatwierdzane (w mniejszych fragmentach), gdy do nich są przydzielone więcej i więcej obiektów.</span><span class="sxs-lookup"><span data-stu-id="03808-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="03808-137">W przypadku raportu o kondycji obiekty, które przeżyły wykaz GC, są podwyższane do nowej generacji.</span><span class="sxs-lookup"><span data-stu-id="03808-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="03808-138">Obiekty, które przeżyły kolekcję generacji 0, są teraz traktowane jak obiekty generacji 1 itd.</span><span class="sxs-lookup"><span data-stu-id="03808-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="03808-139">Jednak obiekty, które przeżyły z najstarszej generacji, są nadal uznawane za najstarszej generacji.</span><span class="sxs-lookup"><span data-stu-id="03808-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="03808-140">Innymi słowy, pozostałe z generacji 2 są obiektami generacji 2; i pozostałe z LOH są obiektami LOH (które są zbierane z Gen2).</span><span class="sxs-lookup"><span data-stu-id="03808-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="03808-141">Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty).</span><span class="sxs-lookup"><span data-stu-id="03808-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="03808-142">Tylko wykaz globalny może "przydzielić" obiekty w generacji 1 (przez podwyższenie poziomu od generacji 0) do generacji 2 (przez podwyższenie poziomu od pokoleń 1 i 2).</span><span class="sxs-lookup"><span data-stu-id="03808-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="03808-143">Po wyzwoleniu wyrzucania elementów bezużytecznych usługa GC śledzi dane za pomocą obiektów na żywo i kompaktuje je.</span><span class="sxs-lookup"><span data-stu-id="03808-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="03808-144">Ale ponieważ kompaktowanie jest kosztowne, *czyszczenie* wykazuje LOH; powoduje to bezpłatną listę niemartwych obiektów, które mogą być ponownie używane później w celu spełnienia żądań alokacji dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="03808-145">Sąsiadujące obiekty martwe są wprowadzane do jednego bezpłatnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="03808-146">.NET Core i .NET Framework (począwszy od .NET Framework 4.5.1) zawierają Właściwość <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType>, która pozwala użytkownikom na określenie, że LOH powinien zostać skompaktowany podczas następnego pełnego blokowania GC.</span><span class="sxs-lookup"><span data-stu-id="03808-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="03808-147">W przyszłości platforma .NET może zdecydować się na automatyczne kompaktowanie LOH.</span><span class="sxs-lookup"><span data-stu-id="03808-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="03808-148">Oznacza to, że w przypadku przydzielenia dużych obiektów i upewnienia się, że nie są one przenoszone, należy je nadal przypiąć.</span><span class="sxs-lookup"><span data-stu-id="03808-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="03808-149">Rysunek 1 ilustruje scenariusz, w którym generacji formularzy GC 1 po pierwszej generacji 0 GC, w której `Obj1` i `Obj3` są martwe, a następnie generacji tworzy 2 po pierwszej generacji 1 GC, gdzie `Obj2` i `Obj5` są martwe.</span><span class="sxs-lookup"><span data-stu-id="03808-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="03808-150">Należy zauważyć, że te i poniższe wartości są przeznaczone tylko do celów ilustracyjnych. zawierają one bardzo mało obiektów, aby lepiej zobaczyć, co się dzieje na stercie.</span><span class="sxs-lookup"><span data-stu-id="03808-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="03808-151">W rzeczywistości wiele więcej obiektów jest zwykle używanych w wykazie globalnym.</span><span class="sxs-lookup"><span data-stu-id="03808-151">In reality, many more objects are typically involved in a GC.</span></span>

![Rysunek 1: Gen 0 GC i gen 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="03808-153">Rysunek 1: generacja 0 i generacja 1 GC.</span><span class="sxs-lookup"><span data-stu-id="03808-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="03808-154">Rysunek 2 pokazuje, że po 2. generacji GC, który zauważał, że `Obj1` i `Obj2` są martwe, system GC tworzy ciągłe wolne miejsce poza pamięcią, która była używana przez `Obj1` i `Obj2`, a następnie była używana do zaspokojenia żądania alokacji dla `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="03808-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="03808-155">Do zaspokojenia żądań alokacji można także użyć odstępu po ostatnim obiekcie, `Obj3`, do końca segmentu.</span><span class="sxs-lookup"><span data-stu-id="03808-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Rysunek 2. po zakończeniu generacji 2 GC](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="03808-157">Rysunek 2. po zakończeniu generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="03808-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="03808-158">Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużego obiektu, GC najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="03808-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="03808-159">Jeśli to się nie powiedzie, spowoduje to wyzwolenie generacji 2 GC w celu zwolnienia miejsca na dysku.</span><span class="sxs-lookup"><span data-stu-id="03808-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="03808-160">Podczas generacji 1 lub 2. generacji wyrzucania elementów bezużytecznych zwalnia segmenty, które nie mają żadnych obiektów na żywo z powrotem do systemu operacyjnego przez wywołanie [funkcji VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="03808-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="03808-161">Miejsce po ostatnim aktywnym obiekcie na końcu segmentu zostaje cofnięte (z wyjątkiem segmentów tymczasowych, gdzie gen0/Gen1 na żywo, gdzie moduł zbierający elementy bezużyteczne wykonuje pewne zatwierdzenie, ponieważ aplikacja będzie od razu przydzielana).</span><span class="sxs-lookup"><span data-stu-id="03808-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="03808-162">A wolne miejsca pozostają zatwierdzone, chociaż są one resetowane, co oznacza, że system operacyjny nie musi zapisywać danych z powrotem na dysku.</span><span class="sxs-lookup"><span data-stu-id="03808-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="03808-163">Ponieważ LOH jest zbierany tylko podczas operacje odzyskiwania pamięci generacji 2, segment LOH można zwolnić tylko podczas tej operacji GC.</span><span class="sxs-lookup"><span data-stu-id="03808-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="03808-164">Rysunek 3 ilustruje scenariusz, w którym Moduł wyrzucania elementów bezużytecznych zwalnia jeden segment (segment 2) z powrotem do systemu operacyjnego i cofa więcej miejsca na pozostałych segmentach.</span><span class="sxs-lookup"><span data-stu-id="03808-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="03808-165">Jeśli konieczne jest użycie nieprzydzielonego miejsca na końcu segmentu w celu zaspokojenia żądań alokacji dużych obiektów, ponownie zostanie zatwierdzona pamięć.</span><span class="sxs-lookup"><span data-stu-id="03808-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="03808-166">(Aby uzyskać wyjaśnienie zatwierdzeń/anulowania zatwierdzenia, zapoznaj się z dokumentacją dotyczącą usługi [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="03808-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Rysunek 3. LOH po utworzeniu generacji 2 GC](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="03808-168">Rysunek 3: LOH po generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="03808-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="03808-169">Kiedy jest zbierany duży obiekt?</span><span class="sxs-lookup"><span data-stu-id="03808-169">When is a large object collected?</span></span>

<span data-ttu-id="03808-170">Ogólnie rzecz biorąc, wykaz globalny występuje, gdy wystąpi jedno z następujących trzech warunków:</span><span class="sxs-lookup"><span data-stu-id="03808-170">In general, a GC occurs when one of the following 3 conditions happens:</span></span>

- <span data-ttu-id="03808-171">Alokacja przekracza wartość progową generacji 0 lub dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="03808-172">Wartość progowa jest właściwością generacji.</span><span class="sxs-lookup"><span data-stu-id="03808-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="03808-173">Próg dla generacji jest ustawiany, gdy moduł wyrzucania elementów bezużytecznych przydzieli do niego obiekty.</span><span class="sxs-lookup"><span data-stu-id="03808-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="03808-174">Po przekroczeniu progu jest wyzwalana dla tej generacji.</span><span class="sxs-lookup"><span data-stu-id="03808-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="03808-175">W przypadku przydzielania małych lub dużych obiektów należy odpowiednio wykorzystać wartości progowe generacji 0 i LOH.</span><span class="sxs-lookup"><span data-stu-id="03808-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="03808-176">Gdy moduł wyrzucania elementów bezużytecznych alokuje do generacji 1 i 2, wykorzystuje ich progi.</span><span class="sxs-lookup"><span data-stu-id="03808-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="03808-177">Te progi są dynamicznie dostrajane podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="03808-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="03808-178">Jest to typowy przypadek; Większość operacje odzyskiwania pamięci występuje ze względu na alokacje na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="03808-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="03808-179">Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="03808-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="03808-180">Jeśli wywoływana jest bezparametrowa Metoda <xref:System.GC.Collect?displayProperty=nameWithType> lub inne Przeciążenie jest przenoszone <xref:System.GC.MaxGeneration?displayProperty=nameWithType> jako argument, LOH jest zbierane wraz z resztą zarządzanej sterty.</span><span class="sxs-lookup"><span data-stu-id="03808-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="03808-181">W systemie występuje niewielka ilość pamięci.</span><span class="sxs-lookup"><span data-stu-id="03808-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="03808-182">Dzieje się tak, gdy moduł zbierający elementy bezużyteczne otrzymuje powiadomienie o wysokim poziomie pamięci od systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="03808-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="03808-183">Jeśli moduł zbierający elementy bezużyteczne uzna, że wykonanie generacji 2 GC będzie produktywne, wyzwala.</span><span class="sxs-lookup"><span data-stu-id="03808-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="03808-184">Konsekwencje dotyczące wydajności LOH</span><span class="sxs-lookup"><span data-stu-id="03808-184">LOH Performance Implications</span></span>

<span data-ttu-id="03808-185">Alokacje na wydajność sterty dużego obiektu są w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="03808-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="03808-186">Koszt alokacji.</span><span class="sxs-lookup"><span data-stu-id="03808-186">Allocation cost.</span></span>

  <span data-ttu-id="03808-187">Środowisko CLR gwarantuje, że pamięć dla każdego nowego obiektu, który wydaje, zostaje wyczyszczona.</span><span class="sxs-lookup"><span data-stu-id="03808-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="03808-188">Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez czyszczenie pamięci (chyba że wyzwala on GC).</span><span class="sxs-lookup"><span data-stu-id="03808-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="03808-189">Jeśli trwa 2 cykle czyszczenia jednego bajtu, trwa 170 000 cykli, aby wyczyścić najmniejszy duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="03808-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="03808-190">Wyczyszczenie pamięci z 16 MB obiektu na maszynie 2GHz trwa około 16ms.</span><span class="sxs-lookup"><span data-stu-id="03808-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="03808-191">To raczej duży koszt.</span><span class="sxs-lookup"><span data-stu-id="03808-191">That's a rather large cost.</span></span>

- <span data-ttu-id="03808-192">Koszt zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="03808-192">Collection cost.</span></span>

  <span data-ttu-id="03808-193">Ponieważ LOH i generacja 2 są zbierane razem, gdy zostanie przekroczony próg jednego z nich, zostanie wyzwolona kolekcja generacji 2.</span><span class="sxs-lookup"><span data-stu-id="03808-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="03808-194">Jeśli kolekcja generacji 2 jest wyzwalana ze względu na LOH, generacja 2 nie będzie konieczna znacznie mniejsza po GC.</span><span class="sxs-lookup"><span data-stu-id="03808-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="03808-195">Jeśli nie ma dużo danych w generacji 2, ma to minimalny wpływ na.</span><span class="sxs-lookup"><span data-stu-id="03808-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="03808-196">Ale jeśli generacja 2 jest duża, może to spowodować problemy z wydajnością w przypadku wyzwolenia wielu operacje odzyskiwania pamięci generacji 2.</span><span class="sxs-lookup"><span data-stu-id="03808-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="03808-197">Jeśli wiele dużych obiektów jest przydzielanych na bardzo tymczasowym czasie i masz duży raport o kondycji, można wyznaczyć zbyt dużo czasu na wykonanie operacje odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="03808-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="03808-198">Ponadto koszt alokacji można naprawdę dodać, jeśli będziesz nadal przydzielać i przełączać się do bardzo dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="03808-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="03808-199">Elementy tablicy z typami referencyjnymi.</span><span class="sxs-lookup"><span data-stu-id="03808-199">Array elements with reference types.</span></span>

  <span data-ttu-id="03808-200">Bardzo duże obiekty na LOH są zwykle tablicami (bardzo rzadko jest to obiekt wystąpienia, który jest naprawdę duży).</span><span class="sxs-lookup"><span data-stu-id="03808-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="03808-201">Jeśli elementy tablicy są rozbudowane odwołania, wiąże się to z kosztem nieobecnym, jeśli elementy nie są rozbudowane.</span><span class="sxs-lookup"><span data-stu-id="03808-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="03808-202">Jeśli element nie zawiera żadnych odwołań, Moduł wyrzucania elementów bezużytecznych nie musi przechodzić przez tablicę.</span><span class="sxs-lookup"><span data-stu-id="03808-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="03808-203">Na przykład, jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów implementacji jest odwołanie do węzła prawego i lewego węzła przez rzeczywiste węzły:</span><span class="sxs-lookup"><span data-stu-id="03808-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="03808-204">Jeśli `num_nodes` jest duże, moduł zbierający elementy bezużyteczne musi przejść przez co najmniej dwa odwołania na element.</span><span class="sxs-lookup"><span data-stu-id="03808-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="03808-205">Alternatywnym podejściem jest przechowywanie indeksu prawego i lewego węzła:</span><span class="sxs-lookup"><span data-stu-id="03808-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="03808-206">Zamiast odwoływać się do danych z lewego węzła jako `left.d`, należy odwołać się do niego jako `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="03808-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="03808-207">A Moduł wyrzucania elementów bezużytecznych nie musi odwoływać się do żadnych odwołań dla lewego i prawego węzła.</span><span class="sxs-lookup"><span data-stu-id="03808-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="03808-208">Od trzech czynników pierwsze dwa są zwykle ważniejsze od trzeciej.</span><span class="sxs-lookup"><span data-stu-id="03808-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="03808-209">W związku z tym zalecamy przydzielenie puli dużych obiektów, których ponowne użycie nie jest możliwe do przydzielenia tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="03808-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collecting-performance-data-for-the-loh"></a><span data-ttu-id="03808-210">Zbieranie danych wydajności dla LOH</span><span class="sxs-lookup"><span data-stu-id="03808-210">Collecting performance data for the LOH</span></span>

<span data-ttu-id="03808-211">Przed zebraniem danych wydajności dla określonego obszaru należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="03808-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="03808-212">Znaleziono dowody, które należy przejrzeć w tym obszarze.</span><span class="sxs-lookup"><span data-stu-id="03808-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="03808-213">Wyczerpuje się inne obszary, które znasz, bez znalezienia wszystkiego, co może wyjaśnić problem z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="03808-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="03808-214">Zapoznaj się [z blogiem, aby](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) uzyskać więcej informacji na temat podstawy pamięci i procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="03808-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="03808-215">Za pomocą poniższych narzędzi można zbierać dane dotyczące wydajności LOH:</span><span class="sxs-lookup"><span data-stu-id="03808-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="03808-216">Liczniki wydajności pamięci CLR platformy .NET</span><span class="sxs-lookup"><span data-stu-id="03808-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="03808-217">Zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="03808-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="03808-218">Debuger</span><span class="sxs-lookup"><span data-stu-id="03808-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="03808-219">Liczniki wydajności pamięci CLR platformy .NET</span><span class="sxs-lookup"><span data-stu-id="03808-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="03808-220">Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (Chociaż zalecamy korzystanie z [zdarzeń ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="03808-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="03808-221">Monitor wydajności można skonfigurować przez dodanie żądanych liczników, jak pokazano na rysunku 4.</span><span class="sxs-lookup"><span data-stu-id="03808-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="03808-222">Te, które są istotne dla LOH są:</span><span class="sxs-lookup"><span data-stu-id="03808-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="03808-223">**Kolekcje generacji 2**</span><span class="sxs-lookup"><span data-stu-id="03808-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="03808-224">Przedstawia liczbę przypadków, w których wystąpiło operacje odzyskiwania pamięci generacji 2 od momentu rozpoczęcia procesu.</span><span class="sxs-lookup"><span data-stu-id="03808-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="03808-225">Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywanej również pełnym wyrzucaniem elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="03808-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="03808-226">Ten licznik wyświetla ostatnią obserwowana wartość.</span><span class="sxs-lookup"><span data-stu-id="03808-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="03808-227">**Rozmiar sterty dla dużego obiektu**</span><span class="sxs-lookup"><span data-stu-id="03808-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="03808-228">Wyświetla bieżący rozmiar (w bajtach), w tym wolne miejsce LOH.</span><span class="sxs-lookup"><span data-stu-id="03808-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="03808-229">Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.</span><span class="sxs-lookup"><span data-stu-id="03808-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="03808-230">Typowym sposobem na przyjrzeć się licznikom wydajności jest Monitor wydajności (Perfmon. exe).</span><span class="sxs-lookup"><span data-stu-id="03808-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="03808-231">Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, które Cię interesują.</span><span class="sxs-lookup"><span data-stu-id="03808-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="03808-232">Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:</span><span class="sxs-lookup"><span data-stu-id="03808-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="03808-233">![zrzut ekranu, który pokazuje Dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="03808-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="03808-234">Rysunek 4. LOH po generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="03808-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="03808-235">Liczniki wydajności mogą być również wykonywane programowo.</span><span class="sxs-lookup"><span data-stu-id="03808-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="03808-236">Wiele osób zbiera je w ten sposób w ramach procesu rutynowego testowania.</span><span class="sxs-lookup"><span data-stu-id="03808-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="03808-237">Gdy znajdują się w nich liczniki z wartościami, które są niezwykłe, wykorzystują inne metody, aby uzyskać bardziej szczegółowe dane, które pomagają w badaniu.</span><span class="sxs-lookup"><span data-stu-id="03808-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="03808-238">Zalecamy korzystanie z zdarzeń ETW zamiast liczników wydajności, ponieważ funkcja ETW udostępnia znacznie bogatsze informacje.</span><span class="sxs-lookup"><span data-stu-id="03808-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="03808-239">zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="03808-239">ETW events</span></span>

<span data-ttu-id="03808-240">Moduł wyrzucania elementów bezużytecznych udostępnia rozbudowany zestaw zdarzeń ETW, które ułatwiają zrozumienie działania sterty i przyczyn.</span><span class="sxs-lookup"><span data-stu-id="03808-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="03808-241">Następujące wpisy w blogu pokazują, jak zbierać i zrozumieć zdarzenia GC z funkcją ETW:</span><span class="sxs-lookup"><span data-stu-id="03808-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="03808-242">Zdarzenia ETW odzyskiwania pamięci — 1</span><span class="sxs-lookup"><span data-stu-id="03808-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="03808-243">Zdarzenia ETW odzyskiwania pamięci — 2</span><span class="sxs-lookup"><span data-stu-id="03808-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="03808-244">Zdarzenia ETW odzyskiwania pamięci — 3</span><span class="sxs-lookup"><span data-stu-id="03808-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="03808-245">Zdarzenia ETW odzyskiwania pamięci — 4</span><span class="sxs-lookup"><span data-stu-id="03808-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="03808-246">Aby zidentyfikować nadmierną operacje odzyskiwania pamięci generacji 2 spowodowaną przez tymczasowe alokacje LOH, zapoznaj się z kolumną przyczyna wyzwalacza dla operacje odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="03808-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="03808-247">Dla prostego testu, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje dotyczące zdarzeń ETW za pomocą następującego wiersza polecenia [Narzędzia PerfView](https://www.microsoft.com/download/details.aspx?id=28567) :</span><span class="sxs-lookup"><span data-stu-id="03808-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="03808-248">Wynik jest podobny do tego:</span><span class="sxs-lookup"><span data-stu-id="03808-248">The result is something like this:</span></span>

<span data-ttu-id="03808-249">![zrzut ekranu, który pokazuje zdarzenia ETW w narzędzia PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="03808-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="03808-250">Rysunek 5. zdarzenia ETW wyświetlane przy użyciu narzędzia PerfView</span><span class="sxs-lookup"><span data-stu-id="03808-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="03808-251">Jak widać, wszystkie operacje odzyskiwania pamięci są generacji 2 operacje odzyskiwania pamięci i są wyzwalane przez AllocLarge, co oznacza, że przydzielanie dużego obiektu wyzwolił ten wykaz GC.</span><span class="sxs-lookup"><span data-stu-id="03808-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="03808-252">Wiemy, że te przydziały są tymczasowe ze względu na to, że procent **przeżycia LOH%** Column brzmi 1%.</span><span class="sxs-lookup"><span data-stu-id="03808-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="03808-253">Można zbierać dodatkowe zdarzenia ETW, które informują użytkownika, kto przydzielił te duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="03808-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="03808-254">Następujący wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="03808-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="03808-255">zbiera zdarzenie AllocationTick, które jest uruchamiane około każdej 100 000 przydziałów.</span><span class="sxs-lookup"><span data-stu-id="03808-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="03808-256">Innymi słowy, zdarzenie jest wywoływane przy każdym przydzieleniu dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="03808-257">Następnie można przyjrzeć się jednemu z widoków alokacji sterty GC pokazujących stosy wywołań przydzieloną duże obiekty:</span><span class="sxs-lookup"><span data-stu-id="03808-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="03808-258">![zrzut ekranu, który pokazuje widok sterty modułu wyrzucania elementów bezużytecznych.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="03808-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="03808-259">Ilustracja 6. Widok alokacji sterty GC</span><span class="sxs-lookup"><span data-stu-id="03808-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="03808-260">Jak widać, jest to bardzo prosty test, który po prostu przypisuje duże obiekty z metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="03808-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="03808-261">Debuger</span><span class="sxs-lookup"><span data-stu-id="03808-261">A debugger</span></span>

<span data-ttu-id="03808-262">Jeśli wszystko jest zrzutem pamięci i chcesz sprawdzić, jakie obiekty faktycznie znajdują się w LOH, możesz użyć [rozszerzenia debugera sos](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) dostarczonego przez platformę .NET.</span><span class="sxs-lookup"><span data-stu-id="03808-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="03808-263">Polecenia debugowania wymienione w tej sekcji dotyczą [debugerów systemu Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="03808-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="03808-264">Poniżej przedstawiono przykładowe dane wyjściowe analizy LOH:</span><span class="sxs-lookup"><span data-stu-id="03808-264">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="03808-265">Rozmiar sterty LOH to (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów.</span><span class="sxs-lookup"><span data-stu-id="03808-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="03808-266">Między adresami 023e1000 i 033db630, 8 008 736 bajty są zajęte przez tablicę obiektów <xref:System.Object?displayProperty=nameWithType>, 6 663 696 bajty są zajęte przez tablicę obiektów <xref:System.Byte?displayProperty=nameWithType> i 2 081 792 bajty są zajęte przez wolne miejsce.</span><span class="sxs-lookup"><span data-stu-id="03808-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="03808-267">Czasami debuger pokazuje, że łączny rozmiar LOH jest mniejszy niż 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="03808-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="03808-268">Dzieje się tak, ponieważ środowisko uruchomieniowe używa LOH do alokowania niektórych obiektów, które są mniejsze niż w przypadku dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="03808-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="03808-269">Ponieważ LOH nie jest kompaktowana, czasami LOH jest uważana za źródło fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="03808-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="03808-270">Fragmentacja oznacza:</span><span class="sxs-lookup"><span data-stu-id="03808-270">Fragmentation means:</span></span>

- <span data-ttu-id="03808-271">Fragmentacja zarządzanego sterty, która jest wskazywana przez ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="03808-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="03808-272">W SoS polecenie `!dumpheap –type Free` Wyświetla ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="03808-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="03808-273">Fragmentacja przestrzeni adresowej pamięci wirtualnej (VM), czyli pamięci oznaczonej jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="03808-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="03808-274">Można to zrobić za pomocą różnych poleceń debugera w programie WinDbg.</span><span class="sxs-lookup"><span data-stu-id="03808-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="03808-275">Poniższy przykład przedstawia fragmentację w obszarze maszyny wirtualnej:</span><span class="sxs-lookup"><span data-stu-id="03808-275">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="03808-276">Jest to bardziej powszechne, aby zobaczyć fragmentację maszyny wirtualnej spowodowaną przez tymczasowe duże obiekty, które wymagają modułu wyrzucania elementów bezużytecznych, aby często uzyskać nowe zarządzane segmenty sterty z systemu operacyjnego i zwalniać puste z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="03808-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="03808-277">Aby sprawdzić, czy LOH powoduje fragmentację maszyny wirtualnej, można ustawić punkt przerwania dla [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) , aby zobaczyć, kto je wywołuje.</span><span class="sxs-lookup"><span data-stu-id="03808-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="03808-278">Na przykład aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z systemu operacyjnego, można ustawić punkt przerwania w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="03808-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="03808-279">To polecenie dzieli się na debuger i pokazuje stos wywołań tylko wtedy, gdy [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływana z rozmiarem alokacji większym niż 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="03808-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="03808-280">Środowisko CLR 2,0 dodaliśmy funkcję o nazwie *VM Hoarding* , która może być przydatna w scenariuszach, w których segmenty (w tym duże i małe sterty obiektów) są często uzyskiwane i zwalniane.</span><span class="sxs-lookup"><span data-stu-id="03808-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="03808-281">Aby określić Hoarding maszyny wirtualnej, należy określić flagę uruchamiania o nazwie `STARTUP_HOARD_GC_VM` za pośrednictwem interfejsu API hostingu.</span><span class="sxs-lookup"><span data-stu-id="03808-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="03808-282">Zamiast zwalniać puste segmenty z powrotem do systemu operacyjnego, środowisko CLR zwalnia pamięć w tych segmentach i umieszcza je na liście gotowości.</span><span class="sxs-lookup"><span data-stu-id="03808-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="03808-283">(Należy pamiętać, że środowisko CLR nie wykonuje tego w przypadku segmentów, które są zbyt duże). Środowisko CLR później używa tych segmentów, aby spełnić nowe żądania segmentów.</span><span class="sxs-lookup"><span data-stu-id="03808-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="03808-284">Następnym razem, gdy aplikacja będzie potrzebowała nowego segmentu, środowisko CLR używa jednego z tej listy w stanie wstrzymania, jeśli będzie można je znaleźć wystarczająco duże.</span><span class="sxs-lookup"><span data-stu-id="03808-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="03808-285">Hoarding maszyny wirtualnej jest również przydatne w przypadku aplikacji, które mają być przechowywane do segmentów, które już uzyskały, takich jak niektóre aplikacje serwerowe, które są aplikacjami dominującymi uruchomionymi w systemie, aby uniknąć wyjątków z pamięci.</span><span class="sxs-lookup"><span data-stu-id="03808-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out of memory exceptions.</span></span>

<span data-ttu-id="03808-286">Zdecydowanie zalecamy dokładne przetestowanie aplikacji podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="03808-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
