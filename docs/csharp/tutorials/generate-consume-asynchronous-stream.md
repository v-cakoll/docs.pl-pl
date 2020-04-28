---
title: Generowanie i używanie strumieni asynchronicznych
description: W tym zaawansowanym samouczku pokazano, jak generować strumienie asynchroniczne i korzystać z nich. Strumienie asynchroniczne zapewniają bardziej naturalny sposób pracy z sekwencjami danych, które mogą być generowane asynchronicznie.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: 03254e5208a048469f4753d632de7b0d451cde40
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200109"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Samouczek: generowanie strumieni asynchronicznych i korzystanie z nich przy użyciu języków C# 8,0 i .NET Core 3,0

W języku C# 8,0 wprowadzono **strumienie asynchroniczne**, które modelują Źródło strumieni danych. Strumienie danych często pobierają lub generują elementy asynchronicznie. Strumienie asynchroniczne korzystają z nowych interfejsów wprowadzonych w .NET Standard 2,1. Te interfejsy są obsługiwane w programie .NET Core 3,0 i nowszych. Zapewniają naturalny model programowania dla asynchronicznych źródeł danych strumieniowych.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:

> [!div class="checklist"]
>
> - Utwórz źródło danych, które generuje sekwencję elementów danych asynchronicznie.
> - Korzystaj z tego źródła danych asynchronicznie.
> - Obsługa anulowania i przechwyconych kontekstów dla strumieni asynchronicznych.
> - Rozpoznawaj, kiedy nowy interfejs i źródło danych są preferowane ze starszymi synchronicznymi sekwencjami danych.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core, w tym kompilatora C# 8,0. Kompilator języka C# 8 jest dostępny w programie [Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3,0 SDK](https://dotnet.microsoft.com/download).

Musisz utworzyć [token dostępu GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) , aby uzyskać dostęp do punktu końcowego usługi GitHub GraphQL. Wybierz następujące uprawnienia dla tokenu dostępu usługi GitHub:

- repozytorium: stan
- public_repo

Zapisz token dostępu w bezpiecznym miejscu, aby można było go użyć w celu uzyskania dostępu do punktu końcowego interfejsu API usługi GitHub.

> [!WARNING]
> Zabezpieczanie osobistego tokenu dostępu. Każde oprogramowanie z osobistym tokenem dostępu może wykonywać wywołania interfejsu API usługi GitHub przy użyciu praw dostępu.

W tym samouczku założono, że znasz języki C# i .NET, w tym Visual Studio lub interfejs wiersza polecenia platformy .NET Core.

## <a name="run-the-starter-application"></a>Uruchom aplikację Starter

