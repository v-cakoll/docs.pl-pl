---
title: Programowanie asynchroniczne
description: "Więcej informacji na temat języka C# poziom języka asynchroniczne modelu programowania udostępniane przez oprogramowanie .NET Core."
keywords: .NET, .NET core
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 35038b3dae80958071a9615f7f131fca73513077
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2017
---
# <a name="asynchronous-programming"></a><span data-ttu-id="0e802-104">Programowanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="0e802-104">Asynchronous programming</span></span>

<span data-ttu-id="0e802-105">Jeśli masz żadnych potrzeb I/E-granica (na przykład żąda danych od sieci lub uzyskiwania dostępu do bazy danych), należy wykorzystać programowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="0e802-105">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="0e802-106">Można również mieć kodu procesora, takich jak przeprowadzanie obliczeń kosztowne, która jest również dobrym scenariusz dotyczące pisania kodu async.</span><span class="sxs-lookup"><span data-stu-id="0e802-106">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="0e802-107">C# ma poziom języka asynchronicznego programowania modelu, który umożliwia łatwe pisanie kodu asynchroniczne bez konieczności łatwiejszą obsługę wywołań zwrotnych lub odpowiadają bibliotekę, która obsługuje asynchrony.</span><span class="sxs-lookup"><span data-stu-id="0e802-107">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="0e802-108">Wynika, co jest nazywane [opartego na zadaniach asynchronicznej wzorca (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span><span class="sxs-lookup"><span data-stu-id="0e802-108">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="0e802-109">Omówienie modelu asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="0e802-109">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="0e802-110">Podstawowe programowania asynchronicznego są `Task` i `Task<T>` obiektów, które modelu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="0e802-110">The core of async programming are the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="0e802-111">Są one obsługiwane przez `async` i `await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="0e802-111">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="0e802-112">Model jest dość proste, w większości przypadków:</span><span class="sxs-lookup"><span data-stu-id="0e802-112">The model is fairly simple in most cases:</span></span> 

<span data-ttu-id="0e802-113">Dla kodu I/E-powiązane z możesz `await` operacji, która zwraca `Task` lub `Task<T>` wewnątrz `async` metody.</span><span class="sxs-lookup"><span data-stu-id="0e802-113">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="0e802-114">Kod, procesora użytkownik `await` operacji, która została uruchomiona w wątku w tle z `Task.Run` metody.</span><span class="sxs-lookup"><span data-stu-id="0e802-114">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="0e802-115">`await` — Słowo kluczowe jest, gdzie się stanie magic.</span><span class="sxs-lookup"><span data-stu-id="0e802-115">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="0e802-116">Go daje sterowania do obiektu wywołującego metody, która jest wykonywana `await`, i ostatecznie umożliwia interfejsu użytkownika, aby odpowiadać lub usługi jest elastyczny.</span><span class="sxs-lookup"><span data-stu-id="0e802-116">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="0e802-117">Istnieją inne sposoby metody asynchronicznej kodu niż `async` i `await` opisane w artykule NACIŚNIJ linki umieszczono powyżej, ale ten dokument koncentruje się na konstrukcji poziom języka od tego momentu.</span><span class="sxs-lookup"><span data-stu-id="0e802-117">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="0e802-118">Przykład I/E-granica: pobieranie danych z usługi sieci web</span><span class="sxs-lookup"><span data-stu-id="0e802-118">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="0e802-119">Konieczne może być pobrać niektóre dane z usługi sieci web po naciśnięciu przycisku, ale nie chcesz zablokować wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0e802-119">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="0e802-120">Można go zrobić po prostu w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0e802-120">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="0e802-121">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="0e802-121">And that’s it!</span></span> <span data-ttu-id="0e802-122">Kod odzwierciedla cele (pobieranie niektóre dane asynchronicznie) bez ugrzęźnięcia w interakcji z obiektami zadań.</span><span class="sxs-lookup"><span data-stu-id="0e802-122">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="0e802-123">Przykład procesora: Przeprowadzanie obliczeń na gry</span><span class="sxs-lookup"><span data-stu-id="0e802-123">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="0e802-124">Powiedz pisania przenośnych grę, gdzie naciśnięcie przycisku może spowodować uszkodzenia na wiele wrogów na ekranie.</span><span class="sxs-lookup"><span data-stu-id="0e802-124">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="0e802-125">Wykonywanie obliczeń uszkodzenia może być kosztowne i to zrobić w wątku interfejsu użytkownika spowodowałoby gry są wyświetlane wstrzymania zgodnie z wykonaniem obliczeń!</span><span class="sxs-lookup"><span data-stu-id="0e802-125">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="0e802-126">Najlepszym sposobem obsługi to jest można uruchomić wątku w tle, która obsługuje pracy, przy użyciu `Task.Run`, i `await` wyniku.</span><span class="sxs-lookup"><span data-stu-id="0e802-126">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="0e802-127">Pozwoli to interfejsu użytkownika uznać smooth, jak praca jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="0e802-127">This will allow the UI to feel smooth as the work is being done.</span></span>

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

