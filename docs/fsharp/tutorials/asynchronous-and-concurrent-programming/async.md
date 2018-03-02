---
title: "Programowanie asynchroniczne w języku F #"
description: "Dowiedz się, jak F # — programowanie asynchroniczne odbywa się za pomocą modelu programowania poziom języka, który jest łatwy w użyciu i fizyczne dla języka."
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
# <a name="async-programming-in-f"></a>Programowanie asynchroniczne w języku F # #

> [!NOTE]
> Niektóre nieścisłości zostały odnalezione w tym artykule.  Jego jest modyfikowany.  Zobacz [&#666; problem](https://github.com/dotnet/docs/issues/666) Aby dowiedzieć się więcej o zmianach.

Async — Programowanie w języku F # można osiągnąć za pomocą modelu programowania poziom języka zaprojektowaną do łatwy w użyciu i fizyczne dla języka.

Jest podstawową async programowania w języku F # `Async<'T>`, reprezentacja prac, które mogą być wyzwalane do uruchamiania w tle, gdzie `'T` albo typ zwracany jest za pomocą specjalnych `return` — słowo kluczowe lub `unit` Jeśli nie ma przepływu pracy async wynik do zwrócenia.

Kluczowe pojęcia zrozumienie jest typ wyrażenia asynchronicznej `Async<'T>`, która jest jedynie _specyfikacji_ pracy można wykonać w kontekście asynchronicznego. Nie została wykonana, dopóki nie zostanie jawnie uruchomiony jeden z wyjścia funkcji (takich jak `Async.RunSynchronously`). Jest to inny sposób planowania wykonywania pracy, kończy się ono jest bardzo proste, w praktyce.

Na przykład załóżmy, że w chcesz pobrać kod HTML z dotnetfoundation.org bez blokowania głównego wątku. Można to wykonać je następująco:

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

I to już wszystko! Oprócz stosowania `async`, `let!`, i `return`, jest to normalne właśnie kodzie języka F #.

Istnieje kilka konstrukcji syntaktycznych, które warto zauważyć:

*   `let!` wiąże wynik wyrażenia async (który jest uruchamiany w kontekście innym).
*   `use!` działa podobnie do `let!`, ale usuwa jego powiązanych zasobów, gdy przechodzi ona poza zakresem.
*   `do!` zostanie await async przepływu pracy, która nie zwraca żadnych czynności.
*   `return` po prostu zwraca wynik wyrażenia asynchronicznej.
*   `return!` wykonuje innego async przepływu pracy i zwraca jego wartości zwracanej w związku z tym.

Ponadto normalne `let`, `use`, i `do` słowa kluczowe można używać razem w wersjach asynchronicznych tak samo, jak w normalnym funkcji.

## <a name="how-to-start-async-code-in-f"></a>Jak uruchomić kod asynchronicznych w języku F # #

Jak wspomniano wcześniej, kod asynchronicznej jest specyfikację pracy w innym kontekście, który musi być jawnie uruchomiona. Poniżej przedstawiono dwa podstawowe sposoby w tym celu:

1.  `Async.RunSynchronously` uruchomi async przepływu pracy w innym wątku i poczekać na jego wynik.

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

2.  `Async.Start` Uruchamianie przepływu pracy asynchronicznych w innym wątku i będzie **nie** poczekać na jego wynik.

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

Istnieją inne sposoby uruchamiania przepływ async dostępne dla bardziej konkretnych scenariuszy. Są one szczegółowe [w odwołaniu Async](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Uwaga na wątków

Wyrażenie "w innym wątku" został podany powyżej, ale należy pamiętać, że **nie oznacza to, że asynchroniczne przepływy pracy są fasad dla wielowątkowości**. Przepływ pracy faktycznie "przejdzie" między wątkami finansowania ich zewnętrznego dla małej ilości czasu na wykonanie pracy przydatne. Gdy przepływ pracy async skutecznie "oczekuje" (np. oczekiwanie na połączenie sieci zwrócić coś), którymkolwiek wątku, który został on finansowania zewnętrznego w tym czasie zostanie zwolniona do pracy przydatne Przejdź innych obiektów. Umożliwia asynchroniczne przepływy pracy, aby korzystać z systemu, które są uruchamiane w możliwie najbardziej efektywny sposób i ich dokonuje szczególnie duży dla dużej liczby operacji We/Wy scenariuszy.

## <a name="how-to-add-parallelism-to-async-code"></a>Jak dodać równoległości do kodu Async

Czasami użytkownik może muszą do wykonywania wielu zadań asynchronicznych równolegle, zbieranie wyników, a zinterpretowane w jakiś sposób. `Async.Parallel` Można to zrobić bez konieczności korzystania z biblioteki równoległych zadań, która wymagałoby konieczności wymuszone `Task<'T>` i `Async<'T>` typów.

Poniższy przykład użyje `Async.Parallel` pobierania kodu HTML z czterech popularnych witryn równolegle, poczekaj na zakończenie tych zadań, a następnie wydrukuj kodu HTML, który został pobrany.

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

## <a name="important-info-and-advice"></a>Ważne informacje i wskazówki

*   Dołącz "Async" na końcu wszystkie funkcje, których będziesz korzystać

 Jest to konwencji nazewnictwa, jego ułatwienia jak odnajdywania interfejsu API. Szczególnie w przypadku, jeśli dostępne są wersje synchroniczne i asynchroniczne tej samej procedury, jest dobrze jest jawnie określać, które jest asynchroniczne przez nazwę.

*   Nasłuchiwanie w kompilatorze!

 F # przez kompilator jest bardzo rygorystyczny, uniemożliwiając niemal czymś troubling jak uruchomić kod "async" synchronicznie. W przypadku napotkać ostrzeżenie, który jest znak kod nie będzie wykonanie jak uważasz, że będzie on. Jeśli kompilator mogą wysyłać wszystkiego, kodzie najprawdopodobniej będzie wykonywał zgodnie z oczekiwaniami.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Dla programisty # / VB. C wyszukiwania w F # #

W tej sekcji założono znasz modelu asynchronicznych w języku C# / VB. Jeśli nie, [Async programowania w języku C#](../../../csharp/async.md) stanowi punkt wyjścia.

Brak główną różnicą między C# / VB. async i F # async modelu.

Jeśli wywołasz funkcję, która zwraca `Task` lub `Task<'T>`, to zadanie zostało już uruchomione wykonywania. Zwracane dojście reprezentuje zadanie asynchroniczne już uruchomiona. Z kolei jeśli wywołasz z funkcji asynchronicznych w języku F #, `Async<'a>` zwrócił reprezentuje zadania, które będą **wygenerowany** w pewnym momencie. Opis tego modelu jest wydajne, ponieważ umożliwia zadań asynchronicznych w języku F # można je połączyć ze sobą łatwiej, wykonywane warunkowo i uruchomić z bardziej precyzyjną ziarna formantu.

Istnieje kilka podobieństwa i różnice warto zauważyć.

### <a name="similarities"></a>Podobieństwa

*   `let!`, `use!`, i `do!` są odpowiednikiem `await` podczas wywoływania metody asynchroniczne zadanie z poziomu `async{ }` bloku.

 Trzy kluczowe można używać tylko w ramach `async { }` bloku, podobnie jak `await` można wywołać tylko wewnątrz `async` metody. Krótko mówiąc `let!` dotyczy umożliwia przechwytywanie i użyć wyniku, `use!` dotyczy coś którego zasoby powinny uzyskać czyszczone po jest on używany, ale sam i `do!` jest dla, gdy chcesz czekać na przepływu pracy async o Brak wartości zwracanej, aby zakończyć Przed kontynuowaniem.

*   Język F # obsługuje równoległość danych w podobny sposób.

 Mimo że działa ona bardzo inaczej `Async.Parallel` odpowiada `Task.WhenAll` dla scenariusza pożądane wyniki zestaw zadań asynchronicznych po ukończeniu wszystkie.

### <a name="differences"></a>Różnice

*   Zagnieżdżone `let!` nie jest dozwolone, w odróżnieniu od zagnieżdżone `await`

 W odróżnieniu od `await`, które mogą być zagnieżdżane przez czas nieokreślony, `let!` nie i musi mieć wynik powiązany przed jego użyciem wewnątrz innego `let!`, `do!`, lub `use!`.

*   Obsługa anulowania jest łatwiejsze w języku F # niż w języku C# / VB.

 Obsługa anulowania połowie zadań, za pośrednictwem jej wykonanie w C# /VB wymaga sprawdzanie `IsCancellationRequested` właściwość lub wywołanie `ThrowIfCancellationRequested()` na `CancellationToken` obiekt, który jest przekazywany do metody asynchronicznej.

Z kolei więcej naturalnie możliwe są F # Asynchroniczne przepływy pracy. Anulowanie jest prosty proces trzech etapów.

1.  Utwórz nową `CancellationTokenSource`.
2.  Przekaż go do wyjścia funkcji.
3.  Wywołanie `Cancel` w tokenie.

Przykład:

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

I to już wszystko!

## <a name="further-resources"></a>Dodatkowe zasoby:

*   [Asynchroniczne przepływy pracy, w witrynie MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Asynchroniczne sekwencji dla F #](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [Narzędzia F # danych protokołu HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)
