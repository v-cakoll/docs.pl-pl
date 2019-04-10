---
title: Programowanie asynchroniczne
description: Dowiedz się, jak F# programowanie async odbywa się za pośrednictwem modelu programowania poziomu języka, który jest łatwy w użyciu i fizycznych dla języka.
ms.date: 06/20/2016
ms.openlocfilehash: 6925a0132f9beed6be5f9dded3630b551072bea2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343457"
---
# <a name="async-programming-in-f"></a><span data-ttu-id="aa707-103">Programowanie asynchroniczne w F\#</span><span class="sxs-lookup"><span data-stu-id="aa707-103">Async Programming in F\#</span></span>

> [!NOTE]
> <span data-ttu-id="aa707-104">Niektóre nieścisłości zostały odnalezione w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="aa707-104">Some inaccuracies have been discovered in this article.</span></span>  <span data-ttu-id="aa707-105">Jego jest modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="aa707-105">It is being rewritten.</span></span>  <span data-ttu-id="aa707-106">Zobacz [666 # problem](https://github.com/dotnet/docs/issues/666) Aby dowiedzieć się więcej o zmianach.</span><span class="sxs-lookup"><span data-stu-id="aa707-106">See [Issue #666](https://github.com/dotnet/docs/issues/666) to learn about the changes.</span></span>

<span data-ttu-id="aa707-107">Async — Programowanie w F# można osiągnąć za pomocą poziomu języka modelu programowania, mają postać łatwy w użyciu i fizycznych dla języka.</span><span class="sxs-lookup"><span data-stu-id="aa707-107">Async programming in F# can be accomplished through a language-level programming model designed to be easy to use and natural to the language.</span></span>

<span data-ttu-id="aa707-108">Podstawowe async — Programowanie w F# jest `Async<'T>`, reprezentacja tych prac, które mogą być wyzwalane do uruchamiania w tle, gdzie `'T` albo typ zwracany jest za pomocą specjalnych `return` — słowo kluczowe lub `unit` Jeśli asynchronicznego przepływu pracy nie ma żadnego wyniku do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="aa707-108">The core of async programming in F# is `Async<'T>`, a representation of work that can be triggered to run in the background, where `'T` is either the type returned via the special `return` keyword or `unit` if the async workflow has no result to return.</span></span>

<span data-ttu-id="aa707-109">Kluczowe pojęcia, aby zrozumieć, że jest typ wyrażenia asynchroniczne `Async<'T>`, który jest jedynie _specyfikacji_ pracy należy wykonać w kontekście asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="aa707-109">The key concept to understand is that an async expression’s type is `Async<'T>`, which is merely a _specification_ of work to be done in an asynchronous context.</span></span> <span data-ttu-id="aa707-110">Nie jest to wykonywane, dopóki nie zostanie jawnie uruchomiony przy użyciu jednej z funkcji początkowy (takie jak `Async.RunSynchronously`).</span><span class="sxs-lookup"><span data-stu-id="aa707-110">It is not executed until you explicitly start it with one of the starting functions (such as `Async.RunSynchronously`).</span></span> <span data-ttu-id="aa707-111">Chociaż jest to inny sposób myślenia o wykonywania pracy, kończy się ono jest bardzo proste, w praktyce.</span><span class="sxs-lookup"><span data-stu-id="aa707-111">Although this is a different way of thinking about doing work, it ends up being quite simple in practice.</span></span>

<span data-ttu-id="aa707-112">Na przykład załóżmy, że chcesz pobrać kod HTML z dotnetfoundation.org bez blokowania wątku głównego.</span><span class="sxs-lookup"><span data-stu-id="aa707-112">For example, say you wanted to download the HTML from dotnetfoundation.org without blocking the main thread.</span></span> <span data-ttu-id="aa707-113">Można wykonać je w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="aa707-113">You can accomplish it like this:</span></span>

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

<span data-ttu-id="aa707-114">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="aa707-114">And that’s it!</span></span> <span data-ttu-id="aa707-115">Oprócz stosowania `async`, `let!`, i `return`, jest to po prostu normalne F# kodu.</span><span class="sxs-lookup"><span data-stu-id="aa707-115">Aside from the use of `async`, `let!`, and `return`, this is just normal F# code.</span></span>

<span data-ttu-id="aa707-116">Istnieje kilka syntaktycznych konstrukcji, które są warte odnotowania:</span><span class="sxs-lookup"><span data-stu-id="aa707-116">There are a few syntactical constructs which are worth noting:</span></span>

*   `let!` <span data-ttu-id="aa707-117">wiąże wynik wyrażenia asynchroniczne (który jest uruchamiany w kontekście innej).</span><span class="sxs-lookup"><span data-stu-id="aa707-117">binds the result of an async expression (which runs on another context).</span></span>
*   `use!` <span data-ttu-id="aa707-118">działa podobnie jak w przypadku `let!`, ale usuwa jego powiązanych zasobów, gdy jej wykracza poza zakres.</span><span class="sxs-lookup"><span data-stu-id="aa707-118">works just like `let!`, but disposes its bound resources when it goes out of scope.</span></span>
*   `do!` <span data-ttu-id="aa707-119">będzie await przepływu pracy "async", która nie zwraca niczego.</span><span class="sxs-lookup"><span data-stu-id="aa707-119">will await an async workflow which doesn’t return anything.</span></span>
*   `return` <span data-ttu-id="aa707-120">po prostu zwraca wynik wyrażenia asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="aa707-120">simply returns a result from an async expression.</span></span>
*   `return!` <span data-ttu-id="aa707-121">wykonuje inną asynchronicznego przepływu pracy i zwraca jego wartość zwracana w wyniku.</span><span class="sxs-lookup"><span data-stu-id="aa707-121">executes another async workflow and returns its return value as a result.</span></span>

<span data-ttu-id="aa707-122">Ponadto normalne `let`, `use`, i `do` słów kluczowych można używać razem z wersjami async tak samo, jak w normalnym funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa707-122">Additionally, normal `let`, `use`, and `do` keywords can be used alongside the async versions just as they would in a normal function.</span></span>

## <a name="how-to-start-async-code-in-f"></a><span data-ttu-id="aa707-123">Jak uruchomić kod asynchroniczny w F\#</span><span class="sxs-lookup"><span data-stu-id="aa707-123">How to start Async Code in F\#</span></span>

<span data-ttu-id="aa707-124">Jak wspomniano wcześniej, kod asynchroniczny jest określenie zadań do wykonania w innym kontekście, który musi być jawnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="aa707-124">As mentioned earlier, async code is a specification of work to be done in another context which needs to be explicitly started.</span></span> <span data-ttu-id="aa707-125">Oto dwa podstawowe sposoby, w tym celu:</span><span class="sxs-lookup"><span data-stu-id="aa707-125">Here are two primary ways to accomplish this:</span></span>

1. `Async.RunSynchronously` <span data-ttu-id="aa707-126">uruchomi przepływ pracy asynchronicznej w innym wątku i poczekać na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="aa707-126">will start an async workflow on another thread and await its result.</span></span>

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

2. `Async.Start` <span data-ttu-id="aa707-127">Uruchom przepływ pracy asynchronicznej w innym wątku, a będzie **nie** poczekać na jego wynik.</span><span class="sxs-lookup"><span data-stu-id="aa707-127">will start an async workflow on another thread, and will **not** await its result.</span></span>

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

<span data-ttu-id="aa707-128">Istnieją inne sposoby, aby uruchomić przepływ pracy async dostępne dla bardziej specyficznych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="aa707-128">There are other ways to start an async workflow available for more specific scenarios.</span></span> <span data-ttu-id="aa707-129">Są szczegółowo opisane [w odwołaniu Async](https://msdn.microsoft.com/library/ee370232.aspx).</span><span class="sxs-lookup"><span data-stu-id="aa707-129">They are detailed [in the Async reference](https://msdn.microsoft.com/library/ee370232.aspx).</span></span>

### <a name="a-note-on-threads"></a><span data-ttu-id="aa707-130">Uwaga dotycząca wątków</span><span class="sxs-lookup"><span data-stu-id="aa707-130">A Note on Threads</span></span>

<span data-ttu-id="aa707-131">Wyrażenie "w innym wątku" został podany powyżej, ale ważne jest, aby poinformować, że **nie oznacza to, że asynchronicznymi przepływami pracy są fasada dla wielowątkowości**.</span><span class="sxs-lookup"><span data-stu-id="aa707-131">The phrase "on another thread" is mentioned above, but it is important to know that **this does not mean that async workflows are a facade for multithreading**.</span></span> <span data-ttu-id="aa707-132">Przepływ pracy faktycznie "skacze" między wątkami i finansowania ich zewnętrznego dla niewielkiej ilości czasu wykonywania użytecznej pracy.</span><span class="sxs-lookup"><span data-stu-id="aa707-132">The workflow actually "jumps" between threads, borrowing them for a small amount of time to do useful work.</span></span> <span data-ttu-id="aa707-133">Gdy przepływ pracy asynchronicznej jest skutecznie "oczekiwanie" (np. oczekiwanie na połączenie sieciowe zwrócić coś), żadnym z wątków, który został on finansowania zewnętrznego w czasie jest zwalniana maksymalnie Przejdź użytecznej pracy na coś innego.</span><span class="sxs-lookup"><span data-stu-id="aa707-133">When an async workflow is effectively "waiting" (for example, waiting for a network call to return something), any thread it was borrowing at the time is freed up to go do useful work on something else.</span></span> <span data-ttu-id="aa707-134">Umożliwia asynchroniczne przepływy pracy służące do korzystają z systemu, które są uruchamiane w możliwie najbardziej efektywny sposób i udostępnianie ich w szczególnie duży dla dużej liczby operacji We/Wy scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="aa707-134">This allows async workflows to utilize the system they run on as effectively as possible, and makes them especially strong for high-volume I/O scenarios.</span></span>

## <a name="how-to-add-parallelism-to-async-code"></a><span data-ttu-id="aa707-135">Jak dodać równoległości do kod asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="aa707-135">How to Add Parallelism to Async Code</span></span>

<span data-ttu-id="aa707-136">Czasami możesz potrzebne do wykonywania wielu zadań asynchronicznych w sposób równoległy, zbieraj ich wyniki i interpretował je w jakiś sposób.</span><span class="sxs-lookup"><span data-stu-id="aa707-136">Sometimes you may need to perform multiple asynchronous jobs in parallel, collect their results, and interpret them in some way.</span></span> `Async.Parallel` <span data-ttu-id="aa707-137">Można to zrobić bez konieczności korzystania z biblioteki równoległych zadań, która obejmowałaby konieczności wymuszone `Task<'T>` i `Async<'T>` typów.</span><span class="sxs-lookup"><span data-stu-id="aa707-137">allows you to do this without needing to use the Task Parallel Library, which would involve needing to coerce `Task<'T>` and `Async<'T>` types.</span></span>

<span data-ttu-id="aa707-138">Poniższy przykład użyje `Async.Parallel` można pobrać kod HTML z czterech popularnych witryn w sposób równoległy, poczekaj na zakończenie tych zadań, a następnie wydrukuj kodu HTML, który został pobrany.</span><span class="sxs-lookup"><span data-stu-id="aa707-138">The following example will use `Async.Parallel` to download the HTML from four popular sites in parallel, wait for those tasks to complete, and then print the HTML which was downloaded.</span></span>

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

## <a name="important-info-and-advice"></a><span data-ttu-id="aa707-139">Ważne informacje i opinie</span><span class="sxs-lookup"><span data-stu-id="aa707-139">Important Info and Advice</span></span>

*   <span data-ttu-id="aa707-140">Dołącza się "Async" na końcu wszystkie funkcje, których będziesz używać</span><span class="sxs-lookup"><span data-stu-id="aa707-140">Append "Async" to the end of any functions you’ll consume</span></span>

 <span data-ttu-id="aa707-141">Chociaż jest to po prostu konwencji nazewnictwa, jego ułatwiają elementów, takich jak odnajdywania interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="aa707-141">Although this is just a naming convention, it does make things like API discoverability easier.</span></span> <span data-ttu-id="aa707-142">Szczególnie, jeśli są synchroniczne i asynchroniczne wersje tej samej procedury, jest dobrym pomysłem jest jawnie określać, które jest asynchroniczne za pomocą nazwy.</span><span class="sxs-lookup"><span data-stu-id="aa707-142">Particularly if there are synchronous and asynchronous versions of the same routine, it’s a good idea to explicitly state which is asynchronous via the name.</span></span>

*   <span data-ttu-id="aa707-143">Nasłuchiwanie w kompilatorze!</span><span class="sxs-lookup"><span data-stu-id="aa707-143">Listen to the compiler!</span></span>

 <span data-ttu-id="aa707-144">F#przez kompilator jest bardzo rygorystyczny, uniemożliwiając niemal trudne, podobnie jak coś zrobić uruchamiane synchronicznie kodu "async".</span><span class="sxs-lookup"><span data-stu-id="aa707-144">F#’s compiler is very strict, making it nearly impossible to do something troubling like run "async" code synchronously.</span></span> <span data-ttu-id="aa707-145">Jeśli trafisz na ostrzeżenie, jest znakiem, kod nie będzie wykonanie, jak uważasz, że będą wykonywane następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="aa707-145">If you come across a warning, that’s a sign that the code won’t execute how you think it will.</span></span> <span data-ttu-id="aa707-146">Jeśli kompilator może wprowadzić wszystkiego, Twój kod najprawdopodobniej będą wykonywane zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="aa707-146">If you can make the compiler happy, your code will most likely execute as expected.</span></span>

## <a name="for-the-cvb-programmer-looking-into-f"></a><span data-ttu-id="aa707-147">Aby uzyskać C#programisty /VB przyjrzeć F\#</span><span class="sxs-lookup"><span data-stu-id="aa707-147">For the C#/VB Programmer Looking Into F\#</span></span>

<span data-ttu-id="aa707-148">W tej sekcji założono, znasz modelu asynchronicznych w C#/VB.</span><span class="sxs-lookup"><span data-stu-id="aa707-148">This section assumes you’re familiar with the async model in C#/VB.</span></span> <span data-ttu-id="aa707-149">Jeśli nie, [asynchroniczne Programowanie w C# ](../../../csharp/async.md) stanowi punkt wyjścia.</span><span class="sxs-lookup"><span data-stu-id="aa707-149">If you are not, [Async Programming in C#](../../../csharp/async.md) is a starting point.</span></span>

<span data-ttu-id="aa707-150">Jest główną różnicą między C#/VB async modelu i F# async modelu.</span><span class="sxs-lookup"><span data-stu-id="aa707-150">There is a fundamental difference between the C#/VB async model and the F# async model.</span></span>

<span data-ttu-id="aa707-151">Gdy zostanie wywołana funkcja, która zwraca `Task` lub `Task<'T>`, że zadanie już się rozpoczęło wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aa707-151">When you call a function which returns a `Task` or `Task<'T>`, that job has already begun execution.</span></span> <span data-ttu-id="aa707-152">Uchwyt zwracany reprezentuje zadanie asynchroniczne już działa.</span><span class="sxs-lookup"><span data-stu-id="aa707-152">The handle returned represents an already-running asynchronous job.</span></span> <span data-ttu-id="aa707-153">Z kolei jeśli wywołasz funkcji asynchronicznej F#, `Async<'a>` zwrócił reprezentuje zadanie, które będą odpowiadać **generowane** w pewnym momencie.</span><span class="sxs-lookup"><span data-stu-id="aa707-153">In contrast, when you call an async function in F#, the `Async<'a>` returned represents a job which will be **generated** at some point.</span></span> <span data-ttu-id="aa707-154">Zrozumienie ten model jest wydajne, ponieważ umożliwia asynchroniczne zadania w F# się ze sobą sposób łatwiej, wykonywane warunkowo i uruchomić z większym ziarna kontrolki.</span><span class="sxs-lookup"><span data-stu-id="aa707-154">Understanding this model is powerful, because it allows for asynchronous jobs in F# to be chained together easier, performed conditionally, and be started with a finer grain of control.</span></span>

<span data-ttu-id="aa707-155">Istnieje kilka innych podobieństwa i różnice warte odnotowania.</span><span class="sxs-lookup"><span data-stu-id="aa707-155">There are a few other similarities and differences worth noting.</span></span>

### <a name="similarities"></a><span data-ttu-id="aa707-156">Podobieństwa</span><span class="sxs-lookup"><span data-stu-id="aa707-156">Similarities</span></span>

*   `let!`<span data-ttu-id="aa707-157">, `use!`, i `do!` są analogiczne do `await` podczas wywoływania asynchroniczne zadanie z poziomu `async{ }` bloku.</span><span class="sxs-lookup"><span data-stu-id="aa707-157">, `use!`, and `do!` are analogous to `await` when calling an async job from within an `async{ }` block.</span></span>

 <span data-ttu-id="aa707-158">Trzech słów kluczowych można używać tylko wewnątrz `async { }` bloku, podobnie jak `await` można wywołać tylko wewnątrz `async` metody.</span><span class="sxs-lookup"><span data-stu-id="aa707-158">The three keywords can only be used within an `async { }` block, similar to how `await` can only be invoked inside an `async` method.</span></span> <span data-ttu-id="aa707-159">Krótko mówiąc `let!` dotyczy sytuacji, gdy chcesz przechwytywać i używać ich wynik `use!` jest coś, którego zasoby powinny uzyskać czyszczone po jest używane, ale ten sam i `do!` dotyczy sytuacji, gdy chcesz czekać na przepływ pracy programu async za pomocą nie zwraca wartości, aby zakończyć Przed kontynuowaniem.</span><span class="sxs-lookup"><span data-stu-id="aa707-159">In short, `let!` is for when you want to capture and use a result, `use!` is the same but for something whose resources should get cleaned after it’s used, and `do!` is for when you want to wait for an async workflow with no return value to finish before moving on.</span></span>

*   <span data-ttu-id="aa707-160">F#obsługuje równoległość danych w podobny sposób.</span><span class="sxs-lookup"><span data-stu-id="aa707-160">F# supports data-parallelism in a similar way.</span></span>

 <span data-ttu-id="aa707-161">Mimo że działa on tak bardzo inaczej `Async.Parallel` odpowiada `Task.WhenAll` scenariusza wskazujące na potrzebę wyniki zestaw zadań asynchronicznych po ich ukończeniu.</span><span class="sxs-lookup"><span data-stu-id="aa707-161">Although it operates very differently, `Async.Parallel` corresponds to `Task.WhenAll` for the scenario of wanting the results of a set of async jobs when they all complete.</span></span>

### <a name="differences"></a><span data-ttu-id="aa707-162">Różnice</span><span class="sxs-lookup"><span data-stu-id="aa707-162">Differences</span></span>

*   <span data-ttu-id="aa707-163">Zagnieżdżone `let!` nie jest dozwolone, inaczej niż w przypadku zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="aa707-163">Nested `let!` is not allowed, unlike nested</span></span> `await`

 <span data-ttu-id="aa707-164">W odróżnieniu od `await`, które mogą być zagnieżdżane przez czas nieokreślony, `let!` nie i muszą mieć wynik powiązany przed jego użyciem wewnątrz innego `let!`, `do!`, lub `use!`.</span><span class="sxs-lookup"><span data-stu-id="aa707-164">Unlike `await`, which can be nested indefinitely, `let!` cannot and must have its result bound before using it inside of another `let!`, `do!`, or `use!`.</span></span>

*   <span data-ttu-id="aa707-165">Obsługę anulowania jest prostsza w F# niż w C#/VB.</span><span class="sxs-lookup"><span data-stu-id="aa707-165">Cancellation support is simpler in F# than in C#/VB.</span></span>

 <span data-ttu-id="aa707-166">Obsługa anulowania zadania w połowie drogi za pośrednictwem jej wykonanie w C#/VB wymaga sprawdzanie `IsCancellationRequested` właściwość lub wywołanie `ThrowIfCancellationRequested()` na `CancellationToken` obiektu, który jest przekazywany do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="aa707-166">Supporting cancellation of a task midway through its execution in C#/VB requires checking the `IsCancellationRequested` property or calling `ThrowIfCancellationRequested()` on a `CancellationToken` object that’s passed into the async method.</span></span>

<span data-ttu-id="aa707-167">Z kolei F# asynchronicznymi przepływami pracy są bardziej naturalnie można anulować.</span><span class="sxs-lookup"><span data-stu-id="aa707-167">In contrast, F# async workflows are more naturally cancellable.</span></span> <span data-ttu-id="aa707-168">Anulowanie jest to prosty proces krok 3.</span><span class="sxs-lookup"><span data-stu-id="aa707-168">Cancellation is a simple three-step process.</span></span>

1. <span data-ttu-id="aa707-169">Utwórz nową `CancellationTokenSource`.</span><span class="sxs-lookup"><span data-stu-id="aa707-169">Create a new `CancellationTokenSource`.</span></span>
2. <span data-ttu-id="aa707-170">Przekaż go do wyjścia funkcji.</span><span class="sxs-lookup"><span data-stu-id="aa707-170">Pass it into a starting function.</span></span>
3. <span data-ttu-id="aa707-171">Wywołaj `Cancel` w tokenie.</span><span class="sxs-lookup"><span data-stu-id="aa707-171">Call `Cancel` on the token.</span></span>

<span data-ttu-id="aa707-172">Przykład:</span><span class="sxs-lookup"><span data-stu-id="aa707-172">Example:</span></span>

```fsharp
open System.Threading

// Create a workflow which will loop forever.
let workflow =
    async {
        while true do
            printfn "Working..."
            do! Async.Sleep 1000
    }
    
let tokenSource = new CancellationTokenSource()

// Start the workflow in the background
Async.Start (workflow, tokenSource.Token)

// Executing the next line will stop the workflow
tokenSource.Cancel()
```

<span data-ttu-id="aa707-173">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="aa707-173">And that’s it!</span></span>

## <a name="further-resources"></a><span data-ttu-id="aa707-174">Dalsze zasoby:</span><span class="sxs-lookup"><span data-stu-id="aa707-174">Further resources:</span></span>

*   [<span data-ttu-id="aa707-175">Asynchronicznymi przepływami pracy w witrynie MSDN</span><span class="sxs-lookup"><span data-stu-id="aa707-175">Async Workflows on MSDN</span></span>](https://msdn.microsoft.com/library/dd233250.aspx)
*   [<span data-ttu-id="aa707-176">Asynchroniczne sekwencji dlaF#</span><span class="sxs-lookup"><span data-stu-id="aa707-176">Asynchronous Sequences for F#</span></span>](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [<span data-ttu-id="aa707-177">F#Narzędzia danych protokołu HTTP</span><span class="sxs-lookup"><span data-stu-id="aa707-177">F# Data HTTP Utilities</span></span>](https://fsharp.github.io/FSharp.Data/library/Http.html)