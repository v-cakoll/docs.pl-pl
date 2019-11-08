---
title: Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core
description: Dowiedz się, jak używać programu AssemblyLoadContexte kolekcjonowane do ładowania i zwalniania zestawów zarządzanych oraz jak debugować problemy uniemożliwiające pomyślne wyładowywanie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 462e6d2c7f135d2ba274d78fe31ad27391eac416
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740448"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="64a33-103">Sposób używania i debugowania funkcji zwolnienia zestawu w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="64a33-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="64a33-104">Począwszy od platformy .NET Core 3,0, możliwość załadowania i późniejszego zwolnienia zestawu zestawów jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="64a33-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="64a33-105">W tym celu w .NET Framework użyto niestandardowych domen aplikacji, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64a33-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="64a33-106">Program .NET Core 3,0 i jego nowsze wersje obsługują możliwości zwalniania za pomocą <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="64a33-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="64a33-107">Można załadować zestaw zestawów do `AssemblyLoadContext`kolekcjonowanych, wykonać metody w nich lub po prostu sprawdzić je przy użyciu odbicia, a następnie zwolnić `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="64a33-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="64a33-108">To zwalnia zestawy ładowane do `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="64a33-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="64a33-109">Istnieje jedna istotna różnica między rozładunkiem przy użyciu `AssemblyLoadContext` i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64a33-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="64a33-110">W przypadku domen aplikacji wyładowywanie jest wymuszane.</span><span class="sxs-lookup"><span data-stu-id="64a33-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="64a33-111">W czasie zwalniania wszystkie wątki działające w docelowej domenie AppDomain są przerywane, zarządzane obiekty COM utworzone w docelowej domenie AppDomain są niszczone i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="64a33-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="64a33-112">W przypadku `AssemblyLoadContext`Unload to "spółdzielnie".</span><span class="sxs-lookup"><span data-stu-id="64a33-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="64a33-113">Wywołanie metody <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> po prostu inicjuje zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="64a33-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="64a33-114">Zwalnianie kończy się po:</span><span class="sxs-lookup"><span data-stu-id="64a33-114">The unloading finishes after:</span></span>

