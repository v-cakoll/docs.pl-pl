---
title: Jak używać i debugować możliwość odciążania zestawów w programie .NET Core
description: Dowiedz się, jak używać programu AssemblyLoadContexte kolekcjonowane do ładowania i zwalniania zestawów zarządzanych oraz jak debugować problemy uniemożliwiające pomyślne wyładowywanie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: a3ba2c2809aedd0af03ec965089f8779c430a335
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331523"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="d06a2-103">Jak używać i debugować możliwość odciążania zestawów w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="d06a2-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="d06a2-104">Począwszy od platformy .NET Core 3,0, możliwość załadowania i późniejszego zwolnienia zestawu zestawów jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d06a2-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="d06a2-105">W tym celu w .NET Framework użyto niestandardowych domen aplikacji, ale program .NET Core obsługuje tylko jedną domyślną domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d06a2-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="d06a2-106">Program .NET Core 3,0 i jego nowsze wersje obsługują możliwości zwalniania w <xref:System.Runtime.Loader.AssemblyLoadContext>programie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="d06a2-107">Zestaw zestawów można załadować do `AssemblyLoadContext`w nich lub po prostu przeprowadzić ich kontrolę przy użyciu odbicia, a wreszcie `AssemblyLoadContext`Zwolnij.</span><span class="sxs-lookup"><span data-stu-id="d06a2-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="d06a2-108">To zwalnia zestawy ładowane do tego `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="d06a2-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="d06a2-109">Istnieje jedna istotna różnica między zwalnianiem przy `AssemblyLoadContext` użyciu i używania domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d06a2-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="d06a2-110">W przypadku domen aplikacji wyładowywanie jest wymuszane.</span><span class="sxs-lookup"><span data-stu-id="d06a2-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="d06a2-111">W momencie zwolnienia wszystkie wątki działające w docelowej domenie aplikacji są przerywane, zarządzane obiekty COM utworzone w docelowej domenie aplikacji są niszczone itp. W `AssemblyLoadContext`przypadku, Unload to "spółdzielnie".</span><span class="sxs-lookup"><span data-stu-id="d06a2-111">At the unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="d06a2-112"><xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Wywołanie metody po prostu inicjuje zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="d06a2-113">Zwalnianie kończy się po:</span><span class="sxs-lookup"><span data-stu-id="d06a2-113">The unloading finishes after:</span></span>

