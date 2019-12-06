---
title: Programowanie asynchroniczne wF#
description: Dowiedz F# się, jak zapewniać czystą pomoc techniczną dla asynchroniczności w oparciu o model programowania na poziomie języka pochodzący z podstawowych koncepcji programowania funkcjonalnego.
ms.date: 12/17/2018
ms.openlocfilehash: 583b0f5154e6ad8875b21503cfb78f70a069ff7b
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837106"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="7f92d-103">Programowanie asynchroniczne w języku F\#</span><span class="sxs-lookup"><span data-stu-id="7f92d-103">Async programming in F\#</span></span>

<span data-ttu-id="7f92d-104">Programowanie asynchroniczne jest mechanizmem, który jest niezbędny dla nowoczesnych aplikacji z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="7f92d-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="7f92d-105">Istnieją dwa podstawowe przypadki użycia, które napotykają większość deweloperów:</span><span class="sxs-lookup"><span data-stu-id="7f92d-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="7f92d-106">Przedstawienie procesu serwera, który może obsłużyć znaczną liczbę współbieżnych żądań przychodzących, jednocześnie minimalizując zasoby systemowe zajęte podczas przetwarzania żądań czeka na dane wejściowe z systemów lub usług zewnętrznych dla tego procesu</span><span class="sxs-lookup"><span data-stu-id="7f92d-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="7f92d-107">Utrzymywanie odpowiedzi na interfejsie użytkownika lub głównego wątku podczas współbieżnego postępu pracy w tle</span><span class="sxs-lookup"><span data-stu-id="7f92d-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="7f92d-108">Mimo że prace w tle często obejmują wykorzystanie wielu wątków, ważne jest, aby rozważyć koncepcje asynchroniczności i wielowątkowości osobno.</span><span class="sxs-lookup"><span data-stu-id="7f92d-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="7f92d-109">W rzeczywistości są one oddzielnymi problemami, a jeden z nich nie ma innych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="7f92d-110">W tym artykule opisano to w bardziej szczegółowy sposób.</span><span class="sxs-lookup"><span data-stu-id="7f92d-110">What follows in this article will describe this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="7f92d-111">Asynchroniczności zdefiniowany</span><span class="sxs-lookup"><span data-stu-id="7f92d-111">Asynchrony defined</span></span>

<span data-ttu-id="7f92d-112">Poprzedni punkt — ten asynchroniczności jest niezależny od użycia wielu wątków — jest również bardziej opisowy.</span><span class="sxs-lookup"><span data-stu-id="7f92d-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="7f92d-113">Istnieją trzy koncepcje, które są czasami powiązane, ale ściśle niezależne od siebie:</span><span class="sxs-lookup"><span data-stu-id="7f92d-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="7f92d-114">Współbieżności gdy wiele obliczeń jest wykonywanych w nadchodzących okresach czasowych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="7f92d-115">Równoległości gdy wiele obliczeń lub kilka części jednego obliczenia jest wykonywanych w dokładnie tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="7f92d-116">Asynchroniczności gdy jedno lub więcej obliczeń można wykonać niezależnie od przepływu głównego programu.</span><span class="sxs-lookup"><span data-stu-id="7f92d-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="7f92d-117">Wszystkie trzy są koncepcjami prostopadłymi, ale można je łatwo rozliczać, szczególnie gdy są używane razem.</span><span class="sxs-lookup"><span data-stu-id="7f92d-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="7f92d-118">Na przykład może być konieczne wykonanie wielu obliczeń asynchronicznych równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="7f92d-119">Nie oznacza to, że równoległość lub asynchroniczności oznacza siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="7f92d-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="7f92d-120">Jeśli rozważasz etymology słowa "asynchroniczne", istnieją dwa elementy:</span><span class="sxs-lookup"><span data-stu-id="7f92d-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="7f92d-121">"a", znaczenie "nie".</span><span class="sxs-lookup"><span data-stu-id="7f92d-121">"a", meaning "not".</span></span>
- <span data-ttu-id="7f92d-122">"synchroniczne", znaczenie "w tym samym czasie".</span><span class="sxs-lookup"><span data-stu-id="7f92d-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="7f92d-123">Po umieszczeniu tych dwóch terminów, zobaczysz, że "asynchroniczne" oznacza "nie w tym samym czasie".</span><span class="sxs-lookup"><span data-stu-id="7f92d-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="7f92d-124">To wszystko!</span><span class="sxs-lookup"><span data-stu-id="7f92d-124">That's it!</span></span> <span data-ttu-id="7f92d-125">W tej definicji nie ma implikacji współbieżności ani równoległości.</span><span class="sxs-lookup"><span data-stu-id="7f92d-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="7f92d-126">Ta metoda jest również prawdziwa.</span><span class="sxs-lookup"><span data-stu-id="7f92d-126">This is also true in practice.</span></span>

