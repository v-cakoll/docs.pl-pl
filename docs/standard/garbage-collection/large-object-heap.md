---
title: Sterta dużych obiektów (LOH) w systemie Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102271"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="2c7f2-102">Sterta dużych obiektów w systemach Windows</span><span class="sxs-lookup"><span data-stu-id="2c7f2-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="2c7f2-103">Moduł zbierający elementy bezużyteczne .NET (GC) dzieli obiekty na małe i duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-103">The .NET garbage collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="2c7f2-104">Gdy obiekt jest duży, niektóre z jego atrybutów stają się bardziej znaczące niż jeśli obiekt jest mały.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="2c7f2-105">Na przykład kompaktowanie&mdash;go, czyli kopiowanie go w&mdash;pamięci w innym miejscu na stercie może być kosztowne.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-105">For instance, compacting it&mdash;that is, copying it in memory elsewhere on the heap&mdash;can be expensive.</span></span> <span data-ttu-id="2c7f2-106">Z tego powodu moduł zbierający elementy bezużyteczne umieszcza duże obiekty na stercie dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-106">Because of this, the garbage collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="2c7f2-107">W tym artykule omówiono, co kwalifikuje obiekt jako duży obiekt, jak duże obiekty są zbierane i jakiego rodzaju wpływ na wydajność nakładają duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-107">This article discusses what qualifies an object as a large object, how large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2c7f2-108">W tym artykule omówiono sterty dużych obiektów w programie .NET Framework i .NET Core uruchomionym tylko w systemach Windows.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-108">This article discusses the large object heap in .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="2c7f2-109">Nie obejmuje loh działających na implementacje .NET na innych platformach.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-109">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-loh"></a><span data-ttu-id="2c7f2-110">Jak obiekt kończy się na LOH</span><span class="sxs-lookup"><span data-stu-id="2c7f2-110">How an object ends up on the LOH</span></span>

<span data-ttu-id="2c7f2-111">Jeśli obiekt jest większy lub równy rozmiarowi 85 000 bajtów, jest uważany za duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-111">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="2c7f2-112">Liczba ta została określona przez dostrajanie wydajności.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-112">This number was determined by performance tuning.</span></span> <span data-ttu-id="2c7f2-113">Gdy żądanie alokacji obiektu jest dla 85 000 lub więcej bajtów, środowisko wykonawcze przydziela je na stercie dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-113">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="2c7f2-114">Aby zrozumieć, co to oznacza, warto zbadać niektóre podstawy dotyczące modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-114">To understand what this means, it's useful to examine some fundamentals about the garbage collector.</span></span>

