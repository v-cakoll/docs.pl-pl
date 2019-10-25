---
title: Tworzenie bibliotek klienckich gRPC — gRPC dla deweloperów WCF
description: Omówienie udostępnionych bibliotek klientów/pakietów dla usług gRPC Services.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 12c628d2b58199a8103c60aa123bb75a34e0797d
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846702"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="afe0f-103">Tworzenie bibliotek klienckich gRPC</span><span class="sxs-lookup"><span data-stu-id="afe0f-103">Create gRPC client libraries</span></span>

<span data-ttu-id="afe0f-104">Nie jest konieczne dystrybuowanie bibliotek klienckich dla aplikacji gPRC.</span><span class="sxs-lookup"><span data-stu-id="afe0f-104">It isn't necessary to distribute client libraries for a gPRC application.</span></span> <span data-ttu-id="afe0f-105">Można utworzyć udostępnioną bibliotekę plików `.proto` w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta w swoich projektach.</span><span class="sxs-lookup"><span data-stu-id="afe0f-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="afe0f-106">Ale jeśli masz prywatne repozytorium NuGet i wiele innych zespołów używa platformy .NET Core, tworzenie i publikowanie pakietów NuGet klienta w ramach projektu usługi może być dobrym sposobem udostępniania i promowania usługi.</span><span class="sxs-lookup"><span data-stu-id="afe0f-106">But if you have a private NuGet repository and many other teams are using .NET Core, creating and publishing client NuGet packages as part of your service project may be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="afe0f-107">Jedną z zalet dystrybucji biblioteki klienta jest możliwość udoskonalenia wygenerowanych klas gRPC i protobuf przy użyciu przydatnych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="afe0f-107">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="afe0f-108">W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są deklarowane jako `partial`, aby można je było rozwijać bez konieczności edytowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="afe0f-108">In the client code, as in the server, all the classes are declared as `partial` so you can extend them without editing the generated code.</span></span> <span data-ttu-id="afe0f-109">Oznacza to, że można łatwo dodawać konstruktory, metody, właściwości obliczeniowe i nie tylko do typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="afe0f-109">This means it's easy to add constructors, methods, calculated properties, and more to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="afe0f-110">**Nie** należy używać niestandardowego kodu w celu zapewnienia podstawowych funkcji, ponieważ oznacza to, że funkcje byłyby ograniczone do zespołów .NET korzystających z biblioteki udostępnionej, a nie do zespołów korzystających z innych języków lub platform, takich jak Python lub Java.</span><span class="sxs-lookup"><span data-stu-id="afe0f-110">You should **not** use custom code to provide essential functionality, as this would mean that functionality would be restricted to .NET teams using the shared library, and not to teams using other languages or platforms such as Python or Java.</span></span>

<span data-ttu-id="afe0f-111">W środowisku wieloplatformowym, w którym różne zespoły często korzystają z różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie, wystarczy udostępnić pliki `.proto`, aby deweloperzy mogli generować własnych klientów, najlepszym sposobem na zapewnienie tak wiele zespołów, jak to możliwe, może uzyskać dostęp do usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="afe0f-111">In a multi-platform environment where different teams frequently use different programming languages and frameworks, or where your API is externally accessible, simply sharing `.proto` files so developers can generate their own clients is the best way to ensure as many teams as possible can access your gRPC service.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="afe0f-112">Przydatne rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="afe0f-112">Useful extensions</span></span>

<span data-ttu-id="afe0f-113">Istnieją dwa powszechnie używane interfejsy w programie .NET do obsługi strumieni obiektów: <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="afe0f-113">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="afe0f-114">Począwszy od platformy .NET Core 3,0 C# i 8,0, istnieje<xref:System.Collections.Generic.IAsyncEnumerable%601>interfejs do przetwarzania strumieni asynchronicznie i składnia`await foreach`do korzystania z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="afe0f-114">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="afe0f-115">Ta sekcja przedstawia kod wielokrotnego użytku do zastosowania tych interfejsów do strumieni gRPC.</span><span class="sxs-lookup"><span data-stu-id="afe0f-115">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="afe0f-116">W przypadku bibliotek klienckich programu .NET Core gRPC istnieje `ReadAllAsync` Metoda rozszerzająca `IAsyncStreamReader<T>`, która tworzy `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="afe0f-116">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>`.</span></span> <span data-ttu-id="afe0f-117">W przypadku deweloperów korzystających z samoczynnego programowania, równoważna Metoda rozszerzenia do tworzenia `IObservable<T>` może wyglądać następująco.</span><span class="sxs-lookup"><span data-stu-id="afe0f-117">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` might look like this.</span></span>

