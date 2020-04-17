---
title: Programowanie asynchroniowe
description: Dowiedz się, jak F# zapewnia czystą obsługę asynchrony na podstawie modelu programowania na poziomie języka pochodzących z podstawowych koncepcji programowania funkcjonalnego.
ms.date: 12/17/2018
ms.openlocfilehash: 9b2e3057c126d84474c21fde653da5bbee32938a
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81608039"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="317c2-103">Programowanie asynchroniowe w F\#</span><span class="sxs-lookup"><span data-stu-id="317c2-103">Async programming in F\#</span></span>

<span data-ttu-id="317c2-104">Programowanie asynchroniczne jest mechanizmem, który jest niezbędny do nowoczesnych zastosowań z różnych powodów.</span><span class="sxs-lookup"><span data-stu-id="317c2-104">Asynchronous programming is a mechanism that is essential to modern applications for diverse reasons.</span></span> <span data-ttu-id="317c2-105">Istnieją dwa podstawowe przypadki użycia, które napotka większość deweloperów:</span><span class="sxs-lookup"><span data-stu-id="317c2-105">There are two primary use cases that most developers will encounter:</span></span>

- <span data-ttu-id="317c2-106">Przedstawianie procesu serwera, który może obsługiwać znaczną liczbę równoczesnych żądań przychodzących, przy jednoczesnym zminimalizowaniu zasobów systemowych zajętych podczas przetwarzania żądań oczekuje na dane wejściowe z systemów lub usług zewnętrznych dla tego procesu</span><span class="sxs-lookup"><span data-stu-id="317c2-106">Presenting a server process that can service a significant number of concurrent incoming requests, while minimizing the system resources occupied while request processing awaits inputs from systems or services external to that process</span></span>
- <span data-ttu-id="317c2-107">Obsługa elastycznego interfejsu użytkownika lub wątku głównego przy jednoczesnym postępie pracy w tle</span><span class="sxs-lookup"><span data-stu-id="317c2-107">Maintaining a responsive UI or main thread while concurrently progressing background work</span></span>

<span data-ttu-id="317c2-108">Chociaż praca w tle często wiąże się z wykorzystaniem wielu wątków, ważne jest, aby rozważyć pojęcia asynchrony i wielowątkowe oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="317c2-108">Although background work often does involve the utilization of multiple threads, it's important to consider the concepts of asynchrony and multi-threading separately.</span></span> <span data-ttu-id="317c2-109">W rzeczywistości są to odrębne obawy, a jedno nie oznacza drugiego.</span><span class="sxs-lookup"><span data-stu-id="317c2-109">In fact, they are separate concerns, and one does not imply the other.</span></span> <span data-ttu-id="317c2-110">Co znajduje się w tym artykule opisano to bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="317c2-110">What follows in this article describes this in more detail.</span></span>

## <a name="asynchrony-defined"></a><span data-ttu-id="317c2-111">Asynchrony zdefiniowane</span><span class="sxs-lookup"><span data-stu-id="317c2-111">Asynchrony defined</span></span>

<span data-ttu-id="317c2-112">Poprzedni punkt - że asynchrony jest niezależna od wykorzystania wielu wątków - warto wyjaśnić nieco dalej.</span><span class="sxs-lookup"><span data-stu-id="317c2-112">The previous point - that asynchrony is independent of the utilization of multiple threads - is worth explaining a bit further.</span></span> <span data-ttu-id="317c2-113">Istnieją trzy pojęcia, które są czasami powiązane, ale ściśle niezależne od siebie:</span><span class="sxs-lookup"><span data-stu-id="317c2-113">There are three concepts that are sometimes related, but strictly independent of one another:</span></span>

- <span data-ttu-id="317c2-114">Współbieżność; gdy wiele obliczeń wykonuje się w nakładających się okresach.</span><span class="sxs-lookup"><span data-stu-id="317c2-114">Concurrency; when multiple computations execute in overlapping time periods.</span></span>
- <span data-ttu-id="317c2-115">Równoległość; gdy wiele obliczeń lub kilka części pojedynczych obliczeń działa dokładnie w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="317c2-115">Parallelism; when multiple computations or several parts of a single computation run at exactly the same time.</span></span>
- <span data-ttu-id="317c2-116">Asynchrony; gdy jedno lub więcej obliczeń może być wykonywanych oddzielnie od głównego przepływu programu.</span><span class="sxs-lookup"><span data-stu-id="317c2-116">Asynchrony; when one or more computations can execute separately from the main program flow.</span></span>

<span data-ttu-id="317c2-117">Wszystkie trzy są pojęciami ortogonalnymi, ale można je łatwo skondensować, zwłaszcza gdy są używane razem.</span><span class="sxs-lookup"><span data-stu-id="317c2-117">All three are orthogonal concepts, but can be easily conflated, especially when they are used together.</span></span> <span data-ttu-id="317c2-118">Na przykład może być konieczne wykonanie wielu obliczeń asynchronicznych równolegle.</span><span class="sxs-lookup"><span data-stu-id="317c2-118">For example, you may need to execute multiple asynchronous computations in parallel.</span></span> <span data-ttu-id="317c2-119">Nie oznacza to, że równoległość czy asynchrony implikuje się nawzajem.</span><span class="sxs-lookup"><span data-stu-id="317c2-119">This does not mean that parallelism or asynchrony imply one another.</span></span>

<span data-ttu-id="317c2-120">Jeśli wziąć pod uwagę etymologię słowa "asynchroniczne", istnieją dwa elementy zaangażowane:</span><span class="sxs-lookup"><span data-stu-id="317c2-120">If you consider the etymology of the word "asynchronous", there are two pieces involved:</span></span>

- <span data-ttu-id="317c2-121">"a", czyli "nie".</span><span class="sxs-lookup"><span data-stu-id="317c2-121">"a", meaning "not".</span></span>
- <span data-ttu-id="317c2-122">"synchroniczne", co oznacza "w tym samym czasie".</span><span class="sxs-lookup"><span data-stu-id="317c2-122">"synchronous", meaning "at the same time".</span></span>

<span data-ttu-id="317c2-123">Po połączeniu tych dwóch terminów zobaczysz, że "asynchroniczne" oznacza "nie w tym samym czasie".</span><span class="sxs-lookup"><span data-stu-id="317c2-123">When you put these two terms together, you'll see that "asynchronous" means "not at the same time".</span></span> <span data-ttu-id="317c2-124">Gotowe.</span><span class="sxs-lookup"><span data-stu-id="317c2-124">That's it!</span></span> <span data-ttu-id="317c2-125">Nie ma żadnych konsekwencji współbieżności lub równoległości w tej definicji.</span><span class="sxs-lookup"><span data-stu-id="317c2-125">There is no implication of concurrency or parallelism in this definition.</span></span> <span data-ttu-id="317c2-126">Dotyczy to również w praktyce.</span><span class="sxs-lookup"><span data-stu-id="317c2-126">This is also true in practice.</span></span>