- <span data-ttu-id="d06a2-114">Żadne wątki nie mają metod z zestawów załadowanych `AssemblyLoadContext` na stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="d06a2-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="d06a2-115">Żaden z typów zestawów nie został załadowany do `AssemblyLoadContext`, wystąpienia tych typów i zestawy same poza `AssemblyLoadContext` nie są przywoływane przez:</span><span class="sxs-lookup"><span data-stu-id="d06a2-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="d06a2-116">Odwołania poza `AssemblyLoadContext`z, z wyjątkiem słabych odwołań (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="d06a2-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="d06a2-117">Mocne uchwyty GC<xref:System.Runtime.InteropServices.GCHandleType>(.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="d06a2-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="d06a2-118">lub <xref:System.Runtime.InteropServices.GCHandleType>)zarównowewnątrz,jakipoza.<xref:System.Runtime.InteropServices.GCHandleType.Pinned> `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="d06a2-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="using-collectible-assemblyloadcontext"></a><span data-ttu-id="d06a2-119">Korzystanie z AssemblyLoadContextów kolekcjonowanych</span><span class="sxs-lookup"><span data-stu-id="d06a2-119">Using collectible AssemblyLoadContext</span></span>

<span data-ttu-id="d06a2-120">Ta sekcja zawiera szczegółowy samouczek krok po kroku, w którym przedstawiono prosty sposób ładowania aplikacji platformy .NET Core do elementu "kolekcjonowania `AssemblyLoadContext`", wykonywania jego punktu wejścia, a następnie jego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="d06a2-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="d06a2-121">Kompletny przykład można znaleźć pod adresem <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span><span class="sxs-lookup"><span data-stu-id="d06a2-121">You can find a complete sample at <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="d06a2-122">Utwórz kolekcjonowaną AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="d06a2-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="d06a2-123">Należy utworzyć klasę z <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążyć jej <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="d06a2-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d06a2-124">Ta metoda rozwiązuje odwołania do wszystkich zestawów, które są zależnościami zestawów ładowanych do `AssemblyLoadContext`tego elementu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="d06a2-125">Poniższy kod jest przykładem najprostszego niestandardowego `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="d06a2-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="d06a2-126">Jak widać, `Load` Metoda zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="d06a2-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="d06a2-127">Oznacza to, że wszystkie zestawy zależności są ładowane do domyślnego kontekstu, a nowy kontekst zawiera tylko zestawy, które są w nim jawnie załadowane.</span><span class="sxs-lookup"><span data-stu-id="d06a2-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="d06a2-128">Jeśli chcesz załadować niektóre lub wszystkie zależności do tego `AssemblyLoadContext` , możesz `AssemblyDependencyResolver` użyć w `Load` metodzie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="d06a2-129">Program rozpoznaje nazwy zestawów dla bezwzględnych ścieżek plików zestawów przy użyciu pliku *. deps. JSON* zawartego w katalogu głównego zestawu załadowanym do kontekstu i przy użyciu plików zestawów w tym katalogu. `AssemblyDependencyResolver`</span><span class="sxs-lookup"><span data-stu-id="d06a2-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the *.deps.json* file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="d06a2-130">Korzystanie z niestandardowego AssemblyLoadContextego kolekcjonowania</span><span class="sxs-lookup"><span data-stu-id="d06a2-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="d06a2-131">W tej sekcji założono, że prostsza `TestAssemblyLoadContext` wersja jest używana.</span><span class="sxs-lookup"><span data-stu-id="d06a2-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="d06a2-132">Można utworzyć wystąpienie niestandardowego `AssemblyLoadContext` i załadować do niego zestaw w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d06a2-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="d06a2-133">Dla każdego z zestawów, do którego odwołuje się załadowany zestaw `TestAssemblyLoadContext.Load` , metoda jest wywoływana, aby `TestAssemblyLoadContext` można było określić miejsce, z którego ma zostać pobrany zestaw.</span><span class="sxs-lookup"><span data-stu-id="d06a2-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="d06a2-134">W naszym przypadku zwraca wartość `null` wskazującą, że powinna zostać załadowana do domyślnego kontekstu z lokalizacji używanych przez środowisko uruchomieniowe do domyślnego ładowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="d06a2-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="d06a2-135">Teraz, gdy zestaw został załadowany, można wykonać z niego metodę.</span><span class="sxs-lookup"><span data-stu-id="d06a2-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="d06a2-136">`Main` Uruchom metodę:</span><span class="sxs-lookup"><span data-stu-id="d06a2-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="d06a2-137">Po powrocie `Unload` `AssemblyLoadContext` `AssemblyLoadContext`metody można zainicjować zwalnianie przez wywołanie metody na Custom lub pozbyć się odwołania do: `Main`</span><span class="sxs-lookup"><span data-stu-id="d06a2-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="d06a2-138">Jest to wystarczające do zwolnienia zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="d06a2-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="d06a2-139">W rzeczywistości przeniesiemy wszystkie te elementy do oddzielnej metody nieliniowej `TestAssemblyLoadContext`, aby upewnić się, że, `MethodInfo` `Assembly`i ( `Assembly.EntryPoint`) nie mogą być utrzymywane przez odwołania do gniazda stosu (wartości lokalne lub JIT).</span><span class="sxs-lookup"><span data-stu-id="d06a2-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="d06a2-140">Może to prowadzić do `TestAssemblyLoadContext` utrzymania aktywności i uniemożliwić zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="d06a2-141">Należy również zwrócić słabe odwołanie do, `AssemblyLoadContext` aby można było użyć go później do wykrywania zakończenia zwalniania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="d06a2-142">Teraz można uruchomić tę funkcję w celu załadowania, wykonania i zwolnienia zestawu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="d06a2-143">Jednak zwalnianie nie zakończy się natychmiast.</span><span class="sxs-lookup"><span data-stu-id="d06a2-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="d06a2-144">Jak wspomniano wcześniej, opiera się on na GC, aby zebrać wszystkie obiekty z zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="d06a2-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="d06a2-145">W wielu przypadkach nie trzeba czekać na ukończenie zwalniania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="d06a2-146">Istnieją jednak przypadki, w których warto wiedzieć, że zwolnienie zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d06a2-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="d06a2-147">Na przykład możesz chcieć usunąć plik zestawu, który został załadowany do niestandardowego `AssemblyLoadContext` z dysku.</span><span class="sxs-lookup"><span data-stu-id="d06a2-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="d06a2-148">W takim przypadku można użyć poniższego fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="d06a2-149">Wyzwala on GC i czeka na oczekujące finalizatory w pętli do momentu, gdy słabe odwołanie do `AssemblyLoadContext` niego jest `null`ustawione na, co wskazuje na to, że obiekt docelowy został zebrany.</span><span class="sxs-lookup"><span data-stu-id="d06a2-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="d06a2-150">Należy pamiętać, że w większości przypadków wymagane jest tylko jedno przejście przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="d06a2-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="d06a2-151">Jednak w przypadku bardziej złożonych przypadków, w których obiekty utworzone przez kod działający `AssemblyLoadContext` w programie mają finalizatory, może być konieczne wykonanie większej liczby przebiegów.</span><span class="sxs-lookup"><span data-stu-id="d06a2-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="d06a2-152">Zdarzenie wyładowywania</span><span class="sxs-lookup"><span data-stu-id="d06a2-152">The Unloading event</span></span>

