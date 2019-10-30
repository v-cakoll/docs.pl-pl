---
title: Programowanie asynchroniczne —C#
description: Dowiedz się C# więcej o modelu programowania asynchronicznego na poziomie języka udostępnianym przez platformę .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 86145e8971d9a59fba17368d9530f40d86bf2858
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037684"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="9cdfc-103">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="9cdfc-103">Asynchronous programming</span></span>

<span data-ttu-id="9cdfc-104">Jeśli istnieją jakieś wymagania dotyczące operacji we/wy (takie jak żądanie danych z sieci lub uzyskiwanie dostępu do bazy danych), należy wykorzystać programowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="9cdfc-105">Można również mieć kod powiązany z PROCESORem, taki jak wykonywanie kosztownych obliczeń, co jest również dobrym scenariuszem do pisania kodu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="9cdfc-106">C#ma model programowania asynchronicznego na poziomie języka, który umożliwia łatwe pisanie kodu asynchronicznego bez konieczności Juggle wywołań zwrotnych lub zgodności z biblioteką obsługującą asynchroniczności.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="9cdfc-107">Następuje to, co jest znane jako [wzorzec asynchroniczny oparty na zadaniach (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="9cdfc-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="9cdfc-108">Podstawowe omówienie modelu asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="9cdfc-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="9cdfc-109">Podstawowym programowaniem asynchronicznym są obiekty `Task` i `Task<T>`, które są modelami operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="9cdfc-110">Są one obsługiwane przez `async` i `await` słowa kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="9cdfc-111">Model jest dość prosty w większości przypadków:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="9cdfc-112">W przypadku kodu powiązanego we/wy `await` operacji zwracającej `Task` lub `Task<T>` wewnątrz metody `async`.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="9cdfc-113">W przypadku kodu powiązanego z PROCESORem `await` operacji, która jest uruchamiana w wątku w tle z metodą `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="9cdfc-114">Słowo kluczowe `await` to miejsce, w którym występuje magiczna.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="9cdfc-115">Zwraca kontrolę do obiektu wywołującego metody, która została wykonana `await`, i ostatecznie pozwala na reagowanie interfejsu użytkownika lub na usługę elastyczną.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="9cdfc-116">Istnieją inne sposoby podejścia do kodu asynchronicznego niż `async` i `await` opisane w artykule TAP połączonym powyżej, ale ten dokument będzie skoncentrowane na konstrukcjach poziomu języka od tego momentu.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="9cdfc-117">Przykład powiązania we/wy: pobieranie danych z usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="9cdfc-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="9cdfc-118">Może być konieczne pobranie niektórych danych z usługi sieci Web po naciśnięciu przycisku, ale nie chcesz blokować wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="9cdfc-119">Można to zrobić w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-119">It can be accomplished simply like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="9cdfc-120">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="9cdfc-120">And that’s it!</span></span> <span data-ttu-id="9cdfc-121">Kod wyraża zamiar (trwa pobieranie danych asynchronicznie) bez pobierania ugrzęźnięcia z obiektów zadań.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="9cdfc-122">Przykład związany z PROCESORem: wykonywanie obliczeń dla gry</span><span class="sxs-lookup"><span data-stu-id="9cdfc-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="9cdfc-123">Załóżmy, że nastąpi napisanie gry mobilnej, gdzie naciśnięcie przycisku może spowodować uszkodzenie wielu Enemies na ekranie.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="9cdfc-124">Wykonywanie obliczeń uszkodzeń może być kosztowne, a wykonanie tej operacji w wątku interfejsu użytkownika spowoduje, że gra zostanie wstrzymana w miarę wykonywania obliczeń.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="9cdfc-125">Najlepszym sposobem obsługi tego jest uruchomienie wątku w tle, który wykonuje pracę przy użyciu `Task.Run`i `await` jego wyniku.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="9cdfc-126">Dzięki temu interfejs użytkownika może być niezakłócony podczas wykonywania pracy.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-126">This will allow the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="9cdfc-127">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="9cdfc-127">And that's it!</span></span>  <span data-ttu-id="9cdfc-128">Ten kod czyści przeznaczenie zdarzenia kliknięcia przycisku, nie wymaga ręcznego zarządzania wątkiem w tle i robi to w sposób nieblokowany.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="9cdfc-129">Co się dzieje w obszarze okładek</span><span class="sxs-lookup"><span data-stu-id="9cdfc-129">What happens under the covers</span></span>

