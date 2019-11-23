---
title: Typy RPC-gRPC dla deweloperów WCF
description: Przegląd typów zdalnego wywołania procedury obsługiwanego przez program WCF i ich odpowiedników w gRPC
ms.date: 09/02/2019
ms.openlocfilehash: 64375236da17c0aedbafe1cb441e72a144203358
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967267"
---
# <a name="types-of-rpc"></a><span data-ttu-id="c4191-103">Typy zdalnych wywołań procedur</span><span class="sxs-lookup"><span data-stu-id="c4191-103">Types of RPC</span></span>

<span data-ttu-id="c4191-104">Jako deweloper Windows Communication Foundation (WCF) prawdopodobnie używasz następujących typów zdalnego wywołania procedury (RPC):</span><span class="sxs-lookup"><span data-stu-id="c4191-104">As a Windows Communication Foundation (WCF) developer, you're probably used to dealing with the following types of Remote Procedure Call (RPC):</span></span>

- <span data-ttu-id="c4191-105">Żądanie/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="c4191-105">Request/Reply</span></span>
- <span data-ttu-id="c4191-106">Stron</span><span class="sxs-lookup"><span data-stu-id="c4191-106">Duplex:</span></span>
  - <span data-ttu-id="c4191-107">Jednokierunkowa dupleks z sesją</span><span class="sxs-lookup"><span data-stu-id="c4191-107">One-way duplex with session</span></span>
  - <span data-ttu-id="c4191-108">Pełny dupleks z sesją</span><span class="sxs-lookup"><span data-stu-id="c4191-108">Full duplex with session</span></span>
- <span data-ttu-id="c4191-109">Jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="c4191-109">One-way</span></span>

<span data-ttu-id="c4191-110">Istnieje możliwość mapowania tych typów RPC w sposób naturalny do istniejących koncepcji gRPC, a ten rozdział będzie wyglądać na każdej z tych obszarów z kolei.</span><span class="sxs-lookup"><span data-stu-id="c4191-110">It's possible to map these RPC types fairly naturally to existing gRPC concepts and this chapter will look at each of these areas in turn.</span></span> <span data-ttu-id="c4191-111">Podobne przykłady zostaną omówione na znacznie większej głębokości w [rozdziale 5](migrate-wcf-to-grpc.md).</span><span class="sxs-lookup"><span data-stu-id="c4191-111">Similar examples will be explored in much greater depth in [Chapter 5](migrate-wcf-to-grpc.md).</span></span>

| <span data-ttu-id="c4191-112">WCF</span><span class="sxs-lookup"><span data-stu-id="c4191-112">WCF</span></span> | <span data-ttu-id="c4191-113">gRPC</span><span class="sxs-lookup"><span data-stu-id="c4191-113">gRPC</span></span> |
| --- | ---- |
| <span data-ttu-id="c4191-114">Regularne żądanie/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="c4191-114">Regular request/reply</span></span> | <span data-ttu-id="c4191-115">Jednostk</span><span class="sxs-lookup"><span data-stu-id="c4191-115">Unary</span></span> |
| <span data-ttu-id="c4191-116">Usługa dupleksowa z sesją przy użyciu interfejsu wywołania zwrotnego klienta</span><span class="sxs-lookup"><span data-stu-id="c4191-116">Duplex service with session using a client callback interface</span></span> | <span data-ttu-id="c4191-117">Przesyłanie strumieniowe serwera</span><span class="sxs-lookup"><span data-stu-id="c4191-117">Server streaming</span></span> |
| <span data-ttu-id="c4191-118">Usługa pełnego dupleksu z sesją</span><span class="sxs-lookup"><span data-stu-id="c4191-118">Full duplex service with session</span></span> | <span data-ttu-id="c4191-119">Przesyłanie strumieniowe dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="c4191-119">Bidirectional streaming</span></span> |
| <span data-ttu-id="c4191-120">Operacje jednokierunkowe</span><span class="sxs-lookup"><span data-stu-id="c4191-120">One-way operations</span></span> | <span data-ttu-id="c4191-121">Przesyłanie strumieniowe klienta</span><span class="sxs-lookup"><span data-stu-id="c4191-121">Client streaming</span></span> |

## <a name="requestreply"></a><span data-ttu-id="c4191-122">Żądanie/odpowiedź</span><span class="sxs-lookup"><span data-stu-id="c4191-122">Request/reply</span></span>

