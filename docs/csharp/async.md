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
# <a name="asynchronous-programming"></a>Programowanie asynchroniczne

Jeśli masz jakiekolwiek potrzeby związane z we/wy (takie jak żądanie danych z sieci lub uzyskiwanie dostępu do bazy danych), należy korzystać z programowania asynchronicznego.  Można również mieć kod związany z procesorem CPU, takich jak wykonywanie kosztownych obliczeń, który jest również dobrym scenariuszem do pisania kodu asynchronicznego.

C# ma model programowania asynchronicznego na poziomie języka, który umożliwia łatwe pisanie kodu asynchronicznego bez konieczności żonglowania wywołaniami zwrotu lub zgodne z biblioteki, która obsługuje asynchrony. Wynika to z tego, co jest znane jako [asynchroniczny wzorzec oparty na zadaniach (TAP).](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)

## <a name="basic-overview-of-the-asynchronous-model"></a>Podstawowy przegląd modelu asynchronicznego

Rdzeń programowania asynchronicznego `Task` jest `Task<T>` i obiektów, które modelują operacje asynchroniczne.  Są one obsługiwane `async` przez `await` słowa kluczowe i.  Model jest dość prosty w większości przypadków:

W `await` przypadku kodu związanego we/wy można `Task` `Task<T>` operacji, `async` która zwraca lub wewnątrz metody.

Dla kodu powiązanego `await` z procesorem CPU, operacja, `Task.Run` która jest uruchamiana w wątku w tle z metodą.

Słowo `await` kluczowe to miejsce, w którym dzieje się magia. Daje kontrolę do obiektu wywołującego metody, która została wykonana `await`, a ostatecznie umożliwia interfejsu użytkownika, aby być elastyczne lub usługi, które mają być elastyczne.

Istnieją inne sposoby podejścia do `async` kodu `await` asynchronicznego niż i opisane w artykule TAP połączonym powyżej, ale ten dokument skupi się na konstrukcjach na poziomie języka od tego momentu.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Przykład związany z we/wy: pobieranie danych z usługi sieci Web

Może być konieczne pobranie niektórych danych z usługi sieci web po naciśnięciu przycisku, ale nie chcesz blokować wątku interfejsu użytkownika. Można to osiągnąć po prostu tak:

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

To wszystko! Kod wyraża intencji (pobieranie niektórych danych asynchronicznie) bez ugrzęznąć w interakcji z Task obiektów.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Przykład związany z procesorem CPU: wykonywanie obliczeń dla gry

Załóżmy, że piszesz grę mobilną, w której naciśnięcie przycisku może zadać obrażenia wielu wrogom na ekranie.  Wykonanie obliczeń uszkodzeń może być kosztowne, a wykonanie tego w wątku interfejsu użytkownika sprawi, że gra będzie pauzować podczas wykonywania obliczeń!

Najlepszym sposobem radzenia sobie z tym jest rozpoczęcie wątku w tle, który wykonuje pracę przy użyciu `Task.Run`, i `await` jego wynik.  Pozwoli to interfejsu, aby czuć się gładko, jak praca jest wykonywana.

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

I to wszystko.  Ten kod czysto wyraża intencji przycisku click zdarzenia, nie wymaga ręcznego zarządzania wątku w tle i robi to w sposób nieblokujący.

### <a name="what-happens-under-the-covers"></a>Co dzieje się pod przykrywką

Istnieje wiele ruchomych elementów, w których chodzi o operacje asynchroniczne.  Jeśli jesteś ciekaw tego, co dzieje się `Task` pod `Task<T>`okładkami i , checkout [Async pogłębiony](../standard/async-in-depth.md) artykuł, aby uzyskać więcej informacji.

Po stronie Języka C# rzeczy kompilator przekształca kod na komputerze stanu, który śledzi `await` rzeczy, takie jak wydajność wykonywania po osiągnięciu i wznowienie wykonywania po zakończeniu zadania w tle.

