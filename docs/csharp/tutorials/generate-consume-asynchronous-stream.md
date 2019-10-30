---
title: Generowanie i używanie strumieni asynchronicznych
description: Ten zaawansowany samouczek ilustruje scenariusze, w których generowanie i zużywanie strumieni asynchronicznych zapewnia bardziej naturalny sposób pracy z sekwencjami danych, które mogą być generowane asynchronicznie.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 412e5de5d9d73846fe2af36e3def383364389c75
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039222"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Samouczek: generowanie i używanie strumieni asynchronicznych C# przy użyciu 8,0 i .net Core 3,0

C#8,0 wprowadza **strumienie asynchroniczne**, które modelują Źródło strumieni danych, gdy elementy w strumieniu danych mogą być pobierane lub generowane asynchronicznie. Strumienie asynchroniczne korzystają z nowych interfejsów wprowadzonych w .NET Standard 2,1 i wdrożonych w środowisku .NET Core 3,0 w celu zapewnienia naturalnego modelu programowania dla asynchronicznych źródeł danych strumieniowych.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
>
> - Utwórz źródło danych, które generuje sekwencję elementów danych asynchronicznie.
> - Korzystaj z tego źródła danych asynchronicznie.
> - Rozpoznawaj, kiedy nowy interfejs i źródło danych są preferowane ze starszymi synchronicznymi sekwencjami danych.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. C# 8 kompilator jest dostępny w programie [Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