<span data-ttu-id="317c2-127">W praktyce obliczenia asynchroniczne w języku F# są zaplanowane do wykonania niezależnie od głównego przepływu programu.</span><span class="sxs-lookup"><span data-stu-id="317c2-127">In practical terms, asynchronous computations in F# are scheduled to execute independently of the main program flow.</span></span> <span data-ttu-id="317c2-128">Nie oznacza to współbieżności lub równoległości, ani nie oznacza, że obliczenia zawsze dzieje się w tle.</span><span class="sxs-lookup"><span data-stu-id="317c2-128">This doesn't imply concurrency or parallelism, nor does it imply that a computation always happens in the background.</span></span> <span data-ttu-id="317c2-129">W rzeczywistości obliczenia asynchroniczne można nawet wykonać synchronicznie, w zależności od charakteru obliczeń i środowiska, w jakim obliczenia są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="317c2-129">In fact, asynchronous computations can even execute synchronously, depending on the nature of the computation and the environment the computation is executing in.</span></span>

<span data-ttu-id="317c2-130">Głównym wynos powinieneś mieć to, że obliczenia asynchroniczne są niezależne od głównego przepływu programu.</span><span class="sxs-lookup"><span data-stu-id="317c2-130">The main takeaway you should have is that asynchronous computations are independent of the main program flow.</span></span> <span data-ttu-id="317c2-131">Chociaż istnieje kilka gwarancji dotyczących tego, kiedy lub jak wykonuje obliczenia asynchroniczne, istnieją pewne podejścia do ich organizowania i planowania.</span><span class="sxs-lookup"><span data-stu-id="317c2-131">Although there are few guarantees about when or how an asynchronous computation executes, there are some approaches to orchestrating and scheduling them.</span></span> <span data-ttu-id="317c2-132">W dalszej części tego artykułu eksploruje podstawowe pojęcia dla asynchrony F# i jak używać typów, funkcji i wyrażeń wbudowanych w F#.</span><span class="sxs-lookup"><span data-stu-id="317c2-132">The rest of this article explores core concepts for F# asynchrony and how to use the types, functions, and expressions built into F#.</span></span>

## <a name="core-concepts"></a><span data-ttu-id="317c2-133">Kluczowe pojęcia</span><span class="sxs-lookup"><span data-stu-id="317c2-133">Core concepts</span></span>

<span data-ttu-id="317c2-134">W języku F# programowanie asynchroniczne jest wyśrodkowane wokół trzech podstawowych pojęć:</span><span class="sxs-lookup"><span data-stu-id="317c2-134">In F#, asynchronous programming is centered around three core concepts:</span></span>

- <span data-ttu-id="317c2-135">Typ, `Async<'T>` który reprezentuje obliczeń asynchronicznych komponowania.</span><span class="sxs-lookup"><span data-stu-id="317c2-135">The `Async<'T>` type, which represents a composable asynchronous computation.</span></span>
- <span data-ttu-id="317c2-136">Funkcje modułu, `Async` które umożliwiają planowanie pracy asynchronicznej, komponowanie obliczeń asynchronicznych i przekształcanie wyników asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-136">The `Async` module functions, which let you schedule asynchronous work, compose asynchronous computations, and transform asynchronous results.</span></span>
- <span data-ttu-id="317c2-137">Wyrażenie `async { }` [obliczeń](../../language-reference/computation-expressions.md), które zapewnia wygodną składnię do tworzenia i kontrolowania obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-137">The `async { }` [computation expression](../../language-reference/computation-expressions.md), which provides a convenient syntax for building and controlling asynchronous computations.</span></span>

<span data-ttu-id="317c2-138">Te trzy pojęcia można zobaczyć w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="317c2-138">You can see these three concepts in the following example:</span></span>

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

<span data-ttu-id="317c2-139">W przykładzie `printTotalFileBytes` funkcja jest `string -> Async<unit>`typu .</span><span class="sxs-lookup"><span data-stu-id="317c2-139">In the example, the `printTotalFileBytes` function is of type `string -> Async<unit>`.</span></span> <span data-ttu-id="317c2-140">Wywołanie funkcji faktycznie nie wykonuje obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-140">Calling the function does not actually execute the asynchronous computation.</span></span> <span data-ttu-id="317c2-141">Zamiast tego `Async<unit>` zwraca, który działa jako *specyfikacja* pracy, która ma wykonać asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="317c2-141">Instead, it returns an `Async<unit>` that acts as a *specification* of the work that is to execute asynchronously.</span></span> <span data-ttu-id="317c2-142">Wywołuje `Async.AwaitTask` w swoim ciele, który konwertuje wynik <xref:System.IO.File.ReadAllBytesAsync%2A> do odpowiedniego typu.</span><span class="sxs-lookup"><span data-stu-id="317c2-142">It calls `Async.AwaitTask` in its body, which converts the result of <xref:System.IO.File.ReadAllBytesAsync%2A> to an appropriate type.</span></span>

<span data-ttu-id="317c2-143">Inną ważną linią jest `Async.RunSynchronously`wezwanie do .</span><span class="sxs-lookup"><span data-stu-id="317c2-143">Another important line is the call to `Async.RunSynchronously`.</span></span> <span data-ttu-id="317c2-144">Jest to jedna z funkcji uruchamiania modułu Async, które należy wywołać, jeśli chcesz faktycznie wykonać obliczenia asynchroniczne F#.</span><span class="sxs-lookup"><span data-stu-id="317c2-144">This is one of the Async module starting functions that you'll need to call if you want to actually execute an F# asynchronous computation.</span></span>

<span data-ttu-id="317c2-145">Jest to zasadnicza różnica w stylu `async` programowania języka C#/Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="317c2-145">This is a fundamental difference with the C#/Visual Basic style of `async` programming.</span></span> <span data-ttu-id="317c2-146">W języku F# obliczenia asynchroniczne można traktować jako **zimne zadania**.</span><span class="sxs-lookup"><span data-stu-id="317c2-146">In F#, asynchronous computations can be thought of as **Cold tasks**.</span></span> <span data-ttu-id="317c2-147">Muszą one być jawnie rozpoczęte do faktycznie wykonać.</span><span class="sxs-lookup"><span data-stu-id="317c2-147">They must be explicitly started to actually execute.</span></span> <span data-ttu-id="317c2-148">Ma to pewne zalety, ponieważ pozwala na łączenie i sekwencji pracy asynchronicznej znacznie łatwiej niż w języku C# lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="317c2-148">This has some advantages, as it allows you to combine and sequence asynchronous work much more easily than in C# or Visual Basic.</span></span>