<span data-ttu-id="d06a2-153">W niektórych przypadkach może być konieczne, aby kod został załadowany do niestandardowym `AssemblyLoadContext` w celu wykonania pewnego oczyszczania po zainicjowaniu zwalniania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="d06a2-154">Na przykład może być konieczne zatrzymanie wątków, oczyszczenie niektórych silnych dojść GC itd. W takich przypadkach można użyć zdarzenia.`Unloading`</span><span class="sxs-lookup"><span data-stu-id="d06a2-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="d06a2-155">Do tego zdarzenia można podłączyć procedurę obsługi, która wykonuje wymagane oczyszczanie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="d06a2-156">Rozwiązywanie problemów z możliwością ponownego ładowania</span><span class="sxs-lookup"><span data-stu-id="d06a2-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="d06a2-157">Ze względu na spółdzielnię zwalniającą, można łatwo zapomnieć o odwołaniach, które ułatwiają odprowadzenie `AssemblyLoadContext` aktywności i uniemożliwiają zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="d06a2-158">Poniżej znajduje się podsumowanie elementów (niektóre z nich nie są oczywiste), które mogą zawierać odwołania:</span><span class="sxs-lookup"><span data-stu-id="d06a2-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="d06a2-159">Regularne odwołania przechowywane poza firmą kolekcjonowaną `AssemblyLoadContext`, przechowywaną w gnieździe stosu lub w rejestrze procesora (metody lokalne, jawnie utworzone przez kod użytkownika lub niejawnie przez JIT), zmiennej statycznej lub dojścia do usługi GC o silnej lub przypinaniu. przechodnie wskazywanie:</span><span class="sxs-lookup"><span data-stu-id="d06a2-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="d06a2-160">Zestaw załadowany do elementu "kolekcjonowane `AssemblyLoadContext`".</span><span class="sxs-lookup"><span data-stu-id="d06a2-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="d06a2-161">Typ z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="d06a2-162">Wystąpienie typu z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="d06a2-163">Wątki uruchamiające kod z zestawu zostały załadowane do `AssemblyLoadContext`kolekcjonowania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="d06a2-164">Wystąpienia niestandardowych niekolekcjonowanych `AssemblyLoadContext` typów utworzonych wewnątrz elementu kolekcjonowanego`AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="d06a2-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="d06a2-165">Wystąpienia <xref:System.Threading.RegisteredWaitHandle> oczekujące z wywołaniami zwrotnymi ustawionymi na metody w niestandardowej`AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="d06a2-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="d06a2-166">Wskazówki dotyczące znajdowania miejsca na stosie/rejestr procesora dla obiektu:</span><span class="sxs-lookup"><span data-stu-id="d06a2-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="d06a2-167">Przekazywanie wyników wywołania funkcji bezpośrednio do innej funkcji może utworzyć katalog główny, nawet jeśli nie istnieje zmienna lokalna utworzona przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d06a2-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="d06a2-168">Jeśli odwołanie do obiektu było dostępne w dowolnym momencie w metodzie, kompilator JIT może postanowić o zachowaniu odwołania w gnieździe stosu/rejestrze procesora tak długo, jak w bieżącej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d06a2-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="d06a2-169">Debuguj problemy z zwalnianiem</span><span class="sxs-lookup"><span data-stu-id="d06a2-169">Debug unloading issues</span></span>

<span data-ttu-id="d06a2-170">Problemy z debugowaniem z rozładowywaniem mogą być żmudnym.</span><span class="sxs-lookup"><span data-stu-id="d06a2-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="d06a2-171">Możesz się dowiedzieć, gdzie nie wiesz, co może być `AssemblyLoadContext` utrzymywane, ale zwolnienie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="d06a2-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="d06a2-172">Najlepsza broń, która pomoże Ci to WinDbg (LLDB w systemie UNIX) z wtyczką SOS.</span><span class="sxs-lookup"><span data-stu-id="d06a2-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="d06a2-173">Należy się dowiedzieć, co zachowuje `LoaderAllocator` się z konkretną `AssemblyLoadContext` aktywnością.</span><span class="sxs-lookup"><span data-stu-id="d06a2-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="d06a2-174">Ta wtyczka umożliwia przeglądanie obiektów sterty GC, ich hierarchii i katalogów głównych.</span><span class="sxs-lookup"><span data-stu-id="d06a2-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="d06a2-175">Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:</span><span class="sxs-lookup"><span data-stu-id="d06a2-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="d06a2-176">W programie WinDbg (po załamaniu do aplikacji .NET Core) automatycznie</span><span class="sxs-lookup"><span data-stu-id="d06a2-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="d06a2-177">W LLDB:</span><span class="sxs-lookup"><span data-stu-id="d06a2-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="d06a2-178">Spróbujmy debugować Przykładowy program, który ma problemy z wyładunkiem.</span><span class="sxs-lookup"><span data-stu-id="d06a2-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="d06a2-179">Kod źródłowy jest uwzględniony poniżej.</span><span class="sxs-lookup"><span data-stu-id="d06a2-179">Source code is included below.</span></span> <span data-ttu-id="d06a2-180">Gdy uruchamiasz go w ramach usługi WinDbg, program przerwie się w debugerze po podjęciu próby sprawdzenia powodzenia zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="d06a2-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="d06a2-181">Następnie można rozpocząć wyszukiwanie culprits.</span><span class="sxs-lookup"><span data-stu-id="d06a2-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="d06a2-182">Należy pamiętać, że jeśli debugujesz przy użyciu LLDB w systemie UNIX, polecenia sos w poniższych przykładach `!` nie mają przed nimi.</span><span class="sxs-lookup"><span data-stu-id="d06a2-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="d06a2-183">To polecenie zrzuca wszystkie obiekty o nazwie typu zawierającego `LoaderAllocator` te, które znajdują się w stercie GC.</span><span class="sxs-lookup"><span data-stu-id="d06a2-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="d06a2-184">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="d06a2-184">Here is an example:</span></span>

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

<span data-ttu-id="d06a2-185">W poniższym składniku "Statistics:" Sprawdź `MT` (`MethodTable`) należący do `System.Reflection.LoaderAllocator`obiektu, który jest obiektem, którego potrzebujemy.</span><span class="sxs-lookup"><span data-stu-id="d06a2-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="d06a2-186">Następnie na liście na początku Znajdź wpis ze zgodną z `MT` nim i uzyskaj adres samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="d06a2-187">W naszym przypadku jest to "000002b78000ce40"</span><span class="sxs-lookup"><span data-stu-id="d06a2-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="d06a2-188">Teraz, gdy wiemy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć jego elementy główne GC</span><span class="sxs-lookup"><span data-stu-id="d06a2-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="d06a2-189">To polecenie zrzuca łańcuch odwołań do obiektów, które prowadzą do `LoaderAllocator` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d06a2-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="d06a2-190">Lista rozpoczyna się od elementu głównego, który jest obiektem, który utrzymuje `LoaderAllocator` naszą aktywność i w ten sposób stanowi rdzeń debugowanego problemu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="d06a2-191">Katalogiem głównym może być gniazdo stosu, rejestr procesora, dojście GC lub zmienna statyczna.</span><span class="sxs-lookup"><span data-stu-id="d06a2-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="d06a2-192">Oto przykład danych wyjściowych `gcroot` polecenia:</span><span class="sxs-lookup"><span data-stu-id="d06a2-192">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="d06a2-193">Teraz musisz ustalić, gdzie znajduje się katalog główny, aby można go było usunąć.</span><span class="sxs-lookup"><span data-stu-id="d06a2-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="d06a2-194">Najłatwiejszym przypadkiem jest to, że katalog główny to gniazdo stosu lub rejestr procesora.</span><span class="sxs-lookup"><span data-stu-id="d06a2-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="d06a2-195">W takim przypadku `gcroot` pokazuje nazwę funkcji, której ramka zawiera element główny i wątek wykonujący tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="d06a2-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="d06a2-196">Trudnym przypadkiem jest to, że element główny jest zmienną statyczną lub dojściem GC.</span><span class="sxs-lookup"><span data-stu-id="d06a2-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="d06a2-197">W poprzednim przykładzie pierwszy element główny jest lokalnym typem `System.Reflection.RuntimeMethodInfo` przechowywanym w ramce funkcji `example.Program.Main(System.String[])` pod adresem `rbp-20` (`rbp` jest to rejestr `rbp` procesora i-20 to szesnastkowe przesunięcie z tego rejestru).</span><span class="sxs-lookup"><span data-stu-id="d06a2-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="d06a2-198">Drugi katalog główny to normalna (silna `GCHandle` ), która przechowuje odwołanie do wystąpienia `test.Test` klasy.</span><span class="sxs-lookup"><span data-stu-id="d06a2-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="d06a2-199">Trzeci element główny jest przypięty `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="d06a2-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="d06a2-200">Ten element jest w rzeczywistości zmienną statyczną.</span><span class="sxs-lookup"><span data-stu-id="d06a2-200">This one is actually a static variable.</span></span> <span data-ttu-id="d06a2-201">Niestety, nie ma możliwości poinformowania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="d06a2-202">Elementy statyczne dla typów referencyjnych są przechowywane w tablicy obiektów zarządzanych w wewnętrznych strukturach środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d06a2-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="d06a2-203">Innym przypadkiem, który może uniemożliwiać `AssemblyLoadContext` zwolnienie, jest, gdy wątek ma ramkę metody z zestawu załadowanego `AssemblyLoadContext` do obiektu na jego stosie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="d06a2-204">Można sprawdzić, czy są używane stosy wywołań zarządzanych wszystkich wątków:</span><span class="sxs-lookup"><span data-stu-id="d06a2-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="d06a2-205">Polecenie oznacza "Zastosuj do wszystkich wątków `!clrstack` polecenia".</span><span class="sxs-lookup"><span data-stu-id="d06a2-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="d06a2-206">Poniżej znajduje się dane wyjściowe tego polecenia dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="d06a2-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="d06a2-207">Niestety, LLDB w systemie UNIX nie ma żadnego sposobu, aby zastosować polecenie do wszystkich wątków, więc musisz ręcznie przełączać wątki i powtarzać `clrstack` polecenie.</span><span class="sxs-lookup"><span data-stu-id="d06a2-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="d06a2-208">Ignoruj wszystkie wątki, w których ten debuger brzmi "nie można przeprowadzić zarządzanego stosu".</span><span class="sxs-lookup"><span data-stu-id="d06a2-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

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

<span data-ttu-id="d06a2-209">Jak widać, ostatni wątek ma `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="d06a2-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="d06a2-210">Jest to funkcja z zestawu `AssemblyLoadContext`, która została załadowana do, i dlatego `AssemblyLoadContext` utrzymuje aktywności.</span><span class="sxs-lookup"><span data-stu-id="d06a2-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="d06a2-211">Przykładowe źródło z problemami z możliwością załadowania</span><span class="sxs-lookup"><span data-stu-id="d06a2-211">Example source with unloadability issues</span></span>

<span data-ttu-id="d06a2-212">Poniższy kod jest używany w poprzednim przykładzie debugowania.</span><span class="sxs-lookup"><span data-stu-id="d06a2-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="d06a2-213">Główny program do testowania</span><span class="sxs-lookup"><span data-stu-id="d06a2-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="d06a2-214">Program został załadowany do TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="d06a2-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="d06a2-215">Poniższy kod reprezentuje `test.dll` przekazaną `ExecuteAndUnload` do metody w głównym programie testowym.</span><span class="sxs-lookup"><span data-stu-id="d06a2-215">The following code represents the `test.dll` passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
