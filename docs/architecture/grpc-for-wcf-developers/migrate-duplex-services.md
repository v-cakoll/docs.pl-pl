---
title: Migrowanie usług programu WCF Duplex do gRPC-gRPC dla deweloperów programu WCF
description: Dowiedz się, jak migrować różne formy usługi programu WCF Duplex do usługi gRPC Streaming Services.
ms.date: 09/02/2019
ms.openlocfilehash: 5737f02044ab9e4064f632164db764541a9c4d31
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628543"
---
# <a name="migrate-wcf-duplex-services-to-grpc"></a><span data-ttu-id="87e4b-103">Migrowanie usług dwukierunkowych WCF do usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="87e4b-103">Migrate WCF duplex services to gRPC</span></span>

<span data-ttu-id="87e4b-104">Teraz, gdy masz sens podstawowe pojęcia, w tej sekcji przedstawiono bardziej skomplikowane usługi *przesyłania strumieniowego* gRPC.</span><span class="sxs-lookup"><span data-stu-id="87e4b-104">Now that you have a sense of the basic concepts, in this section, you'll look at the more complicated *streaming* gRPC services.</span></span>

<span data-ttu-id="87e4b-105">Istnieje wiele sposobów używania usług dupleksowych w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="87e4b-105">There are multiple ways to use duplex services in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="87e4b-106">Niektóre usługi są inicjowane przez klienta, a następnie przesyłają strumieniowo dane z serwera.</span><span class="sxs-lookup"><span data-stu-id="87e4b-106">Some services are initiated by the client and then they stream data from the server.</span></span> <span data-ttu-id="87e4b-107">Inne usługi o pełnym dupleksie mogą pociągnąć za sobą trwającą dwukierunkową komunikację, jak w przypadku przykładowego kalkulatora klasycznego w dokumentacji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="87e4b-107">Other full-duplex services might involve more ongoing two-way communication, like the classic Calculator example in the WCF documentation.</span></span> <span data-ttu-id="87e4b-108">Ten rozdział zajmie się dwoma możliwymi implementacjami cykli magazynowych WCF i migruje je do gRPC: jeden, który korzysta z protokołu RPC przesyłania strumieniowego serwera, a drugi korzysta z dwukierunkowego wywołania RPC przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="87e4b-108">This chapter will take two possible WCF stock ticker implementations and migrate them to gRPC: one that uses a server streaming RPC and another one that uses a bidirectional streaming RPC.</span></span>

## <a name="server-streaming-rpc"></a><span data-ttu-id="87e4b-109">Serwer RPC przesyłania strumieniowego</span><span class="sxs-lookup"><span data-stu-id="87e4b-109">Server streaming RPC</span></span>

<span data-ttu-id="87e4b-110">W [przykładowym rozwiązaniu SIMPLESTOCKTICKER WCF](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker)SimpleStockPriceTicker jest usługa dupleksowa, dla której klient uruchamia połączenie z listą symboli magazynowych, a serwer używa *interfejsu wywołania zwrotnego* do wysyłania aktualizacji, gdy staną się dostępne.</span><span class="sxs-lookup"><span data-stu-id="87e4b-110">In the [sample SimpleStockTicker WCF solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/SimpleStockTickerSample/wcf/SimpleStockTicker), SimpleStockPriceTicker, there's a duplex service for which the client starts the connection with a list of stock symbols, and the server uses the *callback interface* to send updates as they become available.</span></span> <span data-ttu-id="87e4b-111">Klient implementuje ten interfejs, aby odpowiedzieć na wywołania z serwera.</span><span class="sxs-lookup"><span data-stu-id="87e4b-111">The client implements that interface to respond to calls from the server.</span></span>

### <a name="the-wcf-solution"></a><span data-ttu-id="87e4b-112">Rozwiązanie WCF</span><span class="sxs-lookup"><span data-stu-id="87e4b-112">The WCF solution</span></span>

<span data-ttu-id="87e4b-113">Rozwiązanie WCF jest implementowane jako samodzielny serwer net. TCP w .NET Framework 4. Aplikacja konsolowa *x* .</span><span class="sxs-lookup"><span data-stu-id="87e4b-113">The WCF solution is implemented as a self-hosted Net.TCP server in a .NET Framework 4.*x* console application.</span></span>

