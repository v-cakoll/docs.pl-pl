---
title: Generowanie i używanie strumieni asynchronicznych
description: W tym samouczku zaawansowane przedstawiono scenariusze, w którym generowania i używania strumieni asynchronicznych zapewnia bardziej naturalny sposób pracy z sekwencje danych, które mogą być generowane w sposób asynchroniczny.
ms.date: 02/10/2019
ms.custom: mvc
ms.openlocfilehash: 0fa7c778ca9ce0f0124fcc520dd4de65f2f92ea8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675692"
---
# <a name="tutorial-generate-and-consume-async-streams-using-c-80-and-net-core-30"></a>Samouczek: Generowanie i używanie strumieni asynchronicznych za pomocą C# 8.0 i .NET Core 3.0

C#wprowadza 8.0 **strumieni asynchronicznych**, który modelu przesyłania strumieniowego źródła danych, gdy elementy w strumieniu danych, które mogą być pobierane lub generowane asynchronicznie. Asynchroniczne strumienie polegają na nowe interfejsy wprowadzone w programie .NET Standard 2.1 i wdrażane w środowisku .NET Core 3.0 zapewnienie naturalnych modelu programowania asynchronicznego przesyłania strumieniowego źródła danych.

W tym samouczku dowiesz się, jak:

> [!div class="checklist"]
> * Utwórz źródło danych, która generuje sekwencję elementów danych asynchronicznie.
> * Asynchronicznie korzystać z tego źródła danych.
> * Rozpoznaje, gdy nowy interfejs i źródła danych są preferowane wcześniej synchronicznej danych sekwencji.

## <a name="prerequisites"></a>Wymagania wstępne

Należy skonfigurować komputer do uruchamiania platformę .NET Core, w tym C# kompilatora 8.0 beta. C# 8 kompilatora w wersji beta jest dostępna, począwszy od [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), lub r [.NET Core 3.0 (wersja zapoznawcza) zestawu SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0). Asynchroniczne strumienie najpierw są dostępne w wersji zapoznawczej platformy .NET Core 3.0 to 1.