<span data-ttu-id="7f92d-127">W praktyce, asynchroniczne obliczenia w programie F# są zaplanowane do wykonania niezależnie od przepływu głównego programu.</span><span class="sxs-lookup"><span data-stu-id="7f92d-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="7f92d-128">Nie oznacza to współbieżności ani równoległości, ani nie oznacza, że Obliczanie zawsze odbywa się w tle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="7f92d-129">W rzeczywistości asynchroniczne obliczenia mogą nawet wykonywać synchronicznie, w zależności od rodzaju obliczenia i środowiska, w którym jest wykonywane obliczenie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="7f92d-130">Głównym wnioskiemem jest to, że obliczenia asynchroniczne są niezależne od przepływu głównego programu.</span><span class="sxs-lookup"><span data-stu-id="7f92d-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="7f92d-131">Chociaż istnieją pewne gwarancje dotyczące tego, kiedy lub jak są wykonywane asynchroniczne obliczenia, istnieją niektóre podejścia do organizowania i planowania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="7f92d-132">Pozostała część tego artykułu eksploruje podstawowe koncepcje dotyczące F# asynchroniczności oraz sposób używania typów, funkcji i wyrażeń wbudowanych w. F#</span><span class="sxs-lookup"><span data-stu-id="7f92d-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="7f92d-133">Podstawowe koncepcje</span><span class="sxs-lookup"><span data-stu-id="7f92d-133">Core concepts</span></span>

<span data-ttu-id="7f92d-134">W F#programie programowanie asynchroniczne zawiera trzy podstawowe koncepcje:</span><span class="sxs-lookup"><span data-stu-id="7f92d-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="7f92d-135">Typ `Async<'T>`, który reprezentuje szeregowe Obliczanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="7f92d-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="7f92d-136">Funkcje modułu `Async`, które umożliwiają planowanie pracy asynchronicznej, tworzenie obliczeń asynchronicznych i przekształcanie asynchronicznych wyników.</span><span class="sxs-lookup"><span data-stu-id="7f92d-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="7f92d-137">`async { }` [wyrażenie obliczania](../../language-reference/computation-expressions.md), które zapewnia wygodną składnię do kompilowania i kontrolowania asynchronicznych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7f92d-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="7f92d-138">Te trzy koncepcje można zobaczyć w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="7f92d-138">You can see these three concepts in the following example:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    printTotalFileBytes "path-to-file.txt"
    |> Async.RunSynchronously

    Console.Read() |> ignore
    0
```

<span data-ttu-id="7f92d-139">W przykładzie funkcja `printTotalFileBytes` jest typu `string -> Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="7f92d-140">Wywołanie funkcji nie powoduje rzeczywistego wykonania obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="7f92d-141">Zamiast tego zwraca `Async<unit>`, który działa jako Specyfikacja \* dla pracy, która jest wykonywana asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-141">Instead, it returns an `Async<unit>` that acts as a \*specification- of the work that is to execute asynchronously.</span></span> <span data-ttu-id="7f92d-142">Wywoła `Async.AwaitTask` w swojej treści, co spowoduje przekonwertowanie wyniku <xref:System.IO.File.WriteAllBytesAsync%2A> do odpowiedniego typu, gdy zostanie on wywołany.</span><span class="sxs-lookup"><span data-stu-id="7f92d-142">It will call `Async.AwaitTask` in its body, which will convert the result of <xref:System.IO.File.WriteAllBytesAsync%2A> to an appropriate type when it is called.</span></span>

