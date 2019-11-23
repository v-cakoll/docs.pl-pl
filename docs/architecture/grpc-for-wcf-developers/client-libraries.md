---
title: Tworzenie bibliotek klienckich gRPC — gRPC dla deweloperów WCF
description: Omówienie udostępnionych bibliotek klientów/pakietów dla usług gRPC Services.
ms.date: 09/02/2019
ms.openlocfilehash: 2135fe8b24a2311a31cb2bed191d290b1112bc66
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967875"
---
# <a name="create-grpc-client-libraries"></a>Tworzenie bibliotek klienckich gRPC

Nie jest konieczne dystrybuowanie bibliotek klienckich dla aplikacji gRPC. Można utworzyć udostępnioną bibliotekę plików `.proto` w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta w swoich projektach. Ale jeśli masz prywatne repozytorium NuGet i wiele innych zespołów używa platformy .NET Core, tworzenie i publikowanie pakietów NuGet klienta w ramach projektu usługi może być dobrym sposobem udostępniania i promowania usługi.

Jedną z zalet dystrybucji biblioteki klienta jest możliwość udoskonalenia wygenerowanych klas gRPC i protobuf przy użyciu przydatnych metod i właściwości. W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są deklarowane jako `partial`, aby można je było rozwijać bez konieczności edytowania wygenerowanego kodu. Oznacza to, że można łatwo dodawać konstruktory, metody, właściwości obliczeniowe i nie tylko do typów podstawowych.

> [!CAUTION]
> **Nie** należy używać niestandardowego kodu w celu zapewnienia podstawowych funkcji, ponieważ oznacza to, że funkcje byłyby ograniczone do zespołów .NET korzystających z biblioteki udostępnionej, a nie do zespołów korzystających z innych języków lub platform, takich jak Python lub Java.

W środowisku z wieloma platformami, w których różne zespoły często korzystają z różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie, wystarczy udostępnić pliki `.proto`, aby deweloperzy mogli generować własnych klientów, najlepszym sposobem zapewnienia, że wiele zespołów może uzyskać dostęp do usługi gRPC.

## <a name="useful-extensions"></a>Przydatne rozszerzenia

Istnieją dwa powszechnie używane interfejsy w programie .NET do obsługi strumieni obiektów: <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IObservable%601>. Począwszy od platformy .NET Core 3,0 C# i 8,0, istnieje <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs do przetwarzania strumieni asynchronicznie i składnia `await foreach` do korzystania z interfejsu. Ta sekcja przedstawia kod wielokrotnego użytku do zastosowania tych interfejsów do strumieni gRPC.

W przypadku bibliotek klienckich programu .NET Core gRPC istnieje `ReadAllAsync` Metoda rozszerzająca `IAsyncStreamReader<T>`, która tworzy `IAsyncEnumerable<T>`. W przypadku deweloperów korzystających z samoczynnego programowania, równoważna Metoda rozszerzenia do tworzenia `IObservable<T>` może wyglądać następująco.

### <a name="iobservable"></a>IObservable

Interfejs `IObservable<T>` to "Reactive" Reverse `IEnumerable<T>`. Zamiast ściągania elementów ze strumienia, podejście reaktywne umożliwia wypychanie elementów do subskrybenta. Jest to bardzo podobne do gRPC strumieni i jest łatwo otoczyć `IObservable<T>` wokół `IAsyncStreamReader<T>`.

Ten kod jest dłuższy niż kod `IAsyncEnumerable<T>`, ponieważ C# nie ma wbudowanej obsługi pracy z observables, więc należy utworzyć klasę implementacji ręcznie. Jest to Klasa generyczna, dlatego jedna implementacja będzie działała dla wszystkich typów.

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
> Ta niezauważalna implementacja umożliwia tylko jednokrotne wywołanie metody `Subscribe`, co sprawia, że wielu subskrybentów próbujących odczytać dane ze strumienia mógłby spowodować chaos. Istnieją operatory, takie jak `Replay` w [System. Reactive. LINQ](https://www.nuget.org/packages/System.Reactive.Linq) , które umożliwiają buforowanie i powtarzanie udostępniania observables, które mogą być używane z tą implementacją.

Klasa `GrpcStreamSubscription` obsługuje wyliczanie `IAsyncStreamReader`.

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

Wszystkie wymagane teraz jest prostą metodą rozszerzenia, aby można było uzyskać zauważalność z czytnika strumienia.

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

Modele `IAsyncEnumerable` i `IObservable` są dobrze obsługiwane i dobrze udokumentowane sposoby postępowania z asynchronicznymi strumieniami danych w programie .NET. Mapa gRPC strumienie w obu odmianach oferuje bliską integrację z nowoczesnymi i nieaktywnymi/asynchronicznymi stylami programowania.

>[!div class="step-by-step"]
>[Poprzedni](streaming-versus-repeated.md)
>[Następny](security.md)