<span data-ttu-id="c4191-123">W przypadku prostych metod żądania/odpowiedzi, które pobierają i zwracają małe ilości danych, należy użyć najprostszego wzorca gRPC, jednoargumentowego wywołania RPC.</span><span class="sxs-lookup"><span data-stu-id="c4191-123">For simple request/reply methods that take and return small amounts of data, use the simplest gRPC pattern, the unary RPC.</span></span>

```protobuf
service Things {
    rpc Get(GetThingRequest) returns (GetThingResponse);
}
```

```csharp
public class ThingService : Things.ThingsBase
{
    public override async Task<GetThingResponse> Get(GetThingRequest request, ServerCallContext context)
    {
        // Get thing from database
        return new GetThingResponse { Thing = thing };
    }
}
```

```csharp
public async Task ShowThing(int thingId)
{
    var thing = await _thingsClient.GetAsync(new GetThingRequest { ThingId = thingId });
    Console.WriteLine($"{thing.Name}");
}
```

<span data-ttu-id="c4191-124">Jak widać, implementacja metody gRPC jednoargumentowej usługi RPC jest bardzo podobna do implementowania operacji WCF, z wyjątkiem tego, że z gRPC przesłonić metodę klasy bazowej zamiast implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="c4191-124">As you can see, implementing a gRPC unary RPC service method is very similar to implementing a WCF operation, except that with gRPC you override a base class method instead of implementing an interface.</span></span> <span data-ttu-id="c4191-125">Należy pamiętać, że na serwerze gRPC metody podstawowe zawsze zwracają <xref:System.Threading.Tasks.Task%601>, chociaż klient zapewnia metody asynchroniczne i blokujące do wywoływania usługi.</span><span class="sxs-lookup"><span data-stu-id="c4191-125">Note that on the server, gRPC base methods always return a <xref:System.Threading.Tasks.Task%601>, although the client provides both async and blocking methods to call the service.</span></span>

## <a name="wcf-duplex-one-way-to-client"></a><span data-ttu-id="c4191-126">Tryb dupleksu WCF — jednokierunkowe dla klienta</span><span class="sxs-lookup"><span data-stu-id="c4191-126">WCF duplex, one-way to client</span></span>

<span data-ttu-id="c4191-127">Aplikacje WCF (z określonymi powiązaniami) mogą utworzyć trwałe połączenie między klientem i serwerem, a serwer może wysyłać dane do klienta do momentu zamknięcia połączenia przy użyciu *interfejsu wywołania zwrotnego* określonego we właściwości <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4191-127">WCF applications (with certain bindings) can create a persistent connection between client and server, and the server can asynchronously send data to the client until the connection is closed, using a *callback interface* specified in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="c4191-128">usługi gRPC Services zapewniają podobną funkcjonalność przy użyciu strumieni komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c4191-128">gRPC services provide similar functionality with message streams.</span></span> <span data-ttu-id="c4191-129">Strumienie nie mapują *dokładnie* na usługi WCF w warunkach implementacji, ale można osiągnąć te same wyniki.</span><span class="sxs-lookup"><span data-stu-id="c4191-129">Streams don't map *exactly* to WCF duplex services in terms of implementation, but the same results can be achieved.</span></span>

### <a name="grpc-streaming"></a><span data-ttu-id="c4191-130">gRPC Streaming</span><span class="sxs-lookup"><span data-stu-id="c4191-130">gRPC streaming</span></span>

<span data-ttu-id="c4191-131">Program gRPC obsługuje tworzenie strumieni trwałych z klienta na serwer oraz z serwera na klienta.</span><span class="sxs-lookup"><span data-stu-id="c4191-131">gRPC supports the creation of persistent streams from client to server, and from server to client.</span></span> <span data-ttu-id="c4191-132">Oba typy strumieni mogą być aktywne współbieżnie; jest to nazywane dwukierunkową transmisją.</span><span class="sxs-lookup"><span data-stu-id="c4191-132">Both types of stream may be active concurrently; this is called bidirectional streaming.</span></span> <span data-ttu-id="c4191-133">Strumienie mogą służyć do dowolnych, asynchronicznych komunikatów w czasie lub do przekazywania dużych zestawów danych, które są zbyt duże, aby generować i wysyłać w ramach pojedynczego żądania lub odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="c4191-133">Streams can be used for arbitrary, asynchronous messaging over time, or for passing large datasets that are too big to generate and send in a single request or response.</span></span>

