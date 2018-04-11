---
title: 'Programowanie asynchroniczne w języku F #'
description: 'Dowiedz się, jak F # — programowanie asynchroniczne odbywa się za pomocą modelu programowania poziom języka, który jest łatwy w użyciu i fizyczne dla języka.'
keywords: .NET, .NET Core
author: cartermp
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9196bfc-b8a8-4d33-8b53-0dcbd58a69d8
ms.openlocfilehash: c3fde46e804b7acac78d3ce5454a3c6f806e24e7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="async-programming-in-f"></a><span data-ttu-id="f7686-104">Programowanie asynchroniczne w języku F #</span><span class="sxs-lookup"><span data-stu-id="f7686-104">Async Programming in F#</span></span> #

> [!NOTE]
> <span data-ttu-id="f7686-105">Niektóre nieścisłości zostały odnalezione w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="f7686-105">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="f7686-106">Jego jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="f7686-106">It is being rewritten.</span></span>  <span data-ttu-id="f7686-107">Zobacz [&#666; problem](https://github.com/dotnet/docs/issues/666) Aby dowiedzieć się więcej o zmianach.</span><span class="sxs-lookup"><span data-stu-id="f7686-107">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="f7686-108">Async — Programowanie w języku F # można osiągnąć za pomocą modelu programowania poziom języka zaprojektowaną do łatwy w użyciu i fizyczne dla języka.</span><span class="sxs-lookup"><span data-stu-id="f7686-108">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="f7686-109">Jest podstawową async programowania w języku F # `Async<'T>`, reprezentacja prac, które mogą być wyzwalane do uruchamiania w tle, gdzie `'T` albo typ zwracany jest za pomocą specjalnych `return` — słowo kluczowe lub `unit` Jeśli nie ma przepływu pracy async wynik do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="f7686-109">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="f7686-110">Kluczowe pojęcia zrozumienie jest typ wyrażenia asynchronicznej `Async<'T>`, która jest jedynie _specyfikacji_ pracy można wykonać w kontekście asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="f7686-110">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="f7686-111">Nie została wykonana, dopóki nie zostanie jawnie uruchomiony jeden z wyjścia funkcji (takich jak `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="f7686-111">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="f7686-112">Jest to inny sposób planowania wykonywania pracy, kończy się ono jest bardzo proste, w praktyce.</span><span class="sxs-lookup"><span data-stu-id="f7686-112">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="f7686-113">Na przykład załóżmy, że w chcesz pobrać kod HTML z dotnetfoundation.org bez blokowania głównego wątku.</span><span class="sxs-lookup"><span data-stu-id="f7686-113">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="f7686-114">Można to wykonać je następująco:</span><span class="sxs-lookup"><span data-stu-id="f7686-114">You can accomplish it like this:</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()

        // Execution of fetchHtmlAsync won't continue until the result
        // of AsyncDownloadString is bound.
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously
printfn "%s" html
```

<span data-ttu-id="f7686-115">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="f7686-115">And that’s it!</span></span> <span data-ttu-id="f7686-116">Oprócz stosowania `async`, `let!`, i `return`, jest to normalne właśnie kodzie języka F #.</span><span class="sxs-lookup"><span data-stu-id="f7686-116">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="f7686-117">Istnieje kilka konstrukcji syntaktycznych, które warto zauważyć:</span><span class="sxs-lookup"><span data-stu-id="f7686-117">There are a few syntactical constructs which are worth noting:</span></span>

*   <span data-ttu-id="f7686-118">`let!` wiąże wynik wyrażenia async (który jest uruchamiany w kontekście innym).</span><span class="sxs-lookup"><span data-stu-id="f7686-118">`let!` binds the result of an async expression (which runs on another context).</span></span>
*   <span data-ttu-id="f7686-119">`use!` działa podobnie do `let!`, ale usuwa jego powiązanych zasobów, gdy przechodzi ona poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="f7686-119">`use!` works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   <span data-ttu-id="f7686-120">`do!` zostanie await async przepływu pracy, która nie zwraca żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="f7686-120">`do!` will await an async workflow which doesn’t return anything.</span></span>
*   <span data-ttu-id="f7686-121">`return` po prostu zwraca wynik wyrażenia asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f7686-121">`return` simply returns a result from an async expression.</span></span>
*   <span data-ttu-id="f7686-122">`return!` wykonuje innego async przepływu pracy i zwraca jego wartości zwracanej w związku z tym.</span><span class="sxs-lookup"><span data-stu-id="f7686-122">`return!` executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="f7686-123">Ponadto normalne `let`, `use`, i `do` słowa kluczowe można używać razem w wersjach asynchronicznych tak samo, jak w normalnym funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7686-123">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="f7686-124">Jak uruchomić kod asynchronicznych w języku F #</span><span class="sxs-lookup"><span data-stu-id="f7686-124">How to start Async Code in F#</span></span> #

<span data-ttu-id="f7686-125">Jak wspomniano wcześniej, kod asynchronicznej jest specyfikację pracy w innym kontekście, który musi być jawnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f7686-125">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="f7686-126">Poniżej przedstawiono dwa podstawowe sposoby w tym celu:</span><span class="sxs-lookup"><span data-stu-id="f7686-126">Here are two primary ways to accomplish this:</span></span>

1.  <span data-ttu-id="f7686-127">`Async.RunSynchronously` uruchomi async przepływu pracy w innym wątku i poczekać na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="f7686-127">`Async.RunSynchronously` will start an async workflow on another thread and await its result.</span></span>

```fsharp
open System
open System.Net

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

 // Execution will pause until fetchHtmlAsync finishes
 let html = "https://dotnetfoundation.org" |> fetchHtmlAsync |> Async.RunSynchronously

 // you actually have the result from fetchHtmlAsync now!
 printfn "%s" html
 ```

2.  <span data-ttu-id="f7686-128">`Async.Start` Uruchamianie przepływu pracy asynchronicznych w innym wątku i będzie **nie** poczekać na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="f7686-128">`Async.Start` will start an async workflow on another thread, and will **not** await its result.</span></span>

```fsharp
open System
open System.Net
  
let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

// Execution will continue after calling this!
Async.Start(workflow)

printfn "%s" "uploadDataAsync is running in the background..."
 ```

<span data-ttu-id="f7686-129">Istnieją inne sposoby uruchamiania przepływ async dostępne dla bardziej konkretnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f7686-129">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="f7686-130">Są one szczegółowe [w odwołaniu Async](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="f7686-130">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="f7686-131">Uwaga na wątków</span><span class="sxs-lookup"><span data-stu-id="f7686-131">A Note on Threads</span></span>

<span data-ttu-id="f7686-132">Wyrażenie "w innym wątku" został podany powyżej, ale należy pamiętać, że **nie oznacza to, że asynchroniczne przepływy pracy są fasad dla wielowątkowości**.</span><span class="sxs-lookup"><span data-stu-id="f7686-132">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="f7686-133">Przepływ pracy faktycznie "przejdzie" między wątkami finansowania ich zewnętrznego dla małej ilości czasu na wykonanie pracy przydatne.</span><span class="sxs-lookup"><span data-stu-id="f7686-133">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="f7686-134">Gdy przepływ pracy async skutecznie "oczekuje" (np. oczekiwanie na połączenie sieci zwrócić coś), którymkolwiek wątku, który został on finansowania zewnętrznego w tym czasie zostanie zwolniona do pracy przydatne Przejdź innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f7686-134">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="f7686-135">Umożliwia asynchroniczne przepływy pracy, aby korzystać z systemu, które są uruchamiane w możliwie najbardziej efektywny sposób i ich dokonuje szczególnie duży dla dużej liczby operacji We/Wy scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="f7686-135">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="f7686-136">Jak dodać równoległości do kodu Async</span><span class="sxs-lookup"><span data-stu-id="f7686-136">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="f7686-137">Czasami użytkownik może muszą do wykonywania wielu zadań asynchronicznych równolegle, zbieranie wyników, a zinterpretowane w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="f7686-137">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> <span data-ttu-id="f7686-138">`Async.Parallel` Można to zrobić bez konieczności korzystania z biblioteki równoległych zadań, która wymagałoby konieczności wymuszone `Task<'T>` i `Async<'T>` typów.</span><span class="sxs-lookup"><span data-stu-id="f7686-138">`Async.Parallel` allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="f7686-139">Poniższy przykład użyje `Async.Parallel` pobierania kodu HTML z czterech popularnych witryn równolegle, poczekaj na zakończenie tych zadań, a następnie wydrukuj kodu HTML, który został pobrany.</span><span class="sxs-lookup"><span data-stu-id="f7686-139">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

```fsharp
open System
open System.Net

let urlList = 
    [ "https://www.microsoft.com"
      "https://www.google.com"
      "https://www.amazon.com"
      "https://www.facebook.com" ]

let fetchHtmlAsync url = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        let! html = webClient.AsyncDownloadString(uri)
        return html
    }

