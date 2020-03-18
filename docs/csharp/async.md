---
title: 'Programowanie asynchroniczne - C #'
description: Dowiedz się więcej o modelu programowania asynchronicznego na poziomie języka Języka C# dostarczonym przez program .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 38d7c856e9a536db9ef26349175ad440a49f5fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713955"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="72bbb-103">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="72bbb-103">Asynchronous programming</span></span>

<span data-ttu-id="72bbb-104">Jeśli masz jakiekolwiek potrzeby związane z we/wy (takie jak żądanie danych z sieci lub uzyskiwanie dostępu do bazy danych), należy korzystać z programowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="72bbb-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="72bbb-105">Można również mieć kod związany z procesorem CPU, takich jak wykonywanie kosztownych obliczeń, który jest również dobrym scenariuszem do pisania kodu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="72bbb-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="72bbb-106">C# ma model programowania asynchronicznego na poziomie języka, który umożliwia łatwe pisanie kodu asynchronicznego bez konieczności żonglowania wywołaniami zwrotu lub zgodne z biblioteki, która obsługuje asynchrony.</span><span class="sxs-lookup"><span data-stu-id="72bbb-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="72bbb-107">Wynika to z tego, co jest znane jako [asynchroniczny wzorzec oparty na zadaniach (TAP).](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)</span><span class="sxs-lookup"><span data-stu-id="72bbb-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="72bbb-108">Podstawowy przegląd modelu asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="72bbb-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="72bbb-109">Rdzeń programowania asynchronicznego `Task` jest `Task<T>` i obiektów, które modelują operacje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="72bbb-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="72bbb-110">Są one obsługiwane `async` przez `await` słowa kluczowe i.</span><span class="sxs-lookup"><span data-stu-id="72bbb-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="72bbb-111">Model jest dość prosty w większości przypadków:</span><span class="sxs-lookup"><span data-stu-id="72bbb-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="72bbb-112">W `await` przypadku kodu związanego we/wy można `Task` `Task<T>` operacji, `async` która zwraca lub wewnątrz metody.</span><span class="sxs-lookup"><span data-stu-id="72bbb-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="72bbb-113">Dla kodu powiązanego `await` z procesorem CPU, operacja, `Task.Run` która jest uruchamiana w wątku w tle z metodą.</span><span class="sxs-lookup"><span data-stu-id="72bbb-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="72bbb-114">Słowo `await` kluczowe to miejsce, w którym dzieje się magia.</span><span class="sxs-lookup"><span data-stu-id="72bbb-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="72bbb-115">Daje kontrolę do obiektu wywołującego metody, która została wykonana `await`, a ostatecznie umożliwia interfejsu użytkownika, aby być elastyczne lub usługi, które mają być elastyczne.</span><span class="sxs-lookup"><span data-stu-id="72bbb-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="72bbb-116">Istnieją inne sposoby podejścia do `async` kodu `await` asynchronicznego niż i opisane w artykule TAP połączonym powyżej, ale ten dokument skupi się na konstrukcjach na poziomie języka od tego momentu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="72bbb-117">Przykład związany z we/wy: pobieranie danych z usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="72bbb-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="72bbb-118">Może być konieczne pobranie niektórych danych z usługi sieci web po naciśnięciu przycisku, ale nie chcesz blokować wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="72bbb-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="72bbb-119">Można to osiągnąć po prostu tak:</span><span class="sxs-lookup"><span data-stu-id="72bbb-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="72bbb-120">To wszystko!</span><span class="sxs-lookup"><span data-stu-id="72bbb-120">And that’s it!</span></span> <span data-ttu-id="72bbb-121">Kod wyraża intencji (pobieranie niektórych danych asynchronicznie) bez ugrzęznąć w interakcji z Task obiektów.</span><span class="sxs-lookup"><span data-stu-id="72bbb-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="72bbb-122">Przykład związany z procesorem CPU: wykonywanie obliczeń dla gry</span><span class="sxs-lookup"><span data-stu-id="72bbb-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="72bbb-123">Załóżmy, że piszesz grę mobilną, w której naciśnięcie przycisku może zadać obrażenia wielu wrogom na ekranie.</span><span class="sxs-lookup"><span data-stu-id="72bbb-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="72bbb-124">Wykonanie obliczeń uszkodzeń może być kosztowne, a wykonanie tego w wątku interfejsu użytkownika sprawi, że gra będzie pauzować podczas wykonywania obliczeń!</span><span class="sxs-lookup"><span data-stu-id="72bbb-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="72bbb-125">Najlepszym sposobem radzenia sobie z tym jest rozpoczęcie wątku w tle, który wykonuje pracę przy użyciu `Task.Run`, i `await` jego wynik.</span><span class="sxs-lookup"><span data-stu-id="72bbb-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="72bbb-126">Pozwoli to interfejsu, aby czuć się gładko, jak praca jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="72bbb-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="72bbb-127">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="72bbb-127">And that's it!</span></span>  <span data-ttu-id="72bbb-128">Ten kod czysto wyraża intencji przycisku click zdarzenia, nie wymaga ręcznego zarządzania wątku w tle i robi to w sposób nieblokujący.</span><span class="sxs-lookup"><span data-stu-id="72bbb-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="72bbb-129">Co dzieje się pod przykrywką</span><span class="sxs-lookup"><span data-stu-id="72bbb-129">What happens under the covers</span></span>

