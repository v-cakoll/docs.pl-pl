---
title: Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core
description: Dowiedz się, jak używać kolekcjonowania AssemblyLoadContext do załadunku i zwalniania zarządzanych zestawów i jak debugować problemy uniemożliwiające powodzenie zwalniania.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159744"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="4f135-103">Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4f135-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="4f135-104">Począwszy od .NET Core 3.0, możliwość załadowania, a później zwolnić zestaw zestawów jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="4f135-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="4f135-105">W ramach programu .NET Framework w tym celu użyto domen aplikacji niestandardowych, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4f135-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="4f135-106">.NET Core 3.0 i nowsze wersje obsługują rozładunek za pośrednictwem <xref:System.Runtime.Loader.AssemblyLoadContext>programu .</span><span class="sxs-lookup"><span data-stu-id="4f135-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="4f135-107">Można załadować zestaw zestawów do kolekcji, `AssemblyLoadContext`wykonać w nich metody lub po prostu sprawdzić `AssemblyLoadContext`je za pomocą odbicia, a na koniec zwolnić .</span><span class="sxs-lookup"><span data-stu-id="4f135-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="4f135-108">To zwalnia zespoły załadowane `AssemblyLoadContext`do pliku .</span><span class="sxs-lookup"><span data-stu-id="4f135-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="4f135-109">Istnieje jedna godna uwagi różnica między `AssemblyLoadContext` rozładunku przy użyciu i przy użyciu AppDomains.</span><span class="sxs-lookup"><span data-stu-id="4f135-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="4f135-110">Z AppDomains rozładunku jest wymuszone.</span><span class="sxs-lookup"><span data-stu-id="4f135-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="4f135-111">W czasie zwalniania wszystkie wątki uruchomione w docelowej appdomain są przerywane, zarządzane obiekty COM utworzone w docelowej AppDomain są niszczone i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4f135-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="4f135-112">Z `AssemblyLoadContext`, rozładunek jest "spółdzielnia".</span><span class="sxs-lookup"><span data-stu-id="4f135-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="4f135-113">Wywołanie <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metody po prostu inicjuje rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="4f135-114">Rozładunek kończy się po:</span><span class="sxs-lookup"><span data-stu-id="4f135-114">The unloading finishes after:</span></span>

