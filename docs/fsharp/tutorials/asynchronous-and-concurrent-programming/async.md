---
title: Programowanie asynchroniczne
description: Dowiedz się, jak F# programowanie async odbywa się za pośrednictwem modelu programowania poziomu języka, który jest łatwy w użyciu i fizycznych dla języka.
ms.date: 06/20/2016
ms.openlocfilehash: e18697708741eef066a76bbffe35882f3639bb68
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614483"
---
# <a name="async-programming-in-f"></a>Async — Programowanie wF# #

> [!NOTE]
> Niektóre nieścisłości zostały odnalezione w tym artykule.  Jego jest modyfikowany.  Zobacz [666 # problem](https://github.com/dotnet/docs/issues/666) Aby dowiedzieć się więcej o zmianach.

Async — Programowanie w F# można osiągnąć za pomocą poziomu języka modelu programowania, mają postać łatwy w użyciu i fizycznych dla języka.

Podstawowe async — Programowanie w F# jest `Async<'T>`, reprezentacja tych prac, które mogą być wyzwalane do uruchamiania w tle, gdzie `'T` albo typ zwracany jest za pomocą specjalnych `return` — słowo kluczowe lub `unit` Jeśli asynchronicznego przepływu pracy nie ma żadnego wyniku do zwrócenia.

Kluczowe pojęcia, aby zrozumieć, że jest typ wyrażenia asynchroniczne `Async<'T>`, który jest jedynie _specyfikacji_ pracy należy wykonać w kontekście asynchronicznego. Nie jest to wykonywane, dopóki nie zostanie jawnie uruchomiony przy użyciu jednej z funkcji początkowy (takie jak `Async.RunSynchronously`). Chociaż jest to inny sposób myślenia o wykonywania pracy, kończy się ono jest bardzo proste, w praktyce.

Na przykład załóżmy, że chcesz pobrać kod HTML z dotnetfoundation.org bez blokowania wątku głównego. Można wykonać je w następujący sposób:

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

I to wszystko! Oprócz stosowania `async`, `let!`, i `return`, jest to po prostu normalne F# kodu.

Istnieje kilka syntaktycznych konstrukcji, które są warte odnotowania:

*   `let!` wiąże wynik wyrażenia asynchroniczne (który jest uruchamiany w kontekście innej).
*   `use!` działa podobnie jak w przypadku `let!`, ale usuwa jego powiązanych zasobów, gdy jej wykracza poza zakres.
*   `do!` będzie await przepływu pracy "async", która nie zwraca niczego.
*   `return` po prostu zwraca wynik wyrażenia asynchroniczne.
*   `return!` wykonuje inną asynchronicznego przepływu pracy i zwraca jego wartość zwracana w wyniku.

Ponadto normalne `let`, `use`, i `do` słów kluczowych można używać razem z wersjami async tak samo, jak w normalnym funkcji.

## <a name="how-to-start-async-code-in-f"></a>Jak uruchomić kod asynchroniczny wF# #

Jak wspomniano wcześniej, kod asynchroniczny jest określenie zadań do wykonania w innym kontekście, który musi być jawnie uruchomiona. Oto dwa podstawowe sposoby, w tym celu:

1.  `Async.RunSynchronously` uruchomi przepływ pracy asynchronicznej w innym wątku i poczekać na jego wynik.

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

2.  `Async.Start` Uruchom przepływ pracy asynchronicznej w innym wątku, a będzie **nie** poczekać na jego wynik.

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

Istnieją inne sposoby, aby uruchomić przepływ pracy async dostępne dla bardziej specyficznych scenariuszy. Są szczegółowo opisane [w odwołaniu Async](https://msdn.microsoft.com/library/ee370232.aspx).

### <a name="a-note-on-threads"></a>Uwaga dotycząca wątków

Wyrażenie "w innym wątku" został podany powyżej, ale ważne jest, aby poinformować, że **nie oznacza to, że asynchronicznymi przepływami pracy są fasada dla wielowątkowości**. Przepływ pracy faktycznie "skacze" między wątkami i finansowania ich zewnętrznego dla niewielkiej ilości czasu wykonywania użytecznej pracy. Gdy przepływ pracy asynchronicznej jest skutecznie "oczekiwanie" (np. oczekiwanie na połączenie sieciowe zwrócić coś), żadnym z wątków, który został on finansowania zewnętrznego w czasie jest zwalniana maksymalnie Przejdź użytecznej pracy na coś innego. Umożliwia asynchroniczne przepływy pracy służące do korzystają z systemu, które są uruchamiane w możliwie najbardziej efektywny sposób i udostępnianie ich w szczególnie duży dla dużej liczby operacji We/Wy scenariuszy.

## <a name="how-to-add-parallelism-to-async-code"></a>Jak dodać równoległości do kod asynchroniczny

Czasami możesz potrzebne do wykonywania wielu zadań asynchronicznych w sposób równoległy, zbieraj ich wyniki i interpretował je w jakiś sposób. `Async.Parallel` Można to zrobić bez konieczności korzystania z biblioteki równoległych zadań, która obejmowałaby konieczności wymuszone `Task<'T>` i `Async<'T>` typów.

Poniższy przykład użyje `Async.Parallel` można pobrać kod HTML z czterech popularnych witryn w sposób równoległy, poczekaj na zakończenie tych zadań, a następnie wydrukuj kodu HTML, który został pobrany.

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

## <a name="important-info-and-advice"></a>Ważne informacje i opinie

*   Dołącza się "Async" na końcu wszystkie funkcje, których będziesz używać

 Chociaż jest to po prostu konwencji nazewnictwa, jego ułatwiają elementów, takich jak odnajdywania interfejsu API. Szczególnie, jeśli są synchroniczne i asynchroniczne wersje tej samej procedury, jest dobrym pomysłem jest jawnie określać, które jest asynchroniczne za pomocą nazwy.

*   Nasłuchiwanie w kompilatorze!

 F#przez kompilator jest bardzo rygorystyczny, uniemożliwiając niemal trudne, podobnie jak coś zrobić uruchamiane synchronicznie kodu "async". Jeśli trafisz na ostrzeżenie, jest znakiem, kod nie będzie wykonanie, jak uważasz, że będą wykonywane następujące czynności. Jeśli kompilator może wprowadzić wszystkiego, Twój kod najprawdopodobniej będą wykonywane zgodnie z oczekiwaniami.

## <a name="for-the-cvb-programmer-looking-into-f"></a>Aby uzyskać C#programisty /VB przyjrzećF# #

W tej sekcji założono, znasz modelu asynchronicznych w C#/VB. Jeśli nie, [asynchroniczne Programowanie w C# ](../../../csharp/async.md) stanowi punkt wyjścia.

Jest główną różnicą między C#/VB async modelu i F# async modelu.

Gdy zostanie wywołana funkcja, która zwraca `Task` lub `Task<'T>`, że zadanie już się rozpoczęło wykonywania. Uchwyt zwracany reprezentuje zadanie asynchroniczne już działa. Z kolei jeśli wywołasz funkcji asynchronicznej F#, `Async<'a>` zwrócił reprezentuje zadanie, które będą odpowiadać **generowane** w pewnym momencie. Zrozumienie ten model jest wydajne, ponieważ umożliwia asynchroniczne zadania w F# się ze sobą sposób łatwiej, wykonywane warunkowo i uruchomić z większym ziarna kontrolki.

Istnieje kilka innych podobieństwa i różnice warte odnotowania.

### <a name="similarities"></a>Podobieństwa

*   `let!`, `use!`, i `do!` są analogiczne do `await` podczas wywoływania asynchroniczne zadanie z poziomu `async{ }` bloku.

 Trzech słów kluczowych można używać tylko wewnątrz `async { }` bloku, podobnie jak `await` można wywołać tylko wewnątrz `async` metody. Krótko mówiąc `let!` dotyczy sytuacji, gdy chcesz przechwytywać i używać ich wynik `use!` jest coś, którego zasoby powinny uzyskać czyszczone po jest używane, ale ten sam i `do!` dotyczy sytuacji, gdy chcesz czekać na przepływ pracy programu async za pomocą nie zwraca wartości, aby zakończyć Przed kontynuowaniem.

*   F#obsługuje równoległość danych w podobny sposób.

 Mimo że działa on tak bardzo inaczej `Async.Parallel` odpowiada `Task.WhenAll` scenariusza wskazujące na potrzebę wyniki zestaw zadań asynchronicznych po ich ukończeniu.

### <a name="differences"></a>Różnice

*   Zagnieżdżone `let!` nie jest dozwolone, inaczej niż w przypadku zagnieżdżonych `await`

 W odróżnieniu od `await`, które mogą być zagnieżdżane przez czas nieokreślony, `let!` nie i muszą mieć wynik powiązany przed jego użyciem wewnątrz innego `let!`, `do!`, lub `use!`.

*   Obsługę anulowania jest prostsza w F# niż w C#/VB.

 Obsługa anulowania zadania w połowie drogi za pośrednictwem jej wykonanie w C#/VB wymaga sprawdzanie `IsCancellationRequested` właściwość lub wywołanie `ThrowIfCancellationRequested()` na `CancellationToken` obiektu, który jest przekazywany do metody asynchronicznej.

Z kolei F# asynchronicznymi przepływami pracy są bardziej naturalnie można anulować. Anulowanie jest to prosty proces krok 3.

1.  Utwórz nową `CancellationTokenSource`.
2.  Przekaż go do wyjścia funkcji.
3.  Wywołaj `Cancel` w tokenie.

Przykład:

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

I to wszystko!

## <a name="further-resources"></a>Dalsze zasoby:

*   [Asynchronicznymi przepływami pracy w witrynie MSDN](https://msdn.microsoft.com/library/dd233250.aspx)
*   [Asynchroniczne sekwencji dlaF#](https://fsprojects.github.io/FSharp.Control.AsyncSeq/library/AsyncSeq.html)
*   [F#Narzędzia danych protokołu HTTP](https://fsharp.github.io/FSharp.Data/library/Http.html)