<span data-ttu-id="72bbb-130">Istnieje wiele ruchomych elementów, w których chodzi o operacje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="72bbb-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="72bbb-131">Jeśli jesteś ciekaw tego, co dzieje się `Task` pod `Task<T>`okładkami i , checkout [Async pogłębiony](../standard/async-in-depth.md) artykuł, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="72bbb-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="72bbb-132">Po stronie Języka C# rzeczy kompilator przekształca kod na komputerze stanu, który śledzi `await` rzeczy, takie jak wydajność wykonywania po osiągnięciu i wznowienie wykonywania po zakończeniu zadania w tle.</span><span class="sxs-lookup"><span data-stu-id="72bbb-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="72bbb-133">Dla teoretycznie skłonnych jest to realizacja [modelu Promise asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="72bbb-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="72bbb-134">Kluczowe elementy do zrozumienia</span><span class="sxs-lookup"><span data-stu-id="72bbb-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="72bbb-135">Kod asynchronicznego może służyć zarówno dla kodu związanego we/wy i powiązanego z procesorem CPU, ale inaczej dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="72bbb-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="72bbb-136">Async kod `Task<T>` `Task`używa i , które są konstrukcje używane do modelu pracy wykonywanej w tle.</span><span class="sxs-lookup"><span data-stu-id="72bbb-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="72bbb-137">Słowo `async` kluczowe zamienia metodę w metodę asynchroniczną, która umożliwia użycie słowa kluczowego `await` w jego treści.</span><span class="sxs-lookup"><span data-stu-id="72bbb-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="72bbb-138">Po `await` zastosowaniu słowa kluczowego, zawiesza metodę wywołującą i daje kontrolę z powrotem do obiektu wywołującego, dopóki nie zostanie ukończone oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="72bbb-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="72bbb-139">`await`można używać tylko wewnątrz metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="72bbb-139">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="72bbb-140">Rozpoznawanie pracy związanej z procesorem CPU i związaną z we/wy</span><span class="sxs-lookup"><span data-stu-id="72bbb-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="72bbb-141">Pierwsze dwa przykłady tego przewodnika pokazały, `async` `await` jak można używać i do pracy związanej z we/wy i procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="72bbb-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="72bbb-142">Jest to klucz, który można zidentyfikować, gdy zadanie, które należy wykonać jest we/w-bound lub cpu-bound, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie prowadzić do nadużywania niektórych konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="72bbb-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="72bbb-143">Oto dwa pytania, które należy zadać przed napisaniem kodu:</span><span class="sxs-lookup"><span data-stu-id="72bbb-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="72bbb-144">Czy twój kod będzie "czekał" na coś, na przykład dane z bazy danych?</span><span class="sxs-lookup"><span data-stu-id="72bbb-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="72bbb-145">Jeśli odpowiedź brzmi "tak", twoja praca jest **związana z we/wy.**</span><span class="sxs-lookup"><span data-stu-id="72bbb-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="72bbb-146">Czy twój kod będzie wykonywać bardzo kosztowne obliczenia?</span><span class="sxs-lookup"><span data-stu-id="72bbb-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="72bbb-147">Jeśli odpowiedziałeś "tak", twoja praca jest **związana z procesorem**.</span><span class="sxs-lookup"><span data-stu-id="72bbb-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="72bbb-148">Jeśli praca, którą masz jest i `async` / `await` **O-bound**, używać i *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="72bbb-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="72bbb-149">*Nie należy* używać biblioteki równoległej zadania.</span><span class="sxs-lookup"><span data-stu-id="72bbb-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="72bbb-150">Przyczyna tego jest opisana [w artykule Async in Depth](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="72bbb-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="72bbb-151">Jeśli praca masz jest **związany z procesorem CPU** `async` i `await` zależy Ci na responsywność, używać i ale tarło pracy off na inny wątek *z* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="72bbb-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="72bbb-152">Jeśli praca jest odpowiednia dla współbieżności i równoległości, należy również rozważyć użycie [biblioteki równoległej zadania](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="72bbb-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="72bbb-153">Ponadto należy zawsze mierzyć wykonanie kodu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="72bbb-154">Na przykład może znaleźć się w sytuacji, gdy praca związana z procesorem CPU nie jest wystarczająco kosztowne w porównaniu z obciążeniem przełączników kontekstu podczas wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="72bbb-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="72bbb-155">Każdy wybór ma swój kompromis i powinieneś wybrać właściwy kompromis dla swojej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="72bbb-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="72bbb-156">Więcej przykładów</span><span class="sxs-lookup"><span data-stu-id="72bbb-156">More Examples</span></span>

