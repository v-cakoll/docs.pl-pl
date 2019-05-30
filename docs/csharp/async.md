---
title: Programowanie asynchroniczne —C#
description: Więcej informacji na temat języka C# poziomu języka asynchronicznego modelu programowania udostępnianego przez platformy .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: cdfbab381360bfcbae6cf3849d0bf0e18fda24bc
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377858"
---
# <a name="asynchronous-programming"></a>Programowanie asynchroniczne

W przypadku dowolnego potrzeb I/O-powiązane z (takich jak żąda danych od sieci lub uzyskiwania dostępu do bazy danych) można wykorzystywać programowania asynchronicznego.  Może również mieć kod zależne od Procesora CPU, takie jak kosztowne obliczeń, który jest również dobrym scenariusza dotyczące pisania kodu asynchronicznego.

C# ma poziom języka asynchronicznego modelu programowania, który pozwala na łatwe pisania kodu asynchronicznego bez konieczności łatwiejszą obsługę wywołań zwrotnych i być zgodna z biblioteki, która obsługuje asynchroniczności. Następuje to, co jest nazywane [opartego na zadaniach asynchronicznej wzorca (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

## <a name="basic-overview-of-the-asynchronous-model"></a>Ogólne omówienie modelu asynchronicznego

Podstawowe programowanie async jest `Task` i `Task<T>` obiektów, które modelu operacji asynchronicznych.  Są one obsługiwane przez `async` i `await` słów kluczowych.  Model jest dość prosty, w większości przypadków:

Dla kodu I/O-powiązane z możesz `await` operacją, która zwraca `Task` lub `Task<T>` wewnątrz `async` metody.

Kod, zależne od Procesora CPU możesz `await` operacji, która jest uruchomiona w wątku w tle za pomocą `Task.Run` metody.

`await` — Słowo kluczowe jest, gdzie się dzieje w raporcie magic. Jego przekazuje sterowanie do obiektu wywołującego metody, który wykonał `await`, a ostatecznie do szybkość reakcji interfejsu użytkownika lub usługi pod kątem elastyczności.

Istnieją inne sposoby kod asynchroniczny podejście niż `async` i `await` opisane w artykule wzorca TAP linki umieszczono powyżej, ale ten dokument koncentruje się na konstrukcji poziomu języka od tego momentu.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Przykład I/O-granicy: Pobieranie danych z usługi sieci web

Może być konieczne po naciśnięciu przycisku, Pobierz dane z usługi sieci web, ale nie chcesz zablokować wątek interfejsu użytkownika. Można to osiągnąć po prostu następująco:

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

I to wszystko! Kod wyraża intencji (pobierania niektórych danych asynchronicznie) bez ugrzęźnięcia w interakcji z obiektów zadań.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Przykład Procesora CPU: Wykonywanie obliczeń dla gier

Załóżmy, że piszesz grę mobilną, w którym naciśnięcie przycisku mogą skutkować szkody w wielu nieprzyjaciół na ekranie.  Wykonywanie obliczeń szkody może być kosztowne i to zrobić w wątku interfejsu użytkownika czyniłyby gry, są wyświetlane wstrzymania, ponieważ obliczenie jest wykonywane!

Najlepszym sposobem na to obsługa jest uruchomienie wątku w tle, która obsługuje pracę przy użyciu `Task.Run`, i `await` jego wynik.  Umożliwi to interfejsu użytkownika możesz bezproblemowe, ponieważ praca jest wykonywana.

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

I to wszystko!  Ten kod nie pozostawia żadnych śladów wyraża celem Zdarzenie kliknięcia przycisku, nie wymaga ręcznego zarządzania wątku w tle i odbywa się to w taki sposób, bez blokowania.

### <a name="what-happens-under-the-covers"></a>Co się dzieje w tle

Istnieje wiele przenoszenie fragmentów, których dotyczy operacji asynchronicznych.  Jeśli masz zastanawiasz się, co się dzieje w obiekcie nadrzędnym `Task` i `Task<T>`, wyewidencjonowania [Async szczegółowe](../standard/async-in-depth.md) artykuł, aby uzyskać więcej informacji.

C# po stronie rzeczy, kompilator przekształca kodu w automacie stanów, która przechowuje informacje o elementów, takich jak wykonanie reaguje po `await` jest osiągnął i wznawianie wykonywanie po zakończeniu zadania w tle.

