---
title: Generowanie i korzystanie ze strumieni asynchronicznego
description: Ten zaawansowany samouczek ilustruje scenariusze, w których generowanie i używanie strumieni asynchronicznych zapewnia bardziej naturalny sposób pracy z sekwencjami danych, które mogą być generowane asynchronicznie.
ms.date: 02/10/2019
ms.technology: csharp-async
ms.custom: mvc
ms.openlocfilehash: de090eb9cc1e8b511956313ab5169ee4d07a492f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156743"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Samouczek: Generowanie i używanie strumieni asynchronicznyprzy użyciu plików C# 8.0 i .NET Core 3.0

C# 8.0 wprowadza **strumienia asynchronicznego**, które modelują źródło przesyłania strumieniowego danych, gdy elementy w strumieniu danych mogą być pobierane lub generowane asynchronicznie. Strumienie asynchroniczne opierają się na nowych interfejsach wprowadzonych w programie .NET Standard 2.1 i zaimplementowanych w programie .NET Core 3.0 w celu zapewnienia naturalnego modelu programowania dla asynchronicznych źródeł danych strumieniowych.

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:

> [!div class="checklist"]
>
> - Utwórz źródło danych, które generuje sekwencję elementów danych asynchronicznie.
> - Użyj tego źródła danych asynchronicznie.
> - Rozpoznaj, kiedy nowy interfejs i źródło danych są preferowane do wcześniejszych synchronicznych sekwencji danych.

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET Core, w tym kompilator C# 8.0. Kompilator C# 8 jest dostępny począwszy od [programu Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download).

Musisz utworzyć [token dostępu GitHub,](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) aby uzyskać dostęp do punktu końcowego GitHub GraphQL. Wybierz następujące uprawnienia tokenu dostępu usługi GitHub:

- repo:stan
- public_repo

Zapisz token dostępu w bezpiecznym miejscu, dzięki czemu można go użyć, aby uzyskać dostęp do punktu końcowego interfejsu API usługi GitHub.

> [!WARNING]
> Zabezpiecz swój osobisty token dostępu. Każde oprogramowanie z osobistym tokenem dostępu może sprawić, że wywołania interfejsu API usługi GitHub przy użyciu praw dostępu.

W tym samouczku przyjęto założenie, że znasz c# i .NET, w tym visual studio lub .NET Core CLI.

## <a name="run-the-starter-application"></a>Uruchamianie aplikacji startowej