<span data-ttu-id="7f92d-143">Innym ważnym wierszem jest wywołanie `Async.RunSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="7f92d-144">Jest to jeden z funkcji uruchamiania modułów asynchronicznych, które należy wywołać, jeśli chcesz rzeczywiście wykonać F# asynchroniczne obliczanie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="7f92d-145">Jest to podstawowa różnica ze stylem C#/VB programowania `async`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-145">This is a fundamental difference with the C#/VB style of `async` programming.</span></span> <span data-ttu-id="7f92d-146">W F#programie asynchroniczne obliczenia można traktować jako **zimne zadania**.</span><span class="sxs-lookup"><span data-stu-id="7f92d-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="7f92d-147">Muszą być jawnie uruchomione w celu rzeczywistego wykonania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="7f92d-148">Ma to pewne zalety, ponieważ umożliwia łączenie i sekwencję asynchronicznych zadań znacznie łatwiej niż w C#/VB.</span><span class="sxs-lookup"><span data-stu-id="7f92d-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C#/VB.</span></span>

## <a name="combining-asynchronous-computations"></a><span data-ttu-id="7f92d-149">Łączenie asynchronicznych obliczeń</span><span class="sxs-lookup"><span data-stu-id="7f92d-149">Combining asynchronous computations</span></span>

<span data-ttu-id="7f92d-150">Oto przykład, który kompiluje się na poprzednim, przez połączenie obliczeń:</span><span class="sxs-lookup"><span data-stu-id="7f92d-150">Here is an example that builds upon the previous one by combining computations:</span></span>

```fsharp
open System
open System.IO

let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Parallel
    |> Async.Ignore
    |> Async.RunSynchronously

    0
```

<span data-ttu-id="7f92d-151">Jak widać, funkcja `main` ma wiele większej liczby wywołań.</span><span class="sxs-lookup"><span data-stu-id="7f92d-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="7f92d-152">Koncepcyjnie wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7f92d-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="7f92d-153">Przekształć argumenty wiersza polecenia na `Async<unit>` obliczeń z `Array.map`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="7f92d-154">Utwórz `Async<'T[]>`, które zaplanuje i uruchamia równolegle obliczenia `printTotalFileBytes` podczas jego uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="7f92d-155">Utwórz `Async<unit>`, które będą wykonywać obliczenia równoległe, i zignoruj jego wynik.</span><span class="sxs-lookup"><span data-stu-id="7f92d-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="7f92d-156">Jawnie Uruchom ostatnie obliczenie z `Async.RunSynchronously` i blokuj do momentu jego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="7f92d-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="7f92d-157">Po uruchomieniu tego programu `printTotalFileBytes` działa równolegle dla każdego argumentu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f92d-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="7f92d-158">Ponieważ asynchroniczne obliczenia są wykonywane niezależnie od przepływu programu, nie ma kolejności, w której drukują informacje i kończą wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="7f92d-159">Obliczenia będą wykonywane równolegle, ale ich kolejność wykonywania nie jest gwarantowana.</span><span class="sxs-lookup"><span data-stu-id="7f92d-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequencing-asynchronous-computations"></a><span data-ttu-id="7f92d-160">Asynchroniczne obliczenia sekwencjonowania</span><span class="sxs-lookup"><span data-stu-id="7f92d-160">Sequencing asynchronous computations</span></span>

<span data-ttu-id="7f92d-161">Ponieważ `Async<'T>` to specyfikacja pracy, a nie zadania już uruchomionego, można łatwo wykonywać bardziej intricatee przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="7f92d-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="7f92d-162">Oto przykład, który służy do sekwencjonowania zestawu asynchronicznych obliczeń, tak aby były wykonywane jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="7f92d-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

```fsharp
let printTotalFileBytes path =
    async {
        let! bytes = File.ReadAllBytesAsync(path) |> Async.AwaitTask
        let fileName = Path.GetFileName(path)
        printfn "File %s has %d bytes" fileName bytes.Length
    }

[<EntryPoint>]
let main argv =
    argv
    |> Array.map printTotalFileBytes
    |> Async.Sequential
    |> Async.Ignore
    |> Async.RunSynchronously
    |> ignore
```

