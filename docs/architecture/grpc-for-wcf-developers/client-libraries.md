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
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="0250e-103">Tworzenie bibliotek klienckich gRPC</span><span class="sxs-lookup"><span data-stu-id="0250e-103">Create gRPC client libraries</span></span>

<span data-ttu-id="0250e-104">Nie jest konieczne dystrybuowanie bibliotek klienckich dla aplikacji gRPC.</span><span class="sxs-lookup"><span data-stu-id="0250e-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="0250e-105">Można utworzyć udostępnioną bibliotekę plików `.proto` w organizacji, a inne zespoły mogą używać tych plików do generowania kodu klienta w swoich projektach.</span><span class="sxs-lookup"><span data-stu-id="0250e-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="0250e-106">Jeśli jednak masz prywatne repozytorium NuGet i wiele innych zespołów używa platformy .NET Core, możesz tworzyć i publikować pakiety NuGet klienta w ramach projektu usługi.</span><span class="sxs-lookup"><span data-stu-id="0250e-106">But if you have a private NuGet repository and many other teams are using .NET Core, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="0250e-107">Może to być dobry sposób udostępniania i promowania usługi.</span><span class="sxs-lookup"><span data-stu-id="0250e-107">This can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="0250e-108">Jedną z zalet dystrybucji biblioteki klienta jest możliwość udoskonalenia wygenerowanych klas gRPC i protobuf przy użyciu przydatnych metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="0250e-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="0250e-109">W kodzie klienta, podobnie jak na serwerze, wszystkie klasy są deklarowane jako `partial`, więc można je zwiększyć bez konieczności edytowania wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="0250e-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="0250e-110">Oznacza to, że można łatwo dodać konstruktory, metody i właściwości obliczeniowe do typów podstawowych.</span><span class="sxs-lookup"><span data-stu-id="0250e-110">This means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="0250e-111">Nie należy używać niestandardowego kodu w celu zapewnienia zasadniczych funkcji.</span><span class="sxs-lookup"><span data-stu-id="0250e-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="0250e-112">Nie chcesz ograniczyć tej funkcji do zespołów .NET, które korzystają z biblioteki udostępnionej, i nie udostępniaj jej zespołom korzystającym z innych języków lub platform, takich jak Python lub Java.</span><span class="sxs-lookup"><span data-stu-id="0250e-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="0250e-113">Upewnij się, że możliwie jak najwięcej zespołów może uzyskać dostęp do usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="0250e-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="0250e-114">Najlepszym sposobem jest udostępnienie `.proto` plików, aby deweloperzy mogli generować własnych klientów.</span><span class="sxs-lookup"><span data-stu-id="0250e-114">The best way to do this is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="0250e-115">Jest to szczególnie prawdziwe w środowisku wieloplatformowym, w którym różne zespoły często używają różnych języków programowania i struktur lub gdzie interfejs API jest dostępny zewnętrznie.</span><span class="sxs-lookup"><span data-stu-id="0250e-115">This is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="0250e-116">Przydatne rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="0250e-116">Useful extensions</span></span>

<span data-ttu-id="0250e-117">Istnieją dwa powszechnie używane interfejsy w programie .NET do obsługi strumieni obiektów: <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.IObservable%601>.</span><span class="sxs-lookup"><span data-stu-id="0250e-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="0250e-118">Począwszy od platformy .NET Core 3,0 C# i 8,0, istnieje <xref:System.Collections.Generic.IAsyncEnumerable%601> interfejs do przetwarzania strumieni asynchronicznie i składnia `await foreach` do korzystania z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0250e-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="0250e-119">Ta sekcja przedstawia kod wielokrotnego użytku do zastosowania tych interfejsów do strumieni gRPC.</span><span class="sxs-lookup"><span data-stu-id="0250e-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="0250e-120">W przypadku bibliotek klienckich programu .NET Core gRPC istnieje `ReadAllAsync` Metoda rozszerzająca `IAsyncStreamReader<T>`, która tworzy interfejs `IAsyncEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="0250e-120">With the .NET Core gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="0250e-121">W przypadku deweloperów korzystających z samoczynnego programowania, równoważna Metoda rozszerzenia do utworzenia interfejsu `IObservable<T>` może wyglądać podobnie do przykładu w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0250e-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="0250e-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="0250e-122">IObservable</span></span>

<span data-ttu-id="0250e-123">Interfejs `IObservable<T>` to "Reactive" Reverse `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="0250e-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="0250e-124">Zamiast ściągania elementów ze strumienia, podejście reaktywne umożliwia wypychanie elementów do subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="0250e-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="0250e-125">Jest to bardzo podobne do gRPC strumieni i można łatwo otoczyć interfejs `IObservable<T>` wokół interfejsu `IAsyncStreamReader<T>`.</span><span class="sxs-lookup"><span data-stu-id="0250e-125">This is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="0250e-126">Ten kod jest dłuższy niż kod `IAsyncEnumerable<T>`, ponieważ C# nie ma wbudowaną obsługę pracy z observables.</span><span class="sxs-lookup"><span data-stu-id="0250e-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="0250e-127">Musisz ręcznie utworzyć klasę implementacji.</span><span class="sxs-lookup"><span data-stu-id="0250e-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="0250e-128">Jest to Klasa generyczna, dlatego jedna implementacja działa dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="0250e-128">It's a generic class, though, so a single implementation works across all types.</span></span>

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
> <span data-ttu-id="0250e-129">Ta zazauważalna implementacja umożliwia wywoływanie metody `Subscribe` tylko raz, ponieważ wielu subskrybentów próbujących odczytać dane ze strumienia spowodowałaby chaos.</span><span class="sxs-lookup"><span data-stu-id="0250e-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="0250e-130">Istnieją operatory, takie jak `Replay` w [System. Reactive. LINQ](https://www.nuget.org/packages/System.Reactive.Linq), które umożliwiają buforowanie i powtarzanie udostępniania observables, które mogą być używane z tą implementacją.</span><span class="sxs-lookup"><span data-stu-id="0250e-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="0250e-131">Klasa `GrpcStreamSubscription` obsługuje Wyliczenie `IAsyncStreamReader`:</span><span class="sxs-lookup"><span data-stu-id="0250e-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

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

<span data-ttu-id="0250e-132">Wszystkie wymagane teraz jest prostą metodą rozszerzenia, aby można było uzyskać zauważalność z czytnika strumienia.</span><span class="sxs-lookup"><span data-stu-id="0250e-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

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

## <a name="summary"></a><span data-ttu-id="0250e-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="0250e-133">Summary</span></span>

<span data-ttu-id="0250e-134">Modele `IAsyncEnumerable` i `IObservable` są dobrze obsługiwane i dobrze udokumentowane sposoby postępowania z asynchronicznymi strumieniami danych w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="0250e-134">The `IAsyncEnumerable` and `IObservable` models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="0250e-135">gRPC strumienie są dobrze mapowane w obu odmianach, oferując bliską integrację z programem .NET Core oraz z aktywnymi i asynchronicznymi stylami programowania.</span><span class="sxs-lookup"><span data-stu-id="0250e-135">gRPC streams map well to both paradigms, offering close integration with .NET Core, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0250e-136">[Poprzednie](streaming-versus-repeated.md)
>[dalej](security.md)</span><span class="sxs-lookup"><span data-stu-id="0250e-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