let getHtmlList urls =
    urls
    |> Seq.map fetchHtmlAsync   // Build an Async<'T> for each site
    |> Async.Parallel           // Returns an Async<'T []>
    |> Async.RunSynchronously   // Wait for the result of the parallel work

let htmlList = getHtmlList urlList

// We now have the downloaded HTML for each site!
for html in htmlList do
    printfn "%s" html
```

## <a name="important-info-and-advice"></a><span data-ttu-id="f7686-140">Ważne informacje i wskazówki</span><span class="sxs-lookup"><span data-stu-id="f7686-140">Important Info and Advice</span></span>

*   <span data-ttu-id="f7686-141">Dołącz "Async" na końcu wszystkie funkcje, których będziesz korzystać</span><span class="sxs-lookup"><span data-stu-id="f7686-141">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="f7686-142">Jest to konwencji nazewnictwa, jego ułatwienia jak odnajdywania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="f7686-142">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="f7686-143">Szczególnie w przypadku, jeśli dostępne są wersje synchroniczne i asynchroniczne tej samej procedury, jest dobrze jest jawnie określać, które jest asynchroniczne przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="f7686-143">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="f7686-144">Nasłuchiwanie w kompilatorze!</span><span class="sxs-lookup"><span data-stu-id="f7686-144">Listen to the compiler!</span></span>

 <span data-ttu-id="f7686-145">F # przez kompilator jest bardzo rygorystyczny, uniemożliwiając niemal czymś troubling jak uruchomić kod "async" synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="f7686-145">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="f7686-146">W przypadku napotkać ostrzeżenie, który jest znak kod nie będzie wykonanie jak uważasz, że będzie on.</span><span class="sxs-lookup"><span data-stu-id="f7686-146">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="f7686-147">Jeśli kompilator mogą wysyłać wszystkiego, kodzie najprawdopodobniej będzie wykonywał zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f7686-147">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="f7686-148">Dla programisty # / VB. C wyszukiwania w F #</span><span class="sxs-lookup"><span data-stu-id="f7686-148">For the C#/VB Programmer Looking Into F#</span></span> #

<span data-ttu-id="f7686-149">W tej sekcji założono znasz modelu asynchronicznych w języku C# / VB.</span><span class="sxs-lookup"><span data-stu-id="f7686-149">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="f7686-150">Jeśli nie, [Async programowania w języku C#](../../../csharp/async.md) stanowi punkt wyjścia.</span><span class="sxs-lookup"><span data-stu-id="f7686-150">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="f7686-151">Brak główną różnicą między C# / VB. async i F # async modelu.</span><span class="sxs-lookup"><span data-stu-id="f7686-151">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="f7686-152">Jeśli wywołasz funkcję, która zwraca `Task` lub `Task<'T>`, to zadanie zostało już uruchomione wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f7686-152">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="f7686-153">Zwracane dojście reprezentuje zadanie asynchroniczne już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="f7686-153">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="f7686-154">Z kolei jeśli wywołasz z funkcji asynchronicznych w języku F #, `Async<'a>` zwrócił reprezentuje zadania, które będą **wygenerowany** w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="f7686-154">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="f7686-155">Opis tego modelu jest wydajne, ponieważ umożliwia zadań asynchronicznych w języku F # można je połączyć ze sobą łatwiej, wykonywane warunkowo i uruchomić z bardziej precyzyjną ziarna formantu.</span><span class="sxs-lookup"><span data-stu-id="f7686-155">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="f7686-156">Istnieje kilka podobieństwa i różnice warto zauważyć.</span><span class="sxs-lookup"><span data-stu-id="f7686-156">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="f7686-157">Podobieństwa</span><span class="sxs-lookup"><span data-stu-id="f7686-157">Similarities</span></span>

*   <span data-ttu-id="f7686-158">`let!`, `use!`, i `do!` są odpowiednikiem `await` podczas wywoływania metody asynchroniczne zadanie z poziomu `async{ }` bloku.</span><span class="sxs-lookup"><span data-stu-id="f7686-158">`let!`, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="f7686-159">Trzy kluczowe można używać tylko w ramach `async { }` bloku, podobnie jak `await` można wywołać tylko wewnątrz `async` metody.</span><span class="sxs-lookup"><span data-stu-id="f7686-159">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="f7686-160">Krótko mówiąc `let!` dotyczy umożliwia przechwytywanie i użyć wyniku, `use!` dotyczy coś którego zasoby powinny uzyskać czyszczone po jest on używany, ale sam i `do!` jest dla, gdy chcesz czekać na przepływu pracy async o Brak wartości zwracanej, aby zakończyć Przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="f7686-160">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="f7686-161">Język F # obsługuje równoległość danych w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="f7686-161">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="f7686-162">Mimo że działa ona bardzo inaczej `Async.Parallel` odpowiada `Task.WhenAll` dla scenariusza pożądane wyniki zestaw zadań asynchronicznych po ukończeniu wszystkie.</span><span class="sxs-lookup"><span data-stu-id="f7686-162">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="f7686-163">Różnice</span><span class="sxs-lookup"><span data-stu-id="f7686-163">Differences</span></span>

*   <span data-ttu-id="f7686-164">Zagnieżdżone `let!` nie jest dozwolone, w odróżnieniu od zagnieżdżone `await`</span><span class="sxs-lookup"><span data-stu-id="f7686-164">Nested `let!` is not allowed, unlike nested `await`</span></span>

 <span data-ttu-id="f7686-165">W odróżnieniu od `await`, które mogą być zagnieżdżane przez czas nieokreślony, `let!` nie i musi mieć wynik powiązany przed jego użyciem wewnątrz innego `let!`, `do!`, lub `use!`.</span><span class="sxs-lookup"><span data-stu-id="f7686-165">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="f7686-166">Obsługa anulowania jest łatwiejsze w języku F # niż w języku C# / VB.</span><span class="sxs-lookup"><span data-stu-id="f7686-166">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="f7686-167">Obsługa anulowania połowie zadań, za pośrednictwem jej wykonanie w C# /VB wymaga sprawdzanie `IsCancellationRequested` właściwość lub wywołanie `ThrowIfCancellationRequested()` na `CancellationToken` obiekt, który jest przekazywany do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="f7686-167">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="f7686-168">Z kolei więcej naturalnie możliwe są F # Asynchroniczne przepływy pracy.</span><span class="sxs-lookup"><span data-stu-id="f7686-168">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="f7686-169">Anulowanie jest prosty proces trzech etapów.</span><span class="sxs-lookup"><span data-stu-id="f7686-169">Cancellation is a simple three-step process.</span></span>

1.  <span data-ttu-id="f7686-170">Utwórz nową `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="f7686-170">Create a new `CancellationTokenSource`.</span></span>
2.  <span data-ttu-id="f7686-171">Przekaż go do wyjścia funkcji.</span><span class="sxs-lookup"><span data-stu-id="f7686-171">Pass it into a starting function.</span></span>
3.  <span data-ttu-id="f7686-172">Wywołanie `Cancel` w tokenie.</span><span class="sxs-lookup"><span data-stu-id="f7686-172">Call `Cancel` on the token.</span></span>

<span data-ttu-id="f7686-173">Przykład:</span><span class="sxs-lookup"><span data-stu-id="f7686-173">Example:</span></span>

```fsharp
open System
open System.Net

let uploadDataAsync url data = 
    async {
        let uri = Uri(url)
        use webClient = new WebClient()
        webClient.UploadStringAsync(uri, data)
    }

let workflow = uploadDataAsync "https://url-to-upload-to.com" "hello, world!"

let token = new CancellationTokenSource()
Async.Start (workflow, token)

// Immediately cancel uploadDataAsync after it's been started.
token.Cancel()
```

<span data-ttu-id="f7686-174">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="f7686-174">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="f7686-175">Dodatkowe zasoby:</span><span class="sxs-lookup"><span data-stu-id="f7686-175">Further resources:</span></span>

*   [<span data-ttu-id="f7686-176">Asynchroniczne przepływy pracy, w witrynie MSDN</span><span class="sxs-lookup"><span data-stu-id="f7686-176">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="f7686-177">Asynchroniczne sekwencji dla F #</span><span class="sxs-lookup"><span data-stu-id="f7686-177">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="f7686-178">Narzędzia F # danych protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="f7686-178">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)
