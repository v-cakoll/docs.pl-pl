---
title: Tworzenie bibliotek klientów gRPC - gRPC dla programistów WCF
description: Omówienie udostępnionych bibliotek klienckich/pakietów dla usług gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401670"
---
# <a name="create-grpc-client-libraries"></a>Tworzenie bibliotek klientów gRPC

Nie jest konieczne rozpowszechnianie bibliotek klientów dla aplikacji gRPC. Można utworzyć udostępnioną `.proto` bibliotekę plików w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta we własnych projektach. Ale jeśli masz prywatne repozytorium NuGet i wiele innych zespołów używa .NET Core, można tworzyć i publikować pakiety NuGet klienta w ramach projektu usługi. Może to być dobry sposób dzielenia się i promowania swojej usługi.

Jedną z zalet dystrybucji biblioteki klienta jest to, że można zwiększyć wygenerowane klasy gRPC i Protobuf z pomocnymi metodami i właściwościami "wygody". W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są zadeklarowane jako `partial`, dzięki czemu można je rozszerzyć bez edytowania wygenerowanego kodu. Oznacza to, że łatwo jest dodać konstruktory, metody i właściwości obliczeniowe do typów podstawowych.

> [!CAUTION]
> Nie należy używać kodu niestandardowego, aby zapewnić podstawowe funkcje. Nie chcesz ograniczać tej podstawowej funkcji do zespołów .NET, które używają biblioteki udostępnionej, i nie udostępniać jej zespołom, które używają innych języków lub platform, takich jak Python lub Java.

Upewnij się, że jak najwięcej zespołów może uzyskać dostęp do usługi gRPC. Najlepszym sposobem, aby to `.proto` zrobić jest udostępnianie plików, dzięki czemu deweloperzy mogą generować własnych klientów. Jest to szczególnie prawdziwe w środowisku wielu platform, gdzie różne zespoły często używają różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie.

## <a name="useful-extensions"></a>Przydatne rozszerzenia

Istnieją dwa powszechnie używane interfejsy w .NET do radzenia <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>sobie ze strumieniami obiektów: i . Począwszy od .NET Core 3.0 i C# <xref:System.Collections.Generic.IAsyncEnumerable%601> 8.0, istnieje interfejs do przetwarzania `await foreach` strumieni asynchronicznie i składni za pomocą interfejsu. W tej sekcji przedstawiono kod wielokrotnego użytku do stosowania tych interfejsów do strumieni gRPC.

Z .NET Core gRPC bibliotek klienta istnieje `ReadAllAsync` metoda `IAsyncStreamReader<T>` rozszerzenia, `IAsyncEnumerable<T>` który tworzy interfejs. Dla deweloperów korzystających z programowania reaktywnego `IObservable<T>` równoważna metoda rozszerzenia do tworzenia interfejsu może wyglądać jak w przykładzie w poniższej sekcji.

### <a name="iobservable"></a>Iobservable

Interfejs `IObservable<T>` jest "reaktywną" odwrotnością `IEnumerable<T>`. Zamiast ściągać elementy ze strumienia, podejście reaktywne umożliwia przepływanie elementów strumienia do subskrybenta. Jest to bardzo podobne do strumieni gRPC i łatwo `IObservable<T>` jest `IAsyncStreamReader<T>` owinąć interfejs wokół interfejsu.

Ten kod jest `IAsyncEnumerable<T>` dłuższy niż kod, ponieważ c# nie ma wbudowanej obsługi pracy z obserwowalnych. Musisz ręcznie utworzyć klasę implementacji. Jest to klasa ogólna, więc pojedyncza implementacja działa we wszystkich typach.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public Observable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> Ta obserwowana `Subscribe` implementacja umożliwia metodę, która ma być wywoływana tylko raz, ponieważ posiadanie wielu subskrybentów próbujących odczytać ze strumienia spowodowałoby chaos. Istnieją operatory, `Replay` takie jak [system.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), które umożliwiają buforowanie i powtarzalne udostępnianie obserwowalnych, które mogą być używane z tą implementacją.

Klasa `GrpcStreamSubscription` obsługuje wyliczenie `IAsyncStreamReader`:

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public Subscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

Wszystko, co jest wymagane teraz jest prosta metoda rozszerzenia, aby utworzyć obserwowalne z czytnika strumienia.

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a>Podsumowanie

Modele `IAsyncEnumerable` `IObservable` i są dobrze obsługiwane i dobrze udokumentowane sposoby radzenia sobie z asynchronicznych strumieni danych w .NET. Strumienie gRPC dobrze mapują zarówno paradygmaty, oferując ścisłą integrację z .NET Core, jak i reaktywne i asynchroniczne style programowania.

>[!div class="step-by-step"]
>[Poprzedni](streaming-versus-repeated.md)
>[następny](security.md)