<span data-ttu-id="2c7f2-115">Moduł zbierający elementy bezużyteczne jest modułem zbierającym generację.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-115">The garbage collector is a generational collector.</span></span> <span data-ttu-id="2c7f2-116">Ma trzy pokolenia: pokolenie 0, pokolenie 1 i pokolenie 2.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-116">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="2c7f2-117">Powodem posiadania 3 pokoleń jest to, że w dobrze dostrojone aplikacji, większość obiektów umiera w gen0.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-117">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="2c7f2-118">Na przykład w aplikacji serwera alokacje skojarzone z każdym żądaniem powinny umrzeć po zakończeniu żądania.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-118">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="2c7f2-119">Wnioski o przydział w locie sprawią, że będzie on akcjum1 i tam umrze.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-119">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="2c7f2-120">Zasadniczo gen1 działa jako bufor między młodymi obszarami obiektów a obszarami obiektów o długim okresie życia.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-120">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="2c7f2-121">Małe obiekty są zawsze przydzielane w generacji 0 i, w zależności od ich żywotności, mogą być promowane do generacji 1 lub generacji2.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-121">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="2c7f2-122">Duże obiekty są zawsze przydzielane w generacji 2.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-122">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="2c7f2-123">Duże obiekty należą do generacji 2, ponieważ są zbierane tylko podczas kolekcji generacji 2.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-123">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="2c7f2-124">Po zebraniu pokolenia zbierane są również wszystkie jego młodsze pokolenia.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-124">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="2c7f2-125">Na przykład, gdy dzieje się generacji 1 GC, zarówno generacji 1 i 0 są zbierane.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-125">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="2c7f2-126">A kiedy dzieje się generacji 2 GC, cała sterta jest zbierana.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-126">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="2c7f2-127">Z tego powodu, generacji 2 GC jest również nazywany *pełnym GC*.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-127">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="2c7f2-128">Ten artykuł odnosi się do generacji 2 GC zamiast pełnego GC, ale warunki są wymienne.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-128">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="2c7f2-129">Pokolenia zapewniają logiczny widok sterty GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-129">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="2c7f2-130">Fizycznie obiekty znajdują się w segmentach zarządzanych sterty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-130">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="2c7f2-131">*Segment zarządzanego sterty* jest fragmentem pamięci, który GC rezerwuje z systemu operacyjnego, wywołując [virtualalloc funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) w imieniu kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-131">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="2c7f2-132">Po załadowaniu clr, GC przydziela dwa początkowe segmenty sterty: jeden dla małych obiektów (sterty małych obiektów lub SOH) i jeden dla dużych obiektów (sterty dużych obiektów).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-132">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="2c7f2-133">Żądania alokacji są następnie spełnione przez umieszczenie zarządzanych obiektów w tych segmentach zarządzanych sterty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-133">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="2c7f2-134">Jeśli obiekt jest mniejszy niż 85 000 bajtów, jest umieszczany na segmencie dla soh; w przeciwnym razie jest on umieszczany na segmencie LOH.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-134">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="2c7f2-135">Segmenty są zatwierdzane (w mniejszych fragmentów), jak coraz więcej obiektów są przydzielane do nich.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-135">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="2c7f2-136">Dla SOH obiekty, które przetrwają GC są promowane do następnej generacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-136">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="2c7f2-137">Obiekty, które przetrwają kolekcję generacji 0 są teraz uważane za obiekty generacji 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-137">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="2c7f2-138">Jednak obiekty, które przetrwają najstarszą generację, są nadal uważane za najstarsze pokolenie.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-138">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="2c7f2-139">Innymi słowy, ocalałych z generacji 2 są obiekty generacji 2; i ocalałych z LOH są obiekty LOH (które są zbierane z gen2).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-139">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="2c7f2-140">Kod użytkownika można przydzielić tylko w generacji 0 (małe obiekty) lub LOH (duże obiekty).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-140">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="2c7f2-141">Tylko GC może "przydzielać" obiekty w pierwszej generacji (poprzez promowanie ocalałych z pokolenia 0) i generacji 2 (poprzez promowanie ocalałych z pokoleń 1 i 2).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-141">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="2c7f2-142">Po wyzwoleniu wyrzucania elementów bezużytecznych GC śledzi obiekty aktywne i kompakuje je.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-142">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="2c7f2-143">Ale ponieważ zagęszczanie jest drogie, GC *zamiata* LOH; sprawia, że wolna lista z martwych obiektów, które mogą być ponownie ponownie zaspokojone później, aby spełnić żądania alokacji dużych obiektów.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-143">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="2c7f2-144">Sąsiadujące martwe obiekty są przekształcane w jeden wolny obiekt.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-144">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="2c7f2-145">.NET Core i .NET Framework (począwszy od .NET Framework 4.5.1) zawierają <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> właściwość, która umożliwia użytkownikom określenie, że LOH powinny być kompaktowane podczas następnego pełnego blokowania GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-145">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="2c7f2-146">A w przyszłości .NET może zdecydować się na automatyczne kompaktowanie LOH.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-146">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="2c7f2-147">Oznacza to, że jeśli przydzielisz duże obiekty i chcesz się upewnić, że nie są one przesuniętye, nadal należy je przypiąć.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-147">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="2c7f2-148">Rysunek 1 ilustruje scenariusz, w którym GC tworzy generację `Obj1` `Obj3` 1 po pierwszej generacji 0 GC, gdzie `Obj2` `Obj5` i są martwe, i tworzy generację 2 po pierwszej generacji 1 GC, gdzie i są martwe.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-148">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="2c7f2-149">Należy pamiętać, że to i następujące liczby są tylko w celach ilustracyjnych; zawierają one bardzo niewiele obiektów, aby lepiej pokazać, co dzieje się na stercie.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-149">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="2c7f2-150">W rzeczywistości wiele więcej obiektów są zazwyczaj zaangażowane w GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-150">In reality, many more objects are typically involved in a GC.</span></span>