#### <a name="servicecontract"></a><span data-ttu-id="87e4b-114">ServiceContract</span><span class="sxs-lookup"><span data-stu-id="87e4b-114">ServiceContract</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(ISimpleStockTickerCallback))]
public interface ISimpleStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe(string[] symbols);
}
```

<span data-ttu-id="87e4b-115">Usługa ma pojedynczą metodę bez zwracanego typu, ponieważ używa interfejsu wywołania zwrotnego `ISimpleStockTickerCallback` do wysyłania danych do klienta w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="87e4b-115">The service has a single method with no return type because it uses the callback interface `ISimpleStockTickerCallback` to send data to the client in real time.</span></span>

#### <a name="the-callback-interface"></a><span data-ttu-id="87e4b-116">Interfejs wywołania zwrotnego</span><span class="sxs-lookup"><span data-stu-id="87e4b-116">The callback interface</span></span>

```csharp
[ServiceContract]
public interface ISimpleStockTickerCallback
{
    [OperationContract(IsOneWay = true)]
    void Update(string symbol, decimal price);
}
```

<span data-ttu-id="87e4b-117">Można znaleźć implementacje tych interfejsów w rozwiązaniu wraz z niektórymi zewnętrznymi zależnościami, aby dostarczyć dane testowe.</span><span class="sxs-lookup"><span data-stu-id="87e4b-117">You can find the implementations of these interfaces in the solution, along with faked external dependencies to provide test data.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="87e4b-118">gRPC Streaming</span><span class="sxs-lookup"><span data-stu-id="87e4b-118">gRPC streaming</span></span>

<span data-ttu-id="87e4b-119">Proces gRPC na potrzeby obsługi danych w czasie rzeczywistym różni się od procesu WCF.</span><span class="sxs-lookup"><span data-stu-id="87e4b-119">The gRPC process for handling real-time data is different from the WCF process.</span></span> <span data-ttu-id="87e4b-120">Wywołanie z klienta do serwera może utworzyć trwały strumień, który można monitorować w przypadku komunikatów, które są odbierane asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="87e4b-120">A call from client to server can create a persistent stream, which can be monitored for messages that arrive asynchronously.</span></span> <span data-ttu-id="87e4b-121">Pomimo różnic między strumieniami może być bardziej intuicyjny sposób postępowania z tymi danymi i są one bardziej istotne w nowoczesnych programowaniu, co oznacza LINQ, reaktywne strumienie, programowanie funkcjonalne i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="87e4b-121">Despite the difference, streams can be a more intuitive way of dealing with this data and are more relevant in modern programming, which emphasizes LINQ, Reactive Streams, functional programming, and so on.</span></span>

<span data-ttu-id="87e4b-122">Definicja usługi wymaga dwóch komunikatów: jeden dla żądania i jeden dla strumienia.</span><span class="sxs-lookup"><span data-stu-id="87e4b-122">The service definition needs two messages: one for the request and one for the stream.</span></span> <span data-ttu-id="87e4b-123">Usługa zwraca strumień komunikatu `StockTickerUpdate` ze słowem kluczowym `stream` w swojej deklaracji `return`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-123">The service returns a stream of the `StockTickerUpdate` message with the `stream` keyword in its `return` declaration.</span></span> <span data-ttu-id="87e4b-124">Zalecamy dodanie `Timestamp` do aktualizacji w celu pokazywania dokładnego czasu zmiany cen.</span><span class="sxs-lookup"><span data-stu-id="87e4b-124">We recommend that you add a `Timestamp` to the update to show the exact time of the price change.</span></span>

#### <a name="simple_stock_tickerproto"></a><span data-ttu-id="87e4b-125">simple_stock_ticker. proto</span><span class="sxs-lookup"><span data-stu-id="87e4b-125">simple_stock_ticker.proto</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.SimpleStockTickerServer.Protos";

import "google/protobuf/timestamp.proto";

package SimpleStockTickerServer;

service SimpleStockTicker {
  rpc Subscribe (SubscribeRequest) returns (stream StockTickerUpdate);
}

message SubscribeRequest {
  repeated string symbols = 1;
}

message StockTickerUpdate {
  string symbol = 1;
  int32 price_cents = 2;
  google.protobuf.Timestamp time = 3;
}
```

### <a name="implement-simplestockticker"></a><span data-ttu-id="87e4b-126">Implementuj SimpleStockTicker</span><span class="sxs-lookup"><span data-stu-id="87e4b-126">Implement SimpleStockTicker</span></span>

<span data-ttu-id="87e4b-127">Ponownie Użyj fałszywej `StockPriceSubscriber` z projektu WCF, kopiując trzy klasy z biblioteki klas `TraderSys.StockMarket` do nowej biblioteki klas .NET Standard w rozwiązaniu docelowym.</span><span class="sxs-lookup"><span data-stu-id="87e4b-127">Reuse the fake `StockPriceSubscriber` from the WCF project by copying the three classes from the `TraderSys.StockMarket` class library into a new .NET Standard class library in the target solution.</span></span> <span data-ttu-id="87e4b-128">Aby lepiej stosować najlepsze rozwiązania, należy dodać typ `Factory`, aby utworzyć jego wystąpienia, i zarejestrować `IStockPriceSubscriberFactory` za pomocą usług ASP.NET Core wtrysku zależności.</span><span class="sxs-lookup"><span data-stu-id="87e4b-128">To better follow best practices, add a `Factory` type to create instances of it, and register the `IStockPriceSubscriberFactory` with the ASP.NET Core dependency injection services.</span></span>

#### <a name="the-factory-implementation"></a><span data-ttu-id="87e4b-129">Implementacja fabryki</span><span class="sxs-lookup"><span data-stu-id="87e4b-129">The factory implementation</span></span>

```csharp
public interface IStockPriceSubscriberFactory
{
    IStockPriceSubscriber GetSubscriber(string[] symbols);
}

public class StockPriceSubscriberFactory : IStockPriceSubscriberFactory
{
    public IStockPriceSubscriber GetSubscriber(string[] symbols)
    {
        return new StockPriceSubscriber(symbols);
    }
}
```

