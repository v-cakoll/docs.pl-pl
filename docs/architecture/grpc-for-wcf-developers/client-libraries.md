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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="0067a-103">Tworzenie bibliotek klientów gRPC</span><span class="sxs-lookup"><span data-stu-id="0067a-103">Create gRPC client libraries</span></span>

<span data-ttu-id="0067a-104">Nie jest konieczne rozpowszechnianie bibliotek klientów dla aplikacji gRPC.</span><span class="sxs-lookup"><span data-stu-id="0067a-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="0067a-105">Można utworzyć udostępnioną `.proto` bibliotekę plików w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta we własnych projektach.</span><span class="sxs-lookup"><span data-stu-id="0067a-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="0067a-106">Ale jeśli masz prywatne repozytorium NuGet i wiele innych zespołów używa .NET Core, można tworzyć i publikować pakiety NuGet klienta w ramach projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="0067a-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="0067a-107">Może to być dobry sposób dzielenia się i promowania swojej usługi.</span><span class="sxs-lookup"><span data-stu-id="0067a-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="0067a-108">Jedną z zalet dystrybucji biblioteki klienta jest to, że można zwiększyć wygenerowane klasy gRPC i Protobuf z pomocnymi metodami i właściwościami "wygody".</span><span class="sxs-lookup"><span data-stu-id="0067a-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="0067a-109">W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są zadeklarowane jako `partial`, dzięki czemu można je rozszerzyć bez edytowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="0067a-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="0067a-110">Oznacza to, że łatwo jest dodać konstruktory, metody i właściwości obliczeniowe do typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="0067a-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="0067a-111">Nie należy używać kodu niestandardowego, aby zapewnić podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="0067a-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="0067a-112">Nie chcesz ograniczać tej podstawowej funkcji do zespołów .NET, które używają biblioteki udostępnionej, i nie udostępniać jej zespołom, które używają innych języków lub platform, takich jak Python lub Java.</span><span class="sxs-lookup"><span data-stu-id="0067a-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="0067a-113">Upewnij się, że jak najwięcej zespołów może uzyskać dostęp do usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="0067a-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="0067a-114">Najlepszym sposobem, aby to `.proto` zrobić jest udostępnianie plików, dzięki czemu deweloperzy mogą generować własnych klientów.</span><span class="sxs-lookup"><span data-stu-id="0067a-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="0067a-115">Jest to szczególnie prawdziwe w środowisku wielu platform, gdzie różne zespoły często używają różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="0067a-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="0067a-116">Przydatne rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="0067a-116">Useful extensions</span></span>

<span data-ttu-id="0067a-117">Istnieją dwa powszechnie używane interfejsy w .NET do radzenia <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601>sobie ze strumieniami obiektów: i .</span><span class="sxs-lookup"><span data-stu-id="0067a-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="0067a-118">Począwszy od .NET Core 3.0 i C# <xref:System.Collections.Generic.IAsyncEnumerable%601> 8.0, istnieje interfejs do przetwarzania `await foreach` strumieni asynchronicznie i składni za pomocą interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0067a-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="0067a-119">W tej sekcji przedstawiono kod wielokrotnego użytku do stosowania tych interfejsów do strumieni gRPC.</span><span class="sxs-lookup"><span data-stu-id="0067a-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="0067a-120">Z .NET Core gRPC bibliotek klienta istnieje `ReadAllAsync` metoda `IAsyncStreamReader<T>` rozszerzenia, `IAsyncEnumerable<T>` który tworzy interfejs.</span><span class="sxs-lookup"><span data-stu-id="0067a-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="0067a-121">Dla deweloperów korzystających z programowania reaktywnego `IObservable<T>` równoważna metoda rozszerzenia do tworzenia interfejsu może wyglądać jak w przykładzie w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0067a-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="0067a-122">Iobservable</span><span class="sxs-lookup"><span data-stu-id="0067a-122">IObservable</span></span>

<span data-ttu-id="0067a-123">Interfejs `IObservable<T>` jest "reaktywną" odwrotnością `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="0067a-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="0067a-124">Zamiast ściągać elementy ze strumienia, podejście reaktywne umożliwia przepływanie elementów strumienia do subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="0067a-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="0067a-125">Jest to bardzo podobne do strumieni gRPC i łatwo `IObservable<T>` jest `IAsyncStreamReader<T>` owinąć interfejs wokół interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0067a-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="0067a-126">Ten kod jest `IAsyncEnumerable<T>` dłuższy niż kod, ponieważ c# nie ma wbudowanej obsługi pracy z obserwowalnych.</span><span class="sxs-lookup"><span data-stu-id="0067a-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="0067a-127">Musisz ręcznie utworzyć klasę implementacji.</span><span class="sxs-lookup"><span data-stu-id="0067a-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="0067a-128">Jest to klasa ogólna, więc pojedyncza implementacja działa we wszystkich typach.</span><span class="sxs-lookup"><span data-stu-id="0067a-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="0067a-129">Ta obserwowana `Subscribe` implementacja umożliwia metodę, która ma być wywoływana tylko raz, ponieważ posiadanie wielu subskrybentów próbujących odczytać ze strumienia spowodowałoby chaos.</span><span class="sxs-lookup"><span data-stu-id="0067a-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="0067a-130">Istnieją operatory, `Replay` takie jak [system.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), które umożliwiają buforowanie i powtarzalne udostępnianie obserwowalnych, które mogą być używane z tą implementacją.</span><span class="sxs-lookup"><span data-stu-id="0067a-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="0067a-131">Klasa `GrpcStreamSubscription` obsługuje wyliczenie `IAsyncStreamReader`:</span><span class="sxs-lookup"><span data-stu-id="0067a-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="0067a-132">Wszystko, co jest wymagane teraz jest prosta metoda rozszerzenia, aby utworzyć obserwowalne z czytnika strumienia.</span><span class="sxs-lookup"><span data-stu-id="0067a-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="0067a-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="0067a-133">Summary</span></span>

<span data-ttu-id="0067a-134">Modele `IAsyncEnumerable` `IObservable` i są dobrze obsługiwane i dobrze udokumentowane sposoby radzenia sobie z asynchronicznych strumieni danych w .NET.</span><span class="sxs-lookup"><span data-stu-id="0067a-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="0067a-135">Strumienie gRPC dobrze mapują zarówno paradygmaty, oferując ścisłą integrację z .NET Core, jak i reaktywne i asynchroniczne style programowania.</span><span class="sxs-lookup"><span data-stu-id="0067a-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0067a-136">[Poprzedni](streaming-versus-repeated.md)
>[następny](security.md)</span><span class="sxs-lookup"><span data-stu-id="0067a-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