Dla teoretycznie skłonnych jest to realizacja [modelu Promise asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Kluczowe elementy do zrozumienia

* Kod asynchronicznego może służyć zarówno dla kodu związanego we/wy i powiązanego z procesorem CPU, ale inaczej dla każdego scenariusza.
* Async kod `Task<T>` `Task`używa i , które są konstrukcje używane do modelu pracy wykonywanej w tle.
* Słowo `async` kluczowe zamienia metodę w metodę asynchroniczną, która umożliwia użycie słowa kluczowego `await` w jego treści.
* Po `await` zastosowaniu słowa kluczowego, zawiesza metodę wywołującą i daje kontrolę z powrotem do obiektu wywołującego, dopóki nie zostanie ukończone oczekiwane zadanie.
* `await`można używać tylko wewnątrz metody asynchronicznej.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznawanie pracy związanej z procesorem CPU i związaną z we/wy

Pierwsze dwa przykłady tego przewodnika pokazały, `async` `await` jak można używać i do pracy związanej z we/wy i procesora CPU.  Jest to klucz, który można zidentyfikować, gdy zadanie, które należy wykonać jest we/w-bound lub cpu-bound, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie prowadzić do nadużywania niektórych konstrukcji.

Oto dwa pytania, które należy zadać przed napisaniem kodu:

1. Czy twój kod będzie "czekał" na coś, na przykład dane z bazy danych?

    Jeśli odpowiedź brzmi "tak", twoja praca jest **związana z we/wy.**

2. Czy twój kod będzie wykonywać bardzo kosztowne obliczenia?

    Jeśli odpowiedziałeś "tak", twoja praca jest **związana z procesorem**.

Jeśli praca, którą masz jest i `async` / `await` **O-bound**, używać i *bez* `Task.Run`.  *Nie należy* używać biblioteki równoległej zadania.  Przyczyna tego jest opisana [w artykule Async in Depth](../standard/async-in-depth.md).

Jeśli praca masz jest **związany z procesorem CPU** `async` i `await` zależy Ci na responsywność, używać i ale tarło pracy off na inny wątek *z* `Task.Run`.  Jeśli praca jest odpowiednia dla współbieżności i równoległości, należy również rozważyć użycie [biblioteki równoległej zadania](../standard/parallel-programming/task-parallel-library-tpl.md).

Ponadto należy zawsze mierzyć wykonanie kodu.  Na przykład może znaleźć się w sytuacji, gdy praca związana z procesorem CPU nie jest wystarczająco kosztowne w porównaniu z obciążeniem przełączników kontekstu podczas wielowątkowości.  Każdy wybór ma swój kompromis i powinieneś wybrać właściwy kompromis dla swojej sytuacji.

## <a name="more-examples"></a>Więcej przykładów

W poniższych przykładach przedstawiono różne sposoby pisania kodu asynchronicznego w języku C#.  Obejmują one kilka różnych scenariuszy, na które możesz się natknąć.

### <a name="extracting-data-from-a-network"></a>Wyodrębnianie danych z sieci

Ten fragment kodu pobiera kod HTML ze strony głównej w [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza, ile razy ciąg ".NET" występuje w kodzie HTML.  Używa ASP.NET MVC do definiowania metody kontrolera sieci web, która wykonuje to zadanie, zwracając numer.

> [!NOTE]
> Jeśli planujesz analizowanie kodu HTML w kodzie produkcyjnym, nie używaj wyrażeń regularnych. Zamiast tego użyj biblioteki analizy.

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

Oto ten sam scenariusz napisany dla uniwersalnej aplikacji systemu Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Oczekiwanie na wykonanie wielu zadań

Może się okazać, że znajdujesz się w sytuacji, w której musisz pobrać wiele fragmentów danych jednocześnie.  Interfejs `Task` API zawiera dwie `Task.WhenAll` `Task.WhenAny` metody i które umożliwiają pisanie kodu asynchronicznego, który wykonuje nieblokujące oczekiwanie na wiele zadań w tle.

W tym przykładzie pokazano, jak można pobrać `User` dane dla zestawu `userId`s.

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

Oto inny sposób, aby napisać to nieco bardziej zwięźle, za pomocą LINQ:

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

Mimo że jest mniej kodu, należy uważać podczas mieszania LINQ z kodem asynchronicznym.  Ponieważ LINQ używa odroczonego (opóźnienie) wykonanie, wywołania asynchroniczne `foreach()` nie nastąpi natychmiast, jak to zrobić w pętli, `.ToList()` `.ToArray()`chyba że wymusić wygenerowaną sekwencję do iterate z wywołania lub .

## <a name="important-info-and-advice"></a>Ważne informacje i porady

Mimo że programowanie asynchroniczne jest stosunkowo proste, istnieją pewne szczegóły, o których należy pamiętać, które mogą zapobiec nieoczekiwanemu zachowaniu.

* `async`**metody muszą mieć słowo** `await` **kluczowe w swoim ciele lub nigdy nie poddadzą!**

Jest to ważne, aby pamiętać.  Jeśli `await` nie jest używany w `async` treści metody, kompilator C# wygeneruje ostrzeżenie, ale kod skompilują i uruchomi się tak, jakby była to metoda normalna.  Należy zauważyć, że będzie to również bardzo nieefektywne, jak komputer stanu generowane przez kompilator C# dla metody asynchronicznej nie będzie wykonywanie niczego.

* **Należy dodać "Async" jako sufiks każdej nazwy metody asynchronicznej, którą piszesz.**

Jest to konwencja używana w .NET do łatwiejszego rozróżniania metod synchronicznych i asynchronicznych. Należy zauważyć, że niektóre metody, które nie są jawnie wywoływane przez kod (takie jak programy obsługi zdarzeń lub metody kontrolera sieci web) nie koniecznie mają zastosowanie. Ponieważ nie są one jawnie wywoływane przez kod, jest jawne o ich nazewnictwa nie jest tak ważne.

* `async void`**powinny być używane tylko dla programów obsługi zdarzeń.**

`async void`jest jedynym sposobem, aby umożliwić asynchroniczne programy obsługi zdarzeń do pracy, `Task` ponieważ `Task<T>`zdarzenia nie mają typów zwracanych (w związku z tym nie można użyć i ). Jakiekolwiek inne `async void` użycie nie jest zgodne z modelem TAP i może być trudne w użyciu, takie jak:

* Wyjątki generowane `async void` w metodzie nie można przechwycić poza tą metodą.
* `async void`metody są bardzo trudne do przetestowania.
* `async void`metody mogą powodować złe skutki uboczne, jeśli obiekt wywołujący nie oczekuje ich async.

* **Ostrożnie bieżnika podczas korzystania lambdas async w wyrażeniach LINQ**

Wyrażenia Lambda w LINQ używać odroczonego wykonania, co oznacza, że kod może skończyć się wykonywanie w czasie, gdy nie oczekujesz go. Wprowadzenie blokowania zadań w tym może łatwo spowodować zakleszczenie, jeśli nie jest poprawnie napisane. Ponadto zagnieżdżanie kodu asynchronicznego, takie jak to może również utrudnić powodowanie dotyczące wykonywania kodu. Async i LINQ są potężne, ale powinny być używane razem tak dokładnie i wyraźnie, jak to możliwe.

* **Napisz kod, który czeka na zadania w sposób nieblokujący**

Blokowanie bieżącego wątku jako środek oczekiwania na zakończenie zadania może spowodować zakleszczenia i zablokowane wątki kontekstu i może wymagać znacznie bardziej złożonych obsługi błędów. Poniższa tabela zawiera wskazówki dotyczące sposobu radzenia sobie z oczekiwaniami na zadania w sposób nieblokujący:

| Użyj polecenia... | Zamiast tego... | Chcąc to zrobić |
| --- | --- | --- |
| `await` | `Task.Wait` lub `Task.Result` | Pobieranie wyniku zadania w tle |
| `await Task.WhenAny` | `Task.WaitAny` | Oczekiwanie na wykonanie dowolnego zadania |
| `await Task.WhenAll` | `Task.WaitAll` | Oczekiwanie na wykonanie wszystkich zadań |
| `await Task.Delay` | `Thread.Sleep` | Oczekiwanie na okres czasu |

* **Napisz mniej stanowy kod**

Nie zależą od stanu obiektów globalnych lub wykonywania niektórych metod. Zamiast tego zależy tylko od zwracanych wartości metod. Dlaczego?

* Kod będzie łatwiejrozdać do rozumu.
* Kod będzie łatwiejszy do przetestowania.
* Mieszanie kodu asynchronicznego i synchronicznego jest znacznie prostsze.
* Zazwyczaj można całkowicie uniknąć warunków wyścigu.
* W zależności od wartości zwracane sprawia, że koordynacja kodu asynchronicznego jest prosta.
* (Bonus) to działa naprawdę dobrze z zastrzykiem zależności.

Zalecanym celem jest osiągnięcie pełnej lub prawie pełnej [przezroczystości referencyjnej](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie. Spowoduje to niezwykle przewidywalne, sprawdzalne i możliwe do utrzymania codebase.

## <a name="other-resources"></a>Inne zasoby

* [Async w głębi](../standard/async-in-depth.md) zapewnia więcej informacji na temat działania zadań.
* [Asynchroniczne programowanie z async i await (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik's [Six Essential Porady dla Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są wspaniałym źródłem programowania async