<span data-ttu-id="72bbb-157">W poniższych przykładach przedstawiono różne sposoby pisania kodu asynchronicznego w języku C#.</span><span class="sxs-lookup"><span data-stu-id="72bbb-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="72bbb-158">Obejmują one kilka różnych scenariuszy, na które możesz się natknąć.</span><span class="sxs-lookup"><span data-stu-id="72bbb-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="72bbb-159">Wyodrębnianie danych z sieci</span><span class="sxs-lookup"><span data-stu-id="72bbb-159">Extracting Data from a Network</span></span>

<span data-ttu-id="72bbb-160">Ten fragment kodu pobiera kod HTML ze strony głównej w [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza, ile razy ciąg ".NET" występuje w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="72bbb-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="72bbb-161">Używa ASP.NET MVC do definiowania metody kontrolera sieci web, która wykonuje to zadanie, zwracając numer.</span><span class="sxs-lookup"><span data-stu-id="72bbb-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="72bbb-162">Jeśli planujesz analizowanie kodu HTML w kodzie produkcyjnym, nie używaj wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="72bbb-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="72bbb-163">Zamiast tego użyj biblioteki analizy.</span><span class="sxs-lookup"><span data-stu-id="72bbb-163">Use a parsing library instead.</span></span>

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

<span data-ttu-id="72bbb-164">Oto ten sam scenariusz napisany dla uniwersalnej aplikacji systemu Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:</span><span class="sxs-lookup"><span data-stu-id="72bbb-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="72bbb-165">Oczekiwanie na wykonanie wielu zadań</span><span class="sxs-lookup"><span data-stu-id="72bbb-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="72bbb-166">Może się okazać, że znajdujesz się w sytuacji, w której musisz pobrać wiele fragmentów danych jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="72bbb-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="72bbb-167">Interfejs `Task` API zawiera dwie `Task.WhenAll` `Task.WhenAny` metody i które umożliwiają pisanie kodu asynchronicznego, który wykonuje nieblokujące oczekiwanie na wiele zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="72bbb-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="72bbb-168">W tym przykładzie pokazano, jak można pobrać `User` dane dla zestawu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="72bbb-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="72bbb-169">Oto inny sposób, aby napisać to nieco bardziej zwięźle, za pomocą LINQ:</span><span class="sxs-lookup"><span data-stu-id="72bbb-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="72bbb-170">Mimo że jest mniej kodu, należy uważać podczas mieszania LINQ z kodem asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="72bbb-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="72bbb-171">Ponieważ LINQ używa odroczonego (opóźnienie) wykonanie, wywołania asynchroniczne `foreach()` nie nastąpi natychmiast, jak to zrobić w pętli, `.ToList()` `.ToArray()`chyba że wymusić wygenerowaną sekwencję do iterate z wywołania lub .</span><span class="sxs-lookup"><span data-stu-id="72bbb-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="72bbb-172">Ważne informacje i porady</span><span class="sxs-lookup"><span data-stu-id="72bbb-172">Important Info and Advice</span></span>

<span data-ttu-id="72bbb-173">Mimo że programowanie asynchroniczne jest stosunkowo proste, istnieją pewne szczegóły, o których należy pamiętać, które mogą zapobiec nieoczekiwanemu zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="72bbb-174">`async`**metody muszą mieć słowo** `await` **kluczowe w swoim ciele lub nigdy nie poddadzą!**</span><span class="sxs-lookup"><span data-stu-id="72bbb-174">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="72bbb-175">Jest to ważne, aby pamiętać.</span><span class="sxs-lookup"><span data-stu-id="72bbb-175">This is important to keep in mind.</span></span>  <span data-ttu-id="72bbb-176">Jeśli `await` nie jest używany w `async` treści metody, kompilator C# wygeneruje ostrzeżenie, ale kod skompilują i uruchomi się tak, jakby była to metoda normalna.</span><span class="sxs-lookup"><span data-stu-id="72bbb-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="72bbb-177">Należy zauważyć, że będzie to również bardzo nieefektywne, jak komputer stanu generowane przez kompilator C# dla metody asynchronicznej nie będzie wykonywanie niczego.</span><span class="sxs-lookup"><span data-stu-id="72bbb-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* <span data-ttu-id="72bbb-178">**Należy dodać "Async" jako sufiks każdej nazwy metody asynchronicznej, którą piszesz.**</span><span class="sxs-lookup"><span data-stu-id="72bbb-178">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="72bbb-179">Jest to konwencja używana w .NET do łatwiejszego rozróżniania metod synchronicznych i asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="72bbb-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="72bbb-180">Należy zauważyć, że niektóre metody, które nie są jawnie wywoływane przez kod (takie jak programy obsługi zdarzeń lub metody kontrolera sieci web) nie koniecznie mają zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="72bbb-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="72bbb-181">Ponieważ nie są one jawnie wywoływane przez kod, jest jawne o ich nazewnictwa nie jest tak ważne.</span><span class="sxs-lookup"><span data-stu-id="72bbb-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* <span data-ttu-id="72bbb-182">`async void`**powinny być używane tylko dla programów obsługi zdarzeń.**</span><span class="sxs-lookup"><span data-stu-id="72bbb-182">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="72bbb-183">`async void`jest jedynym sposobem, aby umożliwić asynchroniczne programy obsługi zdarzeń do pracy, `Task` ponieważ `Task<T>`zdarzenia nie mają typów zwracanych (w związku z tym nie można użyć i ).</span><span class="sxs-lookup"><span data-stu-id="72bbb-183">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="72bbb-184">Jakiekolwiek inne `async void` użycie nie jest zgodne z modelem TAP i może być trudne w użyciu, takie jak:</span><span class="sxs-lookup"><span data-stu-id="72bbb-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="72bbb-185">Wyjątki generowane `async void` w metodzie nie można przechwycić poza tą metodą.</span><span class="sxs-lookup"><span data-stu-id="72bbb-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* <span data-ttu-id="72bbb-186">`async void`metody są bardzo trudne do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="72bbb-186">`async void` methods are very difficult to test.</span></span>
* <span data-ttu-id="72bbb-187">`async void`metody mogą powodować złe skutki uboczne, jeśli obiekt wywołujący nie oczekuje ich async.</span><span class="sxs-lookup"><span data-stu-id="72bbb-187">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* <span data-ttu-id="72bbb-188">**Ostrożnie bieżnika podczas korzystania lambdas async w wyrażeniach LINQ**</span><span class="sxs-lookup"><span data-stu-id="72bbb-188">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="72bbb-189">Wyrażenia Lambda w LINQ używać odroczonego wykonania, co oznacza, że kod może skończyć się wykonywanie w czasie, gdy nie oczekujesz go.</span><span class="sxs-lookup"><span data-stu-id="72bbb-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="72bbb-190">Wprowadzenie blokowania zadań w tym może łatwo spowodować zakleszczenie, jeśli nie jest poprawnie napisane.</span><span class="sxs-lookup"><span data-stu-id="72bbb-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="72bbb-191">Ponadto zagnieżdżanie kodu asynchronicznego, takie jak to może również utrudnić powodowanie dotyczące wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="72bbb-192">Async i LINQ są potężne, ale powinny być używane razem tak dokładnie i wyraźnie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="72bbb-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="72bbb-193">**Napisz kod, który czeka na zadania w sposób nieblokujący**</span><span class="sxs-lookup"><span data-stu-id="72bbb-193">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="72bbb-194">Blokowanie bieżącego wątku jako środek oczekiwania na zakończenie zadania może spowodować zakleszczenia i zablokowane wątki kontekstu i może wymagać znacznie bardziej złożonych obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="72bbb-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="72bbb-195">Poniższa tabela zawiera wskazówki dotyczące sposobu radzenia sobie z oczekiwaniami na zadania w sposób nieblokujący:</span><span class="sxs-lookup"><span data-stu-id="72bbb-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="72bbb-196">Użyj polecenia...</span><span class="sxs-lookup"><span data-stu-id="72bbb-196">Use this...</span></span> | <span data-ttu-id="72bbb-197">Zamiast tego...</span><span class="sxs-lookup"><span data-stu-id="72bbb-197">Instead of this...</span></span> | <span data-ttu-id="72bbb-198">Chcąc to zrobić</span><span class="sxs-lookup"><span data-stu-id="72bbb-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="72bbb-199">`Task.Wait` lub `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="72bbb-199">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="72bbb-200">Pobieranie wyniku zadania w tle</span><span class="sxs-lookup"><span data-stu-id="72bbb-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="72bbb-201">Oczekiwanie na wykonanie dowolnego zadania</span><span class="sxs-lookup"><span data-stu-id="72bbb-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="72bbb-202">Oczekiwanie na wykonanie wszystkich zadań</span><span class="sxs-lookup"><span data-stu-id="72bbb-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="72bbb-203">Oczekiwanie na okres czasu</span><span class="sxs-lookup"><span data-stu-id="72bbb-203">Waiting for a period of time</span></span> |

* <span data-ttu-id="72bbb-204">**Napisz mniej stanowy kod**</span><span class="sxs-lookup"><span data-stu-id="72bbb-204">**Write less stateful code**</span></span>

<span data-ttu-id="72bbb-205">Nie zależą od stanu obiektów globalnych lub wykonywania niektórych metod.</span><span class="sxs-lookup"><span data-stu-id="72bbb-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="72bbb-206">Zamiast tego zależy tylko od zwracanych wartości metod.</span><span class="sxs-lookup"><span data-stu-id="72bbb-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="72bbb-207">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="72bbb-207">Why?</span></span>

* <span data-ttu-id="72bbb-208">Kod będzie łatwiejrozdać do rozumu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="72bbb-209">Kod będzie łatwiejszy do przetestowania.</span><span class="sxs-lookup"><span data-stu-id="72bbb-209">Code will be easier to test.</span></span>
* <span data-ttu-id="72bbb-210">Mieszanie kodu asynchronicznego i synchronicznego jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="72bbb-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="72bbb-211">Zazwyczaj można całkowicie uniknąć warunków wyścigu.</span><span class="sxs-lookup"><span data-stu-id="72bbb-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="72bbb-212">W zależności od wartości zwracane sprawia, że koordynacja kodu asynchronicznego jest prosta.</span><span class="sxs-lookup"><span data-stu-id="72bbb-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="72bbb-213">(Bonus) to działa naprawdę dobrze z zastrzykiem zależności.</span><span class="sxs-lookup"><span data-stu-id="72bbb-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="72bbb-214">Zalecanym celem jest osiągnięcie pełnej lub prawie pełnej [przezroczystości referencyjnej](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie.</span><span class="sxs-lookup"><span data-stu-id="72bbb-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="72bbb-215">Spowoduje to niezwykle przewidywalne, sprawdzalne i możliwe do utrzymania codebase.</span><span class="sxs-lookup"><span data-stu-id="72bbb-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="72bbb-216">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="72bbb-216">Other Resources</span></span>

* <span data-ttu-id="72bbb-217">[Async w głębi](../standard/async-in-depth.md) zapewnia więcej informacji na temat działania zadań.</span><span class="sxs-lookup"><span data-stu-id="72bbb-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="72bbb-218">Asynchroniczne programowanie z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="72bbb-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="72bbb-219">Lucian Wischik's [Six Essential Porady dla Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są wspaniałym źródłem programowania async</span><span class="sxs-lookup"><span data-stu-id="72bbb-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