<span data-ttu-id="7f92d-163">Spowoduje to zaplanowanie `printTotalFileBytes` wykonywania w kolejności elementów `argv` zamiast planowania ich równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="7f92d-164">Ponieważ następny element nie zostanie zaplanowany do momentu zakończenia ostatniego obliczenia, obliczenia zostaną uporządkowane w taki sposób, że ich wykonanie nie nakłada się na siebie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="7f92d-165">Ważne funkcje modułu asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="7f92d-165">Important Async module functions</span></span>

<span data-ttu-id="7f92d-166">Gdy piszesz kod asynchroniczny F# , zwykle współdziała z platformą, która obsługuje planowanie obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7f92d-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="7f92d-167">Nie jest to jednak zawsze przypadek, dlatego warto poznać różne funkcje uruchamiania w celu zaplanowania pracy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="7f92d-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="7f92d-168">Ponieważ F# asynchroniczne obliczenia są _specyfikacją_ pracy, a nie reprezentacją już wykonywanej pracy, muszą być jawnie uruchomione przy użyciu funkcji początkowej.</span><span class="sxs-lookup"><span data-stu-id="7f92d-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="7f92d-169">Istnieje wiele [funkcji uruchamiania asynchronicznego](https://msdn.microsoft.com/library/ee370232.aspx) , które są przydatne w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="7f92d-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="7f92d-170">W poniższej sekcji opisano niektóre typowe funkcje uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="7f92d-171">Async. StartChild —</span><span class="sxs-lookup"><span data-stu-id="7f92d-171">Async.StartChild</span></span>

<span data-ttu-id="7f92d-172">Uruchamia obliczenie elementu podrzędnego w ramach obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="7f92d-173">Umożliwia to współbieżne wykonywanie wielu asynchronicznych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7f92d-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="7f92d-174">Podrzędne obliczenie udostępnia token anulowania z obliczeniami nadrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="7f92d-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="7f92d-175">Jeśli Obliczanie nadrzędne zostanie anulowane, obliczenia podrzędne również zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="7f92d-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="7f92d-176">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-176">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="7f92d-177">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-177">When to use:</span></span>

- <span data-ttu-id="7f92d-178">Jeśli chcesz wykonać wiele asynchronicznych obliczeń jednocześnie, a nie jeden na raz, ale nie zaplanowano ich równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="7f92d-179">Gdy chcesz powiązać okres istnienia obliczeń podrzędnych z tym, że jest to obliczenie nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f92d-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="7f92d-180">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-180">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-181">Uruchamianie wielu obliczeń przy użyciu `Async.StartChild` nie jest takie samo jak planowanie ich równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="7f92d-182">Jeśli chcesz zaplanować obliczenia równolegle, użyj `Async.Parallel`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="7f92d-183">Anulowanie obliczenia nadrzędnego spowoduje anulowanie wszystkich rozpoczętych obliczeń podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="7f92d-184">Async. StartImmediate —</span><span class="sxs-lookup"><span data-stu-id="7f92d-184">Async.StartImmediate</span></span>

<span data-ttu-id="7f92d-185">Uruchamia asynchroniczne obliczenie, począwszy od razu od bieżącego wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="7f92d-186">Jest to przydatne, jeśli trzeba zaktualizować coś w wątku wywołującym podczas obliczania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="7f92d-187">Na przykład jeśli asynchroniczne obliczenie musi zaktualizować interfejs użytkownika (na przykład zaktualizować pasek postępu), należy użyć `Async.StartImmediate`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="7f92d-188">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="7f92d-189">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-189">When to use:</span></span>