Możesz uzyskać kod dla aplikacji startowej używanej w tym samouczku z repozytorium [dotnet/docs](https://github.com/dotnet/docs) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/start) .

Aplikacja startowa to Aplikacja konsolowa korzystająca z interfejsu [GraphQL GitHub](https://developer.github.com/v4/) do pobierania ostatnich problemów pisanych w repozytorium [dotnet/docs](https://github.com/dotnet/docs) . Zacznij od przejrzenia następującego kodu dla metody Starter App `Main` :

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetStarterAppMain" :::

Można ustawić zmienną `GitHubKey` środowiskową na osobisty token dostępu lub zastąpić ostatni argument w wywołaniu do `GenEnvVariable` osobistego tokenu dostępu. Nie umieszczaj kodu dostępu w kodzie źródłowym, jeśli będziesz udostępniać inne osoby. Nigdy nie przekazuj kodów dostępu do udostępnionego repozytorium źródłowego.

Po utworzeniu klienta usługi GitHub kod w programie `Main` tworzy obiekt raportowania postępu i token anulowania. Po utworzeniu tych obiektów program `Main` wywołuje `runPagedQueryAsync` w celu pobrania najnowszych utworzonych problemów 250. Po zakończeniu tego zadania zostaną wyświetlone wyniki.

Po uruchomieniu aplikacji Starter możesz wprowadzić pewne ważne uwagi dotyczące sposobu działania tej aplikacji.  Zobaczysz Postęp raportowany dla każdej strony zwróconej z usługi GitHub. Można obserwować zauważalne wstrzymanie przed zwróceniem przez usługę GitHub każdej nowej strony problemu. Na koniec problemy są wyświetlane dopiero po pobraniu 10 stron z witryny GitHub.

## <a name="examine-the-implementation"></a>Sprawdzanie implementacji

Implementacja pokazuje, dlaczego zaobserwowano zachowanie omówione w poprzedniej sekcji. Przejrzyj kod dla `runPagedQueryAsync`:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetRunPagedQuery" :::

Skoncentrujemy się na algorytmie stronicowania i strukturze asynchronicznej poprzedniego kodu. (Szczegółowe informacje o interfejsie API usługi GitHub GraphQL można znaleźć w [dokumentacji usługi GitHub GraphQL](https://developer.github.com/v4/guides/) ). `runPagedQueryAsync` Metoda wylicza problemy od najnowszych do najstarszych. Żąda 25 problemów na stronę i analizuje `pageInfo` strukturę odpowiedzi, aby kontynuować z poprzednią stroną. Jest to zgodne ze standardową obsługą stronicowania GraphQL dla odpowiedzi na wiele stron. Odpowiedź zawiera `pageInfo` obiekt, który zawiera `hasPreviousPages` wartość i `startCursor` wartość użytą do żądania poprzedniej strony. Problemy znajdują się w `nodes` tablicy. `runPagedQueryAsync` Metoda dołącza te węzły do tablicy, która zawiera wszystkie wyniki ze wszystkich stron.

Po pobraniu i przywróceniu strony wyników raporty `runPagedQueryAsync` postępują i sprawdzają, czy zostały anulowane. Jeśli żądanie zostało anulowane, `runPagedQueryAsync` program wygeneruje <xref:System.OperationCanceledException>.

W tym kodzie istnieje kilka elementów, które można ulepszyć. Co najważniejsze, `runPagedQueryAsync` należy przydzielić magazyn dla wszystkich zwracanych problemów. Ten przykład zakończył się z powodu 250 problemów, ponieważ pobieranie wszystkich otwartych problemów wymagało dużo więcej pamięci do przechowywania wszystkich pobranych problemów. Protokoły obsługujące raporty z postępów i anulowanie sprawiają, że algorytm jest trudniejszy do zrozumienia podczas pierwszego odczytywania. Są wykorzystywane więcej typów i interfejsów API. Należy śledzić komunikację za pośrednictwem programu <xref:System.Threading.CancellationTokenSource> i powiązane <xref:System.Threading.CancellationToken> z nim, aby zrozumieć, gdzie zażądano anulowania, i miejsce, w którym jest ono udzielone.

## <a name="async-streams-provide-a-better-way"></a>Strumienie asynchroniczne zapewniają lepszy sposób

Strumienie asynchroniczne i powiązane z nimi wsparcie dotyczące języka dotyczą wszystkich problemów. Kod generujący sekwencję może teraz używać `yield return` do zwracania elementów w metodzie, która została zadeklarowana z `async` modyfikatorem. Można wykorzystać strumień asynchroniczny za pomocą `await foreach` pętli tak samo jak w przypadku użycia dowolnej sekwencji przy `foreach` użyciu pętli.

Te nowe funkcje języka zależą od trzech nowych interfejsów dodanych do .NET Standard 2,1 i wdrożonych w środowisku .NET Core 3,0:

- <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>
- <xref:System.IAsyncDisposable?displayProperty=nameWithType>

Te trzy interfejsy powinny być znane dla większości deweloperów języka C#. Działają w sposób podobny do ich synchronicznych odpowiedników:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jednym z typów, które mogą być nieznane <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. `ValueTask` Struktura zapewnia podobny interfejs API do <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy. `ValueTask`jest używany w tych interfejsach ze względu na wydajność.

## <a name="convert-to-async-streams"></a>Konwertuj na strumienie asynchroniczne

Następnie Skonwertuj `runPagedQueryAsync` metodę w celu wygenerowania strumienia asynchronicznego. Najpierw Zmień sygnaturę `runPagedQueryAsync` `IAsyncEnumerable<JToken>`, aby zwracała, i Usuń tokeny anulowania i obiekty postępu z listy parametrów, jak pokazano w poniższym kodzie:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetUpdateSignature" :::

Kod początkowy przetwarza każdą stronę w miarę pobierania strony, jak pokazano w poniższym kodzie:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetProcessPage" :::

Zastąp te trzy wiersze następującym kodem:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetYieldReturnPage" :::

Możesz również usunąć deklarację `finalResults` wcześniej w tej metodzie i `return` instrukcji, która następuje po zmodyfikowanej pętli.

Zakończono wprowadzanie zmian w celu wygenerowania strumienia asynchronicznego. Metoda Final powinna wyglądać podobnie do następującego kodu:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateAsyncStream" :::

Następnie należy zmienić kod, który używa kolekcji, aby wykorzystać strumień asynchroniczny. Znajdź następujący kod w programie `Main` , który przetwarza zbieranie problemów:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/start/Program.cs" id="SnippetEnumerateOldStyle" :::

Zastąp ten kod następującą `await foreach` pętlą:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateAsyncStream" :::

Nowy interfejs <xref:System.Collections.Generic.IAsyncEnumerator%601> pochodzi od <xref:System.IAsyncDisposable>. Oznacza to, że poprzednia pętla będzie asynchronicznie zlikwidować strumień po zakończeniu pętli. Można wyobrazić pętlę, tak jak w poniższym kodzie:

```csharp
int num = 0;
var enumerator = runPagedQueryAsync(client, PagedIssueQuery, "docs").GetEnumeratorAsync();
try
{
    while (await enumerator.MoveNextAsync())
    {
        var issue = enumerator.Current;
        Console.WriteLine(issue);
        Console.WriteLine($"Received {++num} issues in total");
    }
} finally
{
    if (enumerator != null)
        await enumerator.DisposeAsync();
}
```

Domyślnie elementy strumienia są przetwarzane w przechwyconym kontekście. Jeśli chcesz wyłączyć przechwytywanie kontekstu, użyj metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł dotyczący [konsumowania wzorca asynchronicznego opartego na zadaniach](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

Strumienie asynchroniczne obsługują anulowanie przy użyciu tego samego protokołu `async` , co inne metody. Należy zmodyfikować sygnaturę dla asynchronicznej metody iteratora w następujący sposób, aby obsługiwać anulowanie:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetGenerateWithCancellation" :::

Ten <xref:System.Runtime.CompilerServices.EnumeratorCancellationAttribute?dipslayProperty=nameWithType> atrybut powoduje, <xref:System.Collections.Generic.IAsyncEnumerator%601> że kompilator generuje kod dla, który przekazuje token jako `GetAsyncEnumerator` widoczny dla treści iteratora asynchronicznego jako ten argument. Wewnątrz `runQueryAsync`można skontrolować stan tokenu i w razie żądania anulować dalsze prace.

Aby przekazać token anulowania do strumienia <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.WithCancellation%2A>asynchronicznego, należy użyć innej metody rozszerzenia. Należy zmodyfikować pętlę wyliczające problemy w następujący sposób:

:::code language="csharp" source="snippets/generate-consume-asynchronous-streams/finished/Program.cs" id="SnippetEnumerateWithCancellation" :::

Kod gotowego samouczka można uzyskać z repozytorium [dotnet/docs](https://github.com/dotnet/docs) w folderze [CSharp/samouczki/AsyncStreams](https://github.com/dotnet/docs/tree/master/csharp/tutorials/snippets/generate-consume-asynchronous-streams/finished) .

## <a name="run-the-finished-application"></a>Uruchamianie gotowej aplikacji

Uruchom ponownie aplikację. Poróżnij swoje zachowanie z zachowaniem aplikacji startowej. Pierwsza Strona wyników jest wyliczana zaraz po jej udostępnieniu. Po zażądaniu i pobraniu każdej nowej strony istnieje zauważalne wstrzymanie, a następnie wyniki następnej strony są szybko wyliczane. `try` jest wymagany do obsługi anulowania: obiekt wywołujący może zatrzymać wyliczanie  /  `catch` kolekcji. Postęp jest jasno raportowany, ponieważ strumień asynchroniczny generuje wyniki po pobraniu każdej strony. Stan każdego zwróconego problemu jest bezproblemowo zawarty w `await foreach` pętli. Obiekt wywołania zwrotnego nie jest potrzebny do śledzenia postępu.

Aby zobaczyć ulepszenia wykorzystania pamięci, zbadając kod. Nie trzeba już przydzielać kolekcji do przechowywania wszystkich wyników przed ich wyliczeniem. Obiekt wywołujący może określić, jak zużywać wyniki i czy wymagana jest kolekcja magazynu.

Uruchom zarówno aplikacje Starter, jak i gotowe, a także zaobserwuj różnice między implementacjami. Po zakończeniu tego samouczka możesz usunąć token dostępu usługi GitHub, który został utworzony podczas jego uruchamiania. Jeśli osoba atakująca uzyska dostęp do tego tokenu, może uzyskać dostęp do interfejsów API usługi GitHub przy użyciu swoich poświadczeń.