<span data-ttu-id="c4191-134">Poniższy przykład przedstawia serwer RPC przesyłania strumieniowego serwera.</span><span class="sxs-lookup"><span data-stu-id="c4191-134">The following example shows a server streaming RPC.</span></span>

```protobuf
service ClockStreamer {
    rpc Subscribe(ClockSubscribeRequest) returns (stream ClockMessage);
}
```

```csharp
public class ClockStreamerService : ClockStreamer.ClockStreamerBase
{
    public override async Task Subscribe(ClockSubscribeRequest request,
        IServerStreamWriter<ClockMessage> responseStream,
        ServerCallContext context)
    {
        while (!context.CancellationToken.IsCancellationRequested)
        {
            var time = DateTimeOffset.UtcNow;
            await responseStream.WriteAsync(new ClockMessage { message = $"The time is {time:t}." });
            await Task.Delay(TimeSpan.FromSeconds(10), context.CancellationToken);
        }
    }
}
```

<span data-ttu-id="c4191-135">Ten strumień serwera może być wykorzystany z aplikacji klienckiej, jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="c4191-135">This server stream could be consumed from a client application as shown in the following code:</span></span>

```csharp
public async Task TellTheTimeAsync(CancellationToken token)
{
    var channel = GrpcChannel.ForAddress("https://localhost:5001");
    var client = new ClockStreamer.ClockStreamerClient(channel);

    var request = new ClockSubscribeRequest();
    var response = client.Subscribe(request);

    await foreach (var update in response.ResponseStream.ReadAllAsync(token))
    {
        Console.WriteLine(update.Message);
    }
}
```

> [!NOTE]
> <span data-ttu-id="c4191-136">Wywołania RPC przesyłania strumieniowego serwera są przydatne w przypadku usług w stylu subskrypcji, a także do wysyłania bardzo dużych zestawów danych, gdy byłyby one niewydajne lub niemożliwe do skompilowania całego DataSet w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c4191-136">Server streaming RPCs are useful for subscription-style services, and also for sending very large datasets when it would be inefficient or impossible to build the entire dataset in memory.</span></span> <span data-ttu-id="c4191-137">Jednak odpowiedzi na przesyłanie strumieniowe nie są tak szybkie jak wysyłanie `repeated` pól w pojedynczym komunikacie, więc w przypadku małych zestawów danych nie należy używać przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="c4191-137">However, streaming responses isn't as fast as sending `repeated` fields in a single message, so as a rule streaming shouldn't be used for small datasets.</span></span>

### <a name="differences-to-wcf"></a><span data-ttu-id="c4191-138">Różnice w programie WCF</span><span class="sxs-lookup"><span data-stu-id="c4191-138">Differences to WCF</span></span>

<span data-ttu-id="c4191-139">Usługa WCF Duplex korzysta z interfejsu wywołania zwrotnego klienta, który może mieć wiele metod.</span><span class="sxs-lookup"><span data-stu-id="c4191-139">A WCF duplex service uses a client callback interface that can have multiple methods.</span></span> <span data-ttu-id="c4191-140">Usługa przesyłania strumieniowego serwera gRPC może wysyłać komunikaty tylko przez jeden strumień.</span><span class="sxs-lookup"><span data-stu-id="c4191-140">A gRPC server streaming service can only send messages over a single stream.</span></span> <span data-ttu-id="c4191-141">Jeśli potrzebujesz wielu metod, użyj typu komunikatu z [dowolnym polem lub jednym z pól](protobuf-any-oneof.md) , aby wysłać różne komunikaty, a następnie napisz kod w kliencie, aby je obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="c4191-141">If you need multiple methods, use a message type with either [an Any field or a oneof field](protobuf-any-oneof.md) to send different messages, and write code in the client to handle them.</span></span>

<span data-ttu-id="c4191-142">W programie WCF Klasa [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) z sesją jest utrzymywana, dopóki połączenie nie zostanie zamknięte, a wiele metod może być wywoływanych w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="c4191-142">In WCF, the [ServiceContract](xref:System.ServiceModel.ServiceContractAttribute) class with the session is kept alive until the connection is closed, and multiple methods may be called within the session.</span></span> <span data-ttu-id="c4191-143">W gRPC `Task` zwrócone przez metodę implementacji nie powinny zostać ukończone do momentu zamknięcia połączenia.</span><span class="sxs-lookup"><span data-stu-id="c4191-143">In gRPC, the `Task` returned by the implementation method shouldn't complete until the connection is closed.</span></span>