## <a name="combine-asynchronous-computations"></a><span data-ttu-id="317c2-149">Łączenie obliczeń asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="317c2-149">Combine asynchronous computations</span></span>

<span data-ttu-id="317c2-150">Oto przykład, który opiera się na poprzednim, łącząc obliczenia:</span><span class="sxs-lookup"><span data-stu-id="317c2-150">Here is an example that builds upon the previous one by combining computations:</span></span>

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

<span data-ttu-id="317c2-151">Jak widać, `main` funkcja ma sporo więcej połączeń wykonanych.</span><span class="sxs-lookup"><span data-stu-id="317c2-151">As you can see, the `main` function has quite a few more calls made.</span></span> <span data-ttu-id="317c2-152">Koncepcyjnie wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="317c2-152">Conceptually, it does the following:</span></span>

1. <span data-ttu-id="317c2-153">Przekształć `Async<unit>` argumenty wiersza polecenia w obliczenia za pomocą pliku `Array.map`.</span><span class="sxs-lookup"><span data-stu-id="317c2-153">Transform the command-line arguments into `Async<unit>` computations with `Array.map`.</span></span>
2. <span data-ttu-id="317c2-154">`Async<'T[]>` Utwórz, który planuje `printTotalFileBytes` i uruchamia obliczenia równolegle podczas pracy.</span><span class="sxs-lookup"><span data-stu-id="317c2-154">Create an `Async<'T[]>` that schedules and runs the `printTotalFileBytes` computations in parallel when it runs.</span></span>
3. <span data-ttu-id="317c2-155">`Async<unit>` Utwórz, który uruchomi obliczenia równoległe i zignoruje jego wynik.</span><span class="sxs-lookup"><span data-stu-id="317c2-155">Create an `Async<unit>` that will run the parallel computation and ignore its result.</span></span>
4. <span data-ttu-id="317c2-156">Jawnie uruchomić ostatnie obliczenia `Async.RunSynchronously` z i bloku, dopóki nie zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="317c2-156">Explicitly run the last computation with `Async.RunSynchronously` and block until it is completes.</span></span>

<span data-ttu-id="317c2-157">Po uruchomieniu tego `printTotalFileBytes` programu działa równolegle dla każdego argumentu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="317c2-157">When this program runs, `printTotalFileBytes` runs in parallel for each command-line argument.</span></span> <span data-ttu-id="317c2-158">Ponieważ obliczenia asynchroniczne są wykonywane niezależnie od przepływu programu, nie ma kolejności drukowania informacji i zakończenia wykonywania.</span><span class="sxs-lookup"><span data-stu-id="317c2-158">Because asynchronous computations execute independently of program flow, there is no order in which they print their information and finish executing.</span></span> <span data-ttu-id="317c2-159">Obliczenia będą zaplanowane równolegle, ale ich kolejność wykonywania nie jest gwarantowana.</span><span class="sxs-lookup"><span data-stu-id="317c2-159">The computations will be scheduled in parallel, but their order of execution is not guaranteed.</span></span>

## <a name="sequence-asynchronous-computations"></a><span data-ttu-id="317c2-160">Sekwencja obliczeń asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="317c2-160">Sequence asynchronous computations</span></span>

<span data-ttu-id="317c2-161">Ponieważ `Async<'T>` jest to specyfikacja pracy, a nie już uruchomione zadanie, można łatwo wykonywać bardziej skomplikowane przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="317c2-161">Because `Async<'T>` is a specification of work rather than an already-running task, you can perform more intricate transformations easily.</span></span> <span data-ttu-id="317c2-162">Oto przykład, który sekwencjonuje zestaw obliczeń Asynchronii, aby wykonać jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="317c2-162">Here is an example that sequences a set of Async computations so they execute one after another.</span></span>

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

<span data-ttu-id="317c2-163">Spowoduje to `printTotalFileBytes` zaplanowanie wykonania w kolejności `argv` elementów, a nie ich równoległego planowania.</span><span class="sxs-lookup"><span data-stu-id="317c2-163">This will schedule `printTotalFileBytes` to execute in the order of the elements of `argv` rather than scheduling them in parallel.</span></span> <span data-ttu-id="317c2-164">Ponieważ następny element nie zostanie zaplanowany dopiero po zakończeniu wykonywania ostatniego obliczenia, obliczenia są sekwencjonowane w taki sposób, że nie ma nakładania się w ich wykonaniu.</span><span class="sxs-lookup"><span data-stu-id="317c2-164">Because the next item will not be scheduled until after the last computation has finished executing, the computations are sequenced such that there is no overlap in their execution.</span></span>

## <a name="important-async-module-functions"></a><span data-ttu-id="317c2-165">Ważne funkcje modułu Asynchronii</span><span class="sxs-lookup"><span data-stu-id="317c2-165">Important Async module functions</span></span>

<span data-ttu-id="317c2-166">Podczas pisania kodu asynchroniiowego w języku F# zwykle będziesz wchodzić w interakcje z platformą, która obsługuje planowanie obliczeń dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="317c2-166">When you write async code in F# you'll usually interact with a framework that handles scheduling of computations for you.</span></span> <span data-ttu-id="317c2-167">Jednak nie zawsze tak jest, więc dobrze jest nauczyć się różnych funkcji początkowych, aby zaplanować pracę asynchronizacę.</span><span class="sxs-lookup"><span data-stu-id="317c2-167">However, this is not always the case, so it is good to learn the various starting functions to schedule asynchronous work.</span></span>

<span data-ttu-id="317c2-168">Ponieważ obliczenia asynchroniczne F# są _specyfikacją_ pracy, a nie reprezentacją pracy, która jest już wykonywana, muszą być jawnie uruchomione z funkcją początkową.</span><span class="sxs-lookup"><span data-stu-id="317c2-168">Because F# asynchronous computations are a _specification_ of work rather than a representation of work that is already executing, they must be explicitly started with a starting function.</span></span> <span data-ttu-id="317c2-169">Istnieje wiele [funkcji uruchamiania Async,](https://msdn.microsoft.com/library/ee370232.aspx) które są pomocne w różnych kontekstach.</span><span class="sxs-lookup"><span data-stu-id="317c2-169">There are many [Async starting functions](https://msdn.microsoft.com/library/ee370232.aspx) that are helpful in different contexts.</span></span> <span data-ttu-id="317c2-170">W poniższej sekcji opisano niektóre z bardziej typowych funkcji początkowych.</span><span class="sxs-lookup"><span data-stu-id="317c2-170">The following section describes some of the more common starting functions.</span></span>

