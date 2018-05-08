---
title: Programowanie asynchroniczne
description: Więcej informacji na temat języka C# poziom języka asynchroniczne modelu programowania udostępniane przez oprogramowanie .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: 22a63ab55ba7f7888973f08ebdb3cbc149d6ac57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="asynchronous-programming"></a>Programowanie asynchroniczne

Jeśli masz żadnych potrzeb I/E-granica (na przykład żąda danych od sieci lub uzyskiwania dostępu do bazy danych), należy wykorzystać programowanie asynchroniczne.  Można również mieć kodu procesora, takich jak przeprowadzanie obliczeń kosztowne, która jest również dobrym scenariusz dotyczące pisania kodu async.

C# ma poziom języka asynchronicznego programowania modelu, który umożliwia łatwe pisanie kodu asynchroniczne bez konieczności łatwiejszą obsługę wywołań zwrotnych lub odpowiadają bibliotekę, która obsługuje asynchrony. Wynika, co jest nazywane [opartego na zadaniach asynchronicznej wzorca (TAP)](https://msdn.microsoft.com/library/hh873175.aspx).

## <a name="basic-overview-of-the-asynchronous-model"></a>Omówienie modelu asynchroniczne

Podstawowe programowania asynchronicznego są `Task` i `Task<T>` obiektów, które modelu operacji asynchronicznych.  Są one obsługiwane przez `async` i `await` słów kluczowych.  Model jest dość proste, w większości przypadków: 

Dla kodu I/E-powiązane z możesz `await` operacji, która zwraca `Task` lub `Task<T>` wewnątrz `async` metody.

Kod, procesora użytkownik `await` operacji, która została uruchomiona w wątku w tle z `Task.Run` metody.

`await` — Słowo kluczowe jest, gdzie się stanie magic. Go daje sterowania do obiektu wywołującego metody, która jest wykonywana `await`, i ostatecznie umożliwia interfejsu użytkownika, aby odpowiadać lub usługi jest elastyczny.

Istnieją inne sposoby metody asynchronicznej kodu niż `async` i `await` opisane w artykule NACIŚNIJ linki umieszczono powyżej, ale ten dokument koncentruje się na konstrukcji poziom języka od tego momentu.

### <a name="io-bound-example-downloading-data-from-a-web-service"></a>Przykład I/E-granica: pobieranie danych z usługi sieci web

Konieczne może być pobrać niektóre dane z usługi sieci web po naciśnięciu przycisku, ale nie chcesz zablokować wątku interfejsu użytkownika. Można go zrobić po prostu w następujący sposób:

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

I to już wszystko! Kod odzwierciedla cele (pobieranie niektóre dane asynchronicznie) bez ugrzęźnięcia w interakcji z obiektami zadań.

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a>Przykład procesora: Przeprowadzanie obliczeń na gry

Powiedz pisania przenośnych grę, gdzie naciśnięcie przycisku może spowodować uszkodzenia na wiele wrogów na ekranie.  Wykonywanie obliczeń uszkodzenia może być kosztowne i to zrobić w wątku interfejsu użytkownika spowodowałoby gry są wyświetlane wstrzymania zgodnie z wykonaniem obliczeń!

Najlepszym sposobem obsługi to jest można uruchomić wątku w tle, która obsługuje pracy, przy użyciu `Task.Run`, i `await` wyniku.  Pozwoli to interfejsu użytkownika uznać smooth, jak praca jest wykonywana.

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

I to już wszystko!  Ten kod prawidłowo wyraża celem Zdarzenie kliknięcia przycisku, nie wymaga zarządzania ręcznie wątku w tle i kopiuje je w taki sposób, bez blokowania.

### <a name="what-happens-under-the-covers"></a>Co się stanie w tle

Istnieje wiele części ruchu, gdzie są dane operacji asynchronicznych.  Jeśli zastanawiasz się o to, co dzieje się poniżej obejmuje z `Task` i `Task<T>`, wyewidencjonowania [Async szczegółowe](../standard/async-in-depth.md) artykułu, aby uzyskać więcej informacji.

C# strony rzeczy, kompilator przekształca kodu do automatu stanów, które przechowuje informacje o takich elementów, jak reaguje wykonywania podczas `await` jest wykonanie osiągnęło i wznawianie po zakończeniu zadania tła.

W przypadku teoretycznie pochylone, jest implementacją [Promise Model asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).

## <a name="key-pieces-to-understand"></a>Części klucza, aby zrozumieć

