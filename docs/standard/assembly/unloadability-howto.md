---
title: Sposób użycia i debugować unloadability zestawu w programie .NET Core
description: Dowiedz się, jak używać kolekcjonowane AssemblyLoadContext zarządzane zestawy, ładowanie i zwalnianie i jak debugować problemy, zapobiegając powodzeniu zwalnianie.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627790"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="0ea69-103">Sposób użycia i debugować unloadability zestawu w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="0ea69-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="0ea69-104">Począwszy od .NET Core 3.0 to możliwość ładowanie i zwalnianie później zbiór zestawów jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="0ea69-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="0ea69-105">W programie .NET Framework domen niestandardowych aplikacji zostały użyte w tym celu, ale program .NET Core obsługuje tylko jednej domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ea69-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="0ea69-106">.NET core 3.0 i nowsze wersje obsługują unloadability za pośrednictwem <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="0ea69-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="0ea69-107">Możesz załadować zbiór zestawów, do kolekcjonowane `AssemblyLoadContext`, wykonywanie metod w nich lub po prostu je sprawdzić przy użyciu odbicia, a na koniec Zwolnij `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="0ea69-108">Zwalnia, zestawy, ładowane `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="0ea69-109">Brak warte zauważenia różnicy usuwaniu z niej za pomocą `AssemblyLoadContext` i używanie domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ea69-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="0ea69-110">Zwalnianie jest wymuszone za pomocą domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0ea69-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="0ea69-111">W czasie Zwolnij wszystkie wątki uruchomione w docelowej domenie aplikacji zostało przerwane, zarządzanych obiektów COM, utworzone w docelowej domeny aplikacji są niszczone, itp. Za pomocą `AssemblyLoadContext`, zwolnij jest "wspólne".</span><span class="sxs-lookup"><span data-stu-id="0ea69-111">At the unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="0ea69-112">Wywoływanie <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> metoda po prostu inicjuje zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="0ea69-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="0ea69-113">Zwalnianie zostanie zakończone po:</span><span class="sxs-lookup"><span data-stu-id="0ea69-113">The unloading finishes after:</span></span>