### <a name="asyncstartchild"></a><span data-ttu-id="317c2-171">Async.StartChild</span><span class="sxs-lookup"><span data-stu-id="317c2-171">Async.StartChild</span></span>

<span data-ttu-id="317c2-172">Rozpoczyna obliczanie podrzędne w obliczeniach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-172">Starts a child computation within an asynchronous computation.</span></span> <span data-ttu-id="317c2-173">Dzięki temu wiele obliczeń asynchronicznych mają być wykonywane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="317c2-173">This allows multiple asynchronous computations to be executed concurrently.</span></span> <span data-ttu-id="317c2-174">Obliczenia podrzędne współumisuje token anulowania z obliczeń nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="317c2-174">The child computation shares a cancellation token with the parent computation.</span></span> <span data-ttu-id="317c2-175">Jeśli obliczenia nadrzędne są anulowane, obliczenia podrzędne są również anulowane.</span><span class="sxs-lookup"><span data-stu-id="317c2-175">If the parent computation is canceled, the child computation is also canceled.</span></span>

<span data-ttu-id="317c2-176">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-176">Signature:</span></span>

```fsharp
computation: Async<'T> * timeout: ?int -> Async<Async<'T>>
```

<span data-ttu-id="317c2-177">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-177">When to use:</span></span>

- <span data-ttu-id="317c2-178">Jeśli chcesz wykonać wiele obliczeń asynchronicznych jednocześnie, a nie jeden na raz, ale nie mają ich zaplanowane równolegle.</span><span class="sxs-lookup"><span data-stu-id="317c2-178">When you want to execute multiple asynchronous computations concurrently rather than one at a time, but not have them scheduled in parallel.</span></span>
- <span data-ttu-id="317c2-179">Jeśli chcesz powiązać okres istnienia obliczeń podrzędnych z okresem istnienia obliczeń nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="317c2-179">When you wish to tie the lifetime of a child computation to that of a parent computation.</span></span>

<span data-ttu-id="317c2-180">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-180">What to watch out for:</span></span>

- <span data-ttu-id="317c2-181">Uruchamianie wielu `Async.StartChild` obliczeń z nie jest taka sama jak planowanie ich równolegle.</span><span class="sxs-lookup"><span data-stu-id="317c2-181">Starting multiple computations with `Async.StartChild` isn't the same as scheduling them in parallel.</span></span> <span data-ttu-id="317c2-182">Jeśli chcesz zaplanować obliczenia równolegle, `Async.Parallel`użyj .</span><span class="sxs-lookup"><span data-stu-id="317c2-182">If you wish to schedule computations in parallel, use `Async.Parallel`.</span></span>
- <span data-ttu-id="317c2-183">Anulowanie obliczeń nadrzędnych spowoduje anulowanie wszystkich obliczeń podrzędnych, które uruchomił.</span><span class="sxs-lookup"><span data-stu-id="317c2-183">Canceling a parent computation will trigger cancellation of all child computations it started.</span></span>

### <a name="asyncstartimmediate"></a><span data-ttu-id="317c2-184">Async.StartImmediate</span><span class="sxs-lookup"><span data-stu-id="317c2-184">Async.StartImmediate</span></span>

<span data-ttu-id="317c2-185">Uruchamia obliczenia asynchroniczne, uruchamia się natychmiast w bieżącym wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="317c2-185">Runs an asynchronous computation, starting immediately on the current operating system thread.</span></span> <span data-ttu-id="317c2-186">Jest to przydatne, jeśli trzeba zaktualizować coś w wątku wywołującym podczas obliczeń.</span><span class="sxs-lookup"><span data-stu-id="317c2-186">This is helpful if you need to update something on the calling thread during the computation.</span></span> <span data-ttu-id="317c2-187">Na przykład jeśli obliczenia asynchroniczne muszą zaktualizować interfejs użytkownika (na przykład `Async.StartImmediate` aktualizowanie paska postępu), należy użyć.</span><span class="sxs-lookup"><span data-stu-id="317c2-187">For example, if an asynchronous computation must update a UI (such as updating a progress bar), then `Async.StartImmediate` should be used.</span></span>

<span data-ttu-id="317c2-188">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-188">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="317c2-189">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-189">When to use:</span></span>

- <span data-ttu-id="317c2-190">Gdy trzeba zaktualizować coś na wątku wywołującego w środku obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-190">When you need to update something on the calling thread in the middle of an asynchronous computation.</span></span>

<span data-ttu-id="317c2-191">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-191">What to watch out for:</span></span>

- <span data-ttu-id="317c2-192">Kod w obliczeniach asynchronicznych będzie działać na dowolnym wątku jeden dzieje się zaplanowane na.</span><span class="sxs-lookup"><span data-stu-id="317c2-192">Code in the asynchronous computation will run on whatever thread one happens to be scheduled on.</span></span> <span data-ttu-id="317c2-193">Może to być problematyczne, jeśli ten wątek jest w jakiś sposób wrażliwe, takie jak wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="317c2-193">This can be problematic if that thread is in some way sensitive, such as a UI thread.</span></span> <span data-ttu-id="317c2-194">W takich `Async.StartImmediate` przypadkach, jest prawdopodobne, niewłaściwe w użyciu.</span><span class="sxs-lookup"><span data-stu-id="317c2-194">In such cases, `Async.StartImmediate` is likely inappropriate to use.</span></span>

### <a name="asyncstartastask"></a><span data-ttu-id="317c2-195">Async.StartAsTask</span><span class="sxs-lookup"><span data-stu-id="317c2-195">Async.StartAsTask</span></span>

<span data-ttu-id="317c2-196">Wykonuje obliczenia w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="317c2-196">Executes a computation in the thread pool.</span></span> <span data-ttu-id="317c2-197"><xref:System.Threading.Tasks.Task%601> Zwraca, który zostanie ukończony w odpowiednim stanie po zakończeniu obliczeń (daje wynik, zgłasza wyjątek lub zostanie anulowany).</span><span class="sxs-lookup"><span data-stu-id="317c2-197">Returns a <xref:System.Threading.Tasks.Task%601> that will be completed on the corresponding state once the computation terminates (produces the result, throws exception, or gets canceled).</span></span> <span data-ttu-id="317c2-198">Jeśli nie podano tokenu anulowania, używany jest domyślny token anulowania.</span><span class="sxs-lookup"><span data-stu-id="317c2-198">If no cancellation token is provided, then the default cancellation token is used.</span></span>

