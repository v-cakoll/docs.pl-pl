---
title: Programowanie asynchroniczne
description: Więcej informacji na temat języka C# poziomu języka asynchronicznego modelu programowania udostępnianego przez platformy .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 12ecadb3fa3c6760af4884626f68b47ead2754d5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126500"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="e11eb-103">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="e11eb-103">Asynchronous programming</span></span>

<span data-ttu-id="e11eb-104">W przypadku dowolnego potrzeb I/O-powiązane z (takich jak żąda danych od sieci lub uzyskiwania dostępu do bazy danych) można wykorzystywać programowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="e11eb-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="e11eb-105">Może również mieć kod zależne od Procesora CPU, takie jak kosztowne obliczeń, który jest również dobrym scenariusza dotyczące pisania kodu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="e11eb-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="e11eb-106">C# ma poziom języka asynchronicznego modelu programowania, który pozwala na łatwe pisania kodu asynchronicznego bez konieczności łatwiejszą obsługę wywołań zwrotnych i być zgodna z biblioteki, która obsługuje asynchroniczności.</span><span class="sxs-lookup"><span data-stu-id="e11eb-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="e11eb-107">Następuje to, co jest nazywane [opartego na zadaniach asynchronicznej wzorca (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="e11eb-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="e11eb-108">Ogólne omówienie modelu asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="e11eb-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="e11eb-109">Podstawowe programowanie async jest `Task` i `Task<T>` obiektów, które modelu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="e11eb-110">Są one obsługiwane przez `async` i `await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="e11eb-111">Model jest dość prosty, w większości przypadków:</span><span class="sxs-lookup"><span data-stu-id="e11eb-111">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="e11eb-112">Dla kodu I/O-powiązane z możesz `await` operacją, która zwraca `Task` lub `Task<T>` wewnątrz `async` metody.</span><span class="sxs-lookup"><span data-stu-id="e11eb-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="e11eb-113">Kod, zależne od Procesora CPU możesz `await` operacji, która jest uruchomiona w wątku w tle za pomocą `Task.Run` metody.</span><span class="sxs-lookup"><span data-stu-id="e11eb-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="e11eb-114">`await` — Słowo kluczowe jest, gdzie się dzieje w raporcie magic.</span><span class="sxs-lookup"><span data-stu-id="e11eb-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="e11eb-115">Jego przekazuje sterowanie do obiektu wywołującego metody, który wykonał `await`, a ostatecznie do szybkość reakcji interfejsu użytkownika lub usługi pod kątem elastyczności.</span><span class="sxs-lookup"><span data-stu-id="e11eb-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="e11eb-116">Istnieją inne sposoby kod asynchroniczny podejście niż `async` i `await` opisane w artykule wzorca TAP linki umieszczono powyżej, ale ten dokument koncentruje się na konstrukcji poziomu języka od tego momentu.</span><span class="sxs-lookup"><span data-stu-id="e11eb-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="e11eb-117">Przykład I/O-granicy: Pobieranie danych z usługi sieci web</span><span class="sxs-lookup"><span data-stu-id="e11eb-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="e11eb-118">Może być konieczne po naciśnięciu przycisku, Pobierz dane z usługi sieci web, ale nie chcesz zablokować wątek interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e11eb-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="e11eb-119">Można to osiągnąć po prostu następująco:</span><span class="sxs-lookup"><span data-stu-id="e11eb-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="e11eb-120">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="e11eb-120">And that’s it!</span></span> <span data-ttu-id="e11eb-121">Kod wyraża intencji (pobierania niektórych danych asynchronicznie) bez ugrzęźnięcia w interakcji z obiektów zadań.</span><span class="sxs-lookup"><span data-stu-id="e11eb-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="e11eb-122">Przykład Procesora CPU: Wykonywanie obliczeń dla gier</span><span class="sxs-lookup"><span data-stu-id="e11eb-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="e11eb-123">Załóżmy, że piszesz grę mobilną, w którym naciśnięcie przycisku mogą skutkować szkody w wielu nieprzyjaciół na ekranie.</span><span class="sxs-lookup"><span data-stu-id="e11eb-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="e11eb-124">Wykonywanie obliczeń szkody może być kosztowne i to zrobić w wątku interfejsu użytkownika czyniłyby gry, są wyświetlane wstrzymania, ponieważ obliczenie jest wykonywane!</span><span class="sxs-lookup"><span data-stu-id="e11eb-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="e11eb-125">Najlepszym sposobem na to obsługa jest uruchomienie wątku w tle, która obsługuje pracę przy użyciu `Task.Run`, i `await` jego wynik.</span><span class="sxs-lookup"><span data-stu-id="e11eb-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="e11eb-126">Umożliwi to interfejsu użytkownika możesz bezproblemowe, ponieważ praca jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="e11eb-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="e11eb-127">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="e11eb-127">And that's it!</span></span>  <span data-ttu-id="e11eb-128">Ten kod nie pozostawia żadnych śladów wyraża celem Zdarzenie kliknięcia przycisku, nie wymaga ręcznego zarządzania wątku w tle i odbywa się to w taki sposób, bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="e11eb-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="e11eb-129">Co się dzieje w tle</span><span class="sxs-lookup"><span data-stu-id="e11eb-129">What happens under the covers</span></span>