<span data-ttu-id="0e802-128">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="0e802-128">And that's it!</span></span>  <span data-ttu-id="0e802-129">Ten kod prawidłowo wyraża celem Zdarzenie kliknięcia przycisku, nie wymaga zarządzania ręcznie wątku w tle i kopiuje je w taki sposób, bez blokowania.</span><span class="sxs-lookup"><span data-stu-id="0e802-129">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="0e802-130">Co się stanie w tle</span><span class="sxs-lookup"><span data-stu-id="0e802-130">What happens under the covers</span></span>

<span data-ttu-id="0e802-131">Istnieje wiele części ruchu, gdzie są dane operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="0e802-131">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="0e802-132">Jeśli zastanawiasz się o to, co dzieje się poniżej obejmuje z `Task` i `Task<T>`, wyewidencjonowania [Async szczegółowe](../standard/async-in-depth.md) artykułu, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="0e802-132">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="0e802-133">C# strony rzeczy, kompilator przekształca kodu do automatu stanów, które przechowuje informacje o takich elementów, jak reaguje wykonywania podczas `await` jest wykonanie osiągnęło i wznawianie po zakończeniu zadania tła.</span><span class="sxs-lookup"><span data-stu-id="0e802-133">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="0e802-134">W przypadku teoretycznie pochylone, jest implementacją [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="0e802-134">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="0e802-135">Części klucza, aby zrozumieć</span><span class="sxs-lookup"><span data-stu-id="0e802-135">Key Pieces to Understand</span></span>