- <span data-ttu-id="7f92d-190">Gdy trzeba zaktualizować coś w wątku wywołującym w środku obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="7f92d-191">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-191">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-192">Kod w asynchronicznym obliczaniu zostanie uruchomiony niezależnie od wątku, w którym ma zostać zaplanowana.</span><span class="sxs-lookup"><span data-stu-id="7f92d-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="7f92d-193">Może to być problematyczne, jeśli ten wątek jest w sposób niezależny, na przykład wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7f92d-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="7f92d-194">W takich przypadkach `Async.StartImmediate` prawdopodobnie nieodpowiednie do użycia.</span><span class="sxs-lookup"><span data-stu-id="7f92d-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="7f92d-195">Async. Startastask —</span><span class="sxs-lookup"><span data-stu-id="7f92d-195">Async.StartAsTask</span></span>

<span data-ttu-id="7f92d-196">Wykonuje obliczenia w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="7f92d-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="7f92d-197">Zwraca <xref:System.Threading.Tasks.Task%601>, która zostanie zakończona w odpowiadającym stanie po zakończeniu obliczeń (tworzy wynik, zgłasza wyjątek lub jest anulowany).</span><span class="sxs-lookup"><span data-stu-id="7f92d-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="7f92d-198">Jeśli nie podano tokenu anulowania, zostanie użyty domyślny token anulowania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="7f92d-199">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="7f92d-200">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-200">When to use:</span></span>

- <span data-ttu-id="7f92d-201">Gdy musisz wywołać interfejs API platformy .NET, który oczekuje <xref:System.Threading.Tasks.Task%601> do reprezentowania wyniku asynchronicznego obliczenia.</span><span class="sxs-lookup"><span data-stu-id="7f92d-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="7f92d-202">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-202">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-203">To wywołanie spowoduje przydzielenie dodatkowego obiektu `Task`, co może zwiększyć obciążenie, jeśli jest używane często.</span><span class="sxs-lookup"><span data-stu-id="7f92d-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="7f92d-204">Async. Parallel</span><span class="sxs-lookup"><span data-stu-id="7f92d-204">Async.Parallel</span></span>

<span data-ttu-id="7f92d-205">Planuje sekwencję asynchronicznych obliczeń, które mają być wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="7f92d-206">Stopień równoległości można opcjonalnie dostrajać/ograniczyć, określając parametr `maxDegreesOfParallelism`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="7f92d-207">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="7f92d-208">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-208">When to use it:</span></span>

- <span data-ttu-id="7f92d-209">Jeśli konieczne jest uruchomienie zestawu obliczeń w tym samym czasie i nie ma on zależności od ich kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="7f92d-210">Jeśli nie są wymagane wyniki z obliczeń zaplanowanych równolegle, dopóki nie zostaną ukończone.</span><span class="sxs-lookup"><span data-stu-id="7f92d-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="7f92d-211">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-211">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-212">Można uzyskać dostęp tylko do wyników tablicy wartości po zakończeniu wszystkich obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7f92d-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="7f92d-213">Obliczenia będą wykonywane niezależnie od tego, że zaplanowano.</span><span class="sxs-lookup"><span data-stu-id="7f92d-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="7f92d-214">Oznacza to, że nie można polegać na ich kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="7f92d-215">Async. sekwencyjny</span><span class="sxs-lookup"><span data-stu-id="7f92d-215">Async.Sequential</span></span>

<span data-ttu-id="7f92d-216">Planuje sekwencję asynchronicznych obliczeń do wykonania w kolejności, w jakiej zostały przesłane.</span><span class="sxs-lookup"><span data-stu-id="7f92d-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="7f92d-217">Pierwsze obliczenie zostanie wykonane, następnie następne i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="7f92d-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="7f92d-218">Żadne obliczenia nie będą wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="7f92d-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="7f92d-219">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="7f92d-220">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-220">When to use it:</span></span>

- <span data-ttu-id="7f92d-221">Jeśli konieczne jest wykonanie wielu obliczeń w kolejności.</span><span class="sxs-lookup"><span data-stu-id="7f92d-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="7f92d-222">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-222">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-223">Można uzyskać dostęp tylko do wyników tablicy wartości po zakończeniu wszystkich obliczeń.</span><span class="sxs-lookup"><span data-stu-id="7f92d-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="7f92d-224">Obliczenia będą wykonywane w kolejności, w jakiej są przesyłane do tej funkcji, co może oznaczać, że upłynie więcej czasu przed zwróceniem wyników.</span><span class="sxs-lookup"><span data-stu-id="7f92d-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="7f92d-225">Async. Awaittask —</span><span class="sxs-lookup"><span data-stu-id="7f92d-225">Async.AwaitTask</span></span>