<span data-ttu-id="e11eb-130">Istnieje wiele przenoszenie fragmentów, których dotyczy operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="e11eb-131">Jeśli masz zastanawiasz się, co się dzieje w obiekcie nadrzędnym `Task` i `Task<T>`, wyewidencjonowania [Async szczegółowe](../standard/async-in-depth.md) artykuł, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="e11eb-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="e11eb-132">C# po stronie rzeczy, kompilator przekształca kodu w automacie stanów, która przechowuje informacje o elementów, takich jak wykonanie reaguje po `await` jest osiągnął i wznawianie wykonywanie po zakończeniu zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="e11eb-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="e11eb-133">W przypadku teoretycznie pochylone, jest implementacją [modelu Promise asynchroniczności](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="e11eb-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="e11eb-134">Kluczowych elementów, aby zrozumieć</span><span class="sxs-lookup"><span data-stu-id="e11eb-134">Key Pieces to Understand</span></span>

*   <span data-ttu-id="e11eb-135">Kod asynchroniczny może służyć do kodu I/O-powiązane z i od Procesora CPU, ale inaczej dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="e11eb-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="e11eb-136">Kod asynchroniczny używa `Task<T>` i `Task`, służą do konstrukcji używanych do modelu wykonywanej pracy w tle.</span><span class="sxs-lookup"><span data-stu-id="e11eb-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="e11eb-137">`async` — Słowo kluczowe jest przekształcany metody metody asynchronicznej, która pozwala na używanie `await` — słowo kluczowe w jej treści.</span><span class="sxs-lookup"><span data-stu-id="e11eb-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="e11eb-138">Gdy `await` — słowo kluczowe jest stosowana, co wstrzymuje wywoływania metody i przekazuje sterowanie do obiektu wywołującego aż oczekiwane zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="e11eb-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="e11eb-139">`await` należy używać tylko wewnątrz metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="e11eb-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="e11eb-140">Rozpoznaje pracy Procesora CPU i czy/Wy — powiązane z</span><span class="sxs-lookup"><span data-stu-id="e11eb-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="e11eb-141">Pierwszych dwóch przykładach w tym przewodniku pokazano, jak można użyć `async` i `await` do pracy I/O-granicę i zależne od Procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="e11eb-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="e11eb-142">Jego klucza, który można go zidentyfikować zadanie należy wykonać I/O-granicę lub zależne od Procesora CPU, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie doprowadzić do niewłaściwie niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="e11eb-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="e11eb-143">Poniżej przedstawiono dwa pytań, na które należy zapytać przed napisaniem jakiegokolwiek kodu:</span><span class="sxs-lookup"><span data-stu-id="e11eb-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="e11eb-144">Będzie Twój kod można "oczekiwanie" coś, takich jak dane z bazy danych?</span><span class="sxs-lookup"><span data-stu-id="e11eb-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="e11eb-145">Jeśli Twoja odpowiedź to "yes", a następnie praca jest **I/O-powiązane z**.</span><span class="sxs-lookup"><span data-stu-id="e11eb-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="e11eb-146">Będzie Twój kod wykonywać bardzo kosztowna obliczeń?</span><span class="sxs-lookup"><span data-stu-id="e11eb-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="e11eb-147">Jeśli odpowiedzi na "tak", a następnie praca jest **zależne od Procesora CPU**.</span><span class="sxs-lookup"><span data-stu-id="e11eb-147">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="e11eb-148">W przypadku pracy, masz **I/O-powiązane z**, użyj `async` i `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="e11eb-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="e11eb-149">Możesz *nie powinien* Użyj Biblioteka zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="e11eb-150">Przyczyną jest opisany w [asynchronicznych w artykule głębokość](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="e11eb-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="e11eb-151">W przypadku pracy, masz **zależne od Procesora CPU** i interesujące Cię czas reakcji, użyj `async` i `await` , ale zduplikować pracy w innym wątku *z* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="e11eb-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="e11eb-152">Jeżeli praca jest odpowiednia dla współbieżność i równoległości, należy również rozważyć użycie [Biblioteka zadań równoległych](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="e11eb-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="e11eb-153">Ponadto należy zawsze zmierzyć wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="e11eb-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="e11eb-154">Na przykład można znaleźć samodzielnie w sytuacji, gdy Twoje zadań intensywnie angażujących Procesor nie jest kosztowna wystarczająco w porównaniu z obciążeniem przełączeń kontekstu po wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="e11eb-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="e11eb-155">Każdy element ma jego kosztem i należy wybrać poprawny kosztem w danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="e11eb-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="e11eb-156">Więcej przykładów</span><span class="sxs-lookup"><span data-stu-id="e11eb-156">More Examples</span></span>

<span data-ttu-id="e11eb-157">W poniższych przykładach pokazano różne sposoby, które można napisać kod asynchroniczny w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e11eb-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="e11eb-158">Obejmują one kilka różnych scenariuszy, które mogą pochodzić między.</span><span class="sxs-lookup"><span data-stu-id="e11eb-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="e11eb-159">Wyodrębnianie danych z sieci</span><span class="sxs-lookup"><span data-stu-id="e11eb-159">Extracting Data from a Network</span></span>

<span data-ttu-id="e11eb-160">Ten fragment kodu pobiera kod HTML na stronie głównej w [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza liczbę razy występuje w ciągu ".NET" w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="e11eb-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="e11eb-161">Aby zdefiniować metodę kontrolera sieci web, która wykonuje to zadanie, zwracając liczbę używa platformy ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="e11eb-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="e11eb-162">Jeśli planujesz sposób analizowania w środowisku produkcyjnym kod HTML, nie należy używać wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="e11eb-163">Zamiast tego użyj biblioteki analizy.</span><span class="sxs-lookup"><span data-stu-id="e11eb-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="e11eb-164">Oto ten sam scenariusz napisane dla uniwersalnych aplikacji Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:</span><span class="sxs-lookup"><span data-stu-id="e11eb-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="e11eb-165">Oczekiwanie na wykonanie wielu zadań</span><span class="sxs-lookup"><span data-stu-id="e11eb-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="e11eb-166">Może się okazać się w sytuacji, w których trzeba pobrać jednocześnie wiele fragmentów danych.</span><span class="sxs-lookup"><span data-stu-id="e11eb-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="e11eb-167">`Task` Interfejs API zawiera dwie metody `Task.WhenAll` i `Task.WhenAny` umożliwiają pisania kodu asynchronicznego, który wykonuje oczekiwania bez blokowania na wiele zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="e11eb-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="e11eb-168">Ten przykład przedstawia, jak może uzyskać `User` danych dla zestawu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="e11eb-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="e11eb-169">Oto inny sposób zapisu to nieco bardziej zwięzły, za pomocą LINQ:</span><span class="sxs-lookup"><span data-stu-id="e11eb-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="e11eb-170">Chociaż mniejszej ilości kodu, należy szczególnie uważać podczas mieszania LINQ z kodu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="e11eb-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="e11eb-171">Ponieważ LINQ używa odroczonego wykonania (z opóźnieniem), wywołania asynchroniczne nie nastąpi natychmiastowe tak, jak w `foreach()` pętli, chyba że wymusić wygenerowanego sekwencji do iteracji z wywołaniem `.ToList()` lub `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="e11eb-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="e11eb-172">Ważne informacje i opinie</span><span class="sxs-lookup"><span data-stu-id="e11eb-172">Important Info and Advice</span></span>

<span data-ttu-id="e11eb-173">Mimo że programowanie async jest stosunkowo prosta, istnieje kilka szczegółów, o których należy pamiętać o tym, co może uniemożliwić nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e11eb-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="e11eb-174">`async` **metody musi być** `await` **— słowo kluczowe w treści lub nigdy nie przyniesie!**</span><span class="sxs-lookup"><span data-stu-id="e11eb-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="e11eb-175">Jest to ważne, które należy uwzględnić.</span><span class="sxs-lookup"><span data-stu-id="e11eb-175">This is important to keep in mind.</span></span>  <span data-ttu-id="e11eb-176">Jeśli `await` nie jest używany w treści `async` metody, C# kompilatora zostanie wygenerowane ostrzeżenie, ale będzie kodu, skompiluj i uruchom tak, jakby była normalnym metody.</span><span class="sxs-lookup"><span data-stu-id="e11eb-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="e11eb-177">Należy pamiętać, że również byłoby bardzo mało wydajne jako automatu stanów, generowane przez kompilator języka C# dla metody asynchronicznej będzie nie być wykonywania niczego.</span><span class="sxs-lookup"><span data-stu-id="e11eb-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="e11eb-178">**Jako sufiks co nazwa metody async, którą piszesz, należy dodać "Async".**</span><span class="sxs-lookup"><span data-stu-id="e11eb-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="e11eb-179">Jest to Konwencji używany na platformie .NET do łatwiej odróżnienia synchroniczne i asynchroniczne metody.</span><span class="sxs-lookup"><span data-stu-id="e11eb-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="e11eb-180">Pamiętaj, że niektóre metody, które nie są jawnie wywołane przez kod (np. programy obsługi zdarzeń lub metody kontrolera sieci web), niekoniecznie nie mają zastosowania.</span><span class="sxs-lookup"><span data-stu-id="e11eb-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="e11eb-181">Ponieważ te nie są jawnie wywoływane przez kod, są wyraźnie ich nazw nie jest ważne.</span><span class="sxs-lookup"><span data-stu-id="e11eb-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="e11eb-182">`async void` **powinna służyć wyłącznie do obsługi zdarzeń.**</span><span class="sxs-lookup"><span data-stu-id="e11eb-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="e11eb-183">`async void` jest to jedyny sposób, aby umożliwić procedury obsługi zdarzeń asynchronicznych do pracy, ponieważ nie są zwracane typy zdarzeń (dlatego nie może wprowadzać użytkowania `Task` i `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="e11eb-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="e11eb-184">Użycie `async void` nie jest zgodna z modelem wzorca TAP i może stanowić wyzwanie, użycia, taki jak:</span><span class="sxs-lookup"><span data-stu-id="e11eb-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="e11eb-185">Wyjątki zgłaszane w `async void` metoda nie może zostać przechwycony spoza tej metody.</span><span class="sxs-lookup"><span data-stu-id="e11eb-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="e11eb-186">`async void` metody są bardzo trudne do testowania.</span><span class="sxs-lookup"><span data-stu-id="e11eb-186">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="e11eb-187">`async void` metody może spowodować nieprawidłowe efekty uboczne, jeśli obiekt wywołujący nie jest oczekiwana musiały być asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="e11eb-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="e11eb-188">**Bieżnika dokładnie przy użyciu asynchroniczne lambda w wyrażeniach zapytań LINQ**</span><span class="sxs-lookup"><span data-stu-id="e11eb-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="e11eb-189">Wyrażenia lambda w języku LINQ stosować odroczone wykonania, znaczenia kodu może się okazać, wykonywanie w czasie, gdy nie spodziewasz się.</span><span class="sxs-lookup"><span data-stu-id="e11eb-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="e11eb-190">Wprowadzenie blokujących zadania do tego łatwo może spowodować zakleszczenie, jeśli nie jest prawidłowo zapisywane.</span><span class="sxs-lookup"><span data-stu-id="e11eb-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="e11eb-191">Ponadto zagnieżdżania kodu asynchronicznego w następujący sposób można także utrudnić przeglądanie informacji o wykonania kodu.</span><span class="sxs-lookup"><span data-stu-id="e11eb-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="e11eb-192">Async i LINQ to zaawansowane, ale powinny być używane razem oraz dokładnie wyraźnie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="e11eb-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="e11eb-193">**Pisanie kodu i czeka na zadania w sposób, bez blokowania**</span><span class="sxs-lookup"><span data-stu-id="e11eb-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="e11eb-194">Blokuje bieżący wątek, co oznacza, że oczekiwania na zakończenie zadania może spowodować zakleszczenia i kontekst zablokowanych wątków i może wymagać znacznie bardziej skomplikowane obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="e11eb-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="e11eb-195">Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania z oczekujących zadań w sposób nieblokującej na poziomie:</span><span class="sxs-lookup"><span data-stu-id="e11eb-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="e11eb-196">Użyj polecenia...</span><span class="sxs-lookup"><span data-stu-id="e11eb-196">Use this...</span></span> | <span data-ttu-id="e11eb-197">Zamiast tego...</span><span class="sxs-lookup"><span data-stu-id="e11eb-197">Instead of this...</span></span> | <span data-ttu-id="e11eb-198">Jeśli chcesz to zrobić</span><span class="sxs-lookup"><span data-stu-id="e11eb-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="e11eb-199">`Task.Wait` lub `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="e11eb-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="e11eb-200">Podczas pobierania wyniku zadania w tle</span><span class="sxs-lookup"><span data-stu-id="e11eb-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="e11eb-201">Oczekiwanie na dowolne zadanie do wykonania</span><span class="sxs-lookup"><span data-stu-id="e11eb-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="e11eb-202">Oczekiwanie na ukończenie wszystkich zadań</span><span class="sxs-lookup"><span data-stu-id="e11eb-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="e11eb-203">Oczekiwanie przez pewien czas</span><span class="sxs-lookup"><span data-stu-id="e11eb-203">Waiting for a period of time</span></span> |

*   <span data-ttu-id="e11eb-204">**Pisanie kodu mniej stanowe**</span><span class="sxs-lookup"><span data-stu-id="e11eb-204">**Write less stateful code**</span></span>

<span data-ttu-id="e11eb-205">Nie należy polegać na stan obiektów globalnych lub wykonywanie niektórych metod.</span><span class="sxs-lookup"><span data-stu-id="e11eb-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="e11eb-206">Zamiast tego należy być zależne tylko od wartości zwracane metod.</span><span class="sxs-lookup"><span data-stu-id="e11eb-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="e11eb-207">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="e11eb-207">Why?</span></span>

  *   <span data-ttu-id="e11eb-208">Kod będzie łatwiej przeglądanie informacji o.</span><span class="sxs-lookup"><span data-stu-id="e11eb-208">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="e11eb-209">Kod będzie łatwiejsze testowanie.</span><span class="sxs-lookup"><span data-stu-id="e11eb-209">Code will be easier to test.</span></span>
  *   <span data-ttu-id="e11eb-210">Mieszanie asynchroniczne i synchroniczne kodu jest znacznie łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="e11eb-210">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="e11eb-211">Zazwyczaj można całkowicie uniknąć wyścigu.</span><span class="sxs-lookup"><span data-stu-id="e11eb-211">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="e11eb-212">W zależności od wartości zwracane upraszcza koordynującego kod asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="e11eb-212">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="e11eb-213">(Dodatkowe) działa bardzo dobrze z iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="e11eb-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="e11eb-214">Zalecane dowiesz się, jak osiągnąć pełną lub prawie pełną [referencyjną przezroczystości](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e11eb-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="e11eb-215">To spowoduje w bardzo przewidywalny, zakresie testować i obsługiwać bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="e11eb-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="e11eb-216">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="e11eb-216">Other Resources</span></span>

* <span data-ttu-id="e11eb-217">[Asynchroniczne szczegółowe](../standard/async-in-depth.md) zawiera więcej informacji na temat działania zadania.</span><span class="sxs-lookup"><span data-stu-id="e11eb-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="e11eb-218">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="e11eb-218">Asynchronous programming with async and await (C#)</span></span>](../csharp/programming-guide/concepts/async/index.md)
* <span data-ttu-id="e11eb-219">Lucian Wischik [sześć podpowiedzi podstawowych Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są nagraliście zasobu dla programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="e11eb-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