*   <span data-ttu-id="0e802-136">Asynchroniczne kodu można użyć dla kodu zarówno I/E-granica i procesora, ale inaczej dla każdego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="0e802-136">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
*   <span data-ttu-id="0e802-137">Asynchroniczne kodzie użyto `Task<T>` i `Task`, konstrukcje używane do modelu wykonywanej pracy w tle, które są.</span><span class="sxs-lookup"><span data-stu-id="0e802-137">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="0e802-138">`async` — Słowo kluczowe włącza metodę do metody asynchronicznej, dzięki czemu można użyć `await` — słowo kluczowe w jego treści.</span><span class="sxs-lookup"><span data-stu-id="0e802-138">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
*   <span data-ttu-id="0e802-139">Gdy `await` — słowo kluczowe jest stosowana, wstrzymuje metody wywołującej i daje formantu do swojego obiektu wywołującego do czasu ukończenia zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="0e802-139">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
*   <span data-ttu-id="0e802-140">`await`można użyć tylko wewnątrz metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="0e802-140">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="0e802-141">Rozpoznaje procesora i I/E-granica pracy</span><span class="sxs-lookup"><span data-stu-id="0e802-141">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="0e802-142">Pierwsze dwa przykłady w tym przewodniku pokazano, jak używasz `async` i `await` pracy I/E-granica i procesora.</span><span class="sxs-lookup"><span data-stu-id="0e802-142">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="0e802-143">Jego klucz, który można zdefiniować zadanie należy wykonać I/E-granicę lub procesora, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie doprowadzić do niewłaściwie korzysta z niektórych konstrukcje.</span><span class="sxs-lookup"><span data-stu-id="0e802-143">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="0e802-144">Poniżej przedstawiono dwa pytań, na które należy poprosić przed przystąpieniem do napisania kodu:</span><span class="sxs-lookup"><span data-stu-id="0e802-144">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="0e802-145">Zostanie kodzie "oczekuje" na coś, takich jak dane z bazy danych?</span><span class="sxs-lookup"><span data-stu-id="0e802-145">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="0e802-146">Jeśli odpowiedź to "yes", a następnie jest pracy **I/E-granica**.</span><span class="sxs-lookup"><span data-stu-id="0e802-146">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="0e802-147">Będzie kodu wykonywać bardzo kosztowna obliczeń?</span><span class="sxs-lookup"><span data-stu-id="0e802-147">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="0e802-148">Jeśli odpowiedzi na "tak", a następnie jest pracy **procesora**.</span><span class="sxs-lookup"><span data-stu-id="0e802-148">If you answered "yes", then your work is **CPU-bound**.</span></span>
    