W przypadku teoretycznie pochylone, jest implementacją [modelu Promise asynchroniczności](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Kluczowych elementów, aby zrozumieć

* Kod asynchroniczny może służyć do kodu I/O-powiązane z i od Procesora CPU, ale inaczej dla każdego scenariusza.
* Kod asynchroniczny używa `Task<T>` i `Task`, służą do konstrukcji używanych do modelu wykonywanej pracy w tle.
* `async` — Słowo kluczowe jest przekształcany metody metody asynchronicznej, która pozwala na używanie `await` — słowo kluczowe w jej treści.
* Gdy `await` — słowo kluczowe jest stosowana, co wstrzymuje wywoływania metody i przekazuje sterowanie do obiektu wywołującego aż oczekiwane zadanie zostało ukończone.
* `await` należy używać tylko wewnątrz metody asynchronicznej.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznaje pracy Procesora CPU i czy/Wy — powiązane z

Pierwszych dwóch przykładach w tym przewodniku pokazano, jak można użyć `async` i `await` do pracy I/O-granicę i zależne od Procesora CPU.  Jego klucza, który można go zidentyfikować zadanie należy wykonać I/O-granicę lub zależne od Procesora CPU, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie doprowadzić do niewłaściwie niektórych konstrukcji.

Poniżej przedstawiono dwa pytań, na które należy zapytać przed napisaniem jakiegokolwiek kodu:

1. Będzie Twój kod można "oczekiwanie" coś, takich jak dane z bazy danych?

    Jeśli Twoja odpowiedź to "yes", a następnie praca jest **I/O-powiązane z**.

2. Będzie Twój kod wykonywać bardzo kosztowna obliczeń?

    Jeśli odpowiedzi na "tak", a następnie praca jest **zależne od Procesora CPU**.

W przypadku pracy, masz **I/O-powiązane z**, użyj `async` i `await` *bez* `Task.Run`.  Możesz *nie powinien* Użyj Biblioteka zadań równoległych.  Przyczyną jest opisany w [asynchronicznych w artykule głębokość](../standard/async-in-depth.md).

W przypadku pracy, masz **zależne od Procesora CPU** i interesujące Cię czas reakcji, użyj `async` i `await` , ale zduplikować pracy w innym wątku *z* `Task.Run`.  Jeżeli praca jest odpowiednia dla współbieżność i równoległości, należy również rozważyć użycie [Biblioteka zadań równoległych](../standard/parallel-programming/task-parallel-library-tpl.md).

Ponadto należy zawsze zmierzyć wykonywania kodu.  Na przykład można znaleźć samodzielnie w sytuacji, gdy Twoje zadań intensywnie angażujących Procesor nie jest kosztowna wystarczająco w porównaniu z obciążeniem przełączeń kontekstu po wielowątkowości.  Każdy element ma jego kosztem i należy wybrać poprawny kosztem w danej sytuacji.

## <a name="more-examples"></a>Więcej przykładów

W poniższych przykładach pokazano różne sposoby, które można napisać kod asynchroniczny w języku C#.  Obejmują one kilka różnych scenariuszy, które mogą pochodzić między.

### <a name="extracting-data-from-a-network"></a>Wyodrębnianie danych z sieci

Ten fragment kodu pobiera kod HTML na stronie głównej w [www.dotnetfoundation.org](https://www.dotnetfoundation.org) i zlicza liczbę razy występuje w ciągu ".NET" w kodzie HTML.  Aby zdefiniować metodę kontrolera sieci web, która wykonuje to zadanie, zwracając liczbę używa platformy ASP.NET MVC.

> [!NOTE]
> Jeśli planujesz sposób analizowania w środowisku produkcyjnym kod HTML, nie należy używać wyrażeń regularnych. Zamiast tego użyj biblioteki analizy.

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

Oto ten sam scenariusz napisane dla uniwersalnych aplikacji Windows, która wykonuje to samo zadanie po naciśnięciu przycisku:

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

Może się okazać się w sytuacji, w których trzeba pobrać jednocześnie wiele fragmentów danych.  `Task` Interfejs API zawiera dwie metody `Task.WhenAll` i `Task.WhenAny` umożliwiają pisania kodu asynchronicznego, który wykonuje oczekiwania bez blokowania na wiele zadań w tle.

Ten przykład przedstawia, jak może uzyskać `User` danych dla zestawu `userId`s.

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

Oto inny sposób zapisu to nieco bardziej zwięzły, za pomocą LINQ:

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

Chociaż mniejszej ilości kodu, należy szczególnie uważać podczas mieszania LINQ z kodu asynchronicznego.  Ponieważ LINQ używa odroczonego wykonania (z opóźnieniem), wywołania asynchroniczne nie nastąpi natychmiastowe tak, jak w `foreach()` pętli, chyba że wymusić wygenerowanego sekwencji do iteracji z wywołaniem `.ToList()` lub `.ToArray()`.

## <a name="important-info-and-advice"></a>Ważne informacje i opinie

Mimo że programowanie async jest stosunkowo prosta, istnieje kilka szczegółów, o których należy pamiętać o tym, co może uniemożliwić nieoczekiwane zachowanie.

* `async` **metody musi być** `await` **— słowo kluczowe w treści lub nigdy nie przyniesie!**

Jest to ważne, które należy uwzględnić.  Jeśli `await` nie jest używany w treści `async` metody, C# kompilatora zostanie wygenerowane ostrzeżenie, ale będzie kodu, skompiluj i uruchom tak, jakby była normalnym metody.  Należy pamiętać, że również byłoby bardzo mało wydajne jako automatu stanów, generowane przez kompilator języka C# dla metody asynchronicznej będzie nie być wykonywania niczego.

* **Jako sufiks co nazwa metody async, którą piszesz, należy dodać "Async".**

Jest to Konwencji używany na platformie .NET do łatwiej odróżnienia synchroniczne i asynchroniczne metody. Pamiętaj, że niektóre metody, które nie są jawnie wywołane przez kod (np. programy obsługi zdarzeń lub metody kontrolera sieci web), niekoniecznie nie mają zastosowania. Ponieważ te nie są jawnie wywoływane przez kod, są wyraźnie ich nazw nie jest ważne.

* `async void` **powinna służyć wyłącznie do obsługi zdarzeń.**

`async void` jest to jedyny sposób, aby umożliwić procedury obsługi zdarzeń asynchronicznych do pracy, ponieważ nie są zwracane typy zdarzeń (dlatego nie może wprowadzać użytkowania `Task` i `Task<T>`). Użycie `async void` nie jest zgodna z modelem wzorca TAP i może stanowić wyzwanie, użycia, taki jak:

* Wyjątki zgłaszane w `async void` metoda nie może zostać przechwycony spoza tej metody.
* `async void` metody są bardzo trudne do testowania.
* `async void` metody może spowodować nieprawidłowe efekty uboczne, jeśli obiekt wywołujący nie jest oczekiwana musiały być asynchroniczny.

* **Bieżnika dokładnie przy użyciu asynchroniczne lambda w wyrażeniach zapytań LINQ**

Wyrażenia lambda w języku LINQ stosować odroczone wykonania, znaczenia kodu może się okazać, wykonywanie w czasie, gdy nie spodziewasz się. Wprowadzenie blokujących zadania do tego łatwo może spowodować zakleszczenie, jeśli nie jest prawidłowo zapisywane. Ponadto zagnieżdżania kodu asynchronicznego w następujący sposób można także utrudnić przeglądanie informacji o wykonania kodu. Async i LINQ to zaawansowane, ale powinny być używane razem oraz dokładnie wyraźnie, jak to możliwe.

* **Pisanie kodu i czeka na zadania w sposób, bez blokowania**

Blokuje bieżący wątek, co oznacza, że oczekiwania na zakończenie zadania może spowodować zakleszczenia i kontekst zablokowanych wątków i może wymagać znacznie bardziej skomplikowane obsługi błędów. Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania z oczekujących zadań w sposób nieblokującej na poziomie:

| Użyj polecenia... | Zamiast tego... | Jeśli chcesz to zrobić |
| --- | --- | --- |
| `await` | `Task.Wait` lub `Task.Result` | Podczas pobierania wyniku zadania w tle |
| `await Task.WhenAny` | `Task.WaitAny` | Oczekiwanie na dowolne zadanie do wykonania |
| `await Task.WhenAll` | `Task.WaitAll` | Oczekiwanie na ukończenie wszystkich zadań |
| `await Task.Delay` | `Thread.Sleep` | Oczekiwanie przez pewien czas |

* **Pisanie kodu mniej stanowe**

Nie należy polegać na stan obiektów globalnych lub wykonywanie niektórych metod. Zamiast tego należy być zależne tylko od wartości zwracane metod. Dlaczego?

* Kod będzie łatwiej przeglądanie informacji o.
* Kod będzie łatwiejsze testowanie.
* Mieszanie asynchroniczne i synchroniczne kodu jest znacznie łatwiejsze.
* Zazwyczaj można całkowicie uniknąć wyścigu.
* W zależności od wartości zwracane upraszcza koordynującego kod asynchroniczny.
* (Dodatkowe) działa bardzo dobrze z iniekcji zależności.

Zalecane dowiesz się, jak osiągnąć pełną lub prawie pełną [referencyjną przezroczystości](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie. To spowoduje w bardzo przewidywalny, zakresie testować i obsługiwać bazy kodu.

## <a name="other-resources"></a>Inne zasoby

* [Asynchroniczne szczegółowe](../standard/async-in-depth.md) zawiera więcej informacji na temat działania zadania.
* [Programowanie asynchroniczne z async i await (C#)](./programming-guide/concepts/async/index.md)
* Lucian Wischik [sześć podpowiedzi podstawowych Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są nagraliście zasobu dla programowania asynchronicznego