<span data-ttu-id="7f92d-226">Zwraca asynchroniczne obliczenie, które czeka na zakończenie danego <xref:System.Threading.Tasks.Task%601> i zwraca jego wynik jako `Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="7f92d-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="7f92d-227">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="7f92d-228">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-228">When to use:</span></span>

- <span data-ttu-id="7f92d-229">Gdy korzystasz z interfejsu API platformy .NET, który zwraca <xref:System.Threading.Tasks.Task%601> w ramach F# obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="7f92d-230">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-230">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-231">Wyjątki są opakowane w <xref:System.AggregateException> zgodnie z Konwencją biblioteki równoległej zadania i różnią się od sposobu F# , w jaki asynchroniczne są wyjątki na ogół.</span><span class="sxs-lookup"><span data-stu-id="7f92d-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="7f92d-232">Async. catch</span><span class="sxs-lookup"><span data-stu-id="7f92d-232">Async.Catch</span></span>

<span data-ttu-id="7f92d-233">Tworzy asynchroniczne obliczenie, które wykonuje daną `Async<'T>`, zwracając `Async<Choice<'T, exn>>`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="7f92d-234">W przypadku pomyślnego zapełnienia `Async<'T>` zostanie zwrócona `Choice1Of2` z wartością wynikową.</span><span class="sxs-lookup"><span data-stu-id="7f92d-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="7f92d-235">Jeśli przed zakończeniem zostanie zgłoszony wyjątek, zostanie zwrócony `Choice2of2` z podniesionym wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7f92d-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="7f92d-236">Jeśli jest używany w przypadku obliczeń asynchronicznych, które są tworzone w wielu obliczeniach, a jedno z tych obliczeń zgłasza wyjątek, obliczenia obejmujące obejmie zostaną całkowicie zatrzymane.</span><span class="sxs-lookup"><span data-stu-id="7f92d-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="7f92d-237">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="7f92d-238">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-238">When to use:</span></span>

- <span data-ttu-id="7f92d-239">Gdy wykonujesz asynchroniczne zadanie, które może zakończyć się niepowodzeniem z wyjątkiem i chcesz obsłużyć ten wyjątek w obiekcie wywołującym.</span><span class="sxs-lookup"><span data-stu-id="7f92d-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="7f92d-240">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-240">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-241">W przypadku korzystania z połączonych lub sekwencyjnych obliczeń asynchronicznych Obliczanie obejmujące obliczenia zostanie całkowicie zatrzymane, jeśli jedno z jego "wewnętrznego" obliczeń zgłosi wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7f92d-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="7f92d-242">Async. Ignore</span><span class="sxs-lookup"><span data-stu-id="7f92d-242">Async.Ignore</span></span>

<span data-ttu-id="7f92d-243">Tworzy asynchroniczne obliczenie, które uruchamia dane obliczenie i ignoruje wynik.</span><span class="sxs-lookup"><span data-stu-id="7f92d-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="7f92d-244">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="7f92d-245">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-245">When to use:</span></span>

- <span data-ttu-id="7f92d-246">W przypadku obliczeń asynchronicznych, których wynik nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="7f92d-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="7f92d-247">Jest to analogiczne do kodu `ignore` dla kodu nieasynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="7f92d-248">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-248">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-249">Jeśli musisz użyć tego przykładu, ponieważ chcesz używać `Async.Start` lub innej funkcji wymagającej `Async<unit>`, należy rozważyć, czy odrzucanie wyniku nie jest możliwe.</span><span class="sxs-lookup"><span data-stu-id="7f92d-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="7f92d-250">Odrzucanie wyników tylko w celu dopasowania do podpisu typu nie powinno być ogólnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="7f92d-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="7f92d-251">Async. metody RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="7f92d-251">Async.RunSynchronously</span></span>