Możesz uzyskać kod dla aplikacji startowej używanej w tym samouczku z naszego repozytorium [dotnet/samples](https://github.com/dotnet/samples) w folderze [csharp/tutorials/AsyncStreams.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start)

Aplikacja startowa to aplikacja konsolowa, która używa interfejsu [GitHub GraphQL](https://developer.github.com/v4/) do pobierania ostatnich problemów zapisanych w repozytorium [dotnet/docs.](https://github.com/dotnet/docs) Zacznij od spokozić `Main` następujący kod dla metody aplikacji początkowej:

[!code-csharp[StarterAppMain](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Można ustawić zmienną środowiskową `GitHubKey` na token dostępu osobistego lub zastąpić ostatni `GenEnvVariable` argument w wywołaniu tokenem dostępu osobistego. Nie umieszczaj kodu dostępu w kodzie źródłowym, jeśli będziesz zapisywać źródło z innymi osobami lub umieszczać go w udostępnionym repozytorium źródłowym.

Po utworzeniu klienta GitHub, `Main` kod w tworzy obiekt raportowania postępu i token anulowania. Po utworzeniu tych `Main` obiektów `runPagedQueryAsync` wywołania w celu pobrania ostatnich 250 utworzonych problemów. Po zakończeniu tego zadania zostaną wyświetlone wyniki.

Po uruchomieniu aplikacji startowej, można dokonać pewnych ważnych uwag na temat sposobu działania tej aplikacji.  Zobaczysz postęp zgłoszony dla każdej strony zwróconej z Usługi GitHub. Można zaobserwować zauważalną pauzę, zanim gitHub zwróci każdą nową stronę problemów. Na koniec problemy są wyświetlane dopiero po pobraniu wszystkich 10 stron z usługi GitHub.

## <a name="examine-the-implementation"></a>Zbadaj wdrażanie

Implementacja ujawnia, dlaczego zaobserwowałeś zachowanie omówione w poprzedniej sekcji. Sprawdź kod `runPagedQueryAsync`pod kątem:

[!code-csharp[RunPagedQueryStarter](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Skoncentrujmy się na algorytmstronicowania i struktury asynchronicznej poprzedniego kodu. (Szczegółowe informacje na temat interfejsu API Programu GitHub GraphQL można znaleźć w [dokumentacji programu GitHub GraphQL).](https://developer.github.com/v4/guides/) Metoda `runPagedQueryAsync` wylicza problemy od najnowszych do najstarszych. Żąda 25 problemów na stronie `pageInfo` i analizuje strukturę odpowiedzi, aby kontynuować na poprzedniej stronie. Wynika to ze standardowej obsługi stronicowania graphql dla odpowiedzi wielostronicowych. Odpowiedź zawiera `pageInfo` obiekt, który `hasPreviousPages` zawiera `startCursor` wartość i wartość używaną do żądania poprzedniej strony. Problemy są w `nodes` tablicy. Metoda `runPagedQueryAsync` dołącza te węzły do tablicy, która zawiera wszystkie wyniki ze wszystkich stron.

Po pobraniu i przywróceniu `runPagedQueryAsync` strony wyników raportuje postęp i sprawdza anulowanie. Jeśli zażądano anulowania, `runPagedQueryAsync` zgłasza <xref:System.OperationCanceledException>plik .

Istnieje kilka elementów w tym kodzie, które można poprawić. Co najważniejsze, `runPagedQueryAsync` należy przydzielić magazyn dla wszystkich zwróconych problemów. W tym przykładzie zatrzymuje się na 250 problemów, ponieważ pobieranie wszystkich otwartych problemów wymagałoby znacznie więcej pamięci do przechowywania wszystkich pobranych problemów. Ponadto protokoły dotyczące obsługi postępu i obsługi anulowania sprawiają, że algorytm jest trudniejszy do zrozumienia podczas pierwszego czytania. Należy wyszukać klasę postępu, aby znaleźć, gdzie jest raportowany postęp. Należy również prześledzić komunikacji <xref:System.Threading.CancellationTokenSource> za pośrednictwem i skojarzonych z <xref:System.Threading.CancellationToken> nią, aby zrozumieć, gdzie wymagane jest anulowanie i gdzie jest to przyznane.

## <a name="async-streams-provide-a-better-way"></a>Strumienie Async zapewniają lepszy sposób

Strumienie asynchroniczne i obsługa skojarzonego języka rozwiązają wszystkie te problemy. Kod, który generuje sekwencję `yield return` można teraz użyć do zwrócenia `async` elementów w metodzie, która została zadeklarowana za pomocą modyfikatora. Można użyć strumienia asynchronicznego przy użyciu `await foreach` pętli, `foreach` tak jak zużywają dowolną sekwencję przy użyciu pętli.

Te nowe funkcje języka zależą od trzech nowych interfejsów dodanych do .NET Standard 2.1 i zaimplementowanych w .NET Core 3.0:

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

Te trzy interfejsy powinny być znane większości deweloperów języka C#. Zachowują się w sposób podobny do ich synchronicznych odpowiedników:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jeden typ, który może <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>być nieznany jest . Struktura `ValueTask` zapewnia podobny interfejs API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> do klasy. `ValueTask`jest używany w tych interfejsach ze względu na wydajność.

## <a name="convert-to-async-streams"></a>Konwertowanie na strumienie asynchroniczne

Następnie przekonwertuj `runPagedQueryAsync` metodę, aby wygenerować strumień asynchronicznego. Najpierw zmień `runPagedQueryAsync` `IAsyncEnumerable<JToken>`podpis, aby zwrócić , i usunąć token anulowania i obiektów postępu z listy parametrów, jak pokazano w następującym kodzie:

[!code-csharp[FinishedSignature](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Kod początkowy przetwarza każdą stronę podczas pobierania strony, jak pokazano w poniższym kodzie:

[!code-csharp[StarterPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Zastąp te trzy wiersze następującym kodem:

[!code-csharp[FinishedPaging](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Można również usunąć deklarację `finalResults` wcześniej w tej `return` metodzie i instrukcji, która następuje po pętli, który został zmodyfikowany.

Zmiany zostały zakończone w celu wygenerowania strumienia asynchronicznego. Metoda gotowapowinna przypominać poniższy kod:

[!code-csharp[FinishedGenerate](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Następnie należy zmienić kod, który używa kolekcji do używania strumienia asynchronicznego. Znajdź następujący kod `Main` w tym, który przetwarza kolekcję problemów:

[!code-csharp[EnumerateOldStyle](~/samples/snippets/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Zastąp ten `await foreach` kod następującą pętlą:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/snippets/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Domyślnie elementy strumienia są przetwarzane w kontekście przechwyconego. Jeśli chcesz wyłączyć przechwytywanie kontekstu, należy użyć metody <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> rozszerzenia. Aby uzyskać więcej informacji na temat kontekstów synchronizacji i przechwytywania bieżącego kontekstu, zobacz artykuł na [temat korzystania z wzorca asynchronicznego opartego](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md)na zadaniu .

Kod gotowego samouczka można uzyskać z repozytorium [dotnet/samples](https://github.com/dotnet/samples) w folderze [csharp/tutorials/AsyncStreams.](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished)

## <a name="run-the-finished-application"></a>Uruchamianie gotowej aplikacji

Uruchom ponownie aplikację. Kontrast jego zachowanie z zachowaniem aplikacji starter. Pierwsza strona wyników jest wyliczana, gdy tylko będzie dostępna. Istnieje obserwowana pauza, ponieważ każda nowa strona jest żądana i pobierana, a następnie wyniki następnej strony są szybko wyliczane. `try`  /  Blok `catch` nie jest potrzebny do obsługi anulowania: obiekt wywołujący może przestać wyliczania kolekcji. Postęp jest wyraźnie zgłaszane, ponieważ strumień asynchronii generuje wyniki, jak każda strona jest pobierana. Stan dla każdego zwróconego problemu jest `await foreach` bezproblemowo uwzględniany w pętli. Do śledzenia postępów nie jest potrzebny obiekt wywołania oddzwonić.

Można zobaczyć ulepszenia w użyciu pamięci, sprawdzając kod. Nie trzeba już przydzielić kolekcji do przechowywania wszystkich wyników, zanim zostaną one wyliczone. Obiekt wywołujący można określić, jak korzystać z wyników i jeśli kolekcja magazynu jest potrzebna.

Uruchom zarówno starter i gotowe aplikacje i można obserwować różnice między implementacjami dla siebie. Możesz usunąć token dostępu GitHub utworzony po uruchomieniu tego samouczka po zakończeniu. Jeśli osoba atakująca uzyskała dostęp do tego tokenu, może uzyskać dostęp do interfejsów API usługi GitHub przy użyciu poświadczeń.
