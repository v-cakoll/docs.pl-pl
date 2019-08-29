---
title: Generowanie i używanie strumieni asynchronicznych
description: Ten zaawansowany samouczek ilustruje scenariusze, w których generowanie i zużywanie strumieni asynchronicznych zapewnia bardziej naturalny sposób pracy z sekwencjami danych, które mogą być generowane asynchronicznie.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: cd1159c139f2c885eacf55b8577bea9e79bf0d7a
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105865"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Samouczek: Generowanie i używanie strumieni asynchronicznych C# przy użyciu 8,0 i .net Core 3,0

C#8,0 wprowadza **strumienie asynchroniczne**, które modelują Źródło strumieni danych, gdy elementy w strumieniu danych mogą być pobierane lub generowane asynchronicznie. Strumienie asynchroniczne korzystają z nowych interfejsów wprowadzonych w .NET Standard 2,1 i wdrożonych w środowisku .NET Core 3,0 w celu zapewnienia naturalnego modelu programowania dla asynchronicznych źródeł danych strumieniowych.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> - Utwórz źródło danych, które generuje sekwencję elementów danych asynchronicznie.
> - Korzystaj z tego źródła danych asynchronicznie.
> - Rozpoznawaj, kiedy nowy interfejs i źródło danych są preferowane ze starszymi synchronicznymi sekwencjami danych.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0 beta. Kompilator C# 8-Beta jest dostępny począwszy od [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)lub najnowszej wersji [zapoznawczej zestawu SDK programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0). Strumienie asynchroniczne są najpierw dostępne w programie .NET Core 3,0 w wersji zapoznawczej 1.