#### <a name="register-the-factory"></a><span data-ttu-id="87e4b-130">Rejestrowanie fabryki</span><span class="sxs-lookup"><span data-stu-id="87e4b-130">Register the factory</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddGrpc();
    services.AddSingleton<IStockPriceSubscriberFactory, StockPriceSubscriberFactory>();
}
```

<span data-ttu-id="87e4b-131">Tej klasy można teraz używać do implementowania `StockTickerService`gRPC.</span><span class="sxs-lookup"><span data-stu-id="87e4b-131">This class can now be used to implement the gRPC `StockTickerService`.</span></span>

#### <a name="stocktickerservicecs"></a><span data-ttu-id="87e4b-132">StockTickerService.cs</span><span class="sxs-lookup"><span data-stu-id="87e4b-132">StockTickerService.cs</span></span>

```csharp
public class StockTickerService : Protos.SimpleStockTicker.SimpleStockTickerBase
{
    private readonly IStockPriceSubscriberFactory _subscriberFactory;

    public StockTickerService(IStockPriceSubscriberFactory subscriberFactory)
    {
        _subscriberFactory = subscriberFactory;
    }

    public override async Task Subscribe(SubscribeRequest request, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
    {
        var subscriber = _subscriberFactory.GetSubscriber(request.Symbols.ToArray());

        subscriber.Update += async (sender, args) =>
            await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

        await AwaitCancellation(context.CancellationToken);
    }

    private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
    {
        try
        {
            await stream.WriteAsync(new StockTickerUpdate
            {
                Symbol = symbol,
                PriceCents = (int)(price * 100),
                Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
            });
        }
        catch (Exception e)
        {
            // Handle any errors caused by broken connection, etc.
            _logger.LogError($"Failed to write message: {e.Message}");
        }
    }

    private static Task AwaitCancellation(CancellationToken token)
    {
        var completion = new TaskCompletionSource<object>();
        token.Register(() => completion.SetResult(null));
        return completion.Task;
    }
}
```

<span data-ttu-id="87e4b-133">Jak widać, mimo że deklaracja w pliku `.proto` wskazuje, że metoda zwraca strumień komunikatów `StockTickerUpdate`, faktycznie zwraca `Task`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-133">As you can see, although the declaration in the `.proto` file says the method returns a stream of `StockTickerUpdate` messages, it actually returns a `Task`.</span></span> <span data-ttu-id="87e4b-134">Zadanie tworzenia strumienia jest obsługiwane przez wygenerowany kod i biblioteki środowiska uruchomieniowego gRPC, które zapewniają strumień odpowiedzi `IServerStreamWriter<StockTickerUpdate>`, gotowy do użycia.</span><span class="sxs-lookup"><span data-stu-id="87e4b-134">The job of creating the stream is handled by the generated code and the gRPC runtime libraries, which provide the `IServerStreamWriter<StockTickerUpdate>` response stream, ready to use.</span></span>

<span data-ttu-id="87e4b-135">W przeciwieństwie do usługi WCF Duplex, w której wystąpienie klasy usługi jest utrzymywane, gdy połączenie jest otwarte, usługa gRPC używa zwracanego zadania, aby zachować aktywność usługi.</span><span class="sxs-lookup"><span data-stu-id="87e4b-135">Unlike a WCF duplex service, where the instance of the service class is kept alive while the connection is open, the gRPC service uses the returned task to keep the service alive.</span></span> <span data-ttu-id="87e4b-136">Zadanie nie powinno zostać ukończone do momentu zamknięcia połączenia.</span><span class="sxs-lookup"><span data-stu-id="87e4b-136">The task shouldn't complete until the connection is closed.</span></span>

<span data-ttu-id="87e4b-137">Usługa może określić, kiedy klient zamknął połączenie przy użyciu `CancellationToken` z `ServerCallContext`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-137">The service can tell when the client has closed the connection by using the `CancellationToken` from the `ServerCallContext`.</span></span> <span data-ttu-id="87e4b-138">Prosta metoda statyczna `AwaitCancellation`jest używana do tworzenia zadania, które kończy się po anulowaniu tokenu.</span><span class="sxs-lookup"><span data-stu-id="87e4b-138">A simple static method, `AwaitCancellation`, is used to create a task that completes when the token is canceled.</span></span>

<span data-ttu-id="87e4b-139">W metodzie `Subscribe` należy uzyskać `StockPriceSubscriber` i dodać program obsługi zdarzeń, który zapisuje dane w strumieniu odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="87e4b-139">In the `Subscribe` method, then, get a `StockPriceSubscriber` and add an event handler that writes to the response stream.</span></span> <span data-ttu-id="87e4b-140">Następnie poczekaj na zamknięcie połączenia przed natychmiastowe usunięciem `subscriber`, aby zapobiec próbie zapisu danych do zamkniętego strumienia.</span><span class="sxs-lookup"><span data-stu-id="87e4b-140">Then wait for the connection to be closed before immediately disposing the `subscriber` to prevent it from trying to write data to the closed stream.</span></span>

<span data-ttu-id="87e4b-141">Metoda `WriteUpdateAsync` ma `try`/`catch` bloku, aby obsłużyć wszelkie błędy, które mogą wystąpić, gdy komunikat jest zapisywana w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="87e4b-141">The `WriteUpdateAsync` method has a `try`/`catch` block to handle any errors that might happen when a message is written to the stream.</span></span> <span data-ttu-id="87e4b-142">Jest to ważne w przypadku trwałych połączeń za pośrednictwem sieci, które mogą być złamane w dowolnym milisekundach, niezależnie od tego, czy wystąpił błąd w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="87e4b-142">This consideration is important in persistent connections over networks, which could be broken at any millisecond, whether intentionally or because of a failure somewhere.</span></span>

### <a name="use-stocktickerservice-from-a-client-application"></a><span data-ttu-id="87e4b-143">Korzystanie z StockTickerService z aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="87e4b-143">Use StockTickerService from a client application</span></span>

<span data-ttu-id="87e4b-144">Wykonaj te same czynności w poprzedniej sekcji, aby utworzyć bibliotekę klas klienta możliwej do udostępnienia z pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-144">Follow the same steps in the previous section to create a shareable client class library from the `.proto` file.</span></span> <span data-ttu-id="87e4b-145">W przykładzie znajduje się Aplikacja konsolowa programu .NET Core 3,0, która pokazuje, jak korzystać z klienta programu.</span><span class="sxs-lookup"><span data-stu-id="87e4b-145">In the sample, there's a .NET Core 3.0 console application that demonstrates how to use the client.</span></span>

#### <a name="example-programcs"></a><span data-ttu-id="87e4b-146">Przykład Program.cs</span><span class="sxs-lookup"><span data-stu-id="87e4b-146">Example Program.cs</span></span>

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        using var channel = GrpcChannel.ForAddress("https://localhost:5001");
        var client = new SimpleStockTicker.SimpleStockTickerClient(channel);

        var request = new SubscribeRequest();
        request.Symbols.AddRange(args);

        using var stream = client.Subscribe(request);

        var tokenSource = new CancellationTokenSource();

        var task = DisplayAsync(stream.ResponseStream, tokenSource.Token);

        WaitForExitKey();

        tokenSource.Cancel();
        await task;
    }
}
```

<span data-ttu-id="87e4b-147">W takim przypadku Metoda `Subscribe` wygenerowanego klienta nie jest asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="87e4b-147">In this case, the `Subscribe` method on the generated client isn't asynchronous.</span></span> <span data-ttu-id="87e4b-148">Strumień jest tworzony i możliwy do użytku od razu, ponieważ jego Metoda `MoveNext` jest asynchroniczna i po raz pierwszy jest wywoływana, dopóki połączenie nie będzie aktywne.</span><span class="sxs-lookup"><span data-stu-id="87e4b-148">The stream is created and usable right away because its `MoveNext` method is asynchronous and the first time it's called it won't complete until the connection is alive.</span></span>

<span data-ttu-id="87e4b-149">Strumień jest przesyłany do asynchronicznej metody `DisplayAsync`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-149">The stream is passed to an asynchronous `DisplayAsync` method.</span></span> <span data-ttu-id="87e4b-150">Aplikacja czeka, aż użytkownik naciśnie klawisz, a następnie anuluje metodę `DisplayAsync` i czeka na ukończenie zadania przed wyjściem.</span><span class="sxs-lookup"><span data-stu-id="87e4b-150">The application then waits for the user to press a key, and then cancels the `DisplayAsync` method and waits for the task to complete before exiting.</span></span>

> [!NOTE]
> <span data-ttu-id="87e4b-151">Ten kod używa składni deklaracji C# new 8 `using` do usuwania strumienia i kanału, gdy metoda `Main` zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="87e4b-151">This code uses the new C# 8 `using` declaration syntax to dispose of the stream and the channel when the `Main` method exits.</span></span> <span data-ttu-id="87e4b-152">Jest to mała zmiana, ale całkiem taka, która zmniejsza wcięcia i puste wiersze.</span><span class="sxs-lookup"><span data-stu-id="87e4b-152">It's a small change, but a nice one that reduces indentations and empty lines.</span></span>

#### <a name="consume-the-stream"></a><span data-ttu-id="87e4b-153">Korzystanie z strumienia</span><span class="sxs-lookup"><span data-stu-id="87e4b-153">Consume the stream</span></span>

<span data-ttu-id="87e4b-154">Funkcja WCF używa interfejsów wywołania zwrotnego, aby umożliwić serwerowi wywoływanie metod bezpośrednio na kliencie.</span><span class="sxs-lookup"><span data-stu-id="87e4b-154">WCF uses callback interfaces to allow the server to call methods directly on the client.</span></span> <span data-ttu-id="87e4b-155">strumienie gRPC działają inaczej.</span><span class="sxs-lookup"><span data-stu-id="87e4b-155">gRPC streams work differently.</span></span> <span data-ttu-id="87e4b-156">Klient wykonuje iterację na zwracanym strumieniu i przetwarza komunikaty, tak jakby były zwracane z metody lokalnej zwracającej `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-156">The client iterates over the returned stream and processes messages, just as though they were returned from a local method returning an `IEnumerable`.</span></span>

<span data-ttu-id="87e4b-157">Typ `IAsyncStreamReader<T>` działa podobnie jak `IEnumerator<T>`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-157">The `IAsyncStreamReader<T>` type works much like an `IEnumerator<T>`.</span></span> <span data-ttu-id="87e4b-158">Istnieje metoda `MoveNext`, która zwraca wartość PRAWDA, o ile istnieje więcej danych, i Właściwość `Current`, która zwraca najnowszą wartość.</span><span class="sxs-lookup"><span data-stu-id="87e4b-158">There's a `MoveNext` method that returns true as long as there's more data, and a `Current` property that returns the latest value.</span></span> <span data-ttu-id="87e4b-159">Jedyną różnicą jest to, że metoda `MoveNext` zwraca `Task<bool>` zamiast tylko `bool`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-159">The only difference is that the `MoveNext` method returns a `Task<bool>` instead of just a `bool`.</span></span> <span data-ttu-id="87e4b-160">Metoda rozszerzenia `ReadAllAsync` otacza strumień w standardowym C# 8 `IAsyncEnumerable`, który może być używany z nową składnią `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-160">The `ReadAllAsync` extension method wraps the stream in a standard C# 8 `IAsyncEnumerable` that can be used with the new `await foreach` syntax.</span></span>

```csharp
static async Task DisplayAsync(IAsyncStreamReader<StockTickerUpdate> stream, CancellationToken token)
{
    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            Console.WriteLine($"{update.Symbol}: {update.Price}");
        }
    }
    catch (RpcException e) when (e.StatusCode == StatusCode.Cancelled)
    {
        return;
    }
    catch (OperationCanceledException)
    {
        Console.WriteLine("Finished.");
    }
}
```

> [!TIP]
> <span data-ttu-id="87e4b-161">W przypadku deweloperów korzystających z reaktywnych wzorców programowania sekcja w [bibliotekach klienta](client-libraries.md#iobservable) na końcu tego rozdziału pokazuje, jak dodać metodę rozszerzenia i klasy do zawijania `IAsyncStreamReader<T>` w `IObservable<T>`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-161">For developers using reactive programming patterns, the section on [client libraries](client-libraries.md#iobservable) at the end of this chapter shows how to add an extension method and classes to wrap `IAsyncStreamReader<T>` in an `IObservable<T>`.</span></span>

<span data-ttu-id="87e4b-162">Należy również pamiętać o tym, aby przechwytywać wyjątki w tym miejscu ze względu na możliwość awarii sieci i ze względu na <xref:System.OperationCanceledException>, które mają być nieuniknione, ponieważ kod używa <xref:System.Threading.CancellationToken> do przerwania pętli.</span><span class="sxs-lookup"><span data-stu-id="87e4b-162">Again, be sure to catch exceptions here because of the possibility of network failure, and because of the <xref:System.OperationCanceledException> that will inevitably be thrown because the code is using a <xref:System.Threading.CancellationToken> to break the loop.</span></span> <span data-ttu-id="87e4b-163">Typ `RpcException` zawiera wiele przydatnych informacji o błędach środowiska uruchomieniowego gRPC, w tym `StatusCode`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-163">The `RpcException` type has a lot of useful information about gRPC runtime errors, including the `StatusCode`.</span></span> <span data-ttu-id="87e4b-164">Aby uzyskać więcej informacji, zobacz [ *Obsługa błędów* w rozdziale 4](error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="87e4b-164">For more information, see [*Error handling* in Chapter 4](error-handling.md).</span></span>

## <a name="bidirectional-streaming"></a><span data-ttu-id="87e4b-165">Przesyłanie strumieniowe dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="87e4b-165">Bidirectional streaming</span></span>

<span data-ttu-id="87e4b-166">Usługa WCF Full-Duplex umożliwia asynchroniczne wysyłanie komunikatów w czasie rzeczywistym w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="87e4b-166">A WCF full-duplex service allows for asynchronous, real-time messaging in both directions.</span></span> <span data-ttu-id="87e4b-167">W przykładzie przesyłania strumieniowego serwera klient uruchamia żądanie, a następnie odbiera strumień aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="87e4b-167">In the server streaming example, the client starts a request and then receives a stream of updates.</span></span> <span data-ttu-id="87e4b-168">Lepsza wersja tej usługi pozwala klientowi dodawać i usuwać zasoby z listy bez konieczności zatrzymywania i tworzenia nowej subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="87e4b-168">A better version of that service would allow the client to add and remove stocks from the list without having to stop and create a new subscription.</span></span> <span data-ttu-id="87e4b-169">Ta funkcja została zaimplementowana w [przykładowym rozwiązaniu FullStockTicker](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="87e4b-169">That functionality has been implemented in the [FullStockTicker sample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/wcf/FullStockTicker).</span></span>

<span data-ttu-id="87e4b-170">Interfejs `IFullStockTickerService` udostępnia trzy metody:</span><span class="sxs-lookup"><span data-stu-id="87e4b-170">The `IFullStockTickerService` interface provides three methods:</span></span>

- <span data-ttu-id="87e4b-171">`Subscribe` uruchamia połączenie.</span><span class="sxs-lookup"><span data-stu-id="87e4b-171">`Subscribe` starts the connection.</span></span>
- <span data-ttu-id="87e4b-172">`AddSymbol` dodaje symbol giełdowy do obserwowania.</span><span class="sxs-lookup"><span data-stu-id="87e4b-172">`AddSymbol` adds a stock symbol to watch.</span></span>
- <span data-ttu-id="87e4b-173">`RemoveSymbol` usuwa symbol z listy obserwowanych.</span><span class="sxs-lookup"><span data-stu-id="87e4b-173">`RemoveSymbol` removes a symbol from the watched list.</span></span>

```csharp
[ServiceContract(SessionMode = SessionMode.Required, CallbackContract = typeof(IFullStockTickerCallback))]
public interface IFullStockTickerService
{
    [OperationContract(IsOneWay = true)]
    void Subscribe();

    [OperationContract(IsOneWay = true)]
    void AddSymbol(string symbol);

    [OperationContract(IsOneWay = true)]
    void RemoveSymbol(string symbol);
}
```

<span data-ttu-id="87e4b-174">Interfejs wywołania zwrotnego pozostaje taki sam.</span><span class="sxs-lookup"><span data-stu-id="87e4b-174">The callback interface remains the same.</span></span>

<span data-ttu-id="87e4b-175">Implementacja tego wzorca w gRPC jest mniej prosta, ponieważ istnieją teraz dwa strumienie danych z przekazywaniem komunikatów: jeden z klienta do serwera, a drugi z serwera do klienta.</span><span class="sxs-lookup"><span data-stu-id="87e4b-175">Implementing this pattern in gRPC is less straightforward because there are now two streams of data with messages being passed: one from client to server and another from server to client.</span></span> <span data-ttu-id="87e4b-176">Nie jest możliwe użycie wielu metod w celu zaimplementowania operacji dodawania i usuwania, ale można przekazać więcej niż jeden typ komunikatu w jednym strumieniu przy użyciu typu `Any` lub słowa kluczowego `oneof`, które zostały omówione w [rozdziale 3](protobuf-any-oneof.md).</span><span class="sxs-lookup"><span data-stu-id="87e4b-176">It isn't possible to use multiple methods to implement the add and remove operations, but you can pass more than one type of message on a single stream by using either the `Any` type or the `oneof` keyword, which were covered in [Chapter 3](protobuf-any-oneof.md).</span></span>

<span data-ttu-id="87e4b-177">W przypadku gdy istnieje konkretny zestaw typów, które są akceptowalne, `oneof` jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="87e4b-177">In a case where there's a specific set of types that are acceptable, `oneof` is a better way to go.</span></span> <span data-ttu-id="87e4b-178">Użyj `ActionMessage`, która może zawierać `AddSymbolRequest` lub `RemoveSymbolRequest`:</span><span class="sxs-lookup"><span data-stu-id="87e4b-178">Use an `ActionMessage` that can hold either an `AddSymbolRequest` or a `RemoveSymbolRequest`:</span></span>

```protobuf
message ActionMessage {
  oneof action {
    AddSymbolRequest add = 1;
    RemoveSymbolRequest remove = 2;
  }
}

message AddSymbolRequest {
  string symbol = 1;
}

message RemoveSymbolRequest {
  string symbol = 1;
}
```

<span data-ttu-id="87e4b-179">Zadeklaruj dwukierunkową usługę przesyłania strumieniowego, która pobiera strumienie `ActionMessage` komunikatów:</span><span class="sxs-lookup"><span data-stu-id="87e4b-179">Declare a bidirectional streaming service that takes a stream of `ActionMessage` messages:</span></span>

```protobuf
service FullStockTicker {
  rpc Subscribe (stream ActionMessage) returns (stream StockTickerUpdate);
}
```

<span data-ttu-id="87e4b-180">Implementacja tej usługi jest podobna do powyższego przykładu, z wyjątkiem pierwszego parametru metody `Subscribe` jest teraz `IAsyncStreamReader<ActionMessage>`, który może służyć do obsługi żądań `Add` i `Remove`:</span><span class="sxs-lookup"><span data-stu-id="87e4b-180">The implementation for this service is similar to that of the previous example, except the first parameter of the `Subscribe` method is now an `IAsyncStreamReader<ActionMessage>`, which can be used to handle the `Add` and `Remove` requests:</span></span>

```csharp
public override async Task Subscribe(IAsyncStreamReader<ActionMessage> requestStream, IServerStreamWriter<StockTickerUpdate> responseStream, ServerCallContext context)
{
    using var subscriber = _subscriberFactory.GetSubscriber();

    subscriber.Update += async (sender, args) =>
        await WriteUpdateAsync(responseStream, args.Symbol, args.Price);

    var actionsTask = HandleActions(requestStream, subscriber, context.CancellationToken);

    _logger.LogInformation("Subscription started.");
    await AwaitCancellation(context.CancellationToken);

    try { await actionsTask; } catch { /* Ignored */ }

    _logger.LogInformation("Subscription finished.");
}

private async Task WriteUpdateAsync(IServerStreamWriter<StockTickerUpdate> stream, string symbol, decimal price)
{
    try
    {
        await stream.WriteAsync(new StockTickerUpdate
        {
            Symbol = symbol,
            PriceCents = (int)(price * 100),
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }
    catch (Exception e)
    {
        // Handle any errors caused by broken connection, etc.
        _logger.LogError($"Failed to write message: {e.Message}");
    }
}

private static Task AwaitCancellation(CancellationToken token)
{
    var completion = new TaskCompletionSource<object>();
    token.Register(() => completion.SetResult(null));
    return completion.Task;
}
```

<span data-ttu-id="87e4b-181">Klasa `ActionMessage`, która gRPC wygenerowała gwarancje, że można ustawić tylko jedną z właściwości `Add` i `Remove`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-181">The `ActionMessage` class that gRPC has generated guarantees that only one of the `Add` and `Remove` properties can be set.</span></span> <span data-ttu-id="87e4b-182">Znalezienie, który z nich nie `null` jest prawidłowym sposobem określenia, który typ komunikatu jest używany, ale istnieje lepszy sposób.</span><span class="sxs-lookup"><span data-stu-id="87e4b-182">Finding which one isn't `null` is a valid way to determine which type of message is used, but there's a better way.</span></span> <span data-ttu-id="87e4b-183">Generowanie kodu spowodowało również utworzenie `enum ActionOneOfCase` w klasie `ActionMessage`, która wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="87e4b-183">The code generation also created an `enum ActionOneOfCase` in the `ActionMessage` class, which looks like this:</span></span>

```csharp
public enum ActionOneofCase {
    None = 0,
    Add = 1,
    Remove = 2,
}
```

<span data-ttu-id="87e4b-184">Właściwość `ActionCase` w obiekcie `ActionMessage` może być używana z instrukcją `switch`, aby określić, które pole jest ustawione:</span><span class="sxs-lookup"><span data-stu-id="87e4b-184">The property `ActionCase` on the `ActionMessage` object can be used with a `switch` statement to determine which field is set:</span></span>

```csharp
private async Task HandleActions(IAsyncStreamReader<ActionMessage> requestStream, IFullStockPriceSubscriber subscriber, CancellationToken token)
{
    await foreach (var action in requestStream.ReadAllAsync(token))
    {
        switch (action.ActionCase)
        {
            case ActionMessage.ActionOneofCase.None:
                _logger.LogWarning("No Action specified.");
                break;
            case ActionMessage.ActionOneofCase.Add:
                subscriber.Add(action.Add.Symbol);
                break;
            case ActionMessage.ActionOneofCase.Remove:
                subscriber.Remove(action.Remove.Symbol);
                break;
            default:
                _logger.LogWarning($"Unknown Action '{action.ActionCase}'.");
                break;
        }
    }
}
```

> [!TIP]
> <span data-ttu-id="87e4b-185">W instrukcji `switch` występuje `default` przypadek, który rejestruje ostrzeżenie w przypadku napotkania nieznanej wartości `ActionOneOfCase`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-185">The `switch` statement has a `default` case that logs a warning if it encounters an unknown `ActionOneOfCase` value.</span></span> <span data-ttu-id="87e4b-186">Może to być przydatne, aby wskazać, że klient korzysta z nowszej wersji pliku `.proto`, który dodał więcej akcji.</span><span class="sxs-lookup"><span data-stu-id="87e4b-186">This could be useful to indicate that a client is using a later version of the `.proto` file that has added more actions.</span></span> <span data-ttu-id="87e4b-187">Jest to jeden z powodów, dla których użycie `switch` jest lepszym rozwiązaniem niż testowanie `null` w znanych polach.</span><span class="sxs-lookup"><span data-stu-id="87e4b-187">This is one reason why using a `switch` is better than testing for `null` on known fields.</span></span>

### <a name="use-fullstocktickerservice-from-a-client-application"></a><span data-ttu-id="87e4b-188">Korzystanie z FullStockTickerService z aplikacji klienckiej</span><span class="sxs-lookup"><span data-stu-id="87e4b-188">Use FullStockTickerService from a client application</span></span>

<span data-ttu-id="87e4b-189">Istnieje prosta aplikacja WPF platformy .NET Core 3,0, która demonstruje użycie tego bardziej złożonego klienta.</span><span class="sxs-lookup"><span data-stu-id="87e4b-189">There's a simple .NET Core 3.0 WPF application that demonstrates the use of this more complex client.</span></span> <span data-ttu-id="87e4b-190">Pełną aplikację można znaleźć w witrynie [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span><span class="sxs-lookup"><span data-stu-id="87e4b-190">You can find the full application on [GitHub](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTicker).</span></span>

<span data-ttu-id="87e4b-191">Klient jest używany w klasie `MainWindowViewModel`, która pobiera wystąpienie typu `FullStockTicker.FullStockTickerClient` z iniekcji zależności:</span><span class="sxs-lookup"><span data-stu-id="87e4b-191">The client is used in the `MainWindowViewModel` class, which gets an instance of the `FullStockTicker.FullStockTickerClient` type from dependency injection:</span></span>

```csharp
public class MainWindowViewModel : IAsyncDisposable, INotifyPropertyChanged
{
    private readonly FullStockTicker.FullStockTickerClient _client;
    private readonly AsyncDuplexStreamingCall<ActionMessage, StockTickerUpdate> _duplexStream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _responseTask;
    private string _addSymbol;

    public MainWindowViewModel(FullStockTicker.FullStockTickerClient client)
    {
        _cancellationTokenSource = new CancellationTokenSource();
        _client = client;
        _duplexStream = _client.Subscribe();
        _responseTask = HandleResponsesAsync(_cancellationTokenSource.Token);

        AddCommand = new AsyncCommand(Add, CanAdd);
    }
```

<span data-ttu-id="87e4b-192">Obiekt zwrócony przez metodę `client.Subscribe()` jest teraz wystąpieniem typu biblioteki gRPC `AsyncDuplexStreamingCall<TRequest, TResponse>`, który udostępnia `RequestStream` do wysyłania żądań do serwera i `ResponseStream` do obsługi odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="87e4b-192">The object returned by the `client.Subscribe()` method is now an instance of the gRPC library type `AsyncDuplexStreamingCall<TRequest, TResponse>`, which provides a `RequestStream` for sending requests to the server and a `ResponseStream` for handling responses.</span></span>

<span data-ttu-id="87e4b-193">Strumień żądania jest używany z niektórych metod `ICommand` WPF do dodawania i usuwania symboli.</span><span class="sxs-lookup"><span data-stu-id="87e4b-193">The request stream is used from some WPF `ICommand` methods to add and remove symbols.</span></span> <span data-ttu-id="87e4b-194">Dla każdej operacji Ustaw odpowiednie pole na `ActionMessage` obiekcie:</span><span class="sxs-lookup"><span data-stu-id="87e4b-194">For each operation, set the relevant field on an `ActionMessage` object:</span></span>

```csharp
private async Task Add()
{
    if (CanAdd())
    {
        await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Add = new AddSymbolRequest {Symbol = AddSymbol}});
    }
}

public async Task Remove(PriceViewModel priceViewModel)
{
    await _duplexStream.RequestStream.WriteAsync(new ActionMessage {Remove = new RemoveSymbolRequest {Symbol = priceViewModel.Symbol}});
    Prices.Remove(priceViewModel);
}
```

> [!IMPORTANT]
> <span data-ttu-id="87e4b-195">Ustawienie wartości pola `oneof` w komunikacie automatycznie czyści wszystkie pola, które zostały ustawione wcześniej.</span><span class="sxs-lookup"><span data-stu-id="87e4b-195">Setting a `oneof` field's value on a message automatically clears any fields that have been set previously.</span></span>

<span data-ttu-id="87e4b-196">Strumień odpowiedzi jest obsługiwany w metodzie `async`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-196">The stream of responses is handled in an `async` method.</span></span> <span data-ttu-id="87e4b-197">`Task` zwraca, gdy okno zostanie zamknięte:</span><span class="sxs-lookup"><span data-stu-id="87e4b-197">The `Task` it returns is held to be disposed when the window is closed:</span></span>

```csharp
private async Task HandleResponsesAsync(CancellationToken token)
{
    var stream = _duplexStream.ResponseStream;

    try
    {
        await foreach (var update in stream.ReadAllAsync(token))
        {
            var price = Prices.FirstOrDefault(p => p.Symbol.Equals(update.Symbol));
            if (price == null)
            {
                price = new PriceViewModel(this) {Symbol = update.Symbol, Price = update.PriceCents / 100m};
                Prices.Add(price);
            }
            else
            {
                price.Price = update.PriceCents / 100m;
            }
        }
    }
    catch (OperationCancelledException) { }
}
```

### <a name="client-cleanup"></a><span data-ttu-id="87e4b-198">Czyszczenie klienta</span><span class="sxs-lookup"><span data-stu-id="87e4b-198">Client cleanup</span></span>

<span data-ttu-id="87e4b-199">Po zamknięciu okna i usunięciu `MainWindowViewModel` (ze zdarzenia `Closed` `MainWindow`) zalecamy poprawną metodę usuwania obiektu `AsyncDuplexStreamingCall`.</span><span class="sxs-lookup"><span data-stu-id="87e4b-199">When the window is closed and the `MainWindowViewModel` is disposed (from the `Closed` event of `MainWindow`), we recommend that you properly dispose the `AsyncDuplexStreamingCall` object.</span></span> <span data-ttu-id="87e4b-200">W szczególności Metoda `CompleteAsync` na `RequestStream` powinna zostać wywołana, aby bezpiecznie zamknąć strumień na serwerze.</span><span class="sxs-lookup"><span data-stu-id="87e4b-200">In particular, the `CompleteAsync` method on the `RequestStream` should be called to gracefully close the stream on the server.</span></span> <span data-ttu-id="87e4b-201">Ten przykład przedstawia metodę `DisposeAsync` z przykładowego widoku — model:</span><span class="sxs-lookup"><span data-stu-id="87e4b-201">This example shows the `DisposeAsync` method from the sample view-model:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    try
    {
        await _duplexStream.RequestStream.CompleteAsync().ConfigureAwait(false);
        await _responseTask.ConfigureAwait(false);
    }
    finally
    {
        _duplexStream.Dispose();
    }
}
```

<span data-ttu-id="87e4b-202">Zamykające strumienie żądań umożliwia serwerowi usuwanie własnych zasobów w odpowiednim czasie.</span><span class="sxs-lookup"><span data-stu-id="87e4b-202">Closing request streams enables the server to dispose of its own resources in a timely way.</span></span> <span data-ttu-id="87e4b-203">Poprawia to wydajność i skalowalność usług i zapobiega wyjątkom.</span><span class="sxs-lookup"><span data-stu-id="87e4b-203">This improves the efficiency and scalability of services and prevents exceptions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="87e4b-204">[Poprzednie](migrate-request-reply.md)
>[dalej](streaming-versus-repeated.md)</span><span class="sxs-lookup"><span data-stu-id="87e4b-204">[Previous](migrate-request-reply.md)
[Next](streaming-versus-repeated.md)</span></span>