<span data-ttu-id="7f92d-252">Uruchamia asynchroniczne obliczenie i czeka na wynik wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="7f92d-253">To wywołanie blokuje.</span><span class="sxs-lookup"><span data-stu-id="7f92d-253">This call is blocking.</span></span>

<span data-ttu-id="7f92d-254">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="7f92d-255">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-255">When to use it:</span></span>

- <span data-ttu-id="7f92d-256">Jeśli potrzebujesz tego, użyj go tylko raz w aplikacji — w punkcie wejścia dla pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="7f92d-257">Gdy nie masz opieki nad wydajnością i chcesz wykonać zestaw innych operacji asynchronicznych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="7f92d-258">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-258">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-259">Wywołanie `Async.RunSynchronously` blokuje wątek wywołujący do momentu zakończenia wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="7f92d-260">Async. Start</span><span class="sxs-lookup"><span data-stu-id="7f92d-260">Async.Start</span></span>

<span data-ttu-id="7f92d-261">Uruchamia asynchroniczne obliczenie w puli wątków, która zwraca `unit`.</span><span class="sxs-lookup"><span data-stu-id="7f92d-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="7f92d-262">Nie czeka na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="7f92d-262">Doesn't wait for its result.</span></span> <span data-ttu-id="7f92d-263">Zagnieżdżone obliczenia rozpoczęte dla `Async.Start` są uruchamiane całkowicie niezależnie od obliczeń nadrzędnych, które je wywołały.</span><span class="sxs-lookup"><span data-stu-id="7f92d-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="7f92d-264">Ich okres istnienia nie jest powiązany z żadnym z obliczeń nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="7f92d-265">Jeśli Obliczanie nadrzędne zostało anulowane, nie są anulowane żadne obliczenia podrzędne.</span><span class="sxs-lookup"><span data-stu-id="7f92d-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="7f92d-266">Podpis:</span><span class="sxs-lookup"><span data-stu-id="7f92d-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="7f92d-267">Używaj tylko wtedy, gdy:</span><span class="sxs-lookup"><span data-stu-id="7f92d-267">Use only when:</span></span>

- <span data-ttu-id="7f92d-268">Istnieje asynchroniczne obliczenie, które nie zwraca wyniku i/lub wymaga przetwarzania jednego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="7f92d-269">Nie musisz wiedzieć, kiedy kończy się Obliczanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="7f92d-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="7f92d-270">Nie musisz określać wątku, w którym jest wykonywane asynchroniczne obliczenie.</span><span class="sxs-lookup"><span data-stu-id="7f92d-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="7f92d-271">Nie trzeba znać ani zgłosić wyjątków wynikających z zadania.</span><span class="sxs-lookup"><span data-stu-id="7f92d-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="7f92d-272">Co należy obserwować:</span><span class="sxs-lookup"><span data-stu-id="7f92d-272">What to watch out for:</span></span>

- <span data-ttu-id="7f92d-273">Wyjątki wywoływane przez obliczenia rozpoczęte z `Async.Start` nie są propagowane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="7f92d-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="7f92d-274">Stos wywołań zostanie całkowicie odłożony.</span><span class="sxs-lookup"><span data-stu-id="7f92d-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="7f92d-275">Wszelkie efekty pracy (takie jak wywołanie `printfn`) rozpoczęte z `Async.Start` nie spowoduje wystąpienia efektu w głównym wątku wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="7f92d-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperating-with-net"></a><span data-ttu-id="7f92d-276">Współdziałanie z platformą .NET</span><span class="sxs-lookup"><span data-stu-id="7f92d-276">Interoperating with .NET</span></span>