*   Asynchroniczne kodu można użyć dla kodu zarówno I/E-granica i procesora, ale inaczej dla każdego scenariusza.
*   Asynchroniczne kodzie użyto `Task<T>` i `Task`, konstrukcje używane do modelu wykonywanej pracy w tle, które są.
* `async` — Słowo kluczowe włącza metodę do metody asynchronicznej, dzięki czemu można użyć `await` — słowo kluczowe w jego treści.
*   Gdy `await` — słowo kluczowe jest stosowana, wstrzymuje metody wywołującej i daje formantu do swojego obiektu wywołującego do czasu ukończenia zadania oczekiwano.
*   `await` można użyć tylko wewnątrz metody asynchronicznej.

## <a name="recognize-cpu-bound-and-io-bound-work"></a>Rozpoznaje procesora i I/E-granica pracy

Pierwsze dwa przykłady w tym przewodniku pokazano, jak używasz `async` i `await` pracy I/E-granica i procesora.  Jego klucz, który można zdefiniować zadanie należy wykonać I/E-granicę lub procesora, ponieważ może znacznie wpłynąć na wydajność kodu i może potencjalnie doprowadzić do niewłaściwie korzysta z niektórych konstrukcje.

Poniżej przedstawiono dwa pytań, na które należy poprosić przed przystąpieniem do napisania kodu:

1. Zostanie kodzie "oczekuje" na coś, takich jak dane z bazy danych?

    Jeśli odpowiedź to "yes", a następnie jest pracy **I/E-granica**.

2. Będzie kodu wykonywać bardzo kosztowna obliczeń?

    Jeśli odpowiedzi na "tak", a następnie jest pracy **procesora**.
    
Jeśli masz pracy **I/E-granica**, użyj `async` i `await` *bez* `Task.Run`.  Możesz *nie powinien* Użyj Biblioteka zadań równoległych.  Przyczyną tego jest opisane w temacie [asynchronicznych w artykule głębokość](../standard/async-in-depth.md).

Jeśli masz pracy **procesora** i interesujących reakcji, użyj `async` i `await` , ale zduplikować pracy w innym wątku *z* `Task.Run`.  W przypadku potrzeby współbieżności i równoległości pracy, należy również rozważyć użycie Biblioteka zadań równoległych.

Ponadto należy zawsze pomiarów wykonywania kodu.  Na przykład może się okazać się w sytuacji, gdy nie jest kosztowna pracy procesora wystarczająco w porównaniu z obciążenie przełączenia kontekstu, gdy wielowątkowości.  Każdy element ma jego zależnościami, i należy wybrać prawidłowe zależności dla danej sytuacji.

## <a name="more-examples"></a>Więcej przykładów

W poniższych przykładach pokazano różne sposoby, które można napisać kod asynchronicznych w języku C#.  Obejmują one kilku różnych scenariuszy, które może napotkać.

### <a name="extracting-data-from-a-network"></a>Wyodrębnianie danych z sieci

Ta Wstawka kodu pobiera kod HTML z www.dotnetfoundation.org i oblicza liczbę razy występuje ciąg ".NET" w kodzie HTML.  Aby zdefiniować metody kontrolera sieci web, która wykonuje to zadanie, zwracając liczbę używa platformy ASP.NET MVC.

> [!NOTE]
> Jeśli planujesz wykonanie HTML podczas analizowania w kodzie produkcyjnym, nie należy używać wyrażeń regularnych. Zamiast tego użyj biblioteki analizy.

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

Oto napisane dla uniwersalnych aplikacji systemu Windows, która wykonuje to samo zadanie, gdy przycisk zostanie naciśnięty sytuacji:

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

### <a name="waiting-for-multiple-tasks-to-complete"></a>Oczekiwanie na ukończenie wielu zadań

Może się okazać się w sytuacji, w których należy pobrać jednocześnie wiele fragmentów danych.  `Task` Interfejs API zawiera dwie metody `Task.WhenAll` i `Task.WhenAny` umożliwiają zapis asynchroniczny kod, który wykonuje nieblokujące oczekiwania na wielu zadań w tle.

W tym przykładzie pokazano, jak może przechwycić `User` danych dla zestawu `userId`s.

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

Oto innym sposobem zapisu to bardziej krótkiej formie, za pomocą LINQ:

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
Chociaż jest mniejsza ilość kodu, Zachowaj ostrożność podczas mieszanie LINQ z kodem asynchronicznego.  Ponieważ LINQ używa odroczonego wykonania (lazy), wywołania asynchronicznego nie nastąpi natychmiast tak jak w `foreach()` pętli, chyba że wymusić wygenerowanego sekwencji do wykonywania iteracji w wyniku wywołania `.ToList()` lub `.ToArray()`.

## <a name="important-info-and-advice"></a>Ważne informacje i wskazówki

Programowanie asynchroniczne jest stosunkowo prosta, są niektóre szczegółowe informacje, należy wziąć pod uwagę, który pozwala uniknąć nieoczekiwanego zachowania.

*  `async` **metody muszą mieć** `await` **— słowo kluczowe w ich treści lub nigdy nie przyniesie!**