![Rysunek 1: Gen 0 GC i gen 1 GC](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="2c7f2-152">Rysunek 1: Generacja 0 i generacja 1 GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-152">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="2c7f2-153">Rysunek 2 pokazuje, że po generacji `Obj1` `Obj2` 2 GC, który widział, że i są martwe, GC `Obj1` `Obj2`tworzy przyległe wolne miejsce `Obj4`z pamięci, które były zajęte przez i , który następnie został użyty do spełnienia żądania alokacji dla .</span><span class="sxs-lookup"><span data-stu-id="2c7f2-153">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="2c7f2-154">Spacja po ostatnim `Obj3`obiekcie , do końca segmentu może być również używana do spełniania żądań alokacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-154">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Rysunek 2: Po gen 2 GC](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="2c7f2-156">Rysunek 2: Po generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="2c7f2-156">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="2c7f2-157">Jeśli nie ma wystarczającej ilości wolnego miejsca, aby pomieścić żądania alokacji dużych obiektów, GC najpierw próbuje uzyskać więcej segmentów z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-157">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="2c7f2-158">Jeśli to się nie powiedzie, wyzwala generacji 2 GC w nadziei na uwolnienie trochę miejsca.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-158">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="2c7f2-159">Podczas generacji 1 lub generacji 2 GC moduł zbierający elementy bezużyteczne zwalnia segmenty, które nie mają na nich obiektów na żywo z powrotem do systemu operacyjnego, wywołując [virtualfree funkcji](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-159">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="2c7f2-160">Miejsce po ostatnim obiektu na żywo do końca segmentu jest umorzony (z wyjątkiem segmentu efemeryczny, gdzie gen0/gen1 żyć, gdzie moduł zbierający elementy bezużyteczne przechowuje niektóre zatwierdzone, ponieważ aplikacja będzie przydzielanie w nim od razu).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-160">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="2c7f2-161">Wolne miejsca pozostają zatwierdzone, mimo że są resetowane, co oznacza, że system operacyjny nie musi zapisywać w nich danych z powrotem na dysk.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-161">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="2c7f2-162">Ponieważ LOH jest zbierany tylko podczas generacji 2 GC, segment LOH może zostać uwolniony tylko podczas takiego GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-162">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="2c7f2-163">Rysunek 3 ilustruje scenariusz, w którym moduł zbierający elementy bezużyteczne zwalnia jeden segment (segment 2) z powrotem do systemu operacyjnego i ulikuje więcej miejsca na pozostałych segmentach.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-163">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="2c7f2-164">Jeśli musi użyć miejsca umorzone na końcu segmentu, aby spełnić żądania alokacji dużych obiektów, zatwierdza pamięć ponownie.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-164">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="2c7f2-165">(Aby uzyskać wyjaśnienie commit/decommit, zobacz dokumentację [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-165">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Rysunek 3: LOH po gen 2 GC](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="2c7f2-167">Rysunek 3: LOH po generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="2c7f2-167">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="2c7f2-168">Kiedy zbierany jest duży obiekt?</span><span class="sxs-lookup"><span data-stu-id="2c7f2-168">When is a large object collected?</span></span>

<span data-ttu-id="2c7f2-169">Ogólnie rzecz biorąc, GC występuje w jednym z następujących trzech warunków:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-169">In general, a GC occurs under one of the following three conditions:</span></span>

- <span data-ttu-id="2c7f2-170">Alokacja przekracza próg generacji 0 lub dużego obiektu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-170">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="2c7f2-171">Próg jest właściwością pokolenia.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-171">The threshold is a property of a generation.</span></span> <span data-ttu-id="2c7f2-172">Próg dla generacji jest ustawiany, gdy moduł zbierający elementy bezużyteczne przydziela obiekty do niego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-172">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="2c7f2-173">Po przekroczeniu progu gc jest wyzwalany na tej generacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-173">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="2c7f2-174">Podczas przydzielania małych lub dużych obiektów, zużywają generacji 0 i progi LOH, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-174">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="2c7f2-175">Gdy moduł zbierający elementy bezużyteczne przydziela do generacji 1 i 2, zużywa ich progi.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-175">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="2c7f2-176">Progi te są dynamicznie dostrojone podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-176">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="2c7f2-177">Jest to typowy przypadek; większość gc się z powodu alokacji na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-177">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="2c7f2-178">Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-178">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="2c7f2-179">Jeśli metoda <xref:System.GC.Collect?displayProperty=nameWithType> bez parametrów jest wywoływana <xref:System.GC.MaxGeneration?displayProperty=nameWithType> lub inne przeciążenie jest przekazywana jako argument, LOH są zbierane wraz z resztą zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-179">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="2c7f2-180">System znajduje się w sytuacji małej pamięci.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-180">The system is in low memory situation.</span></span>

  <span data-ttu-id="2c7f2-181">Dzieje się tak, gdy moduł zbierający elementy bezużyteczne odbiera powiadomienie o wysokiej pamięci z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-181">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="2c7f2-182">Jeśli moduł zbierający elementy bezużyteczne uważa, że robi generacji 2 GC będzie produktywne, wyzwala jeden.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-182">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="2c7f2-183">Wpływ loh na wydajność</span><span class="sxs-lookup"><span data-stu-id="2c7f2-183">LOH performance implications</span></span>

<span data-ttu-id="2c7f2-184">Alokacje na stercie dużych obiektów wpływają na wydajność w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-184">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="2c7f2-185">Koszt alokacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-185">Allocation cost.</span></span>

  <span data-ttu-id="2c7f2-186">CLR sprawia, że gwarancja, że pamięć dla każdego nowego obiektu, który daje jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-186">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="2c7f2-187">Oznacza to, że koszt alokacji dużego obiektu jest całkowicie zdominowany przez wyczyszczenie pamięci (chyba że wyzwala GC).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-187">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="2c7f2-188">Jeśli trwa 2 cykle, aby wyczyścić jeden bajt, trwa 170.000 cykli, aby wyczyścić najmniejszy duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-188">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="2c7f2-189">Wyczyszczenie pamięci obiektu o rozmiarze 16 MB na komputerze 2GHz zajmuje około 16 m.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-189">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="2c7f2-190">To dość duży koszt.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-190">That's a rather large cost.</span></span>

- <span data-ttu-id="2c7f2-191">Koszt odbioru.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-191">Collection cost.</span></span>

  <span data-ttu-id="2c7f2-192">Ponieważ LOH i generacji 2 są zbierane razem, jeśli jeden próg zostanie przekroczony, kolekcja generacji 2 jest wyzwalany.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-192">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="2c7f2-193">Jeśli kolekcja generacji 2 jest wyzwalana z powodu LOH, generacja 2 nie musi być znacznie mniejsza po GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-193">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="2c7f2-194">Jeśli nie ma zbyt wiele danych na temat generacji 2, ma to minimalny wpływ.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-194">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="2c7f2-195">Ale jeśli generacja 2 jest duża, może powodować problemy z wydajnością, jeśli zostanie uruchomionych wiele gc generacji 2.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-195">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="2c7f2-196">Jeśli wiele dużych obiektów są przydzielane na bardzo tymczasowe i masz duży SOH, można spędzać zbyt dużo czasu robi GCs.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-196">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="2c7f2-197">Ponadto koszt alokacji może naprawdę się sumować, jeśli nadal przydzielasz i puszczasz naprawdę duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-197">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="2c7f2-198">Elementy tablicy z typami odwołań.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-198">Array elements with reference types.</span></span>

  <span data-ttu-id="2c7f2-199">Bardzo duże obiekty na LOH są zwykle tablice (bardzo rzadko mają obiekt wystąpienia, który jest naprawdę duży).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-199">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="2c7f2-200">Jeśli elementy tablicy są bogate w odwołania, ponosi koszt, który nie jest obecny, jeśli elementy nie są bogate w odwołania.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-200">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="2c7f2-201">Jeśli element nie zawiera żadnych odwołań, moduł zbierający elementy bezużyteczne nie trzeba przejść przez tablicę w ogóle.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-201">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="2c7f2-202">Na przykład jeśli używasz tablicy do przechowywania węzłów w drzewie binarnym, jednym ze sposobów jego zaimplementowania jest odwoływanie się do prawego i lewego węzła węzła przez rzeczywiste węzły:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-202">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="2c7f2-203">Jeśli `num_nodes` jest duży, moduł zbierający elementy bezużyteczne musi przejść przez co najmniej dwa odwołania na element.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-203">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="2c7f2-204">Alternatywnym podejściem jest przechowywanie indeksu węzłów po prawej i lewej stronie:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-204">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="2c7f2-205">Zamiast odwoływać się do danych lewego węzła `left.d`jako `binary_tr[left_index].d`, odnosisz się do niego jako .</span><span class="sxs-lookup"><span data-stu-id="2c7f2-205">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="2c7f2-206">A moduł zbierający elementy bezużyteczne nie trzeba patrzeć na żadnych odwołań do lewego i prawego węzła.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-206">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="2c7f2-207">Z trzech czynników, pierwsze dwa są zwykle bardziej znaczące niż trzeci.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-207">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="2c7f2-208">Z tego powodu zaleca się przydzielić pulę dużych obiektów, które można ponownie użyć zamiast przydzielania tymczasowych.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-208">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collect-performance-data-for-the-loh"></a><span data-ttu-id="2c7f2-209">Zbieranie danych dotyczących wydajności dla LOH</span><span class="sxs-lookup"><span data-stu-id="2c7f2-209">Collect performance data for the LOH</span></span>

<span data-ttu-id="2c7f2-210">Przed zebraniem danych o wydajności dla określonego obszaru należy już wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-210">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="2c7f2-211">Znaleziono dowody, że należy spojrzeć na ten obszar.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-211">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="2c7f2-212">Wyczerpane inne obszary, które znasz, nie znajdując niczego, co mogłoby wyjaśnić problem z wydajnością, który widziałeś.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-212">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="2c7f2-213">Zobacz blog [Zrozumieć problem, zanim spróbujesz znaleźć rozwiązanie, aby uzyskać](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) więcej informacji na temat podstaw pamięci i procesora.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-213">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="2c7f2-214">Do zbierania danych na temat wydajności LOH można użyć następujących narzędzi:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-214">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="2c7f2-215">Liczniki wydajności pamięci CLR platformy .NET</span><span class="sxs-lookup"><span data-stu-id="2c7f2-215">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="2c7f2-216">zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="2c7f2-216">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="2c7f2-217">Debuger</span><span class="sxs-lookup"><span data-stu-id="2c7f2-217">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="2c7f2-218">Liczniki wydajności pamięci CLR platformy .NET</span><span class="sxs-lookup"><span data-stu-id="2c7f2-218">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="2c7f2-219">Te liczniki wydajności są zwykle dobrym pierwszym krokiem w badaniu problemów z wydajnością (chociaż zaleca się używanie [zdarzeń ETW).](#etw-events)</span><span class="sxs-lookup"><span data-stu-id="2c7f2-219">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="2c7f2-220">Monitor wydajności można skonfigurować, dodając żądane liczniki, jak pokazano na rysunku 4.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-220">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="2c7f2-221">Te, które są istotne dla LOH są:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-221">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="2c7f2-222">**Kolekcje Gen 2**</span><span class="sxs-lookup"><span data-stu-id="2c7f2-222">**Gen 2 Collections**</span></span>

   <span data-ttu-id="2c7f2-223">Wyświetla liczbę razy generacji 2 GC wystąpiły od momentu rozpoczęcia procesu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-223">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="2c7f2-224">Licznik jest zwiększany na końcu kolekcji generacji 2 (nazywane również pełną wyrzucaniem elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-224">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="2c7f2-225">Ten licznik wyświetla ostatnią zaobserwowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-225">This counter displays the last observed value.</span></span>

- <span data-ttu-id="2c7f2-226">**Rozmiar sterty dużego obiektu**</span><span class="sxs-lookup"><span data-stu-id="2c7f2-226">**Large Object Heap size**</span></span>

   <span data-ttu-id="2c7f2-227">Wyświetla bieżący rozmiar w bajtach, w tym wolne miejsce, LOH.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-227">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="2c7f2-228">Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-228">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="2c7f2-229">Typowym sposobem patrzenia na liczniki wydajności jest monitor wydajności (perfmon.exe).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-229">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="2c7f2-230">Użyj "Dodaj liczniki", aby dodać interesujący licznik dla procesów, na których Ci zależy.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-230">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="2c7f2-231">Dane licznika wydajności można zapisać w pliku dziennika, jak pokazano na rysunku 4:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-231">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="2c7f2-232">![Zrzut ekranu przedstawiający dodawanie liczników wydajności.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="2c7f2-232">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="2c7f2-233">Rysunek 4: LOH po generacji 2 GC</span><span class="sxs-lookup"><span data-stu-id="2c7f2-233">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="2c7f2-234">Liczniki wydajności można również wyszukiwać programowo.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-234">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="2c7f2-235">Wiele osób zbiera je w ten sposób w ramach rutynowego procesu testowania.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-235">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="2c7f2-236">Gdy wykryć liczniki z wartościami, które są nietypowe, używają innych środków, aby uzyskać bardziej szczegółowe dane, aby pomóc w dochodzeniu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-236">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="2c7f2-237">Zaleca się używanie zdarzeń ETW zamiast liczników wydajności, ponieważ ETW dostarcza znacznie bogatszych informacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-237">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="2c7f2-238">zdarzenia ETW</span><span class="sxs-lookup"><span data-stu-id="2c7f2-238">ETW events</span></span>

<span data-ttu-id="2c7f2-239">Moduł zbierający elementy bezużyteczne udostępnia bogaty zestaw zdarzeń ETW, które pomogą Ci zrozumieć, co robi sterty i dlaczego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-239">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="2c7f2-240">Następujące wpisy w blogu pokazują, jak zbierać i rozumieć zdarzenia GC z ETW:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-240">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="2c7f2-241">Wydarzenia ETW GC - 1</span><span class="sxs-lookup"><span data-stu-id="2c7f2-241">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="2c7f2-242">Wydarzenia ETW GC - 2</span><span class="sxs-lookup"><span data-stu-id="2c7f2-242">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="2c7f2-243">Wydarzenia ETW GC - 3</span><span class="sxs-lookup"><span data-stu-id="2c7f2-243">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="2c7f2-244">Wydarzenia ETW GC - 4</span><span class="sxs-lookup"><span data-stu-id="2c7f2-244">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="2c7f2-245">Aby zidentyfikować nadmierne generacji 2 GC spowodowane przez tymczasowe alokacje LOH, należy spojrzeć na trigger reason kolumny dla gc.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-245">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="2c7f2-246">W przypadku prostego testu, który przydziela tylko tymczasowe duże obiekty, można zbierać informacje o zdarzeniach ETW za pomocą następującego wiersza polecenia [PerfView:](https://www.microsoft.com/download/details.aspx?id=28567)</span><span class="sxs-lookup"><span data-stu-id="2c7f2-246">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="2c7f2-247">Rezultatem jest coś takiego:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-247">The result is something like this:</span></span>

<span data-ttu-id="2c7f2-248">![Zrzut ekranu przedstawiający zdarzenia ETW w perfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="2c7f2-248">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="2c7f2-249">Rysunek 5: Zdarzenia ETW wyświetlane przy użyciu PerfView</span><span class="sxs-lookup"><span data-stu-id="2c7f2-249">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="2c7f2-250">Jak widać, wszystkie gc są generacji 2 GCs, i wszystkie są one wyzwalane przez AllocLarge, co oznacza, że przydzielanie duży obiekt wyzwolił ten GC.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-250">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="2c7f2-251">Wiemy, że te przydziały są tymczasowe, ponieważ kolumna **LOH Survival Rate %** mówi 1%.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-251">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="2c7f2-252">Można zbierać dodatkowe zdarzenia ETW, które informują, kto przydzielił te duże obiekty.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-252">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="2c7f2-253">Następujący wiersz polecenia:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-253">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="2c7f2-254">zbiera allocationTick zdarzenie, które jest uruchamiane około co 100k warto alokacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-254">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="2c7f2-255">Innymi słowy zdarzenie jest uruchamiany za każdym razem, gdy duży obiekt jest przydzielany.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-255">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="2c7f2-256">Następnie można spojrzeć na jeden z GC Heap Alloc widoki, które pokazują, że callstacks, które przydzielone duże obiekty:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-256">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="2c7f2-257">![Zrzut ekranu przedstawiający widok sterty modułu zbierającego elementy bezużyteczne.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="2c7f2-257">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="2c7f2-258">Rysunek 6: Widok GC Heap Alloc</span><span class="sxs-lookup"><span data-stu-id="2c7f2-258">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="2c7f2-259">Jak widać, jest to bardzo prosty test, który po `Main` prostu przydziela duże obiekty z jego metody.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-259">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="2c7f2-260">Debuger</span><span class="sxs-lookup"><span data-stu-id="2c7f2-260">A debugger</span></span>

<span data-ttu-id="2c7f2-261">Jeśli wszystko, co masz, to zrzut pamięci i musisz sprawdzić, jakie obiekty znajdują się w rzeczywistości na LOH, możesz użyć [rozszerzenia debugera SoS dostarczonego](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) przez .NET.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-261">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="2c7f2-262">Polecenia debugowania wymienione w tej sekcji mają zastosowanie do [debugerów systemu Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-262">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="2c7f2-263">Poniżej przedstawiono przykładowe dane wyjściowe z analizy LOH:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-263">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="2c7f2-264">Rozmiar sterty LOH wynosi (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-264">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="2c7f2-265">Między adresami 023e1000 i 033db630, 8,008,736 bajty <xref:System.Object?displayProperty=nameWithType> są zajęte przez tablicę obiektów, 6,663,696 bajty są zajęte przez tablicę <xref:System.Byte?displayProperty=nameWithType> obiektów, a 2,081,792 bajty są zajęte przez wolne miejsce.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-265">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="2c7f2-266">Czasami debuger pokazuje, że całkowity rozmiar LOH jest mniejszy niż 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-266">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="2c7f2-267">Dzieje się tak, ponieważ środowisko wykonawcze używa LOH do przydzielenia niektórych obiektów, które są mniejsze niż duży obiekt.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-267">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="2c7f2-268">Ponieważ LOH nie jest zagęszczona, czasami LOH jest uważany za źródło fragmentacji.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-268">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="2c7f2-269">Rozdrobnienie oznacza:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-269">Fragmentation means:</span></span>

- <span data-ttu-id="2c7f2-270">Fragmentacja zarządzanego stosu, co jest wskazywane przez ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-270">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="2c7f2-271">W sosie `!dumpheap –type Free` polecenie wyświetla ilość wolnego miejsca między obiektami zarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-271">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="2c7f2-272">Fragmentacja przestrzeni adresowej pamięci wirtualnej, która jest pamięcią oznaczoną jako `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-272">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="2c7f2-273">Można go uzyskać za pomocą różnych poleceń debugera w windbg.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-273">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="2c7f2-274">W poniższym przykładzie pokazano fragmentację w przestrzeni maszyny Wirtualnej:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-274">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="2c7f2-275">Jest bardziej powszechne, aby zobaczyć fragmentacji maszyny Wirtualnej spowodowane przez tymczasowe dużych obiektów, które wymagają modułu zbierającego elementy bezużyteczne często uzyskać nowe segmenty zarządzanych sterty z systemu operacyjnego i zwolnić puste z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-275">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="2c7f2-276">Aby sprawdzić, czy LOH powoduje fragmentację maszyny Wirtualnej, można ustawić punkt przerwania na [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i [VirtualFree,](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) aby zobaczyć, kto je wywoła.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-276">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="2c7f2-277">Na przykład, aby zobaczyć, kto próbował przydzielić fragmenty pamięci wirtualnej większe niż 8MBB z systemu operacyjnego, można ustawić punkt przerwania w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="2c7f2-277">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="2c7f2-278">To polecenie dzieli się na debuger i pokazuje stos wywołań tylko wtedy, [gdy VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) jest wywoływany o rozmiarze alokacji większym niż 8 MB (0x800000).</span><span class="sxs-lookup"><span data-stu-id="2c7f2-278">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="2c7f2-279">Program CLR 2.0 dodał funkcję o nazwie *VM Hoarding,* która może być przydatna w scenariuszach, w których segmenty (w tym na stertach dużych i małych obiektów) są często nabywane i zwalniane.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-279">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="2c7f2-280">Aby określić gromadzenie maszyn wirtualnych, należy `STARTUP_HOARD_GC_VM` określić flagę uruchamiania wywoływaną za pośrednictwem interfejsu API hostingu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-280">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="2c7f2-281">Zamiast zwalniać puste segmenty z powrotem do systemu operacyjnego, CLR zwalnia pamięć w tych segmentach i umieszcza je na liście wstrzymania.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-281">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="2c7f2-282">(Należy zauważyć, że program CLR nie robi tego dla segmentów, które są zbyt duże). Clr później używa tych segmentów do zaspokojenia nowych żądań segmentu.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-282">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="2c7f2-283">Następnym razem, gdy aplikacja potrzebuje nowego segmentu, program CLR używa go z tej listy wstrzymania, jeśli można znaleźć taki, który jest wystarczająco duży.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-283">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="2c7f2-284">Gromadzenie maszyn wirtualnych jest również przydatne w przypadku aplikacji, które chcą trzymać się segmentów, które zostały już nabyte, takich jak niektóre aplikacje serwera, które są dominującymi aplikacjami działającymi w systemie, aby uniknąć wyjątków braku pamięci.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-284">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out-of-memory exceptions.</span></span>

<span data-ttu-id="2c7f2-285">Zdecydowanie zaleca się, aby dokładnie przetestować aplikację podczas korzystania z tej funkcji, aby upewnić się, że aplikacja ma dość stabilne użycie pamięci.</span><span class="sxs-lookup"><span data-stu-id="2c7f2-285">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>