<span data-ttu-id="317c2-199">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-199">Signature:</span></span>

```fsharp
computation: Async<'T> - taskCreationOptions: ?TaskCreationOptions - cancellationToken: ?CancellationToken -> Task<'T>
```

<span data-ttu-id="317c2-200">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-200">When to use:</span></span>

- <span data-ttu-id="317c2-201">Gdy trzeba wywołać interfejs API platformy .NET, który <xref:System.Threading.Tasks.Task%601> oczekuje, że reprezentuje wynik obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-201">When you need to call into a .NET API that expects a <xref:System.Threading.Tasks.Task%601> to represent the result of an asynchronous computation.</span></span>

<span data-ttu-id="317c2-202">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-202">What to watch out for:</span></span>

- <span data-ttu-id="317c2-203">To wywołanie przydzieli dodatkowy `Task` obiekt, który może zwiększyć obciążenie, jeśli jest często używany.</span><span class="sxs-lookup"><span data-stu-id="317c2-203">This call will allocate an additional `Task` object, which can increase overhead if it is used often.</span></span>

### <a name="asyncparallel"></a><span data-ttu-id="317c2-204">Async.Parallel (Async.Parallel)</span><span class="sxs-lookup"><span data-stu-id="317c2-204">Async.Parallel</span></span>

<span data-ttu-id="317c2-205">Planuje sekwencję obliczeń asynchronicznych, które mają być wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="317c2-205">Schedules a sequence of asynchronous computations to be executed in parallel.</span></span> <span data-ttu-id="317c2-206">Stopień równoległości można opcjonalnie dostroić/ograniczyć, `maxDegreesOfParallelism` określając parametr.</span><span class="sxs-lookup"><span data-stu-id="317c2-206">The degree of parallelism can be optionally tuned/throttled by specifying the `maxDegreesOfParallelism` parameter.</span></span>

<span data-ttu-id="317c2-207">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-207">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> - ?maxDegreesOfParallelism: int -> Async<'T[]>
```

<span data-ttu-id="317c2-208">Kiedy go używać:</span><span class="sxs-lookup"><span data-stu-id="317c2-208">When to use it:</span></span>

- <span data-ttu-id="317c2-209">Jeśli musisz uruchomić zestaw obliczeń w tym samym czasie i nie mają polegania na ich kolejności wykonywania.</span><span class="sxs-lookup"><span data-stu-id="317c2-209">If you need to run a set of computations at the same time and have no reliance on their order of execution.</span></span>
- <span data-ttu-id="317c2-210">Jeśli nie potrzebujesz wyników z obliczeń zaplanowanych równolegle, dopóki nie zostaną ukończone.</span><span class="sxs-lookup"><span data-stu-id="317c2-210">If you don't require results from computations scheduled in parallel until they have all completed.</span></span>

<span data-ttu-id="317c2-211">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-211">What to watch out for:</span></span>

- <span data-ttu-id="317c2-212">Wynikową tablicę wartości można uzyskać tylko po zakończeniu wszystkich obliczeń.</span><span class="sxs-lookup"><span data-stu-id="317c2-212">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="317c2-213">Obliczenia będą uruchamiane, jednak w końcu są one coraz zaplanowane.</span><span class="sxs-lookup"><span data-stu-id="317c2-213">Computations will be run however they end up getting scheduled.</span></span> <span data-ttu-id="317c2-214">Oznacza to, że nie można polegać na ich kolejności ich wykonania.</span><span class="sxs-lookup"><span data-stu-id="317c2-214">This means you cannot rely on their order of their execution.</span></span>

### <a name="asyncsequential"></a><span data-ttu-id="317c2-215">Async.Sequential</span><span class="sxs-lookup"><span data-stu-id="317c2-215">Async.Sequential</span></span>

<span data-ttu-id="317c2-216">Planuje sekwencję obliczeń asynchronicznych do wykonania w kolejności, w jakiej są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="317c2-216">Schedules a sequence of asynchronous computations to be executed in the order that they are passed.</span></span> <span data-ttu-id="317c2-217">Pierwsze obliczenia zostaną wykonane, następnie następne i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="317c2-217">The first computation will be executed, then the next, and so on.</span></span> <span data-ttu-id="317c2-218">Żadne obliczenia nie będą wykonywane równolegle.</span><span class="sxs-lookup"><span data-stu-id="317c2-218">No computations will be executed in parallel.</span></span>

<span data-ttu-id="317c2-219">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-219">Signature:</span></span>

```fsharp
computations: seq<Async<'T>> -> Async<'T[]>
```

<span data-ttu-id="317c2-220">Kiedy go używać:</span><span class="sxs-lookup"><span data-stu-id="317c2-220">When to use it:</span></span>

- <span data-ttu-id="317c2-221">Jeśli musisz wykonać wiele obliczeń w kolejności.</span><span class="sxs-lookup"><span data-stu-id="317c2-221">If you need to execute multiple computations in order.</span></span>

<span data-ttu-id="317c2-222">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-222">What to watch out for:</span></span>

- <span data-ttu-id="317c2-223">Wynikową tablicę wartości można uzyskać tylko po zakończeniu wszystkich obliczeń.</span><span class="sxs-lookup"><span data-stu-id="317c2-223">You can only access the resulting array of values once all computations have finished.</span></span>
- <span data-ttu-id="317c2-224">Obliczenia będą uruchamiane w kolejności, w jakiej są przekazywane do tej funkcji, co może oznaczać, że zanim wyniki zostaną zwrócone, upłynie więcej czasu.</span><span class="sxs-lookup"><span data-stu-id="317c2-224">Computations will be run in the order that they are passed to this function, which can mean that more time will elapse before the results are returned.</span></span>

### <a name="asyncawaittask"></a><span data-ttu-id="317c2-225">Async.AwaitTask (Async.AwaitTask)</span><span class="sxs-lookup"><span data-stu-id="317c2-225">Async.AwaitTask</span></span>

<span data-ttu-id="317c2-226">Zwraca obliczenia asynchroniczne, które czekają <xref:System.Threading.Tasks.Task%601> na zakończenie danego i zwraca jego wynik jako`Async<'T>`</span><span class="sxs-lookup"><span data-stu-id="317c2-226">Returns an asynchronous computation that waits for the given <xref:System.Threading.Tasks.Task%601> to complete and returns its result as an `Async<'T>`</span></span>

<span data-ttu-id="317c2-227">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-227">Signature:</span></span>

```fsharp
task: Task<'T>  -> Async<'T>
```

<span data-ttu-id="317c2-228">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-228">When to use:</span></span>

- <span data-ttu-id="317c2-229">Podczas korzystania z interfejsu API platformy <xref:System.Threading.Tasks.Task%601> .NET, który zwraca w ramach F# obliczeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-229">When you are consuming a .NET API that returns a <xref:System.Threading.Tasks.Task%601> within an F# asynchronous computation.</span></span>

<span data-ttu-id="317c2-230">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-230">What to watch out for:</span></span>

- <span data-ttu-id="317c2-231">Wyjątki są <xref:System.AggregateException> zawijane w następujące konwencji biblioteki równoległej zadania i różni się to od sposobu F# async zazwyczaj powierzchnie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="317c2-231">Exceptions are wrapped in <xref:System.AggregateException> following the convention of the Task Parallel Library, and this is different from how F# async generally surfaces exceptions.</span></span>

### <a name="asynccatch"></a><span data-ttu-id="317c2-232">Async.Catch (Async.Catch)</span><span class="sxs-lookup"><span data-stu-id="317c2-232">Async.Catch</span></span>

<span data-ttu-id="317c2-233">Tworzy obliczenia asynchroniczne, które wykonuje `Async<'T>`dany `Async<Choice<'T, exn>>`, zwracając .</span><span class="sxs-lookup"><span data-stu-id="317c2-233">Creates an asynchronous computation that executes a given `Async<'T>`, returning an `Async<Choice<'T, exn>>`.</span></span> <span data-ttu-id="317c2-234">Jeśli podane `Async<'T>` zakończy się pomyślnie, a następnie `Choice1Of2` zwracany z wartością wynikową.</span><span class="sxs-lookup"><span data-stu-id="317c2-234">If the given `Async<'T>` completes successfully, then a `Choice1Of2` is returned with the resultant value.</span></span> <span data-ttu-id="317c2-235">Jeśli wyjątek zostanie zgłoszony przed jego `Choice2of2` zakończeniem, a następnie zwracany z zgłoszonym wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="317c2-235">If an exception is thrown before it completes, then a `Choice2of2` is returned with the raised exception.</span></span> <span data-ttu-id="317c2-236">Jeśli jest on używany w obliczeniach asynchronicznych, który sam składa się z wielu obliczeń, a jedno z tych obliczeń zgłasza wyjątek, obejmujące obliczeń zostanie całkowicie zatrzymany.</span><span class="sxs-lookup"><span data-stu-id="317c2-236">If it is used on an asynchronous computation that is itself composed of many computations, and one of those computations throws an exception, the encompassing computation will be stopped entirely.</span></span>

<span data-ttu-id="317c2-237">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-237">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<Choice<'T, exn>>
```