- <span data-ttu-id="0ea69-114">Żadne wątki nie mają metod z zestawy, ładowane `AssemblyLoadContext` na ich stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="0ea69-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="0ea69-115">Żaden z typów z zestawy ładowane `AssemblyLoadContext`, wystąpień tych typów i zestawy, samodzielnie poza `AssemblyLoadContext` są przywoływane przez:</span><span class="sxs-lookup"><span data-stu-id="0ea69-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="0ea69-116">Odwołuje się poza `AssemblyLoadContext`, z wyjątkiem słabe odwołania (<xref:System.WeakReference> lub <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="0ea69-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="0ea69-117">Uchwyty silne GC (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="0ea69-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="0ea69-118">lub <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) z obu wewnątrz lub poza `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="using-collectible-assemblyloadcontext"></a><span data-ttu-id="0ea69-119">Za pomocą AssemblyLoadContext kolekcjonowane</span><span class="sxs-lookup"><span data-stu-id="0ea69-119">Using collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0ea69-120">Ta sekcja zawiera szczegółowy samouczek krok po kroku, który pokazuje prosty sposób ładowania aplikacji .NET Core kolekcjonowane `AssemblyLoadContext`, wykonaj jego punktu wejścia, a następnie zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="0ea69-121">Możesz znaleźć pełny przykład o <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span><span class="sxs-lookup"><span data-stu-id="0ea69-121">You can find a complete sample at <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="0ea69-122">Tworzenie AssemblyLoadContext kolekcjonowane</span><span class="sxs-lookup"><span data-stu-id="0ea69-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0ea69-123">Muszą pochodzić z klasy <xref:System.Runtime.Loader.AssemblyLoadContext> i przeciążenia jego <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0ea69-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0ea69-124">Czy metoda jest rozpoznawana jako odwołania do wszystkich zestawów, które zależności zestawów są ładowane, które `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="0ea69-125">Poniższy kod jest przykładem najprostszym niestandardowe `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="0ea69-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="0ea69-126">Jak widać, `Load` metoda zwraca `null`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="0ea69-127">Oznacza to, że wszystkie zespoły zależności są ładowane w kontekście domyślnym, a nowy kontekst zawiera tylko zestawy jawnie załadowane do niego.</span><span class="sxs-lookup"><span data-stu-id="0ea69-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="0ea69-128">Jeśli chcesz załadować niektóre lub wszystkie zależności do `AssemblyLoadContext` , możesz użyć `AssemblyDependencyResolver` w `Load` metody.</span><span class="sxs-lookup"><span data-stu-id="0ea69-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="0ea69-129">`AssemblyDependencyResolver` Jest rozpoznawany jako nazwy zestawów zestawu bezwzględnej ścieżki plików przy użyciu `*.deps.json` pliku znajdującego się w katalogu głównym zestawie ładowane do kontekstu i korzystanie z zestawu plików, w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the `*.deps.json` file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="0ea69-130">Użyj niestandardowego AssemblyLoadContext kolekcjonowane</span><span class="sxs-lookup"><span data-stu-id="0ea69-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0ea69-131">W tej sekcji założono prostszej wersji `TestAssemblyLoadContext` jest używana.</span><span class="sxs-lookup"><span data-stu-id="0ea69-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="0ea69-132">Można utworzyć wystąpienia niestandardowego `AssemblyLoadContext` i załadować zestawu do niego w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0ea69-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="0ea69-133">Dla każdego zestawy przywoływane przez załadowany zestaw `TestAssemblyLoadContext.Load` metoda jest wywoływana, aby `TestAssemblyLoadContext` zdecydować, gdzie można pobrać zestawu z.</span><span class="sxs-lookup"><span data-stu-id="0ea69-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="0ea69-134">W naszym przypadku zwraca `null` do wskazania, że jej powinny być załadowane do domyślnego kontekstu z lokalizacji, używanych przez środowisko uruchomieniowe ładować zestawy domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0ea69-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="0ea69-135">Teraz, że zestaw został załadowany, można wykonać metody z niego.</span><span class="sxs-lookup"><span data-stu-id="0ea69-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="0ea69-136">Uruchom `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="0ea69-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="0ea69-137">Po `Main` metoda zwróci wartość, możesz zainicjować zwalnianie za pośrednictwem dowolnego wywołania `Unload` metody na niestandardowej `AssemblyLoadContext` lub pozbycia się odwołania trzeba `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="0ea69-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="0ea69-138">Jest to wystarczające zwolnić zestaw testowy.</span><span class="sxs-lookup"><span data-stu-id="0ea69-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="0ea69-139">Faktycznie umieśćmy wszystko to w oddzielnych metodach inlineable, aby upewnić się, że `TestAssemblyLoadContext`, `Assembly`, i `MethodInfo` ( `Assembly.EntryPoint`) nie może utrzymywać ich aktywność stosu miejsca odwołania (zmiennych lokalnych wprowadzone rzeczywistym lub JIT).</span><span class="sxs-lookup"><span data-stu-id="0ea69-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="0ea69-140">Można zachować `TestAssemblyLoadContext` aktywności i zapobiec zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="0ea69-141">Ponadto Zwróć słabe odwołanie do `AssemblyLoadContext` tak, aby można było jej użyć później do wykrycia ukończenia zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="0ea69-142">Teraz możesz uruchamiać tę funkcję, aby załadować, wykonywanie i zwolnić zestaw.</span><span class="sxs-lookup"><span data-stu-id="0ea69-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="0ea69-143">Jednak zwolnienie nie wykona natychmiast.</span><span class="sxs-lookup"><span data-stu-id="0ea69-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="0ea69-144">Jak wspomniano wcześniej opiera się na GC, aby zbierać wszystkie obiekty z zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="0ea69-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="0ea69-145">W wielu przypadkach nie trzeba czekać na ukończenie zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="0ea69-146">Jednak istnieją przypadki, w których warto wiedzieć, że zwolnienie została zakończona.</span><span class="sxs-lookup"><span data-stu-id="0ea69-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="0ea69-147">Na przykład, można usunąć pliku zestawu, który został załadowany do niestandardowej `AssemblyLoadContext` z dysku.</span><span class="sxs-lookup"><span data-stu-id="0ea69-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="0ea69-148">W takim przypadku służy poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="0ea69-149">Wyzwala wykazem Globalnym i czeka na oczekujące finalizatory w pętli do momentu słabe odwołanie do niestandardowej `AssemblyLoadContext` ustawiono `null`, wskazujące obiekt docelowy został zebrany.</span><span class="sxs-lookup"><span data-stu-id="0ea69-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="0ea69-150">Należy zauważyć, że tylko jeden przebieg za pomocą pętli w większości przypadków jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="0ea69-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="0ea69-151">Jednak w przypadku bardziej złożonych przypadkach, w których obiekty są tworzone przez kod uruchomiony w `AssemblyLoadContext` mają finalizatory, może być wymagane więcej przebiegów.</span><span class="sxs-lookup"><span data-stu-id="0ea69-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="0ea69-152">Zwalnianie zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0ea69-152">The Unloading event</span></span>