Jest to ważne, należy wziąć pod uwagę.  Jeśli `await` nie jest używany w treści `async` — metoda, C# kompilatora spowoduje wygenerowanie ostrzeżenia, ale będzie kodu kompilowanie i uruchamianie tak, jakby była normalne — metoda.  Należy pamiętać, że również to bardzo mało wydajne, ponieważ automatu stanów generowane przez kompilator języka C# dla metody asynchronicznej może nie być służącymi niczego.

*   **Należy dodać "Async" jako sufiks nazwy metody asynchronicznej, co zostanie zapisany.**

Jest to Konwencji używane w środowisku .NET więcej łatwo rozróżnianie synchroniczne i asynchroniczne metody. Należy pamiętać, że niektórych metod, które nie są jawnie wywołane przez kodu (np. procedury obsługi zdarzeń lub metod kontrolera sieci web) nie mają zastosowania. Ponieważ te są nie jawnie wywoływany przez kod, są jawne o ich nazw nie jest równie ważne.

*   `async void` **należy używać tylko dla programów obsługi zdarzeń.**

`async void` jest to jedyny sposób, aby umożliwić obsługę zdarzeń asynchroniczne do pracy, ponieważ nie mają zwracanych typów zdarzeń (w związku z tym nie można wprowadzić użycie `Task` i `Task<T>`). Użycie `async void` nie jest zgodna z modelem NACIŚNIJ i może być wyzwaniem, aby użyć, takich jak:

  *   Wyjątki zgłaszane w `async void` metody nie można przechwycić poza tej metody.
  *   `async void` metody są bardzo trudne do testowania.
  *   `async void` metody może spowodować zły efekty uboczne, jeśli element wywołujący nie jest oczekiwany do asynchronicznego.

*   **Starannie bieżnika, używając wyrażenia asynchroniczne lambda w wyrażenia LINQ**

Wykonanie odroczone użyć wyrażenia lambda w składniku LINQ, znaczenie kodu może służyć do wykonywania w czasie, gdy nie spodziewasz się. Wprowadzenie blokowania zadania do tego łatwo może doprowadzić do zakleszczenia, jeśli nie jest prawidłowo zapisany. Ponadto zagnieżdżanie kod asynchroniczny następująco można także utrudnić przeglądanie informacji o wykonanie kodu. Async i LINQ są wydajne, ale powinny być używane razem jako dokładnie i wyraźnie, jak to możliwe.

*   **Pisanie kodu, który w sposób nieblokujące oczekujące na zadania**

Blokowanie bieżącego wątku w celu oczekiwania na ukończenie zadania może spowodować zakleszczenie i kontekstu zablokowanych wątków i może wymagać znacznie bardziej skomplikowane obsługi błędów. Poniższa tabela zawiera wskazówki dotyczące sposobu postępowania w przypadku oczekiwania zadania w sposób nieblokujące:

| Użyć tej funkcji... | Zamiast tego... | Jeśli chcą to |
| --- | --- | --- |
| `await` | `Task.Wait` lub `Task.Result` | Trwa pobieranie wyniku zadania w tle |
| `await Task.WhenAny` | `Task.WaitAny` | Oczekiwanie na zakończenie wszystkie zadania |
| `await Task.WhenAll` | `Task.WaitAll` | Oczekiwanie na ukończenie wszystkich zadań |
| `await Task.Delay` | `Thread.Sleep` | Oczekiwanie na pewien czas |

*   **Pisanie kodu mniej stanowe**

Nie są zależne od stanu obiektów globalnych lub wykonywanie niektórych metod. Zamiast tego zależą tylko wartości zwracanych z metod. Dlaczego?

  *   Kod będzie ułatwia przeglądanie informacji o.
  *   Kod będzie łatwiejsze testowanie.
  *   Mieszanie asynchroniczne i synchroniczne kodu jest znacznie prostsze.
  *   Zazwyczaj można uniknąć całkowicie wyścigu.
  *   W zależności od wartości zwracanych upraszcza koordynujący kodu asynchronicznego.
  *   (Podwyższenia) on naprawdę dobrze działa z iniekcji zależności.

Zalecane celem jest uzyskanie pełnej lub prawie pełne [referencyjnej przezroczystość](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) w kodzie. W ten sposób spowoduje codebase bardzo przewidywalne, zakresie testować i obsługiwać.

## <a name="other-resources"></a>Inne zasoby

* [Asynchroniczne szczegółowe](../standard/async-in-depth.md) zawiera więcej informacji na temat działania zadania.
* [Programowanie asynchroniczne z async i await (C#)](../csharp/programming-guide/concepts/async/index.md)
* Lucian Wischik [sześciu Ważne porady dotyczące Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) są cudowne zasobów programowania asynchronicznego