Musisz utworzyć [token dostępu GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , aby uzyskać dostęp do punktu końcowego usługi GitHub GraphQL. Wybierz następujące uprawnienia dla tokenu dostępu usługi GitHub:

- repozytorium: stan
- public_repo

Zapisz token dostępu w bezpiecznym miejscu, aby można było go użyć w celu uzyskania dostępu do punktu końcowego interfejsu API usługi GitHub.

> [!WARNING]
> Zabezpieczanie osobistego tokenu dostępu. Każde oprogramowanie z osobistym tokenem dostępu może wykonywać wywołania interfejsu API usługi GitHub przy użyciu praw dostępu.

W C# tym samouczku założono, że wiesz już, jak i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="run-the-starter-application"></a>Uruchom aplikację Starter

Możesz uzyskać kod dla aplikacji startowej używanej w tym samouczku w repozytorium [dotnet/Samples](https://github.com/dotnet/samples) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) .

Aplikacja startowa to Aplikacja konsolowa korzystająca z interfejsu [GraphQL GitHub](https://developer.github.com/v4/) do pobierania ostatnich problemów pisanych w repozytorium [dotnet/docs](https://github.com/dotnet/docs) . Zacznij od przejrzenia następującego kodu dla metody Starter App `Main` :

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Można ustawić `GitHubKey` zmienną środowiskową na osobisty token dostępu lub zastąpić ostatni argument w wywołaniu do `GenEnvVariable` osobistego tokenu dostępu. Nie umieszczaj kodu dostępu w kodzie źródłowym, jeśli zapiszesz Źródło innym osobom lub umieścisz je w udostępnionym repozytorium źródłowym.

Po utworzeniu klienta usługi GitHub kod w programie `Main` tworzy obiekt raportowania postępu i token anulowania. Po utworzeniu tych obiektów program `Main` wywołuje `runPagedQueryAsync` w celu pobrania najnowszych utworzonych problemów 250. Po zakończeniu tego zadania zostaną wyświetlone wyniki.

Po uruchomieniu aplikacji Starter możesz wprowadzić pewne ważne uwagi dotyczące sposobu działania tej aplikacji.  Zobaczysz Postęp raportowany dla każdej strony zwróconej z usługi GitHub. Można obserwować zauważalne wstrzymanie przed zwróceniem przez usługę GitHub każdej nowej strony problemu. Na koniec problemy są wyświetlane dopiero po pobraniu 10 stron z witryny GitHub.

## <a name="examine-the-implementation"></a>Sprawdzanie implementacji

Implementacja pokazuje, dlaczego zaobserwowano zachowanie omówione w poprzedniej sekcji. Przejrzyj kod dla `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Skoncentrujemy się na algorytmie stronicowania i strukturze asynchronicznej poprzedniego kodu. (Szczegółowe informacje o interfejsie API usługi GitHub GraphQL można znaleźć w [dokumentacji usługi GitHub GraphQL](https://developer.github.com/v4/guides/) ). `runPagedQueryAsync` Metoda wylicza problemy od najnowszych do najstarszych. Żąda 25 problemów na stronę i analizuje `pageInfo` strukturę odpowiedzi, aby kontynuować z poprzednią stroną. Jest to zgodne ze standardową obsługą stronicowania GraphQL dla odpowiedzi na wiele stron. Odpowiedź zawiera `pageInfo` obiekt, który `hasPreviousPages` zawiera wartość i `startCursor` wartość użytą do żądania poprzedniej strony. Problemy znajdują się w `nodes` tablicy. `runPagedQueryAsync` Metoda dołącza te węzły do tablicy, która zawiera wszystkie wyniki ze wszystkich stron.

Po pobraniu i przywróceniu strony wyników raporty `runPagedQueryAsync` postępują i sprawdzają, czy zostały anulowane. Jeśli żądanie zostało anulowane, `runPagedQueryAsync` program <xref:System.OperationCanceledException>wygeneruje.

W tym kodzie istnieje kilka elementów, które można ulepszyć. Co najważniejsze, `runPagedQueryAsync` należy przydzielić magazyn dla wszystkich zwracanych problemów. Ten przykład zakończył się z powodu 250 problemów, ponieważ pobieranie wszystkich otwartych problemów wymagało dużo więcej pamięci do przechowywania wszystkich pobranych problemów. Ponadto protokoły obsługujące postęp i obsługa anulowania sprawiają, że algorytm jest trudniejszy do zrozumienia podczas pierwszego odczytywania. Należy poszukać klasy postępu, aby znaleźć, gdzie jest zgłaszany postęp. Konieczne jest również śledzenie komunikacji za pomocą i skojarzonych <xref:System.Threading.CancellationTokenSource> <xref:System.Threading.CancellationToken> z nią informacji o tym, gdzie żądanie anulowania zostało zażądane i gdzie jest przyznawane.

## <a name="async-streams-provide-a-better-way"></a>Strumienie asynchroniczne zapewniają lepszy sposób

Strumienie asynchroniczne i powiązane z nimi wsparcie dotyczące języka dotyczą wszystkich problemów. Kod generujący sekwencję może teraz używać `yield return` do zwracania elementów w metodzie, która została zadeklarowana `async` z modyfikatorem. Można wykorzystać strumień asynchroniczny za pomocą `await foreach` pętli tak samo jak w przypadku `foreach` użycia dowolnej sekwencji przy użyciu pętli.

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

Jednym z typów, które mogą być nieznane <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. Struktura zapewnia podobny interfejs API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> do klasy. `ValueTask` `ValueTask`jest używany w tych interfejsach ze względu na wydajność.

## <a name="convert-to-async-streams"></a>Konwertuj na strumienie asynchroniczne

Następnie Skonwertuj `runPagedQueryAsync` metodę w celu wygenerowania strumienia asynchronicznego. Najpierw Zmień sygnaturę `runPagedQueryAsync` `IAsyncEnumerable<JToken>`, aby zwracała, i Usuń tokeny anulowania i obiekty postępu z listy parametrów, jak pokazano w poniższym kodzie:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Kod początkowy przetwarza każdą stronę w miarę pobierania strony, jak pokazano w poniższym kodzie:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Zastąp te trzy wiersze następującym kodem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Możesz również usunąć deklarację `finalResults` wcześniej w tej metodzie `return` i instrukcji, która następuje po zmodyfikowanej pętli.

Zakończono wprowadzanie zmian w celu wygenerowania strumienia asynchronicznego. Metoda Final powinna wyglądać podobnie do poniższego kodu:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Następnie należy zmienić kod, który używa kolekcji, aby wykorzystać strumień asynchroniczny. Znajdź następujący kod w programie `Main` , który przetwarza zbieranie problemów:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Zastąp ten kod następującą `await foreach` pętlą:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Kod gotowego samouczka można uzyskać z repozytorium [dotnet/Samples](https://github.com/dotnet/samples) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) .

## <a name="run-the-finished-application"></a>Uruchamianie gotowej aplikacji

Uruchom aplikację ponownie. Poróżnij swoje zachowanie z zachowaniem aplikacji startowej. Pierwsza Strona wyników jest wyliczana zaraz po jej udostępnieniu. Po zażądaniu i pobraniu każdej nowej strony istnieje zauważalne wstrzymanie, a następnie wyniki następnej strony są szybko wyliczane. Blok nie jest wymagany do obsługi anulowania: obiekt wywołujący może zatrzymać Wyliczanie kolekcji. `try`  /  `catch` Postęp jest jasno raportowany, ponieważ strumień asynchroniczny generuje wyniki po pobraniu każdej strony.

Aby zobaczyć ulepszenia wykorzystania pamięci, zbadając kod. Nie trzeba już przydzielać kolekcji do przechowywania wszystkich wyników przed ich wyliczeniem. Obiekt wywołujący może określić, jak zużywać wyniki i czy wymagana jest kolekcja magazynu.

Uruchom zarówno aplikacje Starter, jak i gotowe, a także zaobserwuj różnice między implementacjami. Po zakończeniu tego samouczka możesz usunąć token dostępu usługi GitHub, który został utworzony podczas jego uruchamiania. Jeśli osoba atakująca uzyska dostęp do tego tokenu, może uzyskać dostęp do interfejsów API usługi GitHub przy użyciu swoich poświadczeń.
