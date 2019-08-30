---
title: Programowanie asynchroniczne —C#
description: Dowiedz się C# więcej o modelu programowania asynchronicznego na poziomie języka udostępnianym przez platformę .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 246046fb5ac9b0c03df7df71ef426dc2ac6f0617
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168811"
---
# <a name="asynchronous-programming"></a>Programowanie asynchroniczne

Jeśli istnieją jakieś wymagania dotyczące operacji we/wy (takie jak żądanie danych z sieci lub uzyskiwanie dostępu do bazy danych), należy wykorzystać programowanie asynchroniczne.  Można również mieć kod powiązany z PROCESORem, taki jak wykonywanie kosztownych obliczeń, co jest również dobrym scenariuszem do pisania kodu asynchronicznego.

C#ma model programowania asynchronicznego na poziomie języka, który umożliwia łatwe pisanie kodu asynchronicznego bez konieczności Juggle wywołań zwrotnych lub zgodności z biblioteką obsługującą asynchroniczności. Następuje to, co jest znane jako [wzorzec asynchroniczny oparty na zadaniach (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Podstawowe omówienie modelu asynchronicznego

Podstawowym programowaniem asynchronicznym są `Task` obiekty i `Task<T>` , które modelują operacje asynchroniczne.  Są one obsługiwane przez `async` słowa kluczowe i. `await`  Model jest dość prosty w większości przypadków:

Dla kodu powiązanego we/wy `await` jest operacją, która `Task` zwraca lub `Task<T>` wewnątrz `async` metody.

W przypadku kodu `await` powiązanego z procesorem operacja uruchamiana w wątku w tle `Task.Run` za pomocą metody.

`await` Słowo kluczowe to miejsce, w którym występuje magiczna. Zwraca kontrolę do obiektu wywołującego metody, która została wykonana `await`, i ostatecznie umożliwia interfejsowi użytkownika reagowanie lub na elastyczność usługi.

Istnieją inne sposoby podejścia do kodu asynchronicznego niż `async` `await` opisano w artykule TAP połączonym powyżej, ale ten dokument koncentruje się na konstrukcjach poziomu języka od tego momentu.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Przykład z ograniczeniami we/wy: Pobieranie danych z usługi sieci Web

Może być konieczne pobranie niektórych danych z usługi sieci Web po naciśnięciu przycisku, ale nie chcesz blokować wątku interfejsu użytkownika. Można to zrobić w następujący sposób:

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

I to wszystko! Kod wyraża zamiar (trwa pobieranie danych asynchronicznie) bez pobierania ugrzęźnięcia z obiektów zadań.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Przykład związany z PROCESORem: Wykonywanie obliczeń dla gry

Załóżmy, że nastąpi napisanie gry mobilnej, gdzie naciśnięcie przycisku może spowodować uszkodzenie wielu Enemies na ekranie.  Wykonywanie obliczeń uszkodzeń może być kosztowne, a wykonanie tej operacji w wątku interfejsu użytkownika spowoduje, że gra zostanie wstrzymana w miarę wykonywania obliczeń.

Najlepszym sposobem obsługi tego jest uruchomienie wątku w tle, który wykonuje pracę przy użyciu `Task.Run`i `await` jego wynik.  Dzięki temu interfejs użytkownika może być niezakłócony podczas wykonywania pracy.

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

I to wszystko!  Ten kod czyści przeznaczenie zdarzenia kliknięcia przycisku, nie wymaga ręcznego zarządzania wątkiem w tle i robi to w sposób nieblokowany.

### <a name="what-happens-under-the-covers"></a>Co się dzieje w obszarze okładek

Istnieje wiele elementów, w których dane są wykonywane asynchronicznie.  Jeśli chcesz wiedzieć się o to `Task` [](../standard/async-in-depth.md) `Task<T>`, co się dzieje poniżej, zapoznaj się z nim, aby uzyskać więcej informacji.

Po C# stronie elementów kompilator przekształca kod na maszynę stanu, która śledzi elementy, takie jak wykonywanie operacji, gdy `await` zostanie osiągnięty i wznowiono wykonywanie po zakończeniu zadania w tle.