<span data-ttu-id="7f92d-277">Być może pracujesz z biblioteką lub C# bazą kodu .NET, która używa asynchronicznego [/oczekującego](../../../standard/async.md)programowania w stylu.</span><span class="sxs-lookup"><span data-stu-id="7f92d-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="7f92d-278">Ze C# względu na to, że większość bibliotek .NET używa typów <xref:System.Threading.Tasks.Task%601> i <xref:System.Threading.Tasks.Task> jako ich rdzeń podstawowy, a nie `Async<'T>`, należy przekroczyć granicę między tymi dwoma podejściami do asynchroniczności.</span><span class="sxs-lookup"><span data-stu-id="7f92d-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="7f92d-279">Jak korzystać z asynchronicznej platformy .NET i `Task<T>`</span><span class="sxs-lookup"><span data-stu-id="7f92d-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="7f92d-280">Praca z bibliotekami asynchronicznymi .NET i bazami kodu, które używają <xref:System.Threading.Tasks.Task%601> (czyli obliczeń asynchronicznych, które mają zwracane wartości) jest prosta i ma wbudowaną F#obsługę.</span><span class="sxs-lookup"><span data-stu-id="7f92d-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="7f92d-281">Za pomocą funkcji `Async.AwaitTask` można oczekiwać obliczeń asynchronicznych platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="7f92d-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="7f92d-282">Za pomocą funkcji `Async.StartAsTask` można przekazać asynchroniczne obliczenie do obiektu wywołującego platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="7f92d-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="7f92d-283">Jak korzystać z asynchronicznej platformy .NET i `Task`</span><span class="sxs-lookup"><span data-stu-id="7f92d-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="7f92d-284">Aby można było korzystać z interfejsów API, które używają <xref:System.Threading.Tasks.Task> (czyli obliczeń asynchronicznych platformy .NET, które nie zwracają wartości), może być konieczne dodanie dodatkowej funkcji, która spowoduje przekonwertowanie `Async<'T>` na <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="7f92d-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="7f92d-285">Istnieje już `Async.AwaitTask`, które akceptuje <xref:System.Threading.Tasks.Task> jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="7f92d-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="7f92d-286">Za pomocą tej i wcześniej zdefiniowanej funkcji `startTaskFromAsyncUnit` można rozpoczynać i czekać <xref:System.Threading.Tasks.Task> typów z obliczeń F# asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7f92d-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multithreading"></a><span data-ttu-id="7f92d-287">Relacja do wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="7f92d-287">Relationship to multithreading</span></span>

<span data-ttu-id="7f92d-288">Chociaż wątki są wymienione w tym artykule, istnieją dwie ważne kwestie, które należy zapamiętać:</span><span class="sxs-lookup"><span data-stu-id="7f92d-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="7f92d-289">Nie ma koligacji między asynchronicznym obliczaniem a wątkiem, chyba że jest on jawnie uruchamiany w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="7f92d-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="7f92d-290">Programowanie asynchroniczne w F# programie nie jest abstrakcją dla wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="7f92d-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="7f92d-291">Na przykład obliczenia mogą być uruchamiane w wątku wywołującego, w zależności od rodzaju pracy.</span><span class="sxs-lookup"><span data-stu-id="7f92d-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="7f92d-292">Obliczenia mogą również "przeskoczyć" między wątkami, co pociąga za sobą niewielką ilość czasu, aby wykonywać przydatne działania w okresie "oczekiwanie" (na przykład podczas przesyłania połączenia sieciowego).</span><span class="sxs-lookup"><span data-stu-id="7f92d-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="7f92d-293">Chociaż F# program zapewnia pewne możliwości uruchamiania obliczeń asynchronicznych w bieżącym wątku (lub jawnie nie w bieżącym wątku), asynchroniczności zazwyczaj nie jest skojarzony z określoną strategią wątkowości.</span><span class="sxs-lookup"><span data-stu-id="7f92d-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f92d-294">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f92d-294">See also</span></span>

- [<span data-ttu-id="7f92d-295">F# Asynchroniczny model programowania</span><span class="sxs-lookup"><span data-stu-id="7f92d-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="7f92d-296">Przewodnik F# asynchroniczny aparatu Jet. com</span><span class="sxs-lookup"><span data-stu-id="7f92d-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="7f92d-297">F#dla zabawy i asynchronicznego Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="7f92d-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="7f92d-298">Asynchroniczny C# w F#i: asynchroniczny pytania dotyczące usługi wC#</span><span class="sxs-lookup"><span data-stu-id="7f92d-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