Musisz utworzyć [token dostępu GitHub](https://help.github.com/articles/creating-a-personal-access-token-for-the-command-line/#creating-a-token) tak, aby mogli punktu końcowego usługi GitHub GraphQL. Wybierz następujące uprawnienia dla Twojego tokenu dostępu usługi GitHub:

- repozytorium: stan
- public_repo

Token dostępu należy zapisać w bezpiecznym miejscu, aby można było używać do uzyskania dostępu do punktu końcowego interfejsu API usługi GitHub.

> [!WARNING]
> Bezpieczeństwo Twój osobisty token dostępu. Wszelkie oprogramowanie za pomocą Twój osobisty token dostępu zapytała wywołań interfejsu API usługi GitHub przy użyciu Twoich praw dostępu.

W tym samouczku założono, kiedy znasz już C# i .NET, w tym Visual Studio lub interfejsu wiersza polecenia platformy .NET Core.

## <a name="run-the-starter-application"></a>Uruchom aplikację modułu uruchamiającego

Możesz też uzyskać kod aplikacji starter używanych w tym samouczku z naszych [dotnet/samples](https://github.com/dotnet/samples) repozytorium w [AsyncStreams-csharp/samouczki](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/start) folderu.

Aplikacja startowa jest aplikacja konsolowa która używa [GitHub GraphQL](https://developer.github.com/v4/) interfejsu, aby pobrać najnowsze problemy, które napisana [dotnet/docs](https://github.com/dotnet/docs) repozytorium. Zacznij od przejrzenia następujący kod dla aplikację startową `Main` metody:

[!code-csharp[StarterAppMain](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#StarterAppMain)]

Możesz albo zestaw `GitHubKey` zmiennej środowiskowej, aby Twój osobisty token dostępu, lub można zastąpić ostatni argument w wywołaniu `GenEnvVariable` z Twój osobisty token dostępu. Nie umieszczaj kod dostępu w kodzie źródłowym, będzie można zapisać źródła, czy umieszczenie go w repozytorium źródłowy udostępniony.

Po utworzeniu klienta usługi GitHub, kod w `Main` tworzy postępu raportowania obiektu i token anulowania. Po utworzeniu tych obiektów `Main` wywołania `runPagedQueryAsync` można pobrać ostatnich 250 utworzone problemów. Po zakończeniu tego zadania są wyświetlane wyniki.

Po uruchomieniu aplikacji starter ułatwia pewne istotne obserwacje dotyczące działania tej aplikacji.  Zostanie wyświetlony postęp dla każdej strony zwracane z usługi GitHub. GitHub zwraca każdej nowej strony problemy, które można obserwować zauważalne wstrzymania. Na koniec problemy są wyświetlane tylko wtedy, gdy wszystkie strony 10 zostały pobrane z witryny GitHub.

## <a name="examine-the-implementation"></a>Zapoznania się z implementacją

Wdrożenia, co spowoduje wyświetlenie Dlaczego zaobserwowane zachowanie opisanych w poprzedniej sekcji. Poszukaj w kodzie `runPagedQueryAsync`:

[!code-csharp[RunPagedQueryStarter](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#RunPagedQuery)]

Umożliwia skoncentrowanie się na strukturę algorytmu i async stronicowania dla poprzedniego kodu. (Można zapoznać się [dokumentację GitHub GraphQL](https://developer.github.com/v4/guides/) szczegółowe informacje na temat interfejsu API GraphQL usługi GitHub.) `runPagedQueryAsync` Metoda wylicza problemów od najnowszych do najstarszych. Żąda 25 problemy na każdej stronie i sprawdza, czy `pageInfo` struktury odpowiedzi, aby kontynuować z poprzedniej strony. Następujący firmy GraphQL stronicowania pomoc techniczną standard na wiele stron odpowiedzi. Odpowiedź zawiera `pageInfo` obiektu, który zawiera `hasPreviousPages` wartość i `startCursor` wartości używane do żądania na poprzedniej stronie. Problemy są w `nodes` tablicy. `runPagedQueryAsync` Metoda dołącza te węzły do tablicy, która zawiera wszystkie wyniki ze wszystkich stron.

Po ich pobierania i przywracanie strony wyników, `runPagedQueryAsync` zgłasza postępy pracy i sprawdza, czy anulowania. Jeśli zażądano anulowania, `runPagedQueryAsync` zgłasza <xref:System.OperationCanceledException>.

Istnieje kilka elementów w tym kodzie, który można zwiększyć. Co najważniejsze `runPagedQueryAsync` należy przydzielić magazyn dla wszystkich problemów, które są zwracane. W tym przykładzie zatrzymuje się na 250 problemy, ponieważ podczas pobierania wszystkich otwartych problemów wymaga znacznie większej ilości pamięci do przechowywania wszystkich pobrane problemów. Ponadto protokoły dla obsługi postępu i anulowania obsługi utrudnić algorytm zrozumieć na pierwszego czytania. Musisz sprawdzić dla klasy postęp dowiedzieć się, gdzie jest zgłaszany postępu. Musisz też śledzenia komunikacji za pośrednictwem <xref:System.Threading.CancellationTokenSource> i jego skojarzone <xref:System.Threading.CancellationToken> zrozumienie, której zażądano anulowania i gdzie otrzymuje.

## <a name="async-streams-provide-a-better-way"></a>Asynchroniczne strumienie umożliwiają lepsze

Asynchroniczne strumienie i obsługę języka skojarzone adresów wszystkie te problemy. Kod, który generuje sekwencji mogą teraz używać `yield return` do zwrócenia elementów w metodzie, która została zadeklarowana przy użyciu `async` modyfikator. Będzie można korzystać strumienia asynchronicznego przy użyciu `await foreach` pętli tak samo, jak możesz używać dowolnej sekwencji za pomocą `foreach` pętli.

Te nowe funkcje języka są zależne od trzy nowe interfejsy dodane do platformy .NET Standard 2.1 i zaimplementowane w .NET Core 3.0 to:

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

Te trzy interfejsy należy znać większość C# deweloperów. Zachowują się w sposób podobny do ich odpowiedników synchronicznego:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IEnumerator%601?displayProperty=nameWithType>
- <xref:System.IDisposable?displayProperty=nameWithType>

Jest jeden typ, który może być zaznajomiony <xref:System.Threading.Tasks.ValueTask?displayProperty=nameWithType>. `ValueTask` Struktura zapewnia podobny interfejs API, aby <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klasy. `ValueTask` jest używana w tych interfejsów ze względu na wydajność.

## <a name="convert-to-async-streams"></a>Konwertuj do strumieni asynchronicznych

Następnie przekonwertować `runPagedQueryAsync` metodę w celu wygenerowania strumień async. Najpierw Zmień podpis `runPagedQueryAsync` do zwrócenia `IAsyncEnumerable<JToken>`i Usuń obiekty anulowania tokenu i postępu na liście parametrów, jak pokazano w poniższym kodzie:

[!code-csharp[FinishedSignature](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#UpdateSignature)]

Kod startowy przetwarza każdej strony jako stronę jest pobierana, jak pokazano w poniższym kodzie:

[!code-csharp[StarterPaging](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#ProcessPage)]

Zastąp te trzy wiersze z następującym kodem:

[!code-csharp[FinishedPaging](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#YieldReturnPage)]

Można również usunąć deklaracji `finalResults` wcześniej w tej metodzie i `return` instrukcję, która następuje po pętli został zmodyfikowany.

Zmiany do generowania strumień asynchroniczne zostały ukończone. Zakończono metodę powinien wyglądać podobnie poniższy kod:

[!code-csharp[FinishedGenerate](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#GenerateAsyncStream)]

Następnie możesz zmienić kod, który korzysta z kolekcji z strumienia asynchronicznego. Znajdź następujący kod w `Main` która przetwarza zbiór problemy:

[!code-csharp[EnumerateOldStyle](~/samples/csharp/tutorials/AsyncStreams/start/IssuePRreport/IssuePRreport/Program.cs#EnumerateOldStyle)]

Zastąp kod następującym kodem `await foreach` Pętla:

[!code-csharp[FinishedEnumerateAsyncStream](~/samples/csharp/tutorials/AsyncStreams/finished/IssuePRreport/IssuePRreport/Program.cs#EnumerateAsyncStream)]

Możesz też uzyskać kod Zakończono samouczek z [dotnet/samples](https://github.com/dotnet/samples) repozytorium w [AsyncStreams-csharp/samouczki](https://github.com/dotnet/samples/tree/master/csharp/tutorials/AsyncStreams/finished) folderu.

## <a name="run-the-finished-application"></a>Uruchamianie gotowych aplikacji

Uruchom ponownie aplikację. Porównaj zachowanie z zachowaniem aplikacji starter. Pierwszej strony wyników są wyliczane, jak jest ona dostępna. Jest zauważalne Wstrzymaj każdej nowej strony są żądane i pobrać, a następnie szybko wyliczane są następnej strony wyników. `try`  /  `catch` Blok nie jest wymagane do obsługi anulowania: obiekt wywołujący może zatrzymać wyliczania kolekcji. Postęp wyraźnie jest zgłaszany, ponieważ strumienia asynchronicznego generuje wyniki, ponieważ każda strona zostanie pobrana.

Możesz zobaczyć ulepszenia wykorzystania pamięci, sprawdzając kod. Nie potrzebujesz już przydzielić kolekcji do przechowywania wszystkich wyników, zanim są teraz wyliczane. Obiekt wywołujący może ustalić, jak używać wyników i kolekcję magazynu jest potrzebna, jeśli.

Uruchom starter i gotowe aplikacje i można obserwować różnic między implementacjami dla siebie. Można usunąć tokenu dostępu usługi GitHub, zostały utworzone podczas korzystania z tego samouczka po zakończeniu. Jeśli osoba atakująca uzyska dostęp do tego tokenu, można uzyskać dostępu interfejsów API usługi GitHub przy użyciu poświadczeń.
