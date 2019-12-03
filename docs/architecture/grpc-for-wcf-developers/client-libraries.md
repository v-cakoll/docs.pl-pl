---
title: Tworzenie bibliotek klienckich gRPC — gRPC dla deweloperów WCF
description: Omówienie udostępnionych bibliotek klientów/pakietów dla usług gRPC Services.
ms.date: 09/02/2019
ms.openlocfilehash: bb58cb3cda4b0cbb3a5d34129961349bcb0093e9
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711454"
---
# <a name="create-grpc-client-libraries"></a>Tworzenie bibliotek klienckich gRPC

Nie jest konieczne dystrybuowanie bibliotek klienckich dla aplikacji gRPC. Można utworzyć udostępnioną bibliotekę plików `.proto` w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta w swoich projektach. Jeśli jednak masz prywatne repozytorium NuGet i wiele innych zespołów używa platformy .NET Core, możesz tworzyć i publikować pakiety NuGet klienta w ramach projektu usługi. Może to być dobry sposób udostępniania i promowania usługi.

Jedną z zalet dystrybucji biblioteki klienta jest możliwość udoskonalenia wygenerowanych klas gRPC i protobuf przy użyciu przydatnych metod i właściwości. W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są deklarowane jako `partial`, więc można je zwiększyć bez konieczności edytowania wygenerowanego kodu. Oznacza to, że można łatwo dodać konstruktory, metody i właściwości obliczeniowe do typów podstawowych.

> [!CAUTION]
> Nie należy używać niestandardowego kodu w celu zapewnienia zasadniczych funkcji. Nie chcesz ograniczyć tej funkcji do zespołów .NET, które korzystają z biblioteki udostępnionej, i nie udostępniaj jej zespołom korzystającym z innych języków lub platform, takich jak Python lub Java.

Upewnij się, że możliwie jak najwięcej zespołów może uzyskać dostęp do usługi gRPC. Najlepszym sposobem jest udostępnienie `.proto` plików, aby deweloperzy mogli generować własnych klientów. Jest to szczególnie prawdziwe w środowisku wieloplatformowym, w którym różne zespoły często używają różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie.

## <a name="useful-extensions"></a>Przydatne rozszerzenia

Istnieją dwa powszechnie używane interfejsy w programie .NET do obsługi strumieni obiektów: <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IObservable%601>. Począwszy od platformy .NET Core 3,0 C# i 8,0, istnieje <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs do przetwarzania strumieni asynchronicznie i składnia `await foreach` do korzystania z interfejsu. Ta sekcja przedstawia kod wielokrotnego użytku do zastosowania tych interfejsów do strumieni gRPC.

W przypadku bibliotek klienckich programu .NET Core gRPC istnieje `ReadAllAsync` Metoda rozszerzająca `IAsyncStreamReader<T>`, która tworzy interfejs `IAsyncEnumerable<T>`. W przypadku deweloperów korzystających z samoczynnego programowania, równoważna Metoda rozszerzenia do utworzenia interfejsu `IObservable<T>` może wyglądać podobnie do przykładu w poniższej sekcji.

### <a name="iobservable"></a>IObservable

Interfejs `IObservable<T>` to "Reactive" Reverse `IEnumerable<T>`. Zamiast ściągania elementów ze strumienia, podejście reaktywne umożliwia wypychanie elementów do subskrybenta. Jest to bardzo podobne do gRPC strumieni i można łatwo otoczyć interfejs `IObservable<T>` wokół interfejsu `IAsyncStreamReader<T>`.

Ten kod jest dłuższy niż kod `IAsyncEnumerable<T>`, ponieważ C# nie ma wbudowaną obsługę pracy z observables. Musisz ręcznie utworzyć klasę implementacji. Jest to Klasa generyczna, dlatego jedna implementacja działa dla wszystkich typów.

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
> Ta zazauważalna implementacja umożliwia wywoływanie metody `Subscribe` tylko raz, ponieważ wielu subskrybentów próbujących odczytać dane ze strumienia spowodowałaby chaos. Istnieją operatory, takie jak `Replay` w [System. Reactive. LINQ](https://www.nuget.org/packages/System.Reactive.Linq), które umożliwiają buforowanie i powtarzanie udostępniania observables, które mogą być używane z tą implementacją.

Klasa `GrpcStreamSubscription` obsługuje Wyliczenie `IAsyncStreamReader`:

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

Modele `IAsyncEnumerable` i `IObservable` są dobrze obsługiwane i dobrze udokumentowane sposoby postępowania z asynchronicznymi strumieniami danych w programie .NET. gRPC strumienie są dobrze mapowane w obu odmianach, oferując bliską integrację z programem .NET Core oraz z aktywnymi i asynchronicznymi stylami programowania.

>[!div class="step-by-step"]
>[Poprzednie](streaming-versus-repeated.md)
>[dalej](security.md)