## <a name="wcf-one-way-operations-and-grpc-client-streaming"></a><span data-ttu-id="c4191-144">Operacje jednokierunkowe w programie WCF i gRPC Streaming klienta</span><span class="sxs-lookup"><span data-stu-id="c4191-144">WCF one-way operations and gRPC client streaming</span></span>

<span data-ttu-id="c4191-145">Funkcja WCF oferuje jednokierunkowe operacje (oznaczone `[OperationContract(IsOneWay = true)]`), które zwracają potwierdzenie specyficzne dla transportu.</span><span class="sxs-lookup"><span data-stu-id="c4191-145">WCF provides one-way operations (marked with `[OperationContract(IsOneWay = true)]`) that return a transport-specific acknowledgement.</span></span> <span data-ttu-id="c4191-146">metody usługi gRPC zawsze zwracają odpowiedź, nawet jeśli są puste, a klient zawsze powinien oczekiwać na tę odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="c4191-146">gRPC service methods always return a response, even if it's empty, and the client should always await that response.</span></span> <span data-ttu-id="c4191-147">W przypadku komunikatów w stylu "Uruchom i zapomnij" w programie gRPC można utworzyć usługę przesyłania strumieniowego klienta.</span><span class="sxs-lookup"><span data-stu-id="c4191-147">For "fire-and-forget" style messaging in gRPC, you can create a client streaming service.</span></span>

### <a name="thing_logproto"></a><span data-ttu-id="c4191-148">thing_log. proto</span><span class="sxs-lookup"><span data-stu-id="c4191-148">thing_log.proto</span></span>

```protobuf
service ThingLog {
  rpc OpenConnection(stream Thing) returns (ConnectionClosedResponse);
}
```

### <a name="thinglogservicecs"></a><span data-ttu-id="c4191-149">ThingLogService.cs</span><span class="sxs-lookup"><span data-stu-id="c4191-149">ThingLogService.cs</span></span>

```csharp
public class ThingLogService : Protos.ThingLog.ThingLogBase
{
    private static readonly ConnectionClosedResponse EmptyResponse = new ConnectionClosedResponse();
    private readonly ILogger<ThingLogService> _logger;
    public ThingLogService(ILogger<ThingLogService> logger)
    {
        _logger = logger;
    }

    public override async Task<CompletedResponse> OpenConnection(IAsyncStreamReader<Thing> requestStream, ServerCallContext context)
    {
        while (await requestStream.MoveNext(context.CancellationToken))
        {
            _logger.LogInformation(requestStream.Current.Description);
        }
        return EmptyResponse;
    }
}
```

### <a name="thinglog-client-example"></a><span data-ttu-id="c4191-150">Przykład klienta ThingLog</span><span class="sxs-lookup"><span data-stu-id="c4191-150">ThingLog client example</span></span>

```csharp
public class ThingLogger : IAsyncDisposable
{
    private readonly ThingLog.ThingLogClient _client;
    private readonly AsyncClientStreamingCall<ThingLogRequest, CompletedResponse> _stream;

    public ThingLogger(ThingLog.ThingLogClient client)
    {
        _client = client;
        _stream = client.OpenConnection();
    }

    public async Task WriteAsync(string description)
    {
        await _stream.RequestStream.WriteAsync(new Thing
        {
            Description = description,
            Time = Timestamp.FromDateTimeOffset(DateTimeOffset.UtcNow)
        });
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        _stream.Dispose();
    }
}
```

<span data-ttu-id="c4191-151">Ponownie wywołania RPC przesyłania strumieniowego klientów mogą być używane do obsługi komunikatów na potrzeby uruchamiania i zapomnień, jak pokazano w poprzednim przykładzie, ale również do wysyłania bardzo dużych zestawów danych do serwera.</span><span class="sxs-lookup"><span data-stu-id="c4191-151">Again, client streaming RPCs can be used for fire-and-forget messaging as shown in the previous example, but also for sending very large datasets to the server.</span></span> <span data-ttu-id="c4191-152">To samo ostrzeżenie o wydajności dotyczy: w przypadku mniejszych zestawów danych Użyj `repeated` pól w zwykłych wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="c4191-152">The same warning about performance applies: for smaller datasets, use `repeated` fields in regular messages.</span></span>