<span data-ttu-id="317c2-238">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-238">When to use:</span></span>

- <span data-ttu-id="317c2-239">Podczas wykonywania pracy asynchroniiowej, które mogą zakończyć się niepowodzeniem z wyjątkiem i chcesz obsłużyć ten wyjątek w wywołującym.</span><span class="sxs-lookup"><span data-stu-id="317c2-239">When you are performing asynchronous work that may fail with an exception and you want to handle that exception in the caller.</span></span>

<span data-ttu-id="317c2-240">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-240">What to watch out for:</span></span>

- <span data-ttu-id="317c2-241">W przypadku korzystania z połączonych lub sekwencjonowane obliczeń asynchronicznych, obejmujące obliczeń zostanie całkowicie zatrzymane, jeśli jeden z jego "wewnętrznych" obliczeń zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="317c2-241">When using combined or sequenced asynchronous computations, the encompassing computation will fully stop if one of its "internal" computations throws an exception.</span></span>

### <a name="asyncignore"></a><span data-ttu-id="317c2-242">Async.Ignore (Async.Ignore)</span><span class="sxs-lookup"><span data-stu-id="317c2-242">Async.Ignore</span></span>

<span data-ttu-id="317c2-243">Tworzy obliczenia asynchroniczne, który uruchamia danego obliczeń i ignoruje jego wynik.</span><span class="sxs-lookup"><span data-stu-id="317c2-243">Creates an asynchronous computation that runs the given computation and ignores its result.</span></span>

<span data-ttu-id="317c2-244">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-244">Signature:</span></span>

```fsharp
computation: Async<'T> -> Async<unit>
```

<span data-ttu-id="317c2-245">Kiedy stosować:</span><span class="sxs-lookup"><span data-stu-id="317c2-245">When to use:</span></span>

- <span data-ttu-id="317c2-246">Gdy masz obliczenia asynchroniczne, których wynik nie jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="317c2-246">When you have an asynchronous computation whose result is not needed.</span></span> <span data-ttu-id="317c2-247">Jest to analogiczne `ignore` do kodu dla kodu nieynchroniowego.</span><span class="sxs-lookup"><span data-stu-id="317c2-247">This is analogous to the `ignore` code for non-asynchronous code.</span></span>

<span data-ttu-id="317c2-248">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-248">What to watch out for:</span></span>

- <span data-ttu-id="317c2-249">Jeśli musisz użyć tego, ponieważ `Async.Start` chcesz użyć `Async<unit>`lub innej funkcji, która wymaga, należy rozważyć, czy odrzucenie wyniku jest w porządku.</span><span class="sxs-lookup"><span data-stu-id="317c2-249">If you must use this because you wish to use `Async.Start` or another function that requires `Async<unit>`, consider if discarding the result is okay to do.</span></span> <span data-ttu-id="317c2-250">Odrzucanie wyników tylko po to, aby dopasować podpis typu, nie powinno być zazwyczaj wykonywane.</span><span class="sxs-lookup"><span data-stu-id="317c2-250">Discarding results just to fit a type signature should not generally be done.</span></span>

### <a name="asyncrunsynchronously"></a><span data-ttu-id="317c2-251">Async.RunSynchronously</span><span class="sxs-lookup"><span data-stu-id="317c2-251">Async.RunSynchronously</span></span>

<span data-ttu-id="317c2-252">Uruchamia obliczenia asynchroniczne i oczekuje na jego wynik w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="317c2-252">Runs an asynchronous computation and awaits its result on the calling thread.</span></span> <span data-ttu-id="317c2-253">To wywołanie jest blokowanie.</span><span class="sxs-lookup"><span data-stu-id="317c2-253">This call is blocking.</span></span>

<span data-ttu-id="317c2-254">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-254">Signature:</span></span>

```fsharp
computation: Async<'T> - timeout: ?int - cancellationToken: ?CancellationToken -> 'T
```