<span data-ttu-id="0ea69-153">W niektórych przypadkach może być konieczne dla kodu załadowane do niestandardowego `AssemblyLoadContext` do wykonania niektórych oczyszczania po zainicjowaniu zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="0ea69-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="0ea69-154">Na przykład może wymagać zatrzymać wątków, czyszczenie niektóre silne uchwyty GC itp. `Unloading` Zdarzenia mogą być używane w takich przypadkach.</span><span class="sxs-lookup"><span data-stu-id="0ea69-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="0ea69-155">Program obsługi, który wykonuje niezbędne czyszczenia mogą być dołączane do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="0ea69-156">Rozwiązywanie problemów unloadability</span><span class="sxs-lookup"><span data-stu-id="0ea69-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="0ea69-157">Ze względu na charakter współpracy rozładowania, to można łatwo zapomnieć o odwołaniach do pamiętając zebrać kolekcjonowane `AssemblyLoadContext` aktywności i zapobieganie zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="0ea69-158">Poniżej przedstawiono podsumowanie elementów (niektóre z nich nie jest oczywisty), jaką może zawierać odwołania:</span><span class="sxs-lookup"><span data-stu-id="0ea69-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="0ea69-159">Odwołania do regularnego przechowywane z poza kolekcjonowane `AssemblyLoadContext`, przechowywanych w miejsca na stosie lub rejestrze procesora (metoda zmiennych lokalnych, albo jawnie tworzone przez kod użytkownika, albo niejawnie przez kompilator JIT), zmienna statyczna lub uchwyt GC silne / przypinania, i Wskazuje sposób przechodni:</span><span class="sxs-lookup"><span data-stu-id="0ea69-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="0ea69-160">Zestaw jest ładowany do kolekcjonowane `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="0ea69-161">Typ z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="0ea69-162">Wystąpienie typu z takiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="0ea69-163">Wątki uruchamiania kodu z zestawu, o których ładowane kolekcjonowane `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="0ea69-164">Wystąpienia elementu niestandardowego kolekcjonowane `AssemblyLoadContext` typy utworzone wewnątrz kolekcjonowane `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="0ea69-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="0ea69-165">Oczekujące <xref:System.Threading.RegisteredWaitHandle> wystąpień przy użyciu wywołania zwrotne równa metod w niestandardowej `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="0ea69-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="0ea69-166">Wskazówki można znaleźć miejsca na stosie / procesora register zakorzenienia obiektu:</span><span class="sxs-lookup"><span data-stu-id="0ea69-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="0ea69-167">Przekazywanie wywołanie funkcji wyniki bezpośrednio do innej funkcji może utworzyć katalog główny, nawet jeśli nie jest zmienna lokalna nie utworzone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0ea69-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="0ea69-168">Jeśli odwołanie do obiektu była dostępna w dowolnym momencie w metodzie, kompilator JIT może zdecydował się utrzymywać odwołania w gnieździe stosu / procesora Zarejestruj się, aby tak długo, jak należy utworzyć w bieżącej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0ea69-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="0ea69-169">Debugowanie problemów zwalnianie</span><span class="sxs-lookup"><span data-stu-id="0ea69-169">Debug unloading issues</span></span>

<span data-ttu-id="0ea69-170">Debugowanie problemów z zwalnianie może być żmudne.</span><span class="sxs-lookup"><span data-stu-id="0ea69-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="0ea69-171">Możesz znaleźć się w sytuacjach, w których nie wiesz, co może być zawierający `AssemblyLoadContext` aktywne, ale Zwolnij kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0ea69-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="0ea69-172">Najlepsze broń pomoże Ci, jest WinDbg (LLDB w systemach Unix) za pomocą wtyczki SOS.</span><span class="sxs-lookup"><span data-stu-id="0ea69-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="0ea69-173">Należy określić, co może być utrzymywanie `LoaderAllocator` należące do konkretnej `AssemblyLoadContext` podtrzymywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="0ea69-174">Ta wtyczka umożliwia Spójrz na obiektach sterty GC, hierarchie i katalogi główne.</span><span class="sxs-lookup"><span data-stu-id="0ea69-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="0ea69-175">Aby załadować wtyczkę do debugera, wprowadź następujące polecenie w wierszu polecenia debugera:</span><span class="sxs-lookup"><span data-stu-id="0ea69-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="0ea69-176">W WinDbg (prawdopodobnie WinDbg robi to w automatycznie przy okazji do aplikacji .NET Core):</span><span class="sxs-lookup"><span data-stu-id="0ea69-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="0ea69-177">W LLDB:</span><span class="sxs-lookup"><span data-stu-id="0ea69-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="0ea69-178">Spróbujmy przykładowy program, który ma problemy z zwalnianie debugowania.</span><span class="sxs-lookup"><span data-stu-id="0ea69-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="0ea69-179">Kod źródłowy znajduje się poniżej.</span><span class="sxs-lookup"><span data-stu-id="0ea69-179">Source code is included below.</span></span> <span data-ttu-id="0ea69-180">Po uruchomieniu go w obszarze WinDbg program dzieli się na debuger po prawej stronie po próby sprawdzenia w celu osiągnięcia sukcesu zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="0ea69-181">Możesz następnie rozpocząć wyszukiwanie sprawcami.</span><span class="sxs-lookup"><span data-stu-id="0ea69-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="0ea69-182">Należy pamiętać, że w przypadku debugowania za pomocą LLDB w systemach Unix, nie ma poleceń SOS w poniższych przykładach `!` przed nimi.</span><span class="sxs-lookup"><span data-stu-id="0ea69-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="0ea69-183">To polecenie zrzuca wszystkie obiekty z zawierający nazwę typu `LoaderAllocator` znajdujących się w stercie GC.</span><span class="sxs-lookup"><span data-stu-id="0ea69-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="0ea69-184">Oto przykład:</span><span class="sxs-lookup"><span data-stu-id="0ea69-184">Here is an example:</span></span>

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

<span data-ttu-id="0ea69-185">W "statystyki:" wchodzi w skład poniżej wyboru `MT` (`MethodTable`) należące do `System.Reflection.LoaderAllocator`, który jest obiektem Dbamy o.</span><span class="sxs-lookup"><span data-stu-id="0ea69-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="0ea69-186">Następnie na liście na początku, znajdź wpis o `MT` dopasowanie ten. i Uzyskaj adres samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="0ea69-187">W naszym przypadku jest "000002b78000ce40"</span><span class="sxs-lookup"><span data-stu-id="0ea69-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="0ea69-188">Teraz, gdy wiemy adres `LoaderAllocator` obiektu, możemy użyć innego polecenia, aby znaleźć korzenie jego GC</span><span class="sxs-lookup"><span data-stu-id="0ea69-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="0ea69-189">To polecenie zrzuca łańcuch odwołania do obiektów, które mogą prowadzić do `LoaderAllocator` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="0ea69-190">Lista zaczyna się od katalogu głównego, który jest obiektem, który utrzymuje naszych `LoaderAllocator` aktywny i w związku z tym to podstawowe rozwiązanie problemu debugowania.</span><span class="sxs-lookup"><span data-stu-id="0ea69-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="0ea69-191">Katalog główny może być miejsca na stosie, rejestrze procesora, uchwyt GC lub zmienna statyczna.</span><span class="sxs-lookup"><span data-stu-id="0ea69-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="0ea69-192">Oto przykład danych wyjściowych `gcroot` polecenia:</span><span class="sxs-lookup"><span data-stu-id="0ea69-192">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="0ea69-193">Teraz należy ustalić, której głównym znajduje się więc można go naprawić.</span><span class="sxs-lookup"><span data-stu-id="0ea69-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="0ea69-194">Najprostszym przypadku to główny miejsca na stosie lub rejestrze procesora.</span><span class="sxs-lookup"><span data-stu-id="0ea69-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="0ea69-195">W takim przypadku `gcroot` Wyświetla nazwę funkcji, w których ramka nie zawiera katalog główny i wątek wykonywania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="0ea69-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="0ea69-196">Tak trudne jest, gdy katalog główny jest zmienna statyczna lub uchwyt GC.</span><span class="sxs-lookup"><span data-stu-id="0ea69-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="0ea69-197">W poprzednim przykładzie pierwszy katalog główny jest lokalne o typie `System.Reflection.RuntimeMethodInfo` przechowywane w ramce funkcja `example.Program.Main(System.String[])` pod adresem `rbp-20` (`rbp` jest rejestrze procesora `rbp` i -20 jest szesnastkowe przesunięcie z tego rejestru).</span><span class="sxs-lookup"><span data-stu-id="0ea69-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="0ea69-198">Drugi katalog główny jest jako normalny (silną) `GCHandle` zawierający odwołanie do wystąpienia `test.Test` klasy.</span><span class="sxs-lookup"><span data-stu-id="0ea69-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="0ea69-199">Trzeci główny jest przypięty `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="0ea69-200">Ten zestaw jest faktycznie zmienną statyczną.</span><span class="sxs-lookup"><span data-stu-id="0ea69-200">This one is actually a static variable.</span></span> <span data-ttu-id="0ea69-201">Niestety nie ma możliwości mówić.</span><span class="sxs-lookup"><span data-stu-id="0ea69-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="0ea69-202">Danych statycznych dla typów odwołania są przechowywane w tablicy obiektu zarządzanego w strukturach wewnętrznego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0ea69-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="0ea69-203">Inny przypadek, które mogą uniemożliwić zwalniania `AssemblyLoadContext` , gdy wątek ma ramkę metodę z zestawu załadowaniu do `AssemblyLoadContext` na swój stos.</span><span class="sxs-lookup"><span data-stu-id="0ea69-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="0ea69-204">Aby sprawdzić, czy przez zrzucanie zarządzane stosy wywołań wszystkich wątków:</span><span class="sxs-lookup"><span data-stu-id="0ea69-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="0ea69-205">Oznacza, że polecenie "Zastosuj do wszystkich wątków `!clrstack` polecenia".</span><span class="sxs-lookup"><span data-stu-id="0ea69-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="0ea69-206">Oto dane wyjściowe tego polecenia dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="0ea69-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="0ea69-207">Niestety, LLDB w systemach Unix nie ma żadnego sposobu zastosowanie polecenia do wszystkich wątków, więc należy odwołać się do ręcznego przełączania wątków i powtórzenie `clrstack` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="0ea69-208">Ignoruj wszystkich wątków, w której debuger jest wyświetlany komunikat "Niemożliwości zapoznaj się z zarządzanego stosu."</span><span class="sxs-lookup"><span data-stu-id="0ea69-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

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

<span data-ttu-id="0ea69-209">Jak widać, ostatni wątek ma `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="0ea69-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="0ea69-210">Jest to funkcja z zestawu ładowany `AssemblyLoadContext`, i dlatego zapewnia `AssemblyLoadContext` podtrzymywania połączenia.</span><span class="sxs-lookup"><span data-stu-id="0ea69-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="0ea69-211">Przykładowe źródła z problemami unloadability</span><span class="sxs-lookup"><span data-stu-id="0ea69-211">Example source with unloadability issues</span></span>

<span data-ttu-id="0ea69-212">Poniższy kod jest używany w poprzednim przykładzie debugowania.</span><span class="sxs-lookup"><span data-stu-id="0ea69-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="0ea69-213">Główny program testowania</span><span class="sxs-lookup"><span data-stu-id="0ea69-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="0ea69-214">Program ładowany TestAssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="0ea69-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="0ea69-215">Poniższy kod przedstawia `test.dll` przekazany do `ExecuteAndUnload` metody w głównym program testów.</span><span class="sxs-lookup"><span data-stu-id="0ea69-215">The following code represents the `test.dll` passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