- <span data-ttu-id="4f135-115">Żadne wątki nie mają metod z `AssemblyLoadContext` zestawów załadowanych do ich stosów wywołań.</span><span class="sxs-lookup"><span data-stu-id="4f135-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="4f135-116">Żaden z typów z zestawów załadowanych do `AssemblyLoadContext`, wystąpień tych typów, a same zestawy są przywoływane przez:</span><span class="sxs-lookup"><span data-stu-id="4f135-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="4f135-117">Odniesienia poza `AssemblyLoadContext`, z wyjątkiem<xref:System.WeakReference> słabych odniesień ( lub <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="4f135-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="4f135-118">Silne uchwyty modułu odśmiecania pamięci (GCHandleType.Normal lub [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned)zarówno wewnątrz, jak i na zewnątrz pliku `AssemblyLoadContext`.[GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal)</span><span class="sxs-lookup"><span data-stu-id="4f135-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="4f135-119">Korzystanie z kolekcjonowania AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="4f135-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="4f135-120">Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób `AssemblyLoadContext`załadowania aplikacji .NET Core do kolekcji, wykonać jej punkt wejścia, a następnie zwolnić go.</span><span class="sxs-lookup"><span data-stu-id="4f135-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="4f135-121">Pełną próbkę można [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)znaleźć pod adresem .</span><span class="sxs-lookup"><span data-stu-id="4f135-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="4f135-122">Tworzenie kolekcjonowania AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="4f135-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="4f135-123">Musisz wyprowadzić swoją klasę <xref:System.Runtime.Loader.AssemblyLoadContext> z i <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> przeciążać jej metody.</span><span class="sxs-lookup"><span data-stu-id="4f135-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4f135-124">Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są `AssemblyLoadContext`zależnościzestawów załadowanych do tego .</span><span class="sxs-lookup"><span data-stu-id="4f135-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="4f135-125">Poniższy kod jest przykładem najprostszego `AssemblyLoadContext`niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="4f135-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="4f135-126">Jak widać, `Load` metoda zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="4f135-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="4f135-127">Oznacza to, że wszystkie zestawy zależności są ładowane do kontekstu domyślnego, a nowy kontekst zawiera tylko zestawy jawnie załadowane do niego.</span><span class="sxs-lookup"><span data-stu-id="4f135-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="4f135-128">Jeśli chcesz załadować niektóre lub wszystkie zależności `AssemblyLoadContext` do zbyt, `AssemblyDependencyResolver` można `Load` użyć w tej metody.</span><span class="sxs-lookup"><span data-stu-id="4f135-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="4f135-129">Określa `AssemblyDependencyResolver` nazwy zestawów do bezwzględnych ścieżek plików złożenia.</span><span class="sxs-lookup"><span data-stu-id="4f135-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="4f135-130">Program rozpoznawania nazw używa plików pliku i zestawu *.deps.json* w katalogu głównego zestawu załadowanego do kontekstu.</span><span class="sxs-lookup"><span data-stu-id="4f135-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="4f135-131">Używanie niestandardowego elementu zestawu kolekcji AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="4f135-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="4f135-132">W tej sekcji przyjęto założenie, że używana jest prostsza `TestAssemblyLoadContext` wersja.</span><span class="sxs-lookup"><span data-stu-id="4f135-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="4f135-133">Można utworzyć wystąpienie niestandardowego `AssemblyLoadContext` i załadować do niego zestaw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="4f135-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="4f135-134">Dla każdego z zestawów, do których odwołuje `TestAssemblyLoadContext.Load` się załadowany `TestAssemblyLoadContext` zespół, metoda jest wywoływana tak, aby można było zdecydować, skąd uzyskać zestaw.</span><span class="sxs-lookup"><span data-stu-id="4f135-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="4f135-135">W naszym przypadku `null` zwraca, aby wskazać, że powinien być ładowany do domyślnego kontekstu z lokalizacji, które czas wykonywania używa do załadowania zestawów domyślnie.</span><span class="sxs-lookup"><span data-stu-id="4f135-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="4f135-136">Teraz, gdy zestaw został załadowany, można wykonać metodę z niego.</span><span class="sxs-lookup"><span data-stu-id="4f135-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="4f135-137">Uruchom `Main` metodę:</span><span class="sxs-lookup"><span data-stu-id="4f135-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="4f135-138">Po `Main` zwróceniu metody można zainicjować rozładunku `Unload` przez wywołanie metody na niestandardowy `AssemblyLoadContext` lub `AssemblyLoadContext`pozbycie się odwołania masz do :</span><span class="sxs-lookup"><span data-stu-id="4f135-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="4f135-139">Jest to wystarczające do rozładowania zespołu testowego.</span><span class="sxs-lookup"><span data-stu-id="4f135-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="4f135-140">Let's rzeczywiście umieścić to wszystko w oddzielnym non-inlineable metody `MethodInfo` w `Assembly.EntryPoint`celu `TestAssemblyLoadContext`zapewnienia, że , `Assembly`i () nie mogą być utrzymywane przy życiu przez stos umiejscowienia (real- lub JIT wprowadzone mieszkańców).</span><span class="sxs-lookup"><span data-stu-id="4f135-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="4f135-141">To może `TestAssemblyLoadContext` utrzymać przy życiu i zapobiec rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="4f135-142">Ponadto zwrócić słabe odwołanie `AssemblyLoadContext` do tak, aby można go użyć później do wykrywania zakończenia rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="4f135-143">Teraz można uruchomić tę funkcję, aby załadować, wykonać i zwolnić zespół.</span><span class="sxs-lookup"><span data-stu-id="4f135-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="4f135-144">Jednak rozładunek nie kończy się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="4f135-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="4f135-145">Jak wcześniej wspomniano, opiera się na moduł zbierający elementy bezużyteczne, aby zebrać wszystkie obiekty z zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="4f135-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="4f135-146">W wielu przypadkach nie trzeba czekać na zakończenie rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="4f135-147">Istnieją jednak przypadki, w których warto wiedzieć, że rozładunek został zakończony.</span><span class="sxs-lookup"><span data-stu-id="4f135-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="4f135-148">Na przykład można usunąć plik zestawu, który został `AssemblyLoadContext` załadowany do niestandardowego z dysku.</span><span class="sxs-lookup"><span data-stu-id="4f135-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="4f135-149">W takim przypadku można użyć następującego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="4f135-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="4f135-150">Wyzwala wyrzucanie elementów bezużytecznych i czeka na oczekujące finalizatorów `AssemblyLoadContext` w `null`pętli, dopóki słabe odwołanie do niestandardowego jest ustawiona na , wskazując obiekt docelowy został zebrany.</span><span class="sxs-lookup"><span data-stu-id="4f135-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="4f135-151">W większości przypadków wymagane jest tylko jedno przejście przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="4f135-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="4f135-152">Jednak w bardziej złożonych przypadkach, gdy obiekty `AssemblyLoadContext` utworzone przez kod uruchomiony w finalizatorów mają więcej przebiegów mogą być potrzebne.</span><span class="sxs-lookup"><span data-stu-id="4f135-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="4f135-153">Zdarzenie rozładunku</span><span class="sxs-lookup"><span data-stu-id="4f135-153">The Unloading event</span></span>

<span data-ttu-id="4f135-154">W niektórych przypadkach może być konieczne dla kodu `AssemblyLoadContext` załadowanego do niestandardowego do wykonania niektórych oczyszczania po zainicjowaniu rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="4f135-155">Na przykład może być konieczne zatrzymanie wątków lub oczyszczenie silnych uchwytów GC.</span><span class="sxs-lookup"><span data-stu-id="4f135-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="4f135-156">W `Unloading` takich przypadkach można wykorzystać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4f135-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="4f135-157">Program obsługi, który wykonuje niezbędne oczyszczania można podłączyć do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4f135-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="4f135-158">Rozwiązywanie problemów z rozładowaniem</span><span class="sxs-lookup"><span data-stu-id="4f135-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="4f135-159">Ze względu na kooperatywny charakter rozładunku, łatwo zapomnieć o referencjach, które mogą być utrzymanie rzeczy w kolekcjonowania `AssemblyLoadContext` żyje i zapobieganie rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="4f135-160">Oto podsumowanie jednostek (niektóre z nich nieoczywiste), które mogą posiadać odniesienia:</span><span class="sxs-lookup"><span data-stu-id="4f135-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="4f135-161">Regularne odwołania przechowywane spoza `AssemblyLoadContext` kolekcjonowania, które są przechowywane w gnieździe stosu lub rejestrze procesora (metoda locals, jawnie utworzone przez kod użytkownika lub niejawnie przez kompilator just-in-time (JIT), zmienną statyczną lub silne (przypinanie) gc uchwyt i przechodnie wskazując:</span><span class="sxs-lookup"><span data-stu-id="4f135-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="4f135-162">Zespół załadowany do `AssemblyLoadContext`kolekcji .</span><span class="sxs-lookup"><span data-stu-id="4f135-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="4f135-163">Typ z takiego złożenia.</span><span class="sxs-lookup"><span data-stu-id="4f135-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="4f135-164">Wystąpienie typu z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="4f135-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="4f135-165">Wątki uruchamiane kod z zestawu `AssemblyLoadContext`załadowany do kolekcjonowania .</span><span class="sxs-lookup"><span data-stu-id="4f135-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="4f135-166">Wystąpienia niestandardowych typów niekolekcjonerskich `AssemblyLoadContext` utworzonych wewnątrz kolekcji `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="4f135-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="4f135-167">Oczekujące <xref:System.Threading.RegisteredWaitHandle> wystąpienia z wywołaniami zwrotu `AssemblyLoadContext`ustawiono na metody w niestandardowym pliku .</span><span class="sxs-lookup"><span data-stu-id="4f135-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="4f135-168">Odwołania do obiektów, które są przechowywane w gniazdach stosu lub rejestrów procesora i które mogą zapobiec zwalnianiu może `AssemblyLoadContext` wystąpić w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="4f135-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="4f135-169">Gdy wyniki wywołania funkcji są przekazywane bezpośrednio do innej funkcji, mimo że nie ma zmiennej lokalnej utworzonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4f135-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="4f135-170">Gdy kompilator JIT przechowuje odwołanie do obiektu, który był dostępny w pewnym momencie w metodzie.</span><span class="sxs-lookup"><span data-stu-id="4f135-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="4f135-171">Problemy z rozładowaniem debugowania</span><span class="sxs-lookup"><span data-stu-id="4f135-171">Debug unloading issues</span></span>

<span data-ttu-id="4f135-172">Problemy z debugowaniem z rozładunkiem mogą być uciążliwe.</span><span class="sxs-lookup"><span data-stu-id="4f135-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="4f135-173">Możesz dostać się do sytuacji, w których `AssemblyLoadContext` nie wiesz, co może być przy życiu, ale rozładunek nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="4f135-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="4f135-174">Najlepszą bronią do pomocy w tym jest WinDbg (LLDB na Unix) z pluginem SOS.</span><span class="sxs-lookup"><span data-stu-id="4f135-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="4f135-175">Musisz znaleźć to, co `LoaderAllocator` utrzymuje przynależność do konkretnego `AssemblyLoadContext` żywcem.</span><span class="sxs-lookup"><span data-stu-id="4f135-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="4f135-176">Wtyczka SOS pozwala spojrzeć na obiekty sterty GC, ich hierarchie i korzenie.</span><span class="sxs-lookup"><span data-stu-id="4f135-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="4f135-177">Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:</span><span class="sxs-lookup"><span data-stu-id="4f135-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="4f135-178">W WinDbg (wydaje się, WinDbg robi to automatycznie po włamaniu się do aplikacji .NET Core):</span><span class="sxs-lookup"><span data-stu-id="4f135-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="4f135-179">W LLDB:</span><span class="sxs-lookup"><span data-stu-id="4f135-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="4f135-180">Debugujmy przykładowy program, który ma problemy z rozładowywaniem.</span><span class="sxs-lookup"><span data-stu-id="4f135-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="4f135-181">Kod źródłowy znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="4f135-181">Source code is included below.</span></span> <span data-ttu-id="4f135-182">Po uruchomieniu go w obszarze WinDbg, program włamuje się do debugera zaraz po próbie sprawdzenia sukcesu rozładunku.</span><span class="sxs-lookup"><span data-stu-id="4f135-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="4f135-183">Następnie możesz zacząć szukać winowajców.</span><span class="sxs-lookup"><span data-stu-id="4f135-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="4f135-184">W przypadku debugowania przy użyciu LLDB w uniksie polecenia SOS `!` w poniższych przykładach nie mają przed nimi.</span><span class="sxs-lookup"><span data-stu-id="4f135-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="4f135-185">To polecenie zrzuca wszystkie obiekty `LoaderAllocator` o nazwie typu zawierającej, które znajdują się w stercie GC.</span><span class="sxs-lookup"><span data-stu-id="4f135-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="4f135-186">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="4f135-186">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48
000002b78000ceb0 00007ffadc93a218       24

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="4f135-187">W części "Statystyki:" poniżej, `MT` `MethodTable`sprawdź ( `System.Reflection.LoaderAllocator`) należące do , który jest obiektem, na którym nam zależy.</span><span class="sxs-lookup"><span data-stu-id="4f135-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="4f135-188">Następnie na liście na początku znajdź wpis `MT` z dopasowaniem tego i uzyskaj adres samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4f135-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="4f135-189">W naszym przypadku jest to "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="4f135-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="4f135-190">Teraz, gdy znamy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć jego korzenie GC:</span><span class="sxs-lookup"><span data-stu-id="4f135-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="4f135-191">To polecenie zrzuca łańcuch odwołań do `LoaderAllocator` obiektów, które prowadzą do wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4f135-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="4f135-192">Lista zaczyna się od katalogu głównego, `LoaderAllocator` który jest jednostką, która utrzymuje naszą przy życiu, a tym samym jest sednem problemu.</span><span class="sxs-lookup"><span data-stu-id="4f135-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="4f135-193">Katalog główny może być stosem, rejestrem procesora, uchwytem GC lub zmienną statyczną.</span><span class="sxs-lookup"><span data-stu-id="4f135-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="4f135-194">Oto przykład danych wyjściowych `gcroot` polecenia:</span><span class="sxs-lookup"><span data-stu-id="4f135-194">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="4f135-195">Następnym krokiem jest dowiedzieć się, gdzie znajduje się korzeń, dzięki czemu można go naprawić.</span><span class="sxs-lookup"><span data-stu-id="4f135-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="4f135-196">Najprostszym przypadkiem jest, gdy korzeń jest gniazdo stosu lub rejestru procesora.</span><span class="sxs-lookup"><span data-stu-id="4f135-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="4f135-197">W takim przypadku `gcroot` pokazuje nazwę funkcji, której ramka zawiera katalog główny i wątek wykonujący tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="4f135-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="4f135-198">Trudny przypadek jest, gdy korzeń jest zmienną statyczną lub gc uchwyt.</span><span class="sxs-lookup"><span data-stu-id="4f135-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="4f135-199">W poprzednim przykładzie pierwszy katalog główny jest `System.Reflection.RuntimeMethodInfo` lokalnym typu przechowywane `example.Program.Main(System.String[])` w `rbp-20` ramce funkcji na adres (`rbp` jest rejestr `rbp` procesora i -20 jest przesunięcie szesnastkowego z tego rejestru).</span><span class="sxs-lookup"><span data-stu-id="4f135-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="4f135-200">Drugi katalog główny jest normalne `GCHandle` (silne), który posiada `test.Test` odwołanie do wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="4f135-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="4f135-201">Trzeci korzeń jest `GCHandle`przypięty .</span><span class="sxs-lookup"><span data-stu-id="4f135-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="4f135-202">Ten jest w rzeczywistości zmienną statyczną, ale niestety nie ma sposobu, aby powiedzieć.</span><span class="sxs-lookup"><span data-stu-id="4f135-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="4f135-203">Statyka dla typów odwołań są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4f135-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="4f135-204">Innym przypadkiem, który może `AssemblyLoadContext` zapobiec rozładunku jest, gdy wątek ma `AssemblyLoadContext` ramkę metody z zestawu załadowany do jego stosu.</span><span class="sxs-lookup"><span data-stu-id="4f135-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="4f135-205">Można sprawdzić, że przez dumpingu zarządzanych stosów wywołań wszystkich wątków:</span><span class="sxs-lookup"><span data-stu-id="4f135-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="4f135-206">Polecenie oznacza "zastosuj `!clrstack` do wszystkich wątków polecenie".</span><span class="sxs-lookup"><span data-stu-id="4f135-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="4f135-207">Poniżej przedstawiono dane wyjściowe tego polecenia dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="4f135-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="4f135-208">Niestety, LLDB na Unix nie ma żadnego sposobu, aby zastosować polecenie do wszystkich wątków, `clrstack` więc należy ręcznie przełączyć wątki i powtórzyć polecenie.</span><span class="sxs-lookup"><span data-stu-id="4f135-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="4f135-209">Ignoruj wszystkie wątki, w których debuger mówi "Nie można przejść przez zarządzany stos".</span><span class="sxs-lookup"><span data-stu-id="4f135-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998]
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28]
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0]
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568]
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0]

```

<span data-ttu-id="4f135-210">Jak widać, ostatni wątek `test.Program.ThreadProc()`ma .</span><span class="sxs-lookup"><span data-stu-id="4f135-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="4f135-211">Jest to funkcja z zestawu `AssemblyLoadContext`załadowanego do , `AssemblyLoadContext` a więc utrzymuje przy życiu.</span><span class="sxs-lookup"><span data-stu-id="4f135-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="4f135-212">Przykładowe źródło z problemami z zwalnialnością</span><span class="sxs-lookup"><span data-stu-id="4f135-212">Example source with unloadability issues</span></span>

<span data-ttu-id="4f135-213">Poniższy kod jest używany w poprzednim przykładzie debugowania.</span><span class="sxs-lookup"><span data-stu-id="4f135-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="4f135-214">Główny program testowy</span><span class="sxs-lookup"><span data-stu-id="4f135-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="4f135-215">Program załadowany do modułu TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="4f135-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="4f135-216">Poniższy kod reprezentuje *test.dll* przekazany `ExecuteAndUnload` do metody w głównym programie testowym.</span><span class="sxs-lookup"><span data-stu-id="4f135-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