## <a name="wcf-full-duplex-services"></a><span data-ttu-id="c4191-153">Usługi WCF Full Duplex</span><span class="sxs-lookup"><span data-stu-id="c4191-153">WCF full duplex services</span></span>

<span data-ttu-id="c4191-154">Powiązanie dupleksowe WCF obsługuje wiele operacji jednokierunkowych w interfejsie usługi i interfejsie wywołania zwrotnego klienta, co pozwala na ciągłe konwersacje między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="c4191-154">WCF duplex binding supports multiple one-way operations on both the service interface and the client callback interface, allowing ongoing conversations between client and server.</span></span> <span data-ttu-id="c4191-155">gRPC obsługuje coś podobnego do dwukierunkowych wywołań RPC przesyłania strumieniowego, gdzie oba parametry są oznaczone modyfikatorem `stream`.</span><span class="sxs-lookup"><span data-stu-id="c4191-155">gRPC supports something similar with bidirectional streaming RPCs, where both parameters are marked with the `stream` modifier.</span></span>

### <a name="chatproto"></a><span data-ttu-id="c4191-156">Chat. proto</span><span class="sxs-lookup"><span data-stu-id="c4191-156">chat.proto</span></span>

```protobuf
service Chatter {
    rpc Connect(stream IncomingMessage) returns (stream OutgoingMessage);
}
```

### <a name="chatterservicecs"></a><span data-ttu-id="c4191-157">ChatterService.cs</span><span class="sxs-lookup"><span data-stu-id="c4191-157">ChatterService.cs</span></span>

```csharp
public class ChatterService : Chatter.ChatterBase
{
    private readonly IChatHub _hub;

    public ChatterService(IChatHub hub)
    {
        _hub = hub;
    }

    public override async Task Connect(IAsyncStreamReader<MessageRequest> requestStream, IServerStreamWriter<MessageResponse> responseStream, ServerCallContext context)
    {
        _hub.MessageReceived += async (sender, args) =>
            await responseStream.WriteAsync(new MessageResponse {Text = args.Message});

        while (await requestStream.MoveNext(context.CancellationToken))
        {
            await _hub.SendAsync(requestStream.Current.Text);
        }
    }
}
```

<span data-ttu-id="c4191-158">W poprzednim przykładzie widać, że metoda implementacji odbiera strumień żądania (`IAsyncStreamReader<MessageRequest>`) i strumień odpowiedzi (`IServerStreamWriter<MessageResponse>`) i może odczytywać i zapisywać komunikaty do momentu zamknięcia połączenia.</span><span class="sxs-lookup"><span data-stu-id="c4191-158">In the previous example, you can see that the implementation method receives both a request stream (`IAsyncStreamReader<MessageRequest>`) and a response stream (`IServerStreamWriter<MessageResponse>`), and can read and write messages until the connection is closed.</span></span>

### <a name="chatter-client"></a><span data-ttu-id="c4191-159">Klient rozmawiający</span><span class="sxs-lookup"><span data-stu-id="c4191-159">Chatter client</span></span>

```csharp
public class Chat : IAsyncDisposable
{
    private readonly Chatter.ChatterClient _client;
    private readonly AsyncDuplexStreamingCall<MessageRequest, MessageResponse> _stream;
    private readonly CancellationTokenSource _cancellationTokenSource;
    private readonly Task _readTask;

    public Chat(Chatter.ChatterClient client)
    {
        _client = client;
        _stream = _client.Connect();
        _cancellationTokenSource = new CancellationTokenSource();
        _readTask = ReadAsync(_cancellationTokenSource.Token);
    }

    public async Task SendAsync(string message)
    {
        await _stream.RequestStream.WriteAsync(new MessageRequest {Text = message});
    }

    private async Task ReadAsync(CancellationToken token)
    {
        while (await _stream.ResponseStream.MoveNext(token))
        {
            Console.WriteLine(_stream.ResponseStream.Current.Text);
        }
    }

    public async ValueTask DisposeAsync()
    {
        await _stream.RequestStream.CompleteAsync();
        await _readTask;
        _stream.Dispose();
    }
}
```

>[!div class="step-by-step"]
><span data-ttu-id="c4191-160">[Poprzedni](wcf-bindings.md)
>[Następny](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="c4191-160">[Previous](wcf-bindings.md)
[Next](metadata.md)</span></span>