<span data-ttu-id="317c2-255">Kiedy go używać:</span><span class="sxs-lookup"><span data-stu-id="317c2-255">When to use it:</span></span>

- <span data-ttu-id="317c2-256">Jeśli tego potrzebujesz, użyj go tylko raz w aplikacji — w punkcie wejścia dla pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="317c2-256">If you need it, use it only once in an application - at the entry point for an executable.</span></span>
- <span data-ttu-id="317c2-257">Gdy nie dbasz o wydajność i chcesz wykonać zestaw innych operacji asynchronicznych na raz.</span><span class="sxs-lookup"><span data-stu-id="317c2-257">When you don't care about performance and want to execute a set of other asynchronous operations at once.</span></span>

<span data-ttu-id="317c2-258">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-258">What to watch out for:</span></span>

- <span data-ttu-id="317c2-259">Wywołanie `Async.RunSynchronously` blokuje wątek wywołujący, dopóki wykonanie nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="317c2-259">Calling `Async.RunSynchronously` blocks the calling thread until the execution completes.</span></span>

### <a name="asyncstart"></a><span data-ttu-id="317c2-260">Async.Start</span><span class="sxs-lookup"><span data-stu-id="317c2-260">Async.Start</span></span>

<span data-ttu-id="317c2-261">Uruchamia obliczenia asynchroniczne w puli wątków, która zwraca `unit`.</span><span class="sxs-lookup"><span data-stu-id="317c2-261">Starts an asynchronous computation in the thread pool that returns `unit`.</span></span> <span data-ttu-id="317c2-262">Nie czeka na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="317c2-262">Doesn't wait for its result.</span></span> <span data-ttu-id="317c2-263">Obliczenia zagnieżdżone rozpoczęte `Async.Start` są uruchamiane całkowicie niezależnie od obliczeń nadrzędnych, które je nazwały.</span><span class="sxs-lookup"><span data-stu-id="317c2-263">Nested computations started with `Async.Start` are started completely independently of the parent computation that called them.</span></span> <span data-ttu-id="317c2-264">Ich żywotność nie jest związana z żadnymi obliczeniami nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="317c2-264">Their lifetime is not tied to any parent computation.</span></span> <span data-ttu-id="317c2-265">Jeśli obliczenia nadrzędne zostaną anulowane, żadne obliczenia podrzędne nie zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="317c2-265">If the parent computation is canceled, no child computations are cancelled.</span></span>

<span data-ttu-id="317c2-266">Podpis:</span><span class="sxs-lookup"><span data-stu-id="317c2-266">Signature:</span></span>

```fsharp
computation: Async<unit> - cancellationToken: ?CancellationToken -> unit
```

<span data-ttu-id="317c2-267">Stosować tylko wtedy, gdy:</span><span class="sxs-lookup"><span data-stu-id="317c2-267">Use only when:</span></span>

- <span data-ttu-id="317c2-268">Masz obliczenia asynchroniczne, które nie dają wynik i/lub wymagają przetwarzania jednego.</span><span class="sxs-lookup"><span data-stu-id="317c2-268">You have an asynchronous computation that doesn't yield a result and/or require processing of one.</span></span>
- <span data-ttu-id="317c2-269">Nie musisz wiedzieć, kiedy obliczenia asynchroniczne zakończyć.</span><span class="sxs-lookup"><span data-stu-id="317c2-269">You don't need to know when an asynchronous computation completes.</span></span>
- <span data-ttu-id="317c2-270">Nie obchodzi cię, który wątek jest uruchamiany na obliczeniach asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="317c2-270">You don't care which thread an asynchronous computation runs on.</span></span>
- <span data-ttu-id="317c2-271">Nie musisz być świadomy lub zgłaszać wyjątki wynikające z zadania.</span><span class="sxs-lookup"><span data-stu-id="317c2-271">You don't have any need to be aware of or report exceptions resulting from the task.</span></span>

<span data-ttu-id="317c2-272">Na co uważać:</span><span class="sxs-lookup"><span data-stu-id="317c2-272">What to watch out for:</span></span>

- <span data-ttu-id="317c2-273">Wyjątki wywoływane przez `Async.Start` obliczenia rozpoczęte z nie są propagowane do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="317c2-273">Exceptions raised by computations started with `Async.Start` aren't propagated to the caller.</span></span> <span data-ttu-id="317c2-274">Stos wywołań zostanie całkowicie rozwiany.</span><span class="sxs-lookup"><span data-stu-id="317c2-274">The call stack will be completely unwound.</span></span>
- <span data-ttu-id="317c2-275">Wszelkie prace efektowne `printfn`(takie `Async.Start` jak wywołanie) rozpoczęte z nie spowoduje efekt się na głównym wątku wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="317c2-275">Any effectful work (such as calling `printfn`) started with `Async.Start` won't cause the effect to happen on the main thread of a program's execution.</span></span>

## <a name="interoperate-with-net"></a><span data-ttu-id="317c2-276">Współdziałanie z .NET</span><span class="sxs-lookup"><span data-stu-id="317c2-276">Interoperate with .NET</span></span>

<span data-ttu-id="317c2-277">Być może pracujesz z biblioteką .NET lub bazą kodu Języka C#, która używa programowania asynchroniowego asynchroniiowego [asynchronii.](../../../standard/async.md)</span><span class="sxs-lookup"><span data-stu-id="317c2-277">You may be working with a .NET library or C# codebase that uses [async/await](../../../standard/async.md)-style asynchronous programming.</span></span> <span data-ttu-id="317c2-278">Ponieważ C# i większość bibliotek .NET <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task> używać i typów jako `Async<'T>`ich abstrakcje podstawowe, a nie , należy przekroczyć granicę między tymi dwoma podejściami do asynchrony.</span><span class="sxs-lookup"><span data-stu-id="317c2-278">Because C# and the majority of .NET libraries use the <xref:System.Threading.Tasks.Task%601> and <xref:System.Threading.Tasks.Task> types as their core abstractions rather than `Async<'T>`, you must cross a boundary between these two approaches to asynchrony.</span></span>

### <a name="how-to-work-with-net-async-and-taskt"></a><span data-ttu-id="317c2-279">Jak pracować z .NET async i`Task<T>`</span><span class="sxs-lookup"><span data-stu-id="317c2-279">How to work with .NET async and `Task<T>`</span></span>

<span data-ttu-id="317c2-280">Praca z bibliotekami asynchronizacyjnymi <xref:System.Threading.Tasks.Task%601> platformy .NET i bazami kodu, które używają (czyli obliczeń asynchronii, które mają zwracane wartości) jest prosta i ma wbudowaną obsługę z F#.</span><span class="sxs-lookup"><span data-stu-id="317c2-280">Working with .NET async libraries and codebases that use <xref:System.Threading.Tasks.Task%601> (that is, async computations that have return values) is straightforward and has built-in support with F#.</span></span>