### <a name="iobservable"></a><span data-ttu-id="afe0f-118">IObservable</span><span class="sxs-lookup"><span data-stu-id="afe0f-118">IObservable</span></span>

<span data-ttu-id="afe0f-119">Interfejs `IObservable<T>` to "Reactive" Reverse `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="afe0f-119">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="afe0f-120">Zamiast ściągania elementów ze strumienia, podejście reaktywne umożliwia wypychanie elementów do subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="afe0f-120">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="afe0f-121">Jest to bardzo podobne do gRPC strumieni i jest łatwo otoczyć `IObservable<T>` wokół `IAsyncStreamReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="afe0f-121">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` around an `IAsyncStreamReader<T>`.</span></span>

<span data-ttu-id="afe0f-122">Ten kod jest dłuższy niż kod `IAsyncEnumerable<T>`, ponieważ C# nie ma wbudowanej obsługi pracy z observables, więc należy utworzyć klasę implementacji ręcznie.</span><span class="sxs-lookup"><span data-stu-id="afe0f-122">This code is longer than the `IAsyncEnumerable<T>` code because C# doesn't have built-in support for working with observables, so the implementation class has to be created manually.</span></span> <span data-ttu-id="afe0f-123">Jest to Klasa generyczna, dlatego jedna implementacja będzie działała dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="afe0f-123">It's a generic class, though, so a single implementation will work across all types.</span></span>

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
> <span data-ttu-id="afe0f-124">Ta niezauważalna implementacja umożliwia tylko jednokrotne wywołanie metody `Subscribe`, co sprawia, że wielu subskrybentów próbujących odczytać dane ze strumienia mógłby spowodować chaos.</span><span class="sxs-lookup"><span data-stu-id="afe0f-124">This observable implementation only allows the `Subscribe` method to be called once, as having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="afe0f-125">Istnieją operatory, takie jak `Replay` w [System. Reactive. LINQ](https://www.nuget.org/packages/System.Reactive.Linq) , które umożliwiają buforowanie i powtarzanie udostępniania observables, które mogą być używane z tą implementacją.</span><span class="sxs-lookup"><span data-stu-id="afe0f-125">There are operators such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq) that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="afe0f-126">Klasa `GrpcStreamSubscription` obsługuje wyliczanie `IAsyncStreamReader`.</span><span class="sxs-lookup"><span data-stu-id="afe0f-126">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`.</span></span>

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

<span data-ttu-id="afe0f-127">Wszystkie wymagane teraz jest prostą metodą rozszerzenia, aby można było uzyskać zauważalność z czytnika strumienia.</span><span class="sxs-lookup"><span data-stu-id="afe0f-127">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="afe0f-128">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="afe0f-128">Summary</span></span>

<span data-ttu-id="afe0f-129">Modele `IAsyncEnumerable` i `IObservable` są dobrze obsługiwane i dobrze udokumentowane sposoby postępowania z asynchronicznymi strumieniami danych w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="afe0f-129">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="afe0f-130">Mapa gRPC strumienie w obu odmianach oferuje bliską integrację z nowoczesnymi i nieaktywnymi/asynchronicznymi stylami programowania.</span><span class="sxs-lookup"><span data-stu-id="afe0f-130">gRPC streams map well to both paradigms, offering close integration with the modern .NET Core framework and reactive/asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="afe0f-131">[Poprzedni](streaming-versus-repeated.md)
>[Następny](security.md)</span><span class="sxs-lookup"><span data-stu-id="afe0f-131">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