<span data-ttu-id="9cdfc-130">Istnieje wiele elementów, w których dane są wykonywane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="9cdfc-131">Jeśli chcesz wiedzieć się o to `Task<T>``Task`, co się dzieje poniżej [, zapoznaj](../standard/async-in-depth.md) się z informacjami o tym, co się stało, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="9cdfc-132">Po C# stronie elementów kompilator przekształca kod na maszynę stanu, która śledzi elementy, takie jak wykonywanie operacji, gdy`await`zostanie osiągnięty, i wznowić wykonywanie po zakończeniu zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="9cdfc-133">Dla teoretycznie nachylonego elementu jest to implementacja [modelu Promise asynchroniczności](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="9cdfc-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="9cdfc-134">Najważniejsze elementy do zrozumienia</span><span class="sxs-lookup"><span data-stu-id="9cdfc-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="9cdfc-135">Kod asynchroniczny może być używany zarówno dla kodu powiązanego we/wy, jak i związanego z PROCESORem, ale różnią się w zależności od każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="9cdfc-136">Kod asynchroniczny używa `Task<T>` i `Task`, które są konstrukcjami używanymi do modelowania pracy wykonywanej w tle.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="9cdfc-137">Słowo kluczowe `async` przekształca metodę w metodę asynchroniczną, która umożliwia użycie słowa kluczowego `await` w treści.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="9cdfc-138">Po zastosowaniu słowa kluczowego `await` wstrzymuje metodę wywołującą i przekazuje kontrolę do obiektu wywołującego do momentu ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="9cdfc-139">`await` można używać tylko wewnątrz metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="9cdfc-140">Rozpoznawanie pracy powiązanej z PROCESORem i operacji we/wy</span><span class="sxs-lookup"><span data-stu-id="9cdfc-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="9cdfc-141">W pierwszych dwóch przykładach tego przewodnika pokazano, jak używać `async` i `await` w przypadku pracy związanej ze współdziałaniem i z PROCESORem.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="9cdfc-142">Jest to klucz, który można określić, gdy zadanie, które należy wykonać, jest powiązane z elementem we/wy lub PROCESORem, ponieważ może znacznie wpływać na wydajność kodu i potencjalnie spowodować błędne użycie niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="9cdfc-143">Poniżej przedstawiono dwa pytania, które należy zadać przed pisaniem dowolnego kodu:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="9cdfc-144">Czy kod będzie oczekiwał na coś, takiego jak dane z bazy danych?</span><span class="sxs-lookup"><span data-stu-id="9cdfc-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="9cdfc-145">Jeśli odpowiedź brzmi "tak", Twoja służba jest **powiązana z elementem we/wy**.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="9cdfc-146">Czy kod będzie wykonywał bardzo kosztowne obliczenia?</span><span class="sxs-lookup"><span data-stu-id="9cdfc-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="9cdfc-147">Jeśli otrzymasz odpowiedź "tak", Twoja służba jest **powiązana z procesorem**.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="9cdfc-148">Jeśli osiągnięta jest **powiązana z nią funkcja we/wy**, użyj `async` i `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="9cdfc-149">*Nie należy* używać biblioteki zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="9cdfc-150">Przyczynę tego problemu opisano w artykule dotyczącym [kompleksów](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="9cdfc-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="9cdfc-151">Jeśli posiadana praca jest **zależna od procesora** i masz informacje o czasie reakcji, użyj `async` i `await` ale należy zduplikować działanie w innym wątku *przy użyciu* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="9cdfc-152">Jeśli prace są odpowiednie dla współbieżności i równoległości, należy również rozważyć użycie [biblioteki zadań równoległych](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9cdfc-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="9cdfc-153">Dodatkowo należy zawsze mierzyć wykonywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="9cdfc-154">Można na przykład wyszukać siebie w sytuacji, w której ilość pracy związanej z PROCESORem jest zbyt mała w porównaniu z kosztami przełączeń kontekstu w przypadku wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="9cdfc-155">Każdy wybór ma swoje wady i należy wybrać odpowiednią kompromis dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="9cdfc-156">Więcej przykładów</span><span class="sxs-lookup"><span data-stu-id="9cdfc-156">More Examples</span></span>