Musisz utworzyć [token dostępu GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , aby uzyskać dostęp do punktu końcowego usługi GitHub GraphQL. Wybierz następujące uprawnienia dla tokenu dostępu usługi GitHub:

- repozytorium: stan
- public_repo

Zapisz token dostępu w bezpiecznym miejscu, aby można było go użyć w celu uzyskania dostępu do punktu końcowego interfejsu API usługi GitHub.

> [!WARNING]
> Zabezpieczanie osobistego tokenu dostępu. Każde oprogramowanie z osobistym tokenem dostępu może wykonywać wywołania interfejsu API usługi GitHub przy użyciu praw dostępu.

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="run-the-starter-application"></a>Uruchom aplikację Starter

Możesz uzyskać kod dla aplikacji startowej używanej w tym samouczku w repozytorium [dotnet/Samples](https://github.com/dotnet/samples) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) .

Aplikacja startowa to Aplikacja konsolowa korzystająca z interfejsu [GraphQL GitHub](https://developer.github.com/v4/) do pobierania ostatnich problemów pisanych w repozytorium [dotnet/docs](https://github.com/dotnet/docs) . Zacznij od przejrzenia następującego kodu dla metody `Main` aplikacji Starter:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Można ustawić zmienną środowiskową `GitHubKey` na osobisty token dostępu lub zastąpić ostatni argument w wywołaniu `GenEnvVariable` przy użyciu osobistego tokenu dostępu. Nie umieszczaj kodu dostępu w kodzie źródłowym, jeśli zapiszesz Źródło innym osobom lub umieścisz je w udostępnionym repozytorium źródłowym.

Po utworzeniu klienta usługi GitHub kod w `Main` tworzy obiekt raportowania postępu i token anulowania. Po utworzeniu tych obiektów `Main` wywołań `runPagedQueryAsync` w celu pobrania najnowszych utworzonych problemów 250. Po zakończeniu tego zadania zostaną wyświetlone wyniki.

Po uruchomieniu aplikacji Starter możesz wprowadzić pewne ważne uwagi dotyczące sposobu działania tej aplikacji.  Zobaczysz Postęp raportowany dla każdej strony zwróconej z usługi GitHub. Można obserwować zauważalne wstrzymanie przed zwróceniem przez usługę GitHub każdej nowej strony problemu. Na koniec problemy są wyświetlane dopiero po pobraniu 10 stron z witryny GitHub.

## <a name="examine-the-implementation"></a>Sprawdzanie implementacji

Implementacja pokazuje, dlaczego zaobserwowano zachowanie omówione w poprzedniej sekcji. Przejrzyj kod dla `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Skoncentrujemy się na algorytmie stronicowania i strukturze asynchronicznej poprzedniego kodu. (Szczegółowe informacje o interfejsie API usługi GitHub GraphQL można znaleźć w [dokumentacji usługi GitHub GraphQL](https://developer.github.com/v4/guides/) ). Metoda `runPagedQueryAsync` wylicza problemy od najnowszych do najstarszych. Żąda 25 problemów na stronę i analizuje strukturę `pageInfo` odpowiedzi, aby kontynuować z poprzednią stroną. Jest to zgodne ze standardową obsługą stronicowania GraphQL dla odpowiedzi na wiele stron. Odpowiedź zawiera `pageInfo` obiektu, który zawiera wartość `hasPreviousPages` i `startCursor` wartość użytą do żądania poprzedniej strony. Te problemy znajdują się w tablicy `nodes`. Metoda `runPagedQueryAsync` dołącza te węzły do tablicy, która zawiera wszystkie wyniki ze wszystkich stron.

Po pobraniu i przywróceniu strony wyników `runPagedQueryAsync` raporty o postępie i sprawdzaniu anulowania. Jeśli zażądano anulowania, `runPagedQueryAsync` zgłasza <xref:System.OperationCanceledException>.

W tym kodzie istnieje kilka elementów, które można ulepszyć. Co najważniejsze, `runPagedQueryAsync` musi przydzielić magazyn dla wszystkich zwracanych problemów. Ten przykład zakończył się z powodu 250 problemów, ponieważ pobieranie wszystkich otwartych problemów wymagało dużo więcej pamięci do przechowywania wszystkich pobranych problemów. Ponadto protokoły obsługujące postęp i obsługa anulowania sprawiają, że algorytm jest trudniejszy do zrozumienia podczas pierwszego odczytywania. Należy poszukać klasy postępu, aby znaleźć, gdzie jest zgłaszany postęp. Konieczne jest również śledzenie komunikacji za pośrednictwem <xref:System.Threading.CancellationTokenSource> i skojarzonych <xref:System.Threading.CancellationToken>, aby zrozumieć, w jaki sposób żądanie anulowania zostało zażądane i gdzie jest ono przyznawane.

## <a name="async-streams-provide-a-better-way"></a>Strumienie asynchroniczne zapewniają lepszy sposób

Strumienie asynchroniczne i powiązane z nimi wsparcie dotyczące języka dotyczą wszystkich problemów. Kod generujący sekwencję może teraz używać `yield return` do zwracania elementów w metodzie, która została zadeklarowana przy użyciu modyfikatora `async`. Można wykorzystać strumień asynchroniczny przy użyciu pętli `await foreach` tak samo jak w przypadku korzystania z dowolnej sekwencji przy użyciu pętli `foreach`.

Te nowe funkcje języka zależą od trzech nowych interfejsów dodanych do .NET Standard 2,1 i wdrożonych w środowisku .NET Core 3,0:

```csharp
namespace System.Collections.Generic
{
    public interface IAsyncEnumerable<out T>
    {
        IAsyncEnumerator<T> GetAsyncEnumerator(CancellationToken cancellationToken = default);
    }

    public interface IAsyncEnumerator<out T> : IAsyncDisposable
    {
        T Current { get; }

        ValueTask<bool> MoveNextAsync();
    }
}

namespace System
{
    public interface IAsyncDisposable
    {
        ValueTask DisposeAsync();
    }
}
```

Te trzy interfejsy powinny być znane dla większości C# deweloperów. Działają w sposób podobny do ich synchronicznych odpowiedników:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jednym z typów, które mogą być nieznane, jest <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. Struktura `ValueTask` zapewnia podobny interfejs API do klasy <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>. `ValueTask` jest używany w tych interfejsach ze względu na wydajność.

## <a name="convert-to-async-streams"></a>Konwertuj na strumienie asynchroniczne

Następnie Skonwertuj metodę `runPagedQueryAsync`, aby wygenerować strumień asynchroniczny. Najpierw Zmień sygnaturę `runPagedQueryAsync`, aby zwracała `IAsyncEnumerable<JToken>`, i Usuń tokeny anulowania i obiekty postępu z listy parametrów, jak pokazano w poniższym kodzie:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Kod początkowy przetwarza każdą stronę w miarę pobierania strony, jak pokazano w poniższym kodzie:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Zastąp te trzy wiersze następującym kodem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Można również usunąć deklarację `finalResults` wcześniej w tej metodzie i instrukcji `return`, która następuje po zmodyfikowanej pętli.

Zakończono wprowadzanie zmian w celu wygenerowania strumienia asynchronicznego. Metoda Final powinna wyglądać podobnie do poniższego kodu:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Następnie należy zmienić kod, który używa kolekcji, aby wykorzystać strumień asynchroniczny. Znajdź następujący kod w `Main`, który przetwarza zbieranie problemów:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Zastąp ten kod następującym `await foreach` pętlą:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Kod gotowego samouczka można uzyskać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) .

## <a name="run-the-finished-application"></a>Uruchamianie gotowej aplikacji

Uruchom aplikację ponownie. Poróżnij swoje zachowanie z zachowaniem aplikacji startowej. Pierwsza Strona wyników jest wyliczana zaraz po jej udostępnieniu. Po zażądaniu i pobraniu każdej nowej strony istnieje zauważalne wstrzymanie, a następnie wyniki następnej strony są szybko wyliczane. Blok `try`  /  `catch` nie jest wymagany do obsługi anulowania: obiekt wywołujący może zatrzymać Wyliczanie kolekcji. Postęp jest jasno raportowany, ponieważ strumień asynchroniczny generuje wyniki po pobraniu każdej strony. Stan każdego zwróconego problemu jest bezproblemowo uwzględniony w pętli `await foreach`. Obiekt wywołania zwrotnego nie jest potrzebny do śledzenia postępu.

Aby zobaczyć ulepszenia wykorzystania pamięci, zbadając kod. Nie trzeba już przydzielać kolekcji do przechowywania wszystkich wyników przed ich wyliczeniem. Obiekt wywołujący może określić, jak zużywać wyniki i czy wymagana jest kolekcja magazynu.

Uruchom zarówno aplikacje Starter, jak i gotowe, a także zaobserwuj różnice między implementacjami. Po zakończeniu tego samouczka możesz usunąć token dostępu usługi GitHub, który został utworzony podczas jego uruchamiania. Jeśli osoba atakująca uzyska dostęp do tego tokenu, może uzyskać dostęp do interfejsów API usługi GitHub przy użyciu swoich poświadczeń.