<span data-ttu-id="0e802-149">Jeśli masz pracy **I/E-granica**, użyj `async` i `await` *bez* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="0e802-149">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="0e802-150">Możesz *nie powinien* Użyj Biblioteka zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="0e802-150">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="0e802-151">Przyczyną tego jest opisane w temacie [asynchronicznych w artykule głębokość](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="0e802-151">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="0e802-152">Jeśli masz pracy **procesora** i interesujących reakcji, użyj `async` i `await` , ale zduplikować pracy w innym wątku *z* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="0e802-152">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="0e802-153">W przypadku potrzeby współbieżności i równoległości pracy, należy również rozważyć użycie Biblioteka zadań równoległych.</span><span class="sxs-lookup"><span data-stu-id="0e802-153">If the work is appropriate for concurrency and parallelism, you should also consider using the Task Parallel Library.</span></span>

<span data-ttu-id="0e802-154">Ponadto należy zawsze pomiarów wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="0e802-154">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="0e802-155">Na przykład może się okazać się w sytuacji, gdy nie jest kosztowna pracy procesora wystarczająco w porównaniu z obciążenie przełączenia kontekstu, gdy wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="0e802-155">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="0e802-156">Każdy element ma jego zależnościami, i należy wybrać prawidłowe zależności dla danej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="0e802-156">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="0e802-157">Więcej przykładów</span><span class="sxs-lookup"><span data-stu-id="0e802-157">More Examples</span></span>

<span data-ttu-id="0e802-158">W poniższych przykładach pokazano różne sposoby, które można napisać kod asynchronicznych w języku C#.</span><span class="sxs-lookup"><span data-stu-id="0e802-158">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="0e802-159">Obejmują one kilku różnych scenariuszy, które może napotkać.</span><span class="sxs-lookup"><span data-stu-id="0e802-159">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="0e802-160">Wyodrębnianie danych z sieci</span><span class="sxs-lookup"><span data-stu-id="0e802-160">Extracting Data from a Network</span></span>

<span data-ttu-id="0e802-161">Ta Wstawka kodu pobiera kod HTML z www.dotnetfoundation.org i oblicza liczbę razy występuje ciąg ".NET" w kodzie HTML.</span><span class="sxs-lookup"><span data-stu-id="0e802-161">This snippet downloads the HTML from www.dotnetfoundation.org and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="0e802-162">Aby zdefiniować metody kontrolera sieci web, która wykonuje to zadanie, zwracając liczbę używa platformy ASP.NET MVC.</span><span class="sxs-lookup"><span data-stu-id="0e802-162">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="0e802-163">Jeśli planujesz wykonanie HTML podczas analizowania w kodzie produkcyjnym, nie należy używać wyrażeń regularnych.</span><span class="sxs-lookup"><span data-stu-id="0e802-163">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="0e802-164">Zamiast tego użyj biblioteki analizy.</span><span class="sxs-lookup"><span data-stu-id="0e802-164">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.DownloadStringAsync("http://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="0e802-165">Oto napisane dla uniwersalnych aplikacji systemu Windows, która wykonuje to samo zadanie, gdy przycisk zostanie naciśnięty sytuacji:</span><span class="sxs-lookup"><span data-stu-id="0e802-165">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("http://www.dotnetfoundation.org");

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

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="0e802-166">Oczekiwanie na ukończenie wielu zadań</span><span class="sxs-lookup"><span data-stu-id="0e802-166">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="0e802-167">Może się okazać się w sytuacji, w których należy pobrać jednocześnie wiele fragmentów danych.</span><span class="sxs-lookup"><span data-stu-id="0e802-167">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="0e802-168">`Task` Interfejs API zawiera dwie metody `Task.WhenAll` i `Task.WhenAny` umożliwiają zapis asynchroniczny kod, który wykonuje nieblokujące oczekiwania na wielu zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="0e802-168">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="0e802-169">W tym przykładzie pokazano, jak może przechwycić `User` danych dla zestawu `userId`s.</span><span class="sxs-lookup"><span data-stu-id="0e802-169">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="0e802-170">Oto innym sposobem zapisu to bardziej krótkiej formie, za pomocą LINQ:</span><span class="sxs-lookup"><span data-stu-id="0e802-170">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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
<span data-ttu-id="0e802-171">Chociaż jest mniejsza ilość kodu, Zachowaj ostrożność podczas mieszanie LINQ z kodem asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0e802-171">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="0e802-172">Ponieważ LINQ używa odroczonego wykonania (lazy), wywołania asynchronicznego nie nastąpi natychmiast tak jak w `foreach()` pętli, chyba że wymusić wygenerowanego sekwencji do wykonywania iteracji w wyniku wywołania `.ToList()` lub `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="0e802-172">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="0e802-173">Ważne informacje i wskazówki</span><span class="sxs-lookup"><span data-stu-id="0e802-173">Important Info and Advice</span></span>

<span data-ttu-id="0e802-174">Programowanie asynchroniczne jest stosunkowo prosta, są niektóre szczegółowe informacje, należy wziąć pod uwagę, który pozwala uniknąć nieoczekiwanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="0e802-174">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

*  <span data-ttu-id="0e802-175">`async`**metody muszą mieć** `await` **— słowo kluczowe w ich treści lub nigdy nie przyniesie!**</span><span class="sxs-lookup"><span data-stu-id="0e802-175">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="0e802-176">Jest to ważne, należy wziąć pod uwagę.</span><span class="sxs-lookup"><span data-stu-id="0e802-176">This is important to keep in mind.</span></span>  <span data-ttu-id="0e802-177">Jeśli `await` nie jest używany w treści `async` — metoda, C# kompilatora spowoduje wygenerowanie ostrzeżenia, ale będzie kodu kompilowanie i uruchamianie tak, jakby była normalne — metoda.</span><span class="sxs-lookup"><span data-stu-id="0e802-177">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="0e802-178">Należy pamiętać, że również to bardzo mało wydajne, ponieważ automatu stanów generowane przez kompilator języka C# dla metody asynchronicznej może nie być służącymi niczego.</span><span class="sxs-lookup"><span data-stu-id="0e802-178">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

*   <span data-ttu-id="0e802-179">**Należy dodać "Async" jako sufiks nazwy metody asynchronicznej, co zostanie zapisany.**</span><span class="sxs-lookup"><span data-stu-id="0e802-179">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="0e802-180">Jest to Konwencji używane w środowisku .NET więcej łatwo rozróżnianie synchroniczne i asynchroniczne metody.</span><span class="sxs-lookup"><span data-stu-id="0e802-180">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="0e802-181">Należy pamiętać, że niektórych metod, które nie są jawnie wywołane przez kodu (np. procedury obsługi zdarzeń lub metod kontrolera sieci web) nie mają zastosowania.</span><span class="sxs-lookup"><span data-stu-id="0e802-181">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="0e802-182">Ponieważ te są nie jawnie wywoływany przez kod, są jawne o ich nazw nie jest równie ważne.</span><span class="sxs-lookup"><span data-stu-id="0e802-182">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

*   <span data-ttu-id="0e802-183">`async void`**należy używać tylko dla programów obsługi zdarzeń.**</span><span class="sxs-lookup"><span data-stu-id="0e802-183">`async void` **should only be used for event handlers.**</span></span>

<span data-ttu-id="0e802-184">`async void`jest to jedyny sposób, aby umożliwić obsługę zdarzeń asynchroniczne do pracy, ponieważ nie mają zwracanych typów zdarzeń (w związku z tym nie można wprowadzić użycie `Task` i `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="0e802-184">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="0e802-185">Użycie `async void` nie jest zgodna z modelem NACIŚNIJ i może być wyzwaniem, aby użyć, takich jak:</span><span class="sxs-lookup"><span data-stu-id="0e802-185">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

  *   <span data-ttu-id="0e802-186">Wyjątki zgłaszane w `async void` metody nie można przechwycić poza tej metody.</span><span class="sxs-lookup"><span data-stu-id="0e802-186">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
  *   <span data-ttu-id="0e802-187">`async void`metody są bardzo trudne do testowania.</span><span class="sxs-lookup"><span data-stu-id="0e802-187">`async void` methods are very difficult to test.</span></span>
  *   <span data-ttu-id="0e802-188">`async void`metody może spowodować zły efekty uboczne, jeśli element wywołujący nie jest oczekiwany do asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0e802-188">`async void` methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

*   <span data-ttu-id="0e802-189">**Starannie bieżnika, używając wyrażenia asynchroniczne lambda w wyrażenia LINQ**</span><span class="sxs-lookup"><span data-stu-id="0e802-189">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="0e802-190">Wykonanie odroczone użyć wyrażenia lambda w składniku LINQ, znaczenie kodu może służyć do wykonywania w czasie, gdy nie spodziewasz się.</span><span class="sxs-lookup"><span data-stu-id="0e802-190">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="0e802-191">Wprowadzenie blokowania zadania do tego łatwo może doprowadzić do zakleszczenia, jeśli nie jest prawidłowo zapisany.</span><span class="sxs-lookup"><span data-stu-id="0e802-191">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="0e802-192">Ponadto zagnieżdżanie kod asynchroniczny następująco można także utrudnić przeglądanie informacji o wykonanie kodu.</span><span class="sxs-lookup"><span data-stu-id="0e802-192">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="0e802-193">Async i LINQ są wydajne, ale powinny być używane razem jako dokładnie i wyraźnie, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="0e802-193">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

*   <span data-ttu-id="0e802-194">**Pisanie kodu, który w sposób nieblokujące oczekujące na zadania**</span><span class="sxs-lookup"><span data-stu-id="0e802-194">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="0e802-195">Blokowanie bieżącego wątku w celu oczekiwania na ukończenie zadania może spowodować zakleszczenie i kontekstu zablokowanych wątków i może wymagać znacznie bardziej skomplikowane obsługi błędów.</span><span class="sxs-lookup"><span data-stu-id="0e802-195">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="0e802-196">Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania w przypadku oczekiwania zadania w sposób nieblokujące:</span><span class="sxs-lookup"><span data-stu-id="0e802-196">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="0e802-197">Użyć tej funkcji...</span><span class="sxs-lookup"><span data-stu-id="0e802-197">Use this...</span></span> | <span data-ttu-id="0e802-198">Zamiast tego...</span><span class="sxs-lookup"><span data-stu-id="0e802-198">Instead of this...</span></span> | <span data-ttu-id="0e802-199">Jeśli chcą to</span><span class="sxs-lookup"><span data-stu-id="0e802-199">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | <span data-ttu-id="0e802-200">`Task.Wait`lub`Task.Result`</span><span class="sxs-lookup"><span data-stu-id="0e802-200">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="0e802-201">Trwa pobieranie wyniku zadania w tle</span><span class="sxs-lookup"><span data-stu-id="0e802-201">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="0e802-202">Oczekiwanie na zakończenie wszystkie zadania</span><span class="sxs-lookup"><span data-stu-id="0e802-202">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="0e802-203">Oczekiwanie na ukończenie wszystkich zadań</span><span class="sxs-lookup"><span data-stu-id="0e802-203">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="0e802-204">Oczekiwanie na pewien czas</span><span class="sxs-lookup"><span data-stu-id="0e802-204">Waiting for a period of time</span></span> |

*   <span data-ttu-id="0e802-205">**Pisanie kodu mniej stanowe**</span><span class="sxs-lookup"><span data-stu-id="0e802-205">**Write less stateful code**</span></span>

<span data-ttu-id="0e802-206">Nie są zależne od stanu obiektów globalnych lub wykonywanie niektórych metod.</span><span class="sxs-lookup"><span data-stu-id="0e802-206">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="0e802-207">Zamiast tego zależą tylko wartości zwracanych z metod.</span><span class="sxs-lookup"><span data-stu-id="0e802-207">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="0e802-208">Dlaczego?</span><span class="sxs-lookup"><span data-stu-id="0e802-208">Why?</span></span>

  *   <span data-ttu-id="0e802-209">Kod będzie ułatwia przeglądanie informacji o.</span><span class="sxs-lookup"><span data-stu-id="0e802-209">Code will be easier to reason about.</span></span>
  *   <span data-ttu-id="0e802-210">Kod będzie łatwiejsze testowanie.</span><span class="sxs-lookup"><span data-stu-id="0e802-210">Code will be easier to test.</span></span>
  *   <span data-ttu-id="0e802-211">Mieszanie asynchroniczne i synchroniczne kodu jest znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="0e802-211">Mixing async and synchronous code is far simpler.</span></span>
  *   <span data-ttu-id="0e802-212">Zazwyczaj można uniknąć całkowicie wyścigu.</span><span class="sxs-lookup"><span data-stu-id="0e802-212">Race conditions can typically be avoided altogether.</span></span>
  *   <span data-ttu-id="0e802-213">W zależności od wartości zwracanych upraszcza koordynujący kodu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0e802-213">Depending on return values makes coordinating async code simple.</span></span>
  *   <span data-ttu-id="0e802-214">(Podwyższenia) on naprawdę dobrze działa z iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="0e802-214">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="0e802-215">Zalecane celem jest uzyskanie pełnej lub prawie pełne [referencyjnej przezroczystość](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0e802-215">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="0e802-216">W ten sposób spowoduje codebase bardzo przewidywalne, zakresie testować i obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="0e802-216">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="0e802-217">Inne zasoby</span><span class="sxs-lookup"><span data-stu-id="0e802-217">Other Resources</span></span>

* <span data-ttu-id="0e802-218">[Asynchroniczne szczegółowe](../standard/async-in-depth.md) zawiera więcej informacji na temat działania zadania.</span><span class="sxs-lookup"><span data-stu-id="0e802-218">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* <span data-ttu-id="0e802-219">Lucian Wischik [sześciu Ważne porady dotyczące Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są cudowne zasobów programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="0e802-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