- <span data-ttu-id="64a33-115">Żadne wątki nie mają metod z zestawów załadowanych do `AssemblyLoadContext` na ich stosach wywołań.</span><span class="sxs-lookup"><span data-stu-id="64a33-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="64a33-116">Żaden z typów zestawów nie został załadowany do `AssemblyLoadContext`, wystąpienia tych typów i same zestawy są przywoływane przez:</span><span class="sxs-lookup"><span data-stu-id="64a33-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="64a33-117">Odwołania poza `AssemblyLoadContext`, z wyjątkiem słabych odwołań (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="64a33-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="64a33-118">Dojścia silnego modułu wyrzucania elementów bezużytecznych (GC) ([GCHandleType. Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) lub [GCHandleType. przypięto](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) zarówno wewnątrz, jak i na zewnątrz `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="64a33-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="64a33-119">Użyj AssemblyLoadContextów kolekcjonowanych</span><span class="sxs-lookup"><span data-stu-id="64a33-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="64a33-120">Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób ładowania aplikacji .NET Core do `AssemblyLoadContext`ej kolekcjonowanej, wykonywania punktu wejścia, a następnie zwalniania go.</span><span class="sxs-lookup"><span data-stu-id="64a33-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="64a33-121">Kompletny przykład można znaleźć w [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span><span class="sxs-lookup"><span data-stu-id="64a33-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="64a33-122">Utwórz kolekcjonowaną AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="64a33-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="64a33-123">Należy utworzyć klasę z <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążyć jej metodę <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="64a33-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="64a33-124">Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są zależnościami od zestawów ładowanych do tego `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="64a33-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="64a33-125">Poniższy kod jest przykładem najprostszego `AssemblyLoadContext`niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="64a33-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="64a33-126">Jak widać, Metoda `Load` zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="64a33-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="64a33-127">Oznacza to, że wszystkie zestawy zależności są ładowane do domyślnego kontekstu, a nowy kontekst zawiera tylko zestawy, które są w nim jawnie załadowane.</span><span class="sxs-lookup"><span data-stu-id="64a33-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="64a33-128">Jeśli chcesz załadować niektóre lub wszystkie zależności do `AssemblyLoadContext`, możesz użyć `AssemblyDependencyResolver` w metodzie `Load`.</span><span class="sxs-lookup"><span data-stu-id="64a33-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="64a33-129">`AssemblyDependencyResolver` rozwiązuje nazwy zestawów do bezwzględnych ścieżek plików zestawów.</span><span class="sxs-lookup"><span data-stu-id="64a33-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="64a33-130">Mechanizm rozwiązywania konfliktów używa pliku *. deps. JSON* i plików zestawów w katalogu głównym zestawu załadowanym do kontekstu.</span><span class="sxs-lookup"><span data-stu-id="64a33-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="64a33-131">Korzystanie z niestandardowego AssemblyLoadContextego kolekcjonowania</span><span class="sxs-lookup"><span data-stu-id="64a33-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="64a33-132">W tej sekcji założono, że prostsza wersja `TestAssemblyLoadContext` jest używana.</span><span class="sxs-lookup"><span data-stu-id="64a33-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="64a33-133">Można utworzyć wystąpienie `AssemblyLoadContext` niestandardowego i załadować do niego zestaw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="64a33-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="64a33-134">Dla każdego z zestawów, do którego odwołuje się załadowany zestaw, wywoływana jest metoda `TestAssemblyLoadContext.Load`, aby `TestAssemblyLoadContext` mógł zdecydować, skąd ma zostać pobrany zestaw.</span><span class="sxs-lookup"><span data-stu-id="64a33-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="64a33-135">W naszym przypadku zwraca `null`, aby wskazać, że powinien zostać załadowany do domyślnego kontekstu z lokalizacji używanych przez środowisko uruchomieniowe do domyślnego ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="64a33-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="64a33-136">Teraz, gdy zestaw został załadowany, można wykonać z niego metodę.</span><span class="sxs-lookup"><span data-stu-id="64a33-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="64a33-137">Uruchom metodę `Main`:</span><span class="sxs-lookup"><span data-stu-id="64a33-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="64a33-138">Po powrocie metody `Main` można zainicjować zwalnianie, wywołując metodę `Unload` na niestandardowym `AssemblyLoadContext` lub pozbyć się odwołania do `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="64a33-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="64a33-139">Jest to wystarczające do zwolnienia zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="64a33-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="64a33-140">W rzeczywistości przeniesiemy wszystkie te elementy do oddzielnej metody nieliniowej, aby upewnić się, że `TestAssemblyLoadContext`, `Assembly`i `MethodInfo` (`Assembly.EntryPoint`) nie mogą być utrzymywane przez odwołania do miejsca na stosie (dane lokalne w języku rzeczywistym lub JIT).</span><span class="sxs-lookup"><span data-stu-id="64a33-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="64a33-141">Może to spowodować, że `TestAssemblyLoadContext` działa i uniemożliwia zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="64a33-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="64a33-142">Należy również zwrócić słabe odwołanie do `AssemblyLoadContext`, aby można było użyć go później do wykrywania zakończenia zwalniania.</span><span class="sxs-lookup"><span data-stu-id="64a33-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="64a33-143">Teraz można uruchomić tę funkcję w celu załadowania, wykonania i zwolnienia zestawu.</span><span class="sxs-lookup"><span data-stu-id="64a33-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="64a33-144">Jednak zwalnianie nie zakończy się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="64a33-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="64a33-145">Jak wspomniano wcześniej, polega na wykorzystaniu modułu wyrzucania elementów bezużytecznych w celu zebrania wszystkich obiektów z zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="64a33-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="64a33-146">W wielu przypadkach nie trzeba czekać na ukończenie zwalniania.</span><span class="sxs-lookup"><span data-stu-id="64a33-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="64a33-147">Istnieją jednak przypadki, w których warto wiedzieć, że zwolnienie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="64a33-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="64a33-148">Na przykład możesz chcieć usunąć plik zestawu, który został załadowany do `AssemblyLoadContext` niestandardowego z dysku.</span><span class="sxs-lookup"><span data-stu-id="64a33-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="64a33-149">W takim przypadku można użyć poniższego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="64a33-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="64a33-150">Wyzwala wyrzucanie elementów bezużytecznych i oczekuje na oczekujące finalizatory w pętli do momentu, gdy słabe odwołanie do `AssemblyLoadContext` niestandardowego zostanie ustawione na `null`, co wskazuje na to, że obiekt docelowy został zebrany.</span><span class="sxs-lookup"><span data-stu-id="64a33-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="64a33-151">W większości przypadków wymagane jest tylko jedno przejście przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="64a33-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="64a33-152">Jednak w przypadku bardziej złożonych przypadków, gdy obiekty utworzone za pomocą kodu uruchomionego w `AssemblyLoadContext` mają finalizatory, może być konieczne wykonanie większej liczby przebiegów.</span><span class="sxs-lookup"><span data-stu-id="64a33-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="64a33-153">Zdarzenie wyładowywania</span><span class="sxs-lookup"><span data-stu-id="64a33-153">The Unloading event</span></span>

<span data-ttu-id="64a33-154">W niektórych przypadkach może być konieczne, aby kod został załadowany do niestandardowego `AssemblyLoadContext`, aby przeprowadzić oczyszczanie po zainicjowaniu zwalniania.</span><span class="sxs-lookup"><span data-stu-id="64a33-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="64a33-155">Na przykład może być konieczne zatrzymanie wątków lub oczyszczenie silnych dojść GC.</span><span class="sxs-lookup"><span data-stu-id="64a33-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="64a33-156">W takich przypadkach można użyć zdarzenia `Unloading`.</span><span class="sxs-lookup"><span data-stu-id="64a33-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="64a33-157">Do tego zdarzenia można podłączyć procedurę obsługi, która wykonuje wymagane oczyszczanie.</span><span class="sxs-lookup"><span data-stu-id="64a33-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="64a33-158">Rozwiązywanie problemów z możliwością ponownego ładowania</span><span class="sxs-lookup"><span data-stu-id="64a33-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="64a33-159">Ze względu na spółdzielnię zwalniającą, można łatwo zapomnieć o odwołaniach, które mogą mieć na celu przechowywanie `AssemblyLoadContext` aktywności i zapobiegania zwolnieniu.</span><span class="sxs-lookup"><span data-stu-id="64a33-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="64a33-160">Poniżej znajduje się podsumowanie jednostek (niektóre z nich nie są oczywiste), które mogą zawierać odwołania:</span><span class="sxs-lookup"><span data-stu-id="64a33-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="64a33-161">Regularne odwołania przechowywane z zewnątrz kolekcjonowanych `AssemblyLoadContext` przechowywanych w gnieździe stosu lub w rejestrze procesora (metody lokalne, jawnie utworzone przez kod użytkownika lub niejawnie przez kompilator just-in-Time (JIT), zmienna statyczna lub silne ( Przypinanie do uchwytu GC i przechodnie wskazywanie:</span><span class="sxs-lookup"><span data-stu-id="64a33-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="64a33-162">Zestaw załadowany do `AssemblyLoadContext`u kolekcjonowanego.</span><span class="sxs-lookup"><span data-stu-id="64a33-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="64a33-163">Typ z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="64a33-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="64a33-164">Wystąpienie typu z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="64a33-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="64a33-165">Wątki uruchamiające kod z zestawu załadowanego do `AssemblyLoadContext`kolekcjonowania.</span><span class="sxs-lookup"><span data-stu-id="64a33-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="64a33-166">Wystąpienia niestandardowych, niekolekcjonowanych typów `AssemblyLoadContext` utworzonych wewnątrz `AssemblyLoadContext`kolekcjonowanych.</span><span class="sxs-lookup"><span data-stu-id="64a33-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="64a33-167">Oczekujące wystąpienia <xref:System.Threading.RegisteredWaitHandle> z wywołaniami zwrotnymi ustawionymi na metody w `AssemblyLoadContext`niestandardowym.</span><span class="sxs-lookup"><span data-stu-id="64a33-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="64a33-168">Odwołania do obiektów, które są przechowywane w gniazdach stosu lub rejestrach procesora i mogą uniemożliwiać zwolnienie `AssemblyLoadContext` mogą wystąpić w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="64a33-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="64a33-169">Gdy wyniki wywołań funkcji są przesyłane bezpośrednio do innej funkcji, nawet jeśli nie istnieje zmienna lokalna utworzona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="64a33-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="64a33-170">Gdy kompilator JIT przechowuje odwołanie do obiektu, który był dostępny w pewnym momencie w metodzie.</span><span class="sxs-lookup"><span data-stu-id="64a33-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="64a33-171">Debuguj problemy z zwalnianiem</span><span class="sxs-lookup"><span data-stu-id="64a33-171">Debug unloading issues</span></span>

<span data-ttu-id="64a33-172">Problemy z debugowaniem z rozładowywaniem mogą być żmudnym.</span><span class="sxs-lookup"><span data-stu-id="64a33-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="64a33-173">Możesz przejść do sytuacji, w których nie wiesz, co może być utrzymywane w `AssemblyLoadContext` aktywności, ale zwalnianie kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="64a33-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="64a33-174">Najlepsza broń, która pomoże Ci to WinDbg (LLDB w systemie UNIX) z wtyczką SOS.</span><span class="sxs-lookup"><span data-stu-id="64a33-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="64a33-175">Należy się dowiedzieć, co zachowuje `LoaderAllocator` należące do konkretnej `AssemblyLoadContext` aktywności.</span><span class="sxs-lookup"><span data-stu-id="64a33-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="64a33-176">Wtyczka SOS umożliwia przeglądanie obiektów sterty GC, ich hierarchii i katalogów głównych.</span><span class="sxs-lookup"><span data-stu-id="64a33-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="64a33-177">Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:</span><span class="sxs-lookup"><span data-stu-id="64a33-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="64a33-178">W programie WinDbg (po załamaniu do aplikacji .NET Core) automatycznie</span><span class="sxs-lookup"><span data-stu-id="64a33-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="64a33-179">W LLDB:</span><span class="sxs-lookup"><span data-stu-id="64a33-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="64a33-180">Debugujmy Przykładowy program, który ma problemy z wyładunkiem.</span><span class="sxs-lookup"><span data-stu-id="64a33-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="64a33-181">Kod źródłowy jest uwzględniony poniżej.</span><span class="sxs-lookup"><span data-stu-id="64a33-181">Source code is included below.</span></span> <span data-ttu-id="64a33-182">Gdy uruchamiasz go w ramach usługi WinDbg, program przerwie się w debugerze po podjęciu próby sprawdzenia powodzenia zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="64a33-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="64a33-183">Następnie można rozpocząć wyszukiwanie culprits.</span><span class="sxs-lookup"><span data-stu-id="64a33-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="64a33-184">Jeśli debugujesz przy użyciu LLDB w systemie UNIX, polecenia SOS w poniższych przykładach nie mają `!` przed nimi.</span><span class="sxs-lookup"><span data-stu-id="64a33-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="64a33-185">To polecenie zrzuca wszystkie obiekty o nazwie typu zawierającego `LoaderAllocator`, które znajdują się na stercie GC.</span><span class="sxs-lookup"><span data-stu-id="64a33-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="64a33-186">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="64a33-186">Here is an example:</span></span>

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

<span data-ttu-id="64a33-187">W poniższym składniku "Statistics:" Sprawdź `MT` (`MethodTable`) należących do `System.Reflection.LoaderAllocator`, który jest obiektem, którego potrzebujemy.</span><span class="sxs-lookup"><span data-stu-id="64a33-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="64a33-188">Następnie na liście na początku Znajdź wpis z `MT` pasującym do tego samego obiektu i uzyskaj adres samego samego siebie.</span><span class="sxs-lookup"><span data-stu-id="64a33-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="64a33-189">W naszym przypadku jest to "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="64a33-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="64a33-190">Teraz, gdy wiemy, że znasz adres `LoaderAllocator` obiektu, można użyć innego polecenia, aby znaleźć jego elementy główne GC:</span><span class="sxs-lookup"><span data-stu-id="64a33-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="64a33-191">To polecenie zrzuca łańcuch odwołań do obiektów, które prowadzą do wystąpienia `LoaderAllocator`.</span><span class="sxs-lookup"><span data-stu-id="64a33-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="64a33-192">Lista rozpoczyna się od elementu głównego, który jest jednostką, która utrzymuje `LoaderAllocator` aktywności i w ten sposób stanowi rdzeń problemu.</span><span class="sxs-lookup"><span data-stu-id="64a33-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="64a33-193">Katalogiem głównym może być gniazdo stosu, rejestr procesora, dojście GC lub zmienna statyczna.</span><span class="sxs-lookup"><span data-stu-id="64a33-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="64a33-194">Oto przykład danych wyjściowych polecenia `gcroot`:</span><span class="sxs-lookup"><span data-stu-id="64a33-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="64a33-195">Następnym krokiem jest określenie, gdzie znajduje się katalog główny, aby można go było usunąć.</span><span class="sxs-lookup"><span data-stu-id="64a33-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="64a33-196">Najłatwiejszym przypadkiem jest to, że katalog główny to gniazdo stosu lub rejestr procesora.</span><span class="sxs-lookup"><span data-stu-id="64a33-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="64a33-197">W takim przypadku `gcroot` wyświetla nazwę funkcji, której ramka zawiera element główny i wątek wykonujący tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="64a33-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="64a33-198">Trudnym przypadkiem jest to, że element główny jest zmienną statyczną lub dojściem GC.</span><span class="sxs-lookup"><span data-stu-id="64a33-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="64a33-199">W poprzednim przykładzie pierwszy element główny jest lokalnym typem `System.Reflection.RuntimeMethodInfo` przechowywanym w ramce `example.Program.Main(System.String[])` funkcji pod adresem `rbp-20` (`rbp` jest rejestrem procesora `rbp` i-20 to szesnastkowe przesunięcie z tego rejestru).</span><span class="sxs-lookup"><span data-stu-id="64a33-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="64a33-200">Drugi katalog główny to normalna (silna) `GCHandle`, która przechowuje odwołanie do wystąpienia klasy `test.Test`.</span><span class="sxs-lookup"><span data-stu-id="64a33-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="64a33-201">Trzeci katalog główny jest przypięty `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="64a33-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="64a33-202">Ten element jest w rzeczywistości zmienną statyczną, ale niestety, nie ma możliwości poinformowania.</span><span class="sxs-lookup"><span data-stu-id="64a33-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="64a33-203">Elementy statyczne dla typów referencyjnych są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="64a33-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="64a33-204">Innym przypadkiem, który może uniemożliwić wyładowywanie `AssemblyLoadContext`, jest to, kiedy wątek ma ramkę metody z zestawu załadowanego do `AssemblyLoadContext` na jego stosie.</span><span class="sxs-lookup"><span data-stu-id="64a33-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="64a33-205">Można sprawdzić, czy są używane stosy wywołań zarządzanych wszystkich wątków:</span><span class="sxs-lookup"><span data-stu-id="64a33-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="64a33-206">Polecenie oznacza "Zastosuj do wszystkich wątków `!clrstack` polecenie".</span><span class="sxs-lookup"><span data-stu-id="64a33-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="64a33-207">Poniżej znajduje się dane wyjściowe tego polecenia dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="64a33-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="64a33-208">Niestety, LLDB w systemie UNIX nie ma żadnego sposobu zastosowania polecenia do wszystkich wątków, więc musisz ręcznie przełączać wątki i powtórzyć `clrstack` polecenie.</span><span class="sxs-lookup"><span data-stu-id="64a33-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="64a33-209">Ignoruj wszystkie wątki, w których debuger "nie może przeprowadzić zarządzanego stosu".</span><span class="sxs-lookup"><span data-stu-id="64a33-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="64a33-210">Jak widać, ostatni wątek ma `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="64a33-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="64a33-211">Jest to funkcja z zestawu, która została załadowana do `AssemblyLoadContext`i dlatego utrzymuje `AssemblyLoadContext` aktywności.</span><span class="sxs-lookup"><span data-stu-id="64a33-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="64a33-212">Przykładowe źródło z problemami z możliwością załadowania</span><span class="sxs-lookup"><span data-stu-id="64a33-212">Example source with unloadability issues</span></span>

<span data-ttu-id="64a33-213">Poniższy kod jest używany w poprzednim przykładzie debugowania.</span><span class="sxs-lookup"><span data-stu-id="64a33-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="64a33-214">Główny program do testowania</span><span class="sxs-lookup"><span data-stu-id="64a33-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="64a33-215">Program został załadowany do TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="64a33-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="64a33-216">Poniższy kod przedstawia *test. dll* przekazaną do metody `ExecuteAndUnload` w głównym programie testowym.</span><span class="sxs-lookup"><span data-stu-id="64a33-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