Dla teoretycznie nachylonego elementu jest to implementacja [modelu Promise asynchroniczności](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Najważniejsze elementy do zrozumienia

* Kod asynchroniczny może być używany zarówno dla kodu powiązanego we/wy, jak i związanego z PROCESORem, ale różnią się w zależności od każdego scenariusza.
* Kod asynchroniczny `Task<T>` używa `Task`i, które są konstrukcjami używanymi do modelowania pracy wykonywanej w tle.
* Słowo kluczowe zamienia metodę na metodę asynchroniczną, która umożliwia `await` użycie słowa kluczowego w treści. `async`
* `await` Gdy słowo kluczowe jest stosowane, wstrzymuje metodę wywołującą i zwraca kontrolę do jej obiektu wywołującego do momentu ukończenia zadania.
* `await`można go używać tylko wewnątrz metody asynchronicznej.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznawanie pracy powiązanej z PROCESORem i operacji we/wy

Pierwsze dwa przykłady tego przewodnika pokazują, jak można korzystać `async` z programu oraz `await` w przypadku pracy związanej we/wy i związanej z procesorem.  Jest to klucz, który można określić, gdy zadanie, które należy wykonać, jest powiązane z elementem we/wy lub PROCESORem, ponieważ może znacznie wpływać na wydajność kodu i potencjalnie spowodować błędne użycie niektórych konstrukcji.

Poniżej przedstawiono dwa pytania, które należy zadać przed pisaniem dowolnego kodu:

1. Czy kod będzie oczekiwał na coś, takiego jak dane z bazy danych?

    Jeśli odpowiedź brzmi "tak", Twoja służba jest **powiązana z elementem we/wy**.

2. Czy kod będzie wykonywał bardzo kosztowne obliczenia?

    Jeśli otrzymasz odpowiedź "tak", Twoja służba jest **powiązana z procesorem**.

Jeśli posiadana pracy jest **związana z we/wy**, użyj `async` `await` i *bez* `Task.Run`.  *Nie należy* używać biblioteki zadań równoległych.  Przyczynę tego problemu opisano w [artykule](../standard/async-in-depth.md)dotyczącym kompleksów.

Jeśli praca, którą dysponujesz, jest zależna od **procesora** i masz informacje o czasie `async` reakcji `await` , użyj i ale Powiąż ją z innym wątkiem *z* `Task.Run`.  Jeśli prace są odpowiednie dla współbieżności i równoległości, należy również rozważyć użycie [biblioteki zadań równoległych](../standard/parallel-programming/task-parallel-library-tpl.md).

Dodatkowo należy zawsze mierzyć wykonywanie kodu.  Można na przykład wyszukać siebie w sytuacji, w której ilość pracy związanej z PROCESORem jest zbyt mała w porównaniu z kosztami przełączeń kontekstu w przypadku wielowątkowości.  Każdy wybór ma swoje wady i należy wybrać odpowiednią kompromis dla danej sytuacji.

## <a name="more-examples"></a>Więcej przykładów

W poniższych przykładach pokazano różne sposoby pisania kodu asynchronicznego w programie C#.  Obejmują one kilka różnych scenariuszy, które mogą się pojawić.

### <a name="extracting-data-from-a-network"></a>Wyodrębnianie danych z sieci

Ten fragment kodu pobiera kod HTML z strony głównej pod adresem [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza liczbę wystąpień ciągu ".NET" w kodzie HTML.  Używa ASP.NET MVC do zdefiniowania metody kontrolera sieci Web, która wykonuje to zadanie, zwracając liczbę.

> [!NOTE]
> Jeśli planujesz wykonywanie analizy HTML w kodzie produkcyjnym, nie używaj wyrażeń regularnych. Zamiast tego użyj biblioteki analizy.

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

Jest to ten sam scenariusz Zapisano dla aplikacji uniwersalnej systemu Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Oczekiwanie na zakończenie wielu zadań

Możesz się zastanowić w sytuacji, w której konieczne jest pobranie wielu danych jednocześnie.  Interfejs API zawiera dwie metody `Task.WhenAny` , `Task.WhenAll` które pozwalają pisać kod asynchroniczny, który wykonuje operację nieblokującą w przypadku wielu zadań w tle. `Task`

Ten przykład pokazuje, jak można `User` pobrać dane dla `userId`zestawu s.

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

Oto inny sposób, aby napisać nieco bardziej zwięzłie, przy użyciu LINQ:

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

Chociaż nie jest to mniej kodu, weź pod uwagę podczas mieszania LINQ z kodem asynchronicznym.  Ponieważ LINQ korzysta z odroczonego (opóźnionego) wykonywania, wywołania asynchroniczne nie będą wykonywane natychmiast, dopóki nie `foreach()` wymusisz wygenerowania sekwencji iteracji z `.ToList()` wywołaniem lub `.ToArray()`.

## <a name="important-info-and-advice"></a>Ważne informacje i porady

Chociaż programowanie asynchroniczne jest stosunkowo proste, istnieją pewne szczegółowe informacje, które mogą uniemożliwić nieoczekiwane zachowanie.

* `async`**metody muszą mieć** **słowo kluczowe w swojej treści lub nigdy nie da!** `await`

Jest to ważne, aby mieć świadomość.  Jeśli `await` nie jest używany w treści `async` metody, C# kompilator generuje ostrzeżenie, ale kod zostanie skompilowany i uruchomiony tak, jakby był normalną metodą.  Należy zauważyć, że może to również być niezwykle niewydajne, ponieważ komputer stanu wygenerowany przez C# kompilator dla metody asynchronicznej nie będzie wykonywać żadnych czynności.

* **Należy dodać "Async" jako sufiks każdej zapisywanych nazw metod asynchronicznych.**

Jest to Konwencja używana w programie .NET do łatwiejszego odróżnienia metod synchronicznych i asynchronicznych. Należy zauważyć, że niektóre metody, które nie są jawnie wywoływane przez kod (takie jak procedury obsługi zdarzeń lub metody kontrolera sieci Web), nie muszą być stosowane. Ponieważ nie są one jawnie wywoływane przez kod, jawny opis jego nazewnictwa nie jest ważny.

* `async void`**powinien być używany tylko dla programów obsługi zdarzeń.**

`async void`jest jedynym sposobem zezwalania na działanie programów obsługi zdarzeń asynchronicznych, ponieważ zdarzenia nie mają zwracanych typów (w związku z czym `Task` nie `Task<T>`mogą korzystać z i). Inne użycie `async void` nie jest zgodne z modelem TAP i może być trudne do użycia, takie jak:

* Wyjątki zgłoszone w `async void` metodzie nie mogą być przechwytywane poza tą metodą.
* `async void`metody są bardzo trudne do przetestowania.
* `async void`metody mogą spowodować złe skutki uboczne, jeśli obiekt wywołujący nie oczekuje, że będzie on asynchroniczny.

* **Dokładne użycie asynchronicznych wyrażeń lambda w wyrażeniach LINQ**

Wyrażenia lambda w składniku LINQ wykorzystują odroczone wykonywanie, co oznacza, że kod może zakończyć wykonywanie w czasie, gdy nie jest oczekiwany. Wprowadzenie zadań blokowania w tym celu może w prosty sposób spowodować zakleszczenie, jeśli nie zapisano prawidłowo. Ponadto zagnieżdżanie kodu asynchronicznego, takiego jak ten, może być również trudniejsze do powodowania wykonywania kodu. Asynchroniczne i LINQ są zaawansowane, ale powinny być używane razem, jak to możliwe.

* **Napisz kod, który czeka na zadania w sposób nieblokowany**

Zablokowanie bieżącego wątku jako środka do oczekiwania na ukończenie zadania może spowodować zakleszczenie i zablokowane wątki kontekstu i może wymagać znacznie bardziej złożonej obsługi błędów. Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania z oczekiwaniami w przypadku zadań w sposób nieblokowany:

| Użyj tego... | Zamiast tego... | Jeśli chcesz to zrobić |
| --- | --- | --- |
| `await` | `Task.Wait` lub `Task.Result` | Pobieranie wyniku zadania w tle |
| `await Task.WhenAny` | `Task.WaitAny` | Oczekiwanie na zakończenie dowolnego zadania |
| `await Task.WhenAll` | `Task.WaitAll` | Oczekiwanie na zakończenie wszystkich zadań |
| `await Task.Delay` | `Thread.Sleep` | Oczekiwanie przez pewien czas |

* **Zapisz mniej stanowy kod**

Nie zależą od stanu obiektów globalnych lub wykonywania niektórych metod. Zamiast tego zależą tylko od wartości zwracanych z metod. Dlaczego?

* Kod będzie łatwiejszy z przyczyn.
* Kod będzie łatwiejszy do przetestowania.
* Mieszanie kodu asynchronicznego i synchronicznego jest bardzo prostsze.
* Warunki wyścigu można zwykle uniknąć w ogóle.
* W zależności od zwracanych wartości upraszczamy prosty kod asynchroniczny.
* (Premia) dobrze sprawdza się w przypadku iniekcji zależności.

Zalecanym celem jest osiągnięcie pełnej lub niemal kompletnej [przejrzystości referencyjnej](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie. Wykonanie tej czynności spowoduje powstanie niezwykle przewidywalnej, weryfikowalneej i obsługiwanej bazy kodu.

## <a name="other-resources"></a>Inne zasoby

* [Asynchroniczne](../standard/async-in-depth.md) Szczegóły zawiera więcej informacji na temat działania zadań.
* [Programowanie asynchroniczne z Async i Await (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischike [sześć najważniejszych porad dotyczących Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) to wspaniałe zasoby dla programowania asynchronicznego