<span data-ttu-id="317c2-281">Za pomocą `Async.AwaitTask` funkcji można oczekiwać na obliczenia asynchroniczne platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="317c2-281">You can use the `Async.AwaitTask` function to await a .NET asynchronous computation:</span></span>

```fsharp
let getValueFromLibrary param =
    async {
        let! value = DotNetLibrary.GetValueAsync param |> Async.AwaitTask
        return value
    }
```

<span data-ttu-id="317c2-282">Za pomocą `Async.StartAsTask` tej funkcji można przekazać obliczenia asynchroniczne do wywołującego .NET:</span><span class="sxs-lookup"><span data-stu-id="317c2-282">You can use the `Async.StartAsTask` function to pass an asynchronous computation to a .NET caller:</span></span>

```fsharp
let computationForCaller param =
    async {
        let! result = getAsyncResult param
        return result
    } |> Async.StartAsTask
```

### <a name="how-to-work-with-net-async-and-task"></a><span data-ttu-id="317c2-283">Jak pracować z .NET async i`Task`</span><span class="sxs-lookup"><span data-stu-id="317c2-283">How to work with .NET async and `Task`</span></span>

<span data-ttu-id="317c2-284">Aby pracować z interfejsami <xref:System.Threading.Tasks.Task> API, które używają (czyli .NET async obliczeń, które nie zwracają wartość), `Async<'T>` może <xref:System.Threading.Tasks.Task>być konieczne dodanie dodatkowej funkcji, która spowoduje konwersję na:</span><span class="sxs-lookup"><span data-stu-id="317c2-284">To work with APIs that use <xref:System.Threading.Tasks.Task> (that is, .NET async computations that do not return a value), you may need to add an additional function that will convert an `Async<'T>` to a <xref:System.Threading.Tasks.Task>:</span></span>

```fsharp
module Async =
    // Async<unit> -> Task
    let startTaskFromAsyncUnit (comp: Async<unit>) =
        Async.StartAsTask comp :> Task
```

<span data-ttu-id="317c2-285">Istnieje `Async.AwaitTask` już, że akceptuje <xref:System.Threading.Tasks.Task> jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="317c2-285">There is already an `Async.AwaitTask` that accepts a <xref:System.Threading.Tasks.Task> as input.</span></span> <span data-ttu-id="317c2-286">Za pomocą tej i `startTaskFromAsyncUnit` wcześniej zdefiniowanej funkcji <xref:System.Threading.Tasks.Task> można uruchamiać i czekać na typy z obliczeń asynchronowych języka F#.</span><span class="sxs-lookup"><span data-stu-id="317c2-286">With this and the previously defined `startTaskFromAsyncUnit` function, you can start and await <xref:System.Threading.Tasks.Task> types from an F# async computation.</span></span>

## <a name="relationship-to-multi-threading"></a><span data-ttu-id="317c2-287">Relacja z wieloma wątkami</span><span class="sxs-lookup"><span data-stu-id="317c2-287">Relationship to multi-threading</span></span>

<span data-ttu-id="317c2-288">Chociaż wątki jest wymieniony w tym artykule, istnieją dwie ważne rzeczy do zapamiętania:</span><span class="sxs-lookup"><span data-stu-id="317c2-288">Although threading is mentioned throughout this article, there are two important things to remember:</span></span>

1. <span data-ttu-id="317c2-289">Nie ma koligacji między obliczeniami asynchronizacyjnymi a wątkiem, chyba że jawnie rozpoczęto w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="317c2-289">There is no affinity between an asynchronous computation and a thread, unless explicitly started on the current thread.</span></span>
1. <span data-ttu-id="317c2-290">Programowanie asynchroniczne w języku F# nie jest abstrakcją dla wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="317c2-290">Asynchronous programming in F# is not an abstraction for multi-threading.</span></span>

<span data-ttu-id="317c2-291">Na przykład obliczenia mogą faktycznie działać na wątku wywołującego, w zależności od charakteru pracy.</span><span class="sxs-lookup"><span data-stu-id="317c2-291">For example, a computation may actually run on its caller's thread, depending on the nature of the work.</span></span> <span data-ttu-id="317c2-292">Obliczenia mogą również "przeskakiwać" między wątkami, pożyczając je przez niewielką ilość czasu, aby wykonać użyteczną pracę między okresami "oczekiwania" (na przykład podczas przesyłania połączenia sieciowego).</span><span class="sxs-lookup"><span data-stu-id="317c2-292">A computation could also "jump" between threads, borrowing them for a small amount of time to do useful work in between periods of "waiting" (such as when a network call is in transit).</span></span>

<span data-ttu-id="317c2-293">Chociaż F# zapewnia pewne możliwości, aby rozpocząć obliczenia asynchroniczne w bieżącym wątku (lub jawnie nie w bieżącym wątku), asynchrony ogólnie nie jest skojarzony z określonej strategii wątków.</span><span class="sxs-lookup"><span data-stu-id="317c2-293">Although F# provides some abilities to start an asynchronous computation on the current thread (or explicitly not on the current thread), asynchrony generally is not associated with a particular threading strategy.</span></span>

## <a name="see-also"></a><span data-ttu-id="317c2-294">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="317c2-294">See also</span></span>

- [<span data-ttu-id="317c2-295">Model programowania asynchroniiowego F#</span><span class="sxs-lookup"><span data-stu-id="317c2-295">The F# Asynchronous Programming Model</span></span>](https://www.microsoft.com/research/publication/the-f-asynchronous-programming-model)
- [<span data-ttu-id="317c2-296">Jet.com's F# Przewodnik Async</span><span class="sxs-lookup"><span data-stu-id="317c2-296">Jet.com's F# Async Guide</span></span>](https://medium.com/jettech/f-async-guide-eb3c8a2d180a)
- [<span data-ttu-id="317c2-297">F# dla zabawy i zysku Asynchroniczne Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="317c2-297">F# for fun and profit's Asynchronous Programming guide</span></span>](https://fsharpforfunandprofit.com/posts/concurrency-async-and-parallel/)
- [<span data-ttu-id="317c2-298">Async w języku C# i F#: Asynchroniczne gotchas w C #</span><span class="sxs-lookup"><span data-stu-id="317c2-298">Async in C# and F#: Asynchronous gotchas in C#</span></span>](http://tomasp.net/blog/csharp-async-gotchas.aspx/)