<span data-ttu-id="9cdfc-157">W poniższych przykładach pokazano różne sposoby pisania kodu asynchronicznego w programie C#.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="9cdfc-158">Obejmują one kilka różnych scenariuszy, które mogą się pojawić.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="9cdfc-159">Wyodrębnianie danych z sieci</span><span class="sxs-lookup"><span data-stu-id="9cdfc-159">Extracting Data from a Network</span></span>

<span data-ttu-id="9cdfc-160">Ten fragment kodu pobiera kod HTML z strony głównej pod adresem [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza liczbę wystąpień ciągu ".NET" w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="9cdfc-161">Używa ASP.NET MVC do zdefiniowania metody kontrolera sieci Web, która wykonuje to zadanie, zwracając liczbę.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="9cdfc-162">Jeśli planujesz wykonywanie analizy HTML w kodzie produkcyjnym, nie używaj wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="9cdfc-163">Zamiast tego użyj biblioteki analizy.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="9cdfc-164">Jest to ten sam scenariusz Zapisano dla aplikacji uniwersalnej systemu Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="9cdfc-165">Oczekiwanie na zakończenie wielu zadań</span><span class="sxs-lookup"><span data-stu-id="9cdfc-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="9cdfc-166">Możesz się zastanowić w sytuacji, w której konieczne jest pobranie wielu danych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="9cdfc-167">Interfejs API `Task` zawiera dwie metody, `Task.WhenAll` i `Task.WhenAny`, które umożliwiają pisanie kodu asynchronicznego, który wykonuje operację nieblokującą w przypadku wielu zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="9cdfc-168">Ten przykład pokazuje, jak można uzyskać `User` danych dla zestawu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();

    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="9cdfc-169">Oto inny sposób, aby napisać nieco bardziej zwięzłie, przy użyciu LINQ:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="9cdfc-170">Chociaż nie jest to mniej kodu, weź pod uwagę podczas mieszania LINQ z kodem asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="9cdfc-171">Ponieważ LINQ korzysta z odroczonego (opóźnionego) wykonywania, wywołania asynchroniczne nie będą wykonywane natychmiast, gdy wykonują pętlę `foreach()`, chyba że wygenerowała sekwencja nie będzie mogła wykonać iteracji w wywołaniu `.ToList()` lub `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="9cdfc-172">Ważne informacje i porady</span><span class="sxs-lookup"><span data-stu-id="9cdfc-172">Important Info and Advice</span></span>

<span data-ttu-id="9cdfc-173">Chociaż programowanie asynchroniczne jest stosunkowo proste, istnieją pewne szczegółowe informacje, które mogą uniemożliwić nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="9cdfc-174">**metody `async` muszą mieć** **słowo kluczowe `await` w swojej treści lub nigdy nie będą one dostępne!**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="9cdfc-175">Jest to ważne, aby mieć świadomość.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-175">This is important to keep in mind.</span></span>  <span data-ttu-id="9cdfc-176">Jeśli `await` nie jest używany w treści metody `async`, C# kompilator generuje ostrzeżenie, ale kod zostanie skompilowany i uruchomiony tak, jakby był normalną metodą.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="9cdfc-177">Należy zauważyć, że może to również być niezwykle niewydajne, ponieważ komputer stanu wygenerowany przez C# kompilator dla metody asynchronicznej nie będzie wykonywać żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="9cdfc-178">**Należy dodać "Async" jako sufiks każdej zapisywanych nazw metod asynchronicznych.**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="9cdfc-179">Jest to Konwencja używana w programie .NET do łatwiejszego odróżnienia metod synchronicznych i asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="9cdfc-180">Należy zauważyć, że niektóre metody, które nie są jawnie wywoływane przez kod (takie jak procedury obsługi zdarzeń lub metody kontrolera sieci Web), nie muszą być stosowane.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="9cdfc-181">Ponieważ nie są one jawnie wywoływane przez kod, jawny opis jego nazewnictwa nie jest ważny.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="9cdfc-182">`async void` **należy używać tylko dla programów obsługi zdarzeń.**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="9cdfc-183">`async void` jest jedynym sposobem zezwalania na działanie programów obsługi zdarzeń asynchronicznych, ponieważ zdarzenia nie mają zwracanych typów (w związku z tym nie mogą korzystać z `Task` i `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="9cdfc-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="9cdfc-184">Inne użycie `async void` nie jest zgodne z modelem TAP i może być trudne do użycia, takie jak:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="9cdfc-185">Wyjątki zgłoszone w metodzie `async void` nie mogą być przechwytywane poza tą metodą.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="9cdfc-186">Metody `async void` są bardzo trudne do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="9cdfc-187">Metody `async void` mogą spowodować złe skutki uboczne, jeśli obiekt wywołujący nie oczekuje, że będzie on asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="9cdfc-188">**Dokładne użycie asynchronicznych wyrażeń lambda w wyrażeniach LINQ**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="9cdfc-189">Wyrażenia lambda w składniku LINQ wykorzystują odroczone wykonywanie, co oznacza, że kod może zakończyć wykonywanie w czasie, gdy nie jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="9cdfc-190">Wprowadzenie zadań blokowania w tym celu może w prosty sposób spowodować zakleszczenie, jeśli nie zapisano prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="9cdfc-191">Ponadto zagnieżdżanie kodu asynchronicznego, takiego jak ten, może być również trudniejsze do powodowania wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="9cdfc-192">Asynchroniczne i LINQ są zaawansowane, ale powinny być używane razem, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="9cdfc-193">**Napisz kod, który czeka na zadania w sposób nieblokowany**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="9cdfc-194">Zablokowanie bieżącego wątku jako środka do oczekiwania na ukończenie zadania może spowodować zakleszczenie i zablokowane wątki kontekstu i może wymagać znacznie bardziej złożonej obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="9cdfc-195">Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania z oczekiwaniami w przypadku zadań w sposób nieblokowany:</span><span class="sxs-lookup"><span data-stu-id="9cdfc-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="9cdfc-196">Użyj tego...</span><span class="sxs-lookup"><span data-stu-id="9cdfc-196">Use this...</span></span> | <span data-ttu-id="9cdfc-197">Zamiast tego...</span><span class="sxs-lookup"><span data-stu-id="9cdfc-197">Instead of this...</span></span> | <span data-ttu-id="9cdfc-198">Jeśli chcesz to zrobić</span><span class="sxs-lookup"><span data-stu-id="9cdfc-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="9cdfc-199">`Task.Wait` lub `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="9cdfc-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="9cdfc-200">Pobieranie wyniku zadania w tle</span><span class="sxs-lookup"><span data-stu-id="9cdfc-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="9cdfc-201">Oczekiwanie na zakończenie dowolnego zadania</span><span class="sxs-lookup"><span data-stu-id="9cdfc-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="9cdfc-202">Oczekiwanie na zakończenie wszystkich zadań</span><span class="sxs-lookup"><span data-stu-id="9cdfc-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="9cdfc-203">Oczekiwanie przez pewien czas</span><span class="sxs-lookup"><span data-stu-id="9cdfc-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="9cdfc-204">**Zapisz mniej stanowy kod**</span><span class="sxs-lookup"><span data-stu-id="9cdfc-204">**Write less stateful code**</span></span>

<span data-ttu-id="9cdfc-205">Nie zależą od stanu obiektów globalnych lub wykonywania niektórych metod.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="9cdfc-206">Zamiast tego zależą tylko od wartości zwracanych z metod.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="9cdfc-207">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="9cdfc-207">Why?</span></span>

* <span data-ttu-id="9cdfc-208">Kod będzie łatwiejszy z przyczyn.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="9cdfc-209">Kod będzie łatwiejszy do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-209">Code will be easier to test.</span></span>
* <span data-ttu-id="9cdfc-210">Mieszanie kodu asynchronicznego i synchronicznego jest bardzo prostsze.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="9cdfc-211">Warunki wyścigu można zwykle uniknąć w ogóle.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="9cdfc-212">W zależności od zwracanych wartości upraszczamy prosty kod asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="9cdfc-213">(Premia) dobrze sprawdza się w przypadku iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="9cdfc-214">Zalecanym celem jest osiągnięcie pełnej lub niemal kompletnej [przejrzystości referencyjnej](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="9cdfc-215">Wykonanie tej czynności spowoduje powstanie niezwykle przewidywalnej, weryfikowalneej i obsługiwanej bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="9cdfc-216">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="9cdfc-216">Other Resources</span></span>

* <span data-ttu-id="9cdfc-217">[Asynchroniczne](../standard/async-in-depth.md) Szczegóły zawiera więcej informacji na temat działania zadań.</span><span class="sxs-lookup"><span data-stu-id="9cdfc-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="9cdfc-218">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="9cdfc-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="9cdfc-219">Lucian Wischike [sześć najważniejszych porad dotyczących Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) to wspaniałe zasoby dla programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="9cdfc-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
